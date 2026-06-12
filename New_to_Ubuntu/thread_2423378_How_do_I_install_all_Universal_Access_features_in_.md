---
title: "How do I install all Universal Access features in from Ubuntu in Lubuntu 18.04?"
date: 2019-07-22
forum: New to Ubuntu
---

### Post by lkether on 2019-07-22
I am mostly interested in the Cursor Blinking on/off option.

---

### Post by TheFu on 2019-07-22
My cursor doesn't blink, except inside GTK and Mozilla apps.  
Don't have any Qt apps. 
Standard X/11 apps do not have a blinking cursor. 

I don't use many GUI programs, so my direct knowledge is limited. GTK has this [https://developer.gnome.org/gtk3/stable/GtkSettings.html#GtkSettings--gtk-cursor-blink](https://developer.gnome.org/gtk3/stable/GtkSettings.html#GtkSettings--gtk-cursor-blink) in their manual.  Looks like there are settings somewhere to control it.  Perhaps gconftool or gconftool-2 could be used?

---

### Post by Dennis N on 2019-07-22
> I am mostly interested in the Cursor Blinking on/off option. 
There is a cursor blink option in LXTerminal. See: **Edit > Preferences**
As to the cursor theme (selected in Preferences > Customized Look and Feel), you can modify an existing cursor (like left_ptr) to make a blinking cursor by using the **xcursorgen** utility.
Some discussion of that is in this thread:
[https://ubuntuforums.org/showthread.php?t=2384798](https://ubuntuforums.org/showthread.php?t=2384798)

The animated left-pointer cursor described in post #8 of that thread is a blinking cursor (red-white) with 1/2 sec. blink duration.

---

### Post by him610 on 2019-07-23
I use blinking cursor in Xubuntu 18.04. In *xfce4-terminal*, one can go into Edit>Preferences>General, at the bottom of the page the shape of the cursor (Block, I-beam, Underline) can be set, as well as, a checkbox for Cursor blinks.

---

### Post by Dennis N on 2019-07-23
There are plenty of ready-to-use animated cursors at gnome-look.org that will catch your attention. Blinking cursors are just a subset of these. Have fun and check them out.

---

