---
title: "[SOLVED] 2-drive dual boot not working"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by edzell on 2008-08-29
I've reinstalled Ubuntu 8.04 using alternate (not live) CD. My previous dual-boot arrangement (Win 98 on second drive) no longer works. I've inserted in menu.lst the code:
 
title              Windows
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

- tried it in various locations with no luck. Windows shows up in the start menu (#hidden) but clicking  on it produces no movement. Puzzling because this worked before the Ubuntu reinstal.

History:

Originally installed 7.10 on virgin master HD with existing Win98 slave de-powered; immediately upgraded on-line to 8.04. Reconnected Windows slave HD then edited menu.lst as above: Dual-boot worked right away.

After cluttering Ubuntu with various software, decided to do a clean reinstal. Removed all partitions with gparted, downloaded 8.04 alternate, transferred to a CD and installed from that. (Forgot to de-power the Win slave while doing it.) Edited menu.lst as above but windows option in the start menu doesn't work.

Win slave has 2 partitions - one for OS & apps, one for Data.

All assistance welcome!

---

### Post by louieb on 2008-08-29
Your windows entry looks like its should work.
Please post the partition table. (Lowercase L at the end) for Win98 looking for a partition of type vfat.
```
sudo fdisk -l
```

---

### Post by edzell on 2008-08-30
> **louieb said:**
> 
```
sudo fdisk -l
```

Thanks and here's the result (sdb6 & 7 - where did they come from & why?)
________________________

Disk /dev/sda: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000ece1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1784    14329948+  83  Linux
/dev/sda2            1785        1868      674730    5  Extended
/dev/sda5            1785        1868      674698+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e748b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         638     5124703+   b  W95 FAT32
/dev/sdb2             639        2498    14940450    f  W95 Ext'd (LBA)
/dev/sdb5             639        1913    10241406    b  W95 FAT32
/dev/sdb6            1914        2465     4433908+  83  Linux
/dev/sdb7            2466        2498      265041   82  Linux swap / Solaris

_____________________________

All help gratefully received.

---

### Post by louieb on 2008-08-30
Looks like you have 2 Linux installs. (sda1 and sdb6)  Wonder which one its booting to?
Post the output of 
```
df -h
```
That will list your mount points and show how much of each is being used.

Your XP entry should work if the / (root) mount point is  sda1.

If the df -h command shows it to be **sdb6** the your windows entry may look something like this.
```
title              Windows
root               (hd0,0)
savedefault
makeactive
chainloader        +1
```

Also would like you to post the 1st Ubuntu entry in  menu.lst.

---

### Post by edzell on 2008-08-30
> **louieb said:**
> Looks like you have 2 Linux installs. (sda1 and sdb6)  Wonder which one its booting to?
Post the output of 
```
df -h
```
That will list your mount points and show how much of each is being used.

Your XP entry should work if the / (root) mount point is  sda1.

If the df -h command shows it to be **sdb6** the your windows entry may look something like this.
```
title              Windows
root               (hd0,0)
savedefault
makeactive
chainloader        +1
```

Also would like you to post the 1st Ubuntu entry in  menu.lst.

Sorry, I haven't figured how to format to display properly but df -h gives:
_________________

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.3G   11G  18% /
varrun                236M  108K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M   76K  236M   1% /dev
devshm                236M   52K  236M   1% /dev/shm
lrm                   236M   39M  198M  17% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       14G  2.3G   11G  18% /home/edzell/.gvfs
/dev/sdb6             4.2G  2.1G  1.9G  53% /media/disk
_____________________

So I guess ubuntu is booting to the master drive as expected.
The 4.5G on sdb6 is a recent arrival; not something I consciously created:) It now shows up in nautilus.

menu.lst looks like this, again ill-formatted:
_____________________

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f8547f70-efe9-4ed9-926a-325fcd3c54d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f8547f70-efe9-4ed9-926a-325fcd3c54d8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
_________________________

(currently the windows entry sits just above ### BEGIN AUTOMAGIC KERNELS LIST, one of several places I've tried locating it.)

---

### Post by kansasnoob on 2008-08-30
Look here:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by louieb on 2008-08-30
With all I've seen. your original Win98 grub entry should have worked. But I have rearranged the order and modified the root statement to rootnoverify. Might try that. 
```

title Windows
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```

What exactly does it do when you try to boot Windows? Anything?

Wonder what would happen if you took out the Linux Drive and tried to boot with just Widows drive in set as master.

Could be the boot sector of Widows partition is corrupt. Do you have a Windows install CD? With the Windows drive in and set as master might try the recover console of Windows Install CD. There are two commands to try **fixmbr** and **fixboot**.  

If you don't have the Install CD. I believe the super grub disk can fix a windows boot sector too.

Just have to try and see what happens.

---

### Post by kansasnoob on 2008-08-30
It's always much easier to have all operating systems on one hard drive and use any additional drives for storage.

Otherwise you need to read all of this:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by edzell on 2008-08-31
> **louieb said:**
> With all I've seen. your original Win98 grub entry should have worked. But I have rearranged the order and modified the root statement to rootnoverify. Might try that. 
```

title Windows
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```What exactly does it do when you try to boot Windows? Anything?

Wonder what would happen if you took out the Linux Drive and tried to boot with just Widows drive in set as master.

Could be the boot sector of Widows partition is corrupt. Do you have a Windows install CD? With the Windows drive in and set as master might try the recover console of Windows Install CD. There are two commands to try **fixmbr** and **fixboot**.  

If you don't have the Install CD. I believe the super grub disk can fix a windows boot sector too.

Just have to try and see what happens.

Trying to boot to windows, nothing happens. The entry is in the menu but clicking on it does nothing.

No problem with the Windows drive as sole HD set to master, despite the presence of the uninvited sdb6 (which windows fdisk doesn't see.) WIndows fires up just fine.

I'll try your reworked grub entry but I'm beginning to lean towards a from-scratch reinstal - again! Having occasional freeze-ups and spontaneous reboots of ubuntu; things I hoped would stop when I switched from MS. I'm thinking there's something wrong with the ubuntu or grub on my system.

To other responders: Don't agree that it's always or necessarily "best" to have both OS on 1 HD. Been there & decided to avoid it in future. And my problem isn't the absence of grub; it's there but doesn't respond to the windows option.

---

### Post by edzell on 2008-08-31
> **louieb said:**
> With all I've seen. your original Win98 grub entry should have worked. But I have rearranged the order and modified the root statement to rootnoverify. Might try that. 
```

title Windows
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```Just have to try and see what happens.

Well, well, well ................ I did and it worked! Many thanks.
I'm going to mark this thread solved - if I can find out how - although I still don't understand why the code that worked before wouldn't work this time around. Also don't have a clue why I get freeze-ups & reboots. Oh, well, maybe it will all come right in the end :)

 I know there's a way to register thanks on the forum but I haven't found it either, so this is it;

thanks louieb!!

---

### Post by garyed on 2008-08-31
Glad you got it solved. 
I guess my idea wouldn't have worked.

---

