---
title: "Installed Ubuntu from USB but can't boot to OS."
date: 2015-04-04
forum: New to Ubuntu
---

### Post by robertos2 on 2015-04-04
So I installed Ubuntu from a USB Drive.  However, when I boot up, there is no option to boot the partition that has Ubuntu.  I can boot a Live version of Ubuntu from the USB drive, but not the actual partition.  I tried to boot from Boot-Repair ISO but it didn't work.  Computer is a HP EliteBook 8540w with Windows 7 Pro installed, and as of now, the only OS I have access to.  Any help is appreciated, thanks!

---

### Post by oldfred on 2015-04-04
Best to see details, post link from Summary report.
You can easily install it into the live installer.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by robertos2 on 2015-04-05
I ran Boot-repair and all that happens is it says to remove any CD or other media, and press any key to restart, and then it boots to Windows.

---

### Post by robertos2 on 2015-04-05
Little Update:  Turned out I had Boot Repair mounted incorrectly.  Reinstalled and now grub is working fine, thanks!

---

### Post by Siddhartha_Kashyap on 2015-04-05
I have the same problem :( i use CD/DVD to try Linux distros

---

### Post by flaymond on 2015-04-05
[INDENT]					[QUOTE=Siddharta_Kashyap]I have the same problem :sad: i use CD/DVD to try Linux distros[/QUOTE]

I found most of this issue because of the lack of space by CD/DVD give.

Use USB method or Net(dangerous and hard, but pretty easy sometimes).
[/INDENT]

---

