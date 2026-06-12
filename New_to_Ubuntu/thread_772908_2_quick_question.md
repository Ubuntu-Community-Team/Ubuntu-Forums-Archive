---
title: "2 quick question"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by has3o on 2008-04-28
Okay first question is there an aplication for ebuntu that allows you to acess the power saving setting my laptop charger will power my laptop but not charge it.

Second question when i first installed linux i tryed to do the partitioning with windows xp but i screwed up and end up losing it but kept linux.Is there any way to partition after the fact that i got rid or windows off my comp?

---

### Post by phr0ze on 2008-04-28
1. The only thing I have seen is System->Preferences->Power Management. 

2. What are you trying to do here? I would install gparted and see if it will let you do the changes you need. If anything just reformat the XP partition and use that as additional storage.

John

---

### Post by kwacka on 2008-04-28
I don't believe that your laptop battery not charging is down to Ubuntu - my view is that it is more likely to be down to a problem with your laptop's charging circuitry or a new battery is needed.

Regarding your second question, do you want to get rid of XP completely, or re-install?

If its getting rid of it, use gparted to expand your home partition (if you have a separate partition) or your ubuntu partition if there is only one.

If you want XP, just re-install. Unfortunately, XP will over-write your boot-manager (grub) so search here for instructions on how to reconfigure grub.

Alternatively, an easier route would be to re-install Ubuntu after you've installed XP.

---

### Post by crjackson on 2008-04-28
[QUOTE=has3o;4825470]Okay first question is there an aplication for ebuntu that allows you to acess the power saving setting my laptop charger will power my laptop but not charge it.QUOTE]

I just went through this with my personal laptop>  Laptop would run fine when plugged in but the battery wouldn't charge.

I ordered a new battery and that didn't fix the problem.  I was concerned the charging circuit in the motherboard was defective, but I decided to purchase a cheap charger from eBay just to see what would happen.

It was the charger all along.  The new charger quickly restored the battery to full charge while using the laptop.  It works like new now.  I'll bet you've got the same problem.

---

### Post by has3o on 2008-04-28
yeh i wanna re install xp i dont have a xp disk thou><

---

### Post by has3o on 2008-04-28
> **has3o said:**
> yeh i wanna re install xp i dont have a xp disk thou><
what can i do about this?Can i use my pin sin thing on my computer that certifies that its genuine windows or something?where can i download etc

---

### Post by Tatty on 2008-04-28
> **has3o said:**
> what can i do about this?Can i use my pin sin thing on my computer that certifies that its genuine windows or something?where can i download etc

You cant download an official version of XP from the internet.  Im sure you could find it in places but i would not trust those sources.

As long as you have a licence key for windows then all you need to do is get an XP home or pro (depending on your licence) CD from somewhere and re-install.

---

### Post by has3o on 2008-04-28
So would  a windows recovery disk would work i just have to input the sin and i just have to fix the grub so i can dual boot with both

---

### Post by has3o on 2008-04-28
> **has3o said:**
> So would  a windows recovery disk would work i just have to input the sin and i just have to fix the grub so i can dual boot with both
does anyone know of a site where i can get a genuine windows xp home dl for disk and can i make one of those disks from my other computer that has it? via copying files on a usb then burning on the computer with lunux?

---

### Post by phr0ze on 2008-04-29
It's not that easy. Even if you find a disk, your key may only work on a particular brand of disk (ie. DELL). You should contact your computer manufacturer or try to find a deal on ebay.

This is one of the problems with Windows. Many manufacturers don't give users proper disks and it's easy to have windows crash and then need the disk. I don't think anyone here will be able to legally help you.

John

---

