---
title: "Dual Booting"
date: 2016-06-17
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2016-06-17
Hi new to Linux so please bear with

I have both Win 10 and Ubuntu 15.10 on my hard drive, both showing in gparted, but when I start up it does not give the option of which os to boot into but loads direct to Ubuntu.

Please can someone help :confused:

Regards Bob

---

### Post by Bucky Ball on 2016-06-17
When it boots, and after the manufacturer splash screen at boot, hit the shift key repeatedly. That should bring it up. (It used to be escape and changed to shift but may now be something else, but try that first.)

To make a permanent change so it shows every time, open a terminal and 

```
sudo nano /etc/default/grub
```

In that file, make these lines at the top look like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Control+x and 'y' to write changes, save and close (instructions at bottom of that window for correct keys). Then:

```
sudo update-grub
```

Reboot and you should have a grub menu. Let us know.

---

### Post by grahammechanical on 2016-06-17
In Ubuntu run this command and watch the printout

```
sudo update-grub
```

Do you see the Windows 10 boot loader listed. There is another factor to consider. If that machine came with Windows 10 preinstalled then Windows 10 was installed in EFI mode. Then, that  means that to install Ubuntu we must run the live session in EFI mode and install Ubuntu in EFI mode.

If we install Ubuntu in BIOS/Legacy/CSM mode when Windows is installed in EFI mode then we will get a situation like this. Please read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

