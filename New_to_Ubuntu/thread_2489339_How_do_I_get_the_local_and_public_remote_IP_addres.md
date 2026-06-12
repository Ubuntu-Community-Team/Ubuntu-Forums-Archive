---
title: "How do I get the local and public remote IP addresses of my ssh client?"
date: 2023-07-26
forum: New to Ubuntu
---

### Post by mohanjoy on 2023-07-26
Dear All,


I have many clients connecting to my Ubuntu server. I have checked the server's ssh auth log file, it is only showing the public IP address, but I need both IPs (the client's local private and public IP address). Please share your feedback on this. 

Thank you!!!!

---

### Post by SeijiSensei on 2023-07-26
I see connections over my private VPNs all the time like this:
```
Jul 26 15:48:35 www sshd[1263999]: Accepted password for xxx from 192.168.100.107 port 56334 ssh2
```

If you mean you have clients with public and private IPs and you want to see their private addresses when they are connected to the public interface, that's not possible for obvious security reasons.

If the clients are in the same local network as the server, force them to use the local address on the server, not its public address. Set up a separate internal DNS so that any references to the server point to its internal address. I have a DNS server for my local network with local IPs and another public server with different IPs for public access.

---

### Post by MAFoElffen on 2023-07-26
For ssh clients, I use
```

mafoelffen@opti-ubuntu:~$ w
 13:33:32 up 46 min,  2 users,  load average: 0.32, 0.24, 0.43
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
mafoelff tty7     :0               12:48   46:14   2:32   0.10s /usr/libexec/gn
mafoelff pts/1    10.0.0.170       13:33    3.00s  0.10s  0.02s w

```
If I want to see more about remote connections, then I use WireShark and set up filters to see what I want. But be advised that packet sniffer logs can get astronomical in size very quickly.

---

### Post by ActionParsnip on 2023-07-28
If your clients are connecting over the WWW to your system then you will only see their WAN IP, you won't see the LAN IP they have on the remote LAN (If I'm reading this correctly)

---

### Post by TheFu on 2023-07-28
On the LAN, I connect via port 22/tcp.
Over the internet, I connect through the router using a high-port. The router translates WAN:51077/tcp ---> LAN-Static IP:22

Through the router logs, I know if the connection is local or WAN-based.

Also, be certain to setup DenyHosts or Fail2ban to prevent brute force attacks and change the default 5 min lockout to 5 hours or 10 days after 3 failed attempts.  Anyone connecting over the WAN should be forced to use ssh-keys or ssh-certs, never passwords.  This can be enforced in the sshd_config file.  The manpage explains how.

Be certain you know about banned IPs. The current list on one of my public systems:

```
$ sudo fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed: 0
|  |- Total failed:     1050
|  `- File list:        /var/log/auth.log
`- Actions
   |- Currently banned: 85
   |- Total banned:     623
   `- Banned IP list:   8.222.243.55 167.172.99.211 47.236.25.159 142.93.143.112 122.254.95.77 35.131.26.18 103.164.221.210 1.34.70.148 8.222.155.135 43.155.170.163 43.155.154.61 128.199.24.55 39.65.61.222 148.72.209.121 93.43.231.181 159.89.196.121 218.148.197.203 5.135.179.178 165.154.8.112 43.155.95.31 92.27.140.155 157.7.79.190 208.109.34.15 139.59.251.146 190.103.240.4 43.134.189.31 103.161.17.229 23.126.62.36 87.255.193.50 141.147.180.0 179.43.142.20 195.19.97.157 8.208.94.4 34.100.249.182 128.199.151.172 96.69.13.140 103.189.234.25 152.32.208.150 47.252.112.224 128.199.194.183 163.172.61.168 8.222.171.238 181.228.116.172 51.38.187.93 202.131.106.238 164.90.140.95 43.134.185.27 52.140.61.101 190.181.27.5 42.3.8.136 103.78.143.130 144.172.73.39 47.236.30.19 43.156.76.89 112.161.214.48 67.216.221.59 139.59.93.234 41.33.118.94 8.219.72.121 47.243.99.113 14.140.81.58 92.205.108.168 8.219.239.105 43.131.248.141 157.245.137.143 178.128.172.9 178.62.237.10 176.52.10.84 8.219.160.68 130.93.73.45 47.242.255.198 8.219.253.192 8.222.197.249 47.250.45.206 182.72.142.62 47.90.201.65 92.255.165.123 167.71.120.146 8.222.135.228 142.93.62.53 8.219.156.53 47.89.254.138 8.217.152.154 95.215.153.66 189.51.122.94
```

YMMV.  If sshd listened on the default port, that list would be 100x larger.  As you can see, these are all public IPs. None are in the unroutable private address spaces.  With 600+ banned, I really need to get fail2ban to use **ipset** so all the banned IPs are just 1 firewall rule, not 600+ separate rules.  Too many rules can really slow down a filewall.  On some other systems, I have nearly 8000 banned subnets. Those use ipset for performance reasons.  Highly recommended, if the problem grows to that level for you.

---

