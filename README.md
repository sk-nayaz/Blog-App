MERN Blog Application

A full-stack blog platform built using the MERN stack (MongoDB, Express, React, Node.js) with secure social authentication powered by Clerk.

The application supports role-based access control, allowing users to interact with blog posts while enabling authors to create and manage content.

🚀 Features

Social authentication (Google, GitHub, LinkedIn, etc.)

Secure session management using Clerk

Role-based dashboards

Blog creation and management

Comment system for users

Modern React frontend with protected routes

🔐 Social Login Flow

The authentication flow is handled through Clerk, enabling secure and seamless login.

Step 1 — User Initiates Login

When a user clicks the Sign In button:

The React application sends a request to Clerk.

Clerk redirects authentication to social providers such as:

Google

GitHub

LinkedIn

Step 2 — Credential Verification

The selected provider verifies the user's credentials.

After successful verification:

The provider sends an ID token (JWT) back to Clerk.

Step 3 — Session Creation

Clerk then:

Creates a secure user session

Provides authentication data to the React app using hooks such as:

useAuth()
useUser()

At this point, the social login process is successfully completed.

👤 Role-Based Navigation

After authentication, the React application determines where to navigate the user based on their role.

Possible destinations:

UserDashboard

AuthorDashboard

The navigation depends on the role property stored in the database.

🧠 User Role Handling
1️⃣ Header Component

The Header component retrieves the user object from the database.

2️⃣ First-Time Login

If the user logs in for the first time:

No user record exists in the database.

The application redirects the user to the RoleSelection component.

The user selects a role:

User

Author

After selection:

A new user record is created in the database with the selected role.

3️⃣ Existing User Login

If the user already exists in the database:

The application automatically redirects the user based on their role:

User → UserDashboard

Author → AuthorDashboard

This completes the User or Author account initialization process.

✍️ Author Capabilities

Authors have full control over blog content.

They can:

Create new blog posts

Read all blog posts

Update existing blog posts

Delete blog posts

👀 User Capabilities

Regular users can interact with blog content.

They can:

Read blog posts

Write comments on blog posts

🛠 Tech Stack

Frontend

React

Clerk Authentication

Backend

Node.js

Express.js

Database

MongoDB
