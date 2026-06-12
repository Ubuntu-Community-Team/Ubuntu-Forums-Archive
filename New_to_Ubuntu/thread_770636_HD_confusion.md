---
title: "HD confusion"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by chimchim on 2008-04-27
Ubuntu 8.04 is the only OS on my PC. I have two 80GB HDs the intention being to use one for applications and the other for docs, etc.

I assume that the OS has automatically mounted one of the drives and has installed the necessary programs. Please correct me if I am wrong in assuming this. I could not find the other drive in fstab so I searched the forums for help and eventually was able to mount it in media/mydocs (because that is what the tutorial said to do!). I now have the following situation,

If I go to Places>computer I find three entries Home Folder, File System and 80GB Media. Right clicking Properties on the 80GB Media shows free space 69.5GB and 1 item at 8KB. What happened to the other 10GBs? BTW its UUID is not in fstab and its disk permissions could not be determined.

If I then go to File System>media>disk and open properties I see the same info but with permission granted to read and write.

If I now go to File System>media>mydocs and open properties it shows 65.1GB free and 5 items at 20KB (I created 5 new folders).

Will some kind person please tell me what is going on here:confused:, and as I have obviously done something wrong, what do I need to do to rectify it. Assume I am several steps below absolute beginner.

Thankyou for your attention

---

### Post by hums07 on 2008-04-27
You have swap partition which is used by system. The size can be 2 GB and there are hidden directories not listed (Ctrl+H to view them). To make sure, type this in terminal (Application - Accessories - Terminal):
```
sudo fdisk -l
df -h
```

---

### Post by elpichi on 2008-04-27
whoa. 10gb for swap O.O?
even if it was that amount. wouldn't ubuntu use it from the hard drive where it installed the system and not from the slave/secondary drive?

---

### Post by chimchim on 2008-04-27
Thanks for the response guys but I am still struggling.

From fdisk /dev/sda (which is the boot disk and the equivalent of C:/ in Windows) shows 9729 sectors used. /dev/sdb (which I assume to be my second HD) also shows the same 9729 sectors used.

:confused: :confused: :confused:

The last time I had trouble like this was with Windows 3.1](*,)

---

### Post by ace007 on 2008-04-27
Could you post the output of...
```

sudo fdisk -l

```

I would like to see the setup for myself.

---

### Post by chimchim on 2008-04-27
Hi ace.

You have no idea how confusing this Linux stuff is to me!

This particular problem is just one of a very long list, it seems that even sinple tasks take hours (even weeks) to resolve. If I tell you that I first installed Ubuntu 7.10 six months ago and finally gave up to try 8.04 you will get some idea of my ability.
However, to respond to your request. I have to tell you that Internet access is still a distant dream on Linux. I am using a Windows PC to contact this forum. I tried to copy fdisk to a pendrive to transfer the file to this PC but but as copy and paste did not work it looks like that is another problem to add to the list. I will keep trying and if necessary will retype the whole file.
Thanks for responding.

---

### Post by lswest on 2008-04-27
to copy from the terminal you cannot just do "ctrl + c" that shortcut cancels any running command in the terminal, instead right-click and choose "copy" then paste it into a text file.

---

### Post by chimchim on 2008-04-27
Hi Iswest,
That was the first thing I did - it did not work for me.

I took the easy way out and retyped it in Windows, here it is

Disk /dev/sda: 80.0 GB 80026361856  bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065  * 512 = 8225280 bytes
Disk identifier: 0x00054fb6

    Device Boot	Start		End		Blocks		Id	System
/dev/sda1     *	       1		9327		74919096	83	Linux
/dev/sda2		9328		9729		  3229065	  5	Extended
/dev/sda5		9328		9729		  3229033+	82	Linux swap/
										   Solaris

Disk /dev/sdb:  80.0GB,  80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065  * 512 = 8225280 bytes
Disk identifier: 0x000883c1

Device Boot	Start		End		Blocks		Id	System
/dev/sdb1     	       1		9729		78148161	83	Linux

I hope this helps.

---

### Post by ace007 on 2008-04-27
so it appears that everything is in order, there is no unpartitioned space, no hidden partitions.  

Try typing the command...
```

df -h

```

and if suitable, post the output of the command for us.

It should be very informative about how much of each partition is being used.  It sounds like you think you are missing space on each one of your drives.  Be aware that an "80 GB" hard drive doesn't actually have 80 GB of space.  This is a manufacturer's trick.  Likely, you have about 78.148161 GB of space, I know this doesn't account for this mysterious space you are missing.  But it is things like this that can confure someone.  More than likely you have some hidden files of application data that are consuming the remaining space on your hard drive.

---

### Post by ace007 on 2008-04-27
Oh yeah, and about the permissions not being determined when you go to properties on the "80 GB Media", and then they appear when you go to "disk".  It is likely because the volume is not mounted when you are clicking on "80 GB Media", then its mounted when you enter the "disk" folder.  this is also why it doesn't appear in fstab.

---

### Post by cubeist on 2008-04-27
If you want to see exactly what and where each byte of data on your hdd is you could run the disk usage analyzer ... should be in accessories/disk usage analyzer

---

### Post by ace007 on 2008-04-27
Alright, I'm noticing some funky behaviour when I use the method of determining sizes of the disks in my computer.  when I click on my 20 GB's Linux partition, which is 8 GB.  It is telling me I have about 118.9 GBs used, which interestingly enough, is my combined HD's characteristics.   

**Also, try using the Disk Usage Analyzer application from Applications>>Accesories to get a little different perspective.  Try using it to scan the folders where you have mounted the drives i.e. /media/mydocs, /media/disk**

EDIT: cubeist beat me to it

---

### Post by Xiong Chiamiov on 2008-04-27
Could you also post the show us your fstab?  Just run
```

sudo gedit /etc/fstab

```
and copy+paste that output here.  Oh yeah, and to make it more readable, you can highlight it and click the little # sign up above.

---

### Post by chimchim on 2008-04-28
Hi Guys and thanks for your interest. I am sorry about the delay replying but we seem to be on different time zones (mine is GMT+2).

I checked the Disk Usage Analyser and discovered that the total file system capacity was 215.1GB of which 210.6GB was available. As I only have 2 x 80GB HDs I was agreeably surprised. I am not getting a warm feeling here:)

I am still not able to copy and paste from Linux so have retyped the hidden file and fstab folders. Sorry about the formatting but I am sure you guys are smart enough figure it out.

Filesystem	Size	Used	Avail	Use% Mounted on
/dev/sda1	 71G	2.2G	   66G	     4%	/
Varrun	1.7G	 92K	 1.7G	     1%	/var/run
Varlock	1.7G	    0	 1.7G	     0%	/var/lock
Udev		1.7G	 52K	 1.7G	     1%	/dev
Devshm	1.7G	 12K	 1.7G	     1%	/dev/shm
Lrm		1.7G	 38M	 1.6G	   3%	/lib.modules/2.6.24-16
						-generic/volatile
Gvfs-fuse
-daemon	 71G	2.2G	  66G	   4%	/home/pjmca/ .gvfs


# /etc/fstab: static file system information
#
#<file system> <mount points> <type> <options> <dump> <pass>
Proc                /proc                  proc     defaults      0           0
# /dev/sda1
UUID=0e16ae1f-8e40-4337-9f27-b9a9741db6b9 /   ext3  relatime,errors=remount-ro 0
# /dev/sda5
UUID=67c73b6b-35b1-4daa-863d-85d4df291fd9 / none   swap   sw    0    0
/dev/scd0   /media/cdrom0    udf ,iso9660 user, no auto,exec utf8        0    0
/dev/fd0     /media/floppy0     auto    rw,user,no auto,exec, utf8             0    0
/dev/sdb    /media/mydocs     ext3   defaults                                        0      0

What I am trying to do is to use my second HD exclusively for docs and images with a launcher on my desktop. It seems that Ubuntu recognised the HD and put it in my Home folder but did not mount it. As explained previously I finally managed to mount it and now it appears in 3 places. Would it not be simpler now to uninstall Ubuntu completely and make a fresh start? I have only been playing with it over the weekend so it is no big deal.

Thanks again and have a nice day.

---

### Post by cubeist on 2008-04-29
> **chimchim said:**
> Hi Guys and thanks for your interest. I am sorry about the delay replying but we seem to be on different time zones (mine is GMT+2).

I checked the Disk Usage Analyser and discovered that the total file system capacity was 215.1GB of which 210.6GB was available. As I only have 2 x 80GB HDs I was agreeably surprised. I am not getting a warm feeling here:)

I am still not able to copy and paste from Linux so have retyped the hidden file and fstab folders. Sorry about the formatting but I am sure you guys are smart enough figure it out.

Filesystem	Size	Used	Avail	Use% Mounted on
/dev/sda1	 71G	2.2G	   66G	     4%	/
Varrun	1.7G	 92K	 1.7G	     1%	/var/run
Varlock	1.7G	    0	 1.7G	     0%	/var/lock
Udev		1.7G	 52K	 1.7G	     1%	/dev
Devshm	1.7G	 12K	 1.7G	     1%	/dev/shm
Lrm		1.7G	 38M	 1.6G	   3%	/lib.modules/2.6.24-16
						-generic/volatile
Gvfs-fuse
-daemon	 71G	2.2G	  66G	   4%	/home/pjmca/ .gvfs


# /etc/fstab: static file system information
#
#<file system> <mount points> <type> <options> <dump> <pass>
Proc                /proc                  proc     defaults      0           0
# /dev/sda1
UUID=0e16ae1f-8e40-4337-9f27-b9a9741db6b9 /   ext3  relatime,errors=remount-ro 0
# /dev/sda5
UUID=67c73b6b-35b1-4daa-863d-85d4df291fd9 / none   swap   sw    0    0
/dev/scd0   /media/cdrom0    udf ,iso9660 user, no auto,exec utf8        0    0
/dev/fd0     /media/floppy0     auto    rw,user,no auto,exec, utf8             0    0
/dev/sdb    /media/mydocs     ext3   defaults                                        0      0

What I am trying to do is to use my second HD exclusively for docs and images with a launcher on my desktop. It seems that Ubuntu recognised the HD and put it in my Home folder but did not mount it. As explained previously I finally managed to mount it and now it appears in 3 places. Would it not be simpler now to uninstall Ubuntu completely and make a fresh start? I have only been playing with it over the weekend so it is no big deal.

Thanks again and have a nice day.

First, the reason disk usage analyzer reports more space than you have is due to the gvfs ... go into the prefs and uncheck gvfs and you will get an accurate reading of available space (basically gvfs doubles things)

Second, it appears your disks are recognized with the correct amount of space available... an 80GB disk will have about 71GB free after formatting and you have used a few gigs leaving 66GB free.

Was there another question I am missing?

---

