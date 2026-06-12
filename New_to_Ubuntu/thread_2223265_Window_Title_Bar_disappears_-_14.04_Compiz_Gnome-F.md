---
title: "Window Title Bar disappears - 14.04 Compiz Gnome-Flashback ..."
date: 2014-05-10
forum: New to Ubuntu
---

### Post by cwmoser on 2014-05-10
Ubuntu 14.04 64-bit, Gnome-Flashback desktop, Compiz

    Randomly I loose the Title Bar for my windows.
    Right before this happens, the Desktop flashes and blinks, then the Title Bars for all Windows disappears.
    The only thing I know to do is Ctl+Alt+Backspace to log out and then log back into Ubuntu.

    Is there a fix for this?

---

### Post by Drone4four on 2014-05-11
If I am not mistaken, Gnome 3's Flashback Desktop feature isn't compatible with Compiz - at all.  That's been the case since Gnome 3 was first released in April 2011.  Gnome 3 is Mutter only.  If you want wobbly windows, use either Unity or install Xfce or MATE. I also understand that the 0.9.x branch of compiz is really buggy.  For a smooth and stable experience with MATE or Xfce, you'll have to install 0.8.8 from source.  I wish someone would script the packages and post them to a ppa. Oh well.  I like Mutter.

---

### Post by cwmoser on 2014-05-12
I'm using the classic Gnome -- Gnome-flashback with Ubuntu 14.04.

Until a real fix comes I found this helpful if you loose your title bars:
- Ctrl + Alt + T to open a terminal window
- Enter:  metacity --replace &

This will restore the Window Title bars.

---

