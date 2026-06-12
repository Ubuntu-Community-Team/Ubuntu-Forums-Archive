---
title: "[SOLVED] Logitech S510 for Ubuntu 7.10"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-24
Ubunteros,

Has anyone been able to get the Logitech Model S510 keyboard working to the point where the F1 to F12  can be programmed or launch programs like Word Processor or Spreadsheet.

If so, I'd like to know how to make it work for me as well. I'm using Ubuntu 7.10....

Thanks!

---

### Post by germclown on 2008-11-09
Don't know if this really helps much, but I'm using 8.10 and the only ones I can't program are the alternates for F1-F4 (they don't even register on xev which is a well-known issue).

F5-F6 are set to undo/redo/print/save by default and can be remapped using the same method as any other key (I'm sure there's a guide somewhere around here). I like those on default since the icons are painted right onto the buttons and I don't like to confuse myself/others.

So IMO, your best bet is to use the alternates for F9-F12 as these register with xev (and so can be mapped easily). Since I'm not as hardcore as some of the others around here I just use the commands/bindings area in Compiz (general options --> commands) for all my keybinding spiffity since I'm not one to mess around with existing defaults.

I've also found that the "music notes" button is unassigned in Ubuntu, but does have a keycode. I've set that to my media player du jour, but it can be mapped to anything else by the usual methods.

Maybe someday that silly little s510 workaround patch will become a proper kernel feature, but not today.

---

### Post by SunnyRabbiera on 2008-11-09
yeh those function keys in logitech keyboards dont work that well under linux unless you do some heavy tweaking.
But this is more of a logitech issue, if they would actually provide ways for linux users to use these special keys then it would be better.
But if you need just pop some icons on your desktop for shortcuts or if you want a clean desktop there is a quick launcher for gnome called quick-lounge-applet... it does the job :D

---

