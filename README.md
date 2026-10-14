# Open-Source SOC Lab — SIEM, SOAR & Threat Intelligence

**Author:** Thamer Bousbia  
**Academic institution:** TEK-UP — École Supérieure Privée d’Ingénierie et de Technologie  
**Host organization:** Société Tunisienne de Banque (STB)  
**Project:** Mise en place d’une solution SOC open source pour la détection et la gestion des incidents de sécurité

---

## 1. Project Overview

This project focuses on the design, deployment, and validation of a virtualized Security Operations Center (SOC) using open-source security tools.

The laboratory was developed with VMware Workstation to study how security events can be collected from multiple systems, analyzed by a SIEM, transformed into incidents, and enriched with threat intelligence.

The project combines network security, endpoint monitoring, web application security testing, incident management, and controlled active response in an isolated environment.

**Important:** The laboratory is an educational test environment. It does not reproduce the production information system of STB and does not use real customer data.

## 2. Objectives

- Deploy a virtualized and isolated SOC laboratory.
- Configure network filtering and traffic control using pfSense.
- Centralize Linux, Windows, Apache, and firewall logs in Wazuh.
- Detect suspicious authentication attempts, file changes, network reconnaissance, and web security events.
- Integrate TheHive for alert and incident management.
- Use Cortex and MISP to investigate and enrich observables.
- Test a controlled firewall-based active response.
- Document the results, technical limitations, and security recommendations.

## 3. Architecture

The laboratory uses a private network with the subnet `192.168.100.0/24`, configured through VMware Workstation.

### Main components

| Component | Role |
|---|---|
| pfSense | Firewall, routing, NAT, network filtering, and syslog forwarding |
| Wazuh | SIEM, log collection, correlation, alerting, FIM, and vulnerability detection |
| Kali Linux | Source of authorized security testing scenarios |
| Ubuntu Server / DVWA | Linux target and deliberately vulnerable web application |
| Windows Server 2019 | Active Directory, Windows security events, RDP testing, and FIM |
| TheHive | Security alert and incident management |
| Cortex | Observable analysis and enrichment |
| MISP | Threat intelligence and indicator sharing |

### Data flow

1. Kali Linux generates a controlled test against a laboratory target.
2. The target or pfSense produces security logs.
3. Wazuh agents or syslog forward the events to the Wazuh Manager.
4. Wazuh decodes and evaluates the events using detection rules.
5. Qualified alerts are forwarded to TheHive according to the configured severity threshold.
6. The analyst investigates the alert and extracts relevant observables.
7. Cortex and MISP provide additional analysis and threat context.
8. The analyst evaluates the evidence and determines the appropriate response.

## 4. Technologies Used

- **Virtualization:** VMware Workstation
- **Firewall:** pfSense
- **SIEM / HIDS:** Wazuh
- **Security testing:** Kali Linux, Nmap, Hydra, Ncrack
- **Web security testing:** DVWA, OWASP Top 10, curl, browser-based testing
- **Incident management:** TheHive
- **Observable analysis:** Cortex
- **Threat intelligence:** MISP
- **Network analysis:** Wireshark
- **Endpoint monitoring:** Wazuh agents, File Integrity Monitoring (FIM)
- **Operating systems:** Ubuntu Server 22.04 LTS, Windows Server 2019

## 5. Security Scenarios

The report documents the following laboratory tests:

- **SSH authentication:** Controlled brute-force scenario and detection of failed login attempts.
- **RDP authentication:** Monitoring of Windows authentication events.
- **File Integrity Monitoring:** Detection of changes to monitored files.
- **Vulnerability detection:** Review of vulnerability findings reported by Wazuh.
- **Network reconnaissance:** Nmap scanning against laboratory targets and pfSense.
- **Web application security:** Controlled tests based on the OWASP Top 10 categories using DVWA.
- **Active response:** Configuration and validation of a temporary firewall-based blocking action.

All offensive tests are restricted to the isolated laboratory and authorized targets.

## 6. Results and Validation

The documented tests demonstrate several capabilities of the laboratory:

- Collection of Linux, Windows, Apache, and pfSense security events.
- Detection of failed SSH and RDP authentication attempts.
- Visibility into file integrity changes and vulnerability findings.
- Generation of alerts associated with network reconnaissance and web security tests.
- Forwarding of qualified alerts to TheHive.
- Investigation and enrichment of observables using Cortex and MISP.
- Validation of a controlled `firewall-drop` active response.

The interpretation of results remains evidence-based. A detection alert does not automatically prove that an attack succeeded, and an integration is considered validated only when the corresponding test evidence supports that conclusion.

## 7. Security Considerations

- Keep DVWA and all offensive testing tools inside the isolated laboratory.
- Do not expose deliberately vulnerable services to the public Internet.
- Never publish passwords, API keys, tokens, or sensitive configuration files.
- Revoke and replace any API keys accidentally exposed during demonstrations.
- Review active-response rules carefully to avoid blocking legitimate systems.
- Use snapshots and backups before making major laboratory changes.
- Preserve logs and timestamps to support incident investigation.

## 8. Repository Contents

The repository is intended to contain the project documentation and demonstration evidence:

- `README.md` — Project overview and documentation.
- `report/` — Final project report in PDF format.
- `screenshots/` — Evidence of the architecture, dashboards, alerts, tests, and integrations.
- `demo/` — Demonstration video, when included.
- `architecture/` — SOC architecture diagram, when included.

Actual filenames may differ depending on the uploaded files.

## 9. Limitations and Future Improvements

Potential improvements include:

- Expanding and tuning detection rules to reduce false positives.
- Improving the traceability of each test from the original log to the final incident.
- Strengthening integration monitoring and error handling.
- Refining alert prioritization and incident-response procedures.
- Improving the documentation and reproducibility of the laboratory.
- Reviewing access controls, secret management, log retention, and recovery procedures.

## 10. Conclusion

This project provided practical experience in building and evaluating an open-source SOC laboratory. It brought together network filtering, security event collection, detection, incident management, and threat intelligence in a controlled virtual environment.

The main outcome is a documented security monitoring workflow that can be further improved through additional testing, better detection rules, and more complete incident-response procedures.

---

**Author:** Thamer Bousbia  
**Focus areas:** SOC Operations · SIEM · SOAR · Network Security · Threat Intelligence · Incident Response
