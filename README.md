#  🏥 Hospital Management System

A full-stack web application for managing dental clinic appointments. Patients can book appointments, doctors can view and treat them, and admins can manage doctors, patients and appointment assignments.

- **Frontend:** React (JavaScript / JSX)
- **Backend:** Java, Spring Boot (REST API)
- **Security:** Spring Security with JWT authentication and role-based access
- **API Docs:** Swagger / OpenAPI

---

## ✨ Features

### 👤 Patient
- Register and log in
- Book a new appointment
- View own appointments and their status

### 🩺 Doctor
- Register (with profile image upload) and log in
- View appointments assigned to them
- Treat appointments and update their status

### 🛠️ Admin
- View all doctors, patients and appointments
- Assign appointments to doctors
- Manage the overall system

### 🌐 General
- Home page with carousel, About Us and Contact Us pages
- Role-based navigation (separate headers for Admin, Doctor, Patient and guests)
- JWT-secured endpoints with centralized exception handling

---

## 🧱 Tech Stack

| Layer      | Technology                                   |
|------------|----------------------------------------------|
| Frontend   | React, React Router, Axios/Fetch, CSS        |
| Backend    | Java, Spring Boot, Spring Data JPA           |
| Security   | Spring Security, JWT (`JwtUtil`, `JwtFilter`)|
| Database   | *(e.g. MySQL — update to match your config)* |
| API Docs   | Swagger (`SwaggerConfig`)                    |
| Testing    | JUnit (backend), Jest (frontend)             |

---

## 📁 Project Structure

### Backend (Spring Boot)

```
├── config/
│   ├── ApplicationConfig.java
│   ├── SecurityConfig.java
│   └── SwaggerConfig.java
├── controller/
│   ├── AppointmentController.java
│   ├── DoctorController.java
│   ├── PatientController.java
│   └── UserController.java
├── service/
│   ├── AppointmentService.java
│   ├── UserService.java
│   ├── StorageService.java
│   └── StorageServiceImpl.java      # file/image storage
├── dao/
│   ├── AppointmentDao.java
│   └── UserDao.java
├── entity/
│   ├── Appointment.java
│   └── User.java
├── dto/
│   ├── AppointmentResponseDto.java
│   ├── DoctorRegisterDto.java
│   ├── UpdateAppointmentRequest.java
│   ├── UserLoginRequest.java
│   ├── UserLoginResponse.java
│   ├── UserRoleResponse.java
│   ├── UsersResponseDto.java
│   └── CommanApiResponse.java
├── exception/
│   ├── AppointmentNotFoundException.java
│   ├── UserNotFoundException.java
│   └── MyControllerAdvice.java      # global exception handler
├── security/
│   ├── CustomUserDetailsService.java
│   ├── JwtFilter.java
│   └── JwtUtil.java
└── utility/
    ├── Constants.java
    ├── Helper.java
    └── RequestHeaderInterceptor.java
```

### Frontend (React)

```
src/
├── components/
│   ├── Header/  (NormalHeader, AdminHeader, DoctorHeader, PatientHeader, RoleNav)
│   ├── Footer.jsx
│   ├── Carousel.jsx
│   └── DoctorCard.jsx
├── pages/
│   ├── HomePage.jsx
│   ├── AboutUs.jsx
│   ├── ContactUs.jsx
│   ├── UserLoginForm.jsx
│   ├── UserRegister.jsx
│   ├── DoctorRegister.jsx
│   ├── AddAppointment.jsx
│   ├── AssignAppointment.jsx
│   ├── TreatAppointment.jsx
│   ├── ViewAllAppointment.jsx
│   ├── ViewAllDoctor.jsx
│   ├── ViewAllPatient.jsx
│   ├── ViewDoctorAppointment.jsx
│   └── ViewMyAppointment.jsx
├── App.js
├── App.css
├── index.js
├── index.css
└── reportWebVitals.js
```

> Folder names above are a suggested layout. Adjust them to match your actual repository.

---

## 🚀 Getting Started

### Prerequisites

- Java 17+ (or the version your project targets)
- Maven
- Node.js 16+ and npm
- A running database (e.g. MySQL)

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <your-repo-folder>
```

### 2. Run the backend

1. Create a database, for example:
   ```sql
   CREATE DATABASE dental_management;
   ```
2. Configure `src/main/resources/application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/dental_management
   spring.datasource.username=YOUR_DB_USERNAME
   spring.datasource.password=YOUR_DB_PASSWORD
   spring.jpa.hibernate.ddl-auto=update
   server.port=8080
   ```
3. Start the application:
   ```bash
   mvn spring-boot:run
   ```

The API runs at `http://localhost:8080`.

### 3. Run the frontend

```bash
cd frontend
npm install
npm start
```

The app opens at `http://localhost:3000`.

---

## 📖 API Documentation

Once the backend is running, open Swagger UI:

```
http://localhost:8080/swagger-ui/index.html
```

---

## 🔐 Authentication & Roles

The app uses JWT for stateless authentication.

1. A user logs in via the login endpoint and receives a token.
2. The frontend sends the token in the `Authorization: Bearer <token>` header.
3. `JwtFilter` validates the token on each request, and `SecurityConfig` restricts endpoints by role.

| Role    | Access                                                   |
|---------|----------------------------------------------------------|
| ADMIN   | Manage doctors, patients, appointments; assign doctors   |
| DOCTOR  | View assigned appointments and treat them                |
| PATIENT | Book and view own appointments                           |

---

## 🧪 Running Tests

```bash
# Backend
mvn test

# Frontend
npm test
```

---

## 🛣️ Possible Future Improvements

- Email/SMS appointment reminders
- Online payments and billing
- Patient medical history and prescriptions
- Doctor availability calendar

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---
