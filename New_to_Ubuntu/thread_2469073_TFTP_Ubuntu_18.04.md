---
title: "TFTP Ubuntu 18.04"
date: 2021-11-18
forum: New to Ubuntu
---

### Post by timboz on 2021-11-18
[COLOR=#232629][FONT=-apple-system][FONT=var(--theme-question-body-font-family)][FONT=inherit]I have set up tftp server but having trouble testing / accessing from remote platforms[/FONT]
[FONT=inherit]Setup:[/FONT]
[/FONT]
```
[FONT=var(--theme-question-body-font-family)]sudo apt update;
sudo apt install -y tftpd-hpa;
sudo ufw allow tftp;
put files in
/var/lib/tftpboot[/FONT]

```[FONT=inherit]testing from the remote machine times out (firewall disabled)[/FONT]
```
tftp 109.228.38.69
tftp> get test.txt
Transfer timed out.
tftp>quit

```[FONT=inherit]While testing locally however on the actual server:[/FONT]
```
tftp 127.0.0.1
tftp> get test.txt
Received 11 bytes in 0.0 seconds
tftp>quit
           

```[FONT=inherit]The server is hosted on Virtual Private Server with [https://www.fasthosts.co.uk/](https://www.fasthosts.co.uk/)[/FONT]
[FONT=inherit]UFW status[/FONT]
[FONT=inherit]69/udp (v6) ALLOW Anywhere (v6)[/FONT]
[FONT=inherit]EDIT:[/FONT]
 sudo lsof -i:69 
[FONT=inherit]returns[/FONT]
```
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
in.tftpd 6874 root    4u  IPv4  90405      0t0  UDP *:tftp   
in.tftpd 6874 root    5u  IPv6  90406      0t0  UDP *:tftp  

```[FONT=inherit]cannot find much about in.tftp - is this a built in service ? Which is better to use and where are its files stored.[/FONT]

[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-11-18
Why TFTP? It's unsecure and awful. Is the no score to use SFTP?

---

### Post by The Cog on 2021-11-18
It is quite possible that the hosting provider blocks tftp - it's a protocol that's generally only used locally for booting hardware appliances.
My first step would be to verify that your tftp request packets are actually reaching the server. Use this line to monitor any UDP port 69 packets going over the internet interface (use the correct interface name of course):
```
sudo tcpdump -nnl -i eth0 udp
```
Be aware that the tftp server will choose a different port (not 69) to send its reply from. This can confuse some firewalls.
Looking at this trace will confirm whether the request is reaching the server, and whether the server is sending a response. This will guide where to investigate further.
Also, be aware that tftp has no authentication or encryption - the whole world will be able to read all the files on the server. If you really must use tftp over public internet, consider using firewall rules to limit access.

---

### Post by timboz on 2021-11-18
Thanks will look into this, yes its for reflashing hardware devices. They simply need a WAN IP address and a TFTP server with known readonly files

---

### Post by timboz on 2021-11-18
Fair comment, but see below for The Cog comment - it has its uses and security here is not an issue. Its service of specific set Admin placed files, readonly. Basically Trivial files.

---

