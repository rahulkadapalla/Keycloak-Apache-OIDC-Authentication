**Project Overview**
This project demonstrates the integration of Keycloak Identity and Access Management (IAM) with the Apache HTTP Server to implement centralized authentication and authorization using the OpenID Connect (OIDC) protocol.
The lab simulates a real-world enterprise identity architecture in which Keycloak acts as the Identity Provider (IdP) and Apache HTTP Server acts as the protected application/resource server. Authentication requests are handled by Keycloak, while Apache validates the authenticated user's identity through OIDC.
The project is designed as a practical IAM and cybersecurity laboratory for understanding how modern applications integrate with centralized Identity and Access Management platforms.
**Architecture**
                    ┌──────────────────────┐
                    │       End User       │
                    │      Web Browser     │
                    └──────────┬───────────┘
                               │
                               │ HTTPS / HTTP
                               ▼
                    ┌──────────────────────┐
                    │   Apache Web Server  │
                    │   Protected Resource │
                    │                      │
                    │  mod_auth_openidc    │
                    └──────────┬───────────┘
                               │
                               │ OpenID Connect
                               ▼
                    ┌──────────────────────┐
                    │       Keycloak       │
                    │   Identity Provider  │
                    │                      │
                    │  Realm: apache-lab   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   User / Identity    │
                    │     Management       │
                    └──────────────────────┘
                    
**Technologies Used**
Ubuntu Linux
Apache HTTP Server
Keycloak
Docker
OpenID Connect (OIDC)
OAuth 2.0

**Key Components**
**Keycloak**

Keycloak provides centralized identity management and authentication services. It is responsible for:

User management
Authentication
Realm management
Role and permission management
OpenID Connect configuration
Token issuance
Identity federation capabilities

**Apache HTTP Server**
Apache hosts the protected web application/resource and acts as the relying party for OpenID Connect authentication. The protected endpoint requires users to authenticate through Keycloak before access is granted.

mod_auth_openidc: mod_auth_openidc integrates Apache with an OpenID Connect Identity Provider. It handles functions such as:

OIDC authentication
Redirecting unauthenticated users to Keycloak
Processing OIDC responses
Validating authentication information
Establishing the authenticated user session
Passing identity information to the protected application

**Authentication Flow**
The user requests a protected resource on the Apache server.
Apache checks whether the user has an authenticated OIDC session.
If the user is not authenticated, Apache redirects the browser to Keycloak.
Keycloak authenticates the user.
Keycloak returns the OIDC authentication response.
Apache's mod_auth_openidc processes and validates the response.
An authenticated session is established.
The user is granted access to the protected resource.

**Project Environment**
The laboratory environment consists of:

Host Machine
     │
     └── VirtualBox
          │
          └── Ubuntu Linux
               │
               ├── Apache HTTP Server
               │
               ├── mod_auth_openidc
               │
               └── Docker
                    │
                    └── Keycloak

**Learning Objectives**

This project provides practical experience with:

Identity and Access Management
Authentication vs. authorization
OpenID Connect
OAuth 2.0 concepts
Identity Providers
Keycloak realms and clients
User and role management
Apache authentication modules
Linux system administration
Docker-based application deployment
Web server security
OIDC discovery and metadata
Troubleshooting authentication integrations

**Disclaimer**
This repository is a learning and laboratory project created to demonstrate practical Identity and Access Management concepts. Configuration values and architecture may differ from production enterprise deployments.

**Author**
Rahul Kadapalla

This project is part of a practical learning journey in Identity and Access Management, Cybersecurity, Linux Administration, and Enterprise Authentication.
