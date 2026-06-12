---
title: "installing on external HDD"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2011-10-19
Hi all, I'm trying to install 11.10 on an external USB HDD, but the installer returns saying that installing grub to the /dev/sdd (my USB drive) fails and then the installer crashes.

As this is a work pc (supposedly for doing work things on ;))changing the internal hard drive at all is a no go, so I can't install grub there.

Basically the general idea is that when the external hard drive is removed the pc will boot exactly as when it was given to me, but plug in (or switch on) the external drive and I can dual boot.

Any ideas? Many thanks!

---

### Post by jonnny_j22 on 2011-10-19
sorry I should have said that I've checked the basics - the pc can boot from the hdd, and it is before the internal drive in the boot order.

I've tried twice more with 2 different downloads and hit the same problem (i tried the mini cd but it gets confused by the internal RAID set up) it is installing fine until the boot loader crashes the installer at the removing files stage. I can't see any way to install ubuntu without the bootloader in the installer menus?

Thanks again!

---

### Post by jonnny_j22 on 2011-10-21
okay here's where I'm at after a fair bit of faffing: 

ubuntu 10.04 will install to the external HDD from the live CD (it's a CD from 2010 so I don't know if the installer has changed) and run fine.

Ubuntu 11.04 will only install if the hard drive is connected internally, but will then run externally via usb. However upgrade to 11.10 fails.

Ubuntu 11.10 again only installs if the drive is connected internally, however once the drive is then connected via usb, it boots up fine but all of the drives (internal, usb and it's own file-system) have become read only.

Any ideas anyone? after some faffing I have found a way to get open suse to boot and of course puppy runs fine (i even followed a guide to getting win 7 to boot from usb!) but this latest version of ubuntu seems unusually resistant.

---

### Post by oldfred on 2011-10-21
Is this perhaps a USB3 port? There were some issues before with that, but I do not know if they have all been resolved.

Did you try reinstalling grub2's boot loader to sdd after the install?

Sometimes some BIOS settings can cause issues, but with the very newest BIOS I am not sure if that is an issue with external drives.

I have copied these issues from others, review to see if any apply:

> Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.


---

### Post by jonnny_j22 on 2011-10-23
hi there, Yeah I thought the USB 3.0 card might be the problem, so I've tried it in the motherboards USB 2.0 and, just for a laugh the firewire port, no luck! Also tried using a different external hard drive and a different caddy, but I seem to always end up at the same point - it'll install internally, but as soon as the Hdd is external again the file systems (all hdds connected) become 'read only' and it's useless.

I don't think it's the BIOS as I've got the newest version and opensuse is working fine, tried a couple of different options, but it's not the most feature rich bios i've seen.

I'm thinking it's one of two things -
1) Ubuntu's being confused by the fact the internal drives are in a RAID set up (which, of course, I can't do anything about)
2) This is just not possible with this version of ubuntu?

Has anyone had any luck installing ubuntu to a usb hdd as a traditional install? I would go down the live ubuntu route, but with OS working it seems unnecessary!

---

