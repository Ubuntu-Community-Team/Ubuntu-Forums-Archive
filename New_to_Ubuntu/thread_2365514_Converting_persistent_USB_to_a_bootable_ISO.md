---
title: "Converting persistent USB to a bootable ISO"
date: 2017-07-07
forum: New to Ubuntu
---

### Post by westy004 on 2017-07-07
Hi

I'm really stuck.
As part of a project at work, I was tasked to create a bootable image from a Ghost server which will then go away and secure erase the HDD on the workstations attached.
So I created a bootable USB stick with a 60MB persistent area for my changes and scripts. The USB stick and scripts runs a treat and is exactly how I want it to boot from Ghost, when I boot from USB.

I have tried so many things now to create a bootable ISO image, but nothing seems to work. I have managed to boot from an ISO, but even though the boot loader is set to persistent, it doesn't run any of the scripts. So obviously not in persistent mode.

Any ideas and help would be great.

Thanks in advance.

---

### Post by yancek on 2017-07-07
Which version/release of Ubuntu are you using?
If you have a bootable persistent usb that works the way you want, what is the need to create an iso file to boot from?  It will generally be easier to boot a usb than an iso, maybe explain why?
Did you create a 60MB persistent "file" or "partition"?

Could you name a few of the many things you have tried to create an iso?  Common software used in Linux would be mkisofs or genisoimage.
If you are using Ubuntu, you could use software such as Systemback or PinguyBuilder.  They both are generally used on installed systems to create a bootable iso file.  I've never used either on a persistent usb install so I'm not sure that would work, especially with a 60MB persistent file.

---

### Post by westy004 on 2017-07-07
Hi Yancek

I'm using 16.04 mini remix. The reason for the boot from an ISO image is because we need to securely erase up to 300 odd workstations from a network boot.

---

### Post by westy004 on 2017-07-07
Also..

I've tried dd'ing from unix as well as MagicISO and IMGBurn.

---

### Post by westy004 on 2017-07-07
You know thinking about it, I'm probably over complicating the solution.
From what you have advised, I'd be better of using Systemback and create an ISO of a workstation with Ubuntu and all my scripts ready to go.

Thanks

---

### Post by oldfred on 2017-07-07
I directly boot ISO from grub using loopback, but the mini install ISO has never worked. Have not tried with newest versions. The mini is not configured for loopback mount.
You may need to use sever version.
Or boot any live installer, and run scripts from a data folder.

 [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484) 
      
 ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by HermanAB on 2017-07-08
Secure erase??? If you encrypt the disks then you need not erase them - just forget the key.

Anyhow, the tools you need to erase disks are on the install CD, so you need not do anything.  Just copy the Ubuntu install ISO to a USB key with dd - done.

---

### Post by gordintoronto on 2017-07-08
When I want to erase a hard drive, I use DBAN. Since some of the computers I erase are quite old (won't boot from USB), I have DBAN on a CD.

---

### Post by kyknos12 on 2017-07-09
your make build bootable iso from genisoimage, install cdrkit package, copy files from usb to the home directory somewhere, /home/westy004/ubuntuiso, open the terminal
```
sudo genisoimage -r -V "Ubuntu" -cache-inodes -J -l \-b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot \-boot-load-size 4 -boot-info-table -o "/home/westy004/ubuntu-16.04-mini-remix.iso" /home/westy004/ubuntuiso
```

---

