---
title: "Ocelot - lost launcher"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by 1eth on 2011-10-29
Just upgraded from Natty to Ocelot, no problem there, but have since been in compiz and have lost launcher. Can open files and file systems but cannot start programs (dont know where to find them!!)........ Any guide to open compiz or a terminal and how to restore launcher would be greatly appreciated.

---

### Post by llamabr on 2011-10-29
I'm not quite sure what your problem is. Maybe a screenshot?

So you're saying that when gnome starts you go no menus or anything?  What if you make a new user?  Does that user get anything on login?

---

### Post by 1eth on 2011-10-29
> **llamabr said:**
> I'm not quite sure what your problem is. Maybe a screenshot?
 
So you're saying that when gnome starts you go no menus or anything? What if you make a new user? Does that user get anything on login?
 
Top bar shows file, edit, view, Go, Bookmarks, Help. I cannot get side bar or launch programmes. I can open windows that give me the file system etc. but not knowing where in the file system programmes are held I cannot start compiz, so I cannot restore the launcher. Tried logging on as a guest and everything is fine, just need to fix my session, any ideas?

---

### Post by 1eth on 2011-10-29
> **llamabr said:**
> I'm not quite sure what your problem is. Maybe a screenshot?
 
So you're saying that when gnome starts you go no menus or anything? What if you make a new user? Does that user get anything on login?
 
 
Sorry Llamabar, didn't mean to be rude..... Thanks for the reply, you have helped as I now know I haven't totally goosed the laptop and think there is a way to fix what I've done wrong. Cheers Mate!!

---

### Post by qyot27 on 2011-10-29
The quickest solution would be to move the .config directory to another name (like .configbak) - or just delete it - and let the system regenerate it.  That will force the defaults across all programs which store their settings in that directory (which isn't everything, but it is most of the desktop-relevant stuff).

I'd recommend going about this from a LiveCD.

You might also find a use for the [classicmenu-indicator](https://launchpad.net/~diesch/+archive/testing) which will let you access a traditional menu if the Launcher disappears again (so long as the Unity panel doesn't also disappear or freeze, anyway).

---

