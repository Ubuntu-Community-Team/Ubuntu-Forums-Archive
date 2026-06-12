---
title: "XP Pro connecting to Ubuntu 10.04"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by rutdigger on 2012-02-17
Greetings:
 
Ubuntu newbie here. I have an XP pro workstation, and Ubuntu 10.04 running on another. Both are Dell Optiplex 380 workstations. Both are on the network, and able to see the internet. The Ubuntu pc is NOT on the local domain.
 
I installed telnet on Ubuntu, and reflections/Putty on the XP pc. I also added the XP pc to /etc/hosts.allow
 
I can use "TeamViewer" to connect from my XP pc to the Ubuntu PC. But I can't telnet, rlogin, or shh to the Ubuntu pc. ("connection refused by host").
 
Ideas?

---

### Post by 2F4U on 2012-02-17
SSH requires a SSH server running on Ubuntu. Did you install that? Also, are you able to ping the Ubuntu machine from the Windows computer. As far as I know, rlogin is disabled by default due to security considerations.

---

### Post by rutdigger on 2012-02-17
I can ping the ubuntu pc by IP address (not by hostname since ubuntu is not on the domain).
 
I ran sudo apt-get ssh, but still can't connect.  I thought that telnet could be the most insecure, but easiest to establish connection to a unix box.
 
Could port 23 be disabled?  If so, how would I find it?

---

### Post by cryptotheslow on 2012-02-17
As per here:
[https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)

I believe you need to:
```
sudo apt-get install openssh-server
```

Take a few minutes to read through the configuration steps on that page also.

---

