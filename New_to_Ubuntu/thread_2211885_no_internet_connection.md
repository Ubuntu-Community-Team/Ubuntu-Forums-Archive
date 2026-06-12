---
title: "no internet connection"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by aaron27 on 2014-03-18
hello,

I am fairly new at this ubuntu set up and running and have setup one machine previous to this. I am now in the process of setting another up, this is on a physcial machine. Ubuntu 12.04 is installed and everytime i try to run sudo apt-get update or similar the process fails. 
I have set the machine to run on a static ip address and it is configured to run on our network however i believe there is no connection out. please could someone assist? (in quite basic terms)

KR
Aaron

---

### Post by Vladlenin5000 on 2014-03-18
Ethernet or WiFi?

---

### Post by aaron27 on 2014-03-19
Ethernet

---

### Post by grahammechanical on 2014-03-19
Error messages? What we get as error messages when we run apt-get update/upgrade are clues to what the problem may be. Sometimes those error messages give advice on what to do to rectify the problem.

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
Make sure you are root (sudo -i) before running apt-get.  Do you have any trouble pinging something on the internet by name?  How about by IP address?  For example, ping [www.ubuntu.com](www.ubuntu.com) or ping 4.2.2.2.  And, like grahammechanical said, post any errors you get, it would help figure it out.

---

