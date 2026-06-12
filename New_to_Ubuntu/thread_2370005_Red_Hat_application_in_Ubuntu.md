---
title: "Red Hat application in Ubuntu"
date: 2017-08-29
forum: New to Ubuntu
---

### Post by nottery on 2017-08-29
Hello everyone, I'm new user of Linux. I want to install application developed for only Red Hat Linux. I have bin file, during instalation everything crush before start. My question is, there is some package witch I shoud install first, to install Red Hat app, or it's imposible?

---

### Post by vasa1 on 2017-08-29
See [https://ubuntuforums.org/showthread.php?t=2369919&p=13680578#post13680578](https://ubuntuforums.org/showthread.php?t=2369919&p=13680578#post13680578)

---

### Post by HermanAB on 2017-08-30
The best solution is to get the source code and recompile the program for your version of Ubuntu Linux.  

If you only have the binary, send a complaint to the original author to get the annoyance off your chest, then install a virtualizer like Virtualbox, install the required Redhat Linux version in that and then install your program, effectively running Linux on Linux.  It may sound inefficient, but you'll be pleasantly surprised with how well it works.

---

### Post by nottery on 2017-08-30
@HermanAB - author of program provide support only for RHE. 
If it could help: I used those commands in terminal:
```
sudo chmod +x ./filename.bin
sudo ./filename.bin
```
After this, instalation starts. Stuck on 0%
Link to screenshots:
[https://drive.google.com/open?id=0B9YG264X0mF0VGZzSWtFa05Kd3M](https://drive.google.com/open?id=0B9YG264X0mF0VGZzSWtFa05Kd3M)

---

### Post by mastablasta on 2017-08-31
it won't be compatible. use RHE (or perhaps CentOS or Fedora) to install it.

---

### Post by nottery on 2017-08-31
Thanks for help :) I will try Fedora, it's seems to be more user friendly than CentOS.

---

### Post by HermanAB on 2017-08-31
You need the EXACT version and distribution information, else it won't work.

So you got to talk to the developer and find out what exactly it will run on, then install that either natively or in a virtual machine.

---

