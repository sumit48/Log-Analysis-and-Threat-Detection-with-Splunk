# Log-Analysis-and-Threat-Detection-with-Splunk
Project:Log Analysis and Threat Detection with Splunk
---
Objective
---
To utilize Splunk for analyzing complex security logs, detecting advanced threats, and enhancing SOC operations through the creation of custom dashboards, alerts, and correlation rules.

Project Overview
---
This project demonstrates the configuration and use of Splunk to analyze and detect security threats from diverse log sources. The project covers:

- Log ingestion and normalization to ensure logs are usable in Splunk.
- Advanced SPL queries to identify anomalies and threats.
- Building custom dashboards for real-time monitoring.
- Conducting proactive threat hunting.
- Generating incident reports with actionable mitigation strategies.
- 
Steps
---
**1.Environment Setup**

- Install Splunk on a local system or cloud instance.
- Configure universal forwarders to collect data from servers or devices.
- Ensure logs are being sent to the Splunk instance for ingestion.
  
Commands:
```
bash

./splunk start
./splunk add forward-server <forwarder_ip>:<port>
./splunk add monitor /path/to/logs
```

**2. Log Ingestion and Normalization**

- Ingest logs from various sources like system logs, application logs, and network logs.
- Normalize logs using field extractions to ensure consistency in the data.
- 
Commands:
```
bash
index=_internal | stats count by sourcetype
rex field=_raw "pattern-to-extract-fields"
```

**3. Advanced SPL Queries**

- Use Splunk Processing Language (SPL) to detect anomalies and threats. Examples:
  - Detect brute force login attempts.
  - Identify suspicious IP addresses.
    
Commands:

```
spl

index=security sourcetype=linux_secure "failed password"
 | stats count by user, ip
 | where count > 5
```
```
spl

index=firewall | stats count by src_ip 
| where count > 1000
```

**4. Custom Dashboards**

- Create dashboards for real-time monitoring of threats.
- Use visualizations like bar charts, pie charts, and time series graphs.
  
Commands:

- Configure visualizations from the Splunk UI dashboard editor.
  
**5. Proactive Threat Hunting**

- Conduct searches for known Indicators of Compromise (IoCs).
- Investigate anomalies using correlation searches.
  
Commands:
```
spl

index=security | search "malicious activity"
| table _time, user, ip, action
```

**6. Incident Reporting**

- Generate detailed reports with findings, potential impacts, and mitigation strategies.
  
**Example Report:**

```
**Incident:** Brute Force Attack  
**Findings:** Detected 20 failed login attempts from IP 192.168.1.10.  
**Mitigation:** Block IP and enforce 2FA for user accounts.
```

Results
---
- Successfully configured Splunk to ingest and analyze logs from various sources.
- Detected threats such as brute force attempts and anomalous traffic.
- Created dashboards providing real-time insights into security events.
- Delivered incident reports with actionable strategies.
  
Conclusion
---
This project highlights the potential of Splunk as a powerful tool for SOC analysts to detect and mitigate advanced threats. By leveraging SPL queries, custom dashboards, and incident reporting, this project demonstrated how to enhance cybersecurity operations effectively.
