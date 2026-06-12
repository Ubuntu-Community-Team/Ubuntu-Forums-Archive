---
title: "[SOLVED] How do I mount a drive automatically at start up?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by RobHK on 2008-08-07
All my partitions appear in Computer but only the external ones mount automatically. I want my internal NFTS partitions to mount automatically like the external ones do (so that the VirtualBox they share with can open).

I've browsed the topic but a lot of what I found was complicated, and may have been outdated. I figured I might need to add stuff to fstab, but I don't know what to add.

In case it helps I did fdisk -l and this is the output:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5b4a5b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4724    37945498+   7  HPFS/NTFS
/dev/sda2            4725        9729    40202662+   5  Extended
/dev/sda5            4725        8748    32322748+  83  Linux
[COLOR="Red"]/dev/sda6            9670        9729      481918+   7  HPFS/NTFS
/dev/sda7            9012        9669     5285353+   7  HPFS/NTFS[/COLOR]
/dev/sda8            8749        9011     2112516   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23961542

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdb1               1        5388    43279078+   7  HPFS/NTFS[/COLOR]
/dev/sdb3           14452       14596     1164712+   5  Extended
/dev/sdb4            5389       14451    72798547+  83  Linux
/dev/sdb5           14452       14596     1164681   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045ade

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2        1403    11261533+   b  W95 FAT32
/dev/sdc6            1404       33274   256003776    7  HPFS/NTFS
/dev/sdc7           33275       56221   184321746    7  HPFS/NTFS
/dev/sdc8           56222       68969   102398278+  83  Linux

```[COLOR="Red"]The drives I would like to mount automatically are in red.[/COLOR]

---

### Post by kpkeerthi on 2008-08-07
[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

---

### Post by cdtech on 2008-08-07
Create a mount point:
```
sudo mkdir /mnt/[COLOR="Red"]sda6[/COLOR] ([COLOR="Red"]sda7[/COLOR] or whatever you want to name it).
```

This is the way I set mine up within the "/etc/fstab" file. Use "sudo gedit /etc/fstab" to edit yours. 

```
# Entry for /dev/sda6 :
UUID=C6AAD33AAAD325A9 /mnt/[COLOR="Red"]Yourmountpoint[/COLOR] ntfs defaults,umask=002,gid=46 0 2
```

You can just add three each of the above changing only the device. To find your block id just issue the command (simply) "blkid".

Hope this helps......

---

### Post by cdtech on 2008-08-07
> **kpkeerthi said:**
> [https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

"ntfs-3g" is not needed with the latest kernels.....

---

### Post by Rocket2DMn on 2008-08-07
ntfs-3g is built in nowadays since it is on stable releases.  The wiki link posted earlier is a great resource, it forwards to [uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp] - much of which I wrote myself :)
If you need further help getting your fstab setup, we'd be glad to help.  Just post the output of these commands
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by dileepm on 2008-08-07
There is a better way go to the file /etc/hal/fdi/policy/prefrences.fdi

You find the following 
```

<device>
   <match key="storage.hotpluggable" bool="false">
     <match key="storage.removable" bool="false">
       <merge key="storage.automount_enabled_hint" type="bool">false</merge>
     </match>
   </match>
 </device>

```

Replace the value "false" of the third tag <merge key="storage.automount_enabled_hint" type="bool">false</merge> to "true".

---

### Post by RobHK on 2008-08-07
> **dileepm said:**
> There is a better way go to the file /etc/hal/fdi/policy/prefrences.fdi

You find the following 
```

<device>
   <match key="storage.hotpluggable" bool="false">
     <match key="storage.removable" bool="false">
       <merge key="storage.automount_enabled_hint" type="bool">false</merge>
     </match>
   </match>
 </device>

```

Replace the value "false" of the third tag <merge key="storage.automount_enabled_hint" type="bool">false</merge> to "true".
Thanks Dileep.

I knew there had to be some simple fix like this, if the partitions were already appearing and just needed a click. But this is Linux. Why just change a switch if you can write a dozen lines of code instead? ;)

---

### Post by wadeo on 2008-08-08
> **dileepm said:**
> There is a better way go to the file /etc/hal/fdi/policy/prefrences.fdi

You find the following 
```

<device>
   <match key="storage.hotpluggable" bool="false">
     <match key="storage.removable" bool="false">
       <merge key="storage.automount_enabled_hint" type="bool">false</merge>
     </match>
   </match>
 </device>

```

Replace the value "false" of the third tag <merge key="storage.automount_enabled_hint" type="bool">false</merge> to "true".


I'd love to do the same thing as mentioned at the top of this thread, but following this advice, which seems simple enough, leads me to a blank file? Should I have data in this location?

Thanks

---

### Post by RobHK on 2008-08-09
> **wadeo said:**
> I'd love to do the same thing as mentioned at the top of this thread, but following this advice, which seems simple enough, leads me to a blank file? Should I have data in this location?

Thanks

He mistyped the word "preferences"! Add an "e" ;)

---

### Post by Jeenyus on 2008-08-10
> **Rocket2DMn said:**
> ntfs-3g is built in nowadays since it is on stable releases.  The wiki link posted earlier is a great resource, it forwards to [uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp] - much of which I wrote myself :)
If you need further help getting your fstab setup, we'd be glad to help.  Just post the output of these commands
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

I am trying to have my XP/Ubuntu shared FAT32 partition mount automatically when I boot up.

Output for given commands:
```
drew@ubuntu-3000:~$ sudo fdisk -l
[sudo] password for drew: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda2            4570        6651    16723665    5  Extended
/dev/sda4            6652        9729    24724035    b  W95 FAT32
/dev/sda5            4570        5806     9936171   83  Linux
/dev/sda6            5807        6526     5783368+  83  Linux
/dev/sda7            6527        6651     1004031   82  Linux swap / Solaris
drew@ubuntu-3000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=a047225f-c221-4133-942f-75c28faaddfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=4589f23d-57fb-45ec-85ae-2bd1980c6ba6 /home           ext3    relatime        0       2
# /dev/hda7
UUID=2f31f2b0-6ec6-4f4a-b8f0-2bb76ffad631 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda4	/media/disk	vfat	0	2
drew@ubuntu-3000:~$ sudo blkid
/dev/sda1: UUID="62EAFBF16D5E4C87" TYPE="ntfs" 
/dev/sda4: UUID="FF14-5591" TYPE="vfat" 
/dev/sda5: UUID="a047225f-c221-4133-942f-75c28faaddfe" TYPE="ext3" 
/dev/sda6: UUID="4589f23d-57fb-45ec-85ae-2bd1980c6ba6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="2f31f2b0-6ec6-4f4a-b8f0-2bb76ffad631" 
drew@ubuntu-3000:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/drew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drew)
```

Thanks

---

### Post by RobHK on 2008-08-10
> **Jeenyus said:**
> I am trying to have my XP/Ubuntu shared FAT32 partition mount automatically when I boot up.

Output for given commands:
```
drew@ubuntu-3000:~$ sudo fdisk -l
[sudo] password for drew: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda2            4570        6651    16723665    5  Extended
/dev/sda4            6652        9729    24724035    b  W95 FAT32
/dev/sda5            4570        5806     9936171   83  Linux
/dev/sda6            5807        6526     5783368+  83  Linux
/dev/sda7            6527        6651     1004031   82  Linux swap / Solaris
drew@ubuntu-3000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=a047225f-c221-4133-942f-75c28faaddfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=4589f23d-57fb-45ec-85ae-2bd1980c6ba6 /home           ext3    relatime        0       2
# /dev/hda7
UUID=2f31f2b0-6ec6-4f4a-b8f0-2bb76ffad631 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda4	/media/disk	vfat	0	2
drew@ubuntu-3000:~$ sudo blkid
/dev/sda1: UUID="62EAFBF16D5E4C87" TYPE="ntfs" 
/dev/sda4: UUID="FF14-5591" TYPE="vfat" 
/dev/sda5: UUID="a047225f-c221-4133-942f-75c28faaddfe" TYPE="ext3" 
/dev/sda6: UUID="4589f23d-57fb-45ec-85ae-2bd1980c6ba6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="2f31f2b0-6ec6-4f4a-b8f0-2bb76ffad631" 
drew@ubuntu-3000:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/drew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drew)
```

Thanks

Have you tried Dileepm's suggestion above? It worked for me. Just make sure you correct his typo (prefrences>preferences). It just involves changing a single "false" to "true".

---

