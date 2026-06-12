---
title: "BIOS won't boot from CD"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tapasray on 2008-05-16
I am trying to boot my Acer Aspire laptop, running Windows XP Home, from a CD image of Hardy Heron. When I insert the CD, I get some options. Choosing "demo & full install" leads to reboot. During reboot, I have to hold down the F2 key and enter BIOS setup, because Windows loads if I do not. 

In the BIOS setup, the hard drive boot option shown up as the default value. When I select the CD boot option and hit 'enter', nothing happens. 

I would really appreciate help with this.

Thanks in advance!

---

### Post by volkswagner on 2008-05-16
Acer usually has an option in bios to allow F12 boot option.  If you enable this, hit f12 during ACER splash screen.  You will need to hit f12 each time to change boot priority, as it will default to HD.

---

### Post by tapasray on 2008-05-16
Thank you so much! I'll try this out.



> **volkswagner said:**
> Acer usually has an option in bios to allow F12 boot option.  If you enable this, hit f12 during ACER splash screen.  You will need to hit f12 each time to change boot priority, as it will default to HD.

---

### Post by Anduu on 2008-05-16
Ok as my laptop is new to me I am not familiar with all of the specifics of my bios so I'll lay it out in general terms...

On my Acer laptop I enter the bios by hitting F2 at post.Once I am in there is a list for the boot order of devices.To change the order I have to highlight the device I want to boot from and by hitting F5 or F6(...I think...) it moves up or down the list.The change remains permanent.

Don't know if all Acer bioses are the same but hopefully this will help.

---

