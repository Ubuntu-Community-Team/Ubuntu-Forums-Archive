---
title: "Windows 7 re-install wiped out GRUB dual boot to run Xubuntu 14.04LTS"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by Brother_Dave on 2014-05-07
Right now I can only boot up Windows 7 on my C: or sda drive, Xubuntu 14.04LTS was fine on my sdb or D: drive.  What is the easiest way to fix this?    My past computer info is on this other post of mine is here  [http://ubuntuforums.org/showthread.php?t=2219622](http://ubuntuforums.org/showthread.php?t=2219622)  Thanks for all that help !

The GRUB is now on sda with Win 7 and all of 14.04 is on sdb. and that's probably why Win 7 re-install corrupted or removed GRUB.  Win 7 runs fine if I can fix it from there.  I made a Grub 2 repair disk, but will that work in Win 7 ?   I do have from OSDisc.com  a new 16GB USB Flash Drive with Xubuntu 14.04 LTS on it. Will running that that wipe out Win 7 which I still need for dual boot for maybe another month or so?  Windows XP-pro did not work well, so I re-installed Win 7 and that caused the GRUB loss. 

Thanks for your help !

---

### Post by LastDino on 2014-05-07
From what I've gathered, you installed Linux first and installed W7 later since WinXP didn't work, right? If that is true then yes, new install of W7 probably destroyed grub as Windows don't recognize Linux OS.

---

### Post by oldfred on 2014-05-07
Normal installs of Ubuntu install grub to sda.
With 2 drives, better to install grub2's boot loader to Ubuntu drive and keep Windows boot loader in Windows drive. Then each drive works without the other.

You have to boot a Linux repair CD or flash drive, or boot your Ubuntu live installer in live mode and reinstall grub2's boot loader to sdb.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

After you boot into Ubuntu run this which also reinstall grub, but updates it memory on where to reinstall on a major update. Otherwise it may just reinstall itself to sda, and your boot from sdb stops working and your Windows boot in sda is overwritten.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Brother_Dave on 2014-05-10
To LastDino, Yes, I re-installed Win 7 on C: after having Xubuntu 14.04LTS on sdb and grub2 on sda [C: ] which Win 7 then destroyed.

Tues 5/13, I'll  follow oldfred's solutions to run dual boot again.  Many Thanks !  Right now, I'm getting my writing/publishing work done with Win7.

---

