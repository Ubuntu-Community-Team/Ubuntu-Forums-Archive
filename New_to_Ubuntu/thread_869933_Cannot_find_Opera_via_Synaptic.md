---
title: "Cannot find Opera via Synaptic"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by bbriley on 2008-07-25
[SIZE="3"][/SIZE]I cannot find Opera in Synaptic, and I would like to use it for the browser and for IMAP for my Gmail account.  I have the AMD 64 bit installation DVD from one of the disk distributors - On-Disk?

---

### Post by markjensen on 2008-07-25
I don't think you will find it there, because it is not open source.  It may also be likely that the license for Opera is not compatible with allowing free re-distribution.  (not sure on that second point)

---

### Post by Potatoj316 on 2008-07-25
maybe the opera site has a .deb download, I dont really know

EDIT: I just checked and they do have a .deb download, it is here
[http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.50b2&platform=Linux%20i386&local=y](http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.50b2&platform=Linux%20i386&local=y)

---

### Post by Seisen on 2008-07-25
Check that out it should help you.

[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

---

### Post by gimlithedwarf on 2008-07-25
you may need to enable the commerical repositories to get opera, which should be done automatically if you type ```
sudo apt-get install opera
```
to try and find it you may also want to try
```
apt-cache search opera
```

---

### Post by drs305 on 2008-07-25
You can go to the Opera web site and download a deb package for ubuntu. Download and click on the deb file to install. 

[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by bbriley on 2008-07-25
> **markjensen said:**
> I don't think you will find it there, because it is not open source.  It may also be likely that the license for Opera is not compatible with allowing free re-distribution.  (not sure on that second point)

[SIZE="2"]I will check at the Opera site.  Thanks.  Since I cannot get Opera from within Synaptic, that means I'll have to learn to install applications downloaded from the Internet.  You can tell that I have long been a Windows user (and DOS before that).

Thanks for the info.

Bob R.[/SIZE]

---

### Post by Elfy on 2008-07-25
You can get it from synaptic if you enable 3rd partner repos in software sources. The download from the opera site is a deb - doubleclick it - it will install.

The synaptic is an older version

---

### Post by niyonk on 2008-07-25
Don't you think it is always better to check the official sites themselves before asking these kinds of questions? :rolleyes:

But, then again...I understand you trust Synaptic only, which is  also good ;)

---

### Post by bbriley on 2008-07-25
> **forestpixie said:**
> You can get it from synaptic if you enable 3rd partner repos in software sources. The download from the opera site is a deb - doubleclick it - it will install.

The synaptic is an older version

[SIZE="2"]I did enable 3rd party installs in Synaptic - no luck.  However, all is well!  I went directly to the Opera site for Opera 9.51.  Opera detected that I have the AMD 64 bit Debian version and recommended a download file.  I downloaded it (thinking, "What do I do next?") and Ubuntu's install package detected the downloading file and "spoke up" - "Would you like me to install it?"  I of course answered, "Yes, sir!" and the installation went like a charm.  Now I can check my gmail IMAP using Opera M2 from within both Windows and Ubuntu 8.04.  Thank you, everyone!  I am amazed at this "auto install" feature in Ubuntu and the "auto detect" feature at Opera's website.  

Amazing!  Now if only we were as enlightened spiritually as we are advanced technologically!

Thanks again, everyone.

Bob R.[/SIZE]

---

