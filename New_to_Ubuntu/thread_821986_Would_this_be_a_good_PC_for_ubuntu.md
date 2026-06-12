---
title: "Would this be a good PC for ubuntu?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by DBrocks on 2008-06-07
Hey guys. The story is, My space is very limited in my house. So, I found this nifty little Mini-PC for about 200 bucks. Before investing in it, I want to know if this pc would be able to handle ubuntu. Thanks!

~Dan

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856101065&Tpk=shuttle%2bmini%2bpc](http://www.newegg.com/Product/Product.aspx?Item=N82E16856101065&Tpk=shuttle%2bmini%2bpc)

---

### Post by ibuclaw on 2008-06-07
Shuttle KPC's already ship with Foresight Linux installed on them.

[http://us.shuttle.com/KPC/](http://us.shuttle.com/KPC/)

Look into "**Features**" and read the "**Operating System**" paragraph.

So the answer would be "Yes" :)

Regards
Iain

---

### Post by avtolle on 2008-06-07
[http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236) *might* help answer your question.

---

### Post by stmiller on 2008-06-07
In general, any thing Intel is best at the moment. Intel releases specs for all of their hardware so that Linux drivers can be created and included by default in the Linux kernel.

So look for Intel chipsets, Intel wireless, Intel video (or Nvidia) and you will be all set.

---

### Post by DBrocks on 2008-06-08
> **tinivole said:**
> Shuttle KPC's already ship with Foresight Linux installed on them.

[http://us.shuttle.com/KPC/](http://us.shuttle.com/KPC/)

Look into "**Features**" and read the "**Operating System**" paragraph.

So the answer would be "Yes" :)

Regards
Iain

Yeah. I was just making sure that Foresight wasn't specefically designed for that PC, and that Ubuntu, therefore wouldn't work. Lol. Thanks alot guys! Looking forward to this. Then Im picking up a 22" windescreen monitor for the Shuttle! Score! Thanks!

~Dan

---

### Post by the8thstar on 2008-06-08
Don't frget to add the CD-ROM drive...

---

### Post by DBrocks on 2008-06-08
No room for a CD-ROM drive. However, for the Ubuntu install, Im just going to leave the PC open with an internal CD drive lying on my desk. :lolflag: I'm much to cheap to go buy an external CD drive. :)

---

### Post by bruce89 on 2008-06-08
> **stmiller said:**
> In general, any thing Intel is best at the moment. Intel releases specs for all of their hardware so that Linux drivers can be created and included by default in the Linux kernel.

I was under the impression that AMD/ATI did similarly. The only graphics card lot not to bother now are Nvidia.

---

### Post by mivo on 2008-06-08
It already comes with a Linux variant, but if you want to install Ubuntu on it, there shouldn't be any problems. Personally, I'd probably go with Xubuntu. I use Ubuntu on desktop, but I have been trying to find a nice distro for my laptop which has similar specs to the mini PC you're looking at. Especially with the 512 MB RAM, a fully blown Gnome or KDE are not really the best choices (in my opinion). It's not that you can't use them, but I found Xubuntu (which uses Xfce) to be "snappier" and more responsive.

But anyway, any Ubuntu flavour will work, if you don't want to use the included Forsight Linux (never heard of it before).

---

### Post by the8thstar on 2008-06-28
You'll get to about $459 before S+H and tax to get something decent. Opt for a Mac Mini instead.

---

### Post by capkid2a on 2008-10-08
> **DBrocks said:**
> No room for a CD-ROM drive. However, for the Ubuntu install, Im just going to leave the PC open with an internal CD drive lying on my desk. :lolflag: I'm much to cheap to go buy an external CD drive. :)

Just wanted to add this in case anyone was looking for easy instructions on how to load Ubuntu on a KPC with a USB drive:

Use [Unetbootin]("http://unetbootin.sourceforge.net/") to prepare your USB drive

Put drive in computer.

Power up computer.

Press <del> to get to BIOS set-up.

Under "Integrated peripherals" make sure USB drive is set-up to be read as an HDD.

You might have to save and reboot.

Go to BIOS set-up again.

Under "Advanced BIOS Features --> Hard Disk Boot Priority" make the USB-HDD the first by selecting and using PgUp.

Restart computer.

Ubuntu 8.0.4 should install in a few minutes!


The mistake I was making over and over was thinking that the USB Drive would be recognized as a USB-HDD.  I was putting USB-HDD as the "First Boot Device" in the "Advanced BIOS Features".  That does not work.  You have to set the "First Boot Device" as [Hard Disk] and set up the Hard Disk Boot Priority as noted above.

---

### Post by Nxion on 2008-10-08
This post was very helpful for me. I think I have made my decision for a new desktop 
:)

---

