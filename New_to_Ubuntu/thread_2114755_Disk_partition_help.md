---
title: "Disk partition help"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by asflores3 on 2013-02-10
I am currently running ubuntu 12.04 and I am trying to install windows back on my computer and run a dual boot. I have formatted a usb with a working version of windows but when I run the installation there is no extra partition to install the version of windows to. So pretty much I need to create a partition for windows in Gparted but I am unaware of how to do this. I am kind of new to Gparted so try and keep the instructions as basic as possible. I will attach a picture of what my Gparted looks like.

---

### Post by papibe on 2013-02-10
Hi asflores3. Welcome to the forums ):P

You can't modify partitions that you are using (because you have to unmount them).

Use the Ubuntu installation media as a Live CD/USB. Select 'Try Ubuntu' to get to the Desktop. Once there, you can use gparted to do the job.

First, you need to shrink your Linux partition (sda1) to leave space for Windows. Once that's is done, create an NTFS partition in the unused space.

This would work for up to Windows 7 on a BIOS computer.

If you want to install Windows 8 you would need to set your computer to boot into UEFI.In that case, also take a look at:
[LIST]
[*][UEFI]("https://help.ubuntu.com/community/UEFI")
[*][UEFI Booting]("https://help.ubuntu.com/community/UEFIBooting")
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by oldfred on 2013-02-10
You should just be able to shrink sda1 and create a new sda3 in the unallocated or install Windows into the unallocated.

If you create a partition it must be formatted NTFS, a primary partition (sda1 thru sda4) and have the boot flag which you can add with gparted right click manage flags. If you format it and want to install something newer than XP, you may from Windows installer have to format again as there are different versions of the partition boot sector. In effect to use ntldr (XP) or bootmgr( Vista/7/8) to boot with.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by asflores3 on 2013-02-10
Okay and correct me if I am wrong but to shrink sda1 all i do is select it, right click and click resize/move right? because when I try and do that the only options I have are to unmount, manage flags, and information. So I am kind of confused on what i need to do to shrink sda1 and create a new partition. Thanks both of you guys for your quick help by the way, I really appreciate it!

---

### Post by papibe on 2013-02-10
If you have to unmount sda1, my guess is that you are not using the live media, but running your regular installation.

Take a second look at my post, and for more details: [LiveCD]("https://help.ubuntu.com/community/LiveCD").

Regards.

---

### Post by asflores3 on 2013-02-11
Oh okay I understand what you are telling me to do now. I will try booting to liveCD and resize sda1 and let you know how it goes! Thank you for your help! :D

---

