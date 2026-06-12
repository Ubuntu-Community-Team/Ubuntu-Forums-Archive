---
title: "Closing ports?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by eaterofbrainz13 on 2008-05-27
okay so I used nmap to check the security of my wireless network and it said....
22/tcp open  ssh     OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.21
Uptime: 0.042 days (since Wed May 21 21:16:38 2008)
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=200 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux


Is having 22 ports open dangerous....and how can I close them?

---

### Post by wildpossum on 2008-05-27
By not running SSHd.
Simple turn it off System -> Services etc...

---

### Post by iaculallad on 2008-05-27
Or use the IPTable to manually close the port.

---

### Post by Monicker on 2008-05-27
You don't have 22 ports open.  It is only port 22 which is open; that is a single port.  Port 22 is for SSH (secure shell).  As long as you have a strong password for your user accounts( preferably with root login disabled), it is not a security problem.

See the following for more information about SSH: 

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by cdtech on 2008-05-27
Thats port 22 for ssh. If you login using "ssh hostname". I use the security of ssh, my port is open.

---

