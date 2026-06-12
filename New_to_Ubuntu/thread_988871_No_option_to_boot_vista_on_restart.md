---
title: "No option to boot vista on restart"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2008-11-20
Hi,

Totally new.  Just installed Ubuntu as a dual boot (I think), and I can't figure out how to get back into Vista.

When I restart it goes automatically to Ubuntu rather than getting an option.

Halp!
Charles

---

### Post by tvtech on 2008-11-20
that sounds bad. you should get a grub prompt you can edit grub manually once you've booted.  

what do you see when you do the following at in a terminal 

```
sudo fdisk -l
```  you should see multiple drives showing up something like the following ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               3       20320    10240000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *       20320      262579   122098688    7  HPFS/NTFS
/dev/sda3          262579      484521   111858688    f  W95 Ext'd (LBA)
/dev/sda5          262581      484521   111857664    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d787f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   1c  Hidden W95 FAT32 (LBA)
/dev/sdb2   *         974       15684   118166107+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3           15685       30401   118214302+  83  Linux

```

note that sda2 is my vista installation, sda5 is a storage partition to move things between nix and windows.  Everything on sdb is nix 

if you don't see something showing an ntfs partition you are going to want to stop using your computer right now if you had important files you didn't want to loose and do some reasearch on windows/ ntfs file recovery before you turn anything back on.

---

### Post by tvtech on 2008-11-20
the good thing about windows file recovery is it's fairly easy and straight forward as long as you haven't overwritten anything.  

if it's as simple as a grub failure, you'll need to manually edit it to find the information on this open a terminal and check out 

```
man grub
```

honestly the man pages are the best source of information for how to do things on nix.

---

### Post by NewbuntuUser777 on 2008-11-20
This is what I get.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ace2eeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17124   137548498+   7  HPFS/NTFS
/dev/sda2           37760       38914     9268224    7  HPFS/NTFS
/dev/sda3           17125       37759   165750637+   5  Extended
/dev/sda5           17125       37007   159710166   83  Linux
/dev/sda6           37008       37759     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2008-11-21
OK, when you boot into Ubuntu, how about opening a terminal (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then find the line that says "hiddenmenu", and put a pound sign # in front of it:
```
# hiddenmenu
```
Next, at the very bottom of the file add:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
Reboot, and let me know if booting Vista works; if not, let me know exactly what happens when you choose it from the Grub menu. :)

---

