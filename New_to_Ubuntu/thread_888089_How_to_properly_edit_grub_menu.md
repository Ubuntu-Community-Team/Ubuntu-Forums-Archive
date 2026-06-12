---
title: "How to properly edit grub menu?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by manij on 2008-08-12
Hi, I have been running ubuntu for a year now.

I was trying to do a second HARDY install on the same computer in a second drive, which I can feel free to mess around.

The install went ok, but Grub doesn't recognize it. Here is the fdisk-l output
[B][I]
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Device Boot Start End Blocks Id System
/dev/sda1 1 3161 25390701 83 Linux
/dev/sda2 14180 19452 42355372+ b W95 FAT32
/dev/sda3 3162 3416 2048287+ 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84788478

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3187 25599546 83 Linux
/dev/sdb2 3188 3442 2048287+ 82 Linux swap / Solaris
/dev/sdb3 3443 5995 20506972+ 83 Linux
/dev/sdb4 5996 14593 69063435 b W95 FAT32[/I][/B]

The new istall which is not recognized by grub is in SDA1

I know in grub it is referred to as hd0,0

How do I descrivbve the rest of the info. The intrd image info? this bit here. I copied this from the web and obviuosly refers to Fedora

[B][I]title Fedora 9
	root (hd0,0)
	kernel /boot/vmlinuz-2.6.25-14.fc9.x86_64 ro root=UUID=6086d77f-107e-4a9d-b491-0fa6f25c9754 rhgb quiet
	initrd /boot/initrd-2.6.25-14.fc9.x86_64.img[/I][/B]

Mine is Hardy and hwo exactly do I look up the intrd info correctly?

Thanks

---

### Post by logos34 on 2008-08-12
Which is the Bios boot disk and which grub are you using, the previous or new one?

gksudo gedit /boot/grub/menu.lst

---

### Post by manij on 2008-08-12
> **logos34 said:**
> Which is the Bios boot disk and which grub are you using, the previous or new one?

gksudo gedit /boot/grub/menu.lst

I think my problem is that I'm still using the men.lst from old install on SDB1.

How do I fix this?

Bios boot disk? I was under the impression that the bios is on the motherboard:confused:

If I need to How do I fix this?

Thanks for your help

---

### Post by louieb on 2008-08-12
Use the **configfile** option to load your new installs GRUB menu.

Give what you said it will look something like this:

```

title            Load another menu.lst
configfile (hd0,0)/boot/grub/menu.lst

```

For more information search for configfile on this page [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") 

Another way is to **chainload** the 2nd install boot loader. That same page has good information on that too. 

I've used both   - works great. Good Luck.

---

### Post by logos34 on 2008-08-12
> **manij said:**
> I think my problem is that I'm still using the men.lst from old install on SDB1.

Then you want to use configfile entry, like louieb suggested. (or chainloader format, but for that you'd also need to write grub to the [first sector of the new ubuntu root partition]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader"), so the configfile is easier).


>  Bios boot disk? i.e. 'what disk are you booting from'--I say it that way so people will double-check their Bios hard disk boot priority, because grub does not always install on the same drive as ubuntu root, something that confuses a lot of people

---

