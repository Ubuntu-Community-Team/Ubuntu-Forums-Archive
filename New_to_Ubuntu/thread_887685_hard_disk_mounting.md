---
title: "hard disk mounting"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by amit.padhy on 2008-08-12
Hello everyone again..
i have problems mounting the hard disk.....
i am working on an ubuntu live CD now...
and fsck gives:
```
fsck 1.40.2 (12-Jul-2007)

```

and it is not in my mtab neither on my fstab.and fdisk -l also does not return anything.

It detects "something" at start i.e. the BIOS but there is no GRUB....i have only linux on my computer...

can anybody help me????

it does not auto mount...neither in /mnt nor in /media....

I had 5 partitions on the disk of 160GB when i last accessed it.
i had restarted/reset my computer when it hanged and after that :(
thanks in advance...

---

### Post by Dill on 2008-08-12
Try this:

```
sudo fdisk -l
```

fdisk -l by itself produces no output, but adding a sudo to the front should do the trick. On the Live CD, it shouldn't even prompt you for a password, unless I'm mistaken.

After that, you should get some output like this

```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8001b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        7649    10240965   a5  FreeBSD
Partition 2 does not end on cylinder boundary.
/dev/sda3            7650        7904     2048287+  82  Linux swap / Solaris
/dev/sda4            7905       11978    32724405   83  Linux
```

Here, I have a choice of 4 partitions that I can mount. If I wanted to mount /dev/sda1, I'd first have to create a "mount point" (that is, the place where I'm going to mount it). I might do this by typing something like: 

```
cd /mnt
sudo mkdir sda1
```

Once I've created the mount point, I can finally mount the partition:

```
sudo mount /dev/sda1 sda1
```

Did you say you just had one Linux partition? If you ever want to mount an NTFS volume (Windows XP, Vista, etc.), you can use ntfs-3g . It works just like mount...

```
ntfs-3g /dev/sda1 sda1
```

This mounts NTFS volumes with read/write privileges; if you use mount, you're only allowed to read.

Hope this helps. Please let me know if you have any more trouble.

Cheers, 
Dylan

---

### Post by amit.padhy on 2008-08-12
i thought i clearly mentioned that sudo fdisk -l returns nothing....

somebody please help me!!!!!!!

---

### Post by yochaigal on 2008-08-12
what does dmesg show?  
do:

dmesg | tail  

If fdisk shows nothing, then either the drive has I/O errors or it's disconnected.

---

### Post by Dill on 2008-08-13
Sorry, mate. You stated that you ran fdisk -l , not *sudo* fdisk -l . As you can tell from the screenshot, there's a difference.

Let me know what the output of this command is

```
ls /dev/sda* /dev/hda*
```

---

