---
title: "Locking up"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by rotorhead22 on 2011-11-17
Hello to all. I have been a Windows person for a long time and decided that I had had enough of their issues. A fellow coworker told me about Linux and I decided to give it a try on my HP Pavilion dv6000. I can use the internet being hardwired, but the wireless card crapped out so I am attempting to use a Cisco usb wireless. Here is the info that I retreived, Linux ubuntu 3.0.0-12generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x_64x86_64x86_64 GNU/Linux. I cannot retreive any information about the network using lspci | grep network. I would like to get the wireless working but I may have a bigger issue. The 11.10 Ubuntu that I installed seems to be locking up quite frequently. Is this version too much for my laptop? Should I try a earlier version? Thanks

---

### Post by TBABill on 2011-11-17
For the wireless, since it's usb you just need to use lsusb instead of lspci. The lspci only reports your pci devices. No need to follow the lsusb command with anything else...it can give you what you want with just lsusb (no need for grep).
 
For the lockups, have you tried clicking the upper right corner icon, clicking logout, re-entering your password to get back in, but before hitting enter, select the icon to the right of the box where you enter your password and select Ubuntu 2D? That may help relieve your video card a bit and see if the lockups are related to that or not.

---

### Post by rotorhead22 on 2011-11-17
> **TBABill said:**
> For the wireless, since it's usb you just need to use lsusb instead of lspci. The lspci only reports your pci devices. No need to follow the lsusb command with anything else...it can give you what you want with just lsusb (no need for grep).
 
For the lockups, have you tried clicking the upper right corner icon, clicking logout, re-entering your password to get back in, but before hitting enter, select the icon to the right of the box where you enter your password and select Ubuntu 2D? That may help relieve your video card a bit and see if the lockups are related to that or not.

Thanks for the info, I will give it a shot. Is there a list of these commands somewhere? It would sure help me weed through some of this. Thanks

---

### Post by rotorhead22 on 2011-11-18
lock up issue appears to be taken care of by updating the NVIDA driver. I also updated my BIOS. USB wireless will not work because the driver for the Linksys AE1200 is not Linux compatible (i also tried the converter). Any suggestions for a wireless usb for a HP Pavilion dv6000.

---

