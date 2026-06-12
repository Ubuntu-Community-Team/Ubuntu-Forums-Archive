---
title: "[SOLVED] Move XP partition and remap GRUB"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-11-18
So i've had a problem lately, ubuntu starts up just fine but when I try to boot up into XP it gives me a NTLDR missing message. I don't know why this started because I used XP twice before this happened.

The set up right now is:

Primary HD - home folder partition and storage partition
Secondary HD - mostly Intrepid Ibex followed by XP partition followed by swap partition

From the research that I did it seems to be that XP doesn't like being in the secondary drive, or anywhere other than the begining of the drive. So getting to my question:

Could I just move the XP partition to the beginning of the primary HD and just remap the grub to follow it to (hd0,0)? I just don't want to have to redo the install since I only use XP to sync my Windows Mobile Phone

Thanks in advance

---

### Post by th89 on 2008-11-18
The problem is not that XP is on the incorrect partition. It is becuase when you installed the dual boot it messed up your existing Windows Installation. Try the following to restore your NTLDR file:

>    1.  Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter, which in this case is "e." This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

([http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm))

Also, you may want to check out [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
This allows syncing your WinMO device with Ubuntu.

---

### Post by caljohnsmith on 2008-11-18
I think I might know what happened; your Windows XP boot files were most likely located on your primary data drive, and maybe you deleted them by accident since you might not know what they were there for. How about first posting:
```
sudo fdisk -lu
```
If you do a "Windows Repair" as th89 suggests, that will probably restore your XP boot files back on your data drive; I would instead recommend installing the boot files to the XP partition, modifying boot.ini slightly, and then you can boot XP entirely from its own partition. If that sounds like what you might want, let me know, and I can give you more details. :)

---

### Post by Keen101 on 2008-11-18
Yeah, an NTLDR error means a problem with some windows files. Grub is pointing to the right file, but windows is broken. Try to use an xp rescue disk.

---

### Post by TadeoDiaz on 2008-11-18
I initialy tried to fix the windows boot because I was getting an error 13 (or something like that). so I popped in my winXP disk and did a fix mbr which lead me to the ntldr missing message.

would it work if I copied those files from the cd to the partition via linux (mount partition and copy files)? or do I have to do it via the command line in windows install?

im not at the computer now (responding from my phone) but will post fdisk soon.

---

### Post by handydan918 on 2008-11-18
One thing to keep in mind is that windows, by default, wants to be on the first partition of the first drive. Anything else will lead to "configuration opportunities".



:)

---

### Post by caljohnsmith on 2008-11-18
> **TadeoDiaz said:**
> I initialy tried to fix the windows boot because I was getting an error 13 (or something like that). so I popped in my winXP disk and did a fix mbr which lead me to the ntldr missing message.

would it work if I copied those files from the cd to the partition via linux (mount partition and copy files)? or do I have to do it via the command line in windows install?

im not at the computer now (responding from my phone) but will post fdisk soon.
Yes, you can copy the files over using linux if you want. You'll need to copy over "ntldr" and "NTDETECT.COM". The last file you will need is "boot.ini", but most likely you will need to modify it since your Windows is not on the first partition. Once you post the fdisk output I can help with that if you want.

---

### Post by TadeoDiaz on 2008-11-18
Ok finally got home

This is the fdisk output.

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c186574

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   214596269   107298103+  83  Linux
/dev/sda2       214596270   488392064   136897897+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaec0aec0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   214596269   107298103+  83  Linux
/dev/sdb2       224829675   234436544     4803435    5  Extended
/dev/sdb3   *   214596270   224829674     5116702+   7  HPFS/NTFS
/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

My windows partition is ~5GB /dev/sdb3 (i've been meaning to reformat the other NTFS partition but haven't had the time to move the stuff in it and do it).

I copied the "ntldr" and "NTDETECT.COM" files over but I can't find the boot.ini file in the i386 folder. I ran a search for the file but nothing comes up. Where can I find it and what do I need to do to it?

Thanks for all your help guys!

---

### Post by caljohnsmith on 2008-11-18
OK, I've attached a boot.ini.txt file to this post that I modified to work for your Windows since your Windows is on sdb3. Just download it, rename it to boot.ini, and put it in your sdb3 partition. Also, you'll need to change the Windows entry in your menu.lst to boot Windows from sdb3, so first open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And if you are booting off your sda drive on start up, your Windows entry would then be:
```
title Windows XP
root (hd1,2)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
If instead you boot your sdb drive on start up, your Windows entry should be:
```
title Windows XP
root (hd0,2)
chainloader +1
```
Give that a shot and let me know how it goes or if you run into problems. :)

---

### Post by TadeoDiaz on 2008-11-18
> **caljohnsmith said:**
> OK, I've attached a boot.ini.txt file to this post that I modified to work for your Windows since your Windows is on sdb3. Just download it, rename it to boot.ini, and put it in your sdb3 partition. Also, you'll need to change the Windows entry in your menu.lst to boot Windows from sdb3, so first open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And if you are booting off your sda drive on start up, your Windows entry would then be:
```
title Windows XP
root (hd1,2)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
If instead you boot your sdb drive on start up, your Windows entry should be:
```
title Windows XP
root (hd0,2)
chainloader +1
```
Give that a shot and let me know how it goes or if you run into problems. :)

Oh my God caljohnsmith, you are a genius! It worked like a charm, thank you so much!

---

### Post by caljohnsmith on 2008-11-18
That's great news it worked, I'm glad you have Windows up-and-running again; cheers and have fun with your OSes. :)

:popcorn:

---

### Post by egalvan on 2008-11-19
> **TadeoDiaz said:**
> Oh my God caljohnsmith, you are a genius! It worked like a charm, thank you so much!

+1

for CalJohnSmith

Boot Guru Extra-ordinaire

---

