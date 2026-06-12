---
title: "File system root low disk space"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by abexman on 2012-10-07
Hello,

OK as I said elsewhere am having this issue on two machines with low disk space on file system root. I cannot access anything useful in disk space analyzer  because it hangs showing me usage (other post). In gparted it does seem to show me that I have space in my root??

Below are some screenshots. On this machine my Windows partition is running out of space, but why would that affect root (not the case on the other machine)? Also on this machine I am having issues with the partition getting an underscore and creating two folders under /media. Not sure if its related or if it can be fixed or matters. 

[[IMG]http://s5.postimage.org/o88krbpoj/Screenshot_from_2012_10_05_19_57_13.png[/IMG]]("http://postimage.org/image/o88krbpoj/")

[[IMG]http://s5.postimage.org/txotbmvur/Screenshot_from_2012_10_05_19_58_21.png[/IMG]]("http://postimage.org/image/txotbmvur/")

[[IMG]http://s5.postimage.org/c8x2k0k3n/Screenshot_from_2012_10_07_15_29_09.png[/IMG]]("http://postimage.org/image/c8x2k0k3n/")

> $ sudo du -hs /*
8.5M    /bin
59M    /boot
4.0K    /cdrom
4.0K    /dev
15M    /etc
du: cannot access `/home/[omit]/WualaDrive': Permission denied
du: cannot access `/home/[omit]/.gvfs': Permission denied
3.5G    /home
0    /initrd.img
0    /initrd.img.old
283M    /lib
16K    /lost+found
215G    /media
4.0K    /mnt
122M    /opt
du: cannot access `/proc/1639/task/1639/ns/net': No such file or directory
du: cannot access `/proc/1639/task/1639/ns/uts': No such file or directory
du: cannot access `/proc/1639/task/1639/ns/ipc': No such file or directory
du: cannot access `/proc/1639/ns/net': No such file or directory
du: cannot access `/proc/1639/ns/uts': No such file or directory
du: cannot access `/proc/1639/ns/ipc': No such file or directory
du: cannot access `/proc/18624/task/18624/fd/4': No such file or directory
du: cannot access `/proc/18624/task/18624/fdinfo/4': No such file or directory
du: cannot access `/proc/18624/fd/4': No such file or directory
du: cannot access `/proc/18624/fdinfo/4': No such file or directory
0    /proc
568K    /root
1.3M    /run
8.8M    /sbin
4.0K    /selinux
4.0K    /srv
0    /sys
368K    /tmp
3.2G    /usr
912M    /var
0    /vmlinuz> $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.9G  4.8G     0 100% /
udev                  1.9G  4.0K  1.9G   1% /dev
tmpfs                 755M  988K  754M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  664K  1.9G   1% /run/shm
/dev/sda6             212G  2.0G  200G   1% /home
/home/cabal/.Private  212G  2.0G  200G   1% /home/[omit]
/dev/sda2             215G  215G     0 100% /media/68D0F622D0F5F662_
javafs                5.0G  283M  4.8G   6% /home/[omit]/WualaDrive

---

### Post by NikTh on 2012-10-07
Hi  , 

Can you post the results***** of bellow commands 

```
df -Th 
mount 
sudo parted -l
```*****put the results between the brackets **[noparse]```
Here
```[/noparse]**.

Thanks

---

### Post by abexman on 2012-10-07
```
$ df -Th
Filesystem           Type         Size  Used Avail Use% Mounted on
/dev/sda5            ext4         4.9G  4.8G     0 100% /
udev                 devtmpfs     1.9G  4.0K  1.9G   1% /dev
tmpfs                tmpfs        755M  988K  754M   1% /run
none                 tmpfs        5.0M     0  5.0M   0% /run/lock
none                 tmpfs        1.9G  328K  1.9G   1% /run/shm
/dev/sda6            ext4         212G  2.0G  199G   1% /home
/home/[omit]/.Private ecryptfs     212G  2.0G  199G   1% /home/[omit]
/dev/sda2            fuseblk      215G  215G     0 100% /media/68D0F622D0F5F662_
javafs               fuse.javafs  5.0G  283M  4.8G   6% /home/[omit]/WualaDrive
```

```
$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/[omit]/.Private on /home/[omit] type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=6e04b860f4dd2ec1,ecryptfs_fnek_sig=2e21ed71ca4f7d32)
gvfs-fuse-daemon on /home/[omit]/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=[omit])
/dev/sda2 on /media/68D0F622D0F5F662_ type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
javafs on /home/[omit]/WualaDrive type fuse.javafs (rw,nosuid,nodev,user=[omit])
```

```
Model: ATA WDC WD5000BEVT-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  210MB  209MB   primary   ntfs         boot
 2      210MB   231GB  231GB   primary   ntfs
 4      231GB   475GB  245GB   extended
 5      231GB   236GB  5243MB  logical   ext4
 7      236GB   245GB  8389MB  logical
 6      245GB   475GB  231GB   logical   ext4
 3      475GB   500GB  24.6GB  primary   ntfs


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8389MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8389MB  8389MB  linux-swap(v1)


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label   
```

---

### Post by mcduck on 2012-10-07
4.9GB sure isn't very much for a root partition, I'd usually recommend something around 10-20GB for root. So it's not a surprise you are running low on space.

Try uninstalling old kernel packages, cleaning apt's cache, and check sure there's nothing in root's trash directory. That should give you at least some space back.

---

### Post by ajgreeny on 2012-10-07
Do you have any idea what sda7 might be?

There are 7.81 GB of "unknown" usage as far as gparted is concerned, and as it is next door to your 4.9GB root partition it would be relatively easy to delete sda7 and enlarge sda5, your root partition.  However that is totally dependent on what the partition might contain.

What does ```
sudo fdsik -l
``` show please, as that may give us some clues.

---

### Post by abexman on 2012-10-07
Crap. Had followed this install guide in trying to spec partition sizes, where they used ~5gb.
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

For that command I get
sudo: fdsik: command not found ??

I think the sda7 is just leftovers. I probably did not do a very good job setting up the partition using gparted. I was a little overeager to get Ubuntu up and running. I guess I can try and redo the partition.

Looks like I can resize using the Live CD & gparted? Assuming the partition goes OK, is that it? I won't have to repair the install after resizing root?

[http://askubuntu.com/questions/60431/how-do-i-resize-root-partition](http://askubuntu.com/questions/60431/how-do-i-resize-root-partition)

---

### Post by Bashing-om on 2012-10-07
abexman; Hi !

"fdsik": slip of the fingers .....correct to be 
```
sudo fdisk -l
``` lower case "L"
Re partitioning: Yeah, live disk (so working with non mounted partitions);  delete sda7 and enlarge sda5.
Worst that should result is having to re-install grub. If so, no big deal.

The learning experience is worth all the effort !
[INDENT]regards <==BDQ

[/INDENT]

---

### Post by NikTh on 2012-10-07
> **ajgreeny said:**
> 
What does ```
sudo fd**si**k -l
``` show please, as that may give us some clues.

> **abexman said:**
> 
For that command I get
sudo: fdsik: command not found ?? 

Yes , there is a misspell there. It is  ```
sudo fd**is**k -l
``` 

> **abexman said:**
> Looks like I can resize using the Live CD & gparted? Assuming the partition goes OK, is that it? I won't have to repair the install after resizing root?

[http://askubuntu.com/questions/60431/how-do-i-resize-root-partition](http://askubuntu.com/questions/60431/how-do-i-resize-root-partition)

Yes you can resize (expand) the / root partition , but carefully. DO NOT ever resize from the beginning to the end. Just expand the end of partition. 
Of course you must have space (or steel space from other partitions) and important thing is that This space must be NEXT to / root partition. 

Maybe it will need to move some space. 

IF you are not sure , the best thing is to Attach an image of Gparted here and we will see.

Thanks

---

### Post by abexman on 2012-10-07
gparted
[http://postimage.org/image/c8x2k0k3n/](http://postimage.org/image/c8x2k0k3n/)

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48649473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   450969599   225280000    7  HPFS/NTFS/exFAT
/dev/sda3       928608256   976560127    23975936    7  HPFS/NTFS/exFAT
/dev/sda4       450976680   928605194   238814257+   5  Extended
/dev/sda5       450979840   461219839     5120000   83  Linux
/dev/sda6       477607936   928604159   225498112   83  Linux
/dev/sda7       461221888   477605887     8192000   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 8388 MB, 8388608000 bytes
255 heads, 63 sectors/track, 1019 cylinders, total 16384000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4318d22d

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by abexman on 2012-10-07
I recall now, sd7 was where I had tried to put my swap file, again according to that dedoimedo article!? But it looks like that is not working since even gparted is not recognizing it as a swap? How can I tell where my swap file is going and can I change it? Should I change it?

---

### Post by Bashing-om on 2012-10-08
Let's back up and regroup:
I see from parted output that sda7 is not only swap, but, encrypted swap. (why GParted does not recognize it) I do not know of any good reason to encrypt swap ????

Guys, should we not straighten up sda7 (swap), and as we have no adjoining unallocated space, make a backup of data. Then we can proceed to copy/move partitions to enlarge the root partition?

Can we not then shrink sda6 (/home) to the right from the left side, and extend sda5(/) from it's right side  to the right - into the newly vacated space ?

I do not see that any windows partitions will be affected.

[INDENT]Just my thinkin' <==BDQ
[/INDENT]

---

### Post by NikTh on 2012-10-08
> **abexman said:**
> gparted
[http://postimage.org/image/c8x2k0k3n/](http://postimage.org/image/c8x2k0k3n/)

You are lucky , this "Unknown space" is exactly next to / (root) partition. So you can delete the "Unknown space" and expand the / root partition with 2 moves. 
Do it from a LiveCD/Usb cuz root partition must be Unmounted. 

As for swap you can cut a space from /home (/dev/sda6) , you have 209GB unused space. 

I assume a space 4GB for swap is OK. 

The only thing you must be aware is , AFTER you create the new swap space, you must configure your fstab file. 

When you finish the changes successfully and login to Ubuntu , open a terminal and give the results of these commands 
```
sudo blkid
cat /etc/fstab
```so we can enable swap memory in startup , by changing the numbers (UUID) in fstab.

Thanks

---

### Post by abexman on 2012-10-08
> **NikTh said:**
> You are lucky , this "Unknown space" is exactly next to / (root) partition. So you can delete the "Unknown space" and expand the / root partition with 2 moves. 
Do it from a LiveCD/Usb cuz root partition must be Unmounted. 

As for swap you can cut a space from /home (/dev/sda6) , you have 209GB unused space. 

I assume a space 4GB for swap is OK. 

The only thing you must be aware is , AFTER you create the new swap space, you must configure your fstab file. 

When you finish the changes successfully and login to Ubuntu , open a terminal and give the results of these commands 
```
sudo blkid
cat /etc/fstab
```so we can enable swap memory in startup , by changing the numbers (UUID) in fstab.

Thanks

OK, I ran gparted on a USB stick. It seemed to successfully resize the root partition and decrease the size of the adjacent partition. I then resized the large partition down to make room for a swap file. What I think failed is I tried to format the new partition for linux-swap, which I don't think "took". See below:

```
[omit]@HA-Laptop:~$ sudo blkid
[sudo] password for [omit]: 
/dev/sda1: LABEL="SYSTEM" UUID="7468F1FD68F1BDC4" TYPE="ntfs" 
/dev/sda2: UUID="68D0F622D0F5F662" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="28E8D02EE8CFF7D8" TYPE="ntfs" 
/dev/sda5: LABEL="root" UUID="dcd54473-3a8a-4582-a046-a654a3f95e42" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c" TYPE="ext4" 
/dev/sr1: LABEL="CDROM" TYPE="iso9660" 
/dev/sdd1: UUID="9006-53FD" TYPE="vfat" 
[omit]@HA-Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=dcd54473-3a8a-4582-a046-a654a3f95e42 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=bdb39428-0f55-4152-acf4-4b12f54a18a7 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[omit]@HA-Laptop:~$ 
```

[[img]http://s5.postimage.org/5ssp7o0xv/Screenshot_from_2012_10_08_16_35_12.jpg[/img]](http://postimage.org/image/5ssp7o0xv/)

---

### Post by abexman on 2012-10-09
Anything more I should do to setup my swap? Thanks guys!

---

### Post by NikTh on 2012-10-09
> **abexman said:**
> Anything more I should do to setup my swap? Thanks guys!

Can't you right click on "Unallocated 3.92GB" space and make it swap partition ? 

What is the error ? 

Thanks

---

### Post by Bashing-om on 2012-10-09
can we not edit /etc/fstab for swap on sda7. Presently showing as cryptswap1, make it a normal swap so blkid and GParted recognize it ?
By all means verify the uuid is correct.

[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by abexman on 2012-10-10
OK, so I booted into Ubuntu and ran Gparted and this time I was able to quickly format sda7 as linux-swap. I guess I'm done?? Thanks ya'll!

---

### Post by Bashing-om on 2012-10-10
I do not mean to take over the help you are getting... I do not know that using GParted to redo sda7 will fix/repair /etc/fstab.

What I had in mind on my previous was, with NinkTh's consent, was to edit the file to the proper uuid (if not correct) and commenting out or deleting the cryptswap1 entry.
As I understand it, installer miss calculated some thing and built the swap as encrypted in error as nothing else on your install is encrypted.

Things may be good now. Take a look at the fstab file as is now and see if that cryptswap1 entry still exist.

Post back with the info.
[INDENT]still try'n to help <==BDQ

[/INDENT]

---

### Post by NikTh on 2012-10-11
> **abexman said:**
> OK, so I booted into Ubuntu and ran Gparted and this time I was able to quickly format sda7 as linux-swap. I guess I'm done?? Thanks ya'll!

No you are not done yet. 

Check if swap is up and running. 

Give this command ```
free -m
``` and check the swap. 

If is not up and running then give again the results of 

```
sudo blkid
cat /etc/fstab
```

Thanks

---

### Post by abexman on 2012-10-11
I guess this means Swap is running? 

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3773       3426        347          0         87       1998
-/+ buffers/cache:       1340       2432
Swap:         4008          1       4007

```

```
/dev/sda1: LABEL="SYSTEM" UUID="7468F1FD68F1BDC4" TYPE="ntfs" 
/dev/sda2: UUID="68D0F622D0F5F662" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="28E8D02EE8CFF7D8" TYPE="ntfs" 
/dev/sda5: LABEL="root" UUID="dcd54473-3a8a-4582-a046-a654a3f95e42" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c" TYPE="ext4" 
/dev/sda7: LABEL="swap" UUID="19d09a37-7454-42ab-9143-c7a4cdfadb76" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="1a139895-979c-4421-b6f1-e21d189a1b40" TYPE="swap" 

```

Comment out Cryptswap line?

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=dcd54473-3a8a-4582-a046-a654a3f95e42 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=bdb39428-0f55-4152-acf4-4b12f54a18a7 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

---

### Post by NikTh on 2012-10-11
> **abexman said:**
> I guess this means Swap is running? 

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3773       3426        347          0         87       1998
-/+ buffers/cache:       1340       2432
Swap:         4008          1       4007
``` Yes swap is running , but cryptswap is running. There is no swap entry in /etc/fstab/ 
> **abexman said:**
> ```
/dev/sda1: LABEL="SYSTEM" UUID="7468F1FD68F1BDC4" TYPE="ntfs" 
/dev/sda2: UUID="68D0F622D0F5F662" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="28E8D02EE8CFF7D8" TYPE="ntfs" 
/dev/sda5: LABEL="root" UUID="dcd54473-3a8a-4582-a046-a654a3f95e42" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c" TYPE="ext4" 
/dev/sda7: LABEL="swap" UUID="19d09a37-7454-42ab-9143-c7a4cdfadb76" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="1a139895-979c-4421-b6f1-e21d189a1b40" TYPE="swap" 

```Comment out Cryptswap line?

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=dcd54473-3a8a-4582-a046-a654a3f95e42 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=bc4e2fda-bfac-42c1-b57c-c7e51cbd3c6c /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=bdb39428-0f55-4152-acf4-4b12f54a18a7 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

If you take a closer look in /etc/fstab and blkid results , you will see that UUID of swap is not matched. If you comment out the crypswap as the /etc/fstab it is now ,you will not have swap at all. 

You know what ?
 I suggest to delete the swap you created with gparted. Is not needed. Your swap is (and was) up and running , but is crypted (you used crypt-fs in past to encrypt your /home or /swap ? probably). 

So delete the swap you created and merge the space of 3.92GB with root. (to increase it even more.) 

You can always see if swap is up and running with command ```
free -m
```

Thanks

---

