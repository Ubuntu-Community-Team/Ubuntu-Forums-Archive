---
title: "[SOLVED] Separate icons with each desktop"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-11
So I have 3 workspaces.
Is it possible to have different icons, like actual different desktops on each?
Not really going for the different wallpapers, just different icons.

---

### Post by lovinglinux on 2008-09-11
Probably not, because it is Nautilus that draws your desktop and thus placing the icons there, while workspaces are created by Compiz. For example, if you need different wallpapers in each workspace you have to disable the desktop in Nautilus and enable the wallpapers in compiz. When you do this you loose the desktop icons and the right-click context menu.

---

### Post by Elephantman5 on 2008-09-11
> **lovinglinux said:**
> Probably not, because it is Nautilus that draws your desktop and thus placing the icons there, while workspaces are created by Compiz. For example, if you need different wallpapers in each workspace you have to disable the desktop in Nautilus and enable the wallpapers in compiz. When you do this you loose the desktop icons and the right-click context menu.
So in essence I'd have to find a replacement for nautilus, which doesn't sound very appealing to me.
Ok, thanks dude.

---

### Post by Malac on 2008-09-11
I read somewhere that there is a patch/hack for nautilus which allows different desktop wallpapers, not sure about icons though, but I can't remember where I saw it. I'll see if I can find it again.

**_EDIT_:**
Not sure this will help but here's the link:
[http://forum.compiz-fusion.org/showthread.php?p=25796](http://forum.compiz-fusion.org/showthread.php?p=25796)

This one looks more promising:
[http://forum.compiz-fusion.org/showthread.php?p=30168#post30168](http://forum.compiz-fusion.org/showthread.php?p=30168#post30168)

---

### Post by Elephantman5 on 2008-09-11
> **Malac said:**
> I read somewhere that there is a patch/hack for nautilus which allows different desktop wallpapers, not sure about icons though, but I can't remember where I saw it. I'll see if I can find it again.

**_EDIT_:**
Not sure this will help but here's the link:
[http://forum.compiz-fusion.org/showthread.php?p=25796](http://forum.compiz-fusion.org/showthread.php?p=25796)

This one looks more promising:
[http://forum.compiz-fusion.org/showthread.php?p=30168#post30168](http://forum.compiz-fusion.org/showthread.php?p=30168#post30168)
I found this:
[http://voodoologic45.blogspot.com/2008/05/multiple-desktop-wallpapers-in-ubuntu.html](http://voodoologic45.blogspot.com/2008/05/multiple-desktop-wallpapers-in-ubuntu.html)

I like the setup, no icons w/e I'll get used to it.
But, the wallpapers are all stretched out. I set them to scale in the normal wallpaper GUI, and tried to find something in Compiz to do it, but didn't really find anything. 
Suggestions?
[[IMG]http://img134.imageshack.us/img134/1030/screenshotus6.th.png[/IMG]]("http://img134.imageshack.us/my.php?image=screenshotus6.png")

  found the option kind of hidden in the backgrounds menu of compiz, but they're only scaled down at login/logoff

---

