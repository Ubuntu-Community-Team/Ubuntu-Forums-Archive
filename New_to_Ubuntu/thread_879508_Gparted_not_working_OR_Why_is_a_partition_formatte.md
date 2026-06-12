---
title: "Gparted not working? OR Why is a partition formatted to ext3 still saying its NTFS?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-08-04
This is another in a long ling of strange things that Ubuntu seems to do, though I havent given up on it and im trying to learn, I really feel hobbled in my actions.

Ok, so I got the NTFS drive to be mountable and I pulled the info I needed from the drive, then I installed gparted and deleted the NTFS drive and reformatted, first as FAT32 but when I applied the changes etc and went to click on the newly formatted drive I get this error ... (see pic below)

[http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpg](http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpg)
[IMG]http://http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpg[/IMG]

Apparently my computer still thinks its an NTFS?!?! I even restarted the computer thinking that maybe I missed something but no, ubuntu still tells me that it cant mount the drive because its NTFS, then I go into gparted again and its telling me the whole drive is formatted to ext3 (I changed from fat32 to ext3 thinking maybe it would work, no dice).

What in the world is going on here?

---

### Post by Sef on 2008-08-04
> Ok, so I got the NTFS drive to be mountable and I pulled the info I needed from the drive, then I installed gparted and deleted the NTFS drive and reformatted, first as FAT32 but when I applied the changes etc and went to click on the newly formatted drive I get this error ... (see pic below)

The drive needs to be unmounted if you are going to partition or reformat it. 

No pic is attached.

---

### Post by Rocket2DMn on 2008-08-04
Are you running gparted with gksudo?  You should be.  Then as Sef said, the drive has to be unmounted before you can do anything with it.  (OP attached image link)

---

### Post by VitaminBB on 2008-08-04
> **Rocket2DMn said:**
> Are you running gparted with gksudo?  You should be.  Then as Sef said, the drive has to be unmounted before you can do anything with it.  (OP attached image link)

Yup, I unmounted it ... 

[B]I just ran gparted with gksudo, erased the drive then formatted FAT32, STILL says  "unable to mount volume unpriviledged user can not mount NTFS block devices ....." 
[/B]
I think this might be related to the fact that one part of the partition wouldnt disappear before, even when i unplugged the external drive all together.

Also even though I get an error saying the drive cant be mounted because its NFTS (even after I formatted it to FAT32 in gparted and applied the changes) I now cant mount that drive at all.

This is confusing to explain ...

Follow me though, I had a NTFS drive, I figured out how to mount it and took the important info from it and then using Gparted I wiped the drive clean and formatted it with FAT32, for some reason my computer still thinks the drive is formatted NTFS despite Gparted showing otherwise, also the technic I used for mounting the drive when it was NTFS isent working now so I have zero access to what should be a formatted FAT32 drive.

****!

---

### Post by Rocket2DMn on 2008-08-04
If you were prompted for a password from System->Administration->Partition Editor then you are already using gksu/gksudo.  Otherwise you can start it from a terminal
```
gksudo gparted
```

---

### Post by VitaminBB on 2008-08-04
> **Sef said:**
> The drive needs to be unmounted if you are going to partition or reformat it. 

No pic is attached.

Ya for some reason the image wouldnt attach, thats why i put the link [http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpg](http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpghttp://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.jpg)

---

### Post by ajgreeny on 2008-08-04
Seems strange, but as another option, try running gparted from the ubuntu liveCD.  Then attach the external drive (it is an external drive, isn't it?) make sure it is unmounted and then delete the partition(s) you want to change, and apply that before trying to make new partition(s) in whatever format you want.

EDIT
Just a thought; have you made sure the disk was removed ie unmounted or removed properly from windows before you tried to work on it?  NTFS drives are easy to upset as far as reading and mounting them in ubuntu, if they were removed improperly from windows; it seems to lock them and I wonder if that is stopping gparted from doing its business.

---

### Post by Rocket2DMn on 2008-08-04
Are you still having the problem?  If you can't get it to work from within Ubuntu, do what ajgreeny suggests and try using the LiveCD.  Remember, the drive must be unmounted before you can do anything to it.

---

### Post by VitaminBB on 2008-08-04
> **ajgreeny said:**
> Seems strange, but as another option, try running gparted from the ubuntu liveCD.  Then attach the external drive (it is an external drive, isn't it?) make sure it is unmounted and then delete the partition(s) you want to change, and apply that before trying to make new partition(s) in whatever format you want.

EDIT
Just a thought; have you made sure the disk was removed ie unmounted or removed properly from windows before you tried to work on it?  NTFS drives are easy to upset as far as reading and mounting them in ubuntu, if they were removed improperly from windows; it seems to lock them and I wonder if that is stopping gparted from doing its business.

Ok heres what I did ...

I plugged the external drive (yes it is external) into my windows laptop (old faithful) and formatted the drive as FAT32 with partitionmagic, oddly enough when I plugged in the ext drive my windows machine saw it labelled as an old folder that technically shouldnt have existed, that was weird, anyway, I formatted the drive and just plugged it into the ubuntu machine and it STILL wont work BUT there is progress, now the error I get says this ...

**"You are not privileged to mount the volume 'Osmosis'"**

I still think all of this is related to something I did earlier, I also notice that my main harddrive (internal with ubuntu os installed) is on the desktop and listed as ***"117.3 GB Media"*** which I find odd.

Something I did earlier trying to fix the other problems has created this issue,

Any ideas why I would get **"You are not privileged to mount the volume 'Osmosis'"** ?

---

### Post by Rocket2DMn on 2008-08-04
Superuser privileges are required to mount devices onto the filesystem.  For internal drives, this is easily accomplished by adding an entry to /etc/fstab where you can specify permissions.  I suggest against using FAT32 on external drives because of permission problems that some people have when trying to use them.  If the drive is ONLY going to be used in linux, I would format it with ext3 in GParted.  If you share it with Windows, I suggest NTFS.
What version of Ubuntu are you using?  When you plug the drive in to the computer, you MUST UNMOUNT IT before you can delete the existing partition and format it with a new filesystem.

For information about renaming the USB drive so that it doesn't show up as something like "WXY.Z GB MEDIA", see [uhelp]community/RenameUSBDrive[/uhelp]

---

### Post by Rolcol on 2008-08-04
What you can do is erase the first 512 Bytes (the MBR) of the hard drive to erase any partition info it has before working with GParted.

Steps: 
  1. Unmount the drive and find its device name (eg /dev/sdb)
  2. 
```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```
**[COLOR="Red"]BE CAREFUL! You may not want to use this method because if you choose the wrong drive (from step 1), you can ruin the MBR of your computer and not be able to boot an OS.[/COLOR]**

GParted should then see it as "unallocated".

---

### Post by ajgreeny on 2008-08-04
>  I formatted the drive and just plugged it into the ubuntu machine and it STILL wont workWhen you say, this you still give no indication of having first removed it properly in windows, so make sure you do this first before plugging it into ubuntu.

---

### Post by VitaminBB on 2008-08-04
> **ajgreeny said:**
> When you say, this you still give no indication of having first removed it properly in windows, so make sure you do this first before plugging it into ubuntu.

I guess im not sure what you mean.

Its an external drive, never had an os installed on it, just used for storage.

---

### Post by VitaminBB on 2008-08-04
> **Rocket2DMn said:**
> Superuser privileges are required to mount devices onto the filesystem.  For internal drives, this is easily accomplished by adding an entry to /etc/fstab where you can specify permissions.  I suggest against using FAT32 on external drives because of permission problems that some people have when trying to use them.  If the drive is ONLY going to be used in linux, I would format it with ext3 in GParted.  If you share it with Windows, I suggest NTFS.
What version of Ubuntu are you using?  When you plug the drive in to the computer, you MUST UNMOUNT IT before you can delete the existing partition and format it with a new filesystem.

For information about renaming the USB drive so that it doesn't show up as something like "WXY.Z GB MEDIA", see [uhelp]community/RenameUSBDrive[/uhelp]

This is confusing the heck out of me.

I would like to use this drive with windows at times (plugging it into my windows laptop).

I dont want to have to mount and unmount this external drive every single time I plug the usb in.

Lets say I format to NTFS then, how would I get Ubuntu to recognize this drive and mount it when I plug it in without always having to mount and unmount it manually?

This is pissing me off, I do one thing and then theres 3 things that go wrong and somehow I end up at the beginning.

All I want to do is plug in my damn external drive and have it recognized by Ubuntu, I cant phathom how this is such a difficult process, im a total linux retard but is there no way out there for me to tell this machine to simply mount the damn thing automatically without hassling me to death?

Ill log in as root constantly if I can avoid this sort of annoying crap.

I dont even know what step to take next now.

P.S. the XYZ. GB Media part I originally mentioned is my MAIN HARD DRIVE, I dont know how the hell it ended up on my desktop, that was a seperate question.

---

### Post by Rocket2DMn on 2008-08-04
OK calm down.  The drive should be automatically detected and mounted when you plug it.  Hence to format it, you must unmount it first.  Obviously, it doesn't always happen like this.  Plug your hard drive in and please post the output of the following commands
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by VitaminBB on 2008-08-04
> **Rocket2DMn said:**
> OK calm down.  The drive should be automatically detected and mounted when you plug it.  Hence to format it, you must unmount it first.  Obviously, it doesn't always happen like this.  Plug your hard drive in and please post the output of the following commands
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```




Ok, here is the full list, maybe someone else can make sense of it ...

> arghmonkey@Boontwo:~$ **sudo fdisk -l**
[sudo] password for arghmonkey: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb68f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   b  W95 FAT32


arghmonkey@Boontwo:~$** cat /etc/fstab**
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                                                     0  0  
# Entry for /dev/sda1 :
UUID=a619ae25-2e7b-4230-b681-be77c8e379c7  /               ext3         relatime,errors=remount-ro                                   0  1  
# Entry for /dev/sda5 :
UUID=ef65409c-a3b7-4875-825a-f3ae7efbdfa1  none            swap         sw                                                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                                        0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                                                     0  0  
/dev/sdc5                                  /media/sdc5     vfat         defaults                                                     0  0  
/dev/sda5                                  /media/sda5     swap         defaults                                                     0  0  
/dev/sdc1                                  /media/sdc1     ntfs         nls=iso8859-1,users,umask=000,user,ro                        0  0  
/dev/sdb5                                  /media/sdb5     vfat         uid=root,umask=227,gid=users,users,dmask=227,user,fmask=227  0  0  
/dev/sdb1                                  /media/Osmosis  ntfs         nls=iso8859-1,users,umask=000,user,ro                        0  0  


arghmonkey@Boontwo:~$ **sudo blkid**
/dev/sda1: UUID="a619ae25-2e7b-4230-b681-be77c8e379c7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ef65409c-a3b7-4875-825a-f3ae7efbdfa1" 
/dev/sdb5: LABEL="OSMOSIS" UUID="4896-F28B" TYPE="vfat" 


arghmonkey@Boontwo:~$ **mount**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arghmonkey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arghmonkey)
/dev/sdb5 on /media/sdb5 type vfat (rw)

---

### Post by CJ_Hudson on 2008-08-04
Yep file systems are the bane of my life too. How do you actually get a computer (Windows, Ubuntu etc.) to recognise and external drive as a drive on which you can install and uninstall programs anyway? i.e. could you install vital systems programs on an external drive (whether connected by Firewire or USB 2) or failing that simpler programs (e.g. games, word processor etc.)?
I love the concept or Random Access Memory though- remember the former versions of the Norton anti-virus which actually showed you the block-and-file memory locations on the screen in a kind of grid/graph as it scanned/fixed them in seemeingly endless random arrays? To me, however, the file management system, even the GUI Windows XP one for instance, seems far too complicated for the 'average' user to comprehend. To all computer designers/architects/programmers etc., get this all down to something s bit simpler, PLEASE!
Sorry if this sounds a bit basic, this Absolute Newbie talk is still way above my head!

---

### Post by jimv on 2008-08-04
Sigh.  No one caught that if you change your FS in gparted, you still have to change the fs in fstab.  Here's the offending line:

```
/dev/sdb1 /media/Osmosis ntfs nls=iso8859-1,users,umask=000,user,ro 0 0 
```

Change that to

```
/dev/sdb1 /media/Osmosis ext3 defaults 0 0
```

and I'll bet it works fine.

EDIT: Just noticed that you want to use it in Windows, and that this is a removable drive.  In that case, just delete the entries in fstab for your external drive.

---

### Post by Rocket2DMn on 2008-08-04
sdb1 is actually formatted as fat32 now, not ext3.

Assuming you don't have a second internal hard drive, you should comment out the entries in fstab so that hal can automount the external disk.  
```
gksudo gedit /etc/fstab
```
Now place a # at the front of the sdb1 and sdb5 lines.  The sdb1 partition is a logical partition.  Save and close.

I'm curious as to why there is still a second partition on the drive, I thought we had you delete all existing partitions and format the entire drive with one partition.  It's easiest to delete ALL partitions, including the extended one and just create a normal physical partition.

There is also and sdc1 entry in fstab what is this?  Do you have two internal hard drives?  If so, disregard the above advice and command out the sdc1 line instead (since this would be your external drive).  If so, then you didn't follow my directions correctly, b/c I told you to plug the drive in before running those commands.

---

### Post by VitaminBB on 2008-08-04
> **Rocket2DMn said:**
> sdb1 is actually formatted as fat32 now, not ext3.

Assuming you don't have a second internal hard drive, you should comment out the entries in fstab so that hal can automount the external disk.  
```
gksudo gedit /etc/fstab
```
Now plaec a # at the front of the sdb1 and sdb5 lines.  The sdb1 partition is a logical partition.  Save and close.

I'm curious as to why there is still a second partition on the drive, I thought we had you delete all existing partitions and format the entire drive with one partition.  It's easiest to delete ALL partitions, including the extended one and just create a normal physical partition.

There is also and sdc1 entry in fstab what is this?  Do you have two internal hard drives?  If so, disregard the above advice and command out the sdc1 line instead (since this would be your external drive).  If so, then you didn't follow my directions correctly, b/c I told you to plug the drive in before running those commands.

This is sounding encouraging.

There is only one internal drive (the hard drive) and the external drive in a usb enclosure.

I thought I did erase the external drive and format as FAT3 :O

Should I try what jimv recommends (making ext3 as fat32 of course) and see what happens?

---

### Post by Rocket2DMn on 2008-08-04
OK, first thing you should do is disconnect your external drive and comment out the entries in fstab for sdb1, sdb5, sdc1, and sdc5.

Now plug the external drive back in.  Does it work correctly?  Either way, please post the commands again so we have updated info
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
You will probably ultimately want to format the external drive as NTFS.  People argue between using FAT or NTFS, but I haven't really seen much reason to NOT use NTFS - it is newer and doesn't have the 4GB file size restriction.

One more reason I always promote using UUID over /dev locations...

---

### Post by VitaminBB on 2008-08-04
You guys are the best!

I made the changes and it all works!


So you have me convinced, I should use NTFS then, how hard is this going to be at this point to get my ubuntu to recognize and automount an ntfs external drive?

---

### Post by Rocket2DMn on 2008-08-04
It should be detected automatically, the same as fat32.  If you are using Feisty or Dapper, it may take a bit more config, but it's still easy.
You shouldn't need any of this, but you can have a look at
[uhelp]community/MountingWindowsPartitions[/uhelp]
[uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp]

---

### Post by VitaminBB on 2008-08-04
Just FYI to make sure theres nothing else missing ...
> 
**arghmonkey@Boontwo:~$ sudo fdisk -l**
[sudo] password for arghmonkey: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb68f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdb5               2       14593   117210208+   b  W95 FAT32


**arghmonkey@Boontwo:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                                                     0  0  
# Entry for /dev/sda1 :
UUID=a619ae25-2e7b-4230-b681-be77c8e379c7  /               ext3         relatime,errors=remount-ro                                   0  1  
# Entry for /dev/sda5 :
UUID=ef65409c-a3b7-4875-825a-f3ae7efbdfa1  none            swap         sw                                                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                                        0  0  
/dev/sda1                                  /media/sda1     ext3         defaults                                                     0  0  
#/dev/sdc5                                  /media/sdc5     vfat         defaults                                                     0  0  
/dev/sda5                                  /media/sda5     swap         defaults                                                     0  0  
  
#/dev/sdb5                                  /media/sdb5     vfat         uid=root,umask=227,gid=users,users,dmask=227,user,fmask=227  0  0  
#/dev/sdb1 /media/Osmosis fat32 defaults 0 0  


**arghmonkey@Boontwo:~$ sudo blkid**
/dev/sda1: UUID="a619ae25-2e7b-4230-b681-be77c8e379c7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ef65409c-a3b7-4875-825a-f3ae7efbdfa1" 
/dev/sdb5: LABEL="OSMOSIS" UUID="4896-F28B" TYPE="vfat" 


**arghmonkey@Boontwo:~$ mount**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arghmonkey/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arghmonkey)
/dev/sdb5 on /media/OSMOSIS type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by Rocket2DMn on 2008-08-04
Looks good.  You should be able to plug the drive in, unmount it, then format it with GParted again.  This time, make sure you delete the sdb5 AND the sdb1 logical partition.  Then you should NO partitions on the drive.  At this point, tell GParted to make a new partition using the entire space, make sure it is a physical partition (not logical), and format it as NTFS.  You should then be good to go.

---

### Post by VitaminBB on 2008-08-04
Heres the original problem again ...

It wont mount because it says its an NTFS volume (see pic below) ...

At this point now im assuming there is a simple fix.

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Untitled.jpg[/IMG]

---

### Post by VitaminBB on 2008-08-04
You know what, I followed what it said and safetly removed the hardware from the windows laptop and then plugged into ubuntu and it works now :)

Thank you again to everyone, especially rocket, much appreciated!

On to the next issue :)

---

### Post by Rocket2DMn on 2008-08-04
When you remove the drive from a windows computer, you need to make sure that you use the Safely Remove from the system tray, otherwise you will get this message every time.  You can't just unplug the drive immediately when you are done with it.
You can override the unclean shutdown in linux with the following command, but don't make a habit of it:
First create the temporary mount point (this only needs to be done once, ever)
```
sudo mkdir /media/external
```
Now you can force the drive to mount
```
sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force
```
Now unmount it (this must be done from the terminal since you mounted it from the terminal)
```
sudo umount /media/external
```
Now unplug the drive and plug it back in - it should automount.

Don't forget - safely remove from windows!

EDIT: Glad you got it working.

---

### Post by ajgreeny on 2008-08-05
If only the OP had noted my comments in the edit of post #7 a lot of time and trouble could have been saved!  When will people realise the problems of just pulling a USB drive from windows without properly removing it first?

---

