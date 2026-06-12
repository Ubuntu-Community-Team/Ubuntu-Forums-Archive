---
title: "One OS, 2 computers"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by rixon2 on 2014-05-14
Hi, I've run into a bit of a predicament. I have a laptop I regularly use (Dell Latitude e6430) and inherited another ultrabook (Lenovo Thinkpad X100e). 
[LIST=1]
[*]The Lenovo does not have an internal hard drive, so I attempted to install Ubuntu 14.04 on an external hard drive (ADATA HD710 1TB) and use it for the Lenovo.
[*]The Lenovo doesn't have a cd drive and I don't have an external cd drive, so I used the Dell to do the installation.
[*]Ubuntu boots fine from the external hard drive on the Dell, but on the Lenovo I end up with boot options on the Grub menu as if I'm still on the Dell. I boot Ubuntu but have this similar error message:
[/LIST]

[LIST]
[*]error failure reading x8310 from 'hd0'
[/LIST]

I've tried the fixes suggested for this error message but I'm just stumped. I thought I'd be fine installing a standalone OS on an external hard drive from any capable computer. Any ideas? Anything I overlooked?

---

### Post by electrohandyman501 on 2014-05-14
Not sure about usb hard drives, but I have a couple of thumb drives that I have setup for booting the 'live cd' software.

---

### Post by Impavidus on 2014-05-15
The Lenovo can boot from usb. So assuming you have at least 2 usb ports on the Lenovo you can boot it from a live usb, then connect the external hard drive and install Ubuntu on the external drive. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Whilst installing from the Dell, the installer ran the OS prober, detecting the OS installed on the Dell and putting that in the grub menu. If you clicked "install restricted software" (or something like that) it may also have installed drivers, which are specific for the Dell's hardware.

---

### Post by sudodus on 2014-05-15
> **Impavidus said:**
> The Lenovo can boot from usb. So assuming you have at least 2 usb ports on the Lenovo you can boot it from a live usb, then connect the external hard drive and install Ubuntu on the external drive. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Whilst installing from the Dell, the installer ran the OS prober, detecting the OS installed on the Dell and putting that in the grub menu. If you clicked "install restricted software" (or something like that) it may also have installed drivers, which are specific for the Dell's hardware.

+1

I have often made installed systems in USB drives, pendrives as well as HDDs and SSDs, and they are portable between computers, as long as you avoid proprietary drivers. If one computer needs a proprietary driver or if one computer has UEFI, things get more complicated, but there are ways around that too.

In this case I suggest that you install from an Ubuntu install USB drive (typically a pendrive) to another USB drive (typically a HDD). Select 'Something else' at the partitioning page in the installer, and check carefully that the bootloader will be installed into the correct USB drive (the same drive as the installed system, to its head /dev/sdx, not to a partition for example /dev/sdx1).

---

### Post by rixon2 on 2014-05-15
Ok, I'll try that. I used an SD card but discovered that it wasn't wasn't bootable (stupid me). I didn't know if most flashdrives fell under that category too. Is any type fine? Do I have to format it from anything besides the common FAT32?

---

### Post by rixon2 on 2014-05-15
Thank you all very much by the way

---

### Post by rixon2 on 2014-05-15
So I tried this process and I ended up with this:
[ATTACH=CONFIG]253196[/ATTACH][ATTACH=CONFIG]253197[/ATTACH]

is it because the boot manager is looking for a hard drive? I thought the liveUSB was sufficient even though I have no hard drive and will use an external instead.

---

### Post by sammiev on 2014-05-15
You need to tell your bios that you want to boot from usb.

---

### Post by rixon2 on 2014-05-15
I tried that too. Same result.

---

### Post by sammiev on 2014-05-15
Have you tried to boot the USB device from your other computer to see if it boots?

---

### Post by rixon2 on 2014-05-15
It worked for the Dell but not for the Lenovo

---

### Post by rixon2 on 2014-05-15
It works for the Dell, but still not working for the Lenovo.

---

### Post by sammiev on 2014-05-15
I read this thread all over again and post #3 & 4 has it very well covered. Read post #3 and follow it closely.

---

### Post by sudodus on 2014-05-16
> **sammiev said:**
> I read this thread all over again and post #3 & 4 has it very well covered. Read post #3 and follow it closely.

+1

Maybe the tips in this link [Booting the Computer from USB]("https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB") will help.

---

