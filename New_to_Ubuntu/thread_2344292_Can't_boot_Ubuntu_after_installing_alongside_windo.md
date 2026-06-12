---
title: "Can't boot Ubuntu after installing alongside windows"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by erotichousecat on 2016-11-23
I just installed 16.04.01 LTS with a live-USB alongside a windows 10 install. However, now when I try to change the boot options, there is no option to boot ubuntu install, only from the live-USB, or Windows.  I tried running the boot-repair tool from the live session off the usb but got a report saying the repair failed.
Report: [paste2.org/ZtvdpaKw]("paste2.org/ZtvdpaKw")
Any help would be appreciated, thanks.

---

### Post by oldfred on 2016-11-23
What brand/model system?

Many systems violate UEFI standard and use description as part of boot. And only valid description is "Windows Boot Manager". But many work arounds.

If you want to read ahead in link in my signature are most of the work arounds.
Boot-Repair now does copy shimx64.efi to /EFI/Boot/bootx64.efi and then many systems can boot the fallback or hard drive boot entry. Some require using efibootmgr to add the hard drive entry.

---

### Post by erotichousecat on 2016-11-24
I'm working on an MSI Apache GE72 with an intel i7-6700HQ processor.

---

### Post by oldfred on 2016-11-24
All the links on various MSI systems. Generally issues are common across a brand, but some can be unique to a model with different chips.

 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

