# Nmap Attack Project: Network Reconnaissance and Vulnerability Assessment

## Overview
This project demonstrates a **network reconnaissance attack** using **Nmap** from a Kali Linux machine (attacker) to an Ubuntu Linux machine (victim). The objective is to explore open ports, services, OS version, and vulnerabilities of the target machine.

---

## Network Topology
<pre lang="markdown">

                                                      [Router]
                                                      /      \
                                                     /        \
                                                    /          \    
                                                   /            \
                                            [Kali Server]    [Ubuntu Server]  
                                        [IP: 192.168.64.3]  [IP: 192.168.64.4]
                                                |                   |
                                               [---------------------]
                                                      Nmap Scan
</pre>

## Attacker (Kali Linux) Terminal Commands

### Step 1: Upgrade Kali System
```bash
sudo apt upgrade -y
```

### Step 2: Install Nmap, Wireshark, and Metasploit
```bash
sudo apt install -y nmap wireshark metasploit-framework
```

### Step 3: Find the IP Address of Kali
```bash
ip a
```

### Step 4: Run Nmap Aggressive Scan on Ubuntu (Victim)
```bash
nmap -A 192.168.64.4
```
**Target IP**: `192.168.64.4` (Ubuntu)  
**Flags Used**:  
- `-A`: Aggressive scan (includes OS detection, version detection, script scanning, and traceroute)

----

## Victim (Ubuntu Linux) Terminal Commands

### Step 1: Install OpenSSH, Apache, and vsftpd (for simulation)
```bash
sudo apt install openssh-server apache2 vsftpd
```

### Step 2: Check the IP Address of Ubuntu
```bash
ip a
```

### Step 3: Monitor the Network Traffic
```bash
ip.addr == 192.168.64.3 && tcp
```
**Filter Explanation: This will show all TCP traffic from the Kali machine `(IP: 192.168.64.3)`**

## Expected Results







                                            Victim Ubuntu reply to Attacker Kali


### On Kali (Attacker):

The Nmap scan will provide detailed information on:
- Open ports on the victim (Ubuntu) machine.
- Running services and their versions.
- Operating system details of the target system.
- Potential vulnerabilities, based on the services discovered.
- In the case of closed ports, the scan will return **TCP RST (Reset)** packets, indicating that the connection attempt was denied.

### On Ubuntu (Victim):

Using **Wireshark**, you will observe:
- **TCP packets** with the **SYN** and **RST flags**. These red-colored packets in Wireshark indicate closed ports and rejected connection attempts.
- The attacker (Kali) probes various ports, but Ubuntu responds with **TCP RST** (Reset) packets for those closed ports.
- **TCP RST packets** show up in red in Wireshark, signaling that the connection attempts were intentionally reset or blocked.

---

## Conclusion

This project demonstrates how **Nmap** can be used for **network reconnaissance**, particularly in identifying open ports and services on a target machine (Ubuntu in this case). The Nmap scan helps highlight potential vulnerabilities that could be exploited during penetration testing.

By observing the **red TCP RST packets** in **Wireshark**, you can see how closed ports respond to Nmap scans. These packets indicate that the connection attempts were blocked by the target machine, a normal outcome in security testing when no service is listening on those ports. This exercise illustrates a fundamental concept in **ethical hacking** and **penetration testing**, where scanning and analyzing traffic is crucial for identifying security weaknesses in networks.


                                           
