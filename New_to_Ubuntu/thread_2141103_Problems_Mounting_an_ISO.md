---
title: "Problems Mounting an ISO"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by swapfox on 2013-05-01
Hello,

I'm having some trouble mounting an .iso file. The iso contains an installation script I need for another program. I've correctly mounted this iso and installed the program two times before without a hitch (once with Ubuntu 10.04 64bit and another time with Kubuntu 12.04 32bit). I'm currently trying to mount the file on my new installation of Kubuntu 12.04 64bit. When I give the command: mount file.iso /media/iso -t iso9660 -o loop I get the error message:
>  mount: wrong fs type, bad option, bad superblock on /dev/loop1,       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I run dmesg | tail I get:
> [   22.907676] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   22.908398] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.908946] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.909280] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.208460] init: plymouth-stop pre-start process (1360) terminated with status 1
[   23.813958] r8169 0000:02:00.0: eth0: link up
[   23.814334] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.057140] eth0: no IPv6 routers present
[ 3561.392137] isofs_fill_super: bread failed, dev=loop1, iso_blknum=16, block=32
[ 4719.354798] isofs_fill_super: bread failed, dev=loop1, iso_blknum=16, block=32


I'm guessing that the fail messages have something to do with whats wrong? I've googled this problem and seen a few solutions that don't seem to be applicable. 

I don't think there's a problem with the iso, but I checked it anyways:
> matt@ubuntu:~/Downloads$ md5sum IRAF_Ubuntu.iso 
882f6f077f1101658c1288d627964f16  IRAF_Ubuntu.iso



If someone could help me with this I'd be very appreciative. 

Thanks!

---

### Post by zero2xiii on 2013-05-02
Hay,

I think your command is not syntaxed correctly:
>  mount file.iso /media/iso -t iso9660 -o loop
Should be
 ```
mount -o loop -t iso9660 file.iso /media/iso 
```

Also I THINK loop mounts require sudo, I can not confirm this because my computer has very custom sudo rights.

Cheers

---

