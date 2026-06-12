---
title: "No space left on device"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by jmate24 on 2012-02-12
My hdd is having problems as well with the root partition losing space. I have tried all that you suggest and bleachbit and to no avail the space keeps filling up. I am also wondering that if I really need swap space wnen I have 16GB of memory I also noticed at boot that there was an error in which it said it cannot create swap files in the swap space and so it is filling up my /. So do I just delete / and swap and create a large / partition or do I add a smaller swap partition say 24GB instead of 32?       
     Because I heard that you need atleast 2-2.5x swap space to memory so that when you hibernate you can save your state to disk without any problems especially if you have many programs running at once.


Here's my sudo fdisk -l and etc.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000493c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    46886911    23442432   83  Linux
/dev/sda2        46886912   117800959    35457024   82  Linux swap / Solaris
/dev/sda3       117800960  1465147391   673673216   83  Linux

Disk /dev/sdb: 15.8 GB, 15812526080 bytes
255 heads, 63 sectors/track, 1922 cylinders, total 30883840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0ee6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    30883839    15440896   83  Linux

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G   21G   56M 100% /
udev                  7.9G   12K  7.9G   1% /dev
tmpfs                 3.2G  1.2M  3.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  7.9G  132K  7.9G   1% /run/shm
/dev/sda3             633G  302G  299G  51% /home
/dev/sdb1              15G  1.5G   13G  11% /media/56b30434-a22f-48d9-a912-3c7eb7a18bd3

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4bec49c8-9552-41b2-8b01-9722de2fccf4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=13a6fb47-c14a-4b89-b89d-a25fea1b85e4 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=e5ca5a88-54d7-4cc2-a86f-e1941976b33f none            swap    sw              0       0


sudo blkid
/dev/sda1: UUID="4bec49c8-9552-41b2-8b01-9722de2fccf4" TYPE="ext4" 
/dev/sda2: UUID="e5ca5a88-54d7-4cc2-a86f-e1941976b33f" TYPE="swap" 
/dev/sda3: UUID="13a6fb47-c14a-4b89-b89d-a25fea1b85e4" TYPE="ext4" 
/dev/sdb1: UUID="56b30434-a22f-48d9-a912-3c7eb7a18bd3" TYPE="ext4"

Any help would be apprieciated.
Thanx

---

### Post by oldos2er on 2012-02-12
Post moved to its own thread. Please don't hijack other people's threads; thanks for understanding.

---

### Post by SeijiSensei on 2012-02-12
You need to see where the usage is concentrated.  Try this:

```
cd /
sudo du -s *

```

That will print a summary of disk usage by top-level directory.  The big ones are typically /var and /usr (since you mount /home from a separate partition).

Did you ever have /home not housed separately on /dev/sda3?  If you did, it's possible there are still files in /home on the root filesystem which are "hidden" because /dev/sda3 is mounted on top of them.

You can try this:  first, reboot into recovery mode, then issue the command "umount /home".  Now run "du -s /home".  You should get back a trivially small number.  If not, then there are files in the old /home that are eating up space, but you never see them because /dev/sda3 is mounted on top of them.

---

### Post by mcduck on 2012-02-12
If you want to be able to hibernate the machine, you need at much swap space as you are using memory when you hibernate. (so if you want to be sure it'll always work, you should have at as much swap as you have RAM). Even if you don't ever hibernate, I'd recommend having at least a small swap partition of a gigabyte or two as the kernel uses a little swapping as means of memory management. (most of the time things will work fine without any swap, but it can sometimes cause problems and considering the sizes of hard drives these days using a gigabyte for this shouldn't be a problem...)

The rule about swap being 2-2.5 times RAM was true when the amounts of RAM in computers were much lower than what we have these days. It really doesn't apply any more once you go over 1GB of RAM, after that it's just a question of having enough swap for hibernating.

Anyway, if the system can't use the swap for some reason or other, it's not going to fill your root partition. So whatever is using the space there,  it's something else than swap. SeijiSensei's tips about figuring out where the space has gone would be a good start.

---

### Post by jmate24 on 2012-02-12
Here's what the output of that command.
8428	bin
46692	boot
4	cdrom
4	dev
17708	etc
du: cannot access `home/justin/.gvfs': Permission denied
316161564	home
0	initrd.img
0	initrd.img.old
361168	lib
14560	lib32
4	lib64
16	lost+found
1339184	media
4	mnt
4	nonexistent
139504	opt
du: cannot access `proc/3179/task/3179/fd/4': No such file or directory
du: cannot access `proc/3179/task/3179/fdinfo/4': No such file or directory
du: cannot access `proc/3179/fd/4': No such file or directory
du: cannot access `proc/3179/fdinfo/4': No such file or directory
0	proc
35740	root
1276	run
21288	sbin
4	selinux
4	srv
0	sys
32236	tmp
5203048	usr
15767796	var
0	vmlinuz
0	vmlinuz.old
I belive it is mostly in my /var and /lib folder. And home is it's separate mountpoint I have had problems with Segate hdds in the past and not with WD drives maybe I should go back to WD?

---

### Post by mcduck on 2012-02-13
/var seems quite big indeed. You might want to check in /var/log if there's any log files that are large in size. If there's some problem on your system it might result in huge numbers of error messages causing logs to grow and eat the disk space.

(And if any of the log files is large, make sure you actually take a look inside it to see what the error messages are before deleting the file...  That would make it a lot easier to fix the underlying problem, as deleting the log file is just a temporary cure...)

---

