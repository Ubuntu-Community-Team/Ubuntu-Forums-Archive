---
title: "Device for boot loader installation?"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by heartofwhite on 2012-04-13
Hey guys, 

So I am just ready to install Ubuntu but do not know what option to select for boot loader installation? /dev/sda5 is the drive that I have created to hold Ubuntu and this is an option. However, it is also giving me the option of selecting /dev/sda ATA Toshiba MK2046GS (200 GB). Which do I select and what does it mean?

Thanks guys.

---

### Post by sudodus on 2012-04-13
> **heartofwhite said:**
> Hey guys, 

So I am just ready to install Ubuntu but do not know what option to select for boot loader installation? /dev/sda5 is the drive that I have created to hold Ubuntu and this is an option. However, it is also giving me the option of selecting /dev/sda ATA Toshiba MK2046GS (200 GB). Which do I select and what does it mean?

Thanks guys.
If you want it to be used, you should install it into the very beginning of the drive, [COLOR="Red"]/dev/sda[/COLOR], and not to any partition (with a number, /dev/sda5 etc).

---

### Post by oldfred on 2012-04-13
The boot loader is just a small bit of code that the BIOS jumps to on the very first sector of the hard drive or MBR - master boot record.

You can only install a boot loader to anything other than the MBR if you have another boot loader in the MBR that allows multi-booting. Windows only boots Windows. The MBR actually has two parts, the boot code and a partition table.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Pictures, primarily Windows related
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by heartofwhite on 2012-04-14
Thanks for that, I got it solved!

---

