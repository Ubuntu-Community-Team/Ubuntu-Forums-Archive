---
title: "Quick Launch bar missing"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by slownewsday on 2008-11-29
HI Everyone:

New here, but recently after a restart, the quick-launch bar (or whatever may be the correct term for the bar with Applications, Places, System... and the system tray, etc.) has gone missing!  Now, all I have is an empty desktop with the hardy heron!  How can I bring that back?  I'm unable to do any real work on my v8.04 Ubuntu system now.

---

### Post by super.rad on 2008-11-29
Try pressing alt+f2 to bring up the "Run Application" menu and enter gnome-panel to see if that brings them back, if it does you could always add "gnome-panel" to your startup programs in System > Preferences > Sessions

---

### Post by slownewsday on 2008-11-29
Hi

Alt+F2 doesn't bring up anything.  What next?

---

### Post by Yuki_Nagato on 2008-11-29
Try pressing and holding:

"Control + Alt + backspace"

Backspace, not delete.

This should restart the "xserver" (the desktop and such.)  See what happens.

If the screen quits and appears to restart, try pressing and holding "Alt + F2" again.  That attempts to open the "launch application" menu.  If nothing happens, try "Control + Space."  That tries the GNOME-Do program.

---

### Post by endoubt on 2008-11-29
Right click the desktop and select "create launcher" and then fill in this information.

[IMG]http://rendicott.homelinux.org/help.png[/IMG]

that should give you a launcher on the desktop for the panel.

If you end up with a blank panel you can always right click the bar and select "Add to Panel" and then pick "Main Menu" or whatever else you want.

---

### Post by slownewsday on 2008-11-30
Thank you all!  I've got it to work, after getting gnome-panel, and changing the login option to a new session.

I had tried the Create Launcher, but that didn't do anything.

But thanks again!

---

