---
title: "Cairo Dock"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by sammas22 on 2008-06-17
i just installed Cairo Dock and i was messing with it and i set something way high and now when i open it lags my computer and does not show on the screen. i tried reinstalling it i did not work is there a way to reset the settings with out opening the app? or somehow open the settings without opening the dock?

---

### Post by friendofpugs on 2008-06-17
A quick way to work around it would be to remove it from your session. System > Preferences > Sessions and remove it from the start up list. Then restart your computer. Everything should boot up without it. This way you can use your computer as you figure out what to do. I'm partial to Awn myself. Good luck!
BTW, be patient with the forums. We've got some really smart people here that will get around to this eventually.

---

### Post by collinp on 2008-06-17
Well, try searching for "cario-dock" in Synaptic Package Manager, then right-click on the box next to it and click "Reinstall". That should reset the configuration file for Cario Dock to default.

---

### Post by fabounet on 2008-06-19
launch it in maintenance mode : "cairo-dock --maintenance", and change the value that is messing your dock. (by the way, what is it ?)
if it is not enough, try a "cairo-dock --safe-mode" and select another theme. (save your current one before if you want to keep it).

---

### Post by crl0901 on 2008-06-20
I have a question about Cairo-Dock, so I'm just going to post it in a thread that's already made instead of this one.

I can't figure out how to change the view.  I want to change it to curve.  I have the plugins installed, and I see the render plugin, and I can go in and view the properties of each of the views including curve, but I don't see anything on how to actually select curve at the view I want to use.  Thanks in advance.

---

### Post by fabounet on 2008-06-23
Curve is not yet in the package, it is only in the SVN.
I probably forgot to remove it fro the config panel ^_^
it will probably be integrated in the 1.6.1.

---

