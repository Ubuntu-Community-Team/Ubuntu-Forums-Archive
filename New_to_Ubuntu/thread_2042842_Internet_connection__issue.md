---
title: "Internet connection  issue"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by sankalp84 on 2012-08-15
Hi i just install Ubuntu 12.04, but its not allow to connect me either wifi or cable internet(modem is broad-com).
when i download the b43-fwcutter file from different system & then try to install through terminal.
its respond with error message.
"E: Unable to locate package b43-fwcutter"

Please help me out this.
Thanks

---

### Post by chili555 on 2012-08-15
Please post:```
lspci -nn | grep -e 0200 -e 0280
```Thanks.

---

### Post by sankalp84 on 2012-08-15
Thanks for reply.
i am getting these response while executing the given command.


ranu@ubuntu:~$ lspci -nn | grep -e 0200 -e 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
ranu@ubuntu:~$

---

### Post by chili555 on 2012-08-15
Please do:```
sudo modprobe tg3
```Does your wired ethernet come to life? If so, please proceed:```
sudo apt-get install linux-firmware-nonfree
```Both should now be working.

---

### Post by sankalp84 on 2012-08-15
Thanks !

its working now.

---

### Post by chili555 on 2012-08-15
Awesome! Please use thread tools at the top to mark Solved.

---

