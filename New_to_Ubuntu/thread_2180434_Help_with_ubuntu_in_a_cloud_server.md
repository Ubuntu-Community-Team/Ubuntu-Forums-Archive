---
title: "Help with ubuntu in a cloud server"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by r0d01f0- on 2013-10-13
So i create this ubuntu 13.04 server on a cloud to host some html and mysql files, when i type*** sudo apt-get install tasksel*** i get this error:
 
> root@psbm-ptc01b07:~# sudo apt-get install tasksel
sudo: unable to resolve host psbm-ptc01b07.pt.lunacloud.local
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package tasksel
root@psbm-ptc01b07:~#

can i get some help configuring this server, im new to this business :/

---

### Post by richardeszes on 2013-10-13
The server cannot reach the host. The server have connection to internet? DNS is ok?

Please try this in terminal/console:
ping -c 5 google.com

---

### Post by r0d01f0- on 2013-10-14
yes it has, im acessing it from putty and my dns file is fine i even added 8.8.8.8 tring to fix it :/

> root@psbm-frc01b01:~# ping -c 5 google.com
PING google.com (94.20.252.55) 56(84) bytes of data.
64 bytes from cache.google.com (94.20.252.55): icmp_req=1 ttl=53 time=90.5 ms
64 bytes from cache.google.com (94.20.252.55): icmp_req=2 ttl=53 time=90.5 ms
64 bytes from cache.google.com (94.20.252.55): icmp_req=3 ttl=53 time=90.3 ms
64 bytes from cache.google.com (94.20.252.55): icmp_req=4 ttl=53 time=90.6 ms
64 bytes from cache.google.com (94.20.252.55): icmp_req=5 ttl=53 time=90.5 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 32423ms
rtt min/avg/max/mdev = 90.392/90.544/90.687/0.285 ms


---

### Post by r0d01f0- on 2013-10-14
ok i was able to instal tasksel after running **sudo apt-get uptade** but now i get this after chossing to instal lamp server on tasksel:

> debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog  based frontend cannot be used. at  /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Installing packages
-------------------

..100%

tasksel: aptitude failed (100)

every time i use sudo apt-get install...i get the line **sudo: unable to resolve host psbm-ptc01b07.pt.lunacloud.local** but it works fine i think.

---

