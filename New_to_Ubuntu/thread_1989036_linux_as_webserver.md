---
title: "linux as webserver"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by newbie61040 on 2012-05-28
Hi I have a question.
I will rent in the next times a vserver and i looked tuts on youtube how I can install php, apache etc... and I checked it.

My question is become I the FTP Details from my Hosting Company or I must create this self?

---

### Post by roton on 2012-05-28
> **newbie61040 said:**
> Hi I have a question.
I will rent in the next times a vserver and i looked tuts on youtube how I can install php, apache etc... and I checked it.

My question is become I the FTP Details from my Hosting Company or I must create this self?

You'll get the ssh and ftp details from the vps company. You can then ssh to it and install anything you like.

---

### Post by codemaniac on 2012-05-28
Once you get the ssh credentials from your VPS provider ypu can install the FTP server on it.
All you need is to install the **vsftpd **package .
```
sudo apt-get install vsftpd
```
[https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html)

---

### Post by d4m1r on 2012-05-28
Should this not be moved to the server section?

---

### Post by newbie61040 on 2012-05-28
Thanks, roton and codemaniac.

---

