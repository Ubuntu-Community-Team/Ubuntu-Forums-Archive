---
title: "Wireless adaptor problems"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by pablodamon on 2008-05-24
can not get internet,no device manager? help!

---

### Post by tamoneya on 2008-05-24
we are going to need some more details: Wireless or wired?  What is the chipset for your internet.  If you dont know this post the result of ```
lspci
```Also try posting ```
ifconfig
```That will help us get familiarized with your networking setup.

As for device manager you can install restricted drivers through system -> administration -> hardware drivers

---

### Post by pablodamon on 2008-05-24
need help
please
have just installed 8.04
using xp laptop to chat
new to linux
ubuntu doesnot recognise my  wireless adaptor
can not find device mgr

---

### Post by HermanAB on 2008-05-24
OK, cool.  You need a working network connection to proceed, so you have to plug in a Cat5 wire and use that till you got wireless to work.

You may have to use ndiswrapper with a Windows XP device driver for the wireless connection.  Go and read here: [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Cheers,

Herman

---

### Post by pablodamon on 2008-05-24
wireless only here  now what?

---

### Post by dstin1 on 2008-05-24
> **pablodamon said:**
> wireless only here  now what?

down load the file with xp copy to cd or usb stick then boot linux and install from the cd or usb.

here is a guide on how to install anything

[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

