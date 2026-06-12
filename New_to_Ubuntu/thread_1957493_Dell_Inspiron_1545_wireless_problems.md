---
title: "Dell Inspiron 1545 wireless problems"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by krumdub on 2012-04-12
OK well just dual booted Ubuntu 11.10  and windows vista on my Dell inspiron 1545 laptop and everything is working fine i like it but i cannot figure out how to install the firmware needed to get my wireless card working can someone help me with this

*update*

i have a wired connection as of right now if thats any help

---

### Post by PhantomTurtle on 2012-04-12
Open Additional Drivers(search for it in dash). It should have a driver package for wireless card(something like Broadcom STA). Click on it and at the bottom, click on activate, this will install the driver. Then just restart and it should work.

---

### Post by arochester on 2012-04-12
1)First look for a simple solution. See if there are  proprietary drivers which can be activated under the desktop menu System > Administration >Hardware/Additional Drivers using an existing Internet connection (Ethernet or USB) for best results.

2) Second,if that doesn't work,  Dell were guilty of changing the wifi cards. They might use A for a while, then B, then C. To find out what chip you have open a Terminal and issue the command: lspci (that's l for lemur and not I for India) copy and paste the result here so we can have a look.

---

### Post by krumdub on 2012-04-12
i tried that and this is the message i got 

_____________

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

_____________

---

### Post by krumdub on 2012-04-12
after going to terminal and using lspci i get 

______________


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

________________

---

### Post by arochester on 2012-04-12
Your wifi is Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Have a look at e.g. [http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working](http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working)

---

### Post by krumdub on 2012-04-12
Well i used the update and upgrade commands in the terminal

restarted the computer and the additional drivers worked

thanks guys :)

---

