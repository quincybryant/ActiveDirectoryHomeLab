# Active Directory Home Lab – Domain Services & Group Policy

## 📌 Project Overview
This project demonstrates the deployment and configuration of an on-premises Active Directory environment using VMware Workstation Pro. The lab simulates a small enterprise domain with centralized authentication, organizational units, bulk user creation, Group Policy enforcement, and security validation.

---

## 🧰 Technologies Used
- VMware Workstation Pro
- Windows Server 2022 (Domain Controller)
- Windows 10 (Domain Client)
- Active Directory Domain Services (AD DS)
- DNS
- Group Policy Management
- PowerShell
- Event Viewer

---

## 🏗️ Lab Architecture

![VMware Lab Overview](screenshots/vmware-lab-overview/vmware-lab-overview.png)

*VMware Workstation Pro showing the Domain Controller (DC01) and domain-joined client (CLIENT01).*

- **DC01** – Windows Server 2022  
  - Active Directory Domain Services
  - DNS Server
  - Group Policy Management

- **CLIENT01** – Windows 10  
  - Domain-joined workstation

- **Domain Name:** `lab.local`
- ![VMware Lab Overview](screenshots/client/client01-domain-joined.png)

---

## 🔧 Configuration Steps

### 1️⃣ Domain Controller Setup
- Installed Windows Server 2022
- Promoted server to Domain Controller
- Created new forest: `lab.local`
- Verified AD DS and DNS functionality

![DC System Info](screenshots/domain-controller/dc01-system-about.png)
![DNS Configuration](screenshots/domain-controller/dc01_dns_config.png)

---

### 2️⃣ Organizational Units (OU)
- Created dedicated OUs for domain users
- Enabled deletion protection for OUs

![AD OUs](screenshots/domain-controller/dc01_ad_users_ou.png)

---

### 3️⃣ Bulk User Creation
- Created 50 domain users using PowerShell
- Users placed in the designated OU
- Verified creation using ADUC and PowerShell

![PowerShell User Creation](screenshots/users/powershell_user_creation.png)
![Users Created](screenshots/users/users_created_verification.png)

---

### 4️⃣ Domain Join (Client)
- Configured DNS to point to DC01
- Joined Windows 10 client to `lab.local`
- Verified secure domain trust

![Client System Info](screenshots/client/client01_system_about.png)
![Domain Join](screenshots/client/client01_domain_joined.png)
![Client DNS](screenshots/client/client01_dns_settings.png)

---

### 5️⃣ Group Policy Configuration
- Edited **Default Domain Policy** to enforce:
  - Password complexity
  - Minimum password length
  - Account lockout threshold and duration
- Policies applied domain-wide

![Password Policy](screenshots/gpo/password_policy.png)
![Account Lockout Policy](screenshots/gpo/account_lockout_policy.png)

---

### 6️⃣ Authentication Validation
- Successfully authenticated domain users on CLIENT01
- Verified identity using `whoami`
- Triggered account lockout through failed logon attempts

![WhoAmI](screenshots/client/client01_whoami.png)
![Ping DC](screenshots/networking/ping_dc01.png)

---

### 7️⃣ Security Event Logging
- Reviewed authentication logs on DC01
- Verified:
  - Event ID 4624 (successful logon)
  - Event ID 4625 (failed logon / lockout)

![Security Logs](screenshots/networking/nslookup_corp_local.png)

---

## 🔐 Security Controls Implemented
- Centralized domain authentication
- Password complexity enforcement
- Account lockout protection
- Audit logging of authentication events

---

## 🎯 Skills Demonstrated
- Active Directory administration
- Windows Server configuration
- Group Policy enforcement
- PowerShell automation
- Authentication troubleshooting
- Security event analysis

---

## 🚀 Future Improvements
- Fine-Grained Password Policies (FGPP)
- Additional Group Policy Objects (GPOs)
- SIEM integration (Splunk / Sentinel)
- Privileged Access Management (PAM)

---

## 🧠 Author
**Quincy Bryant**  
Entry-Level Cybersecurity / SOC Analyst Candidate
