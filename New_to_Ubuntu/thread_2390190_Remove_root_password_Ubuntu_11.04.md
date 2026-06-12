---
title: "Remove root password Ubuntu 11.04"
date: 2018-04-26
forum: New to Ubuntu
---

### Post by guimail on 2018-04-26
Hi, have installed ubuntu 11.04 and want to uninstall it, thing is that cannot create a bootable usb or cannot enter command in terminal about removing, unlocking, deleting or whatever i want to do with root account because it always prompts me to enter root password, I have tried:

sudo passwd -u root
sudo passwd -l root
sudo passwd -dl root
sudo visudo

and every command I enter it will request for root password so I cannot creat a clean usb for booting OS Uninstaller or enter GRUB for deleting partitions in HDD.

Really need help with this because I have to install windows 7 starter in a pretty old netbook and don't find the way to remove Ubuntu.

Also tried booting windows installer from usb but message "operating system not found" pops up so, don't know.

thank you

---

### Post by Mark Phelps on 2018-04-26
This is a really OLD version of Ubuntu and is LONG out of support.

You need to use a more recent, supported, version.

---

### Post by Holger_Gehrke on 2018-04-26
Unless you want to get some old data of the system you don't need to do anything with that old Ubuntu. Just run the Windows Installer, tell it to use the whole disk and you're done. The error message "operating system not found" shows that there's something wrong with the USB-device you're trying to use. You might have missed a step or two in preparing it. 

If that netbook is anything like my trusty old Asus EEE, it might have a recovery partition on the harddisk and  you might not need the thumb drive at all. There is some kind of key combination (usually documented in the manual) you need to hold during or shortly after switching the machine on to start the recovery which will reset the system to the way it was when it left the factory.

Holger

---

### Post by guimail on 2018-04-27
Thank you guys for the suggestions,  indeed it was so simple to resolve, the usb stick I was using was not properly formatted as booting usb stick, just used the microsoft bootable usb creation tool, that resolved everything and windows installer came up and did everything.

thank you for having a minute for reading my problem, have a great day!

---

