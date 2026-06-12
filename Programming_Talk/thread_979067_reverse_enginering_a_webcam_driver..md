---
title: "reverse enginering a webcam driver."
date: 2008-11-11
forum: Programming Talk
---

### Post by wildman4god on 2008-11-11
I bought a cheap webcam from staples (because it was cheap) and it cam with windows drivers, but I can get it to work on ubuntu. I did some research and found it is made by a company called Sakar (they make a lot of cheapo products for other companies who don't have the means to produce products stamped with their logo) My question is, is there a way to take the windows driver and reverse enginer it so i can turn it into a linux driver. 

please note: I have almost no programing experiance and what little i do have is with webpages and basic stamp robots.

---

### Post by dwhitney67 on 2008-11-11
> **wildman4god said:**
> ...
is there a way to take the windows driver and reverse enginer it so i can turn it into a linux driver.

Yes there is; in fact many drivers that are used with Linux were developed in this fashion.  There is also the 'ndiswrapper' utility, but I have only heard of it being used for wireless drivers.

> **wildman4god said:**
> 
please note: I have almost no programing experiance and what little i do have is with webpages and basic stamp robots.
The lack of experience could impact your ability to develop a driver.  Nevertheless, this shouldn't stop you from trying.

---

### Post by loell on 2008-11-11
[one-man-writes-linux-drivers-for-235-usb-webcams]("http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams")
that is old news..

i'd imagine, this is close to 300 webcams now, but he started with gphoto then moving forward from there.

---

### Post by LaRoza on 2008-11-11
> **wildman4god said:**
> I bought a cheap webcam from staples (because it was cheap) and it cam with windows drivers, but I can get it to work on ubuntu. I did some research and found it is made by a company called Sakar (they make a lot of cheapo products for other companies who don't have the means to produce products stamped with their logo) My question is, is there a way to take the windows driver and reverse enginer it so i can turn it into a linux driver. 

please note: I have almost no programing experiance and what little i do have is with webpages and basic stamp robots.

No. You can't. You can try existing solutions, like ndiswrapper though.

Reverse engineering or disassembling the code of drivers is almost always explicitly against the EULA of the driver.

You can try to find a driver that will work with it though. Look at [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Zugzwang on 2008-11-12
> **LaRoza said:**
> Reverse engineering or disassembling the code of drivers is almost always explicitly against the EULA of the driver.


With regards to this, one should mention that some countries (unfortunately not the one that the OP seems to live in) have laws stating that you can always disassemble programs if your aim is to fix compatibility problems (which cannot be overwritten by any EULA). See [here]("http://http://en.wikipedia.org/wiki/Decompiler#Legality") for details.

---

### Post by loell on 2008-11-12
I would just like to add that you **can not** in any way, **use ndiswrapper ** for webcam windows drivers.

---

### Post by Sinkingships7 on 2008-11-12
And I would like to point out that reverse engineering is never illegal.

---

