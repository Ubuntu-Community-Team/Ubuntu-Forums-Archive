---
title: "Entire hard drive shows up as unallocated in gparted"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by bobheaps on 2008-10-15
I finally decided to get rid of my xp partition and use the space to expand my /home. When i entered gparted it shows the hard drive as one big unallocated space. I searched the forum and got some leads but the problem still persists. The following are some of my findings 
running mount in a terminal produces
bobheaps@bobheaps-desktop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
/dev/sda1 on /media/Windows type vfat (rw,nosuid,nodev,uid=1000,gid=100,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bobheaps/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bobheaps)
bobheaps@bobheaps-desktop:~$ 

running fdisk -l produces
bobheaps@bobheaps-desktop:~$ sudo fdisk -l
sudo: unable to resolve host bobheaps-desktop
[sudo] password for bobheaps: 
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec4bec4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5176    41576188+   c  W95 FAT32 (LBA)
/dev/sda2            5177       19457   114712132+   5  Extended
/dev/sda3            9511       19457    79899246   83  Linux
/dev/sda5            5177        5243      538114+  82  Linux swap / Solaris
/dev/sda6            5244        9510    34274646   83  Linux
bobheaps@bobheaps-desktop:~$ 

running sudo testdisk produces
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA                0   1  1  5175 254 63   83152377 [NO NAME]
 2 E extended              5176   0  1 19456 254 63  229424265
 3 P Linux                 9510   1  1 19456 254 63  159798492
Space conflict between the following two partitions
 2 E extended              5176   0  1 19456 254 63  229424265
 3 P Linux                 9510   1  1 19456 254 63  159798492
   X extended              5176   0  2  5242 254 63    1076354
 5 L Linux Swap            5176   2  1  5242 254 63    1076229
   X extended              5243   0  1  9509 254 63   68549355
 6 L Linux                 5243   1  1  9509 254 63   68549292




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

and also 
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1  5175 254 63   83152377 [NO NAME]
P Linux                 5176   0  1  8494 254 63   53319735











Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 42 GB / 39 GiB
 
What can I do now?

---

### Post by dhtseany on 2008-10-15
OK so I'll admit that I only skimmed what you posted but did you format your drive after deleting the old XP partition? That is what unallocated space is: unformatted space.

Peace
Sean

Quick definition:
[http://www.real-knowledge.com/unallocated-space.htm](http://www.real-knowledge.com/unallocated-space.htm)

---

### Post by eternalnewbee on 2008-10-15
Only thing I can think of is windows wasn't shut down properly...
Can't really help you, just be careful with Gparted. I destroyed my whole system once. Don't even know where it went wrong. Wait for some more expert advice.
Patience is a virtue.
Good luck

---

### Post by drs305 on 2008-10-15
If you get to the point where you are afraid you may have reformatted your entire drive, stop doing anything that may write to the disk.

You can use the TestDisk (testdisk) to restore the partition information and most likely restore your lost partitions. I believe you can get to it from the livecd or from a systemrescuecd. [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by louieb on 2008-10-16
Primary partition sda3 is inside extended partition sda2.  
That should not be. only logical partitions should be in an extended partition. 
GParted (or the Ubuntu installer) sees that and won't do anything with the drive.  

Just wondering if you have installed PCLinoxOS?  Its partitioner (Disk Drake) will do stuff like that.  May be able to use it again to fix the problem.

Basically to get the partition layout to follow the rules  you need to shrink extended partition sda2 so that it stops just before primary partition sda3 begins.

---

### Post by hyper_ch on 2008-10-16
posting config files/terminal output in [noparse]```

```[/noparse] brackets makes it a lot simpler to read.

---

### Post by bobheaps on 2008-10-17
Sorry - Will try to remember next time.
Could you post an example?

---

### Post by bobheaps on 2008-10-17
If I understand you I have to reset the end of sda2 to 9509 is this correct?
also, what tool could i use to do this? I used gparted(I think) when installing Ubuntu but now it doesn't recognize any partitions

---

