---
title: "Can't boot Ubuntu after installing vista"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by jezebel on 2008-10-05
Hi - I hope someone can help me.

I have XP and Hardy Heron on my C drive; well, I recently (yesterday) installed Vista on a separate drive (G). It installed well, but when I boot up, I only get the option for XP or Vista. I tried to add Ubuntu in VistaBootpro program, and it adds the entry, but thinks it's a Windows OS and can start in Ubuntu. 

At this point, I cannot even access my Ubuntu... 

Can anyone help me get my machine to triple-boot??

Thanks in advance.

---

### Post by shifty_powers on 2008-10-05
you need to reinstall grub, vista overwrites it.

have a look [here](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

---

### Post by jezebel on 2008-10-05
Thanks for the quick reply; I've looked at that link, but I can't get into Ubuntu at all.

---

### Post by xreaper on 2008-10-05
Have you reinstalled grub?

---

### Post by shifty_powers on 2008-10-05
that link tells you how to do it from the *live cd* :D

download and burn the livecd, boot from it and follow the instructions...

---

### Post by jezebel on 2008-10-05
Oops - thanks, I should read more carefully:)

I'm going to give that a try now.

Just one thing - I just noticed that my Ubuntu partition says it's a RAW file system... Don't know if this means it's toast, but I'll give the grub a try.

---

### Post by SuperSonic4 on 2008-10-05
It could well be.

EasyBCD is meant to be a good tool for changing vista's bootloader too

---

### Post by shifty_powers on 2008-10-05
good luck :D

---

### Post by jezebel on 2008-10-06
I can now boot into Ubuntu again!! And I haven't lost access to XP or Vista either, woo hoo!

Shifty - I started following the tutorial that you linked me too; when I got to the part that said, "Be very careful" and that I had to know which drive Ubuntu was on, it scared the crap outta me. (I'm a bit nervous working under the hood).

But anyway, I ventured forth, and once the Live CD was running, I realized I had full access to all the files on the Ubuntu partition. So...I just copied menu.lst from the boot/grub directory, copying to a clip drive. 

Then I rebooted in Vista, downloaded EasyBCD (thanks, Super Sonic), and followed step #5 of this tutorial here:[ http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5")

It ain't beautiful, but it works! Now I can boot into any of my three systems. 

Thanks again.

Thanks

---

