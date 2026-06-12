---
title: "[SOLVED] How Do I Create a Shortcut to an Application in the Menu?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-13
I was reorganizing my menu and somehow I lost some items (EnvyNG and Cairo-Dock). How does one replace lost launchers in gnome's menu? In XP I just created shortcuts to the executable and dropped it in the menu. In gnome I don't even know where the executables are. A related question... whenever I install an appl. in XP, a menu item appears. In Ubuntu it may or may not. So if I have an application installed and want a shortcut to it in the menu, how do I create that? Thanks!

---

### Post by Squish on 2008-09-13
just go to applications, find the program you want to create a launcher for, click, hold, keep holding, and pull it slowly to the right and drag it onto the dock.

To create a shortcut, right click applications, then go to edit menus. Then you can add new launchers, etc...

---

### Post by bobsmith2 on 2008-09-14
Thanks Squish. As a very new Linux user (and long-time MS user -since DOS 3.2), I had trouble finding the applications (or links to them). Since they disappeared from my menu, I didn't know where to go. So I'll report what I did in case it helps someone else. I now see that Ubuntu has a number of places in the file system where such links can be found (like usr/share/applications). By right clicking on those and selecting Properties, I was able to find the correct launch command to enter into the new menu item (and it isn't always just the path... cairo-dock was just "cairo-dock"). 

EnvyNG's menu entry was created with the generic launch icon, and finding a way to change that icon was a struggle. I finally found where the icons were located: /usr/share/envy/pixmaps   There were other places as well (like /usr/share/icons/hicolor/...). Once I found them it was just a matter of linking the menu item to the correct icon.

Another thing I noticed that was tripping me up... when I navigated from the menu item's "Properties" and then browsed for a new icon (located at /usr/share/envy/pixmaps) the file list was empty. As an ex-XP user, I expected that when I clicked on the "pixmaps" folder that I'd see a populated file list... in Windows I always expected to see the list of files in whatever folder I'm clicking on, unless there were none of the correct type. So I just figured that there must be nothing in that "pixmaps" directory that I could use to replace an icon (even though I KNEW there were .png files in there), or that it was a permission issue. Otherwise, why would the window be empty? I finally tripped on the fact that one must click "open" to get another window that's populated with a bunch of icons to choose from. Kind of hard to explain, but once I realized that it was an easy matter. Just enough different to trip up a rookie, but now I'll remember it.

---

### Post by t0p on 2008-09-14
If you want to edit your Applications menu - by removing entries, or by adding them - you can do so by right-clicking on the top panel where it says Applications.

---

### Post by bobsmith2 on 2008-09-14
> **t0p said:**
> If you want to edit your Applications menu - by removing entries, or by adding them - you can do so by right-clicking on the top panel where it says Applications.

Thanks t0p. Yes, editing the menu is very easy if the app you want is in the list where it can be checked or unchecked. I needed to browse the file system to add one to the list, and then change its icon.

---

### Post by Squish on 2008-09-15
> **bobsmith2 said:**
> Thanks Squish. As a very new Linux user (and long-time MS user -since DOS 3.2), I had trouble finding the applications (or links to them). Since they disappeared from my menu, I didn't know where to go. So I'll report what I did in case it helps someone else. I now see that Ubuntu has a number of places in the file system where such links can be found (like usr/share/applications). By right clicking on those and selecting Properties, I was able to find the correct launch command to enter into the new menu item (and it isn't always just the path... cairo-dock was just "cairo-dock"). 


usr/share/applications eh?

Hey, I learned something new.

Thanks bru:guitar:

---

