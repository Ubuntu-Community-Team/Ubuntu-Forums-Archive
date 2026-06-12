---
title: "Access to gnome-keybinding OSD"
date: 2008-05-29
forum: Programming Talk
---

### Post by Toufik on 2008-05-29
In gnome, using Preferences > Keyboard Shorcuts (= gnome-keybindings-properties), you can assign a key to an event. For instance, when you press the volume down key, you get a nice OSD on the screen.

I'd like to write some code that would be able to prompt the OSD directly, however, I search a bit but I didn't even find which is the relevant package (gnome-keybindings-properties only writes in gconf, I'm looking for the guy who reads it :) ).  To be more precise, I'd like to find the header files (or the piece of code) that allow me to prompt this OSD from a home-made program.  Currently I'm using xosd but this is text only and not really beautiful (and gnome-osd is not better)

Thanks

---

### Post by Channon on 2008-06-06
Ah - I've been looking for this too.  Don't know if this thread might be of interest:

[http://ubuntuforums.org/showthread.php?t=165073]("http://ubuntuforums.org/showthread.php?t=165073")

---

### Post by Toufik on 2008-06-11
Thanks for the answer. However acpi_fakekey is buggy on my laptop (vol down works, but vol up don't, and brightness up/down neither), that's the reason I want to write a home made code to handle correctly (already done) and nicely (I'd like the OSD) this kind of events

---

