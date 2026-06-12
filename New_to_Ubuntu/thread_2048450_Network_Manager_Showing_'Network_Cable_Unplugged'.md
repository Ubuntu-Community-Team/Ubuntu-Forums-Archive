---
title: "Network Manager Showing 'Network Cable Unplugged'"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by smoegyu on 2012-08-26
I have just installed Ubuuntu 12.04 from CD. I have two problems and cannot connect to the internet from this computer.

First, Network Manager shows the ethernet cable as unplugged, even though it is plugged in.  I know the network connection works because I can swap the ethernet cable to another computer and connect to the internet. I believe the hardware itself is not the problem, but I'm not sure how to check this.

Second, the internal wireless card does not appear to be recognized at all. This is a bcm4311 card.

This is my first use of linux so I am not sure what hardware information you need to know. Thanks in advance for any help. I cannot copy/paste from the terminal because I have no internet access on the computer where Ubuntu is installed, but I will try to give what information I can.

nm-tool shows only eth0
Type: Wired
Driver: forcedeth
State: unavailable
Default: no
HW Address: 00:23:8B:6D:46:98

Capabilities:
Carrier Detect: yes

Wired Properties
Carrier: off

---

### Post by spiky001 on 2012-08-26
Hi  When you installed did you have the ethernet plugged in if not it might be easier to reinstall with cable plugged in

---

### Post by smoegyu on 2012-08-26
> **spiky001 said:**
> Hi  When you installed did you have the ethernet plugged in if not it might be easier to reinstall with cable plugged in

I did have it plugged in on install.  Unfortunately, it did not show that the computer was connected to the internet there either. I have tried re-installing, but that did not work either.

---

### Post by newb85 on 2012-08-26
> **smoegyu said:**
> I know the network connection works because I can swap the ethernet cable to another computer and connect to the internet. 

That doesn't necessarily mean you have the right kind of ethernet cable.  If the other machine has Tx/Rx autosense, it will work, even if you're using a crossover cable.  Make sure you're using a straight-through cable.

---

