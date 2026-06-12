---
title: "Acer BIOS has no option to change boot order"
date: 2019-10-17
forum: New to Ubuntu
---

### Post by anothermick on 2019-10-17
Hi, and thank you in advance for the help.
i'm trying to install Ubuntu on an Acer Spin 11 (SP111-33) running Windows 10, but i'm having trouble. Specifically, the BIOS has no option to boot from a USB or CD/DVD. The only option is "windows boot" or some such nonsense. I have disabled "secure boot" mode, but still there is no option to boot to anything but "windows boot manager".
When I try to boot to USB through windows 10, i run into the same problem.
AND, when I contacted Acer support, they told me that they could not help me install any OS but the one that came pre-loaded on the computer! they also said that the Acer warranty would be voided if I did.
currently the laptop is running Acer BIOS version 1.09, which is the most recent BIOS that i had to install because windows stopped working with the old BIOS the first day I bought the computer...

anyway, I have Ubuntu on a USB drive waiting to install. And my specific request is how to boot to a USB drive in Acer BIOS v. 1.09 on an Acer SP111.

help?

---

### Post by mastablasta on 2019-10-18
> **anothermick said:**
> 
AND, when I contacted Acer support, they told me that they could not help me install any OS but the one that came pre-loaded on the computer! they also said that the Acer warranty would be voided if I did.

makes sense. just because you can install linux on your fridge doesn't mean everyone should.

would the EasyBCD work in this case? [https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

make sure to read documentations and make backups.

another option is to use Virtualbox or similar virtual machine and install Ubuntu there.

---

### Post by yancek on 2019-10-18
Newer Acer computers require you to set a UEFI password and to enable trust in the BIOS before you can install another OS.  See the response at the link below.

[https://askubuntu.com/questions/991581/ubuntu-wont-install-on-acer-veriton-desktop](https://askubuntu.com/questions/991581/ubuntu-wont-install-on-acer-veriton-desktop)

The link below to the Acer forums has some information which 'may' help.

[https://community.acer.com/en/discussion/542994/sa5-271-dual-booting-and-changing-the-boot-order-in-the-acer-boot-manager](https://community.acer.com/en/discussion/542994/sa5-271-dual-booting-and-changing-the-boot-order-in-the-acer-boot-manager)

Did you get a user manual with your purchase of the Acer?  If so, take a detailed look at it.  You might also take a look at the Ubuntu documentation on dual booting UEFI with windows 10 at the link below before beginning the install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-10-18
Older Spin model with older version of Ubuntu. May give some clues.
Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238)

Many with Acer (All models) have needed UEFI update.

Acer has started some support of Linux:
Acer Begins Publishing UEFI Firmware Updates For Linux Users On LVFS For Fwupd,  Aspire A315 laptop first
[https://www.phoronix.com/scan.php?page=news_item&px=Acer-Updates-On-LVFS](https://www.phoronix.com/scan.php?page=news_item&px=Acer-Updates-On-LVFS)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by VMC on 2019-10-18
When my Acer got wrapped around itself, and I couldn't get Linux booted, I reset the bios to factory default. 
Also pushing **F12** while booting brings up another boot screen that shows USB UEFI boot iso.
I have newer Acer

---

### Post by anothermick on 2019-10-18
My problem is that there is no boot to USB option. I have chatted with Acer support twice and they say that the BIOS is intentionally locked. The only boot option is "Windows Boot Manager." That is true in f2 and f12, and after I have altered security settings, etc.

I think I need a way to get linux on this computer without using a USB boot.  Is that possible?
thanks,

---

### Post by Autodave on 2019-10-18
I did a little research and found this: either after getting to the BIOS screen, or upon first power up, try pressing and holding the F10 key: this could unlock the BIOS.

---

### Post by oldfred on 2019-10-18
Others have posted that you have to set a UEFI password which then opens many more options. Never lose that password or reset when done reconfiguring.

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread....2#post13369742]("https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742") &

---

