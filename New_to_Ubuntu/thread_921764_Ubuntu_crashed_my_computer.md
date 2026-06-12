---
title: "Ubuntu crashed my computer"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by tcyk on 2008-09-16
I was running Ubuntu H ...version 8.04 in a Dell inspiron 530 dual core quad processor with 500 GB Sato drive and 500 GB USB drive in a dual-boot configuration. I was running Squeak in my Ubuntu 1n the 121 GB petition on the USB drive. I decided to reboot and received the following message:
GRUB Loading stage1.5.


GRUB loading. please wait...
Error 21
_

When trying to restart, I get the same message. So I can't load Ubuntu, or windows, or anything else. Not wanting to reinstall windows Vista 'God forbid' I booted Ubuntu from the ISO. I thought perhaps I could examine GRUB and determine what the problem might be. I couldn't tell anything but I am a newby.

Can someone help me with this problem or must I reinstall everything? Is this a bug in Ubuntu or Squeak? If Ubuntu is going to cause this kind of problem, I a going to look for another distribution and would recommend that everyone stop using Ubuntu Hardy Heron. Well, maybe the problem is in GRUB.

Charles Gray

---

### Post by emobrad on 2008-09-16
Try reinstalling grub

---

### Post by porchrat on 2008-09-16
[URL="http://ubuntuforums.org/showthread.php?t=672136"]http://ubuntuforums.org/showthread.php?t=672136[/URL

[http://www.mepis.org/node/7330]("http://www.mepis.org/node/7330")

Thought these might help you.  Seems like error 21 means that grub is attempting to read the /boot contents from a drive that doesn't exist...you either have the drives incorrectly set up in your BIOS or your grub is being pointed towards the wrong drive partition... i.e. pointing towards the wrong location for /boot

Let us know if it helps.

Also emobrad...not trying to start a fight or anything, but surely you should at least offer a link to the guy or something.

---

### Post by scorchgeek on 2008-09-16
How long were you using Ubuntu before this happened? It's possible your machine can't boot off a USB drive, which means that you simply need to turn off the drive and boot into whatever OS you had on the internal drive.

---

### Post by halitech on 2008-09-16
try this

Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE device

---

### Post by tcyk on 2008-09-17
> **halitech said:**
> try this

Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE device

Thank you for a very informative answer. I booted the ISO and here is what I get:

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       52818   413718750    7  HPFS/NTFS
/dev/sda4           52819       60801    64123447+   5  Extended
/dev/sda5           52819       60470    61464658+  83  Linux
/dev/sda6           60471       60801     2658726   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# grub-install /dev/sda5
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

I am not sure how to read this but it is evidently only finding the SATO drive, evidenced by the presence of the Dell Utility and NTFS petitions. 

I thought there might be a problem with the BIOS but didn't find anything that I thought was wrong. It appears that the USB drive has failed. I disconnected it and pluged it into my laptop and got the very discouraging message that one of the devices attached to the computer has malfunctioned and windows does not recognize it. I disconnected and reconnected the device several times into different USB ports with the same results. I originally used this device with the laptop for backup.

Probably because of operator error, there were two Ubuntu operating systems installed on my computer. The version I used was installed on the USB drive the other was on the SATO drive. GRUB let me select either of these. The SATO version was 'bare-bones'. I did all my work in the USB version.

Can I proceed from here without reinstalling windows?

---

### Post by t0p on 2008-09-17
> **tcyk said:**
> If Ubuntu is going to cause this kind of problem, I a going to look for another distribution and would recommend that everyone stop using Ubuntu Hardy Heron.

Thanks for the heads-up!  I shall cease using ubuntu immediately!!

*Ubuntu!  Get off my computer at once!  Off!! Bad operating system!*

---

### Post by tcyk on 2008-09-17
> **scorchgeek said:**
> How long were you using Ubuntu before this happened? It's possible your machine can't boot off a USB drive, which means that you simply need to turn off the drive and boot into whatever OS you had on the internal drive.

Thanks for responding. My answer to Halitech answers your question.

---

### Post by tcyk on 2008-09-17
> **t0p said:**
> Thanks for the heads-up!  I shall cease using ubuntu immediately!!

*Ubuntu!  Get off my computer at once!  Off!! Bad operating system!*

Thanks for responding. It appears that the fault is not with Ubuntu but with a failed USB drive and my own inexperience.

---

### Post by halitech on 2008-09-17
sorry to hear about the bad external drive but at least you know now what it is.

to fix grub, it won't install in /dev/sda3 because that isn't a bootable partition. I'm not sure this will work but try this
```
cat /dev/sda3/etc/fstab
```
to see if we can get at your grub info

---

### Post by tcyk on 2008-09-17
> **porchrat said:**
> [URL="http://ubuntuforums.org/showthread.php?t=672136"]http://ubuntuforums.org/showthread.php?t=672136[/URL

[http://www.mepis.org/node/7330]("http://www.mepis.org/node/7330")

Thought these might help you.  Seems like error 21 means that grub is attempting to read the /boot contents from a drive that doesn't exist...you either have the drives incorrectly set up in your BIOS or your grub is being pointed towards the wrong drive partition... i.e. pointing towards the wrong location for /boot

Let us know if it helps.

Also emobrad...not trying to start a fight or anything, but surely you should at least offer a link to the guy or something.

Thank you for responding. Yes it did help. It appears that my USB drive has failed and I must use the version that is installed on my internal SATO drive. Now if I can just manage to change GRUB so that it isn't looking for the USB drive.

---

### Post by nothingspecial on 2008-09-17
> **tcyk said:**
>  It appears that the fault is not with Ubuntu but with a failed USB drive and my own inexperience.

Inexperience is what makes it interesting. God knows what I`m going to do when I never have to type man, can write proper scripts, use Gimp & Inkscape etc etc.

Probably take up the trombone.

---

### Post by tcyk on 2008-09-17
> **halitech said:**
> sorry to hear about the bad external drive but at least you know now what it is.

to fix grub, it won't install in /dev/sda3 because that isn't a bootable partition. I'm not sure this will work but try this
```
cat /dev/sda3/etc/fstab
```
to see if we can get at your grub info

It says it is not a directory. I am pretty sure sda3 is where windows is installed. I originally made a bootable petition for Ubuntu on this drive but notice that it is not shown as being bootable.

---

### Post by halitech on 2008-09-17
crap yes, try it with sda5 which is where linux is showing as installed. 
```
cat /dev/sda5/etc/fstab
```

---

### Post by manishtech on 2008-09-17
> If Ubuntu is going to cause this kind of problem, I a going to look for another distribution and would recommend that everyone stop using Ubuntu Hardy Heron. Well, maybe the problem is in GRUB.
What does Ubuntu has to do with GRUB errors? Its the bootloader which is giving problems. Even ubuntu is somewhat slave of bootloader. :D

---

### Post by Mornedhel on 2008-09-17
> **nothingspecial said:**
> when i never have to type man

hahahahaha * wipes tears *

---

### Post by tcyk on 2008-09-17
> **halitech said:**
> crap yes, try it with sda5 which is where linux is showing as installed. 
```
cat /dev/sda5/etc/fstab
```

I did and got the same results.
cat: /dev/sda5/etc/fstab: Not a directory

---

### Post by halitech on 2008-09-17
did you put a : in there after cat? there shouldn't be anything there.

maybe try ```
cd /dev/sda5
``` to see if you can get in that directory then try the ```
cat /etc/fstab
```

---

### Post by stalkingwolf on 2008-09-17
> probably take up the trombone.

no! Not that!!!!!!!!!!!!!!

---

### Post by nothingspecial on 2008-09-17
"Oh When the saints go marching in"

---

### Post by clive littlewood on 2008-09-17
"I want to be in that number"

---

### Post by tcyk on 2008-09-17
> **halitech said:**
> did you put a : in there after cat? there shouldn't be anything there.

maybe try ```
cd /dev/sda5
``` to see if you can get in that directory then try the ```
cat /etc/fstab
```

I see sda5 listed in dev but but it says it is not a directory when I try to cd into it. 
dir says
... 	sda5	    ttya1  ttyp1  ttytd  ttyyd
...
I went to bed for all of two hours and here I am looking at this thing again.
](*,)

---

### Post by tcyk on 2008-09-17
> **manishtech said:**
> What does Ubuntu has to do with GRUB errors? Its the bootloader which is giving problems. Even ubuntu is somewhat slave of bootloader. :D

You are correct. It had nothing to do with Ubuntu. The bootloader appears to be trying to access the now-dead USB drive.

---

