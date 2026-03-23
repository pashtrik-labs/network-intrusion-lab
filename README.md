#  Home Lab: Layer 2 Network Intrusion & Python IDS Simulation

##  Overview
This project is a physical Red vs. Blue team home lab designed to simulate an internal network intrusion and demonstrate transparent traffic monitoring. 

The lab features a custom-built Python Intrusion Detection System (IDS) running on a physical Layer 2 Ethernet bridge. This architecture allows the Blue Team node to invisibly intercept and analyze malicious traffic between the Attacker and the Victim without altering the network's logical topology or alerting the attacker.

##  Hardware Architecture & Roles
This environment was built using a three-node physical hardware setup to accurately replicate localized network traffic flow:

*  **Attacker Node (Red Team):** Kali Linux (Dell Latitude). Executed automated reconnaissance and custom Python-based SMB brute-force attacks.
*  **Detector Node (Blue Team):** Windows 10 (HP ZBook). Configured as a transparent Layer 2 Bridge running a custom Python packet sniffer (`ids_monitor.py`) and Wireshark.
*  **Victim Node (Target):** Windows 10 (Toshiba). Intentionally vulnerable host configured with Sysmon to track Event ID 4625 (Failed Logons) and Event ID 3 (Network Connections).

##  Simulation Lifecycle

**1. Network Reconnaissance**
* Automated discovery and port scanning utilizing `Nmap` to identify exposed SMB services (Port 445).

**2. Automated Exploitation**
* Deployed a custom Python script (`smb_brute.py`) leveraging the `Impacket` library to automate SMB authentication bypass and establish an interactive remote shell.

**3. Post-Exploitation & Exfiltration**
* Utilized native Linux tools (`smbclient`) to access administrative shares (C$), navigate the victim's file system, exfiltrate sensitive files, and prove persistent write-access.

**4. Invisible Threat Detection (IDS)**
* Successfully detected and logged the Nmap scans and inbound attack traffic in real-time using the custom Scapy-based Python IDS running on the bridged monitoring node.

##  Full Technical Documentation
> ** [Click Here to Read the Full Lab Execution & Architecture Report](Home_Lab/Home_Lab_Documentation.md)**

*(The full report includes detailed network topology diagrams, Layer 2 bridging configuration steps, raw Python exploit/IDS code, and execution screenshots).*

---

## ⚠️ Disclaimer
*This lab environment is strictly for educational purposes within an isolated and controlled network. The specific IP addresses, MAC addresses, and gateway details have been obfuscated to protect the integrity of the local network. Do not execute these tools against live or production environments.*
