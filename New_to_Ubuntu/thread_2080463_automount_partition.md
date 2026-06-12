---
title: "automount partition"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by john.errington on 2012-11-04
I'm using 12.04 trying to mount a partition at start-up.
Nautilus shows 4 entries, as follows:
120G hard disk:21 G file system (which is a windows data directory)
120G hard disk: data (the ubuntu partition?)
CD/DVD drive
File system.

When I launch sdm I get sda1, sda5, sda6, sda7
and when I click on sda1 sdm says:
"..hasnt been configured"
however it also tells me all 4 are set to automount.

Can you please tell me
1: how to find out the connection between the 4 sda's and the 4 things nautilus shows me?
and
2: how sdm should be configured?

---

### Post by ibjsb4 on 2012-11-04
Try here  :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+mount+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+mount+partitions&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by NikTh on 2012-11-04
Hi , 
you can give here the results of bellow commands and someone will help you to create the correct line in /etc/fstab/ 

```
cat /etc/fstab
sudo blkid 
sudo fdisk -l
``` 

and tell us which partition you want to auto-mounted at start-up.
_Put the result between these brackets [noparse]```
the results here
```[/noparse] to be easier to read._
Thanks

---

### Post by john.errington on 2012-11-04
```

john@john-HP-nx7400:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5e4df704-4a41-4135-a7d7-53378a461af8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ebd346ef-a004-4a4c-9c00-6b9f8b6a3025 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
john@john-HP-nx7400:~$ sudo blkid
[sudo] password for john: 
/dev/sda1: UUID="AE7846C678468D51" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="01CBC9EDABE84830" TYPE="ntfs" 
/dev/sda6: UUID="5e4df704-4a41-4135-a7d7-53378a461af8" TYPE="ext4" 
/dev/sda7: UUID="ebd346ef-a004-4a4c-9c00-6b9f8b6a3025" TYPE="swap" 
john@john-HP-nx7400:~$ 
john@john-HP-nx7400:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb526b526

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40975199    20487568+   7  HPFS/NTFS/exFAT
/dev/sda2        40975261   234440703    96732721+   f  W95 Ext'd (LBA)
/dev/sda5        40975263   166203838    62614288    7  HPFS/NTFS/exFAT
/dev/sda6       166205440   230264831    32029696   83  Linux
/dev/sda7       230266880   234440703     2086912   82  Linux swap / Solaris
john@john-HP-nx7400:~$ 

```

---

### Post by john.errington on 2012-11-04
Thanks! I cant make any sense of the information, but 
21g filesystem is a windows parttion
Data is a 64g partition with data that I want to automount

---

### Post by pkadeel on 2012-11-04
> **john.errington said:**
> Thanks! I cant make any sense of the information, but 
21g filesystem is a windows parttion
Data is a 64g partition with data that I want to automount
create a folder in /media and name it "sda5", put the entry for "data" partition in your fstab file
```

UUID=01CBC9EDABE84830       /media/sda5            ntfs            defaults                0               2

```

---

### Post by NikTh on 2012-11-04
Here is a very explainable tutorial about [How to Fstab - from ]("http://ubuntuforums.org/showthread.php?t=283131")[bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054")
so you know what are you doing. 

First create the mount point with this command 
```
sudo mkdir /media/data
```Then open the fstab with gedit editor with this command 
```
gksudo gedit /etc/fstab
```and add this line at the end
```
LABEL=Data /media/data ntfs defaults 0 0
```After above and when reboot , you should see an entry named "data" that contains your folders and files from the 64GB partition.

P.S @pkadeel the fsck option better should be 0 when the filesystem is NTFS. 

Thanks

---

### Post by Bashing-om on 2012-11-04
Hi ! john.

 In my perusal of your submitted info, I can not help but see that your current /etc/fstab file is a mess. As how a partition is mounted and accessed (for security) is a personal preference with many many options may I present some how-tos and guides:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

These links provide the needed instruction to square your /etc/fstab file away, to your specifications.

I believe reading is a good thing; After study please post back with any additional queries.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by john.errington on 2012-11-04
bashing-om: yes I installed ubuntu on a laptop that had previously been windows machine, and  needed to keep the data accessible both to ubuntu and to my windows network.

You've all given me a lot to digest, so I'll do some reading and follow this up later.  At least now I know WHAT to read!

Pity its not just as straightforward as clicking in sdm!

Thanks all.

---

### Post by jerome1232 on 2012-11-04
> **john.errington said:**
> option to create folderin media is greyed out
```
sudo mkdir /media/data
```

> **john.errington said:**
> how do i edit the fstab file?

```
gksu gedit /etc/fstab
```

---

### Post by NikTh on 2012-11-04
> **Bashing-om said:**
> 
In my perusal of your submitted info, I can not help but see that your current /etc/fstab file is a mess.

Why is a mess ? 
Bellow are the entries of john's fstab.

> **john.errington said:**
> ```

john@john-HP-nx7400:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5e4df704-4a41-4135-a7d7-53378a461af8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ebd346ef-a004-4a4c-9c00-6b9f8b6a3025 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

the only weird line is the /dev/sdb , probably refers to an external drive or floppy drive and the filesystem is "auto" because is such devices (like floppy or CD-rom) the filesystem identified automatically. (is not constant)
Thanks

---

### Post by Bashing-om on 2012-11-04
john. 
there is a GUI tool to do what you want ...but the Command Line method offers more control to obtain desired results..... and is not control what it is all about ??

[INDENT]knowledge is power ==> BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-11-04
@ NikTh ...Thanks for your advisement/direction on my part. I am guilty again of not differentiating the blkid output ...seeing the blkid as a part of the /etc/fstab ...and jumping all over ntfs mounting problems.
will try to focus better in the future ! [INDENT]thanks < == BDQ

[/INDENT]

---

### Post by john.errington on 2012-11-05
T%hanks to links I discovered this command

```
john@john-HP-nx7400:~$ sudo parted -l
[sudo] password for john: 
Model: ATA FUJITSU MHV2120B (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.0GB  21.0GB  primary   ntfs            boot
 2      21.0GB  120GB   99.1GB  extended                  lba
 5      21.0GB  85.1GB  64.1GB  logical   ntfs
 6      85.1GB  118GB   32.8GB  logical   ext4
 7      118GB   120GB   2137MB  logical   linux-swap(v1)
```

now I can make some sense of the entries in nautilus

#2 - 21G file system is my windows partition
#5 - 64G is my windows data that needs to be accessible to ubuntu
#6 - 33G is my ubuntu partition
#7 - 2G linux swap

---

### Post by pkadeel on 2012-11-05
Now all you need to do is simply follow what NikTh advised in his post.

Open a terminal. If you can not find it in your installed applications then use the keyboard shortcut Ctrl + Alt + t

Following command will create a new folder where you can automount the partition
```

sudo mkdir /media/data

```

Following command will open the fstab file for editing
```

gksu gedit /etc/fstab

```

Once you get your file opened append the following text to the end of the file.
```

LABEL=Data       /media/data     ntfs       defaults       0      0

```

Save and close the file and reboot.

---

### Post by john.errington on 2012-11-05
Thanks NikTh
did as you suggested and..
SUCCESS! the data drive is mounted when I restart.

..

for some reason Banshee will not play the music from there now - it did before!
-needed to re-import the music library.

Many thanks to all for your help.

---

### Post by NikTh on 2012-11-05
Glad you solved it. 

Please mark the thread as solved by clicking the "thread tools" above. 

[How to mark a thread as solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks

---

