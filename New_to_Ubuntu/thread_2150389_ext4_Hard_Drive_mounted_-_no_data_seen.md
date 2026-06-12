---
title: "ext4 Hard Drive mounted - no data seen"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by ltp88 on 2013-05-31
HI,

I have recently altered my media box that was running xbmcbuntu to run Ubuntu 13:04 then back to 12:04 (currently running).
During this process i have somehow screwed up at least one of my drives so that I can no longer see any of the data on it.
I think the drive has been screwed up by my hashed attempts to set up the mounting points again.
I have used some of the gui methods to edit the fstab (which i now see was a mistake) and i think this caused the problem.

currently i have the drive plugged in using an external usb slot drive (with no change in behavior).

Odd behavior
[LIST]
[*]the drive now mounts with the partition labeled with the UUID number
[*]the drive name has the monkier of 'filesystem' added to it.
[/LIST]

I have done a bit of searching and cant seem to find another case that seems to fit this issue

note: i have also seen in a swap partition attributed to this drive where one shouldn't be.

any help to recover the drive would be appreciated.

Thanks

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]ltp88; Hi ! Welcome to the forum.

It is late here my time, I do not intend to maintain a state of awareness much longer; but I will start this ball rolling.
Let us see:
```
sudo fdisk -lu
sudo blkid
cat /etc/fstab
cat etc/mtab
```

Make sure that fstab and mtab are differentiated and labeled (commands included in the outputs) to prevent confusion.
Place the outputs between code ("#") tags -top of post- for clarity.
[/COLOR][INDENT=2][COLOR=#000000]
the tale will be told
 [/COLOR][/INDENT]

---

### Post by ltp88 on 2013-05-31
here is the output from those commands

**sudo fdisk -lu**
```
Disk /dev/sda: 123.7 GB, 123705843712 bytes
255 heads, 63 sectors/track, 15039 cylinders, total 241612976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f473


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   225101823   112549888   83  Linux
/dev/sda2       225103870   241612799     8254465    5  Extended
/dev/sda5       225103872   241612799     8254464   82  Linux swap / Solaris


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5087a9dc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  2930276351  1465137152   83  Linux
```

**sudo blkid**


```
/dev/sda1: UUID="cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1" TYPE="ext4" 
/dev/sda5: UUID="83ec7b05-57ed-41d1-b145-f4b2d9351427" TYPE="swap" 
/dev/sdb1: UUID="78fd5cd6-cd3c-4733-b1bc-769f9529a8e9" TYPE="ext4" 
```

**cat /etc/fstab**
```
ltp@ltp-htpc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
#UUID=cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=83ec7b05-57ed-41d1-b145-f4b2d9351427 none            swap    sw              0       0
UUID=78fd5cd6-cd3c-4733-b1bc-769f9529a8e9       /mnt/test    ext4    defaults,errors=remount-ro  0  2  
```


**cat etc/mtab**
```
cat: etc/mtab: No such file or directory
```

---

### Post by Bashing-om on 2013-06-01
ltp88; Hey, I am still here ...

Ok not much ,lessen ya count my typo from my last directive ("etc/mtab" should have been "/etc/mtab" -leading slash)//

but at hand,...yeah let's edit your "data" disk mount: MAke a backup copy first and then Remove what ya inserted ",errors=remount-ro" from:
"UUID=78fd5cd6-cd3c-4733-b1bc-769f9529a8e9       /mnt/test    ext4    defaults,errors=remount-ro  0  2"
so that it is this:```
UUID=78fd5cd6-cd3c-4733-b1bc-769f9529a8e9       /mnt/test    ext4    defaults  0  2
```
MORE Importantly you have commented ("#") - the pound sign symbol - at the beginning of your root and as well  you have commented out your swap partition. remove the '#' sybols from:
 #UUID=cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1 /  and from
#UUID=83ec7b05-57ed-41d1-b145-f4b2d9351427

And while you are editing change the comments (lines beginning with #) of the locations to what is now actual:
#"/" root is presently insalled on sda1 -31may13
#swap is presently installed on sda5 -31may13
#My_Media box is on sdb1 as of 31may13
-----> or some such 
the '#' sybol means that the line is not to be executed and is but a "comment".
and lets make sure the mount point "/mnt/test" exist ; -> you gotta have a mount point !
```
ls -la /mnt/
```
and post the output of your new fstab (file system table):
```
cat /etc/fstab
```

Here are most excellent guides on how to fstab:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

we are in good shape for the shape we are in

---

### Post by ltp88 on 2013-06-01
ok, well i did what you said

(I have also added the other drives to the system and cleaned up all the mount points)

I can read all the drives, including the 1.5GB drive that has lost all the data.

here is the output of the fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=83ec7b05-57ed-41d1-b145-f4b2d9351427 none            swap    sw              0       0


# 1.5 Gb Drive
UUID=78fd5cd6-cd3c-4733-b1bc-769f9529a8e9       /mnt/1500    ext4    defaults  0  2 


# 500GB 
UUID=a844d6fe-550e-464b-ae26-37a8a9144265       /mnt/500-1    ext4    defaults  0  2  


# 500GB
UUID=17080bdc-8593-40ff-91e6-3135e4556041       /mnt/500-2    ext4    defaults  0  2  


#120GB
UUID=4bfd4996-56ae-49ab-b214-4884f7a8b7a5       /mnt/120    ext4    defaults  0  2  

```

also the associated mtab

```
/dev/sdb1 / ext4 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdc1 /mnt/500-1 ext4 rw,errors=remount-ro 0 0
/dev/sde1 /mnt/500-2 ext4 rw,errors=remount-ro 0 0
/dev/sda1 /mnt/120 ext4 rw,errors=remount-ro 0 0
/dev/sdd1 /mnt/1500 ext4 rw,errors=remount-ro 0 0
gvfs-fuse-daemon /home/ltp/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ltp 0 0
/dev/sdf1 /media/1TB fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdg1 /media/SAMSUNG fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0

```


SO while I can mount all the drives ok, for some reason the one drive seems to have lost all the data on it.

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]ltp88; Hey;

Looking much better.......but still have a problem with the sda1 partition per what "mtab" reports. sda1 is your root partition and there is no reason to have to explicitly mount it ...I assume that you have a mount point for sda1 at /mnt/120 - which I expect is a major conflict with what the system sets.
Let's look at your mount points and what the system then sees for what is mounted:
show us:
```
ls -la /mnt/
mount
cat /etc/mtab
```[INDENT=2]
we be stepp'n[/INDENT]

[/COLOR]

---

### Post by ltp88 on 2013-06-01
the 120 is actually another drive (not the boot drive)

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]ltp88; Hummmm.

[/COLOR]> [COLOR=#000000]the 120 is actually another drive (not the boot drive)[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]lemme go back and relook,,,I saw that it was root's mount in fstab....
I be back in a tic or so.[INDENT=2]
look'n

[/INDENT]

[/COLOR]

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]ltp88; I am back ...and ...I am correct...there exist a problem with "sda1" see ->
blkid's id :[/COLOR]> /dev/sda1: UUID="cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1"  
now look at fstab:
> #UUID=cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1 /               ext4    errors=remount-ro 0       1
which verifies that root is mounted sda1 and should not be mounted as another drive,,,,

We need to know why mtab (system) is mounting sda1 to that /mnt/120/
AND mtab shows mounting root as sdb1:
> /dev/sdb1 / ext4 rw 0 0 the "/" means root !

OK... What Drive holds your primary operating system sda or sdb ???
and in bios please make sure ///doubly sure/// that the primary operating system's hard disk is the first boot priority.[I just got through that one -  on my system not having my drives in bios mapped the way I had my drives mapped on the system as a whole]

Unless I am basing my deductions on old data !!! Have you made changes such that the old data is now invalid ??
and UUID's do not change ...so what is up ??

What are your thoughts ?[INDENT]
[/INDENT]
[INDENT=3]
current data is always a good thing

[/INDENT]

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]ltp88; adding to me last:
For reference, this is what my system reports... I have drive sda as my primary operating system and all UUIDs agree to /:
[/COLOR]
```

sudo blkid
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4"[COLOR=#000000]
[/COLOR] mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
 cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
 cat /etc/fstab
# / was on /dev/sda1 during installation
UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 /               ext4    errors=remount-ro 0

```[INDENT=2]
my question on your system[/INDENT]
[INDENT=5]
how now brown cow

[/INDENT]

---

### Post by ltp88 on 2013-06-01
ok here is the latest UUIDs

```
/dev/sda1: UUID="4bfd4996-56ae-49ab-b214-4884f7a8b7a5" TYPE="ext4" 
/dev/sdb1: UUID="cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1" TYPE="ext4" 
/dev/sdb5: UUID="83ec7b05-57ed-41d1-b145-f4b2d9351427" TYPE="swap" 
/dev/sdc1: UUID="a844d6fe-550e-464b-ae26-37a8a9144265" TYPE="ext4" 
/dev/sdd1: UUID="78fd5cd6-cd3c-4733-b1bc-769f9529a8e9" TYPE="ext4" 
/dev/sde1: LABEL="500GB-1" UUID="17080bdc-8593-40ff-91e6-3135e4556041" TYPE="ext4" 
/dev/sdf1: LABEL="1TB" UUID="50E86435E8641B8A" TYPE="ntfs" 
/dev/sdg1: LABEL="SAMSUNG" UUID="7818741E1873DA18" TYPE="ntfs"
```


What i have installed is
sda 120GB sata drive (old drive ) 
sdb 120GB SSD (boot drive)
sdc 500GB sata
sdd 1.5TB sata
sde 500GB sata
sdf 1TB USB
sdg 2TB USB


here is the latest fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=cb92e8e2-8ae6-4d1a-b4e3-4eb49102cba1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=83ec7b05-57ed-41d1-b145-f4b2d9351427 none            swap    sw              0       0


# 1.5 Gb Drive
UUID=78fd5cd6-cd3c-4733-b1bc-769f9529a8e9       /mnt/1500    ext4    defaults  0  2 


# 500GB 
UUID=a844d6fe-550e-464b-ae26-37a8a9144265       /mnt/500-1    ext4    defaults  0  2  


# 500GB
UUID=17080bdc-8593-40ff-91e6-3135e4556041       /mnt/500-2    ext4    defaults  0  2  


#120GB
UUID=4bfd4996-56ae-49ab-b214-4884f7a8b7a5       /mnt/120    ext4    defaults  0  2  


# 1.0 Gb Drive
UUID=50E86435E8641B8A       /mnt/1000    ntfs    defaults  0  2 


# 2.0 Gb Drive
UUID=7818741E1873DA18       /mnt/2000    ntfs    defaults  0  2 

```

and mtab
```
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sde1 /mnt/500-2 ext4 rw 0 0
/dev/sdf1 /mnt/1000 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdg1 /mnt/2000 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda1 /mnt/120 ext4 rw 0 0
/dev/sdc1 /mnt/500-1 ext4 rw 0 0
/dev/sdd1 /mnt/1500 ext4 rw 0 0
gvfs-fuse-daemon /home/ltp/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ltp 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0

```

to my mind these look ok.. (maybe could be cleaner.. but working


What I cant figure out is why the 1.5TB drive lost all the data. it says 50GB used (even though there doesnt seem to be anything on it)
IT should have about 70% of it used.
I would have understood if it lost the partition, but it has an active partition, just no files

```
Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5087a9dc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  2930276351  1465137152   83  Linux

```

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]ltp88; Yep

I agree now things look'n good ..gonna be better .
The only problem remaining is can not read the data on that (sdd) disk ?
OK, let us "assume" the disk's (sdd) super block is bad ...there exist a number of spare super blocks to switch it out, 
This is a good guide to check it out and switch them out:
[/COLOR][http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04](http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04)
see:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)

Also:
 labelling your partitions makes things a lot easier as you can read the sudo blkid. 
Not only do they display in terminal, they display as labelled in Ubuntu, which makes it a lot easier than perhaps displaying a UUID. 
Here is the command to label your partitions: 
sudo tune2fs -L "Precise" /dev/sda5 
sudo tune2fs -L "Quantal" /dev/sda6 
sudo tune2fs -L "Raring" /dev/sda8 

Example: sudo tune2fs -L {label} {devicename}
 

example; My system ->
sysop@1304mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1304mini:~$ 
----------------------

That will keep ya occupied for a spell, but, get back and let me know what haps.[INDENT=2]
it is still a learning experience

[/INDENT]

---

### Post by ltp88 on 2013-06-02
Thanks, that seems like what the problem is.

I will do some research to understand it and find out what i need to do.

The drive that is 'bad' is just normal magnetic media not used to boot off.

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]ltp88;

The "data" disk sdd still has a superblock that can be bad and if so can be spared off. wont take long to check it out...[/COLOR][INDENT][COLOR=#000000]
good luck !

[/COLOR][/INDENT]

---

### Post by ltp88 on 2013-06-02
ok, so I ran the updated the superblock as per instructions and no luck.

I then ran a program called TESTDISK which can analyse partitions and so forth.

what i have found out is that it seems that all the files have been deleted. they seem to be still on the drive.

the partition is still ok.

I will try to recover them and see where I go.

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]ltp88; That is tough...

Testdisk, from what I am aware of, is excellent at recovering files ! Just can not tell you the file names... the onerous chore of identifying the files is on you.

The good feeling thing is that your system is intact and this can be done ! 
[/COLOR][INDENT=2][COLOR=#000000]
Computers, like people - if it ain't one thing, it's another[/COLOR][/INDENT]

---

### Post by ltp88 on 2013-06-04
OK, so no luck so far,

I bought another drive to put the files on (i needed more space anyway, and i can get rid of the crappy 120)

I can see the folders in testdisk, but cant seem to recover them.
```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
 1 * Linux                    0  32 33 182401  68  3 2930274304 [1.5TB]
Directory /


 drwxrwxrwx     0     0      4096 26-May-2013 19:05 .
 drwxrwxrwx     0     0      4096 26-May-2013 19:05 ..
 drwx------     0     0      4096 26-May-2013 20:16 lost+found
[COLOR=#ff0000]>?---------     0     0         0                   Anime[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Documentaries[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Movies[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Other Videos[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Standup[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   TV Shows[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Downloads[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   .Trash-1000[/COLOR]
[COLOR=#ff0000] -rw-r--r--  1000  1000         0 26-May-2013 19:02 repository.googlecode.xbmc-c[/COLOR]
[COLOR=#ff0000] -rw-r--r--  1000  1000         0 26-May-2013 19:02 repository.urlXL.zip[/COLOR]
[COLOR=#ff0000] ?---------     0     0         0                   Untitled Folder[/COLOR]
[COLOR=#ff0000]                                                   Next[/COLOR]
Use Right to change directory, h to hide deleted files
    q to quit, : to select the current file, a to select all files
    C to copy the selected files, c to copy the current file



```
The files/folders in red are the missing files

I tried extundelete as well, but it says there are no files to recover

 ```
ltp@ltp-htpc:/mnt/3000$ sudo extundelete /dev/sdf1 --restore-allWARNING: Extended attributes are not restored.
Loading filesystem metadata ... 11179 groups loaded.
Loading journal descriptors ... 21846 descriptors loaded.
Writing output to directory RECOVERED_FILES/
Searching for recoverable inodes in directory / ... 
0 recoverable inodes found.
Looking through the directory structure for deleted files ... 
0 recoverable inodes still lost.
No files were undeleted.

```

Not sure there is much else I can do, if you have any suggestions it would be appreciated.

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]ltp88; Hey,

I have no experience with testdisk, there are many on this forum who do. As there is but limited visibility to this situation on this thread, how about starting a new thread about "testdisk recovery" to gain a lot of attention ....
[/COLOR][INDENT=2][COLOR=#000000]
just what I wud do [/COLOR][/INDENT]

---

### Post by ltp88 on 2013-06-05
Thanks for all your help.

I have mainly solved this issue anyway.

I used Photorec (comes with Testdisk) and have managed to recover 28000+ files.
now need to be sorted and renamed.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]ltp88; Hey, You do good work....

Please mark this thread then as "solved"; aids others in seeking solutions, and helps keep the forum tidy.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT]
as we move onto bigger and better things
 [/INDENT]
[COLOR=#000000]
[/COLOR]

---

