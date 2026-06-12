---
title: "trouble with wireless connection"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by munezz on 2012-03-23
my laptop works fine with wired internet connection but i just can't get my wireless connection work. Well my laptop detects the USB but doesn't seem to get the internet connection. :confused:

---

### Post by Daveth on 2012-03-23
Hi.
Can you give us a bit more information about the make of your laptop and the version of Ubuntu you are using? Bit tricky on what you have written so far.

---

### Post by wildmanne39 on 2012-03-23
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time with your wireless plugged in, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by munezz on 2012-03-24
> **Daveth said:**
> Hi.
Can you give us a bit more information about the make of your laptop and the version of Ubuntu you are using? Bit tricky on what you have written so far.

CPU
    Intel Mobile Core 2 Duo T7100  @ 1.80GHz   
    Merom 65nm Technology
RAM
    2.00 GB Dual-Channel DDR2 @ 332MHz (5-5-5-15)
Motherboard
    Sony Corporation VAIO (CR VGN-CR12GH/B)    
and i'm using Ubuntu 11.10

Thanxx

---

### Post by vivekpandey1991 on 2012-03-24
first you need to check whether wireless drivers are activated or not... go to system->admin->additional drivers.. if not activated .. activate(install)the wireless drivers and then see if you can connect or not

---

