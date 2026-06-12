---
title: "just loaded 12.04 on to my acer aspire revo"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by blake7 on 2012-05-02
and it does not feel right
chrome will not expand when i drag it to the top i gettign wifo problem eta

is there any way to test if it has loaded on my system ok or does this compter just not work with 12.04???

iam also getting crash reports i dont know how to copy and past them or whree there are stored so you can see them?


thank you

---

### Post by NikTh on 2012-05-02
> **blake7 said:**
> and it does not feel right
chrome will not expand when i drag it to the top i gettign wifo problem eta

is there any way to test if it has loaded on my system ok or does this compter just not work with 12.04???

iam also getting crash reports i dont know how to copy and past them or whree there are stored so you can see them?


thank you


Hi , 
for crashes you must hit the expanding button to see what program exactly crashed. 
For example : i was getting crashes about Xorg . I tried ```
sudo dpkg --configure -a
``` and ```
sudo dpkg-reconfigure xorg xorg-common xserver-xorg
``` and crashes stopped.
You must allow to program to collect info from your pc-O.S to complete the report. Sometimes it asks for your permission to do that(asks for your password).

---

