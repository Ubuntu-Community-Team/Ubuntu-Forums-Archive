---
title: "Live &amp; Persistent &quot;Buntu&quot; on USBv3 - Updates Problematic"
date: 2015-03-21
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-03-21
Of late, I've been experimenting (aka playing) with various "buntus" on a Live-Persistent USBv3.    When done on a fast v3 usb stick, the speed and functionality of this method of running Linux is "almost" as good as a standard hdd install.   Applications can be installed & uninstalled, the system can be tweaked, and things like wifi password are saved and don't need updating at next login yada yada yada.   A handy tool to say the least.    Note this is a "Live" version of the distro, not an installed version on the flash-stick.

However, one seeming disadvantage is that the standard update process (security and bug updates) do not work nearly as well as a standard install (especially if the updates are many/large).   Basically, the updates never seem to complete or there are various errors.

So, I've been wondering - is there any way to accomplish these updates in smaller chunks or sections, so the entire update has a better chance of completing?   (assuming there is ample room on the usb-stick).  

a)    Would it make more sense to utilize a distro that features a "rolling-update" process so various "complete OS build snapshots" can be downloaded and installed?

b)    Would it make more sense to actually install the OS to flash-stick rather than utilize the Live method on a larger (16 GiB) usbv3 stick? (am trying to visualize what grub/boot loader changes would result from this type of install).

Any thoughts appreciated.

GG

---

### Post by kerry_s on 2015-03-21
you can install to the usb, just make sure when your partitioning you chose "something else", you'll see right below the option to install grub, set it to the same usb your installing to.

i do something similar with sd cards, so i just swap cards when i want something else.

---

### Post by C.S.Cameron on 2015-03-21
I have been working with Persistent and Full flash drive installs for a few years now and do not find much advantage of a persistent install over a Full install.

A persistent install can be used to install Ubuntu to another drive. 

A Full install can be more secure and is easier to update and upgrade and install proprietary video drivers.

I've tried some rough benchmarking and both had similar scores, The Full install booted the fastest.

---

### Post by kerry_s on 2015-03-21
also i'v found installing on ext2, helps to give a little speed.

---

### Post by Geoffrey_Arndt on 2015-03-21
OK, CS & Kerry,  thanks for your feedback!   I haven't yet done a full install to usb-stick and look forward to trying it out.   It seems to me the major advantage is the "update-ability" of the install.   When I get to the choice of where to write Grub, do I indicate sda so the updated bootup menu will show the install?  Or would the new grub file be installed to the usb at /media/name of flash drive?   Not clear on this last point . . . 

I think I would prefer one comprehensive Grub menu with all OS's showing up, and then using the grub "reinstall-update" steps later if I want one of the hdd installs to have the controlling grub.

Well, I'm for sure making the most of my 9 year old Lenovo laptop as my "Linux Test Lab" . . :guitar:


GG

---

### Post by kerry_s on 2015-03-22
i install grub to the same location as i install the system to so it's separate other wise, grub will be on the main drive(sda) but /boot will be on the drive, so if you ever try to boot with out the drive, it will fail. you can always add menu entry's to any grub menu by running "sudo update-grub" but if that grub is scattered between different installs your screwed.
you want each install to be self contained, it needs it's own grub with out touching any other install. it also gives you the option to boot from the bios boot menu, like when you run it live.

so if you install on sdc, grub needs to be on sdc.

---

### Post by Geoffrey_Arndt on 2015-03-22
Thanks Kerry . . . that clears things up.  So, sdc it'll be then.   

GG

---

### Post by kerry_s on 2015-03-22
> **Geoffrey_Arndt said:**
> Thanks Kerry . . . that clears things up.  So, sdc it'll be then.   

GG

try doing it on ext2. for example when go to make your live usb, use gparted to format the usb ext2, then just use unetbootin to make your installer as usual.
same thing when you install use ext2 rather than the ext4.

---

