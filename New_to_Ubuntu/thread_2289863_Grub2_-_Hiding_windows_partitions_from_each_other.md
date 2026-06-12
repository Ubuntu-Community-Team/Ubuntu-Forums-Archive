---
title: "Grub2 - Hiding windows partitions from each other"
date: 2015-08-07
forum: New to Ubuntu
---

### Post by LinuxAlexs on 2015-08-07
Hello

**BACKGROUND**

I have partitions/OS's set up like this:

DISK 1 (Grub bootloader on MBR)

1) DOS partition hanging around. _It says boot but it isn't anything to do with booting_.
2) Windows 8 NTFS operating system (DAW)
3) Another Windows 8 operating system (GAMES)
4) Yet another Windows 8 operating system (DEV)

DISK 2

1) Data partition (NTFS)
2) Linux (Latest Ubuntu studio, where grub2 is)
3) Linux swap

As a picture says a thousand words here it is:
[IMG]http://s22.postimg.org/b9f75ljgh/disklayout.jpg[/IMG]


Right now Grub 2 is booting all 4 operating system fine.


**THE PROBLEM**

I want to hide all windows operating system drives from each other. So when I boot up in Windows 8 (DAW) it will not see Windows 8 (GAMES) or Windows 8 (DAW).

I've looked at the documentation but I'm pretty confused.

Could you give me some basic pointers and code examples please. I'm fairly nooby here.

Many Thanks!

---

### Post by yancek on 2015-08-07
>  DOS partition hanging around. _It says boot but it isn't anything to do with booting_.

In all likelihood, if you are using MBR/BIOS to boot, that would be your windows boot partition.

Do you mean that after you boot one of the windows systems, you do not want to be able to view/access another windows system from the current windows system?  If that's the case, you are on the wrong forum and need to go to some windows forum such as the one at the link below:

 
[http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives](http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives)

---

### Post by LinuxAlexs on 2015-08-07
> **yancek said:**
> In all likelihood, if you are using MBR/BIOS to boot, that would be your windows boot partition.
 [http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives](http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives)


Nope,  as stated this has 100% nothing to do with booting. The volume label is a red herring. I was playing around with acronis OSSelector at the time and this has been condemned to history. We don't need to worry about this, although would be nice to hide it as well from windows as well. Each windows installation boots itself on it's own BCD contained on it's own partition. They can be regarded as standalone.

Any info on my problem above?

Thanks

---

### Post by LinuxAlexs on 2015-08-07
> **yancek said:**
> 

Do you mean that after you boot one of the windows systems, you do not want to be able to view/access another windows system from the current windows system?  If that's the case, you are on the wrong forum and need to go to some windows forum such as the one at the link below:
 
[http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives](http://www.tomshardware.com/forum/5383-63-dual-boot-windows-windows-hide-drives)

Nope. In a nutshell I want grub to mark an  NTFS partition as hidden before Windows starts. I also want it to hide the DOS partition. I've did this before with the Acronis boot loader which got removed. Grub2 is installed in LInux partition and triggers off the MBR. I just need to hack the grub files in Linux.
Any ideas?

---

### Post by oldfred on 2015-08-07
Windows installs only boot from one primary NTFS partition with the boot flag.
       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Since already installed, you may be able to move boot flag to each install and run Windows repairs to install Windows boot files & BCD into each install. Then grub2's os-prober can find all installs separately. Otherwise each additional install overwrites the BCD in first install and adds all installs to BCD. You may need to houseclean BCD in first install.

Usually better to keep grub installed to Ubuntu drive or sdb in your case and keep a Windows boot loader in sda. Then if issues with grub you can still boot Windows. But if you reconfigure you only will be able to boot one Windows with boot flag. Grub only boots Working Windows so that is why you need to have a way to boot Windows, but best to also have a Windows repair flash drive.

---

### Post by LinuxAlexs on 2015-08-07
> Windows installs only boot from one primary NTFS partition with the boot flag.

Each copy of windows has BCD installed on it. They are stand alone entities. GRUB points to this when menu is selective.
Everything works fine right now.

I appreciate the advice but please ... :p
All I need is grub to hide NTFS and DOS partitions selectively upon the user selecting a grub menu entry before any operating system boots. How can I do this?
I'm actually in */etc/default *and /boot/grub/[/I] right now scratching my head.

Many Thanks..!!

---

### Post by oldfred on 2015-08-07
See #12 on parttool.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

> insmod chain
insmod ntfs
parttool (hd0,1) hidden-
parttool (hd0,2) hidden+
parttool (hd0,5) hidden-

---

### Post by LinuxAlexs on 2015-08-07
Got it many thanks! It works as below... Does this look good? (Working on mirrored RAID)

Another question, any idea what this does?

```

if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  5E69B2320A3D16F1
else
  search --no-floppy --fs-uuid --set=root 5E69B2320A3D16F1
fi


```

SOLUTION BELOW!

/etc/grub,d/40_custom:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "START - Adding Windows OS to Grub 2 Menu"
menuentry "DAW - Windows 8" {
insmod part_msdos
insmod ntfs
set root='(/dev/mapper/isw_ifefcjibh_ARRAY0p2)'
parttool (hd0,1) hidden+ boot-
parttool (hd0,2) hidden- boot+
parttool (hd0,3) hidden+ boot-
parttool (hd0,4) hidden+ boot-
parttool (hd1,2) boot-
set root='(hd0,2)'
chainloader +1
}

menuentry "GAMES - Windows 8" {
insmod part_msdos
insmod ntfs
set root='(/dev/mapper/isw_ifefcjibh_ARRAY0p2)'
parttool (hd0,1) hidden+ boot-
parttool (hd0,2) hidden+ boot-
parttool (hd0,3) hidden- boot+
parttool (hd0,4) hidden+ boot-
parttool (hd1,2) boot-
set root='(hd0,3)'
chainloader +1
}

menuentry "DEV - Windows 8" {
insmod part_msdos
insmod ntfs
set root='(/dev/mapper/isw_ifefcjibh_ARRAY0p2)'
parttool (hd0,1) hidden+ boot-
parttool (hd0,2) hidden+ boot-
parttool (hd0,3) hidden+ boot-
parttool (hd0,4) hidden- boot+
parttool (hd1,2) boot-
set root='(hd0,4)'
chainloader +1
}
echo "FINISH - Adding Windows OS to Grub 2 Menu"
```

p.s. Grub Customizer is a life saver!

---

### Post by LinuxAlexs on 2015-08-09
Bumping can somebody briefly explain the nofloppy code above?

Many thanks...

---

### Post by oldfred on 2015-08-09
I assume the search will not include looking for boot files on a floppy drive. It searches other devices for correct UUID.

Before Linux booted using the set root = device like /dev/sda. But many systems changed device order in BIOS. My system would see a flash drive as sdf, but when rebooting as sdb. And I normally booted from sdc which then became sdd. Or if only booting from sdc device it would not boot as it had changed.
But Linux changed to use UUIDs and uses a search to find the UUID.

You can still boot with only a set root by device or you can remove the set root line and just use search.

---

### Post by LinuxAlexs on 2015-08-16
OK brilliant thanks!

---

