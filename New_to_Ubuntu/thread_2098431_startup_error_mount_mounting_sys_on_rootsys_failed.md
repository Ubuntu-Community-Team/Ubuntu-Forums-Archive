---
title: "startup error: mount: mounting /sys on /root/sys failed: No such file or directory"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by polynue on 2012-12-26
Hello! I'm a new ubuntu user without much useful computer experience, so sorry if this includes irrelevant information. I have an 8 year old macbook that was running 12.04 beautifully for months, the macbook would not boot up past a white screen until i installed pangolin from a live cd to replace the mac os without partitioning. 

 Last night i opened it up to clean dust out of the fans, and it worked great for about 3 hours after i put it back together, but then it froze and now boots directly into the grub menu.  Probably stupidly, i tried each of the four or 5 options, restarting each time after they eventually went to an unresponsive black screen, and now it's running recovery mode, with a screen that looks like the matrix. 

It's thousands of lines in, which are running too fast to read well, but i can make out these repeating phrases

```
Input/output error 
init: mountall-main process (17____) terminated with status 2 
end_request
hostbyte=DID_BAD_TARGET
VER_OK

```


Also in one of the previous non recovery reboots, something similar to this showed up 


```
mount: mounting /dev/disk/by-uuid/a3c31122-6794-4fa6-a039-91d49dadfa8a on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a lit of built in commands.

(initramfs)
```


 I'm afraid the unknown original problems with the mac might be the source of the present problem, but it also seems like it's missing an important file somewhere. Should I let recovery mode continue running (its been going a couple hours now), or is there a faster way to reinstall ubuntu so the missing file or directory gets replaced, but without losing the personal files I had on there?  Or, if i run the live cd on it, is there a way i can save my old desktop files?

I was going to try to boot onto the liveCD and try to mount the filesystem from there like it's described at [ http://ubuntuforums.org/archive/index.php/t-1244466.html ]("http://ubuntuforums.org/archive/index.php/t-1244466.html"), hoping that would rewrite the lost files, but my drive is not partitioned and the instructions are for an older version. Should I try it anyway?

Thanks very much for reading!

---

### Post by bodhi.zazen on 2012-12-26
Basically your system can not boot as the root file system can not be mounted.

Could be anything from a bad hard drive to having changed the uuid of the root partition.

Yes, you need to boot a live CD and investigate.

---

### Post by polynue on 2012-12-26
Thanks for the reply! Could you point me towards instructions for investigating what's up after the liveCD boot?

---

### Post by bodhi.zazen on 2012-12-26
You open a terminal and mount the partition(s)

You can :

```
sudo -i

blkid #This will list your partitions by uuid

fdisk -l
```

Then mount them

```
mount /dev/sdxy /mnt
```

"sdxy" is your partition to mount, /dev/sda1 for example ...

and look at the contents with

```
gksu nautilus
```

---

### Post by polynue on 2012-12-26
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660" 
/dev/sda2: UUID="0f32e2e2-8683-4c64-9453-1cc845c27429" TYPE="ext4" 
/dev/sda3: UUID="4e284d1b-0091-48e3-a72e-76333a50df20" TYPE="swap" 
root@ubuntu:~# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002753

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1987         993+  ee  GPT
/dev/sda2   *        1988   480078159   240038086   83  Linux
/dev/sda3       480078160   488397054     4159447+  82  Linux swap / Solaris
root@ubuntu:~# mount /dev/sda1 /mnt
mount: you must specify the filesystem type
 
```

i was getting "mount: you must specify the filesystem type" so i tried "mkfs.ext3" and it seemed to mount them but none of my old files are showing up on nautilus search. 

```
root@ubuntu:~# mkfs.ext3 /dev/sda3
mke2fs 1.42 (29-Nov-2011)
/dev/sda3 is mounted; will not make a filesystem here!
root@ubuntu:~# mkfs.ext3 /dev/sda2
mke2fs 1.42 (29-Nov-2011)
/dev/sda2 is mounted; will not make a filesystem here!
root@ubuntu:~# mkfs.ext3 /dev/sda1
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
128 inodes, 976 blocks
48 blocks (4.92%) reserved for the super user
First data block=1
Maximum filesystem blocks=1048576
1 block group
8192 blocks per group, 8192 fragments per group
128 inodes per group

Allocating group tables: done                            
Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Writing inode tables: done                            

Filesystem too small for a journal
Writing superblocks and filesystem accounting information: done


```

i'm lost, thanks so far and for any further instruction :KS

---

