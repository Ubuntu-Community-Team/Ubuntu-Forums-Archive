---
title: "Nothing appearing on the desktop"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by WVSteelers28 on 2008-09-17
Hi all.

Last night I was working on my laptop which has Ubuntu 8.04, everything was working fine, and it shut off just fine no problems.  Well, I booted up this evening to do some work, well it boots up like normal, but when it loads the desktop nothing appears! My two panel bars don't show up at all, but I'm able to right-click and choose items in the list.  Plus, I'm able to navigate through everything, just nothing on my desktop (panel bars which has my menus).  Would GREATLY appreciate help.  

Thanks.
WVSteelers28

---

### Post by kjohansen on 2008-09-17
open a terminal and type nautilus. You may have somehow removed nautilus from autorunning.

you also could have taken desktop control away from nautilus.  you can change that by typing gconf-editor in a terminal and finding the settings for nautilus.  it will be something like control desktop...

---

### Post by Shazaam on 2008-09-17
Have you tried a reboot?
Hold down ALT+SysRq(PrintScreen) type...
```
reisub
```

---

### Post by WVSteelers28 on 2008-09-17
kjohansen, it appears that everything is ok with nautilus.
Shazaam, I've tried multiple reboots

Thanks for the quick replies.

---

### Post by Shazaam on 2008-09-17
This will temporarily get a panel back...
Right-click your desktop, choose "Create launcher". In the command box input
```
gnome-panel
```
Then read these-
[http://ubuntuforums.org/showthread.php?t=772229](http://ubuntuforums.org/showthread.php?t=772229)
[http://ubuntuforums.org/showthread.php?t=840105](http://ubuntuforums.org/showthread.php?t=840105)

---

### Post by Tux Aubrey on 2008-09-18
This is happening to me every week or so on a previously stable set-up.  I use another WM (enlightenment) for my own user account but my wife still uses the Ubuntu/Gnome desktop.  She will log in to a blank desktop - no background and no icons but with the panels/menus still working.

I have fixed this (several times now!) by using gconf-editor and tweaking the applications>nautilus settings.  The weird thing is that the correct settings are usually set ("show desktop icons", etc) but they have to be unchecked and checked again for the desktop to return.

I have no idea what is triggering the change in the first place.

---

### Post by WVSteelers28 on 2008-09-19
Thanks everyone.  Shazaam, the first linked fixed most of everything.  Just had to go back and install a couple other things, but everything is good now.

---

