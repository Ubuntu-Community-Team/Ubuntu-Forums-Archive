---
title: "cannot changeUSB portable boot menu"
date: 2014-12-10
forum: New to Ubuntu
---

### Post by Paul_Beard on 2014-12-10
Has anyone got Grub2 Customizer to work on a USB system created via Pendrive's universal install system? Or found a way to change the boot menu to automatically login without the option to install Ubuntu etc,  I'm really struggling, bercause I can't edit isolinux.cfg and Grub Customizer doesn't seem able to find /cow.

Any ideas?

---

### Post by nerdtron on 2014-12-10
First, Pendrive linux's universal install doesn't really create a fully installed Ubuntu. Remember the days when you have an .iso file and you burn it to CD and then boot to it, next comes installation to hard drive? That "burn to CD" is like "burn to USB" now, which is what you created using pendrive linux.

So basically, pendrive linux creates an installer for Ubuntu which can be fully installed to the internal hard drive, external hard drive, or "another" USB drive.

Next, GRUB customizer only works for fully installed Ubuntu in which GRUB is full installed. It simply will not work on a Live USB which you already have now.

Finally, to get rid of the "Install ubuntu" option found on the Live USB created by Pendrive Linux (or unetbootin or Linux Live creator, or YUMI...etc..) you need to have a fully installed Linux.

I suggest this for full installation of Linux on 
You need two USB drives, one should be large enough to contain a full install (about 8GB and up)
1. Remove internal hard drives, (to avoid configusion on drives.)
2. Insert you USB with the Ubuntu Installer and boot to it.
3. Now insert the bigger USB.
4. Click the ubuntu installer on the desktop and install it on the bigger flash drive.

After the full installation you can use ubuntu, configure auto login, and use grub customizer.

---

### Post by Paul_Beard on 2014-12-10
What I really want is a portable OS on a usb that can be plugged into any computer and work. I am trying to get this so that we can give a school in the Gambia a bunch of laptops and give each kid a usb drive and then when they use the laptop it will be theirs entirely and when they make changes they will still be changed when they come back and use their stck again. They won't muck each other up and they can explore to their heart's content. (Like the Keepod project, but not using Android) Is this a pipe dream, or can it be achieved , somehow?

---

### Post by nerdtron on 2014-12-10
> **Paul_Beard said:**
> What I really want is a portable OS on a usb that can be plugged into any computer and work.?

That's why I said on my post.
You need at least 2 USB drives. The smaller one is the installer, and another bigger one will be the holding the Portable OS. You just install Ubuntu on the bigger USB just like a normal hard drive.

---

### Post by C.S.Cameron on 2014-12-11
You can do a Full install to flashdrive and then clone that drive for each of your gift computers.
You should use a 8GB min drive for a full install of Ubuntu. a 4GB drive may work for a Persistent install.
If you do not install any proprietary drivers, a Full install should work on any computer with the right spec's
Ubuntu 14.04 may be too much for an older machine, Lighter alternatives include LUbuntu and Puppy, (Puppy will work on just about anything).
My experience here in Sri Lanka is that the kids wipe Ubuntu and install Windows because they like the games, they then use the pendrives to transport viruses to all there friends in the form of pirate game downloads.
With the death of XP many kids are reinstalling Linux because Windows 7 is too much for many of the machines.

If you want to make persistent installs without Try/Install screen try the following, that pendrivelinux stuff is pretty old:


Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
Enter the syslinux directory, (or for UNetbootin the root directory).
Make the syslinux.cfg file writeable
Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.
Code is for 32bit versions, if using 64 bit change vmlinuz to vmlinuz.efi.

---

