---
title: "Dual boot with Win 7 x64 issues"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by robshaw1170 on 2013-12-12
Have been working on this for about a week now and if i had any hair i would have torn it out by now!
I am a noob when it comes to all things Linux but am learning fast and think i know my way around prety well.
SO have a Win 7 desktop, AMD A6-3500, 8gb ram, single 750gb hard drive, windows 7 64 bit installed on it.
Now i want an ubuntu dual boot to ease my transition away from Windows so have downloaded the ISO vreated a USB and used the GUI to create a 150gb partition for Ubuntu (LTS) and loaded okay. Reboot and no grub screen straight into windows.
Read a few things and have run boot repair ([http://paste.ubuntu.com/6563425](http://paste.ubuntu.com/6563425))
Now when i boot i get the grub screen with all the options but if i try and boot ubuntu, it drops out to a command prompt saying it cannot find the boot.
If i select the recovery mode it seems to time out on an "ata5 softreset: ata5 failed (device not ready)
I have tried various things including Easy BCD as well and nothing seems to work. Even tried Ubuntu 13, Mint but all seem to have the same issue..so akes me think i am doing something wrong each time...
Help!

---

### Post by oldfred on 2013-12-12
Did I not answer this at AskUbuntu?
You need nomodeset since you have a nVidia card.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At grub menu use e for edit, scroll to linux line, and replace quiet splash with nomodeset. That will solve nVidia issues, but if a drive issue it may show what is failing. 

Is drive set in SATA mode in BIOS not RAID nor IDE? Or large or large block allocation.

It seems you booted Boot-Repair in UEFI mode as your system is also UEFI capable? But Windows is BIOS and it looks like Ubuntu is in BIOS boot mode. So be sure to boot in BIOS mode. You may need to set UEFI/BIOS to Legacy/BIOS/CSM only mode.

---

