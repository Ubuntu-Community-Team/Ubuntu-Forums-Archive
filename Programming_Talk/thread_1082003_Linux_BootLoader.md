---
title: "Linux_BootLoader"
date: 2009-02-27
forum: Programming Talk
---

### Post by Lekshmi on 2009-02-27
Is linux can work without a boot loader? Now there is boot loader,am asking about the previous days...

---

### Post by smani on 2009-02-27
Every OS needs a bootloader, it is just that i.e. in windows it is "invisible", that is it shows no text on the screen. You can also achieve the same in grub by setting the menu-timeout to 0, although I would not recommend it in case you need to boot from an older kernel for some reason.

---

### Post by PythonPower on 2009-02-27
smani is right but here's some extra information that may or may not be relevant/ useful. ;)

Basically when you power on a PC the computer searches in some order for bootable devices. Most often it gets to the hard disk in which case it needs to hand over execution to the operating system on the hard disk. So the BIOS copies the first 512 bytes on the hard disk into memory and jumps to the first position in that copied memory.

After this, the bootloader is responsible for loading the operating system using the [real mode]("http://wiki.osdev.org/Real_Mode") BIOS functions (or other methods).

As far as I know, pretty much every computer boots this way making bootsectors a necessity.

---

### Post by Frank Kotler on 2009-02-27
At one time, I used to boot to dos and start Linux with "loadlin". Still works, AFAIK. There's still a bootsector involved, but not a "Linux bootsector". I don't know if that counts as a "yes" or "no" to Lekshmi's original question.

To expand on what PythonPower was saying, the BIOS loads the first sector of the boot device (search order is settable in the BIOS "setup" program) into memory - at 0x7C00. Normally this is the "Master Boot Record" (MBR) of a hard drive. The MBR includes the "partition table" this is what you write to when you partition a disk with "fdisk" or other utility. One of the bytes in the partition table indicates which partition is "active" (bootable). The actual code in the MBR moves itself out of the way, reads the partition table, reads the first sector of *that* partition into memory at 0x7C00, and again jumps to that memory address.

This process can be interrupted by a "menu", and can then boot to something other than the "default" boot device. This is what we normally see when we boot up. (for certain values of "normal")

Best,
Frank

---

### Post by slavik on 2009-02-27
> **smani said:**
> Every OS needs a bootloader, it is just that i.e. in windows it is "invisible", that is it shows no text on the screen. You can also achieve the same in grub by setting the menu-timeout to 0, although I would not recommend it in case you need to boot from an older kernel for some reason.
windows bootloader menu = F8

even if menu timeout is 0, you can still press Esc in order to get it.

---

### Post by mmix on 2009-02-27
Yes, no bootloader but bios.
[http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)
[http://en.wikipedia.org/wiki/Linuxbios](http://en.wikipedia.org/wiki/Linuxbios)

---

