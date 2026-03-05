# Restaurant Reservation System

## 📌 Project Overview
The **Restaurant Reservation System** is a database project designed to manage customer information, table reservations, and dining schedules in a restaurant.  
Many restaurants rely on phone calls or manual reservation books, which can lead to double bookings, lost reservations, and poor customer experience.  

This project focuses on designing and implementing a **relational database using MySQL** to efficiently manage reservations and improve restaurant operations.

## ❗ Problem Statement
Restaurants face challenges when reservations are handled manually:
- Double bookings due to lack of centralized tracking  
- Lost or misplaced reservation records  
- Difficulty managing table availability  
- Poor customer experience from delays and errors  

A **centralized database system** ensures accurate reservation management, improves efficiency, and enhances customer satisfaction.

## 🛠️ Tools & Technologies
- **MySQL** – Database engine  
- **SQL (Structured Query Language)** – Query language  
- **MySQL Workbench** – Database design and management  
- **ER Diagram Tool (Draw.io / Lucidchart)** – Database schema visualization  
- **GitHub** – Project documentation and version control  

## ⚙️ Features
- Customer information management (ID, name, contact details)  
- Table reservation tracking (date, time, table number)  
- Dining schedule management  
- Prevention of double bookings  
- Fast retrieval of reservation history  
- Improved customer experience  

📄 Database Design
✅ Why a Relational Database Model is Suitable
A relational database is ideal for a restaurant reservation system because:
- It enforces data integrity with primary keys, foreign keys, and constraints.
- It reduces redundancy by organizing customer, reservation, and table data into separate but related tables.
- It supports complex queries for checking availability, retrieving customer history, and managing schedules.
- It ensures consistency across transactions (e.g., preventing double bookings).
- It scales easily as the restaurant grows and handles more reservations.

  📊 Main Entities and Relationships
Entities:
- Customer
- Attributes: customer_id, first_name, last_name, contact_info
- Reservation
- Attributes: reservation_id, customer_id, table_number, reservation_date, reservation_time
- DiningSchedule
- Attributes: schedule_id, reservation_id, special_request

Relationships:
- One Customer → Many Reservations
- One Reservation → One DiningSchedule (optional, for special requests)
- Reservation links Customer to a specific table and time.



📄 Normalization

❌ Problems with a Single Table Design

If all reservation data (customer details, tables, reservation times) is stored in one table:

- Redundancy: Customer details repeated for every reservation.
- Update anomalies: Changing customer info requires multiple updates.
- Insertion anomalies: Cannot add a new customer until they have a reservation.
- Deletion anomalies: Removing a reservation may delete customer info.

✅ Normalization Steps

1NF (First Normal Form):

- Remove repeating groups.
- Separate customer details, reservations, and dining schedules into different tables.
  
2NF (Second Normal Form):

- Ensure all non-key attributes depend on the whole primary key.
- Example: In Reservation, attributes like table_number depend on reservation_id, not partially on customer_id.
  
3NF (Third Normal Form):

- Remove transitive dependencies.
- Example: special_request belongs in DiningSchedule, not in Reservation.
- Derived attributes (like “reservation status”) should be calculated, not stored redundantly.

🎯 Final Normalized Schema (3NF)
- Customer(customer_id PK, first_name, last_name, contact_info)
- Reservation(reservation_id PK, customer_id FK, table_number, reservation_date, reservation_time)
- DiningSchedule(schedule_id PK, reservation_id FK, special_request)
  
Using MySQL, we are going to:

1. Create the database.
2. Create all required tables with proper constraints.
3. Insert the provided sample data.
4. Retrieve all reservations for a specific date.
5. Check available tables for a given time slot.
6. Update reservation details.
7. Cancel a reservation.
8. Use JOINs to generate reservation reports.



