---
title: "Advent Webcam"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by lizandeen on 2012-10-25
I have an Advent 9215 laptop with Ubuntu 12.04 installed. The problem is I cannot get the inbuilt webcam to work! (Cheese,Skype-no devices found,other alerts- no /dev/video0).Any suggestions? Thanks in advance, lizandeen

---

### Post by Hadaka on 2012-10-25
Hi, in terminal try..

```
lspci 
```  read through the list and see if you can get some information
to load a driver for it...

or...possibly

```
lsusb
``` it..may..be listed as a USB device

---

### Post by squakie on 2012-10-26
what does ls /dev/video* return?

---

