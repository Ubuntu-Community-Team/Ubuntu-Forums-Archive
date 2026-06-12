---
title: "O2 mobile broadband dongle not working"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by CAMEMBEAR on 2012-11-26
Using Ubuntu 12.04: Have o2 E160 mobile broadband dongle and using Eee PC netbook, but can't get dongle to work. Single flashing green and then blue lights, but dongle not listed when I hover over networks icon in tool bar. Netbook shows device as memory device in "Places",  "computer". Any ideas?

---

### Post by audiomick on 2012-11-26
I think you need to set it up.

First of all, just for interest's sake really, open a terminal with the dongle plugged in and do 
```
lsusb
```
This should tell exactly what it  really is. Chances are it is a Huawei. They make an awful lot of those things.

Anyway, right click on the network icon and look for an entry the is something like "connection settings" or "setup connection". Mine is in German, so I don't know what it is exactly in English. 

When you have that, look for a tab for "mobile broadband", look for "add" on there and go through the steps. It should just work.

---

### Post by audiomick on 2012-11-27
I just stumbled across this old post from me. There are some screenshots in there of the process.

[http://ubuntuforums.org/showpost.php?p=12056592&postcount=6]("http://ubuntuforums.org/showpost.php?p=12056592&postcount=6")

---

### Post by CAMEMBEAR on 2012-11-28
Thanks, but we have tried all these things already, but to no avail! An other ideas?

---

### Post by audiomick on 2012-11-28
No, I'm afraid I don't, but:

Can you see the dongle when you do lsusb?

What sort is it? If you post that here, maybe someone will be able to help. I mean that which you see via lsub more than than which o2 has in their brochure.

---

### Post by CAMEMBEAR on 2012-11-29
Yes,lsusb identifies dongle as:Huawei E230/E270/E870 HSDPA/HSUPA Modem

---

### Post by audiomick on 2012-11-29
Close, but not the same as mine, which works.


```
Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```

---

