---
title: "Changing Volume/Brightness through a Panel Dropdown"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by Birchle on 2011-09-29
If I click on one of the panel items (either a menu option on the left, or one of the indicator icons on the right), so long as the resulting dropdown is still open, I am unable to use the keyboard buttons to change the volume, brightness, and possibly more -- those are the only two I've found so far.  Confusingly, even if the open menu is the volume menu, I still cannot change the volume using the volume buttons.

Is this intentional?  It seems like the menus block popups from appearing/changing, so does that in turn prevent the button-changes, since there is no on-screen feedback without the popups?  If that is in fact the logic behind it, it seems a bit strange.  Granted, the menus aren't typically open for long, but that doesn't seem like a valid reason to be blocked from affecting minor changes to my system.

If it is not intentional, is it a bug, or an option?  If an option, where can I find it to change it?

I'm on Ubuntu 11.04 64-bit, with the "Classic (no effects)" desktop theme (which I believe is basic Gnome).

---

### Post by cariboo on 2011-09-30
If you have one of the indicator menus open, it's assumed you are going to adjust them using the mouse, if you use the keyboard keys to make adjustments a different indicator pops up showing the level change.

---

### Post by Birchle on 2011-09-30
I guess you could argue that logic for the volume menu and volume buttons...  But it still doesn't seem reasonable that having the volume menu, or the time, or email, or wireless open should block the brightness from being changed.  Especially since (at least by default) there is no brightness menu; it can only be changed with the keyboard.  So to assume that having one random menu open means you're going to change anything/everything with the mouse doesn't follow through at all.

Is there a way to change settings to allow keyboard-based changes regardless of if menus are or aren't open?

---

### Post by Birchle on 2011-10-01
The situation gets even stranger.

I rebooted the computer, and this time, I can change the brightness if a menu is open.  I still can't change the volume while a menu is open, however.

But what's more, with a menu open, the brightness only changes by one level, rather than by the two (I'm pretty sure I have [this]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/207473") bug, or at least something with the same result) I normally see.  Changing by only one level is wonderful, of course, and clearly the intended outcome of a single button-press, but how can *an open menu* possibly be causing that difference?  And, if the open menu is somehow blocking one of the button-press-recognizers for brightness, is that also why volume can't be changed when a menu is open, because volume uses the same recognition system as whatever the blocked brightness uses?

---

