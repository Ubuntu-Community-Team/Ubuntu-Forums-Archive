---
title: "Borked Install Help"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-10-05
I've been away from Ubuntu for a while, came back, and upgraded by alpha install; of course, that broke compiz. So... I figured I'd just do a complete reinstall. Downloaded the Oneiric daily, burned to USB, and the install got so far as the kernel and errored out. No worries, right? <b>Wrong</b>. Now, I get the "grub rescue>" prompt.

I'm a smart guy, so I just downloaded the Oneiric beta instead of the daily and the lappie won't boot from USB again, throwing-up the grub rescue prompt. Hmm... so, I download the SuperGrub2 iso, put in on a USB, pop that in, and... wait, what!? I get this:
```

GRUB loading.
Welcome to GRUB!

error: invalid arch independent ELF magic.
Entering rescue mode...
grub rescue>

```
Now I'm at a loss. I have multiple partitions--and distros installed on each--on my drive, but can't get into any of them. I've tried all the grub rescue prompt tricks, but nothing works.

Any ideas?

---

### Post by dino99 on 2011-10-05
how is formated this usb stick ?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by moore.bryan on 2011-10-05
FAT32... I've done this a million times before and never ran into *this* kind of problem. Come to think of it, my install never even got to install GRUB, so how could it be affecting anything?

---

### Post by ventrical on 2011-10-05
> **moore.bryan said:**
> FAT32... I've done this a million times before and never ran into *this* kind of problem. Come to think of it, my install never even got to install GRUB, so how could it be affecting anything?

Just giving you a bump here ! I know the feeling.  I know how to fix this .. but .. thing is .. right now I forget (honestly)!

If I remember soon I'll get  back or for sure someone else will.

---

### Post by lucazade on 2011-10-05
> **ventrical said:**
> Just giving you a bump here ! I know the feeling.  I know how to fix this .. but .. thing is .. right now I forget (honestly)!

If I remember soon I'll get  back or for sure someone else will.

so it is a bump just for the sake of it..

---

### Post by paul_in_london on 2011-10-05
Have you tried booting from a live (Oneiric) CD and chrooting into your borked install to install/reinstall grub?

(Beta 2 - [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)).

---

### Post by moore.bryan on 2011-10-05
> **paul_in_london said:**
> Have you tried booting from a live (Oneiric) CD and chrooting into your borked install to install/reinstall grub?

(Beta 2 - [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)).

That's just it... I can't even get a USB to boot. It's really weird, especially because the install itself never even got to the "install the bootloader" part.

---

### Post by ranch hand on 2011-10-05
But have you tried booting a Live CD?

---

### Post by ventrical on 2011-10-05
> **ranch hand said:**
> But have you tried booting a Live CD?


Yeah .. thats it I think.

---

### Post by effenberg0x0 on 2011-10-05
I lost an external HDD data in a situation like that - felt like killing myself. Instead of mounting the unit in another working linux PC while I could, I spent hours messing around with grub and rescue tools. It's easy to break things seriously using grub options and some tools supposed to recover broken partitions. 

So I can't stress enough that you should play it safe now. Do as other are recommending you to: While you can, either move this PC HDD to another Linux machine or use a LiveCD / LiveUSB at this PC, and try to boot and mount your primary disk and backup the data first. After you have your data secured elsewhere, then you go ahead with the fixing attempts.

Good luck.

Regards,
Effenberg

---

