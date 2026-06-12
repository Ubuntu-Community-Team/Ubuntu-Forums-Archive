---
title: "using UUID for fstab"
date: 2018-03-30
forum: New to Ubuntu
---

### Post by w4qed on 2018-03-30
Hello all,

 I have been mounting my two Hard Drives I use for multimedia/Videos (/media) and some sort of backup (/mnt). My problem is that sometimes it uses the sawps the mounting of the Hard Drive's.
Here is my /etc/fstab:
```

proc            /proc           proc    defaults          0       0
/dev/mmcblk0p2  /               ext4    defaults,noatime  0       1
/dev/mmcblk0p1  /boot/          vfat    defaults          0       2
UUID=ad0bf458-6245-48fb-ae93-77d854a0e074 /mnt           auto nosuid,nodev,nofail,x-gvfs-show 0 0
UUID=7f456dc7-b09a-4ce1-88fc-59a6d6a0a2c5 /media         auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

and here is blkid:

```
/dev/sda1: UUID="73c60a19-a0a6-4f7d-bfaf-c2c4cab6da56" TYPE="ext4" PARTUUID="9a107aa0-01"
/dev/sda2: UUID="ad0bf458-6245-48fb-ae93-77d854a0e074" TYPE="ext4" PARTUUID="9a107aa0-02"
/dev/sdb1: UUID="3d78f0bc-f9bd-4fd3-8992-491f92e8e507" TYPE="ext4" PARTUUID="c9869e02-605b-44e6-bbc4-d9a55aadcc57"
/dev/sdb2: LABEL="Data" UUID="7f456dc7-b09a-4ce1-88fc-59a6d6a0a2c5" TYPE="ext4" PARTUUID="8ea82888-fb34-4bf0-85d1-3f256c6cbed2"
```



I am believe I am trying to sudo mount /dev/sda2 to /mnt
and also sudo mount /dev/sdb2 /media

 Once in a while on reboot it outs /dev/sda2 on /media and /dev/sdb2 on /mnt. Any ideas? Perhaps I need to add the PARTUUID but I'm not sure.

 I have searched the Forum but I could have missed the answer to this poblem.

Thank you,
Ben

---

### Post by firehorse19662 on 2018-03-30
sorry for english
your machine mounts the swap is this right

please post your fstab

---

### Post by ajgreeny on 2018-03-30
You should **always use UUIDs in fstab** as it is possible for device names such as your /dev/mmcblk0p1 and /dev/mmcblk0p2 to interchange depending on how fast each device is detected at power-on, so in your situation I would edit fstab and replace those two dev names with the correct UUIDs.

I will try to help you further with this if I can when on a larger screen machine that I am at present, as I am a little confused seeing it now about which partition is which.
I also assume you are using 17.10 which does not create, nor need a separate swap partition but uses a swapfile instead, though that should be shown in your fstab but without a mountpoint.

---

### Post by ajgreeny on 2018-03-30
I have now looked at your detailed partition info a bit closer and am even more confused.

Your fstab file shows a partition which is set to mount at boot which is formatted as vfat,
```
/dev/mmcblk0p1  /boot/          vfat    defaults          0       2
```
but that does not show in the blkid output where nothing with a vfat format is listed; all are ext4.

I will keep looking back at this thread to see if anyone el;se can make head or tail of what is going on but for now I shall have to admit defeat.

---

### Post by SeijiSensei on 2018-03-31
Is there a reason you aren't entering "ext4" in the filesystem type field instead of "auto?" Why not just use "defaults" in the options field?

---

### Post by Morbius1 on 2018-03-31
> **SeijiSensei said:**
> Is there a reason you aren't entering "ext4" in the filesystem type field instead of "auto?" Why not just use "defaults" in the options field?
Because he's using Disks. It's just a guess on my part but it's the only utility that adds x-gvfs-show in response to a silly question ( "show in user interface" ) and doesn't bother to specify the filesystem leaving it up to the system to figure it out with "auto".

---

