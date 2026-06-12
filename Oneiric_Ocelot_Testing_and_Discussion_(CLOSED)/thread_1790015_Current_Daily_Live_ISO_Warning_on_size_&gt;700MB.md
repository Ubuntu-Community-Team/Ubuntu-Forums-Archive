---
title: "Current Daily Live ISO: Warning on size &gt;700MB"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2011-06-24
I noticed the ISO are larger than what can fit on a CD, and rightfully a warning is provided on the [download site]("http://cdimage.ubuntu.com/daily-live/current/").
> Warning: This image is oversized (which is a bug) and will not fit onto a standard 700MiB CD. However, you may still test it using a DVD, *_**a USB drive**_*, or a virtual machine.My question(s):
(1) After I download the ISO, how do I "put" it on the USB so I can install daily live off the USB? Do I just copy the ISO file to USB and boot off the USB? or Do I have to firstly have Ubuntu (or other distro that allows live USB Creation) installed, then use the USB Creator app to make a live USB?
(2) I have read somewhere on this forum, that it may be possible to "place" the ISO directly on the USB and run off it, without going through above step. Is this possible? how?

Thanks
swb

---

### Post by teh603 on 2011-06-24
I always use the USB creator app from within Kubuntu, although there's supposed to one for Windows on the desktop of the DVD/CD. So if you can find a way to mount the iso you might be able to get that to work.

---

### Post by oldfred on 2011-06-24
I use the grub2 loop mount, so I just copy ISO to flash drive, edit a grub.cfg file with correct boot stanza.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I have multiple ISOs on one 4GB flash. They are all in the folder /boot/iso. I still add nomodeset, I have had to have it for the last several versions with my nVidia, but have not tried without it recently.

Part of my grub.cfg:

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 11.10 Oneiric 64bit" {
    set isofile="/boot/iso/oneiric-desktop-amd64+mac.iso"
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset noprompt
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}
```

---

### Post by P-I H on 2011-06-24
It is discussed in this thread
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=usb](http://ubuntuforums.org/showthread.php?t=1783752&highlight=usb)

I use the Disk Utility to format the USB with no partition.
Then I use the command
**dd if=oneiric-desktop-amd64.iso of=/dev/sdb**
in the terminal to copy the ISO to the USB.
Then it is just to reboot, but this different depending on the motherboard.
On my test system with an older MSI motherboard the boot device shall be set to Hard Disk with the USB as the first disk in BIOS.
On another motherboard from Gigabyte it is possible to set the USB as boot device in BIOS.

---

### Post by shuttleworthwannabe on 2011-06-24
Thank you all; P-I H it worked perfectly; had I known this it would have saved me a couple of CD-ROM/DVD.
Thanks
BTW-- I ran that command from Fedora 15.

---

