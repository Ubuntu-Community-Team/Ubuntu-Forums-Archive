---
title: "lsusb"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by msidhard on 2013-03-08
When i type "lsusb" in terminal it shows:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0421:04bc Nokia Mobile Phones
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Now i want to know in what name Nokia Mobile Phone is registered in /dev,   example:/dev/ttyusb0

Thanks in advance

---

### Post by siddharth007 on 2013-03-08
There are many ways to find it out.

1. On the terminal/console you can do '**dmesg'**.This would give you something like this

```
[  271.987069] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[  272.139009] Initializing USB Mass Storage driver...
[  272.139133] scsi6 : usb-storage 2-1.5:1.0
[  272.139210] usbcore: registered new interface driver usb-storage
[  272.139212] USB Mass Storage support registered.
[  272.167493] usbcore: registered new interface driver uas
[  273.138540] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
[  273.139709] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  273.142797] sd 6:0:0:0: [sdb] 15645120 512-byte logical blocks: (8.01 GB/7.45 GiB)
[  273.143340] sd 6:0:0:0: [sdb] Write Protect is off
[  273.143347] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  273.143948] sd 6:0:0:0: [sdb] No Caching mode page present
[  273.143954] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  273.147183] sd 6:0:0:0: [sdb] No Caching mode page present
[  273.147189] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  273.148697]  **sdb: sdb1**
[  273.150804] sd 6:0:0:0: [sdb] No Caching mode page present
[  273.150811] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  273.150816] sd 6:0:0:0: [sdb] Attached SCSI removable disk


```

This indicates that the device has ben registered as /dev/sdb1 

2. Type the command **mount **on the terminal.This will list all the mounted devices on the system

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fortunepay/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fortunepay)
[B]/dev/sdb1 on /media/1815-94AC type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
[/B]
```

3. Cat /var/log/messages and you would find something like this

```
Mar  8 12:41:49 fortunepay-desktop mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5" 
Mar  8 12:41:49 fortunepay-desktop mtp-probe: bus: 2, device: 3 was not an MTP device 
Mar  8 12:41:49 fortunepay-desktop kernel: [  272.139009] Initializing USB Mass Storage driver...
Mar  8 12:41:49 fortunepay-desktop kernel: [  272.139133] scsi6 : usb-storage 2-1.5:1.0
Mar  8 12:41:49 fortunepay-desktop kernel: [  272.139210] usbcore: registered new interface driver usb-storage
Mar  8 12:41:49 fortunepay-desktop kernel: [  272.139212] USB Mass Storage support registered.
Mar  8 12:41:49 fortunepay-desktop kernel: [  272.167493] usbcore: registered new interface driver uas
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.138540] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 8GB    8.07 PQ: 0 ANSI: 2
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.139709] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.142797] sd 6:0:0:0: [sdb] 15645120 512-byte logical blocks: (8.01 GB/7.45 GiB)
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.143340] sd 6:0:0:0: [sdb] Write Protect is off
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.148697]  sdb: sdb1
Mar  8 12:41:50 fortunepay-desktop kernel: [  273.150816] sd 6:0:0:0: [sdb] Attached SCSI removable disk


```

I hope this helps you out.

---

