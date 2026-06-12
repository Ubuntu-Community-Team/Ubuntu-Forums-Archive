---
title: "[SOLVED] adding a usb external drive"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-20
I have added an external 80 gig usb 2.0 drive to the 'puter. It shows up in /media named:

usb

My /etc/fstab shows no sign of this device:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

How can I make the device "visible" to the computer?

---

### Post by imsully on 2008-10-20
Can you post the contents of your /etc/mtab file while the drive is connected?

Thanks!

---

### Post by Mark_in_Hollywood on 2008-10-20
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mark/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mark 0 0
/dev/sdb1 /media/UDISK\04028X vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdc1 /media/PRESTON vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

---

### Post by imsully on 2008-10-20
Are either of the items in the last two lines your drive?

---

### Post by Mark_in_Hollywood on 2008-10-20
No, they are thumb drives, 256 meg and 1 gig.

---

### Post by drowner on 2008-10-20
It won't show up in your fstab. That's for permanently mounted disks.

When you say its not visible, how can you see it in /media?

---

### Post by Mark_in_Hollywood on 2008-10-21
> **drowner said:**
> It won't show up in your fstab. That's for permanently mounted disks.

When you say its not visible, how can you see it in /media?

/media shows a number of devices, cdrom, floppy (not called that, I think it's floppy), both usb memory sticks (pen or thumb drives) and something named:

usb

which is "new" that is, it's there only since I plugged the external drive into a usb port. Meanwhile, I've deleted that icon, turned the drive off and on and it's still not working.

---

### Post by Duck2006 on 2008-10-21
This may help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Mark_in_Hollywood on 2008-10-21
Since the drive was not being found in lsusb, I set the jumper from master to cable-select. On power up, the icon appeared /home/mark/Desktop and while the drive still has a "lost+found" folder in it, it progress and I'm closing this thread.

Thanks, community.

---

