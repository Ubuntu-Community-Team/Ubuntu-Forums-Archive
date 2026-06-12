---
title: "[SOLVED] Spoilt FSTAB Problem"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by moeness86 on 2008-05-22
Hello ppl,

I have to admit that it was stupid of me to not backup FSTAB before fiddling with it ignorantly

Anyhoo there goes my problem:

When I purchased this Laptop ( Lenovo 3000 N200 ) I installed XP and Gutsy 64-bit, things went fine and then I had to reinstall XP, so i did, fixed grub with superGRUB disk, and i got my dual booting back alright with one bug: it won't mount the Windows partition automatically, although i could see it in "Computer", double click it, enter password and it becomes mounted.

I wanted to overcome this, so i first tried the mount manual "mount 8 man" and got to know that the solution might be in fstab. What I have now is that it won't mount automatically AND it wont mount from Computer either ..
I get this Error Dialog: "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

 so here is my fstab and i wish someone can help me with this. 
Another note : the field UUID of that partition in fstab is different from the one i see in the volume tab of that partition's properties. I dont know if it matters but i thought i better list all the info I know of.

Thank you very much in advance.

---

### Post by drs305 on 2008-05-22
Please post the results of 
```
sudo blkid
sudo fdisk -l
```

Also, are you using ntfs-3g?

---

### Post by moeness86 on 2008-05-22
> :/$ sudo blkid
/dev/sda1: UUID="D05CD5F65CD5D776" TYPE="ntfs" LABEL="WinXP" 
/dev/sda3: UUID="D880768580766A40" LABEL="Deeeeeeeee" TYPE="ntfs" 
/dev/sda4: TYPE="swap" UUID="3ea217b8-5edd-43db-8fe3-2262b4568b37" 
/dev/sda5: UUID="c30d86df-26af-4ef1-a05c-5731171d6c26" SEC_TYPE="ext2" TYPE="ext3" 

:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7648    30716280    f  W95 Ext'd (LBA)
/dev/sda3            7649       14457    54693292+   7  HPFS/NTFS
/dev/sda4           14458       14593     1092420   82  Linux swap / Solaris
/dev/sda5            3825        7648    30716248+  83  Linux


If ntfs-3g means Version 3 then yes.

---

### Post by moeness86 on 2008-05-22
**.**

---

### Post by drs305 on 2008-05-22
Your sda1 partition uuid has changed. It is now: D05CD5F65CD5D776 and is ntfs . ntfs-3g is pretty standard now. I believe it is the default for hardy but you can check in synaptic to make sure it's installed.

So that line should read:
```

UUID=D05CD5F65CD5D776  /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
```

I'm still looking at the rest of the line and the rest...

---

### Post by drs305 on 2008-05-22
Please post 
```
mount
```

I just want to confirm a couple of things.

Oh yeah, once you get it working:
```
sudo cp /etc/fstab /etc/fstab-`date +%F`
```

;-)

---

### Post by moeness86 on 2008-05-22
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by drs305 on 2008-05-22
I forgot you couldn't mount windows.

```

# /dev/sda1
UUID=D05CD5F65CD5D776  /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```

You might be able to put ntfs-3g in the line.
It will be mounted on /media/sda1. If you want it somewhere else, make the mount point, make yourself the owner, and then change the fstab entry.

---

### Post by moeness86 on 2008-05-22
IT WORKS :D
you're the man :D

now, i really don't know how u could reach this info, but is there a manual that is beginner friendly that can teach me how to diagnose stuff like this ?

---

### Post by drs305 on 2008-05-22
> **moeness86 said:**
> IT WORKS :D
you're the man :D

now, i really don't know how u could reach this info, but is there a manual that is beginner friendly that can teach me how to diagnose stuff like this ?

Well, I make a lot of mistakes but I take a lot of notes!  When my notes don't have the answer, I have a few good bookmarks. One of the ones I use for fstab is [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) but it's a little old. 

Finally, google is your friend. You can search the entire internet or just this forum. Generally you would want to include 'hardy' to get results that are recent. On this forum, adding 'SOLVED' also helps. Be as specific as you can, even copying error messages at least in part if that's what the problem is.


[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://www.stchman.com/](http://www.stchman.com/)
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

