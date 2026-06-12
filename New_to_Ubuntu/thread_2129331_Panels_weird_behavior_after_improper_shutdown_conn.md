---
title: "Panels weird behavior after improper shutdown connected to projector"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by raequin on 2013-03-25
My laptop is running 12.04 (upgraded, twice, from 10.04).  Today the battery died while in standby?  Or something?  Anyway, it did not shutdown properly.  I don't know if that is germane, but wanted to include it just in case.  The next time I turned it on, it was connected to a projector on the VGA port.  That just showed a tan-ish screen and did not respond to keypresses (that I could see), so I turned it off by holding down the power button.  Okay, now I'm back home and when I started up the computer (not connected to a projector) the panels and junk are acting weird.  A screenshot is attached.

[ATTACH=CONFIG]240571[/ATTACH]

Previously, I only had one panel, at the top of the screen.  Now I have three (?) panels, two at top and one at bottom.  Plus there are duplicates of most of my applets on the top panel.  Furthermore, I can't remove any of the applets or the two new panels (right click does not present the option of "remove" now).  I would really appreciate any suggestions on how to fix this.

---

### Post by DuckHook on 2013-03-26
You have good instincts reporting all of the dirty shutdowns. This definitely might have an impact on your system stability, especially if system files were improperly closed or were corrupted. Firstly, log into another tty with <Ctrl>+<Alt>+<F1> and try:```
unity --replace
```If this doesn't work, then stronger medicine is needed, but this will reset your Unity settings to default:```
unity --reset
```<Ctrl>+<Alt>+<F7> will bring you back to your Unity session. Be sure to logout/login from Unity after each attempt. Do *not* use *sudo*. It is not needed and may confuse your system.

---

### Post by raequin on 2013-03-26
<code>unity --replace</code> added the Unity panel to the LHS, but did not fix the gnome panels
<code>unity --reset</code> crashed with Segmentation fault after several <code>compiz core - Warn: unhandled ConfigureNotify on ___ </code>

I'll try "turning it off and on again."

Edit: After trying both of those in another tty (and getting the Segmentation fault mentioned above) my desktop looks the same as in the attached image.  Well, after restarting it looks the same.

---

### Post by ibjsb4 on 2013-03-27
Can't you just **Alt + right click** and remove those extra panels?

Maybe reset those icons.

[http://askubuntu.com/questions/125662/how-to-reset-gnome-panel](http://askubuntu.com/questions/125662/how-to-reset-gnome-panel)

---

### Post by raequin on 2013-03-27
Oh, yeah!  (Though I have to use

alt + super + right-click

).  Thank you.

---

