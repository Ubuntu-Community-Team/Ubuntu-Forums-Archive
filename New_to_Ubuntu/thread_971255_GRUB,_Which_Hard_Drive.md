---
title: "GRUB, Which Hard Drive"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by daniell59 on 2008-11-04
I have been getting different opinions on this.
Here are the facts.
2 hard drives
One has Vista installed on it.
The other is empty.
I want to install Ubuntu on the empty drive.
Which drive do I install GRUB on?

---

### Post by bumanie on 2008-11-04
If you use a live cd, in preference to the alternate cd, grub should set itself up correctly - off a live cd the installer sets up automatically. Essentially what grub does in a dual boot such as you are proposing, is to put its 'root' boot files on the second hard drive so that it can boot ubuntu. Grub also puts a reference to the vista bootloader and if you choose to boot vista, grub hands the job of booting vista over to vista's bootloader.

---

### Post by Miljet on 2008-11-04
It would be best to install GRUB on the disk that contains Ubuntu, but it needs to be the disk that is booted first.

---

### Post by daniell59 on 2008-11-04
I have tried  Ubuntu 8.10 for a couple of days from the CD. So far I like what I see. I really want to install it, but being a newbie. I have my concerns. I do not want to adversely affect the Vista which I also like.

I have Vista installed on a 250 GIG hard drive.

The other hard drive is 160 GIG and is empty.

Someone please tell me what to do, so that I can get going.

Thanks

---

### Post by bumanie on 2008-11-04
> **Miljet said:**
> It would be best to install GRUB on the disk that contains Ubuntu, but it needs to be the disk that is booted first.

I don't believe the above is correct - it is well known that in a dual boot situation that windows works best from the first partition of the first drive. Grub can boot linux from any partition on a hard drive, even logical partitions - windows can't boot from within a logical partition. It is also often problematic (but not impossible) to get windows to boot off a secondary hard drive without editing /boot/grub/menu.lst by adding 'map' commands. The live cd installer will do it correctly 99% of the time.

---

### Post by bumanie on 2008-11-04
There are multiple tutorials and various ways of achieving a dual boot. I prefer to choose manual at the partitioning stage (but there are other ways) and opt for a 10gb/ a swap of 1-2gb and /home as large as I want. When installing, make sure you only format the second hard drive. Ubuntu will 'name' your hard drives differently to how windows does - your present drive (with vista) will be /dev/sda and the second drive /dev/sdb. You can do it another way if you wish - it's up to you; there is no right or wrong way. Just make sure you don't make any changes to /dev/sda and everything should be fine. [Here's an apc.mag tutorial]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") - they do it different than I do - but as I said, there is no right or wrong - it comes down to personal choice. Look at other tutorials too and then choose which one you feel most comfortable with.

---

