# CS305
CS305 module 8
This repository contains my Artemis Financial Vulnerability Assessment Report
---
Reflection
The client and its software requirements
Artemis Financial is a consulting company that builds individualized financial plans for its customers, covering savings, retirement, investments, and insurance. The company wanted to modernize its operations by using a RESTful web application to exchange data with customers. Its main concern was protecting that sensitive financial data. Artemis asked me to review its Spring Boot application, find security vulnerabilities, and recommend and put in place fixes. The company wanted to protect data in transit and to verify file integrity. It also wanted to make sure its dependencies were free of known vulnerabilities.
What I did well, and why secure coding matters
I worked through the code systematically, mapping each area to the vulnerability categories in the assessment. Those areas included input validation, APIs, cryptography, client/server communication, error handling, and code quality. I combined manual code review with an automated dependency scan, and this let me catch problems that one method alone would have missed.
Secure coding matters because vulnerabilities are far cheaper to prevent than to fix after a breach. For a financial company, one breach can mean stolen customer data, regulatory fines, legal liability, and lost trust that may never fully return. Software security protects a company's reputation, its customers, and its ability to keep operating. In that sense, it is a business asset and not just a technical detail.
What was challenging or helpful
The most challenging part was interpreting the dependency-check report. Many of the flagged CVEs were in third-party libraries, and some were false positives or not relevant to how the application used the library. I had to research each one to decide whether it was a real risk and how to address it, such as by upgrading versions or suppressing false positives with documentation. The vulnerability assessment process flowchart was very helpful. It gave me a structured way to approach a codebase I hadn't written.
Increasing layers of security
I added layers of security by:
Implementing a SHA-256 checksum to verify data integrity, choosing a modern algorithm over outdated ones like MD5 and SHA-1.
Generating a certificate with Java Keytool and configuring the application to use HTTPS, which encrypts data in transit.
Updating vulnerable dependencies identified by the scan.
In the future, I would keep using tools like OWASP Dependency-Check alongside manual review and threat modeling. I would also refer to resources like the OWASP Top 10 and the NIST National Vulnerability Database to rank vulnerabilities by severity and choose appropriate mitigations. I would pair those with a defense-in-depth approach so that no single control is the only line of protection.
Ensuring the code was functional and secure
After refactoring, I ran the application and confirmed it worked in the browser. The app served over HTTPS and displayed the correct checksum value. I then ran the dependency-check scan again and compared the results to the original report to confirm that my changes did not introduce new vulnerabilities. I also reviewed my own added code for issues like hard-coded values and improper error handling.
Useful resources, tools, and practices
OWASP Dependency-Check (Maven plugin) for static analysis of dependencies
Java Keytool for creating and managing certificates
OWASP Top 10 and the NIST NVD / CVE database for researching vulnerabilities
Java's `MessageDigest` class for secure hashing
Practices such as validating input, using current cryptographic algorithms, keeping dependencies updated, and rescanning after every change
What I would show future employers
I would show employers the completed report and the refactored code. Together they demonstrate that I can perform a vulnerability assessment on an existing application and turn findings into concrete fixes. They also show that I can configure secure communication with HTTPS and certificates, implement data-integrity checks, and verify my own work with static testing. Most importantly, they show that I approach software development with a security-first mindset, which is valuable on any development team.
