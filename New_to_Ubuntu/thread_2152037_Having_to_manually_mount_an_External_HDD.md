---
title: "Having to manually mount an External HDD"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-06-06
Hello all

When I plug in my Seagate External HDD Linux tells me "you can't mount /dev/sdg1 only root can do that." So I open xterm and type in:
```

sudo mount -t ext4 /dev/sdg1 /media/Seagate

```
and it mounts fine. Similarly, when I want to remove the drive I type:
```

glenn@design:~$ sudo umount /dev/sdg1

```
Although it takes 2 or three tries in 'Computer' to "safely remove drive" before the drive powers down and the power light goes out.

Is there any way I can get around having to manually mount the drive when I plug it in? Its already in fstab:
```

# Seagate External HDD
UUID=d4964716-bc5b-43b2-bfa3-379daf0a068d /media/Seagate ext4 noatime,relatime 0 0

```
 Glenn.

---

### Post by bab1 on 2013-06-06
What happens if you comment out the line for this partition in fstab.  It should automount without you needing to add the line to fstab.  As far as needing root to mount the drive; you can add *user* as an option and the regular users will be able to mount it -- but that's not automount now is it?

---

### Post by Rebelli0us on 2013-06-06
It should mount if you double-click it in file manger. Likewise you should be able to right-click and select "unmount".  Perhaps there's something wrong in the fstab line, I'd comment it out temporarily, reboot and see what happens.

---

### Post by ajgreeny on 2013-06-06
For ease of use, particularly if you want to be able to write to the drive, I suggest you make sure the partition on it is labeled with some descriptive name, eg, **Seagate** with command ```
sudo tune2fs -L Seagate /dev/sdg1
```assuming sdg1 is still the device name when attached.   This means that when attached by USB the drive will always automount at /media/**Seagate**.  Now with the disk attached and mounted run ```
sudo chown glenn:glenn /media/Seagate
```That should mean you can now write to the partition on the disk as user without any difficulties.

---

### Post by bab1 on 2013-06-06
> **Rebelli0us said:**
> It should mount if you double-click it in file manger. Likewise you should be able to right-click and select "unmount".  Perhaps there's something wrong in the fstab line, I'd comment it out temporarily, reboot and see what happens.

If the partition is mounted via the fstab file, by default, only root can mount and dismount it.  On the other hand USB connected media wil be auto mounted unless the the partition (drive) is defined in fstab.  You can use the option (in the 4th field) of *user* to allow mortal users to mount and dismount  fstab defined mounts.  See the fstab man page```
 user   allow a user to mount
```

---

### Post by VMC on 2013-06-06
> **bab1 said:**
> What happens if you comment out the line for this partition in fstab.  It should automount without you needing to add the line to fstab.  As far as needing root to mount the drive; you can add *user* as an option and the regular users will be able to mount it -- but that's not automount now is it?
Exactly. No fstab entry, and any usb drive is mounted automatically when inserted.

---

