---
title: "[SOLVED] Setting Up A Separate Data Partition"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Ralph L on 2008-08-12
I need some help in setting up a directory structure.  I have partitioned my hard disk in to 6 partitions:
A.  Windows XP ntfs partition
B.  Gnome Partition (Current Ubuntu partition and will be used for playing around in the future)
C.  Dual Gnome/KDE partition 1 (in process of installation)
D.  Dual Gnome/KDE partition 2 (will be used next Ubuntu upgrade)
E.  Shared Data partition (I plan to keep all user files here and access them from the other paritions).
F.  Swap partition.

1.  When running in one of the Gnome partitions, I can mount the shared data partition by selecting it under Nautilus>computer and right clicking to Properties>Mount.  However, when I restart the computer, the shared_data is no longer mounted.  How do I maintain the mounting through restarts?  Does it have anything to do with fstab?  What is the purpose of fstab?  If I need to alter it, is there any GUI utility to do that?

2.  Even when I have shared_data mounted, I cannot access it (copy a file to it).  When I right click>properties>permissions, all the permissions are dimmed so I can't set them.  Is there someway I can make this partition accessible?

3.  I would like to have files on shared_data be owned (and permitted) by each user account just like data on the Ubuntu partitions.  I would also like to have the same user accounts on different Ubuntu paritions be able to access the files for that user.  Is there any way to do this?  I am thinking of Group permissions but as I say in 2 above, I can't move even a single file to shared_data.

4.  Under GParted I gave all my partitions labels.  However, 
GParted would not maintain the windows partition label and hence my windows partition shows up in Nautilus as "31.5 GB Media".  Is there any way to give that a name of "Windows"?  Windows file format is ntfs.

5.  When I set up my current Ubuntu (partition B above), I defined a swap partition for it.  I would like to move away from using a swap partition to having each partition just swap to one of its own files.  This way (as I understand it) the swap partition won't be shared among the various Ubuntu partitions and hibernate will work.  How can I redirect the various Ubuntu partitions to swap to local files so I can delete the swap partition?  Right now they are all coming up with swap pointed at the swap partition (at least that is how I read fstab).

I am running Ubuntu Hardy on a Dell Latitude D610 laptop
Thanks

Ralph

---

### Post by unutbu on 2008-08-12
Please post
```

sudo fdisk -l
cat /etc/fstab
```

The info will allow us to include code in our answers.

---

### Post by nick_h on 2008-08-12
> How do I maintain the mounting through restarts? Does it have anything to do with fstab? What is the purpose of fstab? If I need to alter it, is there any GUI utility to do that?
Yes, that is exactly what /etc/fstab is for.  Edit it with:
```
gksudo gedit /etc/fstab
```
For a good guide read - [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131).

> Even when I have shared_data mounted, I cannot access it (copy a file to it). When I right click>properties>permissions, all the permissions are dimmed so I can't set them. Is there someway I can make this partition accessible?
What filesystem are you using?  If it is FAT then you need to set the mount options in fstab.  If it is ext3 then you need to set the permissions.  For a GUI solution run nautilus with root permissions:
```
gksudo nautilus
```

> Is there any way to give that a name of "Windows"? Windows file format is ntfs.
Either change the mount point in fstab or change the volume label.
Have a look at [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

> Right now they are all coming up with swap pointed at the swap partition (at least that is how I read fstab).
Yes, they probably are.  Do you really need to hibernate more than one Ubuntu installation at a time?

---

### Post by Ralph L on 2008-08-12
Unutbu

Here is the output from doing the commands you requested.  If you copy it to a text editor you don't get the wraparound.

Thanks

Ralph

ralph@ralph-laptop:~$ sudo fdisk -l
[sudo] password for ralph: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f301f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3834    30796573+   7  HPFS/NTFS
/dev/sda2            8166       12161    32097870    5  Extended
/dev/sda3            3835        6616    22346415   83  Linux
/dev/sda4            6617        8165    12442342+  83  Linux
/dev/sda5            8166        8299     1076292   82  Linux swap / Solaris
/dev/sda6            8300        9841    12386083+  83  Linux
/dev/sda7            9842       12161    18635368+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15744     4030448    c  W95 FAT32 (LBA)
ralph@ralph-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=3ee962ca-c40c-4357-8840-eeb7f7d88538 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6bd2a895-afd0-4651-b8fb-1060b2bacbc7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
ralph@ralph-laptop:~$ 
ralph@ralph-laptop:~$

---

### Post by unutbu on 2008-08-12
Please post the output of 

```
blkid
```

and confirm or deny:
```

/dev/sda1 Win XP			  
/dev/sda2 Extended partition
/dev/sda3 Gnome Ubuntu current	  
/dev/sda4 KDE In process of install?  
/dev/sda5 swap                            
/dev/sda6 KDE for next Ubuntu upgrade 
/dev/sda7 Shared data                 

```

---

### Post by Ralph L on 2008-08-12
> **unutbu said:**
> Please post the output of 

```
blkid
```

and confirm or deny:
```

/dev/sda1 Win XP			  
/dev/sda2 Extended partition
/dev/sda3 Gnome Ubuntu current	  
/dev/sda4 KDE In process of install?  
/dev/sda5 swap                            
/dev/sda6 KDE for next Ubuntu upgrade 
/dev/sda7 Shared data                 

```

The above is essentially correct.  However, I intend to use sda4 and sda6 for dual desktop Gnome/KDE systems.

Here is the output of blkid:

ralph@ralph-laptop:~$ sudo blkid
[sudo] password for ralph: 
/dev/sda1: UUID="3A34D40334D3C055" TYPE="ntfs" 
/dev/sda3: LABEL="Spare_Partition" UUID="fe09792c-6176-4d2a-af37-c5162c03c25d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="Gnome_KDE_1" UUID="3ee962ca-c40c-4357-8840-eeb7f7d88538" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6bd2a895-afd0-4651-b8fb-1060b2bacbc7" 
/dev/sda6: LABEL="Gnome_KDE_2" UUID="2d71648f-a0af-436f-8ad8-681d6e84d31f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Shared_Data" UUID="32cf258a-9518-4024-92dd-d8d689ea4608" SEC_TYPE="ext2" TYPE="ext3" 
ralph@ralph-laptop:~$

---

### Post by unutbu on 2008-08-13
[list]
[*] To mount your shared data partition at boot time. 2 options:
[list]
[*] Use the PySDM gui. drs305 has written a nice tutorial here: [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
[*] Do it manually: In what follows I'm assuming you want to mount the shared data partition at /data. If not, simply replace "/data" with the correct mount point in each place it appears below.
[list]
[*] 
```

sudo mkdir /data          
gksu gedit /etc/fstab

```
Add the following lines to the end of /etc/fstab: 
```

# /dev/sda7
UUID=32cf258a-9518-4024-92dd-d8d689ea4608 /data               ext3    relatime,defaults 0       2

```
Now when you reboot the computer, /dev/sda7 (Shared_Data) should be mounted at /data automatically.
[/list]
[/list]
[*] To access the files on Shared_Data as a normal user:
Run this command:
```

sudo mount /dev/sda7 /data       # Your data partition should now be mounted at /data
sudo chown -R $USER:$USER /data

```
This command will make you the owner of all files in /data.
Try reading/writing to /data. If you still have permission problems, try the command
```

sudo chmod -R u+rw /data

```
This will give you read and write permission on all files in /data. 
[*] Hopefully the above will be enough to allow all your Linux operating systems to share files in /data. If it doesn't work, it probably means the is a UID (user ID) mismatch. In case it is, a quick word about UIDs:

Suppose you have a user named Harry on sda3 (GNOME/Ubuntu), and a user named Joe on sda4 (KDE/Kubuntu). Harry and Joe can share the same file, and both be considered the owner of the file by their respective operating systems as long as they have the same UID. When a user is created, the OS assigns the user a UID number. By default Ubuntu and Kubuntu start handing out UIDs to normal users starting with the number 1000. So if Harry was the first user account created on sda3 and Joe was the first user account created on sda4, then they will both have UID 1000, and sharing files for them is automatic. 

To check what your uid is, just type "id".

So the above commands will allow you to share files in /data as long as the users all share the same UID. If they don't, post back and maybe we can suggest a way to solve the problem (there are a couple of ways, none of them super-simple).
[*]
> 
4. Under GParted I gave all my partitions labels. However,
GParted would not maintain the windows partition label and hence my windows partition shows up in Nautilus as "31.5 GB Media". Is there any way to give that a name of "Windows"? Windows file format is ntfs.


Unfortunately, there is a "bug/feature" in Hardy which causes windows partitions to have names like "31.5 GB Media". See:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366)

You can force the Windows partition to be mounted at a mount point you can control like /Windows, but you may not be able to prevent the icon on your desktop from labeling the Windows partition "31.5 GB Media". I'm not sure about this though, so it would not hurt to try nick_h's advice by following the steps at [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).

[*] To mount your Windows partition at /Windows, for each OS edit your /etc/fstab:
[list]
[*] Use PyDSM, or
[*] Do it manually:
```

sudo mkdir /Windows
gksu gedit /etc/fstab

```
Add the following lines to the end: 
```

# /dev/sda1
UUID=3A34D40334D3C055 /Windows ntfs relatime,uid=1000,gid=1000,dmask=027,fmask=137 0 2

```
[/list]
[/list]

Gee, that's a lot of stuff. If you run into any problems, post back here.

---

### Post by Ralph L on 2008-08-23
Following the instructions given earlier in this thread I managed to get a shared partition working, but it was somewhat unhandy.  When I installed Ubuntu into a new partition on the disk, I discovered (under Prepare Disk Space section of the install) that I could specify the shared partition to be /home for each of my Ubuntu OS partitions.  This meant that each user's data would be automatically stored on the shared partition.  I also used the advice given earlier in this thread about how to set up the User accounts with the same User id in each OS.  The only glitch was that I had to do the account creation using a terminal command line, because Users & Groups would do it.  I think I used adduser or useradd. Once the account was established, I could modify it using Users & Groups.  

Ralph

---

### Post by nick_h on 2008-08-24
> I managed to get a shared partition working, but it was somewhat unhandy
You could always create a symbolic link from the mount point of your shared partition to a directory under your home directory.

> I could specify the shared partition to be /home for each of my Ubuntu OS partitions.
Yes, this is a good approach if you want to share application settings as well.  It will also make re-installation of Ubuntu easy.

> The only glitch was that I had to do the account creation using a terminal command line
The Users & Groups should allow you to add a new user and specify the userid.  It is also useful to know the command line method though.

---

### Post by Ralph L on 2008-10-29
Using the same shared data partition /home/ralph directory for all three of my operating system partitions turned out to be a bad idea.  That is because in addition to sharing my personal files, it shared all my hidden .xxxxx configuration files.  So when I installed a new version of, say Open Office, on one partition, it messed up the configuration of Open Office on the other partitions.  And because having the capability to experiment with different operating systems and applications on one partition without affecting the other partitions was the whole reason I wanted multiple partitions, I changed the location of the /home/ralph directory back to their own OS partition (the way things normally are).  To access the shared data partition I put a symbolic link in each OS partition's /home/ralph called "documents" and pointed it to /media/Shared_Data/documents_ralph.  Then I changed the permissions on documents_ralph to allow only ralph to access it and its files.

---

### Post by nick_h on 2008-10-29
Yes, good idea.  That is the approach I use.

You could make 4 shortcuts - one for each of the Documents, Music, Pictures and Video folders under the Places menu.

---

### Post by pablotanguero on 2013-02-26
It work for me with the folowing line!

# /dev/sda4	  	 
UUID=EA41-4B72	/media/HDpermastore			vfat     relatime,defaults 0       2

---

### Post by oldfred on 2013-02-26
Thread Closed. Some of suggestions are not valid or best anymore.

---

