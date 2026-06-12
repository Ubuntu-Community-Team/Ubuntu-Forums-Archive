---
title: "access to second disk sdb"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by mike acker on 2012-10-13
ok, I got the additional SATA cables and hooked up the second disk.    got it formatted and created a partition -- type EXT4 -- which it selected apparently as the default.

now I can get it mounted but what do i do to grant permissions on it ?

I see the device is mounted and owned by /media/ -- which is owned by root.

so a SUDO command is going to be needed,--

can I sudo mkdir and then sudo chomod permission on that directory ?  if i sudo mkdir the new directory will be owned by root still,-- i think

---

### Post by sandyd on 2012-10-13
> **mike acker said:**
> ok, I got the additional SATA cables and hooked up the second disk.    got it formatted and created a partition -- type EXT4 -- which it selected apparently as the default.

now I can get it mounted but what do i do to grant permissions on it ?

I see the device is mounted and owned by /media/ -- which is owned by root.

so a SUDO command is going to be needed,--

can I sudo mkdir and then sudo chomod permission on that directory ?  if i sudo mkdir the new directory will be owned by root still,-- i think
Firstly, this assumes you have already added the partition to /etc/fstab to be automatically mounted

Do multiple users need to access the drive?

If not, chowning the drive to the user ```

chown -R user:user /path/to/mountpoint
```
should do it.

Otherwise, you can either

a) Create a group that can write to the folder, and add any user that wants to access the drive to the group.

```

chown -R root:**group_name** /path/to/mountpoint
chmod -R 770 /path/to/mountpoint

```

b) Just chmod to 777 - that will allow anyone to access it.

---

### Post by oldfred on 2012-10-13
You can manually mount it and set ownership and permissions. But if permanently installed you will want to add to fstab so it is automatically done on every reboot.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Manuallly - data partition only, not any system folders:
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
sudo chown $USER:$USER /mnt/data
#if not known to list partitions
sudo fdisk -l

sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.
Just be careful of -R or recursion. Only run that on a partition that you know is data only. Running it on a system folder may force a total reinstall.

Some detail on adding to fstab:
from Morbius1--
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

---

### Post by mike acker on 2012-10-14
thanks for some really good pointers to help here!!

I have to read my homework here and get to work!!

after all: I built my new u-box particularly because I wanted t learn!!

so, first things first: I'll have to learn to mount the drive.

one of the things that is hard, coming from the Windows environment is the language

the new drives are no longer C: and D: they are now /dev/sda/ and /dev/sdb/

next: there is disk utility . I get Disk Utility from the Dash Menu.  this allowed me to format the new drive -- which seems to be different from formatting a partition

Disk-U lets me create partitions, lots of different kinds:confused:

my general objective is to create a general use auxilliary area on my U-Box shared by selected  users of the U-box  and the Home Network -- which now contains 2 Windows and 2 U-boxes , a Kindle reader, and occasional guest machines all using my CISCO wireless hub

being as i will want to create shares in the new partition for Windows boxes I may decide on NTFS format partition

i believe the partition name combined with the drive name become the "mount point" e.g. /dev/sdab/A4SHARE1 -- if A4SHARE1 is the partition name -- which I create with Disk-U

I think from my early experiments I understand some of SAMBA,-- a Windows user needs to be assigned to a Ubox user (table update) and the Ubox user has to be assigned access to the area to be shared (table update)

the various updates -- starting with mounting the partition -- will probably have to be done from my admin logon using SUDO and GEDIT as this is a modification to the machine boot-up

hope everyone forgives me for "thinking out loud" here

---

### Post by mike acker on 2012-10-14
here is data from File System Table (fstab):
[FONT=Lucida Console]
[FONT=Courier New][SIZE=1]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8aaa7f1-28e7-4024-96c3-3fc4d898ad9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48eee500-b271-4e27-9e8b-d02e0326f8e4 none            swap    sw              0       0

[SIZE=1]~~~~~ 
[FONT=Arial][SIZE=2]me lost:(

[SIZE=2]Observations: I have no clue what to do with the above.

[SIZE=2]apparently the partition is mounted/not mounted -- based on the login user id: I am using 2 user IDs as generally suggested, 1 as administrator, and 2 as an ordinary use[SIZE=2]r.

[SIZE=2]when i log in as administrator it gives me access to the /dev/sdb1 partition. work[SIZE=2]ing from that i should be able to set up the share using SAMBA[/SIZE][/SIZE]. perhaps that is the best route to take.  if i remember [SIZE=2]right i have to install the samba service, create user id e[SIZE=2]quivalence entries and crea[SIZE=2]t[SIZE=2]e user group rights entries[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]
[/SIZE][/SIZE][/FONT][/FONT]

---

### Post by oldfred on 2012-10-14
With Ubuntu you do not need multiple logins. You just use sudo when you need to do administrative things. Other Linux' usually do have separate login & passwords for users and an admin.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

See previous post with link to  Morbius1 details on exactly how to copy & paste a new entry into fstab.

---

### Post by mike acker on 2012-10-14
RESOLUTION Part 1

Accessing the Windows Workgroup from UBOX

In order to get access to the Windows Workgroup I had to issue a CONNECT TO SERVER:


[LIST=1]
[*]on my Windows PC: press start menu, and type cmd to get terminal windows.  issue IPCONFIG command.  this will type out the IP address of my Windows Computer -- which is already running a shared WORKGROUP properly.
[*]on my U-Box: I had to open my "Home Folder", and at the top(menu) line select FILES and then CONNECT TO SERVER.  I have to enter the IP address of my Windows PC and select windows/share instead of FTP
[/LIST]
the above let's me see all of the root menu off my windows PC; I have to take care to select a directory I know is shared.

it is apparently necessary to re-issue the command following a new LOGON

RESOLUTION Part 2 : /dev/sdb

Evidently that 2d hard drive mounts automatically in the administrator account, only.  and it mounts as /media/<volume name> where <volume name> is the name of the volume I created on the disk using the Disk Utility.

at this point recall: I installed 2 Seagate 1TB baracuda drives in my new U-Box.  
I was only able to connect the first drive { /dev/sda } because only 2 SATA cables were shipped with the motherboard.  1 had to be used for the optical drive -- so i could load the UBUNTU install disk

so, eventually USPS gets the packet containing the 2 additional SATA cables.  I ordered SATA level 3 as these are backward compatible to the earlier levels. i don't know what level i have; hopefully level 3.

So, on receipt of the SATA cables I was able to cable up /dev/sdb drive.   following that I had to call the Disk Utility from the DASH menu and format the drive.  and then add a partition to it.

I added an NTFS partition because I have Windows computers in the net.

I also added the remaining 2 4GB ram chips bringing the system total to 16GB-- which appears to be completely un-necessary: the performance monitor usually shows me using between 1 and 2 GB

now, with the /dev/sdb drive formatted, volume name assigned, and a partition created I needed to determine how to control access

the volume that i created using my administrator account shows up using TERMINAL:
cd /media
ll
-- with my admin account -- as owner.  that being the case I can CD to the volume and issue another ll.  here i see the partition i created using the Disk Utility -- again -- with my admin account as owner.  Bear in mind here: multiple logins for this machine are required.

so far so good: I can now change the ownership and the permissions for the partition -- or-- for any folder in the partition. meaning I should be able to make it an "everyone" drive by just setting chmod 777

which leads us to the role of SAMBA -- and the mount problem. somehow i have to find the proper syntax for a mount command for fstab .  I think the windows workgroup needs a mount command as well.

~~

starting to dig thru this,... I found this explanation:
The standard form of the mount command, is


    mount -t type device dir 

This tells the kernel to attach the file system found on device (which is of type type) at the directory dir. The previous contents (if any) and owner and mode of dir become invisible, and as long as this file system remains mounted, the pathname dir refers to the root of the file system on device.
~~

-t type : indicates the type of partition being mounted. evidently this can be "auto" and LINUX will check and set the type

device : will be of the form /dev/sdb1 where /dev/ is a constant and /sd means SCSI(SATA) device ; b -- second SCSI device, 1 -- 1st partition on /dev/scb  ...

dir is the hard part to understand: the content of /dev/scb1 ( a SATA disk partition ) -- will be added to the Linux Files System Directory as /<dir> where <dir> is whatever name is to be used

now i have to figure out if there is just one fstab for the system -- or if each user has one that is applied at logon... ...and i have to figure out how SAMBA and CHMOD and CHOWN interact.  These seem to be 2 different systems for controlling access to a shared directory

more experiments tw  ...maybe i can figure out what parts of this i understand
~~~~~~~~~~~~~~~~~~
2012-10-15  MONDAY

my first experiment for this morning is to examine the existing /etc/fstab. and to find out if each user has their own copy of if this critter is owned by root.

accordingly, i went into my Ordinary user and, using terminal, issued 
gedit /etc/fstab

the table appeared as follows

[B]# /etc/fstab: static file system information. 
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8aaa7f1-28e7-4024-96c3-3fc4d898ad9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48eee500-b271-4e27-9e8b-d02e0326f8e4 none            swap    sw              0       0[/B]

To identify the table i added to the line 1 comment a note "user table", and attempted to save fstab.  this failed as the table is marked READ ONLY.  that's probably a Good Thing; helps to keep sailors like me from messing things up 

next, I scucrried over to my admin account and accessed the table via sudo:
sudo gedit /etc/fstab

uh oh, now I have lifted the safety; better be real carefull!  I added to the comment on line 1 SYSTEM MASTER TABLE and saved the table.  i then re-booted the system (it came up ok :-) and went to my ordinary account and accessed fstab via an ordinary edit:
gedit /etc/fstab

the result:[B]
# /etc/fstab: static file system information.   SYSTEM MASTER TABLE
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8aaa7f1-28e7-4024-96c3-3fc4d898ad9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48eee500-b271-4e27-9e8b-d02e0326f8e4 none            swap    sw              0       0[/B]

Conclusion: there is only 1 copy of fstab; it belongs to root, and you need system privilege to edit it
~~~~~~~~~~~~~~~~~~~

2012-10-15 Cont'd

OBSERVATION

digging back through my notes it appears to me that, in the absence of
instruction in the FSTAB file UBUNTU handles the added hard drive ( /dev/sdb )
in the same manner as it would a CD or USB Stick

in formatting the new drive using disk utility I had created a partition
and apparently I became the owner of the partition as a result of that

as a result i was able to create a shared directory in the new partition,
set the new directory to shared, and use chmod to assign 777 access rights
to that folder

after that -- "everyone"  had access to this area -- even from Windows

this is "OK" for an "everyone" drive -- and that will have its use in a home net environment.

but generally shared resources are owned by a group and users needing access to such
resources are simply added to the group that owns the resource

so, today's experiments will involve change ownership, building groups,
and assigning users to groups as well as fussing with the mount command.

I'd like to get thje mount command in the fstab so that the drive mounts automatically
on but up.   as it is now I have to mount it and supply the admin password to do it .
~~~~~

---

