---
title: "urgent"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Roza on 2008-05-28
i was trying to log on every thing was just fine the log in screen appears i entered my user name and password and loged in but after few seconds my desktop screen froze without any reason!!! i rebooted several times but the same problem i can not beleive it crashed that simply any help would be great

---

### Post by sayakb on 2008-05-28
Which version are you using? You need to provide more details..

---

### Post by Scyron on 2008-05-28
Try booting into Safe Graphics Mode. I don't know the specifics offhand, but restart the computer, wait for a GRUB prompt counting down and telling you to press this-or-that button for the boot menu. Boot into safe graphics mode and see how things go.

If things don't go well and you need to recover files, get your hands on a Live CD and a thumbdrive. Run the Live CD: when you "test out Ubuntu" there should be an icon for your hard disk on the Desktop. Mount it with the right-click menu. Copy the files you want onto the Desktop, and then onto the thumb drive. That method saved me from major data loss once.

Good luck.

---

### Post by sayakb on 2008-05-28
I thinks there's a bit of correction there. GRUB doesn't provide an option for safe graphics mode. It can be though accessed from the LiveCD.

---

### Post by Roza on 2008-05-28
> **Scyron said:**
> Try booting into Safe Graphics Mode. I don't know the specifics offhand, but restart the computer, wait for a GRUB prompt counting down and telling you to press this-or-that button for the boot menu. Boot into safe graphics mode and see how things go.

If things don't go well and you need to recover files, get your hands on a Live CD and a thumbdrive. Run the Live CD: when you "test out Ubuntu" there should be an icon for your hard disk on the Desktop. Mount it with the right-click menu. Copy the files you want onto the Desktop, and then onto the thumb drive. That method saved me from major data loss once.

Good luck.

hi there thanx for replay i did tried to use the live CD but it refused to boot even after changing the BIOS setup!! so wired isn't it??

---

### Post by kpkeerthi on 2008-05-28
> **Roza said:**
> i was trying to log on every thing was just fine the log in screen appears i entered my user name and password and loged in but after few seconds my desktop screen froze without any reason!!! i rebooted several times but the same problem i can not beleive it crashed that simply any help would be great

It could be one of your startup programs. The startup program entries are stored in ~/.config/autostart folder. Boot in recovery mode from GRUB and move the autostart files to a temp folder. Now see if you can login in regular mode.

---

### Post by kesman on 2008-05-28
1. Don't do multiple posts, just one for your problem on the appropriate subforum

2. Give more information on your problem. "PLX HELP MY PC'S BROKEN!!11" isn't good enough.

---

### Post by Roza on 2008-05-28
> **kesman said:**
> 1. Don't do multiple posts, just one for your problem on the appropriate subforum

2. Give more information on your problem. "PLX HELP MY PC'S BROKEN!!11" isn't good enough.

1- i did my first post in the general help section but i got no replay then i thought the beginner section would be appropiate most
2-you are right i think that title is much better but i did not think too much about title thanx any way

---

