---
title: "Permissions problems."
date: 2013-09-15
forum: New to Ubuntu
---

### Post by WacoJohn on 2013-09-15
I downloaded a tarball(?) and the instructions said extract it and it is 'ready to run'.  I did, to my Desktop, and the pkg runs perfectly.  Wanted to run it from a flash drive, so I copied its directory/folder to the drive.  When I try to run from there, don't have permissions to do it.  I run it by clicking on a script file .. and when on the Desktop, it says owner(me) has permission to execute.  Looking at the copy on the flash drive, the same file permissions for execution is 'nobody'.

This image illustrates the top two are on the desktop .. folder and script file.  The bottom two are on the flash drive .. folder and script file:

[ATTACH=CONFIG]246248[/ATTACH]

Evidently a Linux copy is not a true copy.   What can I do to run this package from my flash drive .... and then delete it from my desktop?  Thank you, in advance.

---

### Post by sudodus on 2013-09-15
If you want security, you can use a ready-made system with TOR, ***tails***. See this link
[URL="https://tails.boum.org/"]
https://tails.boum.org/[/URL]

---

### Post by steeldriver on 2013-09-15
is the flash drive FAT or NTFS formatted? if so it won't understand *nix file permission attributes

---

### Post by WacoJohn on 2013-09-15
Ahhh.  It is formatted FAT.  Thank you.  If I reformat it to 'nix ... can I later format it back to FAT if I so choose??

---

### Post by WacoJohn on 2013-09-15
> **sudodus said:**
> If you want security, you can use a ready-made system with TOR, ***tails***. See this link
[URL="https://tails.boum.org/"]
https://tails.boum.org/[/URL]

Thing about Tails is it has to be booted.  Wanted to 'Tor' on the fly from flash drive.

---

### Post by ajgreeny on 2013-09-15
> **WacoJohn said:**
> Ahhh.  It is formatted FAT.  Thank you.  If I reformat it to 'nix ... can I later format it back to FAT if I so choose??
Yes it can, very easily with gparted, either on a live system, or as it's a separate drive you can install gparted to your ubuntu system and use that.

As usb drives mount automatically when inserted, you will need to right click on the partition in gparted and unmount it before you can format it.

---

### Post by WacoJohn on 2013-09-15
> **ajgreeny said:**
> Yes it can, very easily with gparted, either on a live system, or as it's a separate drive you can install gparted to your ubuntu system and use that.

As usb drives mount automatically when inserted, you will need to right click on the partition in gparted and unmount it before you can format it.


THANK YOU.  I found this on the internet with a google search:

> [COLOR=#000000][FONT=Helvetica]1. To see what is the filesystem for your flashdrive[/FONT][/COLOR]type -> df
[COLOR=#000000][FONT=Helvetica]2. Type -> mkfs /dev/sdb1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica](The /dev/sdb1 is according to your outcome of the df command previously)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]This command will format the flash drive to ext3 format which is the default.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]To format it to fat;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]type -> mkfs -t vfat /dev/sdb1[/FONT][/COLOR]

Sooo, I take it I dismount drive then do above(?).

---

### Post by Dennis N on 2013-09-15
> **WacoJohn said:**
> 
Sooo, I take it I dismount drive then do above(?).

Probably not.

df command won't tell you the type of filesystem. Output from this computer with a mounted flash drive:

```
dn@Sydney:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       30237648 8884952  19816696  31% /
udev              488980       4    488976   1% /dev
tmpfs             198716     776    197940   1% /run
none                5120       0      5120   0% /run/lock
none              496784       0    496784   0% /run/shm
none              102400       8    102392   1% /run/user
/dev/sdf1        3823984  589480   3234504  16% /media/dn/COMMON
```

here, sdf1 is formatted FAT32 on the flash drive, but you can't tell from this output. You could read this from the gparted window.

note 1: using df -h would give you more readable output
note 2: The man page for mkfs (ver 2.20.1) says that ext2 is the default.

Best solution to everything you need to know and do is to use gparted as suggested in a previous post.

---

### Post by WacoJohn on 2013-09-15
> **Dennis N said:**
> Best solution to everything you need to know and do is to use gparted as suggested in a previous post.

Yes, Sir.  I THINK Gparted is already installed on this Lubuntu installation.  Going to run it, dismount flash drive, format it to Ext2 .. the default(?) and then copy that folder to it.

I only hesitated because I want to be fairly certain I know what to do.  Here goes .... will most likely be back.

EDIT:
By the way, this is a 1GB flash drive.

I think I might have bricked (another) flash drive.  Installed GPARTED, ... and on running it, the drive seemed to have 2 partitions ... or at least one with a fair amount of unallocated space.  Soooo, I tried to tell GPARTED to resize.  LOOKED to me like the right thing to do, .. and I thought I did it successfully.  Here is the current state (could not seem to squeeze that last bit of space out of it):

[ATTACH=CONFIG]246258[/ATTACH]

says it's mounted and supposedly formatted EXT 2.  Sadly, it does not show up in File manager any more .... and when I insert it, I get:

> Error mounting system-managed device /dev/sdd1: Command-line `mount "/mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

:(

---

### Post by ajgreeny on 2013-09-15
I am not sure about that error message, but I suspect you you can revive the flash drive with gparted, and as for that unallocated space; ignore it; it is simply because gparted now aligns partitions by megabytes, not cylinders.

With the drive plugged in run gparted again, and go to the flash drive.  Now use the menu **Device ->Create new partition table** and use the default msdos for table type.  Having completed that, click on the newly unallocated space (the whole disk) and choose to make a new partition of the full space, of fat32 or ext2 as you want, and also label it to some useful name (you'll see why in a minute).  You will still possibly see the 1MB unallocated, but as I say, ignore that.

If you make an ext2 partition, you will need to make the mountpoint yours, which is why I said it was worth labelling it, so with the drive plugged in and the system showing a folder in /media named as the label you gave it, run ```
sudo chown username:username /media/label
```Obviously change username to your user and label to whatever you used; don't forget Linux is case sensitive.  That flash drive will always mount to the same named folder and as that now belongs to you it will be possible to read and more importantly, write to the drive as user.

---

### Post by WacoJohn on 2013-09-15
> If you make an ext2 partition, you will need to make the mountpoint  yours, which is why I said it was worth labelling it, so with the drive  plugged in and the system showing a folder in /media named as the label  you gave it

All went well except no show folder .. either in File Manager or Terminal.  I went back to GPARTED and mounted the device .. thinking that was the problem.  I used the default.  It now shows device mounted:

> Mounted on /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1

but still no folder.  Tried to UNmount in GPARTED and get:

> Could not unmount /dev/sdd1
The partition could not be unmounted from the following mount points:

/mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

FWIW, Easy Setup Key is the original lable ... it's a little Cisco Router thumb drive I no longer needed.

When I followed your instructions, I did Ext 2 and labeled it 1GBFLASH

So .. now can't unmount ... and don't know what to do next.

EDIT:  Maybe this will help

```
wacojohn@ubuntuCOMPAQ:/media/wacojohn$ df
Filesystem        1K-blocks      Used    Available Use% Mounted on
/dev/sda1           8970452   2566508      5941608  31% /
none                      4         0            4   0% /sys/fs/cgroup
udev                 245276        12       245264   1% /dev
tmpfs                 50704       772        49932   2% /run
none                   5120         0         5120   0% /run/lock
none                 253512         0       253512   0% /run/shm
none                 102400        12       102388   1% /run/user
/dev/fuse      101074887820 240204564 100834683256   1% /media/pogoplug
/dev/sdb1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
/dev/sdd1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
```

EDIT2:
In trying to get back to square one with your instructions, I have done some more work.  Thing is, can't remember what all I have done.  I know I did a couple of umounts.  In GPARTED, I deleted the partition and recreated it as you instructed.  Still no folder.  I deleted a folder in /mnt.  Went back to GPARTED and deleted and recreated.  In LUBUNTU is a utility called DISK.  It is similar to GPARTED.  There, I set some 'automount' parameters.  Still no folder.  Rebooted, and Bingo .. there is a folder in /media/wacojohn called 1GBFLASH.  I do NOT remember the order in which I did all this.

The one thing I have not done is the chown instruction you gave.  Do I still need to do that??  Do I need to be in a particular folder/directory when I do it?  Maybe DISK does that already(?????)

here is the current df

```
wacojohn@ubuntuCOMPAQ:~$ df
Filesystem        1K-blocks      Used    Available Use% Mounted on
/dev/sda1           8970452   2567416      5940700  31% /
none                      4         0            4   0% /sys/fs/cgroup
udev                 245276         4       245272   1% /dev
tmpfs                 50704       760        49944   2% /run
none                   5120         0         5120   0% /run/lock
none                 253512         0       253512   0% /run/shm
none                 102400         8       102392   1% /run/user
/dev/fuse      101074887820 240204564 100834683256   1% /media/pogoplug
/dev/sdb1            963544      1204       913396   1% /media/wacojohn/1GBFLASH

```

Here are the permissions for /media/wacojohn/1GBFLASH

Owner root
Group root
View Content anyone
Change Content only owner
Access Content anyone

---

### Post by ajgreeny on 2013-09-16
At the moment I have two comments to make.

First an apology for forgetting that usb drives now automount at /media/user/mountpoint.  This is a change from ubuntu versions up to and including 12.10, where it was direct in /media/mountpoint, and if the usb was labelled the mountpoint would be the same as the label.

You say:-
"Bingo .. there is a folder in /media/wacojohn called 1GBFLASH.  I do NOT remember the order in which I did all this."
This is good news as it means that the partition has been made and is now mounted at /media/wacojohn/1GBFLASH as it should be.  If that partition is ext2, ext3 or ext4 you will need to run the **chown** command I mentioned on the mountpoint for you to be able to write to it as user; if it's fat32 you do not need to run that command, nor do you, I think, if it's ntfs, but I am not 100% sure about ntfs.

I also see in your first df output
```
/dev/sdb1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
/dev/sdd1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
```
which is really the wrong mountpoint for a usb drive which will always automount as /media, not /mnt, and I am wondering if your system has been confused as, I may have been, by this unusual mountpoint being used.

---

### Post by WacoJohn on 2013-09-16
> **ajgreeny said:**
> At the moment I have two comments to make.

First an apology for forgetting that usb drives now automount at /media/user/mountpoint.  This is a change from ubuntu versions up to and including 12.10, where it was direct in /media/mountpoint, and if the usb was labelled the mountpoint would be the same as the label.

No one has to apologize for helping me (unless it is to themselves ... HAH!!).  I appreciate your efforts.

> You say:-
"Bingo .. there is a folder in /media/wacojohn called 1GBFLASH.  I do NOT remember the order in which I did all this."
This is good news as it means that the partition has been made and is now mounted at /media/wacojohn/1GBFLASH as it should be.  If that partition is ext2, ext3 or ext4 you will need to run the **chown** command I mentioned on the mountpoint for you to be able to write to it as user; if it's fat32 you do not need to run that command, nor do you, I think, if it's ntfs, but I am not 100% sure about ntfs.

That partition is ext2.  I will next run the chown command.  I just hope I run it correctly.

> I also see in your df output
```
/dev/sdb1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
/dev/sdd1            963544      1204       913396   1% /mnt/usb-_Easy_Setup_Key_07A60409B21BCC81-0:0-part1
```
which is really the wrong mountpoint for a usb drive which will always automount as /media, not /mnt, and I am wondering if your system has been confused as, I may have been, by this unusual mountpoint being used.

That is an earlier output .. before I stumbled along fixing things.  Notice the latter and final output.  I think I am OK as long as I run chown correctly.  Does this look right AND can I run it in terminal from any prompt???:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo chown wacojohn:wacojohn /media/1GBFLASH[/FONT][/COLOR]
```

---

### Post by ajgreeny on 2013-09-16
[FONT=verdana][COLOR=#000000]Not quite.  It needs to be
```
sudo chown wacojohn:wacojohn /media/wacojohn/1GBFLASH
``` just like it is in the last line of your final df output.

You can run it from your own user's terminal without a problem, and if you get no output, but straight back to the prompt, then it has worked as it should.  Now when you insert the drive it should mount automatically to that **/media/wacojohn/1GBFLASH** folder and as that now belongs to you you should be able to write to it as user.
[/COLOR][/FONT]

---

### Post by WacoJohn on 2013-09-17
That did the job, .. and we are done.  Thank you .. you have been immeasurably helpful and I have learned a lot.  Thank you again.

---

### Post by ajgreeny on 2013-09-17
You are very welcome.

---

