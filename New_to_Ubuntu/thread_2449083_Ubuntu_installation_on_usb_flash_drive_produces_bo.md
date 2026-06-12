---
title: "Ubuntu installation on usb flash drive produces boot errors"
date: 2020-08-19
forum: New to Ubuntu
---

### Post by ggolub on 2020-08-19
hello Forum,

i am new to Ubuntu.
I have installed it on flash driver.
When i try to boot, I am getting the following errors. 

Can you tell if i can run Ubuntu from flash drive and/or this error is fixable.
thank you!

_&#8203;boot message:_
vfs: cannot open root device sdc5 or unknown-block(0.0): error -6
Please append a correct "root=" boot option: here are the available paritions:
Kernel panic - not synciing: VFS: Unable to mount root fs on uknown-block(0.0)

_fstab file:_

# /etc/fstab: static file system information. 
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc5 during installation
UUID=f38adcb0-ecf6-451c-9d9b-1ab438341d59 /               ext4    errors=remount-ro 0       1
# /mount1 was on /dev/sdc1 during installation
UUID=83A0-B965  /mount1         vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdc6 during installation
UUID=aabde635-1fb3-43f4-889d-6451649cec9e none            swap    sw              0       0

---

### Post by sudodus on 2020-08-20
Please describe with details

- The computer (brand name and model)
- Thr computer's graphics chip/card (brand name and model)
- The USB flash drive (size, brand name and model)

- Is the computer booting in UEFI mode or BIOS mode? (If Windows 10 was installed, when you bought the computer, it is probably booting in UEFI mode).

- How did you make the installation (the more details, the better)?

[hr][/hr]
The following link and links from it can give you some tips of what might be the problem,

[Can I install Ubuntu in a USB stick and run it as my learning machine? Will it run as a normal Ubuntu without difference?](https://askubuntu.com/questions/1267370/can-i-install-ubuntu-in-a-usb-stick-and-run-it-as-my-learning-machine-will-it-r/1267376#1267376)

---

### Post by ggolub on 2020-08-20
Hello,

thank you for your respond. 
The issue was fixed by re-installing usb drive. 
I choose 11gb for root partition instead of 5.7 as an installation screen was recommending.
Documentation recommends not less then 4. 

After installation i found ubuntu running Incredibly slow - much beyond point of usability. 
This laptop has 4gb ram and T... dual processor - very old. 
But it runs Win 7 well. 

It could be an issue with usb drive 2. 
I am going to continue researching the idea to run Linux on that pc.

---

### Post by sudodus on 2020-08-21
There are **flavours** of Ubuntu with a lighter footprint, that work much better [than standard Ubuntu] in a very old computer,

- [Lubuntu](https://lubuntu.me/)
- [Xubuntu](https://xubuntu.org/)

You find all currently supported versions and flavours of Ubuntu via this link:

- [releases.ubuntu.com/](https://releases.ubuntu.com/)

[hr][/hr]
The following link can help you decide how an old computer can be used:

- [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by CelticWarrior on 2020-08-21
As above.

And regardless of the flavour you need to have realistic expectations. "Old computer" + USB2 will be slow no matter how light the Ubuntu flavour is.
Installing in an internal HDD will be much different in this case.

---

