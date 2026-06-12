---
title: "Boot system without drives which are registered in the fstab"
date: 2018-09-27
forum: New to Ubuntu
---

### Post by sed_faster on 2018-09-27
Hello folks,

I am using Raspbian Stretch Lite on my Raspberry Pi 3 ([https://www.raspberrypi.org/downloads/raspbian/](https://www.raspberrypi.org/downloads/raspbian/)). Through fstab I setup a disk to connect during boot (pen drive). I remove this pen drive and I reboot the system, but the system didn't start up well. The process boot freeze on this screen: [https://postimg.cc/cK6cCQDs](https://postimg.cc/cK6cCQDs) and this [https://postimg.cc/v11WbGBT](https://postimg.cc/v11WbGBT)

I try connect again the pen drive and reboot the system, but I can't advance this screen. What can I do?

---

### Post by oldfred on 2018-09-27
Generally best not to have removable devices in fstab.
You may have to edit fstab & comment out line with external drive. 

But there are several parameters that may help. If you want to keep entry in fstab and not always manually mount.

       Systemd mount issues:
LABEL="test"  /mnt/test  ext4  defaults,nofail,x-systemd.device-timeout=4  0  2
if you have not set its mount as "nofail" in the mount options in fstab, systemd blocks boot process after a minute and a half of timeout.
If you did set the "nofail" it will just complain that it can't mount it. 
    
For details see also:
man mount

---

### Post by sed_faster on 2018-09-28
Thanks to your reply. But I can't get past these screens. How can I edit fstab if I can't access the system?

Thanks

---

### Post by oldfred on 2018-09-28
Can you plug MMC card into your PC?

---

### Post by sed_faster on 2018-10-06
> **oldfred said:**
> Can you plug MMC card into your PC?

My "PC" it is a rapsberry PI. I use this hardware to study linux. I know which I can configure the fstab to don't mount drive if the drive it isn't connect on board. But in this setup I am simulate the situation which I didn't configured the fstab in this parameter and the drive it is disconnected. 

Therefore how can I handle this situation? If this environment will be a normal pc I should connect a pen drive with image ubuntu and try changed fstab? This is a correctly way? But since I'm with a raspberry pi I should try connect SDCard in another pc, change the fstab file and try boot the system in raspberry pi again?

Thanks

---

### Post by oldfred on 2018-10-06
I would think you could edit fstab from another PC, but have not played with my Raspberry Pi that much, yet.

---

### Post by sed_faster on 2018-10-06
Yes, I can solved the problem. I simply plug the SD card on my desktop and appear two partition. one to boot and another to the system. I accessed the system and edit fstab, through user root. I commented the line about mount my external drive and I came back start up my raspberry pi. And works :)

To I don't receive again messages error about external drives in my boot:
```

proc            /proc           proc    defaults          0       0
PARTUUID=a42d4sdfd-01  /boot           vfat    defaults          0       2
PARTUUID=a42d4sdfd-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that

UUID=CC5C7E645C7E496A   /media/penusb   auto    defaults,uid=1000,gid=1000,umask=022   0       0

```

Should I put parameter "auto" in fourth column?

Thanks

---

### Post by oldfred on 2018-10-06
I believe it is nofail, but did not think Raspberry Pi used systemd, so other settings may be better.

---

