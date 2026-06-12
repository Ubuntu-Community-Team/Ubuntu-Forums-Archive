---
title: "Where is my desktop (Ubuntu 8.04)"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by carusoswi on 2008-09-10
Every fifth time or so, when I boot up Ubuntu 8.04, the result is a blank desktop.  That doesn't really bother me other than knowing that something is not right.  Right clicking my mouse yields no response, either.  Normally, a right click brings up a menu that includes, among other things, cleaning up by name which organizes my icons.

When a blank desktop appears, the screen is just solid orange as if there were nothing on my desktop at all.  I can click the menu at the top of the screen to open applications, etc, but nothing from the desktop.

The only way I have found to restore it is to reboot.

Has anyone else experienced this and is there some better way to fix it?

Thanks.

Caruso

---

### Post by SunnyRabbiera on 2008-09-10
I think this is an error in gnome of some kind and not really the entire OS.
It happened to me every so often, probably due to something stupid I did (like run a lot of memory dependent apps)

---

### Post by carusoswi on 2008-09-11
> **SunnyRabbiera said:**
> I think this is an error in gnome of some kind and not really the entire OS.
It happened to me every so often, probably due to something stupid I did (like run a lot of memory dependent apps)

Thanks for the reply, but I'm not running anything.  Computer is off (in most cases has been off for 12 hours or so).  I turn it on, no desktop.  Have to reboot in order for the desktop to re appear.

Caruso

---

### Post by Znupi on 2008-09-11
You can probably just log out and back in again and it will be fixed (so you don't have to wait for it to completely reboot).

The problem is (I think) caused by nautilus, because nautilus handles the desktop. Try opening a folder (Places -> Home Folder), see if that restores the desktop.

Also, check the status of the "/apps/nautilus/preferences/show_desktop" key in gconf-editor and maybe try to turn it toggle it a few times. Maybe even as root (for me, as normal user, i can set the key to false, if i try to set it to true, nothing happens. if i'm root, i have to set it to true and then open some folder and it works).

---

### Post by gvartser on 2008-09-11
"CTRL + ALT + BACKSPACE" 
could do the trick.

/g

---

### Post by gvartser on 2008-09-11
"CTRL + ALT + BACKSPACE" 
could do the trick.
That will reset you x session.

/g

---

### Post by carusoswi on 2008-09-12
CTRL/ALT/BACKSPACE does do the trick.  I'm not concerned so much about restoring the desktop as I am concerned about the underlying issue that might be causing this problem . . . never had this in 7.10.

Thanks for the replies.

Caruso

---

### Post by m.lilja on 2008-09-12
I have this problem as well, although running 8.10..

Desktop is completly blank (only background color showing), ctrl+alt+del works - I get the "logout-dialog".

restarting X doesn't help.

Anyone?

---

### Post by Znupi on 2008-09-12
Try this:

> **Znupi said:**
> Also, check the status of the "/apps/nautilus/preferences/show_desktop" key in gconf-editor and maybe try to turn it toggle it a few times. Maybe even as root (for me, as normal user, i can set the key to false, if i try to set it to true, nothing happens. if i'm root, i have to set it to true and then open some folder and it works).

Try setting the key to true (if it's not) and restarting X or the computer.

If that's not the problem, then I don't know.

**Edit:** Also note that by default an Ubuntu installation **has** a blank desktop (i.e. no icons). Try putting some file on the desktop by dragging and dropping from a folder. See if it appears. You can play around with the keys in /apps/nautilus to get it to show drives on the desktop, the home folder, network drives, etc.

---

