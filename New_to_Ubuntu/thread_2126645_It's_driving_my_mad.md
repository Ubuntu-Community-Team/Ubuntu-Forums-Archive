---
title: "It's driving my mad"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by Mike Zahorik on 2013-03-17
I thought that I'd try Linux because I have had it with MS stuff, but the file system is driving me mad. I have ubuntu 12.04 up and running and I can do all the normal person stuff good enough, but when I want to some other things like in nautials or on the command line, the logic of the file system is ......... maybe I'm too focused on MS. Anyway, I understand that the hard drives (I have two) are /sda1 & /sda2. I can not find them when looking for them in the file manager. I had thought that they would be listed in the /dev directory, no soap. Thought that maybe they would listed under /media, no soap. Maybe under /mnt, nothing. Where in the world are they. I want to look for paths and filenames on both drives and my usb keys. Help Please.

Mike

---

### Post by trundlenut on 2013-03-17
If you have two physical hard drives they would be listed as sda and sdb.  sda1 is the first partition on sda and sda2 is the second etc.  just doing a normal installation will leave with ubuntu installed on sda1 and sda2 is used for swap (bit like the pagefile in windows).

sda1 will contain everything file wise and / is equivalent to the C: in windows.  All you settings and files live in /home/*your username*/

Does your machine definately have two hardrives?  Is only ubuntu installed or is it dual booting with windows?

---

### Post by Mike Zahorik on 2013-03-17
OK, that makes sense, I had forgot about paritions. Yes the machine has a single TB seagate hard drives, and one solid state drive,  freshly installed yesterday. This machine only has ubuntu 12.04 on it. A little more info, please, <1> ok if my 'stuff' is in /home/mike/, why don't or can't I see the drive names /sda, etc. <2> what is the difference between /sda, which is the 1st physical drive, which could have /sda1 through /sdax paritions on it, and what  I have seen as /hda, etc.  <3> are the usb drives names /da0, etc? and where would they be?

I appreciate your help, Mike

---

### Post by Bashing-om on 2013-03-17
Mike; Hi ! Welcome to the forum .

The short answer is use the file manager - nautilus - ( folder icon in the launcher).
Long answer: In order to access any file in linux, the device containing the file must be attached to the file system. This is done by making a mount point and then mounting it to the file system. There are a number of ways to do this, depending on what you want to accomplish.

A great place to start for all things ubuntu:
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)[INDENT=2]
Hope this helps, one can always always ask

[/INDENT]

---

### Post by Mike Zahorik on 2013-03-17
I've been using nautilus. So a drive or device has to mounted, to be seen? And mounted means that it is attached the file system? Then since the OS is running on /sda1, doesn't mean that this drive is mounted and why doesn't it show in the nautilus. What I mean by that is shouldn't I see /sda1 in the /dir or /media directories. Thanks, I'll look into the NewDocs file. I think that I need to fully comfortable with the file system and it is a little ..... different. Mike

---

### Post by Bashing-om on 2013-03-17
Mike;
Devices in linux work like this.
sda is the first sata mode hard dive on the buss. then sda1 = the fist partition on this first hard drive, sda2 = 2nd partition, 1st hard drive, sda5 = 5th partition on the 1st hard drive.
hda = older ide hard drive designations
sdb then is the second sata mode hard drive (1,2,3,n == partitions)
then perhaps the usb device will be recognized as "sdc" if only one partition on the usb device "sdc" then it might be picked up as sdc1.

As to why you do not see the "sda" in the file management system// partitions on the respective devices are mounted not the device itself. There are many many tools available to look at things at the device level, that is not in the realm of file management.

usb devices will not be seen until they are mounted( why you do not arbitrarily see them), whrn they are inserted, the system recognizes them and then is the designator assigned ie "sdc" or depending what other devices are plugged in and when perhaps "sdg"

In the file manager, unless you have labeled the devices, they may be identified thus "8.0 filesystem-long string of numbers" that string is the UUID of the associated device.[INDENT=2]
good 'nuff -> next question

[/INDENT]

---

### Post by trundlenut on 2013-03-17
when you open nautilus it defaults to your home directory (/home/*username*/), think of this as sda1/home/*username*/

If you click on "File System" on the left hand side it will take you to root directory (effectively sda1/, equivalent to C:/)

I dual boot with windows and so at the top left of the nautilus window I have "60GB FIle System", which is the partition with windows on it on the hard drive on my laptop (which is actually sda1 and ubuntu is installed under sda2 as windows was already installed when I installed ubuntu).  When I click on this option it mounts the windows partition.

---

### Post by trundlenut on 2013-03-17
Whoops double post.

---

### Post by Paqman on 2013-03-17
One place you can look to "see" where drives/partitions are is the file /etc/fstab. This is the filesystem table, and shows what locations in the filesystem are mounted on what actual devices.

What you'll probably see is a line that equates sda1 with a location called / (root). That means the whole filesystem is on that device. So when you browse every location from / on down (which includes places like /tmp, /media, /home/username, etc) then you're browsing stuff on that device.

In reality you could have a setup somewhat different to that. It's quite possible to put / on one device and have locations such as /home on a totally different device, but the default setup is to put everything all on one partition.

---

### Post by Bashing-om on 2013-03-17
Mike;
You are absolutely correct that one must be comfortable with the file system ! The documentation is overwhelmingly abundant on the 'net and can lead to a lot of confusion in understanding a lot of the aspects of linux in general. Take small bites and digest well before moving onto other matters,

A word of advise. This ain't Windows. So develop a different mind set and a new attitude (intellectual approach) and do not even try to apply what you know from Windows to ubuntu in any specifics. You will become even more confused and frustrated. Small steps.

We are here to help you along the way >>

---

### Post by trundlenut on 2013-03-17
As you have two hard drives in your machine could you open a terminal and type the following:

```
sudo fdisk -l
```

then enter your password when prompted.

Post the output here.

As an example below is the output I get:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b3609ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117194174    58597056    7  HPFS/NTFS/exFAT
/dev/sda2       117194752   156256255    19530752   83  Linux
/dev/sda3       156258302   312580095    78160897    5  Extended
/dev/sda5       304769024   312580095     3905536   82  Linux swap / Solaris
/dev/sda6       156258304   304766975    74254336   83  Linux
```

My laptop has only one drive, the first partition is windows, the second is ubuntu.  sda3 actually contains sda5 and sda6 (which you can see from the blocks) and sda5 is the swap partition.  sda6 is actually my home partition, I set this up when I installed ubuntu to allow me to mess around with less chance of losing everything if I messed ubuntu up.

---

### Post by Mike Zahorik on 2013-03-17
The old noodle is still a little foggy. Since I have to think about the nautilus a little how about, in the terminal, if I wanted to view all the files on the USB key, /sdc. why doesn't this work? 
:/media/mike# cd              to get to the root
:~# cd /dev/sdc         to chance to the USB key
:/media/sdc dir            to display the files        

I tried this and it doesn't work where did I go wrong?

Thanks Mike

---

### Post by trundlenut on 2013-03-17
> **Mike Zahorik said:**
> The old noodle is still a little foggy. Since I have to think about the nautilus a little how about, in the terminal, if I wanted to view all the files on the USB key, /sdc. why doesn't this work? 
:/media/mike# cd              to get to the root
:~# cd /dev/sdc         to chance to the USB key
:/media/sdc dir            to display the files        

I tried this and it doesn't work where did I go wrong?

Thanks Mike

Because you are trying to access the drive not a partition, the C drive in windows is a partition rather than a physical disk.  The drive may only have one partition but you still have to specify it e.g. sdc1.  Also you can't directly access partitions via /dev/, can't remember why off the top of my head though.

Also if you try listing the files in a folder using ls instead of dir you will find they get colour coded which is quite handy in working out what is what.

---

### Post by Bashing-om on 2013-03-17
Mike;
Small steps, keep aware of the basics. Ok to scan the files on the external usb device -> the device must first become mounted. The device may become mounted automatically when activated in "nautilus" else must be explicitly mounted by making a mount point and then from the command line mounting that device with the found out particulars.
This is one method and you may find it simpler:
in the file manager, right click on the device and choose properties;
look at Location: ....maybe says /media 
look at name something like 8023-774F

now back on the command line do:
```
 ls -la /media/8023-774F
```
In this instance, the usb device is mounted in the directory "/media" and is named "8023-774F".
If you wanted to Change Directory to this partition:
```
 cd /media/8023-774F
```
now one may manipulate files in any manner ones wishes. The device has been "automagically" mounted by clicking on it in the file manager.[INDENT=2]
clear as mud ?

[/INDENT]

---

### Post by Curtis310 on 2013-03-17
I had the same problem and it drove me crazy too how it didn't just work. I had to set it up, so the operating system can read it, still I don't think I did it right.

---

### Post by Bashing-om on 2013-03-17
Curtis310; Hi !

Please elaborate. Do you mean you need someone to verify how you have set up to mount a device external to what was in the default in the installation ?[INDENT=3]a step in the right direction ?
[/INDENT]

---

### Post by Bashing-om on 2013-03-17
@ Mike !
I failed to advise you to make SURE you (un)mount the usb device prior to removing it or shutting your system down. Failure to remember to (un)mount the device is likely to produce file system corruption. (ubuntu uses a cache ing system and the cache is not written to disk until the device is (un)mounted.)[INDENT=7]
Wheewhh !

[/INDENT]

---

