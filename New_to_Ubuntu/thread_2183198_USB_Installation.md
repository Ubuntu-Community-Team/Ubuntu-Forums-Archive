---
title: "USB Installation"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Bruce_Hooley on 2013-10-23
The Computer magazine I receive gave details about how to create a bootable USB stick and then how to install Ubuntu on the computer. I did as they suggested and all worked well until I got to the Installation type screen. The magazine said there would be an Install Ubuntu alongside Windows 7 option on that screen, but there wasn't. The other predicted options were all there (Replace Windows, Encrypt, Use LVM and Something else, but no dual boot option. How do I get to this option? Someone suggested I didn't have enough space, but my C drive says it has 290Gb free, so I hardly expect it was that. The version I downloaded was ubuntu-13.10-desktop-amd64.iso. I have Windows 7 Home Premium on a 64bit Dell laptop with 4Gb RAM. What have I done or not done? Thanks. Bruce

---

### Post by Johan De Cauwer on 2013-10-24
Actually the fact that your C: drive has 290GB free is an indication that Windows uses that space so in fact you have to shrink the C: drive in order to make space for the Ubuntu installation. Look it up on the internet or use this url I found with Google: [http://www.petri.co.il/shrink-system-partition-in-windows-7.htm](http://www.petri.co.il/shrink-system-partition-in-windows-7.htm)

---

### Post by Impavidus on 2013-10-24
Unfortunately Windows uses the word "drive" to refer to a partition. The free space on your C partition is irrelevant, you need free space on your hard drive, not allocated to any partition. Although the installer can shrink Windows partitions (which worked fine with Win XP), it's recommended you only use Windows tools to do so.

But I think the problem is that you may already have four primary partitions, so Ubuntu cannot make a partition for itself. Read for example [http://ubuntuforums.org/showthread.php?p=11299287#post11299287](http://ubuntuforums.org/showthread.php?p=11299287#post11299287) for a way to handle this.

---

### Post by mastablasta on 2013-10-24
a screenshot from windows disk manager is worth a thousand words :-)  [ seriously, please provide that so we can give better advice on how to proceed]

---

### Post by 3rdalbum on 2013-10-24
I agree with mastablasta, but it sounds to me like your system already has four primary partitions. The good news is, the Ubuntu installer's "Something Else" option can allow you to erase one of those partitions, if one is not needed, and install Ubuntu onto that.

Ubuntu can't install into a Windows partition, of course, so the Ubuntu installer will need to format the partition you set for Ubuntu. You'll need to tell it to format to the Ext4 filesystem, using the mountpoint "/", in the Something Else screen of the installer. It'll make sense when you go into it.

You could install onto a spare external hard disk if you don't have a spare partition.

---

### Post by Bruce_Hooley on 2013-10-26
Thank you all very much for your help. I'll have a try and see how I get on.

---

