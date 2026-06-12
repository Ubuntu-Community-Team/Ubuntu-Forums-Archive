---
title: "Error 21 external dual booting"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by bryce11 on 2008-05-31
A while back I installed ubuntu on an external HD in the interest of dual booting. Like many people i received the Grub loader stage 1.5 Error 21 problem when trying to boot without the external HD plugged in. I am finally getting around to trying to fix it. It is annoying to have to drag my external around everywhere just so I can boot.

I've read several forums and the general consensus is to install ubuntu internally and not bother with installing it on an external drive. That would make using ubuntu easier but it still doesn't fix my current problem. I can't boot without the external drive regardless of what is installed internally. I have tried changing the bios options to boot from the internal HD first, but that doesn't help. How do I fix this problem? Would uninstalling Ubuntu fix it? If so how do I uninstall it?

My current setup: Dell Inspiron 1520 laptop
Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00ghz
2 GB RAM
32 bit OS
Interal HD: Windows Vista Business
External HD: Ubuntu 8.04

---

### Post by meindian523 on 2008-05-31
What you should do is install Grub to the MBR of your internal HDD.

---

### Post by issih on 2008-05-31
Never had this exact problem myself, but I would have thought that a good solution would be to set things up as follows:

Install grub onto the external hard disk, set up so it can boot from there to ubuntu on the external or windows on the internal disk.

Remove grub from the internal disk and replace the windows boot loader.

Set bios boot order so the external is tried first, and if its not there it falls through to boot the internal.

If you cn set your boot order up like that, the laptop should just boot as it used to straight into windows, but if the external is plugged in you will get the grub menu and a choice.

Not simple maybe, but that sounds most likely to be livable with for you

---

### Post by logos34 on 2008-05-31
> **issih said:**
> ...Install grub onto the external hard disk, set up so it can boot from there to ubuntu on the external or windows on the internal disk...

I agree with Issih, but remember to also change the groot and root lines in /boot/grub/menu.lst to **(hd[COLOR="Blue"]0[/COLOR],?)** because as soon as you make the external drive first in the Bios hard disk boot order it becomes drive (hd0). 

Actually, there's another way that I often recommend: Use windows bootloader to chainload grub (=> [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux"))

I'm no fan of Microsoft but I think it makes sense in this case to use it.

(if you go the latter route you shouldn't have to edit menu.lst because it will remain second drive in bios order, (hd1)

---

