---
title: "Can't get back into Windows."
date: 2014-09-20
forum: New to Ubuntu
---

### Post by rapzeh on 2014-09-20
I just installed Linux on a secondary 1TB HDD, AWAY from my windows HDD, which I now can't access. When I turn on my computer I just boot straight into Ubuntu, help!

EDIT: When trying to look at the drive in Ubuntu, it says the following:
"Error mounting /dev/sda2 at /media/james/Standard Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/james/Standard Drive"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

---

### Post by QIII on 2014-09-20
Hello!

Just to be sure, is this Windows 8?

---

### Post by rapzeh on 2014-09-20
It is, yes.

---

### Post by QIII on 2014-09-20
Did you disable the "Fast Boot" feature in the BIOS/UEFI setup before installing Ubuntu?  Did you install Ubuntu in EFI or Legacy BIOS mode?

---

### Post by grahammechanical on 2014-09-20
That error message is normal. I have a Windows 8 preview installed on one of my partitions. My machine is BIOS and not UEFI. I get exactly the same message if I use the File Manager (Nautilus) to access that partition with Windows 8. The key part of the message is the bit that says "Windows is hibernated." In order to give Windows 8 a fast loading time Microsoft set Windows 8 to hibernate instead of shutting down. That message is nothing to do with the machine loading straight into Ubuntu.

When you install Ubuntu was that Windows 8 hard disk connected? If not then Ubuntu does not know that Windows 8 exists. Try this command from Ubuntu

```
sudo update-grub
```

Does the printout show a line for a Windows 8 boot loader? Now, do you get a Grub boot menu with Windows 8 boot loader as an option?

Regards.

---

### Post by rapzeh on 2014-09-21
> **QIII said:**
> Did you disable the "Fast Boot" feature in the BIOS/UEFI setup before installing Ubuntu? Did you install Ubuntu in EFI or Legacy BIOS mode?
I'm fairly new to Ubuntu and stuff, but this is what I did:
Used a program to create a bootable USB stick.
Booted from said USB Stick
Installed Ubuntu on my second drive, making it ext4 or whatever it was.
Installed Ubuntu.
Changed the boot options so now it boots from the HDD.
Now it only boots into Ubuntu, not windows :(

---

### Post by rapzeh on 2014-09-21
> **grahammechanical said:**
> That error message is normal. I have a Windows 8 preview installed on one of my partitions. My machine is BIOS and not UEFI. I get exactly the same message if I use the File Manager (Nautilus) to access that partition with Windows 8. The key part of the message is the bit that says "Windows is hibernated." In order to give Windows 8 a fast loading time Microsoft set Windows 8 to hibernate instead of shutting down. That message is nothing to do with the machine loading straight into Ubuntu.

When you install Ubuntu was that Windows 8 hard disk connected? If not then Ubuntu does not know that Windows 8 exists. Try this command from Ubuntu

```
sudo update-grub
```

Does the printout show a line for a Windows 8 boot loader? Now, do you get a Grub boot menu with Windows 8 boot loader as an option?

Regards.

So uh.. what happened when I did that was weird, to say the least..
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
**Found Windows 7 (loader) on /dev/sda1**
Found Windows 8 (loader) on /dev/sda2
I have NO idea why that is there, because I have previously installed and uninstalled Windows 7, but no traces of it exist at the moment.

---

### Post by Rob Sayer on 2014-09-21
Well, the fact that it found a loader tells me there is a trace of windows 7.  One of the things I dislike about windows is that it's so difficult and non transparent to completely uninstall software.  You often just think you've totally removed stuff.

I don't think that's really relevant to this problem, but I can't think of any better suggestions than in post #5.

---

