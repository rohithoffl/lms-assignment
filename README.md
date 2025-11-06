# Full-Stack Learning Management System (LMS)

This is a complete full-stack web application for an online learning platform. It's built with a modern stack featuring React for the frontend and Spring Boot for the backend, with security managed by JWT (JSON Web Tokens).

The application allows:
* **Instructors** to sign up, log in, and manage their courses (create, update, delete).
* **Students** to sign up, log in, browse courses, enroll, and leave reviews.
* **Admins** to manage users and courses from a central dashboard.

---

## 🚀 Tech Stack

| Category | Technology |
| :--- | :--- |
| **Frontend** | React, React Router, Axios, Bootstrap |
| **Backend** | Java 17+, Spring Boot, Spring Security, Spring Data JPA |
| **Database** | MySQL |
| **Authentication** | JSON Web Tokens (JWT) |
| **Build Tools** | Maven (Backend), npm (Frontend) |

---

## ✨ Features

* **Authentication & Authorization:**
    * Secure JWT-based user signup and login.
    * Role-based access control for **STUDENT**, **INSTRUCTOR**, and **ADMIN** roles.
    * Protected routes for different user actions (e.g., only instructors can create courses).
* **Course Management (Instructor):**
    * Instructors can create new courses with a title, description, price, and thumbnail.
    * Instructors can edit and delete the courses they own.
* **Student Experience (Student):**
    * Students can browse all publicly available courses.
    * Students can enroll in courses.
    * Enrolled students can post reviews (1-5 star rating) and comments for a course.
    * Students can view a "My Courses" page showing their enrollments.
* **Admin Dashboard (Admin):**
    * View all users and courses in the system.
    * Ability to remove users or delete any course.

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed on your system:
* **Java JDK 17** or newer.
* **Node.js** (which includes npm).
* **MySQL Server** (running on its default port `3306`).
* A tool to run SQL commands (like **MySQL Workbench** or the command line).

---

## ⚙️ Setup & Installation

Follow these steps to get your local development environment running.

### 1. Backend (`lms-backend`)

1.  **Set up the Database:**
    * Open MySQL Workbench (or your preferred SQL tool).
    * Run the following command to create the database:
        ```sql
        CREATE DATABASE lms_db;
        ```

2.  **Configure the Backend:**
    * Navigate to the `lms-backend` folder.
    * Open `src/main/resources/application.properties`.
    * Update the `spring.datasource.password` to match your MySQL root password.
    * (Optional) Change the `app.jwt.secret` to a new random, long string for production.

3.  **Run the Backend:**
    * Open the `lms-backend` project in your Java IDE (like VS Code or IntelliJ).
    * Run the main application file (`LmsBackendApplication.java`).
    * The server will start on `http://localhost:8080`. It will automatically create all the necessary tables in your `lms_db` database.

### 2. Frontend (`lms-frontend` / `lms-assignment`)

1.  **Navigate to the Frontend:**
    * Open a new terminal.
    * `cd` into the frontend project folder (e.g., `cd lms-assignment`).

2.  **Install Dependencies:**
    * Run the following command to install all required libraries:
        ```bash
        npm install
        ```

3.  **Run the Frontend:**
    * Start the React development server:
        ```bash
        npm start
        ```
    * Your default browser will automatically open to `http://localhost:3000`.

You can now use the application! Try signing up as an **INSTRUCTOR** to create your first course.

---

## 🔌 API Endpoints

Here are the main API routes handled by the Spring Boot backend:

### Authentication

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/auth/signup` | Register a new user (Student or Instructor). |
| `POST` | `/api/auth/login` | Log in a user and receive a JWT. |

### Courses & Reviews

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/courses/public` | Get all courses (public). |
| `GET` | `/api/courses/{id}/reviews/public` | Get all reviews for a course (public). |
| `POST`| `/api/courses` | Create a new course (Instructor only). |
| `PUT` | `/api/courses/{id}` | Update an existing course (Instructor only). |
| `POST`| `/api/courses/{id}/enroll` | Enroll in a course (Student only). |
| `POST`| `/api/courses/{id}/reviews` | Post a review for a course (Student only). |

### Admin

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/admin/users` | Get a list of all users (Admin only). |
| `GET` | `/api/admin/courses` | Get a list of all courses (Admin only). |
| `DELETE` | `/api/admin/users/{id}` | Delete a user (Admin only). |
