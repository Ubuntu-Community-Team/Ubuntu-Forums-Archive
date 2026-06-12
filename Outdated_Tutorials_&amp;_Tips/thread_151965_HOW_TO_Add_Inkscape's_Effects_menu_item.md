---
title: "HOW TO: Add Inkscape's Effects menu item"
date: 2006-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by BobSongs on 2006-03-28
Inkscape is very versatile but it might be fairly soon before you reach the limits of what it can do. So let's add a few extra tools with some cool features to raise the productivity levels.

I'm going to assume you've got Inkscape installed. If not, download Automatix and get installing.

Now let's activate the extra effects.

[LIST=1]
[*]Shut down any running copy of Inkscape.
[*]Open an instance of Nautilus at your home folder (Places &#8594; Home Folder).
[*]When Nautilus opens cause it to display hidden folders (View &#8594; Show Hidden Folders).
[*]The right-hand side of Nautilus should fill with a few more folders, folders that begin with a dot. Scroll down until you locate **.inkscape** and double click it to open it.
[*]Inside that folder should be a file called **preferences.xml**. Edit that file with your favorite text editor or the Ubuntu default editor called **Gedit**.
[*]Scroll down in the file to near the bottom. There should be an entry that looks like:```
<group
id="extensions"
show-effects-menu="0"
org.inkscape.print.ps.bitmap="0"
org.inkscape.print.ps.resolution="72"
org.inkscape.print.ps.destination="lp -P [printer]" />
```Replace **show-effects-menu="0"** with **show-effects-menu="1"** and save the file.
[/LIST]

Now open Inkscape and enjoy the various goodies found under the new menu item called **Effects**.

---

