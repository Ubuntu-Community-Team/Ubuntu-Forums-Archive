---
title: "New triple boot install WinXP/10.04 and 12.04 - 2 MBR?"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by emarkay on 2012-08-24
I reinstalled 12.04.1 on a trible boot system and got the  "error no such device", "Grub rescue" prompt.

I found this thread: 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
but you see what happened, then here:


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058ed2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   125835263    62916608    7  HPFS/NTFS/exFAT
/dev/sda2       125835264   461389823   167777280    7  HPFS/NTFS/exFAT
/dev/sda3       461389824   618676223    78643200   83  Linux
/dev/sda4       618676224   625141759     3232768   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6065

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   188570969    94285453+   7  HPFS/NTFS/exFAT
/dev/sdb2       188570970   272462399    41945715    7  HPFS/NTFS/exFAT
/dev/sdb3   *   272462400   398297087    62917344   83  Linux
ubuntu@ubuntu:~$ sudo mkdir /media/sdb3 
ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /media/sdb3
ubuntu@ubuntu:~$ sudo grub-install --root-directory=media/sdb3 /dev/sdb3
/usr/sbin/grub-probe: error: cannot find a device for media/sdb3/boot/grub (is /dev mounted?).
```


When I reinstalled new 12.04 I "think" I said sdb, not remembering that I "may" have used sda for the mbr...  It appears this is so.

Anyway, Ignore my noobiness but I am sort of stuck here and I need to get off to work - can someone please assist so I can get to my system when I return.

I just want a grub2 boot  to 12.04.1 LTS, WinXP and 10.04LTS as  I had before.

Also, is that what I did?  The 12.04.1 install defaulted to sdb to load bootloader on install - I presumed it "knew" that is where it was/should be (but I guess not?)

 I would like to not have to reinstall 120.4.01 all over, but if i have to,  will it delete the (apparently now wrong) boot loader on sdb?   
If NOT, how do I do it before re-installing?

Thank you (again!)!  
 MRK

---

### Post by sandyd on 2012-08-24
Two ways to do it.
```

sudo grub-install --root-directory=/media/sdb3 /dev/sda

```or
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sdb3 /mnt/ubuntu
sudo mount --bind /dev /mnt/ubuntu/dev
sudo mount --bind /sys /mnt/ubuntu/sys
sudo mount --bind /proc/mnt/ubuntu/proc
sudo chroot /mnt/ubuntu
sudo grub-install /dev/sda
```

---

### Post by emarkay on 2012-08-24
Thanks!

Or - forgot all about this lifesaver!

"sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair"

---

