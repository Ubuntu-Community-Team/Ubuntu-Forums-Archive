---
title: "setting ubuntu to auto-mount storage drives"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by pikeman47 on 2008-07-28
I have a storage drive and a storage partition on my Ubuntu Hardy setup, but when my computer starts up, i have to manually mount these drives. How could i set up Ubuntu to automatically mount these drives at startup?

Thanks

---

### Post by Potatoj316 on 2008-07-28
you can add a line to your fstab file.  Post the result of this
```
cat /etc/fstab
```
also what kind of drive it the one you want to auto-mount (ide, sata?)

---

### Post by pikeman47 on 2008-07-28
cat /etc/fstab results:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c515482-7ef0-4040-859e-983644f3a828 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c935e399-2d63-4930-be0f-d6b5db2f2e3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

the drives are IDE drives

---

### Post by Potatoj316 on 2008-07-28
Ok then add this file to that file
/dev/sdb1 /MOUNTPOINT ext3 defaults 0 0

change the MOUNTPOINT to where you want the drive to show up.

This is if you want the first partition on your second IDE drive to be mounted.  Tell me what drives and partitions you want to have mounted and I can modify it to fit your needs.  Also I will need to know what filesystems they use.

---

### Post by bodhi.zazen on 2008-07-28
See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Please ask if you are having problems.

---

### Post by pikeman47 on 2008-07-28
I have a physical 80 gig IDE drive and a 150 gig partition from my main hard drive (also IDE). I ran the diskmounter script found in the How To Fstab link, but it only auto mounted my 80 gig.
The filesystem for the 150 i need to mount is ext3.

---

### Post by bodhi.zazen on 2008-07-28
You need to add an entry (manually) to fstab.

To see your partitions :

```
sudo fdisk -l
```

or 

```
sudo blkid
```

---

### Post by pikeman47 on 2008-07-28
ok, the drive that i need to be mounted is sda3 and has an ext3 filesystem. when i open up ```
sudo gedit /etc/fstab
```, what do i need to add to that file to get my sda3 partition to be automatically mounted?

---

### Post by bodhi.zazen on 2008-07-28
The link I gave you goes through fstab

device mount_point file_system options 0 0

so, all you need is a mount point ...

/dev/sda3 <mount_point> ext3 defaults 0 0

---

### Post by pikeman47 on 2008-07-28
I tried editing fstab and adding this line to the end of it:

```
/dev/sda3 /media/sda3 ext3 defaults 0 0
```

and nothing.
I restarted my computer and my drive is unmounted.

---

### Post by bodhi.zazen on 2008-07-28
does the mount point exist ?

```
sudo mkdir /media/sda3
```

If so, change "defaults" to "users,auto"

---

### Post by pikeman47 on 2008-07-28
Thanks, worked like a charm.

---

