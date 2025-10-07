+++
hideMeta = true
draft = false
title = 'Troubleshooting DNS issues'
categories = ["Troubleshooting", "Networking", "DNS", "Cybersecurity"]
tags = ["DNS", "troubleshooting", "network", "connectivity", "guide", "commands", "diagnostics", "tools", "dns server", "ipconfig", "nslookup", "dig"]
+++
## Unable to resolve domain names

A common DNS issue is the inability to resolve domain names, which can result in websites being inaccessible despite an active Internet connection.

### Causes and solutions

-   **Incorrect DNS server configuration:** Ensure the DNS server addresses are correctly configured on client devices. To do so open a command prompt on the client device. Type nslookup <domain> and press **Enter**. Verify that the DNS server listed in the output is the correct one and is resolving domain names correctly. Note you have to enter the specific domain details, not type just "domain". For example, you could use nslookup google.com.
    
-   **DNS server downtime:** Verify that the DNS server is operational and reachable. Use the ping command to test connectivity to the DNS server by typing ping <DNS_server_IP_or_hostname> into the command prompt. If successful, you should see replies indicating that the server is reachable. Note that you have to enter the details of the specific DNS server, IP address, or hostname, not just type “DNS_server_IP_or_hostname”. For example, you can ping 8.8.8.8, which is Google's public DNS server IP address.
    
-   **Propagation delays:** Checking with DNS resolvers can help. To query a DNS record use nslookup <domain> to verify propagation status. nslookup will display the IP address(es) associated with the domain name, along with the DNS server(s) that provided the resolution. And then use dig <domain> to view detailed DNS query information. Changes to DNS records can take time to propagate, so patience is required.
    

### Commands

-   Use nslookup <domain> to query the DNS server for domain resolution.
    
-   Use dig <domain> for detailed DNS query information.
    
-   Use ping to test connectivity to the DNS server.
    

## DNS server not responding

When a DNS server does not respond, clients cannot resolve domain names, which can lead to a failure to access internet resources.

### Causes and solutions

-   **Server issues:** Restart the DNS server or check for software updates.
    
-   **Firewall settings:** Ensure firewalls are not blocking DNS traffic (port 53).
    
-   **Network issues:** Check the network path between clients and the DNS server for disruptions.
    

### Tools and commands

-   Use tracert <DNS server> if you are using your computer to trace the route and identify where the communication fails. Remember to enter the specific DNS server’s details, don't just type "DNS server".
    
-   Review DNS server logs for indications of failure. To do so, log into the server where the DNS service is running, and locate the directory where DNS server logs are stored. This can vary depending on the DNS server software and configuration.
    

## Incorrect DNS records

Incorrect DNS records can lead to domain resolution issues, such as pointing to the wrong IP address or non-existent domains.

### Causes and solutions

-   **Manual entry errors:** Double-check DNS entries for typos or incorrect values by using nslookup and dig.
    
-   **Expired records:** Ensure DNS records are up to date and refresh if necessary. To do so you should log into your DNS management console. This could be hosted by your domain registrar, DNS hosting provider, or within your organization's network infrastructure (e.g., Windows Server DNS Manager). Locate the section where DNS records are managed. This is often labeled as DNS Zone, DNS Records, or similar terminology. Scan through the list of DNS records to identify any records that may have expired or are due for renewal. Modify or renew expired DNS records as necessary.
    

### Tools and commands

-   Use nslookup and dig to verify DNS records.
    
-   Check the DNS management console for correct configurations.
    

## Using diagnostic utilities

### ipconfig

ipconfig is a command-line tool used primarily on Windows systems to display and manage network configuration settings. It provides detailed information about network interfaces, IP addresses, DNS settings, and more, which is essential for network troubleshooting and configuration management.

-   ipconfig /flushdns can be used to clear the DNS resolver cache.
    
-   ipconfig /all can be used to check DNS server settings on client devices.
    

### nslookup

nslookup is used to query DNS servers and obtain domain name information. It helps diagnose DNS resolution issues and verify DNS configurations. Common commands include:

-   nslookup <domain> to resolve a domain name to an IP address.
    
-   nslookup followed by server address to switch to a different DNS server for queries.
    

### dig

dig (Domain Information Groper) is a powerful tool for querying DNS servers and analyzing DNS responses. It provides more detailed output than nslookup. Common commands include:

-   dig <domain> for a basic DNS query.
    
-   dig +trace <domain> to perform a trace from the root servers to the authoritative server for the domain.
    
-   dig @<DNS server> <domain> to query a specific DNS server.
    

## Advanced troubleshooting techniques for DNS

These are essentially the same as the techniques used for DHCP troubleshooting but can also be applied to DNS issues.

### Network scanning

Network scanning helps identify all devices on the network, their assigned IP addresses, and potential conflicts.

-   Use nmap for comprehensive network scanning and host discovery.
    
-   Use arp -a to view ARP cache and identify IP assignments.
    

### Packet analysis

Packet analysis provides detailed insights into network traffic, helping identify DNS communication issues.

-   Use Wireshark for capturing and analyzing network packets.
    
-   Filter DNS traffic to isolate relevant packets for troubleshooting.
    

### Server log analysis

Analyzing server logs can reveal configuration errors, software bugs, or network issues impacting DNS services.

-   Review DNS server logs for query handling and resolution failures.
    

## Practical scenario: Fixing domain name resolution failures

Users report that they cannot access specific websites due to DNS resolution failures. These are the steps you should follow to resolve the problem.

1.  **Verify DNS configuration:** Use ipconfig /all to check DNS server settings on client devices.
    
2.  **Query DNS records:** Use nslookup <domain> and dig <domain> to check the DNS resolution.
    
3.  **Check DNS server status:** Ensure the DNS server is operational and reachable using ping and tracert if you are using your computer.
    
4.  **Update DNS records:** Verify and correct DNS records in the DNS management console.
    
5.  **Clear DNS cache:** Use ipconfig /flushdns to clear the DNS cache on client devices.
