# 🫘 pediNephro

> A comprehensive Pediatric Nephrology Information System built with a microservices architecture

---

## Overview

**pediNephro** is a specialized healthcare information system designed to support pediatric nephrology departments in managing the full care continuum — from patient registration and diagnostic assessments to post-transplant follow-up and inter-departmental coordination.

The platform centralizes clinical workflows, streamlines communication between care teams, and provides real-time dashboards to support data-driven decision-making in pediatric kidney care.

---

## Features

The system is organized into **10 functional modules**:

| Module | Description |
|--------|-------------|
| 🔐 **Module 1** | Identity and Authentication Management |
| 🧒 **Module 2** | Patient Records and Medical Profiles |
| 🧪 **Module 3** | Biological Assessments and Laboratory Tests |
| 💊 **Module 4** | Treatment and Prescription Management |
| 🏥 **Module 5** | Hospitalizations and Care Episodes |
| 🖼️ **Module 6** | Medical Imaging and Documentation |
| 📈 **Module 7** | Vital Signs and Monitoring |
| 🫘 **Module 8** | Post-Kidney Transplant Follow-up |
| 🔗 **Module 9** | Inter-departmental Coordination and Communication |
| 📊 **Module 10** | Dashboards and Analytical Reports |

---

## Tech Stack

### Frontend

- **Angular** — Single-page application framework for building the user interface
- **Angular Router** — Client-side navigation and routing between modules
- **Angular HttpClient** — REST API communication with backend microservices
- **Bootstrap / Angular Material** — UI component library and responsive design

### Backend

- **Spring Boot** — Core framework for each microservice
- **Spring Security + JWT** — Authentication and role-based access control
- **Spring Data JPA + Hibernate** — ORM for database interactions
- **Spring Cloud Netflix Eureka** — Service discovery and registration
- **Spring Cloud Gateway** — API Gateway for routing, load balancing, and cross-cutting concerns
- **MySQL / PostgreSQL** — Relational database per microservice
- **Maven** — Dependency management and build tool

---

## Architecture

pediNephro follows a **microservices architecture** where each functional module is deployed as an independent service.

```
                        ┌─────────────────────┐
                        │     Angular Frontend  │
                        └────────┬────────────┘
                                 │ HTTP / REST
                        ┌────────▼────────────┐
                        │    API Gateway       │
                        │  (Spring Cloud GW)   │
                        └────────┬────────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
   ┌──────────▼──────┐  ┌───────▼──────┐  ┌───────▼──────┐
   │  Auth Service   │  │ Patient Svc  │  │  Lab Service  │
   │   (Module 1)    │  │  (Module 2)  │  │  (Module 3)   │
   └─────────────────┘  └─────────────┘  └──────────────┘
              │                  │                  │
   ┌──────────▼──────┐  ┌───────▼──────┐  ┌───────▼──────┐
   │ Treatment Svc   │  │Hospital Svc  │  │ Imaging Svc   │
   │   (Module 4)    │  │  (Module 5)  │  │  (Module 6)   │
   └─────────────────┘  └─────────────┘  └──────────────┘
              │                  │                  │
   ┌──────────▼──────┐  ┌───────▼──────┐  ┌───────▼──────┐
   │  Vitals Svc     │  │Transplant Svc│  │  Coord. Svc   │
   │   (Module 7)    │  │  (Module 8)  │  │  (Module 9)   │
   └─────────────────┘  └─────────────┘  └──────────────┘
                                 │
                        ┌────────▼────────────┐
                        │   Analytics Svc      │
                        │     (Module 10)      │
                        └─────────────────────┘
                                 │
                        ┌────────▼────────────┐
                        │   Eureka Server      │
                        │ (Service Discovery)  │
                        └─────────────────────┘
```

Each microservice:
- Runs independently on its own port
- Registers with the **Eureka Discovery Server**
- Is exposed to the frontend exclusively through the **API Gateway**
- Manages its own database schema

---

## Contributors

| Name | Module(s) | Role |
|------|-----------|------|
| Souhir Zitoun | Module 1 – Identity & Auth | Developer |
| Souhir Zitoun | Module 2 – Patient Records | Developer |
| Dhia Dridi | Module 3 – Laboratory Tests | Developer |
| Dhia Dridi | Module 4 – Treatment & Prescriptions | Developer |
| Alaa Diden | Module 5 – Hospitalizations | Developer |
| Alaa Diden | Module 6 – Medical Imaging | Developer |
| Med Aziz Turki | Module 7 – Vital Signs | Developer |
| Med Aziz Turki | Module 8 – Post-Transplant Follow-up | Developer |
| Brahim Boukadida | Module 9 – Coordination & Communication | Developer |
| Brahim Boukadida | Module 10 – Dashboards & Analytics | Developer |

> 📝 *Contributors: please update this table with your full names and GitHub profiles.*

---

## Academic Context

This project was developed as part of the **Software Engineering curriculum** at:

> 🎓 **ESPRIT — École Supérieure Privée d'Ingénierie et de Technologies**
> Ariana, Tunisia

It was realized as an end-of-semester engineering project, applying enterprise-grade software architecture patterns in a real-world healthcare domain. The project demonstrates proficiency in distributed systems design, RESTful API development, and modern frontend engineering.

---

## Getting Started

### Prerequisites

Make sure the following are installed on your machine:

- Java 17+
- Node.js 18+ & npm
- Angular CLI (`npm install -g @angular/cli`)
- Maven 3.8+
- MySQL or PostgreSQL
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/pediNephro/[repoName].git
cd [repoName]
```

### 2. Start the Eureka Discovery Server

```bash
cd eureka-server
mvn spring-boot:run
```

> Eureka dashboard available at: `http://localhost:8761`

### 3. Start the API Gateway

```bash
cd api-gateway
mvn spring-boot:run
```

> Gateway runs on: `http://localhost:8080`

### 4. Start the Microservices

Each module is a standalone Spring Boot application. Navigate to each service directory and run:

```bash
mvn spring-boot:run
```

> Ensure each service has its database configured in `application.properties` or `application.yml`.

### 5. Start the Angular Frontend

```bash
cd frontend
npm install
ng serve
```

> Frontend available at: `http://localhost:4200`

---

## Acknowledgments

- **ESPRIT School of Engineering** for providing the academic framework and resources
- The **Spring Cloud** and **Angular** open-source communities
- Our supervising professors and project coordinators for their guidance throughout the development cycle

---

<p align="center">
  Made with ❤️ by the pediNephro team · ESPRIT · 2024–2025
</p>
