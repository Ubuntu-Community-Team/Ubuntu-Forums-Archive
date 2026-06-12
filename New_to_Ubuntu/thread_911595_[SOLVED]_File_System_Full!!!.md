---
title: "[SOLVED] File System Full!!!"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by 2uRcJQ34G1 on 2008-09-05
Hello,
I am a fairly new Ubuntu user, and its great! But I have encountered a problem. My File System is full. When I open Synaptics Package Manager i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'sudo dpkg --configure -a', I get this error:

dpkg: failed to write status record about `libgtk2.0-common' to `/var/lib/dpkg/status': No space left on device

I cannot update either. Now what do I do?

---

### Post by TransitMan on 2008-09-05
How do you have your partitions set up, and how much hard drive space have you devoted to Ubuntu?

More information on this so we can help.

---

### Post by drs305 on 2008-09-05
Please check out the "Trash Full" link in my signature line. It is possible you have unemptied trash in either your local trash bin or in root's. The tutorial instructs you on how to find and delete it.

You can quickly check you disk space with:
```

df -Th
```

---

### Post by lukjad on 2008-09-05
Also try:
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
This may give you a bit more room. To get to the terminal go to Applications->Accessories->Terminal and then copy/paste these commands.

---

### Post by jemate18 on 2008-09-05
> **gore_grinder said:**
> Hello,
I am a fairly new Ubuntu user, and its great! But I have encountered a problem. My File System is full. When I open Synaptics Package Manager i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I run 'sudo dpkg --configure -a', I get this error:

dpkg: failed to write status record about `libgtk2.0-common' to `/var/lib/dpkg/status': No space left on device

I cannot update either. Now what do I do?

you should type first 

```
sudo dpkg --configure -a
``` so that it will be fixed(the one which was interrupted)

---

### Post by 2uRcJQ34G1 on 2008-09-05
Ok,

so now I have with apt-get clean and autoclean, I have exactly 6.8 MB free. I have 3Gbs for root and 30 Gbs for the user. The user folder is hardly full since I have not started to use Ubuntu on a daily basis yet. Although my File System is full. But this still is not enough. Can someone tell me how to clean my Cache. Furthermore, tell me how to re-configure my partitions to avoid this dilemma in the future?

Thanks for the help!

---

### Post by nhasian on 2008-09-05
only 3 gigs for the filesystem?  yikes!  boot off the liveCD and then use gparted in the system/admininstration/partition editor to resize the filesystem.  you need to do it from the live cd, because you cant resize a partition while its mounted.

---

### Post by 2uRcJQ34G1 on 2008-09-05
what would be a good size?

---

### Post by drs305 on 2008-09-05
> **gore_grinder said:**
> Ok,

so now I have with apt-get clean and autoclean, I have exactly 6.8 MB free. I have 3Gbs for root and 30 Gbs for the user. The user folder is hardly full since I have not started to use Ubuntu on a daily basis yet. Although my File System is full.

Did you look at your trash bins? Run these two commands. When nautilus opens, highlight the "Trash" folder and delete it:
```
gksu nautilus ~/.local/share/
gksu nautilus /root/.local/share/
```

---

### Post by cmat on 2008-09-05
I find 10 or so gigs to be safe. But the more the better.

---

### Post by Zack McCool on 2008-09-05
I usually break it down a bit more than you did, but here's mine, then my recommendation for you...

My Partitions:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     11G  3.5G  6.2G  37% /
/dev/sda2     ext3    137M   46M   85M  36% /boot
/dev/sdb1     ext3    193G  121G   62G  67% /home
/dev/sdc1     ext3     74G   59G   11G  85% /mnt/backup
/dev/sda3     ext3     28G  173M   27G   1% /tmp
/dev/sda5     ext3    5.6G  1.2G  4.1G  23% /var
/dev/sda6     ext3     83G   53G   26G  68% /vmware
/dev/sdb3 reiserfs    174G   90G   85G  52% /torrent

```

My tmp is a bit oversized.  I expanded it a lot when it filled on me once, but it doesn't need to be nearly THAT large...   ;)

Sticking with your plan, here's how I would do it:
```

/ = 8GB
swap = 1.5x RAM
/home = remaining space

```

var and tmp need some room.  var holds all your logs, tmp runs things like the print queue.  Since you are running everything on one partition, you want to make sure they have enough room, including some breathing room.  If you have the space, I'd go even a bit larger, or split things off more.  If splitting things up, give /var at least 4GB, and /tmp should have 2-4, imo.  

As for cleaning space now, I can't really give you much help on that.  you could try cleaning out some old logs, or maybe there is junk in your /tmp folder...

---

### Post by 2uRcJQ34G1 on 2008-09-05
how do i run the live cd? Everytime i restart with the cd in the tray it gives me the same dual boot menu.

---

### Post by nhasian on 2008-09-05
i can help with this one as well :)
when you boot your computer, you need to get into the BIOS.  depending on your computer, it may be DEL, or F2 or something.  it should say during bootup.  There are a lot of options in there, so dont change anything if you dont know what your doing.  There should be a boot options or something similar where it shows for example a floppy drive, HD, usb
, etc.  make sure that the CD-rom option is listed above the HD so it boots off the cd first.  then you can boot off the live cd.

i think you had a smaller HD, so 8-10 gigs should be fine for the filesystem.


> **gore_grinder said:**
> how do i run the live cd? Everytime i restart with the cd in the tray it gives me the same dual boot menu.

---

### Post by 2uRcJQ34G1 on 2008-09-05
Also, how do I clean my tmp, just delete everything here?

---

### Post by 2uRcJQ34G1 on 2008-09-05
ok so now i am booted from the disk. Thanks!

---

### Post by 2uRcJQ34G1 on 2008-09-05
All right, so now that I have the installation going on. I go through the normal process until I reach the partitioner right? And then I manually repartition.....

---

### Post by nhasian on 2008-09-05
when you boot off the live cd, just use the option to try ubuntu without making any changes to the hard disk.  dont install it again or you'll overwrite your data !  then after its loaded you can use the partition editor.

---

### Post by djschlotte on 2010-10-28
I'm having a similar problem. I've gotten an error message saying my file system is nearly out of space. I've tried deleting the trash's, but that does not seem to have made a difference. Is there a possibility to delete old versions of programs, or logs or something? If so, how would one go about finding these things? Thanks.

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4    5.6G  4.9G  397M  93% /
none      devtmpfs    2.0G  348K  2.0G   1% /dev
none         tmpfs    2.0G  752K  2.0G   1% /dev/shm
none         tmpfs    2.0G  196K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none         tmpfs    2.0G     0  2.0G   0% /lib/init/rw
/dev/sda4     ext4    223G  117G   96G  55% /home

*just in case the above info helps.

---

### Post by sofasurfer on 2010-10-29
And I found that it appears that there is no trash folder in 10.04.
gksu nautilus /root/.local/share/ shows nothing.

---

### Post by drs305 on 2010-10-29
> **sofasurfer said:**
> And I found that it appears that there is no trash folder in 10.04.
gksu nautilus /root/.local/share/ shows nothing.

If the Trash folder is missing from that folder it probably means that no 'root' trash has been created yet. Once something is deleted by root, the Trash file will probably appear.

---

### Post by daviddwd on 2011-06-13
> **gore_grinder said:**
> Ok,

so now I have with apt-get clean and autoclean, I have exactly 6.8 MB free. I have 3Gbs for root and 30 Gbs for the user. The user folder is hardly full since I have not started to use Ubuntu on a daily basis yet. Although my File System is full. But this still is not enough. Can someone tell me how to clean my Cache. Furthermore, tell me how to re-configure my partitions to avoid this dilemma in the future?

Thanks for the help!

What if it says all 30 gig full but the hard drive partition  has 137 gig free?

---

