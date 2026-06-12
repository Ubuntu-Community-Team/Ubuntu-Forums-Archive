---
title: "[SOLVED] Mounting Floppy Drive"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by bj218 on 2008-08-31
How do I Mount my floppy drive?

---

### Post by nitro_n2o on 2008-08-31
do u mean an external one? 
the internal one should automatically mount!

---

### Post by falcon61102 on 2008-08-31
The first thing I would do is look under the Places menu and see if it's listed there.

If not, then you can try to manually mount it.  Your floppy is going to be something like /dev/fda1, to check that, go to your terminal and run:
```
sudo fdisk -l
```
-l being a lower case L

It should show up there.  Once you determine what it's being called you can mount it.  First you need to create a location for you to mount to, then actually mount it.  To do this, use:
```
sudo mkdir /media/Floppy
sudo mount /dev/fda1 /media/Floppy
```

Your floppy drive should then mount.  But like nitro_n2o mentioned, if it's an internal it should automount.

---

### Post by billgoldberg on 2008-08-31
> **bj218 said:**
> How do I Mount my floppy drive?

Double click on the icon it will put on your desktop.

---

### Post by bj218 on 2008-09-01
> **falcon61102 said:**
> The first thing I would do is look under the Places menu and see if it's listed there.

If not, then you can try to manually mount it.  Your floppy is going to be something like /dev/fda1, to check that, go to your terminal and run:
```
sudo fdisk -l
```
-l being a lower case L

It should show up there.  Once you determine what it's being called you can mount it.  First you need to create a location for you to mount to, then actually mount it.  To do this, use:
```
sudo mkdir /media/Floppy
sudo mount /dev/fda1 /media/Floppy
```

Your floppy drive should then mount.  But like nitro_n2o mentioned, if it's an internal it should automount.

I could not find it in fdisk.

When I go to Places then to Computer and double clk on the floppy drive icon I get a small window that says “Unable to mount location” ”no media in the drive” I then put a disk in the drive and double clk the icon again this time I get a small window that says “Unable to mount location” ”can't mount file”. In the Floppy File Browser window I see what is on the floppy. I close this window and now the Computer File Browser  no longer shows the floppy icon but a new icon that looks just like a floppy
disk that is labeled “BM70_Disk_1”. I then removed this disk and put in a different one, when I double clk on this new floppy icon I get the info that was on the first disk not what is on this disk. Since the original floppy icon is no longer shown in the Computer File Browser window how do I get to see what is on this second disk?
 
On bootup if go to Places then Removable Media I see Floppy Drive but when Iclk on it nothing, but if I clk on one of the other items in the list it goes to the desktop. After I go through the exercise above if I go to Places then to Removable Media the Floppy Drive words have been replaced with BM70_Disk_1 if I clk on this it goes to the desktop!!

---

### Post by bj218 on 2008-09-02
I tied to mount the floppy as you suggested but no luck. Here is what I got.

bill@bill-desktop:~$ sudo mkdir /media/Floppy
[sudo] password for bill: 
bill@bill-desktop:~$ sudo mount /dev/fda1 /media/Floppy
mount: special device /dev/fda1 does not exist
bill@bill-desktop:~$


Should fda1 be fda0?


bill@bill-desktop:~$ sudo su
root@bill-desktop:/home/bill# sudo mkdir /media/Floppy
mkdir: cannot create directory `/media/Floppy': File exists
root@bill-desktop:/home/bill# sudo mount /dev/fda1 /media/Floppy
mount: special device /dev/fda1 does not exist
root@bill-desktop:/home/bill#

---

### Post by falcon61102 on 2008-09-02
Try /dev/fd0 instead of fda1.

Also look in your fstab to see if your floppy is listed.  You can view it with:
```
cat /etc/fstab
```

---

### Post by bj218 on 2008-09-04
I do not seem to being doing very well here are my latest results.

bill@bill-desktop:~$ sudo su
[sudo] password for bill: 
root@bill-desktop:/home/bill# sudo mkdir /media/Floppy
mkdir: cannot create directory `/media/Floppy': File exists
root@bill-desktop:/home/bill# sudo mount /dev/fda0 /media/Floppy
mount: special device /dev/fda0 does not exist
root@bill-desktop:/home/bill# sudo mount /dev/fda1 /media/Floppy
mount: special device /dev/fda1 does not exist
root@bill-desktop:/home/bill# sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=e2c057b4-5682-4789-b564-d2369e769c9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
root@bill-desktop:/home/bill# 

Does the above help any with my problem?

---

### Post by falcon61102 on 2008-09-04
The second to last line in that code you posted is the fstab entry for your floppy drive.  I looks right from what I can tell.  Are you able to test the drive in another OS to see if it might be hardware related?

---

### Post by plucky on 2008-09-04
> bill@bill-desktop:~$ sudo su
[sudo] password for bill:
root@bill-desktop:/home/bill# sudo mkdir /media/Floppy
mkdir: cannot create directory `/media/Floppy': File exists
root@bill-desktop:/home/bill# sudo mount /dev/fda0 /media/Floppy
mount: special device /dev/fda0 does not exist
root@bill-desktop:/home/bill# sudo mount /dev/fda1 /media/Floppy
mount: special device /dev/fda1 does not exist


1) **sudo su** puts you into "super user" mode as denoted by the # before every line.

2) When you are in "super user" mode you don't need to use sudo before the commands.

3) To mount a floppy,you don't need to be in "super user" mode

4) For a floppy it is not /dev/fda0 but it is **/dev/fd0** so use command ```
mount /dev/fd0
``` and that is a zero not a letter o

5) After you have finished using the drive,you have to un-mount it before removing the disk,or else the system will still think the original disk is in the drive. Use ```
umount /dev/fd0
``` **It is umount not unmount** 

6) You cannot umount the floppy if a process is accessing the drive i.e the file browser window or terminal window is accessing the drive.

For example:-
> :~$ mount /dev/fd0
:~$ cd /media/floppy0
:/media/floppy0$ ls
intels21.cat  intels22.inf  u2kg54
intels21.inf  intels.wwh    U2KG54_1-01-02-0002.zip
:/media/floppy0$ umount /dev/fd0
umount: /media/floppy0: device is busy
umount: /media/floppy0: device is busy
:/media/floppy0$ cd
:$ umount /dev/fd0
:$

Good Luck

---

### Post by bj218 on 2008-09-05
> **falcon61102 said:**
> The second to last line in that code you posted is the fstab entry for your floppy drive.  I looks right from what I can tell.  Are you able to test the drive in another OS to see if it might be hardware related?

I noticed there is a difference in the way I have entered the floppy drive, it looks to me like I should enter it as /dev/fd0 not /dev/fda0. Would the a after fd louse things up?
The floppy works great on windows.

---

### Post by falcon61102 on 2008-09-05
fda is not correct, it was just a guess on my part on what your floppy drive is called by Ubuntu.  The actual name is fd0.

---

### Post by bj218 on 2008-09-07
> **falcon61102 said:**
> fda is not correct, it was just a guess on my part on what your floppy drive is called by Ubuntu.  The actual name is fd0.

bill@bill-desktop:~$ sudo mount /dev/fd0 
[sudo] password for bill: 
mount: /dev/fd0 is not a valid block device 
bill@bill-desktop:~$ 

What is a valid block device?


I think I do not understand the big picture. Maybe I should start all over!! First all the floppy I have were made in Windows ie fat32, which might explain some of my problems. I went to synaptic pk mgr and did a search ie "mount floppy" it said there is a program to read DOS floppy disk's. I did not go any further. Should I have synaptic install this
prog?
Can I make floppies on Ubuntu and format them ETC3? I have a lot of personal data on floppies that I would like to keep up to date.

---

### Post by plucky on 2008-09-07
> bill@bill-desktop:~$ sudo mount /dev/fd0
[sudo] password for bill:
mount: /dev/fd0 is not a valid block device
bill@bill-desktop:~$

What is a valid block device?


I get that error if there is no floppy in the drive.


The commands to format a floppy are ```
mkfs -t ext2  /dev/fd0  #For ext2
mkfs.vfat  /dev/fd0   #For Fat32
```

and you don't need the **sudo** before the mount command.

Good Luck

---

### Post by bj218 on 2008-09-07
> **plucky said:**
> I get that error if there is no floppy in the drive.


The commands to format a floppy are ```
mkfs -t ext2  /dev/fd0  #For ext2
mkfs.vfat  /dev/fd0   #For Fat32
```

and you don't need the **sudo** before the mount command.

Good Luck

bill@bill-desktop:~$ mount /dev/fd0 /media/Floppy0
mount: only root can do that
bill@bill-desktop:~$ sudo su
[sudo] password for bill: 
root@bill-desktop:/home/bill# mount /dev/fd0 /media/Floppy0
mount: block device /dev/fd0 is write-protected, mounting read-only
root@bill-desktop:/home/bill# 

what did I do wrong here I put in 1 of my floppies. If I put in a blank
floppy that is not write protected would this make it so I can read and write to floppies that have been formated FAT32?

---

### Post by plucky on 2008-09-07
The command is ```
mount /dev/fd0
```


> what did I do wrong here I put in 1 of my floppies. If I put in a blank floppy that is not write protected would this make it so I can read and write to floppies that have been formated FAT32? 

You need to format a floppy before you can read/write to it.Is the floppy write protected?

If the floppy you have put in is already formatted as FAT32, then the above command will mount it.Don't forget to un-mount it before removing the disk with the command ```
umount /dev/fd0
```

---

### Post by bj218 on 2008-09-08
When I go to Places/Removable Media/Floppy and clk on "floppy Drive" I get nothing but when I clk on any other item in the list it opens the item and also puts the icon on my desktop. When I go to "Computer" and clk clk on the floppy icon I get a small window that says "unable to mount location".
Is there any way I can  use the floppy drive like I did in windows?

---

### Post by plucky on 2008-09-09
Lets go back to basics.Get a blank floppy or one that you can over write.

Open a terminal and ```
id
``` and you should see "25(floppy)" in the list.This means you should have access to the floppy drive

Place floppy in drive and from a terminal window copy and paste these commands one at a time```
mkfs.vfat /dev/fd0
mount /dev/fd0
```

A floppy icon should appear on your desktop.If it doesn't or you get any errors in the previous two commands,copy the error messages back to this thread.

If the icon appears,double click on it and the Nautilus file manager window will open.Try to copy a file or two to the floppy.

If that works,remember to un-mount the drive before removing the floppy with ```
umount /dev/fd0
```

Also remember in the terminal linux is case sensitive.


Good Luck

---

### Post by Shobuz99 on 2008-09-09
plucky,
I have a similar problem. My floppy will not mount.
It gives me this popup error when I click the icon to mount the drive:
[B]Unable to Mount the selected floppy drive
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: I could not determine the file system type, and none was specified[/B]

I also tried your previous suggestion. 
I opened a terminal and typed id. This is what I got back:
[B]rick@rick-desktop:~$ id
uid=1000(rick) gid=1000(rick) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),
105(scanner),107(fuse),109(lpadmin),115(admin),1000(rick)
rick@rick-desktop:~$
[/B]
Then I tried the commands you suggested next, one at a time.
The first one gave me this error:
[B]rick@rick-desktop:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0[/B]

Obviously, I couldn't try the second one. What did I do wrong?

Thanks for your help
Rick (shobuz99)

---

### Post by plucky on 2008-09-09
> rick@rick-desktop:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0


Can you post the output of ```
cat /etc/fstab
```

---

### Post by bj218 on 2008-09-09
> **plucky said:**
> Lets go back to basics.Get a blank floppy or one that you can over write.

Open a terminal and ```
id
``` and you should see "25(floppy)" in the list.This means you should have access to the floppy drive

Place floppy in drive and from a terminal window copy and paste these commands one at a time```
mkfs.vfat /dev/fd0
mount /dev/fd0
```

A floppy icon should appear on your desktop.If it doesn't or you get any errors in the previous two commands,copy the error messages back to this thread.

If the icon appears,double click on it and the Nautilus file manager window will open.Try to copy a file or two to the floppy.

If that works,remember to un-mount the drive before removing the floppy with ```
umount /dev/fd0
```

Also remember in the terminal linux is case sensitive.


Good Luck

bill@bill-desktop:~$ id
uid=1000(bill) gid=1000(bill) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(bill)
bill@bill-desktop:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
bill@bill-desktop:~$ mount /dev/fd0
bill@bill-desktop:~$ 
I did the 2 commands you suggested and it worked I was able to read and write to a floppy. Thank You

Today by accident I was messing around in "COMPUTER"  and I rt clked the floppy icon and the dropdown menu had an item "Mount Volume" I clked on it and it worked. After mounting the floppy I was able to read it. I did not try to write to it. I
then rt clked the floppy icon again and the dropdown muneu now has an item "Unmount Volume" I clked on it and that worked also. I still do not under stand why you have mount and unmount the floppy. I would think once it was mounted it would be available to use at any time in the future, Do you have to do the same thing with your CD drive? I think I need to do a bit more checking before I cause any more trouble.

---

### Post by Kellemora on 2008-09-09
Hi BJ

I found the answer in a post made here on October 26, 2006!

Here is what I had to do:

Open your /etc/fstab

It should look like the below /fstab taken from my computer, the changes are noted in the file itself.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7196d168-75bc-4ff9-ad09-91b77abb1acf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8ee0a603-6865-495e-9e70-ecc8e0174796 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# above line was the original entry for the floppy drive
# line below is the new line I added also added exec and utf8 to new line below
/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0 0

BJ, the line directly ABOVE this line is how it reads AFTER I changed it, twice.
The directions I got read this way:
/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext rw,user,noauto 0 0 
I added the ,exec,utf8 because the old original line had it in it.  If your's don't have it in it, I wouldn't add it, since I have no idea what it's for.

TTUL
Gary

---

### Post by Shobuz99 on 2008-09-09
> **plucky said:**
> Can you post the output of ```
cat /etc/fstab
```

Yep. Here it is:

rick@rick-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bb89afd-e18e-4e91-8a66-2394af41fb39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2c971fda-b03b-46a2-8df4-5fbdcdad5b68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
rick@rick-desktop:~$ 

What should I change?

Thank you for your help
Rick (shobuz99)

---

### Post by Kellemora on 2008-09-09
Hi Rick

Replace the line /def/fd0  etc.  with the following line and it should work!

/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0 0

TTUL
Gary

---

### Post by plucky on 2008-09-10
> rick@rick-desktop:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

I think you need to un-mount the drive ```
umount /dev/fd0
``` notice no n in umount and then try the **mkfs.vfat** command.

 > /dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

That is the same as mine.(See "man mount" for fstab options)

----------------------------------------------------------------------------------------------------------------
@BJ
> I still do not under stand why you have mount and unmount the floppy. I would think once it was mounted it would be available to use at any time in the future, Do you have to do the same thing with your CD drive?


There is no auto mount in linux like there is in windows and so mounting and un-mounting tells the system when a new disk is available.
Try mounting a floppy and then removing it without un-mounting and see what happens.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
@Kellemora

Do you know what those options are for?

---

### Post by Shobuz99 on 2008-09-10
> **plucky said:**
> I think you need to un-mount the drive ```
umount /dev/fd0
``` notice no n in umount and then try the **mkfs.vfat** command.
That is the same as mine.(See "man mount" for fstab options)

----------------------------------------------------------------------------------------------------------------
@BJ

There is no auto mount in linux like there is in windows and so mounting and un-mounting tells the system when a new disk is available.
Try mounting a floppy and then removing it without un-mounting and see what happens.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
@Kellemora

Do you know what those options are for?


Plucky,
 did what you suggested and I'm still gettin the errors:

rick@rick-desktop:~$ umount /dev/fd0
umount: /dev/fd0 is not mounted (according to mtab)
rick@rick-desktop:~$ mkfs.vfat /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

What is mtab and how do I edit the options referred to
in Kellemora's post?:

Re: Mounting Floppy Drive
Hi Rick

Replace the line /def/fd0 etc. with the following line and it should work!

/dev/fd0 /media/floppy0 auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0 0

TTUL
Gary 

Rick (shobuz99)

---

### Post by plucky on 2008-09-10
> What is mtab and how do I edit the options referred to
in Kellemora's post?:


mtab shows mounted partitions ```
cat /etc/mtab
``` will show what partitions you have mounted.

To edit the options you open a terminal and ```
sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab
```
Those commands will make a copy of your fstab file and then open the file with the gedit editor.You make the changes there.

No harm in trying,but I still think your system thinks the floppy is mounted.

Can you post output of ```
sudo file -s /dev/fd0
ls -l /dev/fd0
cat /etc/mtab
```

Good Luck

---

### Post by pzs on 2008-09-10
Many moons ago, we used to use mtools to access floppy drives. It emulates DOS commands and allows you to access your floppy disk drive using them. You could do things like:

mcopy A:* ~/fdiskcontents/

I haven't tried it for a while and don't have a floppy drive on this machine, but it might be worth a try. mtools is in the package repository.

---

### Post by Kellemora on 2008-09-10
Hi Plucky

I honestly have no idea, I'm so Noob I'm using these boards to get my machine up and running too.
Once I finally found what worked and saw others asking the same question, I just posted what I learned from here to save them the trouble of trying to find it themselves.

I just figured, if it WAS in my original line, why not put it back into the new line and try it.  I tried it both ways, with and without the extra two words.  So I have no idea what they do YET, but I'm sure I'll find out.

I will say one thing!
Ubuntu users seem to be the most informative and helpful folks around!
No wonder Ubuntu climbed to the #1 position so fast!!!!!

TTUL
Gary

---

### Post by Shobuz99 on 2008-09-10
> **plucky said:**
> mtab shows mounted partitions ```
cat /etc/mtab
``` will show what partitions you have mounted.

To edit the options you open a terminal and ```
sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab
```
Those commands will make a copy of your fstab file and then open the file with the gedit editor.You make the changes there.

No harm in trying,but I still think your system thinks the floppy is mounted.

Can you post output of ```
sudo file -s /dev/fd0
ls -l /dev/fd0
cat /etc/mtab
```

Good Luck

Plucky,
Ok. here are the results from the commands you suggested I try:

rick@rick-desktop:~$ sudo file -s /dev/fd0
[sudo] password for rick: 
/dev/fd0: ERROR: cannot read `/dev/fd0' (Input/output error)

rick@rick-desktop:~$ ls -l /dev/fd0
brw-rw---- 1 root floppy 2, 0 2008-09-10 05:13 /dev/fd0

rick@rick-desktop:~$ cat /etc/mtab
/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-18-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/rick/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=rick 0 0
/dev/sdc /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda1 /media/Local\040Disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
rick@rick-desktop:~$ 

there ya go..
BTW.. I think you're riht that it is mounted; BUT
that's not what the error messages have been telling me...
Maybe errors are issued when you try to mount an already mounted drive?

I'm also wondering if this drive is not a 1.44MB drive and is really a 720KB drive. Is there a possibility that the drive is not able to read 1.44MB disks?

Rick (shobuz99)

---

### Post by plucky on 2008-09-10
> mount: /dev/fd0 already mounted or /media/floppy0 busy
mount: according to mtab, /dev/fd0 is already mounted on /media/floppy0



That is the error I get when I try to mount and already mounted drive.

> I'm also wondering if this drive is not a 1.44MB drive and is really a 720KB drive. Is there a possibility that the drive is not able to read 1.44MB disks?


That would make it a very old drive.Wouldn't the mkfs.vfat still work as it is trying to format the disk? 

Unless the geometry of the floppy is incorrect.Don't know as never tried it.

Is there any other way of testing the drive?
Do you have an old windows boot floppy?
Can you boot from it?

---

### Post by bj218 on 2008-09-10
Today by accident I was messing around in "COMPUTER" and I rt clked the floppy icon and the dropdown menu had an item "Mount Volume" I clked on it and it worked. After mounting the floppy I was able to read it. I did not try to write to it. I
then rt clked the floppy icon again and the dropdown muneu now has an item "Unmount Volume" I clked on it and that worked also. I still do not under stand why you have mount and unmount the floppy. I would think once it was mounted it would be available to use at any time in the future, Do you have to do the same thing with your CD drive? I think I need to do a bit more checking before I cause any more trouble.

I posted the above yesterday. Today (sept 10) I spent about an hour and half messing around with the floppy drive. I used fat32 formated disks some blank some with data. AS near I can tell the Mount and Unmount worked great. However one thing I noticed is if the disk is write protected when you mount it , it is mounted as a read only disk. My problem now is I can not figure out how to copy data from a hard drive partition to the floppy (this was easy in Windows) Copy and Paste does not seem to work in Ubuntu.

---

### Post by Kellemora on 2008-09-10
Hi BJ

When you MOUNT the Floppy, a linked icon of it appears on your desktop for easy access.
With it ON the desktop, you CAN drag files and folders to it and it will write them IF you have given write permission to the floppy itself.

I have about 100 2 meg floppy disks and no way to use them in Ubuntu, it recognizes 1.28 1.44, 1.45 and 2.88 but NOT 2.00

The other thing I've discovered is that you cannot format a floppy the proper way from the command line.

It will accept fdformat /dev/fd0 but not the proper /dev/fd0H1440 says file or directory not found, instead of formatting the drive.
It's the same way in almost all Debian based releases.
In Red Hat (but NOT CentOS) you can format every size floppy ever made, even the old 8 inch jobs if you download the driver for them.

Once you get used to the differences between WinDoze and Linux, you'll come to appreciate the GREATER CONTROL you have over the processes in Linux.  The bummer is LEARNING just WHAT those controls are and how to implement them properly.

A good place to learn about the Debian based platform is O'Reilly online.  I've found more good Noob stuff there than in all the expensive books I have purchased.

TTUL
Gary

---

### Post by bj218 on 2008-09-11
Hi Kellemora

I just tried the drag and drop method to copy some data and it worked great
THANK YOU.
I noticed that when I clk on"Mount Volume" the floppy drive light comes ON
and runs about 20 sec. which seems like a long time but not a problem, this
sure beats using the command line method. Also I noticed when I clk  
"Unmount Volume" the floppy light does not come ON at all!!
I think I am going to keep Windows on my computer for some time as it does 
do some things easily like format floppies for one.
Thanks for the O'Reilly Online tip to get their is it "www.o'reilly online.com"?  AGAIN THANKS FOR THE HELP

---

### Post by Kellemora on 2008-09-11
Hi BJ

Glad it worked for you!

FWIW:  I forgot that O'Reilly does not have anything Ubuntu specific.
They do have a Debian book I can get into without being a paying member, thanks to a link from someone else.
Unfortunately, it's NOT in this instance of Ubuntu so I can't get to it right now.

Do we have PM like messages here?  If not, I'm pretty sure I put my e-mail address in my profile here.  I'm new here too and don't know how everything works yet.
I also don't want to publish a password coded URL that belongs to someone else in public.  

I'm working from an OLDE 4 gig hard drive I loaded Ubuntu onto for another computer that has no CDs or much of anything else in it for that matter so I could do some testing of things I wanted to try without messing up my other big hard drive.

In any case, send me a PM and I'll track down the url and get back to you.

TTUL
Gary

---

### Post by Shobuz99 on 2008-09-11
> **plucky said:**
> mtab shows mounted partitions ```
cat /etc/mtab
``` will show what partitions you have mounted.

To edit the options you open a terminal and ```
sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab
```
Those commands will make a copy of your fstab file and then open the file with the gedit editor.You make the changes there.

No harm in trying,but I still think your system thinks the floppy is mounted.

Can you post output of ```
sudo file -s /dev/fd0
ls -l /dev/fd0
cat /etc/mtab
```

Good Luck

Plucky,
Yep..it was the floppy drive...piece of crap.
I removed it, found another one in my computer pile,
and installed it. It seems to work, except I get a strange error message:
"[B]Cannot mount volume
You are not privileged to mount this volume[/B]"

The green light comes on and it attempts to read the 1.44MB disk
(which is the size it's set up for in my BIOS).
Then the error message pops up...
The drive is still mounted, regardless of the message....weird..
Won't list the contents of the diskette either..

yet if I set the bios to boot from the floppy and
put the same diskette in, it reads the file and lists contents
in a terminal session (like DOS does) and shows an "A:" prompt..
Any ideas?
Thanks for all of your help previously, as well.
Sorry it was for naught because I had a dead floppy drive..

Rick (shobuz99)

---

### Post by plucky on 2008-09-12
Did you change your fstab as advised by Kellemora?

If so change it back to original and try again,as your problem was the drive itself and not the fstab line.

I assume the floppy was dos format,so it should mount.

Good Luck

---

### Post by Shobuz99 on 2008-09-12
> **plucky said:**
> Did you change your fstab as advised by Kellemora?

If so change it back to original and try again,as your problem was the drive itself and not the fstab line.

I assume the floppy was dos format,so it should mount.

Good Luck

Yep. You're right! It works now.
I changed the fstab back to its original setup
for the floppy:
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

No errors. 
Thanks for everything Plucky
Thanks to everyone else for their suggestions and experiences as well.

Rick (shobuz99)

---

### Post by AlanInVancouverBC on 2008-09-14
There is an applet "Disk Mounter" that I downloaded and installed on the "taskbar". I can't find it in Synaptic or Applications/Add-Remove. I don't remember where I got it from, but it works.
I have spent about 3 hours figuring out how/when to mount and unmount and how/when to format floppies.
1. I can mount only a FAT-formatted floppy; I cannot mount a Linux Native (ext2) formatted floppy (I don't understand why).
2. I can only format when the drive is "unmounted" (I don't understand that.)
3. I also don't understand why the drive(s) don't stay mounted always, a la Windows.

---

