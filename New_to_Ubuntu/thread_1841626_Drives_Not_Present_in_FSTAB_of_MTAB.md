---
title: "Drives Not Present in FSTAB of MTAB"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by benzodiaz on 2011-09-09
Hi, and thanks for reading,

   When I try executing,

```
mount /dev/sda2
```

   I receive the error,

"mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab"

   I am running on crunch bang; fresh install.

   It's installed on a partition of one of my drives: the linux partitions are all I can see in the *media* folder.

For blkid, this is the return

```
 sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="14A271C9A271AFBA" TYPE="ntfs" 
/dev/sda2: LABEL="OS7" UUID="DCA2DE22A2DE0146" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="06FCE3BEFCE3A661" TYPE="ntfs" 
/dev/sdb1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="2EDA89C6DA898AB3" TYPE="ntfs" 
/dev/sdb2: LABEL="STORAGE" UUID="70B41FDFB41FA71E" TYPE="ntfs" 
/dev/mmcblk0p1: UUID="FC30-3DA9" TYPE="vfat" 
/dev/sda5: UUID="c01f2e2e-ebd8-4211-aa76-c31746ee9b17" TYPE="ext4" 
/dev/sda6: UUID="a1725cca-8af7-466b-a942-9f83ca02c8a5" TYPE="swap" 
/dev/sdc1: LABEL="FANTOM" UUID="10D8-132E" TYPE="vfat" 

```

I would like to mount the following drives, which are not present in fstab or mtab:

   sda2, sda3, and sdb2

The only drives in fstab and mtab are the two linux partitions: sda5(ext4) and sda6(swap).

Any ideas?  For further info., please let me know!

Thanks in advance!
Have a great day!

-Jeff

---

### Post by Cheesemill on 2011-09-09
To mount a partition that isn't present in /etc/fstab you have to specify where you wish to mount it; for example.

```
mkdir /mount/OS7
sudo mount /dev/sda2 /mount/OS7
```

Also you're probably better off asking in the Crunchbang or Debian forums, Crunchbang has nothing to do with Ubuntu nowadays.

---

### Post by TeoBigusGeekus on 2011-09-09
I think you get this message because you don't specify a mount point in your command.
Without a mount point, your system tries to find one in fstab or mtab, thus failing miserably.
Create a folder in /media
```
sudo mkdir /media/mountpoint
```
become its owner
```
sudo chown -R yourusername /media/mountpoint
```
so that you have recursive rights in it and then try to mount your partition
```
sudo mount /dev/sda2 /media/mountpoint
```

EDIT: I'm getting old and slow.

---

### Post by Wim Sturkenboom on 2011-09-09
I don't think /media is really intended for manually mounting. /mnt might be better choice

---

### Post by TeoBigusGeekus on 2011-09-10
> **Wim Sturkenboom said:**
> I don't think /media is really intended for manually mounting. /mnt might be better choice

/mnt was the preferred mount point in the past.
Nowadays it's all /media.

---

### Post by saltmarshlamb on 2011-09-10
If you don't want your fstab mounts to show on the desktop use /mnt then your plugged in devices will still show there.

ALternatively you can probably still tunr it off in gconf-editor

---

### Post by Gone fishing on 2011-09-10
> /mnt was the preferred mount point in the past.
Nowadays it's all /media. 

+1

Plus if you mount in /media it will create a desktop icon that can be handy.

---

### Post by Wim Sturkenboom on 2011-09-10
Just my thought
/media is for dynamic stuff (udev like)
/mnt is for more permanent stuff

If /media was the way for everything, /mnt would no longer exist. And /media would have obsoleted itself before even existing as /mnt could already do the job.

---

### Post by benzodiaz on 2011-09-10
Hi,

   Sorry about posting that in the wrong directory.

   Thanks a lot though.  Everything worked fine.

   I just made a new directory in the media folder, then took ownership, then mounted it like I was trying to and it worked perfectly.

   Thanks again to everyone, solid answers all around.

Cheers,

Jeff

---

