---
title: "***frustrated*** Broadcom b43 does not work on Hardy Herron"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Parind on 2008-06-20
Hi friends,

I've tried and tried installing and reinstalling broadcom wireless driver and it does not work. Need some help. I followed many online helps and dont know what to do next.

Here is some info. 
1. lspci | grep Broadcom ---> 09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

2.lspci -n | grep '14e4:43'--->0c:00.0 0280: 14e4:4312

3.  uname -mr--->2.6.24-18-generic i686
4.  lsb_release -d  ---> Ubuntu 8.04 LTS

I also installed ndiswrapper as explained in ubuntu documentation
([https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))) and it did not work for me. Now I'm completely lost and the hardware driver keeps telling me to restart and it is not enabled every single time (but status is in use ofcourse).

Can somebody tell me what's the problem ? I have a Dell Vostro 1400 computer with intel core 2 duo processor. 

HELP..........

---

### Post by flowevd on 2008-06-20
have you tried using wicd instead of network manager? it's in synaptic.

---

### Post by noobuntu_ger on 2008-06-20
what is your source ? where do you get the driver from ?

I had the same problem. After I removed my install cd as a software source I installed the driver again and it worked perfectly fine

---

### Post by drunkardivan on 2008-06-20
Have you enabled restricted drivers?

I had just installed Hardy on a Vostro 1000, and between ndiswrapper and Wicd, I had lost my wlan0. I booted into the Live CD, erased my Linux partition, re-installed Hardy (64), and enabled the restricted drivers.

Solved all my wireless issues (except WPA2, but I'm working on that...)

---

### Post by player999 on 2008-06-20
I`m running BCM4311. Look at this little [how2]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") It really helped me, but one of the steps("Making It Permanent") i couldn`t apply. So I wrote little script, that i run at every startup:
```
#!/bin/bash
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```
One note: run script before any appliction that need connection to internet

---

