---
title: "Editing my Bootloader"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-11-23
First of all, let me explain how my system is currently structured. To assist me, here's the output of sudo fdisk -lu

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x509ee0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24578047    12288000   27  Unknown
/dev/sda2   *    24578048   217948159    96685056    7  HPFS/NTFS
/dev/sda4       217948160   312578047    47314944    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301487 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    83554064    41777001    f  W95 Ext'd (LBA)
/dev/sdb3        83554065   156296384    36371160    7  HPFS/NTFS
/dev/sdb5             126     4209029     2104452   82  Linux swap / Solaris
/dev/sdb6         4209093    36290834    16040871   83  Linux
/dev/sdb7        36290898    83554064    23631583+  83  Linux
```

So, sda is my internal HDD on which Vista is my default O/S and Ubuntu is there as a wubi install.

When the external HDD is not connected, I get the bootloader (that I think is part of Windows) offering me the option of Vista or Ubuntu. All very nice and simple. I don't see any reason to make any changes there.

My sdb device is my external HDD on which I have openSUSE installed, as well as an NTFS drive for keeping backups and files that I want to use in any of the operating systems.

When I boot with the external HDD connected, the bootloader that appears is the one put there by openSUSE, as you'd expect because the USB HDD is higher ranking in my bios boot options.

This works OK, but what I'd like to do is to add options to the openSUSE bootloader such that I can boot Vista and/or Ubuntu from it.

Anyone got any suggestions as to how I should do that?

---

### Post by maybeway36 on 2008-11-23
Adding this to /boot/grub/menu.lst should help:
```
title Windows Vista
rootnoverify (hd0,1)
chainloader +1
```
If it doesn't work, try chaning it to (hd1,1).

---

### Post by Roger Allott on 2008-11-23
> **maybeway36 said:**
> Adding this to /boot/grub/menu.lst should help:
```
title Windows Vista
rootnoverify (hd0,1)
chainloader +1
```
If it doesn't work, try chaning it to (hd1,1).

Blimey, it's THAT simple?!!?

Presumably, that would give it the option of booting Vista. Any ideas on how to boot Ubuntu that's been installed through wubi?

Could you (or someone) please explain why you suggest using 'rootnoverify' instead of 'root'? What's the difference? What is to be verified (or not)?

Also, what is the second parameter in rootnoverify (in this case 1) signalling?

I've noticed in other threads discussing grub that there's usually a line starting 'kernel' and another starting 'initrd'. What do they do and why do you suggest not using them in this instance?

Is it possible/advisable to make changes to menu.lst in the text editor?

---

### Post by phidia on 2008-11-23
You can use the chainloader command to boot linux/ubuntu also and there are good reasons IMO to do so.

The # 1 you are asking about is the 2nd partition hd0,1 means the first drive, 2nd partition. Grub counts from "0".

Added: You can open gedit with sudo or gksudo (from a terminal) to get root privilege.

---

### Post by Roger Allott on 2008-11-23
Ah, thanks. Any chance you could explain what the chainloader command is/does?

---

### Post by Roger Allott on 2008-11-23
Ah, just got this from the grub manual:

```
chainloader [‘--force’] file [Command]
Load file as a chain-loader. Like any other file loaded by the filesystem code, it can
use the blocklist notation to grab the first sector of the current partition with ‘+1’.
If you specify the option ‘--force’, then load file forcibly, whether it has a correct
signature or not. This is required when you want to load a defective boot loader, such
as SCO UnixWare 7.1.
```

Bugger knows what the fugg it actually means though!

---

### Post by Roger Allott on 2008-11-23
And I think this explains why the rootnoverify was suggested earlier:

> **rootnoverify** *device* [*hdbias*]
Similar to root, but don’t attempt to mount the partition. This is useful for when an OS is outside of the area of the disk that GRUB can read, but setting the correct root device is still desired. Note that the items mentioned in root above which derived from attempting the mount will not work correctly.

---

### Post by Roger Allott on 2008-11-23
First the good news - I haven't completely fugged up my system.

But then, I haven't exactly sorted it out yet either.

I booted up openSUSE and tried to open menu.lst in the standard file browser or text editor. No chance!

Then I saw that there's a superuser browser, so I opened that and pointed to the file. It opened, but I couldn't make any changes.

Then I looked around and found a prog that seems quite similar to Ubuntu's Start-Up Manager. So I started that.

There wasn't the option of manually editing the bootloader, but there was an option to get the prog to look at my system and recommend a re-write of menu.lst.

Jolly good, I thought, as that might find Ubuntu too.

Well, this is what it revised my menu.lst as:
```
# Modified by YaST2. Last modification on Sun Nov 23 23:19:57 GMT 2008
default 0
timeout 8
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6    resume=/dev/sdb5 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Original name: xen###
title XEN
    root (hd0,5)
    kernel /boot/xen.gz 
    module /boot/vmlinuz-xen root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6    resume=/dev/sdb5 splash=silent showopts
    module /boot/initrd-xen

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,5)
    chainloader (hd1,1)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,5)
    chainloader (hd1,3)+1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    rootnoverify (hd0,5)
    chainloader (hd0,2)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off  3
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Original name: Kernel-xen###
title Kernel-xen
    root (hd0,5)
    kernel /boot/vmlinuz-xen root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6    resume=/dev/sdb5 splash=silent showopts
    initrd /boot/initrd-xen

###Don't change this comment - YaST2 identifier: Original name: Kernel-2.6.22.5-31-xen###
title Kernel-2.6.22.5-31-xen
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.22.5-31-xen root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6    resume=/dev/sdb5 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-xen

###Don't change this comment - YaST2 identifier: Original name: Kernel-2.6.22.5-31-default###
title Kernel-2.6.22.5-31-default
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/usb-FUJITSU_MHT2080AT_PL_0-0:0-part6    resume=/dev/sdb5 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default
```

This has now given me three Windows options on my boot up, but none of them seem to point to the right place! And there's still no option to boot up Ubuntu.

And why it has added the bottom two is a bit of a mystery too.

---

