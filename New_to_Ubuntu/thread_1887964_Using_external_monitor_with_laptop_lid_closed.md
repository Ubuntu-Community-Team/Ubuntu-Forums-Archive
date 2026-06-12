---
title: "Using external monitor with laptop lid closed"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by greg.fordyce on 2011-11-28
I am trying to figure out how to do this on 11.10. I am using the nvidia-current drivers. Since gnome has been removed in 11.10, I installed dconf-tools package and ran dconf-editor, but can't find the settings for the laptop lid button. Can someone point me in the right direction?

Thanks in advance,

Greg

---

### Post by Corporation on 2011-11-28
Click the battery in Unity toolbar > power settings > When I close the lid > Do nothing.

---

### Post by nothingspecial on 2011-11-28
Hi Greg,

Welcome to the forums :)

If you have a question that you can't find the answer to, rather than digging up an old thread and bumping it to the top, create your own thread.

Thanks

---

### Post by greg.fordyce on 2011-11-28
> **Corporation said:**
> Click the battery in Unity toolbar > power settings > When I close the lid > Do nothing.

Thanks Corporation, I tried that first, but it doesn't work. As soon as I close the lid the external monitor goes off with the "do nothing" option selected. Seems the "do nothing" option still does something. :confused: The laptop is an Asus X59GL and this worked fine with Fedora 11.

---

### Post by greg.fordyce on 2011-11-28
I've found a work around, disable Unity and roll back to Gnome as per the sticky in this forum. Then using this thread, [http://ubuntuforums.org/showthread.php?t=1307857](http://ubuntuforums.org/showthread.php?t=1307857) (that nothingspecial edited out of my original post because it wasn't relevant :rolleyes:) I installed gconf-editor package and ran this command in a terminal.

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"


I can now close the lid on my laptop keeping the external monitor on. If anyone can tell me how to do the same thing in Unity I'll give it another go, but for now I will just stick with Gnome.

Greg

---

### Post by greg.fordyce on 2011-11-30
I figured this out. Corporation was right about the power settings, but the monitor still goes blank when closing the lid. Wiggle the mouse and it comes back on. :shock:

In Fedora 11, that was previously installed on this laptop, never blanked the screen when closing the lid.

---

