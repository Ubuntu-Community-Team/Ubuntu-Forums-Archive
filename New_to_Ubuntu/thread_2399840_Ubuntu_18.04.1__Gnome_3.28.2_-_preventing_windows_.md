---
title: "Ubuntu 18.04.1 / Gnome 3.28.2 - preventing windows overlapping the dock"
date: 2018-08-30
forum: New to Ubuntu
---

### Post by martinu2 on 2018-08-30
I'm new to Ubuntu, having used Windows.

I've found how to move the dock around, vary the size of the icons and auto-hide it - all from the Dock menu of Settings.

But is there way of configuring Gnome so the dock is excluded from being part of the window area that applications can use (as is the case in Windows) so applications don't overlap the dock.

It's a particular nuisance with the dock at the bottom of the screen (like the Windows taskbar) with applications such as Skype running, because part of the app is hidden by the dock - the area to the left of the "+" sign where you type Skype messages - and it seems that the Skype window can't be dragged to make it smaller top-to-bottom.

I don't want to have to auto-hide the dock, for the same reason that I don't auto-hide the taskbar in Windows - I want to see it all the time!

I've seen references to dconf-editor, but "sudo apt install dconf-editor" can't find it.


Is it relevant that I'm currently running Ubuntu as a guest OS in Oracle Virtual Box, while I'm away from home on my laptop - I'll install it properly on a spare PC when I get home.

---

### Post by monkeybrain20122 on 2018-08-30
I think the dash to dock extension has intelhide feature, but may not work in  VM

---

### Post by vanadium on 2018-09-02
> But is there way of configuring Gnome so the dock is excluded from being part of the window area that applications can use (as is the case in Windows) so applications don't overlap the dock.
This is how the dock already works now. Try maximizing a window. It will fill all available space excluding the dock. If you have a windows that is larger than the available space, like you show in your screenshot, then indeed it will not fit and be covered by the dock. You will need to reduce the size of the application window to make it fit. To also gain that screen space, you can intellihide the dock so it moves out when a window covers the area. 
If possible, you may increase the resolution of your screen. That way, much more screen real estate will be available.

---

