---
title: "Flash drive multiboot?"
date: 2009-01-31
forum: Other OS Talk
---

### Post by zmjjmz on 2009-01-31
I acquired an old 1GB flash drive from my brother, and I installed Knoppix 6 by creating a fat32 partition and using syslinux.
I made that particular partition 700MB, so I have around 300MB free space.
Is it possible to install GRUB and have a multiboot going with, say SliTaz and xPUD (Moblin is too big, but I could have that alongside Knoppix only)?

---

### Post by smartboyathome on 2009-01-31
It is possible using syslinux. Check out multicd, specifically how it does it's multibooting. something similar could probably be done for a USB. :)

---

### Post by zmjjmz on 2009-01-31
[http://www.mepis.org/docs/en/index.php/Create_a_multiboot_CD_(or_USB_flash_drive](http://www.mepis.org/docs/en/index.php/Create_a_multiboot_CD_(or_USB_flash_drive))
Does that look sane?

---

### Post by smartboyathome on 2009-01-31
> **zmjjmz said:**
> [http://www.mepis.org/docs/en/index.php/Create_a_multiboot_CD_(or_USB_flash_drive](http://www.mepis.org/docs/en/index.php/Create_a_multiboot_CD_(or_USB_flash_drive))
Does that look sane?

Here is the correct place:
[http://ubuntuforums.org/showthread.php?t=718016](http://ubuntuforums.org/showthread.php?t=718016)

---

### Post by chris4585 on 2009-02-01
So I think I've mastered the art of multiusb booting, I have successfully installed and booted DSL, Slitaz, Puppy, Slax, and TinycoreLinux from my flash drive.

What I do is a bit tricky and messy (you'll end up with cruft files you don't need, but they're tiny and of course removable), but it does work.  I'm using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") to install whatever distro from whatever ISO I want to boot from my flash drive.

So lets say I have the Slitaz livecd, and unetbootin installed, I dump slitaz to my flash drive using unetbootin.

I see if it boots, it does.  Then on the flash drive I create a folder called /slitaz and move everything on the flash drive root to the folder /slitaz on my flash drive.

Then I select another distro I want, lets say Tinycore because it is small and easy peasy to get working.  On the same flash drive I use unetbootin to install Tinycore.

When you boot off your flash drive at this point, you should ONLY see tinycore on the boot menu.  Then see if tinycore boots, it does.

Now open up your flash drive, and open /syslinux.cfg and /slitaz/syslinux.cfg

Copy the slitaz entry from /slitaz/syslinux.cfg

> label Slitaz
menu label Slitaz
kernel /boot/bzImage
append initrd=/boot/rootfs.gz rw root=/dev/null vga=normal autologin

to /syslinux.cfg so it looks like this:

> default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label tinycore
menu label TinyCoreLinux
kernel /boot/bzImage
append initrd=/boot/tinycore.gz quiet waitusb=4 tinycore tce=sdb1 restore=sdb1

label Slitaz
menu label Slitaz
kernel /boot/bzImage
append initrd=/boot/rootfs.gz rw root=/dev/null vga=normal autologin

Now leaving this the way it is is wrong. You will have to change the kernel and append line for slitaz to look like this:

> label Slitaz
menu label Slitaz
kernel /slitaz/boot/bzImage
append initrd=/slitaz/boot/rootfs.gz rw root=/dev/null vga=normal autologin

so slitaz will boot the right kernel and the append line will be right, other wise you probably would get a conflict.

With this setup you should be able to boot Tinycore and Slitaz off of a flash drive.

To add another distro go to the flash drive's root and create a folder /tinycore and move everything tinycore related to /tinycore and repeat the same steps. Hint: When creating a folder for your distro, don't move the other distro's folder into the new folder, eg:

When creating /tinycore and copying everything tinycore related into /tinycore don't copy /slitaz to /tinycore.

[B]Tips:
[/B]
1) I periodically created backups of my flash drives root incase somewhere I screwed up heavily and would have to start over

2) Sometimes there will be conflicts with a distro's own boot loader and the unetbootin boot loader, all I can say is carefully remove the distro's boot loader and add the right entries to /syslinux.cfg.  I had a issue getting slax to work properly but I finally did figure out slax need to have the folder /slax with its modules in the right place, or something.

I hope this helps someone.

P.S. I might actually make a tutorial this is more of a write-up of how I did it.

Here is a example of my /syslinux.cfg

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label ubnentry0
menu label Slax (KDE)
kernel /slaxlinux/boot/vmlinuz
append initrd=/slaxlinux/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;telinit~4 changes=/slax/

label ubnentry2
menu label Slax Copy To RAM
kernel /slaxlinux/boot/vmlinuz
append initrd=/slaxlinux/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw copy2ram autoexec=xconf;telinit~4

label Slitaz
menu label Slitaz
kernel /slitaz/boot/bzImage
append initrd=/slitaz/boot/rootfs.gz rw root=/dev/null vga=normal autologin

label Puppy
menu label Puppy
kernel /puppylxde/vmlinuz
append initrd=/puppylxde/initrd.gz pmedia=cd

label DSL
menu label DSL
kernel /dsl/boot/isolinux/linux24
append initrd=/dsl/boot/isolinux/minirt24.gz ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791  nomce noapic quiet BOOT_IMAGE=knoppix

label tinycore
menu label TinyCoreLinux
kernel /tinycore/boot/bzImage
append initrd=/tinycore/boot/tinycore.gz quiet waitusb=4 tinycore tce=sdb1 restore=sdb1 
```

---

### Post by Zoasterboy on 2009-02-04
Thanks chris4585! Your mini-tutorial was incredibly helpful.

---

### Post by zmjjmz on 2009-02-04
I actually might have something like this working, by using chris's tutorial sans unetbootin.
I have Knoppix and SliTaz on a 1GB drive, and while Knoppix works fine, SliTaz suffered from a massive kernel panic on boot, but that may be due to a lack of netbook support.

---

### Post by chris4585 on 2009-02-05
> **Zoasterboy said:**
> Thanks chris4585! Your mini-tutorial was incredibly helpful.

Glad the mini tutorial worked for you.

---

