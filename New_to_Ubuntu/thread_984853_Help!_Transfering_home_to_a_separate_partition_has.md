---
title: "Help! Transfering /home to a separate partition has turned into a catastrophe"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by slimjim4959 on 2008-11-17
So I used the psychocats guide to creating a new /home partition but I have no spent a few hours trying to undo it because of the mess I have created.

So when I logged on I got the error about not being about to log in. I went into recovery mode but whenever I tried to take ownership of the files I got a "no such file or directory error."

Now I am just trying to go back to the original setup from the live cd and when ever I run the terminal and these commands:

sudo mkdir /recovery
sudo mount -t ext3 /dev/sda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

the terminal hands at the 3rd line and won't work. I feel in way over my head and I just want to get my old files back any help would be greatly appreciated.

My partition editor currently reads:

/dev/sda1 ntfs (my windows boot)

/dev/sda3 ext3 (my new partition where I wanted to move home- it is currently mounted on /recovery)

/dev/sda2 extended (my original ubuntu boot)
   /dev/sda5 linux swap
   /dev/sda6 ext3 (mounted on /recovery)


I have really made a mess of things.... Any help would be greatly appreciated!

---

### Post by philinux on 2008-11-17
As the installation stands will it boot and what error do you get at login. It's probably fixable. I assume you backed up any important files first?

---

### Post by bumanie on 2008-11-17
I suggest you go [here]("http://www.cgsecurity.org/wiki/TestDisk") and download testdisk. It is a data recovery program. Read the documentation on testdisk's site and also read Herman's [tutorial]("http://www.users.bigpond.net.au/hermanzone/p21.html"). Testdisk works very well - as said **read first** before doing anything! If you know what your partitions were before, testdisk should find them and should be able to restore them (as long as you have not overwritten stuff already. Good luck.

---

### Post by slimjim4959 on 2008-11-18
The specific error that I get is:

Your home directory is listed as: '/home/leo' but it does not appear to exist. Do you want to login with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session.

When I boot into my Windows XP I can see two Linux partitions (I am using ext2ifs)- one that has my files and one that says it is  not formatted. I feel like I may have screwed up the file transferring process when I was switching my /home files and now ubuntu is looking in the wrong partition for my files.


As for the testdisk program. Is there any forum post that used this program with a more helpful step by step explanation? I read through the documentation and I don't feel confident enough to use the program successfully (it seems powerful).

I did download the program though and I think pasting the log of my partitions might help:


ext2fs lib: 1.41.0, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(/dev/sda)=320072933376
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\PhysicalDrive0)=320072933376
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\C:)=94582462464
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\D:)=120582604800
filewin32_getfilesize(\\.\E:) GetFileSize err Incorrect function.

filewin32_setfilepointer(\\.\E:) SetFilePointer err Incorrect function.

Warning: can't get size for \\.\E:
disk_get_size_win32 IOCTL_DISK_GET_LENGTH_INFO(\\.\F:)=100405960704
file_read(4,1,buffer,625153409(38913/254/63)) lseek err Invalid argument
Hard disk list
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector size=512 - WDC WD3200BEVT-00ZCT0

Partition table type (auto): Intel
Disk /dev/sda - 320 GB / 298 GiB - WDC WD3200BEVT-00ZCT0
Partition table type: Intel

Analyse Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
Info: size boot_sector 184731361, partition 184731372
get_geometry_from_list_part_aux head=255 nbr=12
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=12
Current partition structure:
 1 * HPFS - NTFS              0   1  1 11498 254 63  184731372
 2 E extended             26159   0  1 38912 254 63  204893010
 3 P Linux                11499   0  1 26158 254 63  235512900
 5 L Linux Swap           26159   1  1 26705 254 63    8787492
   X extended             26706   0  1 38912 254 63  196105455
 6 L Linux                26706   1  1 38912 254 63  196105392

SDA3 or te P Linux is the resized partition that I created to transfer /home. SDA6 and 5 are the original ubuntu partitions that I created when I setup the system.
 
Thank you all very much for your help!

---

### Post by slimjim4959 on 2008-11-18
Since I didn't get much of a response I guess I should ask this question as well.

I have access to my ubuntu partitions from windows and I can technically see my /home and all of my system folders. Is there anyway that I can back up my files from windows and just reinstall ubuntu? I can see the backup I created and the old /home folder so I figure this is reversible. 

Thanks for any help you can give!

---

### Post by philinux on 2008-11-18
> Your home directory is listed as: '/home/leo' but it does not appear to exist. Do you want to login with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session.Well i would login then using a failsafe session. you would be able to have a look at all your files and hopefully back them up and look at /etc/fstab. This may just need editing.
10 hours ago i was in bed.

---

### Post by mapes12 on 2008-11-18
This is what I would do if I were in your situation.

1. Make a full backup of my XP stuff using the standard backup application that comes with XP. I would use a "Normal" backup and store it some where safe. As belt and braces I would also image my XP partition using [DriveImage XML]("http://www.runtime.org/driveimage-xml.htm"). You will also need to make a WinPE boot CD in case you need to restore the backup. See the link for details. Keep the image somewhere safe again. i.e. on another machine or external HDD / removable media.

2. I would then get myself a [GParted Live CD]("http://gparted.sourceforge.net/")  (Yes, I know UBU Live CD's will do the job but some machines don't like Ubu Live CD's).

3. Boot the machine with the above CD.

4. Locate the Ubuntu partitions and either format them (except Swap) or delete them completely.

5. Re establish my partition planning. This is a good starting point to see what I mean : [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

6. Reboot the machine to make sure XP still loads OK. Hopefully it will. If not then reinstall image / fresh install plus add backup from 1 above. Whatever, to get it running.

7. Once XP is OK reinstall Ubuntu but when you get to the "Partitioning" section select "Manual" then set the variables for each partion to tell the installer what you want to do e.g. where to install /(root) /home and Swap in accordance with how you have built your partitions in 5.

8. The fresh installation should also reinstall Grub to pick up your XP installation.

9. If all goes well...................Have a beer!

Others may have an alternative solution. The above is only my humble opinion and how I would approach the problem.

EDIT - this is no good to you now but in the future it's always a good idea to have a backup of your Ubuntu system (and other OS if you need to) where you know that if something breaks you can simply restore the backup and have your machine exactly how it was before something broke. I us a simple tar ball for my "/" sytem files from this Howto: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)   If you have /home on a separate partition (which is what you were trying to do in the first place and to be recommended) then also --exclude=/home in the command. The same command can also be used to back up /home. I would suggest doing this backup method (or another you are comfortable that will work) even before using Update Manager or installing Firefox addons. Basically, if you are doing anything that will change your machines setup then backup before hand.

---

### Post by egalvan on 2008-11-18
> **slimjim4959 said:**
> 
I have access to my ubuntu partitions from windows and I can **technically see my /home** and all of my system folders. Is there anyway that I can back up my files from windows and just reinstall ubuntu? I can see the backup I created and the old /home folder so I figure this is reversible. 


Did you install any drivers in XP to see the Ubuntu partitions?

What do you mean by **"technically see /home"** ?

If you have a driver that lets you run ext2 under XP, then yes you can copy under XP. And ext2 is just ext3 without journaling.

Have you tried using a LiveCD to copy your Ubuntu partitions?

(You may find Parted Magic LiveCD to be easier to use.)



ErnestG

---

### Post by egalvan on 2008-11-18
> **mapes12 said:**
> This is what I would do if I were in your situation.
...
**4. Locate the Ubuntu partitions and either format them (except Swap) or delete them completely.**
...
9. If all goes well...................Have a beer!

Others may have an alternative solution. The above is only my humble opinion and how I would approach the problem.

The OP wants to "get his old files back", not simply re-install Ubuntu.

I'm still not good enough under Linux to do this, but it looks do-able under XP.

ErnestG

---

### Post by mapes12 on 2008-11-18
> Is there anyway that I can back up my files from windows and just reinstall ubuntu?

Ernest, I answered the question.

---

### Post by slimjim4959 on 2008-11-18
Thank you all for your help!

I can see my Ubuntu partitions because I am using ext2ifs in XP. I got it after this whole debacle because I wanted to make sure I could get all of my vital documents off of my partition.

At this point I feel like I just need to redirect Ubuntu to the right partition so that it can see my /home. What would be the right way of doing that? I think where I screwed up was in the transferring of the files over from my old partition to my new partition because the old partition is intact (with my root directory and even my home back up) and my new partition seems unformatted, at least from windows. I feel like ubuntu has already been directed to find /home in the new partition and this is just a matter of switching.

If this is all crazy speak please feel free to correct me. Thanks!

---

### Post by philinux on 2008-11-18
From your ubuntu bit we'd need. Why not login to your ubuntu to bit with a failsafe session or use the live cd.

[FONT=Trebuchet MS][SIZE=4]sudo fdisk -l
and
cat /etc/fstab[/SIZE][/FONT]

---

### Post by slimjim4959 on 2008-11-18
I just followed through and entered into a fail safe session and another error I got was:


"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

And I can't get to a terminal to enter those commands. Should I run failsafe in a terminal? Will that work for me? Or should I run this in root?


I did go into recovery mode and entered in root:

chmod 644 /home/leo/.dmrc 

But I get an error that said cannot access ... No such file or directory

---

### Post by philinux on 2008-11-18
In this order.

chmod 700 /home/username
chmod 644 /home/username/.dmrc

However these should not be done as root or sudo.

Before this how about those other two commands first.

---

### Post by slimjim4959 on 2008-11-18
Alright when I run the first command my output is:

Disk /dev/sda: 320gb 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
units=cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x5ce683eb

Device    Boot   Start  End     Blocks     Id   System
/dev/sda1 *      1      11499   92365686   7    HPFS/NTFS
/dev/sda2        26160  38913   102446505  5    Extended        
/dev/sda3        11500  26159   117756450  83   Linux
/dev/sda5        26160  26706   4393746    82   Linux swap/Solaris
/dev/sda6        26707  38913   98052696   83   Linux

Partition table entries are not in disk order

The second Command displays:

#static file system information.
#
# <file system> <mount point> <type> <options>   <dump>  <pass>
proc            /proc         proc   defaults    0       0
#/dev/sda6
UUID=e1b6a0e5-17a0-4c00-ab2b-17e4bbc5fd85 /   ext3 realtime,error
s=remount-ro 0        1
#/dev/sda5
UUID=c287afef-47bb-43c2-a202-d79773a487e2 none   swap    sw
0     0
/dev/scd0       /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0   0


I hope that helps! Thanks again.

---

### Post by slimjim4959 on 2008-11-18
Also I have been looking into testdisk and I have kind of a simple question.

If I were to run it would I lose all of my data or would that be restored as well?

---

### Post by dazzlindonna on 2008-11-18
I just finished dealing with this issue. "maybe" my experience will help.  my user folder was at home/home_backup/user rather than home/user which is the chmod was saying the directory didn't exist.  what i did was login using livecd, opening terminal, typed sudo nautilus, which opened nautilus as root.  then i did the same thing again so i could have two nautilus windows open, both as root.  i then grabbed the user folder in one window and moved it into home (bypassing home_backup) in the other window.  essentially that just moved it where it was supposed to be, making home_backup empty.  so now i had /home/user as i was supposed to.  rebooting into recovery mode and chown'ing worked after that and all was well again.  Not sure if that's your issue or not, but thought I'd throw it out there just in case.

---

