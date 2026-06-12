---
title: "[SOLVED] External drive cannot be mounted?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by germanix on 2008-10-11
I have connected an external drive, currently formatted in nfts. When I switch it on I get an error message "cannot mount drive"
here the output from syslog:

jac@jac-desktop:~$ tail /var/log/syslog
Oct 11 15:51:37 jac-desktop kernel: [20306.095658] sd 7:0:0:0: [sdf] Mode Sense: 23 00 00 00
Oct 11 15:51:37 jac-desktop kernel: [20306.095660] sd 7:0:0:0: [sdf] Assuming drive cache: write through
Oct 11 15:51:37 jac-desktop kernel: [20306.095663]  sdf: sdf1
Oct 11 15:51:37 jac-desktop kernel: [20306.110587] sd 7:0:0:0: [sdf] Attached SCSI disk
Oct 11 15:51:37 jac-desktop kernel: [20306.110630] sd 7:0:0:0: Attached scsi generic sg6 type 0
Oct 11 15:51:37 jac-desktop NetworkManager: <debug> [1223733097.669299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_59b_375_00303C0540123320_if0_scsi_host'). 
Oct 11 15:51:37 jac-desktop NetworkManager: <debug> [1223733097.673745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_59b_375_00303C0540123320_if0_scsi_host_scsi_device_lun0'). 
Oct 11 15:51:37 jac-desktop NetworkManager: <debug> [1223733097.675728] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_59b_375_00303C0540123320_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 11 15:51:37 jac-desktop NetworkManager: <debug> [1223733097.767538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Iomega_HDD_00303C0540123320_0_0'). 
Oct 11 15:51:37 jac-desktop NetworkManager: <debug> [1223733097.900813] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_C8442D67442D5988'). 
jac@jac-desktop:~$ sudo blkid
[sudo] password for jac: 
/dev/sda1: UUID="4c11f8a6-a67b-45e4-85bb-1903e393c7a8" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="92d4d112-6b2d-43ab-beb8-cb8bcddd5a2d" 
/dev/sdf1: UUID="C8442D67442D5988" LABEL="Volume" TYPE="ntfs" 
jac@jac-desktop:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found

jac@jac-desktop:~$ sudo fsck /dev/sdf1
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdf1
jac@jac-desktop:~$ 


Can anyone help please?

---

### Post by superprash2003 on 2008-10-11
have you used this on a windows machine before without safely removing it?

---

### Post by germanix on 2008-10-11
Yes, I did have it connected to my pc when I was using Vista. Since then I deleted Vista and installed Ubuntu. This is my first try to use this drive again. I cannot say whether I had removed it un-safely or not.

---

### Post by drs305 on 2008-10-11
Fsck is meant to be used on linux systems (not ntfs). If you don't have the ability to remount it in windows and then safely shut it down there, the next option is to try to repair it with ntfsfix.

```
sudo apt-get install ntfsprogs
```

```
sudo ntfsfix /dev/sdf1
```

If you don't already have any entry in fstab, the easiest way to set this up is to install ntfs-config (if it isn't already installed) and then run it:
```

sudo apt-get install ntfs-config

```

System Tools, NTFS Configuration Tool

---

### Post by germanix on 2008-10-11
This worked perfectly, thank you very much. I now would like to make a back-up of my "home" file, to this drive. It will be very helpfull if you could advise my how to do this please.

All ok. Used "sbackup" which did the job.

---

