---
title: "upgrade to xubuntu 11.10 from ubuntu 10.10 on dual boot windwos xp"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Journeyman1962 on 2011-12-08
Hi all,

Am considering putting xubuntu 11.10 over my present maverick system on a dual boot maching (with xp)

I've searched around a bit but haven't managed to pin down something similar.

I'm assuming the fresh install would be the best option, but how can I overwrite the Ubuntu 10.10 system with Xubuntu 11.10 without affecting the windows xp partition / setup.

(I've tried Unity - honest - don't like it. Much prefer the freedom and lightness of XFCE)

Any help/links etc... gratefully received.
Thanks
Tim

---

### Post by editheraven on 2011-12-08
Well, the installer will allow you to format the partition for root. Any other partitions will remain intact. AFter the installation process, grub will override the code in mbr (if you had previously installed the bootloader on root partition, the bootloader will get anyway deleted) and automatically add any other boot marked partitions OR bootloaders at grub menu.

Since xubuntu and ubuntu are both debian based, most of packages will be available for both distros. You should backup your sources.list file. This comand will save you a list of current installed packages : 
"sudo dpkg --get-selections > /home/user/package.selections ". If you have another partition for /home mount point, you'll not lose any of it.


Links : 
[http://sites.google.com/site/easylinuxtipsproject/reinstallation](http://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by Journeyman1962 on 2011-12-09
Hi,

Thanks for the reply.

I'm not an IT whizz, so I was trying to avoid messing around with the partitions manually.

I don't think I explained in properly. I have windows and ubuntu 10.10. I just want to REPLACE the ubuntu 10.10 with Xubuntu 11.10 and leave windows where it is. Will the installer let me do that, or do I have to delete Ubuntu manually first?

Tim

---

### Post by mike555 on 2011-12-09
If your talking about a "Wubi" install I'm not sure you can do what you want to do, better to backup your stuff and do fresh install of Xubuntu.

---

### Post by Journeyman1962 on 2011-12-09
If a "wubi" install is where you do it from a disk and it asks you if you want to install it alongside the existing operating system, yes, that's what I mean.

How can I install xubuntu in place of the ubuntu 10.10, but leave the windows xp where it is?

---

### Post by Elfy on 2011-12-09
wubi is installed inside windows - can be found in windows add/remove.

Sounds to me like you have a dual boot.

Boot with the livecd, open a terminal and run

```
sudo fdisk -l
```

If you can see a linux and linux swap partition only then the linux partition is the one with ubuntu on, if there are more than 1 linux then you either have other linux installed or perhaps a seperate home.

Edit - if you do only have the one and are sure you just want to overwrite it - make a note of the partition name, sdaX then when the installer asks what you want to do - choose "Soemthing Else".

Pick the partition - edit/change - in the new window - format and pick / as the mountpoint - the installer will now format and install to the original install partition.

~If you are not sure post the fdisk output. 

Or if you wish run the bootscript from here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by verymadpip on 2011-12-09
Assuming you are dual booting I would proceed thus:

Make bootable medium, CD or USB

Boot from said medium & fire up the GParted utility

Delete Ubuntu partition.  With this being alongside XP I would expect there to be 3 partitions: XP, Ubuntu & swap.  (Definitely check using fdisk -l  from a terminal).
GParted should give you an indication of which partition is which by file system type anyway; XP=NTFS, Ubuntu=ext4 probably (or ext3 perhaps) & swap is, well, swap. You may have to deactivate swap for the deletion, just activate it again when it's done.

Crack on with the installer, choosing the "something else" option when asked.

Install to, what should now be, "free space", setting the mount point to "/" (without quotes).

I can identify with the not wanting to alter partitions manually.  Take your time & BACK UP anything of value to you before you start.

Post screenshots of GParted & fdisk output here before going ahead if you are unsure of anything.
The partitioning thing is only scary to start with & does become less so after having done it a few times.

As an aside, I did wipe out the wrong drive in a 2 HDD dual boot a few weeks ago.  Luckily for me it was on a test machine & didn't really matter.  That'll teach me for getting complacent with partitioning :-)

---

### Post by Journeyman1962 on 2011-12-09
Thanks all,

I'll let you know how I get on. Got to convince the wife to lose maverick first.. :D

---

### Post by Journeyman1962 on 2011-12-10
This is the output of fdisk -l
I only need about 200 gigs for Windows. The rest would be for xubuntu.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15363366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22947   184321746    7  HPFS/NTFS
/dev/sda2           22948       60802   304063728    f  W95 Ext'd (LBA)
/dev/sda5           22948       38245   122881153+   7  HPFS/NTFS
/dev/sda6           38246       40920    21484544   83  Linux
/dev/sda7           40920       59765   151366656   83  Linux
/dev/sda8           59765       60802     8329216   82  Linux swap / Solaris
tim@tim-MS-7592:~$

---

### Post by Elfy on 2011-12-10
So you have 2 linux partitions - do you know what they are? Do you have a seperate home?

Can you post the output of 

cat /etc/fstab

---

### Post by Journeyman1962 on 2011-12-10
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=28a58940-ec31-4fb1-99d3-1d69202bdc0a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=5a10b3e2-5e89-46f6-ac5a-3a846d67842e /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=25e921b7-eaf0-4bab-a026-0f0545f7257a none            swap    sw              0       0
tim@tim-MS-7592:~$

---

### Post by Elfy on 2011-12-10
Ok - so you do have a seperate home. 

Boot the livecd - start the installer - once you reach the partitioning section - chhose the something else option. 

Select sda6 - change/edit - use as ext4, format, pick / as the mountpoint
Select sda7 - change/edit - use as ext4, DO NOT FORMAT, pick /home as mountpoint

Carry on with the install - xubuntu will be installed where maverick ubuntu was, your old home will be available - as long as you use the same username.

Edit - if you want some realtime help - go here [http://webchat.freenode.net/](http://webchat.freenode.net/)  put #ubuntu-beginners in the channel and a nick in the nickname box - I'm in there at the moment - just say forestpiskie sent you - I'm there for a couple of hours now, or try the realtime help link in my sig.

---

### Post by Journeyman1962 on 2011-12-10
Thanks.

---

### Post by Journeyman1962 on 2011-12-10
When I got this computer, the guy I bought it from set up the partitions for me, and I've never been really happy with how he did it.

I've got 189 Gig of xp, 120-odd Gigs of another NTFS partition, a 22 Gig linux partition (which I can't find on the GUI and don't know why it's there) and then the main ubuntu partition plus 8.5 Gigs of swap.

What I was thinking of doing was to go into disk management of XP and delete all the partitions (all my stuff is backed up - twice) except the 189 xp partition and then install Xubuntu from the disk/usb. Would that work?

I'm just concerned that if I use (x)ubuntu's automatic partitioning, it will give extra disk space to XP. I hardly ever use windows and 189 Gigs is more than ample (I can even use most of it to dump data). 

So, my question is: How do I say to the xubuntu installer, Leave only the 189 for Windows and take all the rest for yourself! (and do I need to specify the swap as well - if so, is 8.5 a good number?? etc... etc...) 

Thanks in advance as always. :D
Tim

---

### Post by Elfy on 2011-12-10
Personally I would be inclined to create my own partitions and then install to those. 

You can do that - why not do your deleting and resizing as you wish to. Then come back with exactly how much free space you have and how much RAM you have.

Also do you want to hibernate - this could be important.

Then armed with that info - you'll get loads of different ways to partiton the install - everyone has different ways to look at it :)


Do you have data in your XP you want to be able to access from within xubuntu - better to do that than try and share xubunt with xp.

---

### Post by Journeyman1962 on 2011-12-10
Mmm. To be honest, I don't feel 100% confident doing my own partitioning. I'm not quite sure how to do it. I also don't want to risk damaging the XP bit. I haven't got an installation disk for Windows.

Hibernate??? Is that related to the computer, or my personal winter sleeping habits? :confused:

I'm not sure about your last question either: I've always been able to access the stuff on the Windows partition from Ubuntu.

(I only keep windows on the computer because occasionally I need to check how WORD handles the formatting on documents that I need to share with others - and also for the odd windows application)

Finally - it's the family computer, so when I do it, it needs to be quick. Desktop up and running and looking like the previous one. I already have Xubuntu on my laptop, so I know what to do to make XFCE look like Gnome :D

---

### Post by Elfy on 2011-12-10
You can always forego the resizing and just do the removing you intended to do - creating the partitions is quick once you've got the live environment up - either cd or usb.

Do you hibernate/suspend the PC? IF you do then we need to make sure that there is enough swap.

WE can find out how much RAM you have from the livecd/usb. 

Installing is likely to be the longest time. 

One way or another you will be doing some partitioning - either automatically or manually and to be honest you have more control manually. 

I'm subscribed to this and watching - I'm also on IRC where you can talk to me if you wish - link in sig for that.

---

### Post by Journeyman1962 on 2011-12-12
Righty-ho. thanks for that. I'm keeping this thread for future reference and will definitely ask if the computer delivers a yorker :D

thanks again
Tim

---

