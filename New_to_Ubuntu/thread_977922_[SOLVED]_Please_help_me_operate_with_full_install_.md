---
title: "[SOLVED] Please help me operate with full install on USB"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-10
I have searched the forums and the community documentation for help on this and I can't understand directions and/or they don't work.

I think my question is... Can I have two separate boot directories?  The computer will boot from the USB-Flash's /boot/grub when it is installed.  And then the computer will boot to the internal HD /boot/grub when the USB-Flash is not installed.

The goal is to have two options:
[LIST=1]
[*]Plug USB Flash in, turn on computer and boot from /boot/grub located on USB Flash drive (to chose either internal HD OS or OS on USB-Flash) 
[*]Turn computer on without USB plugged in and boot from /boot/grub located on internal HD (to chose either OS on internal HD)
[/LIST]

Right now I have to keep the USB-Flash plugged in to boot to any of the operating systems on the box.  If I unplug the USB-Flash before restart/turn-on then I get a grub "error 21".

Am able to boot without the USB-Flash installed by using a SuperGrub disk.  But once I do that I am not able to boot the OS on the USB-Flash.

Have searched for information on the "master boot record" but I can't find anything that helps me.  If I could understand where and what's-in the MBR that might help.

Following is information when I'm booted from and using the OS on the USB-Flash drive and /boot/grub/menu.lst (on USB-Flash) is included as an attachment.  If you need a certain part of the menu.lst, let me know and I'll post it.

fstab:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1461914      730926   83  Linux
/dev/sdb2        14329980    15791894      730957+  82  Linux swap / Solaris
/dev/sdb3         1461915    14329979     6434032+  83  Linux
```

blkid:
```
/dev/sdb1: UUID="275e4d72-b1db-4896-9b42-34a36f8740cd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="61e7e252-a95d-402d-9110-5bcf7b1702fb" 
/dev/sdb3: UUID="6d62bb9e-c908-4309-9fb7-02b1d7379cf2" TYPE="ext3"
```

fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=6d62bb9e-c908-4309-9fb7-02b1d7379cf2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc1
UUID=275e4d72-b1db-4896-9b42-34a36f8740cd /boot           ext3    relatime        0       2
# /dev/sdc2
UUID=61e7e252-a95d-402d-9110-5bcf7b1702fb none            swap    sw              0       0
```

mount:
```
/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb1 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
```

Thanks for any help with this.

:guitar:

---

### Post by ugm6hr on 2008-11-10
As a simple guide to get you started:

1. Install your USB OS with GRUB on the USB MBR (which I believe the USB-installer for Ubuntu does: [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/))

2. Install your HD OS with GRUB on the HD MBR.

3. Set BIOS to boot from USB as 1st boot device.

4. Edit your /boot/menu.lst on the USB OS to include your HD OS.

Essentially, this means that if there is no bootable USB plugged in, the computer will boot from the HD (GRUB on HD MBR, pointing to menu.lst on HD).  If a bootable USB is plugged in, it will boot from GRUB on USB MBR, which points to edited menu.lst on USB; this includes the USB OS, as well as the HD OS.

Apart from step 4, this is pretty straightforward.

---

### Post by Carl Hamlin on 2008-11-10
While it can be done, I would *really* reconsider running your OS off of a USB drive. Flash can sustain a finite number of write/erase cycles before failing, and when it fails it tends to do so suddenly. Running your OS off of the flash drive will substantially shorten the lifespan of the drive by way of sustained writes to swapfile.

---

### Post by boof1988 on 2008-11-10
> **ugm6hr said:**
> As a simple guide to get you started:

1. Install your USB OS with GRUB on the USB MBR (which I believe the USB-installer for Ubuntu does: [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/))

2. Install your HD OS with GRUB on the HD MBR.

3. Set BIOS to boot from USB as 1st boot device.

4. Edit your /boot/menu.lst on the USB OS to include your HD OS.

Essentially, this means that if there is no bootable USB plugged in, the computer will boot from the HD (GRUB on HD MBR, pointing to menu.lst on HD).  If a bootable USB is plugged in, it will boot from GRUB on USB MBR, which points to edited menu.lst on USB; this includes the USB OS, as well as the HD OS.

Apart from step 4, this is pretty straightforward.

Thanks for the help.  I'm taking a look at it right now.  No more questions for now.

---

### Post by boof1988 on 2008-11-10
> **Carl Hamlin said:**
> While it can be done, I would *really* reconsider running your OS off of a USB drive. Flash can sustain a finite number of write/erase cycles before failing, and when it fails it tends to do so suddenly. Running your OS off of the flash drive will substantially shorten the lifespan of the drive by way of sustained writes to swapfile.

I appreciate the advice.  The reason for doing this is to learn as well as have a USB pendrive ready to operate in/on this computer.

The pendrive I want to use is just a 8Gb one and they're pretty cheap.

One of the other things I want to do is see if there is a difference in the amount of battery run-time between running the OS on the HDD vs. pendrive.

And I'll just have to remember not to put naything important on the pendrive.

Thanks Again.

---

### Post by boof1988 on 2008-11-11
> **ugm6hr said:**
> As a simple guide to get you started:

1. Install your USB OS with GRUB on the USB MBR (which I believe the USB-installer for Ubuntu does: [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/))

2. Install your HD OS with GRUB on the HD MBR.

Thanks for the link.  I tried it... and no success.  I do have OSes with grub on each (HD and USB).  Will continue to look at it and try to understand what each step is actually doing.  I was able to get a full OS on USB to work by adding the appropriate lines to /boot/grub/menu.lst on the HD.  Maybe this is the best way.

> **ugm6hr said:**
> 3. Set BIOS to boot from USB as 1st boot device.

This is the confusing part for me.  The bios is set to boot to USB then CD/DVD then HD.  An install/LiveCD (burnt directly from an iso) will boot automatically on startup but the USB I created using the method at pendrivelinux.com would not boot automatically.

> **ugm6hr said:**
> 4. Edit your /boot/menu.lst on the USB OS to include your HD OS.

I have done the reverse of this and I think it will probably be the best choice *dunno*.  The only thing I need to figure (if I continue with this method) is how to make it so I can boot a different USB than the original (since the UUID is included in the lines added to menu.lst).

> **ugm6hr said:**
> Essentially, this means that if there is no bootable USB plugged in, the computer will boot from the HD (GRUB on HD MBR, pointing to menu.lst on HD).  If a bootable USB is plugged in, it will boot from GRUB on USB MBR, which points to edited menu.lst on USB; this includes the USB OS, as well as the HD OS.

Apart from step 4, this is pretty straightforward.

I'm trying to understand where to see the MasterBootRecord and how to modify it, or at-least understand how it works.

Thanks again for your help with this.

:)

---

