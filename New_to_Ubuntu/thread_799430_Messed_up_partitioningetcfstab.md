---
title: "Messed up partitioning/etc/fstab"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by zabien1970 on 2008-05-19
I just redid my partitions following this guide [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) and in the process moved my swap from /dev/sda5 to /dev/sda4, then made my /home /dev/sda5, when I went to add /home to my etc/fstab I seen /swap was listed there as sda5.
 How can I fix this, my computer won't boot now.

 I do have a backup for fstab but was wondering if I could change the /swap in fstab to fix this

---

### Post by forestpixie on 2008-05-19
You should be able to boot into recovery mode - you can use nano to edit the file there. Ctrl+O and enter to save, Ctrl+X to exit.

Find the lines that refer to /home and swap - they will start with UUID=, remove the UUID reference and replace with /dev/sda4 or /dev/sda5 where necessary

---

### Post by zabien1970 on 2008-05-19
OK, that was simple enough but now when I log in I type my name then password and a message comes up stating '/home/brendon' does not appear to exist,then it asks if I would like to login as root, I hit continue and it says '/home not found' then takes me back to the login screen.
 could something in the psychocats howto renamed it?

---

### Post by forestpixie on 2008-05-19
Can you give us the outputs for

```
df -h
sudo fdisk -l
cat /etc/fstab
```

Not sure whether it would have - at least I didn't get that when I tried that last year.

---

### Post by zabien1970 on 2008-05-19
OK, I'm back, had to get some sleep
I did run the /home recovery commands that were at the end of the link, same results

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 502M   16M  486M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 502M   16M  486M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   64K  502M   1% /dev
devshm                502M   28K  502M   1% /dev/shm
tmpfs                 502M  3.0M  499M   1% /tmp
gvfs-fuse-daemon      502M  167M  335M  34% /home/ubuntu/.gvfs

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            2806        9729    55617030    5  Extended
/dev/sda3            1276        2550    10241437+  83  Linux
/dev/sda4            2551        2805     2048287+  82  Linux swap / Solaris
/dev/sda5            2806        4080    10241406   83  Linux
/dev/sda6            4081        5355    10241406   83  Linux
/dev/sda7            5356        6630    10241406   83  Linux
/dev/sda8            6631        9729    24892686   83  Linux

Partition table entries are not in disk order

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda4 swap swap defaults 0 0

---

### Post by forestpixie on 2008-05-19
That'll be the output from the livecd I guess. Can you get fstab from the proper ubuntu partition - you should be able to get to it with gksudo nautilus in the livecd - you'll have to get to the right one from there. If you can't get to it - try getting it from the recovery prompt

You won't be able to df -h I think though.

---

### Post by zabien1970 on 2008-05-19
Is this what you're looking for?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2f49317-904e-4337-aa93-09db4071962a /               ext3    defaults,erro$
# /dev/sda5
/dev/sda4      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by forestpixie on 2008-05-19
Yep - that's more like it - you haven't got home mounting there and I'm a bit concerned about the end of the root entry as well - never seen that.

Edit the file as root whichever way you prefer

Change the sda1 line to 
```
UUID=c2f49317-904e-4337-aa93-09db4071962a / ext3 errors=remount-ro 0       1
``` apart from the UUID that is how mine mounts

Add a line for home - if you are sure it's at sda5
```
/dev/sda5  /home ext3 defaults  0       2
```

 You can also change the description line for swap, change 
# /dev/sda5
to 
# /dev/sda4

Edit - I hope that works - I've taken it from mine

---

### Post by zabien1970 on 2008-05-19
OK, made the changes, heres the new fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2f49317-904e-4337-aa93-09db4071962a /               ext3  errors=remount-ro 0       1
# /dev/sda4 swap
/dev/sda4      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /home
/dev/sda5  /home ext3 defauts  0       2


the root entry was the same, for some reason if you shrink the terminal box it shows lines that run on out of the box as $, maximizing corrected this

still the same problem

should /home and /swap be logical partitions under the primary?
I partitioned as follows

/dev/sda1  ext3 9.77G   <existing 7.04>
/dev/sda2  extended 53.04   <misc. /home, pics, music, etc>
/dev/sda3  ext3 9.77G   <to add 8.04>
/dev/sda4  swap 1.95G   <swap>
/dev/sda5  ext3 9.77G   </home>
/dev/sda6  ext3 9,77G   <for music files>
/dev/sda7  ext3 9.77G   <for pics>
/dev/sda8  ext3 23.74   <extra>

---

### Post by forestpixie on 2008-05-19
I was under the impression that numbering of logicals started from #5, so you to my mind 5,6,7,8 inside sda2. sda1,2,3,4 are either primary or extended.

From the psychocats page it says use as syntax for ftsab

/dev/hda7 /home ext3 nodev,nosuid 0 2

try changing to that, sda5 replacing hda7

Other than that I'm not sure why it's not working.

---

### Post by zabien1970 on 2008-05-19
clarifying partitions

primary   /dev/sda1 ext3 9.77G <existing 7.04>
extended  /dev/sda2 extended 53.04 <misc. /home, pics, music, etc>
primary   /dev/sda3 ext3 9.77G <to add 8.04>
primary   /dev/sda4 swap 1.95G <swap>
logical   /dev/sda5 ext3 9.77G </home>
logical   /dev/sda6 ext3 9,77G <for music files>
logical   /dev/sda7 ext3 9.77G <for pics>
logical   /dev/sda8 ext3 23.74 <extra> 
 sda 5-8 logical under sda2

on startup
user name>
password>
Your home directory is listed as: '/Home/brendon' but it does not appear to exist. Do you want to log in with / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.
I hit yes
User's $Home/.dmrc file is being ignored this prevents the default session and language from being saved. file should be owned by user and have 644 permissions. Users $Home directory must be user and not writeable by others
I hit OK and it goes back to 
user name>

details
(skipping startup)
(gnome-session:5488): libgnomevfs-
Warning **:Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory '/home/brendon/.gnome2/': No such file or directory

One thing I noticed typing this (I'm on two seperate computers) the /Home directory's have a capital H, the psychocats howto is in lowercase h, could there lie a problem?  Although the final line is in lowercase
edit: I did change hda7 to sda5

---

### Post by forestpixie on 2008-05-19
I'm sorry it's beyond me why it's not working - I assume it's something to do with the move. 

The .dmrc error is I'm sure part of the same thing - that error is well documented on the forum - plenty of threads.

Sorry I can't be of more help.

---

### Post by zabien1970 on 2008-05-19
Yeah, it's beyond me too, I thought I read somewhere the /swap and /home partitions should be under the primary partition, I'm wondering if that's so it gets mounted during startup since if I had a seperate partition with let's say windows I wouldn't expect Ubuntu to mount it.
 So if this is the case then somewhere there should be startup mount points, or is that what fstab is (newbie forum here lol)
 Also, Ubuntu being case sensitive could /home, /Home make a difference? or /home compared to /home/brendon since thats the file that's no longer being found?

---

### Post by forestpixie on 2008-05-19
I've had / as a primary, swap and /home as logicals and I've had them all as logicals. It shouldn't matter, case does matter though and /home and /Home would be different I guess - /home is the folder in which your home resides, my home is /home/kevin

If you installed with the guided or do it all for me options - buntu puts it in an extended.

Yes fstab is the list by which partitions are mounted afaik.

It would definitely seem that it shouldn't belooking for /Home/brendon though

This is a complete guess - if you can get into the system you could try going to Users and Groups - go to the properties for brendon - in Advanced you can set the home directory, if that's set to /Home/brendon you could try changing it - BUT I've never done it and don't know what could happen ;)

---

### Post by zabien1970 on 2008-05-19
The thing that gets me is at the end of the howto it shows how to restore everything and that doesn't even do anything!
I still wonder if it can't find /home/brendon and in the how to I switched only /home, would the files in /home all be altered (/home/brendon) or could there be a typo and when I'm moving directories instead of /home I should use /home/brendon,
 The line that does this I believe is 
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
Also if you look at the howto there is a /old and a /new for the original install and the new partition
I'm still learning here but shouldn't the last line read
sudo mkdir /new/home 
arrrgh, I'm sure there's some stupid little thing we're all missing!

---

### Post by forestpixie on 2008-05-19
I'm afraid that I can't see the wood for the trees here, it needs new eyes I think.

As I said I used the howto myself and it worked for me. 

If you can't get it sorted maybe it'd be worth reinstalling, at the least your /home will be ok.

Sorry I can't be of nay more help :(

---

### Post by zabien1970 on 2008-05-19
What do you mean if I reinstall? are you saying since I saved my /home to a new partition it may still be safe? if you look at my partitions I originally had linux using most of my HD and 2G for swap, then I partitioned to give a new sspace for 8.04 and a seperate partition for home, music, pics, etc... my //dev/sda3 is blank right now awaiting 8.04 which is the live cd I'm running off of, I suppose it will be a custom install which scares me since my original ubuntu install erased my dual boot with windows although that has become a blessing, lol, 
 I suppose I could start from scratch and do it all again since thats how I've learned what I know so far.
 If anyone else is reading this thread feel free to but in, Pixie and myself are at a standtill!

---

### Post by volkswagner on 2008-05-19
I am not sure if it is too late for this.  I had the same problem with /home.

I was able to revert the partition table with, chkdisk.

[http://ubuntuforums.org/showthread.php?t=724156]("http://ubuntuforums.org/showthread.php?t=724156")

---

### Post by JC Cheloven on 2008-05-19
As far as I see, you didn't run ```
blkid
```to find out the UUIDs the partitions have actually assigned. These UUIDs should match the ones in etc/fstab. Do they?
Hope to be of any help

Greetings

---

### Post by JC Cheloven on 2008-05-19
Note: requires sudo:
sudo blkid

---

### Post by zabien1970 on 2008-05-19
Uh, I can't read this but here it is anyway

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="c2f49317-904e-4337-aa93-09db4071962a" TYPE="ext3" 
/dev/sda3: UUID="14bebe28-8d87-476c-bb73-08a7e1bbb2e3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="881ac030-7e97-457a-9810-f2402e9a2b12" TYPE="swap" 
/dev/sda5: UUID="642113ff-ca05-4dd7-8bd7-09776188c08c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="c741e368-7cfa-4a17-b3f3-de5add05b346" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="2264b34d-6b38-49ce-910a-cf1b3a389ba9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="0fd1059a-c397-4799-a7fd-ff162548bf25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

---

### Post by zabien1970 on 2008-05-19
compared to fstab which is>

edit> wrong output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2f49317-904e-4337-aa93-09db4071962a /               ext3  errors=remount-ro 0       1
# /dev/sda4 swap
/dev/sda4      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /home
/dev/sda5  /home ext3 defauts  0       2

---

### Post by Skeet on 2008-05-19
Similar thing happened to me, but I did nothing to cause it.

/dev/sda1 (windows boot partition) swapped to /dev/sdb1 which was my linux partition.

Its still the same to this day, no idea why it happened mind you.

---

### Post by zabien1970 on 2008-05-19
So does anybody have any ideas on what I should do next? Getting kinda old running off the livecd :(

---

### Post by JC Cheloven on 2008-05-19
> **zabien1970 said:**
> compared to fstab which is>

edit> wrong output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2f49317-904e-4337-aa93-09db4071962a /               ext3  errors=remount-ro 0       1
# /dev/sda4 swap
/dev/sda4      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /home
/dev/sda5  /home ext3 defauts  0       2

Well, nothing strange here: the UUID for sda1 match in both fstab & blkid, as it should be. Your sda4 (swap) and sda5 (ext3) are referred by name instead of by UUID in fstab, which I think is a valid possibility. The other partitions are mounted when you first access them in the session (I figure out). So nothing weird here, to my knowledge. Your problem should be elsewhere. I'm sorry.
Greetings

---

### Post by tropdoug on 2008-05-19
Must be the day for this, are you my Brother? LOL, I did the exact same thing, same experience with the recovery stuff, and same message on boot, and I am scratching my head right now too, and working off my desktop,l whilst my laptop refuses to acknowledge the location of /home/kim, so if anyone else can help .......

(PS my thread is at [http://ubuntuforums.org/showthread.php?t=800387](http://ubuntuforums.org/showthread.php?t=800387) but not much else there)

---

