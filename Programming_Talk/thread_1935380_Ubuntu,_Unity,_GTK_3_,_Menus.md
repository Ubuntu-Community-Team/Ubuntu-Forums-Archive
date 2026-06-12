---
title: "Ubuntu, Unity, GTK 3 , Menus"
date: 2012-03-04
forum: Programming Talk
---

### Post by anewguy on 2012-03-04
When using the Unity d.e., is there a way when writing your own programs in C and GTK to have menubars on the local window, instead of on the top bar of Unity? 

I have an app that doesn't run full screen and has a menu bar with "File" and "Help" submenus for now.  They don't show on the smaller window - only on the top Unity bar.

I'd like this app to be independent of desktop environment if at all possible.

Thanks in advance!
Dave ;)

---

### Post by MG&amp;TL on 2012-03-04
Well, you could use a bizarre widget set that the Unity thing doesn't recognize (but that doesn't work as you're using Gtk. Oops!)...or you could look at how libreoffice currently does it, as that breaks Unity global menu too. 

Why do you not want that to happen? Anyone who uses Unity "gets" global menus (and soon, HUD), and anyone who doesn't gets to see the menus?

---

### Post by anewguy on 2012-03-04
I want to put the menu right on the app window, like you would see when not using Unity.  The app I'm developing is going to be used on other distributions as well, so I'm trying to avoid ubuntu/gnome 3/unity specific coding.

Actually, I suppose I could code it all myself - vboxes/hboxes, show/hide entried, attach signal handlers, etc., is just the GTK menuing does make it a little easier to code ;)

Thanks!
Dave ;)

---

### Post by diesch on 2012-03-04
If you use the normal GTK menu bar your menu is shown in top panel if you run Unity and in your app window if you run an environment that doesn't support the global menu. So that's the way to get the menu where the user expects it.

In Unity you can disable the global menu for your program by setting the environment variable $UBUNTU_MENUPROXY to 0 (or anything else that is not "libappmenu.so"). So if for some reason you want to make sure that even in Unity your app shows the menu inside the app window just create a small wrapper shell script that unsets $UBUNTU_MENUPROXY and starts your program.

---

### Post by anewguy on 2012-03-04
> **diesch said:**
> If you use the normal GTK menu bar your menu is shown in top panel if you run Unity and in your app window if you run an environment that doesn't support the global menu. So that's the way to get the menu where the user expects it.

Yep - knew that - was just trying to find a way around it.  Your suggestion that follows sounds like it might do it - I'll have to try and see what I think.  I hadn't heard of that variable before.

> In Unity you can disable the global menu for your program by setting the environment variable $UBUNTU_MENUPROXY to 0 (or anything else that is not "libappmenu.so"). So if for some reason you want to make sure that even in Unity your app shows the menu inside the app window just create a small wrapper shell script that unsets $UBUNTU_MENUPROXY and starts your program.

Thanks - I'll consider this closed.

Dave ;)

---

