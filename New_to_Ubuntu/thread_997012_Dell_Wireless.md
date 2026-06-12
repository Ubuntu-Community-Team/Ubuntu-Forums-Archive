---
title: "Dell Wireless"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-11-29
HI all, 

I am trying to convert my friend to Linux he has a dell inspiron 1525 we want to dual boot with Vista and Ubuntu version 8.10 or 8.4.01 we have live CD's of both the 8.10 will not allow the wireless to work the 8.4.01 will not even boot 

Do you know what the problem is with 8.10 and this machine ? 

We have tried 8.4.01 because I believe the wireless works but it would not even boot.

Any ideas ?

---

### Post by mikewhatever on 2008-11-29
Regarding 8.10, can you boot from the cd and post the outputs of the following commands:
sudo lshw -C network
ifconfig
dmesg | grep wlan0

Regarding 8.04. Did you check the cd for errors? At what stage does the booting stop?

---

### Post by Oliver.BS on 2008-11-29
> **mikewhatever said:**
> Regarding 8.10, can you boot from the cd and post the outputs of the following commands:
sudo lshw -C network
ifconfig
dmesg | grep wlan0

Regarding 8.04. Did you check the cd for errors? At what stage does the booting stop?

8.4 boots and gets to the page were you can choose to install, try etc etc

---

### Post by mikewhatever on 2008-11-29
> **Oliver.BS said:**
> 8.4 boots and gets to the page were you can choose to install, try etc etc

So it boots ok, can you detail what happens then, presumably when trying to load the OS.

---

### Post by Oliver.BS on 2008-11-29
> **mikewhatever said:**
> So it boots ok, can you detail what happens then, presumably when trying to load the OS.

A little box appears when ever I clicked start cd without changed to pc and the box said "Try reboot again"

---

### Post by ugm6hr on 2008-11-29
The Dell 1525 was one of the Ubuntu 7.10 offers.

The Windows versions tend to have Broadcom rather than Intel wifi.

Nevertheless, you can get a custon Dell iso from: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Some more info about what happens when you run the "check CD for defects" would be helpful.

Just decide which version of Ubuntu you want.  It would be easier to help with 1 version.

---

### Post by Oliver.BS on 2008-11-29
Well I choose 8.4 can I found a thread saying it supported the wi-fi problem does 8.10 with the dell iso work ?

---

### Post by ugm6hr on 2008-11-29
> **Oliver.BS said:**
> Well I choose 8.4

OK. Going with 8.04.

You can either just download the Dell DVD iso, or if you want to try and persevere with your existing disc: check the md5 of the CD iso file, and run the "Check CD for defects" choice when booting from the CD.

> does 8.10 with the dell iso work ?
I have no idea. I didn't realise that the 8.10 Dell iso was available.

---

### Post by Oliver.BS on 2008-11-29
Thanks for all your help I cannot test this for a week due to going on holiday but as soon as I gt back I will tell you my outcome.

---

