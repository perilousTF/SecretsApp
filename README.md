# Secrets App 

A full-stack web application where users can register, authenticate securely, and submit secrets anonymously. 

> **Note:** This project was built as part of the coursework for **[The Complete Full-stack Web Development Bootcamp](https://www.udemy.com/course/the-complete-web-development-bootcamp/)** by Angela Yu on Udemy.

## 📋 Table of Contents
- [About](#about)
- [Features](#features)
- [Tech Stack](#tech-stack)
Xs- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Database Setup](#database-setup)
- [Environment Variables](#environment-variables)
- [Google OAuth Setup](#google-oauth-setup)

## 📖 About
The Secrets App allows users to create accounts securely using email/password or log in via Google. Once authenticated, users can submit secrets to the database. The application demonstrates the implementation of authentication levels, session management, and database interactions in a Node.js environment.

## ✨ Features
- **Authentication:**
  - Local Login (Email & Password)
  - Third-party OAuth 2.0 (Google Login)
- **Security:**
  - Passwords are hashed and salted using `bcrypt` before storage.
  - Session management using `express-session`.
  - Environment variables for sensitive data protection.
- **Database:** Persistent storage using PostgreSQL.
- **Templating:** Dynamic HTML rendering using EJS.

## 🛠 Tech Stack
- **Backend:** Node.js, Express.js
- **Database:** PostgreSQL
- **Authentication:** Passport.js (Local Strategy, Google OAuth2 Strategy)
- **Frontend:** EJS (Embedded JavaScript templating), CSS
- **Utilities:** Dotenv, Bcrypt, Body-Parser

## ⚙️ Prerequisites
Before running this project, ensure you have the following installed:
- [Node.js](https://nodejs.org/)
- [PostgreSQL](https://www.postgresql.org/)
- A Google Cloud Console Account (for OAuth)

## 🚀 Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/secrets-app.git
   cd secrets-app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up the Database** (See [Database Setup](#database-setup) below).

4. **Configure Environment Variables** (See [Environment Variables](#environment-variables) below).

5. **Run the server**
   ```bash
   node index.js
   # or if using nodemon
   nodemon index.js
   ```

6. **Visit the app**
   Open your browser and go to `http://localhost:3000`.

## 🗄 Database Setup
1. Open your PostgreSQL interface (PgAdmin or Command Line).
2. Create a new database named `secrets` (or whatever you prefer, just update the `.env` file).
3. Run the following SQL command to create the necessary table:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(100),
    secret TEXT
);
```

## Environment Variables
Create a `.env` file in the root directory of your project and add the following keys:

```env
# Database Config
PG_USER=your_postgres_username
PG_HOST=localhost
PG_DATABASE=your_database_name
PG_PASSWORD=your_postgresWy_password
PG_PORT=5432

# Session Config
SESSION_SECRET=your_long_random_string

# Google OAuth Config
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

## 🔑 Google OAuth Setup
To enable "Log In with Google":
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project.
3. Navigate to **APIs & Services > Credentials**.
4. Click **Create Credentials** > **OAuth client ID**.
5. Select **Web application**.
6. Set the **Authorized redirect URIs** to:
   `http://localhost:3000/auth/google/secrets`
7. Copy the **Client ID** and **Client Secret** and paste them into your `.env` file.

---
*Created by @perilousTF as part of the Udemy Web Development Bootcamp.*
```
