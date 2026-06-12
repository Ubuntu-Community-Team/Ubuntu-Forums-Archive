---
title: "Recover XP files"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by swissscf on 2008-08-13
Hey Guys, 
I am limping along from an XP log-on crash that keeps me from booting up my "C" drive.  I have SEEN the drives from my system 2 times while I have been using Ubuntu to check email and try to figure out how to do a save for some of my files that I did not have backed up and then reload XP to clean up things.  I would like to dual boot with XP after I get things straightened out.  Problem is that I can't seem to figure out how to open my hard drive from Ubuntu and copy the files that I need to.  After I get them copied, I can reformat my C drive and reload everything clean.  
How do I get access to the files on the old "C" drive?

Thanks, 
Swiss

---

### Post by Dill on 2008-08-13
Hi Swiss,

Just so I understand, do you already have Ubuntu installed, and is it on a separate partition of the same hard drive, or on a separate drive? Or, are you booting from an Ubuntu Live CD? Also, when you "see" the drive, does it appear on the Desktop of your Ubuntu installation/CD?

When you boot into Ubuntu, open up a Terminal and type this command:

```
sudo fdisk -l
```

And post the output here. This lists all of the drives and partitions that Ubuntu can recognize. And if you can see your XP drive from Ubuntu, chances are that it will show up here. If it does, we can mount the drive and copy the files somewhere else.

And if you want to dual boot afterwards, you'll want to install Windows XP before installing Ubuntu. The Windows XP Installation disc will be able to reformat the drive for you, as well.

So yeah, just let me know what's up and hopefully we can start to recover some data!

Cheers, 
Dylan

---

### Post by swissscf on 2008-08-13
Hi Dylan,
Thanks for the offer to help.  Man this forum moves FAST.  I typed this in last night and found it on page 8, then an hour later it is on page 10!  I am running 8.04 from CD.  I actually saw it when running the 7.04 CD and figured that the 8.04 would possibly give me more options.  Using the 8.04, the email/internet connection seems to drop out after I close it and I am having to reboot the program in order for it to recognise the web addresses.  Course, that is a different problem!  HA!HA!  When I did see the different hard drive partitions from the two hard drives, I was in the File Browser.  But when I went back there when I had more time I couldn't get the hard drives to pull up using the File Browser.  I did the Terminal query and this is what I got for reply:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 

Thanks,
Swiss

---

### Post by aysiu on 2008-08-13
This link should help you:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-i-the-backstory/)

P.S. If you want to go the terminal way (which you don't have to), use copy and paste instead of retyping. It's not *-1*; it's *-l*

---

### Post by swissscf on 2008-08-20
Sorry, I was out of town for a few days and still haven't had the time to recover any of the files off of the old drive.  I have not seen the drive information in the last several times that I have booted up and checked email etc...  
I did the fdisk -l and it just returns to the input prompt.  

I also started the link from aisyu and when I open the Places list it doesn't show any additional drives.

I KNOW that I saw the drives and files when I first started this, but can't find them now?

Swiss

---

### Post by Nepherte on 2008-08-20
Are you hard disks shown in BIOS (the very first screen when you boot up your computer)?

---

### Post by swissscf on 2008-08-20
OK, I went into my Boot bios and went to the Hard Disk Boot Priority and it showed both my 250G and my 500G drives.  Then I started Ubuntu and did the fdisk-l probe and it read out the following:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30400   192988845    f  W95 Ext'd (LBA)
/dev/sda5            6375       18485    97281576    7  HPFS/NTFS
/dev/sda6           18486       30120    93458106    7  HPFS/NTFS
/dev/sda7           30121       30400     2249068+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       60800   385977690    f  W95 Ext'd (LBA)
/dev/sdb5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sdb6           25497       38244   102398278+   7  HPFS/NTFS
/dev/sdb7           38245       50992   102398278+   7  HPFS/NTFS
/dev/sdb8           50993       60800    78782728+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

So, it CAN see them. And now I can see them when I open Places and click on Desktop.  I will see if this will let me follow the post on recovery.
Swiss

---

### Post by swissscf on 2008-08-20
OK, for my Email files Under Documents and Settings/XPmail I am seeing my file categories as .dbx files.  I thought that the email files were supposed to be .pst files?  Are these the entire files or just part of the email files?  Where is Outlook hiding the email files that I was using when the system went down?

Thanks,
Swiss

---

### Post by sandysandy on 2008-08-20
faced a similar problem. u can also consider installing windows again on another partition (not the problem one). once windows is up and runnning, u can transfer required files from earlier install to the new one.

(of course u can always force open windows partition from ubuntu even after unclean shutdown)

regards

---

