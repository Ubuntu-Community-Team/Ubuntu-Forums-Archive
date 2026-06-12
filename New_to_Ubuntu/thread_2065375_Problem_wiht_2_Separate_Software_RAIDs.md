---
title: "Problem wiht 2 Separate Software RAIDs"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by garyhook on 2012-10-01
I have a problem with a 12.04 LTS Alternate install.  I have 5 disks in my server box.  2 - 500 GB and 3 - 2TB.  I have installed the 12.04 LTS on the 2 - 500's using the RAID-LVM installation method.  All installs well and is functional just fine.  The Volume groups install along with the Logical Volumes.

When i create the RAID5 from the 3 - 2TB disks everything goes bad.  The /dev/md1 is created just fine.  I then pvcreate /dev/md1...that's fine.  I vgcreate the volume group and lv create one large logical volume.

I can format the /dev/mapper/vgname-lvname just fine.  All works well until i reboot!

When i reboot the system doesn't reboot.  I've changed the /etc/defaults/grub.cfg file to list the grub menu...it comes up but when the machine reboots it just displays a blank screen....nothing...

the only way i can reboot is if i physically disconnect the 2 TB hard drives.

Any help would be appreciated!

---

