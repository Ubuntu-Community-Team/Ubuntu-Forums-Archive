---
title: "automatic mount partitions at startup"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-01-16
I have a NTSC partition that I will share with the "legacy OS" if I should use it (still getting habit of linux, but I'm more and more excited by all the power and control I'm getting using it);

I noticed that that partition appears under "Places" as '164 Gb partition', but it isn't mounted at startup. I have to open it to be mounted. Then (it appears to me) it remains mounted all the session.

I'd really like to change this behaviour and keep it mounted always, so that I don't have to open it every time I want to use it.

That's beacause I have a bunch of tasks which perform savings in that partition and if it's not mounted, they can't find their directories to save.

Thanks for help as always.

---

### Post by Miljet on 2012-01-16
You will need to create a mount point and then add an entry in the /etc/fstab file. Here is a link to one guide. [http://embeddedlinuz.wordpress.com/2011/11/03/how-to-mount-partition-automatically-at-startup-in-ubuntu/](http://embeddedlinuz.wordpress.com/2011/11/03/how-to-mount-partition-automatically-at-startup-in-ubuntu/)
You can also open a terminal and type "man fstab" (without the quotes) to learn more about the fstab file.

---

### Post by Mark Phelps on 2012-01-16
What is an "NTSC" partition?

If you mean NTFS, as long as it's only a data partition -- meaning no programs and no OS on that partition, you'll probably be OK.

But, if it's a data partition, as long as it's for Windows XP, again, you'll probably be OK.

But, if it's an OS partition for Vista, then do NOT mount it read/write, especially at startup.  Vista, like Win7, is really picky about its OS filesystem and easily breaks when tampered with from  "outside" (as in writing to it from a Linux OS).

---

### Post by il_maniscalco on 2012-01-16
thank you guys

---

### Post by il_maniscalco on 2012-01-17
sorry, perhaps it was not what I meant doing.

ok, now the system makes the following:

I boot, i see top-left Application **Places**; if I click Places, there's an item: **164Gb Filesystem**. I click ther and enter the ntfs partition.

That's mounted under **/media**.

The fact is that until I don't click there, under /media (after booting) nothing is mounted, and so, if there's an application (notably my thunderbird) that tries to access to that partition, it can't.

in order to not to change everything, I'd like to automatically mount the **same** partition using the same name, in the same location (/media). basically, to avoid to click on the **164Gb Filesystem** under **Places**. But keep the partition there.
in other words, to automatically mount it under /media.

can you help me for this?

---

### Post by Double.J on 2012-01-17
> **il_maniscalco said:**
> sorry, perhaps it was not what I meant doing.

ok, now the system makes the following:

I boot, i see top-left Application **Places**; if I click Places, there's an item: **164Gb Filesystem**. I click ther and enter the ntfs partition.

That's mounted under **/media**.

The fact is that until I don't click there, under /media (after booting) nothing is mounted, and so, if there's an application (notably my thunderbird) that tries to access to that partition, it can't.

in order to not to change everything, I'd like to automatically mount the **same** partition using the same name, in the same location (/media). basically, to avoid to click on the **164Gb Filesystem** under **Places**. But keep the partition there.
in other words, to automatically mount it under /media.

can you help me for this?

Hi there! as the others have said, you set this up in the filesystems tabel at /etc/fstab. if you navigate there with nautilus, then open with gedit, could you post everything you have in that file? as well as the output of 
```

sudo fdisk -l

```

put the replys in quote marks like ^^^ by hilighting and clicking the # button at the top of the reply window :)

---

### Post by il_maniscalco on 2012-01-17
> **gnu/mirow said:**
> Hi there! as the others have said, you set this up in the filesystems tabel at /etc/fstab. if you navigate there with nautilus, then open with gedit, could you post everything you have in that file? as well as the output of 
```

sudo fdisk -l

```

put the replys in quote marks like ^^^ by hilighting and clicking the # button at the top of the reply window :)

hey thanks 4 replying I'm giving the infos:

fstab file:

```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=69b135a0-c7d5-4b79-a8f0-40bcf91f0f75 /               ext4    errors=remoun$
# swap was on /dev/sda8 during installation
UUID=1c32a15d-cfe2-4306-8662-97ac05d54936 none            swap    sw           $


```

and the fdisk -l:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33fdae9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024   100663289    36699133    7  HPFS/NTFS/exFAT
/dev/sda4       100663294   488396799   193866753    5  Extended
/dev/sda5       163557376   167751679     2097152   82  Linux swap / Solaris
/dev/sda6       167753728   488396799   160321536    7  HPFS/NTFS/exFAT
/dev/sda7       100663296   159639551    29488128   83  Linux
/dev/sda8       159641600   163540991     1949696   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Double.J on 2012-01-17
Hi there, You don't have an entry for it in the fstab, so to mount at boot.. best add one!

try using the following - just paste into your fstab under the other entries and save!
```

# NTFS Shared partition
/dev/sda6  /media  ntfs-3g rw,auto,user,exec,sync 0 0

```

this is assuming that /dev/sda6 is what you want mounted? if you want the windows primary, make an entry for /dev/sda2 as well. The only thing I'd say to change is where it's mounted - Ubuntu uses /media for mounting removable devices. I'd advice making a new directory to mount it at, for example:
```

sudo mkdir /data or /home/username/data

```
and mounting at this directory by replacing /media with "/data" for example? you'll have to restart to take effect.

---

### Post by il_maniscalco on 2012-01-17
great, I'll do it asap.
and I'll have to change my profiles on thunderbird, hope it won't corrupt nothing.

---

