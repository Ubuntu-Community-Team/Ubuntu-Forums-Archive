---
title: "Detecting my windows drives"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by santhinen on 2008-06-01
Hi guys..i am using ubuntu 7.10...
i have 4 windows partitions...ubuntu when installed automatically detected only 3 of them... i manually added the 4th partition and mounted it..

So i am able to see only 3 of my partitions in "Computer//" folder..how can i add my 4th partition in this folder...i am now accessing my 4th partition from the mount point i have given /media/DRIVE... i want to add this partition in the Computer:/// folder so that i can easily access it ....
pls help..

I also want to know whether there is any wizard kind of or easy only mouse clicking way to connect to internet via PPPoE??
I have to type sudo pon dsl-provider whenever i need to connect..isn't that a problem for home users?? is there any wizard available like that in fedora??

---

### Post by prshah on 2008-06-01
> **santhinen said:**
> Hi guys..i am using ubuntu 7.10...
i have 4 windows partitions...ubuntu when installed automatically detected only 3 of them... i manually added the 4th partition and mounted it..

So i am able to see only 3 of my partitions in "Computer//" folder..how can i add my 4th partition in this folder...

Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. These commands will give us the structure of your hard drive and a clue to why it is not auto mounting the 4th partition.```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by santhinen on 2008-06-01
*sudo fdisk -l*

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb77bb77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2434        3580     9213246    b  W95 FAT32
/dev/sda6            4867        7299    19543041    b  W95 FAT32
/dev/sda7            7300        9729    19518943+   b  W95 FAT32
/dev/sda8   *        3581        4805     9839781   83  Linux
/dev/sda9            4806        4866      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

```

sudo cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=29798d81-fbaf-4ad9-b641-0df04c7892a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=c8ea1af3-347d-4fd9-82d1-d07d1afc94c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda6       /media/SANTHINEN  vfat    iocharset=utf8,umask=000   0       0

```

sda6 was added by me manually in /etc/fstab...

sda7 was getting detected and mounted automatically and appearing in "Computer:///"...
sda6 was not getting detected automatically..i added manually..

---

### Post by prshah on 2008-06-01
> **santhinen said:**
> 
sudo cat /etc/fstab

sda6 was added by me manually in /etc/fstab...



Your fstab seems incomplete to me. (btw, no "sudo" required for this command) There are no entries for the other partitions, I don't see how they can be loaded automatically.

Please post output of ```
mount
df -h | grep sda

```

---

### Post by rraj.be on 2008-06-01
you can use NTFS configuration tools from

```
Applictions --> System Tools --> NTFS configuration tools
```

---

### Post by santhinen on 2008-06-02
```
 mount
/dev/sda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda6 on /media/SANTHINEN type vfat (rw,iocharset=utf8,umask=000)
/dev/sda7 on /media/SANOV type vfat (rw,iocharset=utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=santhosh)
santhosh@SAN-WORLD:~$ df -h | grep sda
/dev/sda8             9.3G  3.8G  5.1G  43% /
/dev/sda6              19G   17G  2.2G  89% /media/SANTHINEN
/dev/sda7              19G   17G  2.1G  89% /media/SANOV

```

prshah.... ya i know those entries are not there in /etc/fstab... but it gets 3 of my drives got detected even when i used live cd..and after installation also..i dont know how though....after installation as my 4th partition was not there i manually added it...
I see other 3 partitions in the Computer:/// folder.... i just want to add my 4th partition also to that folder..This 4th partition was added by me..so i can only access it from the point/folder where i mounted it..i am unable to add it to Computert:/// folder...
do u know the procedure??

---

### Post by santhinen on 2008-06-02
a new phenomena...

I started my comp..i didn't access any of my drives or windows partitions..
```

 df -h | grep sda
/dev/sda8             9.3G  3.8G  5.1G  43% /
/dev/sda6              19G   17G  2.2G  89% /media/SANTHINEN
/dev/sda7              19G   17G  2.1G  89% /media/SANOV

```
i get this

later i access my windows partitions being shown in the Computer folder..each and every windows partitions being shown in the Computer folder..
now i type the same command.
```
/dev/sda8             9.3G  3.8G  5.1G  43% /
/dev/sda6              19G   17G  2.2G  89% /media/SANTHINEN
/dev/sda7              19G   17G  2.1G  89% /media/SANOV
/dev/sda5             8.8G  6.4G  2.5G  73% /media/SANTHOSH
/dev/sda1              19G   13G  5.8G  70% /media/disk

```


what i understand is the ones given in /etc/fstab are being loaded when the system boots...but my other partitions being shown in Computer folder are mounted or loaded only when i access them or click their icons in Computer folder...

does anybody have reason..solution..
and method to add a shortcut or icon of my 4th partition??

---

### Post by rraj.be on 2008-06-02
OH,  what you had experienced is what generally all ubuntu users experience every time they boot.

The reason is that ubuntu recognises only its root file system and its own file systems as its own and mounts during booting along with any removable storage medias.

NTFS is a file system that ubuntu can suport but not its native.

hence it considers it as a partition that can be accesed but wont be mounted automaticaly.

I think theres some way to mount them automaticaly.

But i dont know.

could any ne help me with it.

take a look here

[www.forums.whirlpool.net.au/forum-replies-archive.cfm/974350.html]("www.forums.whirlpool.net.au/forum-replies-archive.cfm/974350.html")

---

### Post by rraj.be on 2008-06-02
Here is a way to mount NTFS automaticaly when you boot.

open 

```
/etc/modules
```

get into a new line in the file and add the following code to it and save


```
fuse
```

Example:

```
eg:  

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse 
```

Reboot the system.

now all your NTFS drives will be mounted automaticaly.

---

### Post by prshah on 2008-06-02
> **rraj.be said:**
> 
NTFS is a file system that ubuntu can suport but not its native.


He's not using NTFS. Study fdisk output from previous posts.

> **rraj.be said:**
> Here is a way to mount NTFS automaticaly when you boot.
```
fuse
```


Ubuntu from 6.10 onwards (at least) loads the "fuse" (Userspace file system module) automatically.

There is no need to make this change.

---

### Post by santhinen on 2008-06-03
so prshah...what could be the solution??

does anyone have a way to add a drive to computer:/// folder??

---

### Post by prshah on 2008-06-03
> **santhinen said:**
> so prshah...what could be the solution??

does anyone have a way to add a drive to computer:/// folder??

I'm hesitant to give you a solution because I can't get a clear picture. However, in my opinion, from what I see, adding the below two lines to your fstab should clear your problem.

NOTE: You do this at your own risk.

```

/dev/sda1 /media/disk     vfat    defaults,umask=007 0       1
/dev/sda5 /media/SANTHOSH     vfat    defaults,umask=007 0       1

```

From what I understand, sda6,7,8 automount. I can understand 8 (linux) but not why sda6,7 automounts, unless you have certain files active on those partitions at startup, such as torrents, pictures, music, etc.

So all you need to do is have entries for computer:/// for sda1,5. The above entries added into the /etc/fstab should do the trick.

I also assume that the correct directories as named above are setup in /media/ and have user root and group plugdev.

Finally, _once again_, I specify the risk is all yours. You can feel free to ignore my advice related to fstab entries, or get it confirmed elsewhere.

---

