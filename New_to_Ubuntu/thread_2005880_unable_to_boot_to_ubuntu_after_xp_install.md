---
title: "unable to boot to ubuntu after xp install"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by oldstumpy on 2012-06-18
:popcorn:Hi:Everyone my problem is I installed xp on my 80gb hard drive and have Ubuntu 11.04 on the 120gb hard drive forgot to install duel boot system.Would like to boot to either one.Can anyone please help?Thanks oldstumpy

---

### Post by Cheesemill on 2012-06-18
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by drs305 on 2012-06-18
Windows most likely overwrote the MBR information to point back to the Windows bootloader.

The most foolproof method of restoring Grub/Ubuntu is to boot an Ubuntu LiveCD, install Boot Repair, and click the Recommended Repair button.

If that doesn't work you can run the boot info script, which will post information we can review, and/or we can give you the commands that might restore Grub.

The link to Boot Repair is in my signature line.

---

### Post by oldstumpy on 2012-06-18
HI:drs305,is the boot repair installed on the live cd?and if not where to get?Thanks for the help oldstumpy

---

### Post by Cheesemill on 2012-06-18
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by flemur13013 on 2012-06-18
Since you have two disks, the best idea is to install each system separately on it's own disk - as you have done, but with the other disk physically disconnected, and then select the boot OS via BIOS.

Then in the future you'll be able to do whatever you want with windows - reinstall, delete, upgrade - and it won't affect linux; and vice-versa.  It's very superior to using grub to boot windows.

Right now you should disconnect the linux disk and fix windows with a windows boot repair CD (or just reinstall XP) - with two HDs there's no reason at all to mess with "grub", it's just a pointless hassle.  Then use BIOS to select the OS to boot.

---

### Post by verymadpip on 2012-06-19
+1 for installing on one HDD at a time with the other disconnected.

If GRUB is installed on the HDD containing Ubuntu, & that HDD is then set to boot first in the BIOS you will be able to select XP or Ubuntu from the GRUB menu which is displayed at startup. (It may be necessary to run update-grub from a terminal in Ubuntu for this to work correctly).

IMO entering the BIOS is more hassle.

---

