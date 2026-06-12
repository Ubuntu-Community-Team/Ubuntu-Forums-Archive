---
title: "second hard drive cannot be written to"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by wog on 2008-05-22
I have a 10GB drive (which is where the main body of Linux is) and a 30GB drive (which is where the /home directory was before updating to 8.04.

When I upgraded to 8.04, the system couldn't access the second drive, so I had to revert to the old backup /home.

I still can't automount the second drive, so I can't set up the second drive as /home again. I can only access it after the system finishes booting.

Now I'm discovering when I try to use Azureus that I can read the data on the second drive, but I can't write to that drive.

Can someone tell me what to do and in what order?

---

### Post by shifty_powers on 2008-05-22
btw, careful with that name, it is a very offensive word here in britain ;)

---

### Post by TeoBigusGeekus on 2008-05-22
Well, if you want it to be automounted on startup, you have to fiddle with your fstab file.
Please post us the output of
```
sudo fdisk -l
```
```
mount
```
and the content of fstab
```
gksudo gedit /etc/fstab
```

---

### Post by wog on 2008-05-22
> **shifty_powers said:**
> btw, careful with that name, it is a very offensive word here in britain ;)

I named myself that on purpose. Is it still an insult if I'm insulting myself? :)

---

### Post by shifty_powers on 2008-05-22
hey, i ain't fussed, don't get me wrong :D

but over here, that is a rather racist and very derogative term ;)

just warning you in case you didn't realise.

hope you get yourproblem sorted btw....

---

### Post by wog on 2008-05-22
**Output of sudo fdisk -l**:
Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000230b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2c3c2c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3738    30025453+  83  Linux

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3936     1007600    6  FAT16

**Output of mount**:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

**Output of gksudo gedit /etc/fstab**:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=15c1f36a-162f-4df8-8fce-0223e67babd3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=36e6a684-fe6f-408e-b791-a7439c4dc885 none            swap    sw              0       0
# This is my attempted mount point
# /dev/sdb1 UUID=68c84fec-c953-4ed9-9371-27c8fcc9aa57    /home           ext3        nodev  1       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto   0       0
/dev/fd0        /media/floppy0  auto       rw,user,noauto  0       0

---

### Post by TeoBigusGeekus on 2008-05-23
Try this
```
/dev/sdb1     /media/disk     ext3     relatime     0     2
```

---

### Post by wog on 2008-05-26
I can make folders in the old home folder, but not in the spaces below that.

Perhaps in the interests of helping me go back to the way things were before, you could explain what sort of fstab line I'd need to automount that drive as my home directory? Or is it better to get all of the drive working again before trying to convert the drive to my home directory?

---

### Post by hyper_ch on 2008-05-26
(1) when posting some code or output, use [noparse]```

```[/noparse] tags around it. It makes it much easier to read

(2) I'm not sure if I understand your problem right. You want to mount /dev/sdb1 as /home folder, right?

---

### Post by wog on 2008-05-26
> **hyper_ch said:**
> (1) when posting some code or output, use [noparse]```

```[/noparse] tags around it. It makes it much easier to read

(2) I'm not sure if I understand your problem right. You want to mount /dev/sdb1 as /home folder, right?

Yes, I'd like to mount /dev/sdb1 as home.

---

### Post by hyper_ch on 2008-05-26
Add this to your fstab:

```

/dev/sdb1 /home ext3 nodev,nosuid 0 2

```

and then run

```

sudo mount -a

```

---

### Post by wog on 2008-05-28
Do I need to do anything to the other entry in my fstab that lists another directory as home?

---

