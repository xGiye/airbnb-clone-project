# airbnb-clone-project

The Airbnb Clone Project Blueprint is a clone of the AirBnB website, focusing on the backend structure. It is a learning project to understand backend development. It is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments.

## Goals

Recreate core functionalities of AirBnB, which includes:

- **User Management**: Implement a secure system for user registration,
- **Property Management**: Develop features for property listing creation, updates, and retrieval.
- **Booking System**: Create a booking mechanism for users to reserve properties and manage booking details.
- **Payment Processing**: Integrate a payment system to handle transactions and record payment details.

## Technology Stack

This project utilizes a modern and powerful technology stack to build a robust and scalable Airbnb clone:

- **Python**: The core programming language used to develop the backend logic and server-side functionality.

- **Django**: A high-level Python web framework that simplifies the creation of complex, secure, and maintainable web applications. It’s used for handling URL routing, views, models, and admin interfaces.

- **Django REST Framework (DRF)**: An extension of Django that provides tools and libraries to build and manage RESTful APIs. It handles authentication, serialization, and response formatting.

- **PostgreSQL**: A reliable and powerful open-source relational database system used to store and manage structured data for the application.

- **GraphQL**: A query language for APIs that enables clients to request only the data they need. It provides flexibility and efficiency in data retrieval, especially useful in complex frontends.

- **Git/GitHub**: Used for version control and collaboration. Git tracks changes in the source code, while GitHub hosts the project repository and facilitates team collaboration.

## Team Roles

### 1. Product Owner (PO)

- **Responsibilities**: Holds responsibility for the product vision and evolution. Ensures the final product meets customer requirements by balancing business needs and market trends.

### 2. Business Analyst (BA)

- **Responsibilities**: Understands customer’s business processes and translates business needs into requirements. Bridges the gap between the customer and the development team.

### 3. Project Manager (PM)

- **Responsibilities**: Ensures the product or its parts are delivered on time and within budget. Manages and motivates the software development team.

### 4. UI/UX Designer

- **Responsibilities**: Transforms the product vision into user-friendly designs. Creates user journeys for the best user experience and highest conversion rates.

### 5. Software Architect

- **Responsibilities**: Designs the software architecture, ensuring scalability, performance, and alignment with business goals.

### 6. Software Developer

- **Responsibilities**: Implements the software solution based on the defined architecture and requirements.

### 7. Quality Assurance (QA) Engineer

- **Responsibilities**: Validates that the software functions as expected and meets all defined criteria. Performs manual or automated testing and reports bugs.

### 8. Test Automation Engineer

- **Responsibilities**: Develops automated tests to ensure the software's reliability and efficiency over time.

### 9. DevOps Engineer

- **Responsibilities**: Automates infrastructure deployment, manages CI/CD pipelines, and ensures the application runs smoothly in different environments.

## Database Design

The database schema is designed to support key Airbnb-like functionalities. The main entities and their relationships are outlined below:

### 1. Users

Stores data for guests and hosts.

- `id` (Primary Key)
- `name`
- `email` (unique)
- `password_hash`
- `is_host` (boolean)

**Relationships**:

- A user can list multiple properties (1-to-many).
- A user can make multiple bookings (1-to-many).
- A user can write multiple reviews (1-to-many).

---

### 2. Properties

Represents property listings created by hosts.

- `id` (Primary Key)
- `host_id` (Foreign Key to Users)
- `title`
- `location`
- `price_per_night`

**Relationships**:

- A property belongs to one host.
- A property can have multiple bookings.
- A property can have multiple reviews.

---

### 3. Bookings

Captures reservation data.

- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `check_in_date`
- `check_out_date`

**Relationships**:

- A booking is made by one user for one property.

---

### 4. Reviews

User feedback on a property.

- `id` (Primary Key)
- `user_id` (Foreign Key to Users)
- `property_id` (Foreign Key to Properties)
- `rating`
- `comment`

**Relationships**:

- A review is made by one user for one property.

---

### 5. Payments

Stores transaction details.

- `id` (Primary Key)
- `booking_id` (Foreign Key to Bookings)
- `payment_date`
- `amount`
- `payment_method`

**Relationships**:

- A payment is associated with a single booking.

## Feature Breakdown

This section outlines the main features that make up the Airbnb Clone backend and how each contributes to the functionality of the platform.

### 1. API Documentation

The backend APIs are documented using the **OpenAPI standard**, ensuring they are clear, consistent, and easy to integrate. The project supports both RESTful APIs via **Django REST Framework (DRF)** and flexible data querying through **GraphQL**, making it adaptable to various frontend needs.

### 2. User Authentication

Endpoints: `/users/`, `/users/{user_id}/`  
This feature allows users to register, log in, and manage their profiles. Secure authentication mechanisms ensure only authorized users can access and update their data.

### 3. Property Management

Endpoints: `/properties/`, `/properties/{property_id}/`  
Hosts can list properties, update details, view listings, or delete them. This system allows effective management of accommodation offerings on the platform.

### 4. Booking System

Endpoints: `/bookings/`, `/bookings/{booking_id}/`  
Users can make reservations for listed properties, as well as view and manage their bookings. It includes handling of check-in/check-out data to streamline the reservation lifecycle.

### 5. Payment Processing

Endpoints: `/payments/`  
Handles secure processing of payments related to bookings. It ensures transactions are recorded and linked to the appropriate user and booking data.

### 6. Review System

Endpoints: `/reviews/`, `/reviews/{review_id}/`  
Allows guests to leave feedback and rate properties after their stay. This builds trust in the platform and helps future users make informed decisions.
