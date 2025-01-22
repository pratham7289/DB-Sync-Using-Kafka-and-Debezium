# Real-Time Database Synchronization Using Debezium and Kafka

This project demonstrates how to set up real-time bidirectional synchronization between two PostgreSQL databases (`db1` and `db2`) using Debezium and Apache Kafka. Changes made in `db1` are automatically reflected in `db2`, and vice versa.

## Architecture Overview

The system consists of the following components:

1. **Debezium**: Captures changes (inserts, updates, deletes) from PostgreSQL databases and publishes them to Kafka topics.
2. **Kafka**: Acts as a message broker to stream change events between databases.
3. **Kafka Connect**: Manages connectors (Debezium source connectors and JDBC sink connectors).
4. **PostgreSQL**: Two databases (`db1` and `db2`) hosted on the same server.

## Prerequisites

Before setting up the synchronization, ensure the following prerequisites are met:

1. **Two RHEL Servers**:
   - **Server 1**: Hosts Apache Kafka and Zookeeper.
   - **Server 2**: Hosts PostgreSQL databases (`db1` and `db2`).

2. **Tools Installed**:
   - Java 17 (required for Kafka).
   - Apache Kafka (version 3.9.0).
   - PostgreSQL (latest version).
   - Debezium PostgreSQL Connector.

## Steps to Set Up Synchronization

### 1. Environment Setup
- Update the system packages on both servers.
- Install Java 17 on Server 1.
- Install PostgreSQL on Server 2.

### 2. Install Apache Kafka
- Download and extract Kafka on Server 1.
- Start Zookeeper and Kafka broker.
- Test Kafka by creating a topic, producing, and consuming messages.

### 3. Configure PostgreSQL
- Allow remote connections to PostgreSQL.
- Create databases (`db1` and `db2`) and users with the necessary privileges.
- Enable logical replication in PostgreSQL.

### 4. Install and Configure Debezium
- Download the Debezium PostgreSQL connector.
- Start Kafka Connect in distributed mode.

### 5. Configure Debezium Connectors
- Set up Debezium source connectors for `db1` and `db2` to capture changes and publish them to Kafka topics.

### 6. Create Kafka Topics
- Create Kafka topics for the changes captured from `db1` and `db2`.

### 7. Configure JDBC Sink Connectors
- Set up JDBC sink connectors to write changes from `db1` to `db2` and vice versa.

### 8. Test Synchronization
- Insert records into `db1` and verify they are replicated in `db2`.
- Insert records into `db2` and verify they are replicated in `db1`.

### 9. Troubleshooting
- Check Kafka Connect logs and PostgreSQL logs if synchronization is not working.
- Verify that messages are being published to the correct Kafka topics.

## Conclusion

This setup enables real-time bidirectional synchronization between two PostgreSQL databases using Debezium and Apache Kafka. Changes in one database are automatically reflected in the other, ensuring data consistency across both systems.
