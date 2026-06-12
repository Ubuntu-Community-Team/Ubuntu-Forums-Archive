---
title: "windows 7 became unbootable"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2012-04-02
My friend had a dual boot of Kubuntu 10.04 and windows7. Few days back, he formated the entire linux partition and after restarting, Grub displays error and windows 7 is not booting. How to revert to windows boot loader ?and He doesnt have the windows repair cd. Is there any possibilty of installing grub through ubuntu live session ( without installing ubuntu again)?

---

### Post by CSNate on 2012-04-02
Yes, you should run the grub-install from the terminal, I'm not sure if this will autodetect Windows 7 on install.  If your friend's NTLDR is damaged, I'm not quite sure he will be able to use GRUB at all to boot Windows, as I believe GRUB chainloads the NT Boot Loader.  You may need the Windows disc in the end.

```
sudo grub-install /dev/sdx
``` Where x is the drive.

---

### Post by santosh83 on 2012-04-02
> **1991sudarshan said:**
> My friend had a dual boot of Kubuntu 10.04 and windows7. Few days back, he formated the entire linux partition and after restarting, Grub displays error and windows 7 is not booting. How to revert to windows boot loader ?and He doesnt have the windows repair cd. Is there any possibilty of installing grub through ubuntu live session ( without installing ubuntu again)?

Have you looked through these threads?
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
[http://ubuntuforums.org/showthread.php?t=1911968](http://ubuntuforums.org/showthread.php?t=1911968)
[http://tips.mistergeek.com/87](http://tips.mistergeek.com/87)[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Among the first hits on Google for 'restore windows mbr from ubuntu.'

---

### Post by 1991sudarshan on 2012-04-02
> **CSNate said:**
> Yes, you should run the grub-install from the terminal, I'm not sure if this will autodetect Windows 7 on install.  If your friend's NTLDR is damaged, I'm not quite sure he will be able to use GRUB at all to boot Windows, as I believe GRUB chainloads the NT Boot Loader.  You may need the Windows disc in the end.

```
sudo grub-install /dev/sdx
``` Where x is the drive.

Should that go in to the partition where windows 7 is located or separate partition ?

---

### Post by Mark Phelps on 2012-04-02
> **1991sudarshan said:**
> He doesnt have the windows repair cd. 

Had you friend bothered to check in a Win7 forum, he would have discovered that he could have created a Win7 Repair CD -- for FREE (except the price of a CD blank).

What you can try, because this sometimes works, is using Boot-Repair to see if it will repair the Win7 boot:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by 1991sudarshan on 2012-04-02
> **santosh83 said:**
> Have you looked through these threads?
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
[http://ubuntuforums.org/showthread.php?t=1911968](http://ubuntuforums.org/showthread.php?t=1911968)
[http://tips.mistergeek.com/87](http://tips.mistergeek.com/87)[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Among the first hits on Google for 'restore windows mbr from ubuntu.'


sudo apt-get install ms-sys

that package is not found.

---

### Post by CSNate on 2012-04-02
> **1991sudarshan said:**
> Should that go in to the partition where windows 7 is located or separate partition ?

If you want grub to be your bootloader, it needs to be installed to disk not in a partition.  So for example, my hard disk is /dev/sda.  So I would execute

```
grub-install /dev/sda
```

You can install grub to a partition, but I'm not really sure that would help fix the problem, in fact I can't really think of a situation where you would want to do that.  And remember, he likely is going to need to repair both grub and NTLDR (the Windows NT boot loader).  I'm not exactly sure where to get the recovery environment, but that is what I would recommend.

---

### Post by oldfred on 2012-04-02
The grub-install /dev/sda works if you are booted into your install, but not from a liveCD.

Probably best to run boot info script from Boot-repair so we can make more specific repair suggestions.

From liveCD you have to mount the partition with Ubuntu and install. But this just reinstalls grub2's  boot loader to the MBR and does nothing for fixing Windows.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

