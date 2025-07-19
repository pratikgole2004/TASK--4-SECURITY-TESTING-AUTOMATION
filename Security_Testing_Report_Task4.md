# 🔐 Security Testing Report — Task 4
**Internship Task:** Security Testing Automation  
**Tool Used:** OWASP ZAP  
**Target Web Application:** http://testphp.vulnweb.com  
**Test Date:** July 19, 2025  
**Tested By:** Pratik Gole  

---

## 📋 Objective
To perform automated security testing on a sample vulnerable web application using OWASP ZAP and document the discovered vulnerabilities along with appropriate remediation steps.

---

## 🧪 Scan Overview

- **Tool:** OWASP ZAP (Zed Attack Proxy)
- **Scan Type:** Passive and Active Scan
- **Mode:** Automated Attack Mode
- **Methodology:**
  - Crawled and analyzed the target application
  - Identified potential security flaws
  - Categorized by severity (Low, Medium, High, Critical)

---

## ⚠️ Vulnerability Report

| No. | Vulnerability              | Severity  | Description                                                                 | Recommended Remediation                                                    |
|-----|----------------------------|-----------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| 1   | **Cross-Site Scripting (XSS)** | High      | Malicious scripts can be injected and executed in browser context.          | Sanitize user input, use output encoding (e.g., DOMPurify), apply CSP headers. |
| 2   | **SQL Injection**          | Critical  | Application input is vulnerable to direct SQL command execution.            | Use parameterized queries and input validation. Avoid dynamic SQL queries.    |
| 3   | **Insecure Cookies**       | Medium    | Cookies are not set with `Secure`, `HttpOnly`, or `SameSite` attributes.    | Set cookies with security flags to prevent theft and unauthorized access.    |
| 4   | **Missing Security Headers** | Medium    | Headers like `Content-Security-Policy`, `X-Frame-Options` are missing.      | Add these headers to enforce client-side protections and framing control.    |
| 5   | **Information Disclosure** | Low       | Server reveals tech stack or debug messages in responses.                   | Suppress server version banners and use generic error pages.                |
| 6   | **Deprecated HTTP Methods** | Medium    | HTTP methods like `TRACE`, `OPTIONS` are exposed.                           | Disable unused methods in the server configuration (e.g., Apache/Nginx).     |

---

## 🔧 Remediation Steps

1. **Validate Inputs:**
   - Apply strict input validation on all user-controlled fields.
   - Use allow-lists rather than block-lists.

2. **Use Prepared Statements:**
   - Prevent SQL Injection by using ORMs or parameterized queries (e.g., `PreparedStatement` in Java).

3. **Implement Secure Headers:**
   - `Content-Security-Policy`
   - `X-Frame-Options: DENY`
   - `Strict-Transport-Security`

4. **Secure Cookies:**
   - Add flags: `HttpOnly`, `Secure`, `SameSite=Strict`

5. **Disable Verbose Error Messages:**
   - Customize error handling to prevent information leakage.
   - Turn off server signature/version disclosure.

6. **Server Hardening:**
   - Disable unnecessary HTTP methods.
   - Disable directory listing and default configurations.

---

## ✅ Final Remarks

The scan revealed both critical and medium severity vulnerabilities. Immediate focus should be given to high-risk issues like **SQL Injection** and **Cross-Site Scripting**. Medium and low severity issues should be addressed to improve the overall security posture.

---

## 📎 Attachments for Submission

- `Security_Test_Report_Task4.html` – OWASP ZAP Export
- `Security_Testing_Report_Task4.md` – This file


---

