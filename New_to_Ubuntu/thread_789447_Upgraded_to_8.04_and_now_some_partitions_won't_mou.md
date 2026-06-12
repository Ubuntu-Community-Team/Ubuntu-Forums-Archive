---
title: "Upgraded to 8.04 and now some partitions won't mount"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by marmaladejackson on 2008-05-10
Hi All,

Just did the upgrade last night.  Upon booting, my icons for the partitions of my secondary SATA drive (I mounted them at /media/SATA1 and /media/SATA5) and my old IDE (/media/ide) were missing.  Under "places" in the task bar, the partitions are shown and right-clicking causes them to mount at a default position (/media/disk).  I popped open the partition editor and noticed that the locations of the drives under /dev had changed slightly.  So i changed my fstab file to reflect the new changes:

```
/dev/sda /media/ide auto defaults 0 1
/dev/sdb1 /media/SATA1 auto defaults 0 1
/dev/sdb5 /media/SATA5 auto defaults 0 1
```
and rebooted.  Got a bunch of errors on the reboot and it dumped me off at the root prompt.  So I pico-ed the fstab and commented the above lines and booted again.  No problems, but the drives remain unmounted.  

So I started playing around with the Properties window on one of the drives and on the volume tab under settings, it has a blank for "Mount Point".  I put /media/ide in there, unmounted the drive and attemped to remount and got a  "cannot mount volume" error:

```
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

and I can't get to the properties tab to undo the /media/ide.  Any ideas on how to get these to mount on boot to their old mount points so that my playlists know where to find the songs?

Thanks!
Brian

---

### Post by Oldsoldier2003 on 2008-05-10
> **marmaladejackson said:**
> Hi All,

Just did the upgrade last night.  Upon booting, my icons for the partitions of my secondary SATA drive (I mounted them at /media/SATA1 and /media/SATA5) and my old IDE (/media/ide) were missing.  Under "places" in the task bar, the partitions are shown and right-clicking causes them to mount at a default position (/media/disk).  I popped open the partition editor and noticed that the locations of the drives under /dev had changed slightly.  So i changed my fstab file to reflect the new changes:

```
/dev/sda /media/ide auto defaults 0 1
/dev/sdb1 /media/SATA1 auto defaults 0 1
/dev/sdb5 /media/SATA5 auto defaults 0 1
```
and rebooted.  Got a bunch of errors on the reboot and it dumped me off at the root prompt.  So I pico-ed the fstab and commented the above lines and booted again.  No problems, but the drives remain unmounted.  

So I started playing around with the Properties window on one of the drives and on the volume tab under settings, it has a blank for "Mount Point".  I put /media/ide in there, unmounted the drive and attemped to remount and got a  "cannot mount volume" error:

```
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

and I can't get to the properties tab to undo the /media/ide.  Any ideas on how to get these to mount on boot to their old mount points so that my playlists know where to find the songs?

Thanks!
Brian

media is where things automount
try making a mount point in /mnt and then mounting the partitions there:
```

sudo mount /device /mnt/mountpoint
```

---

### Post by marmaladejackson on 2008-05-10
OK, I think I may have discovered part of the problem... every time I reboot, the drives change their /dev location.  Has anybody else encountered this?  I thought their /dev position was determined by where they were physically wired into the mother board.  What gives?

When I say they change /dev location, I mean that the drive currently showing as /dev/sdc on the last boot is now found at dev/sda.  When I was following Oldsoldier's advice, I took another look at my fstab file and thought I had mad a bunch of typos, but I noticed on this boot that they are jumping around.

Thanks.

---

