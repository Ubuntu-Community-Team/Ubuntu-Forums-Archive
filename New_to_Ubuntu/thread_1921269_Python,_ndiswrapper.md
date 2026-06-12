---
title: "Python, ndiswrapper"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by xweetok59 on 2012-02-06
Okay, so I borked my windows XP and I couldn't boot it anymore. I just got a black screen. I remember i got ubuntu 11.10 on my USB, so i decided i would just install ubuntu on it. I installed ubuntu now, but this thing is driving me crazy.

I have a 3m internet cable and I have to sit next to my router to be able to surf on the internet. I discovered i need this program called ndiswrapper to install drivers from xp on ubuntu. So I want to install  wireless internet and graphics drivers ofcourse.

I followed some tutorial and it said the ndiswrapper should be in the installation place thing, being in my usb. I found it. Installed the ndiswrapper common and utils. But I got some problems while trying to install GTK.

The problem is, when I try to install it I get the error: python-glade2.

I googled a bit and downloaded it. When i tried to install it I got: Python-numpy2 or something, if i rememer correctly.

And when i tried to install numpy, i got python <2.7 (but  have python > 2.7.2 installed.

Now i see the software center doesnt open too (hope reboot fixes it).

Please somebody help me!

---

### Post by TeoBigusGeekus on 2012-02-06
Have you looked in "Additional Drivers" to see if there's a proprietary driver for your wireless chip?

---

### Post by xweetok59 on 2012-02-06
Yes, it isn't in there.

I managed to download the ndiswrapper. I downloaded the drivers, installed them, but it says

netathw

Hardware present: No.

I'm pretty sure it isnt the wrong driver, because i downloaded it from the official website =/. What am i supposed to do now...

---

### Post by wildmanne39 on 2012-02-06
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

