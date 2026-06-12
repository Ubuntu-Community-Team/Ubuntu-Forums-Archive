---
title: "burn dvd iso to usb?"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by jrhayden82 on 2013-11-13
Am running Ubuntu 13.10 and trying to burn a dvd iso (opensuse dvd iso) to a usb. However have not been able to. Maybe I am typing in something wrong?

sudo dmesg | tail -20
[sudo] password for joe: 
[ 5411.551184] usb 2-1.1: Manufacturer: UFD
[ 5411.551188] usb 2-1.1: SerialNumber: AAS2CST024W7WN08
[ 5411.551591] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[ 5411.551700] scsi6 : usb-storage 2-1.1:1.0
[ 5412.908976] scsi 6:0:0:0: Direct-Access     UFD      USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[ 5412.909432] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 5413.408303] sd 6:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 5413.409665] sd 6:0:0:0: [sdb] Write Protect is off
[ 5413.409673] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 5413.411062] sd 6:0:0:0: [sdb] No Caching mode page found
[ 5413.411072] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5413.416910] sd 6:0:0:0: [sdb] No Caching mode page found
[ 5413.416919] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5413.418047]  sdb: sdb1
[ 5413.422545] sd 6:0:0:0: [sdb] No Caching mode page found
[ 5413.422553] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5413.422560] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 5413.652017] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 5413.743444] systemd-hostnamed[3696]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 5941.394802] Valid eCryptfs headers not found in file header region or xattr region, inode 402675
joe@sovereign:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
joe@sovereign:~$ sudo dd if=/home/joe/opensuse-12.3.iso of=/dev/sdb1 bs=1M
dd: opening ‘/home/joe/opensuse-12.3.iso’: Input/output error

---

### Post by sudodus on 2013-11-13
Welcome to the Ubuntu Forums :-)

I think the problem is that you try to flash the iso file to the first partition of the USB drive. Instead you should flash it to the drive itself

```
/dev/sdb (not /dev/sdb1)
```

The procedure with dd is risky, so I recommend that you use the shell-script ***mkusb*** to reduce the risk and increase the chance to succeed. See this link

[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by thesleash on 2013-11-15
there's an app called unetbootin you could use

---

### Post by couder on 2013-11-17
Hi, you can use the Startup Disc Creator to make bootable usb from .iso file.

---

### Post by heir4c on 2013-11-17
Or use multisystem: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
I have a 32GB USB with 20+ Linux distro's on it.

---

