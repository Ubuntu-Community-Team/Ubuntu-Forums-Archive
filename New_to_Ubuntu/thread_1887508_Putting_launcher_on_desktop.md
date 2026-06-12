---
title: "Putting launcher on desktop"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by corncob on 2011-11-27
I just installed 11.10.  Is there any way to copy a launcher from the dash to the desktop?  I see how to put in into that launcher stack on the left and into cairo-dock but some things I'd like to have on the desktop.

---

### Post by BC59 on 2011-11-27
I drag and drop a link from the the dash to the desktop, then right click to make it executable. After again drag and drop to the launcher.

Problem! Stays a link on the desktop, if you delete it, you are losing the launcher link, so improvise. You can drag and drop from the dash to another folder.

---

### Post by corncob on 2011-11-27
I opened the dash and, just as a test, I dragged Archive Manager over to the side panel to the HOME folder, which opened and I dropped Archive Manager onto the desktop folder.  Success -- Archive Manager now appears on the desktop.  However, when I dragged something that I really wanted over to the side panel, the launchers (lenses) moved aside so I could drop it into the panel -- not what I wanted, I wanted it on the desktop.

---

### Post by corncob on 2011-11-28
Just in case anybody else wants to do this, I finally did figure it out (sorta).  The launchers appear to be in the /usr/bin directory.  While open in Nautilus I dragged the appropriate launchers to the Home/Desktop directory.  They appeared on the desktop with that generic diamond icon which I could right-click, then Properties, then click on the icon to select something better.
I'll mark the thread as solved but this does seem quite clumsy and Google Earth doesn't show up so any other suggestions are welcome.

---

### Post by BC59 on 2011-11-28
There is the classic solution as well. Write alacarte on the dash search and you have the classic Ubuntu menu to manipulate.

---

### Post by beew on 2011-11-28
> **corncob said:**
> Just in case anybody else wants to do this, I finally did figure it out (sorta).  The launchers appear to be in the /usr/bin directory.  While open in Nautilus I dragged the appropriate launchers to the Home/Desktop directory.  They appeared on the desktop with that generic diamond icon which I could right-click, then Properties, then click on the icon to select something better.
I'll mark the thread as solved but this does seem quite clumsy and Google Earth doesn't show up so any other suggestions are welcome.

Are you sure it is /usr/bin? I think .desktop files are usually in /usr/share/applications, or if you create them yourself with alacarte they will be ~/.local/share/applications. I think you can  change the generic diamond by going to properties and choose allow to execute as program (something like that, forget the exact words)

P.S. alarcarte works in Unity as well for creating .desktop files, but the launchers thus created don't sort properly in the Unity dash, they all end up unsorted (but they do in Gnome Shell). To make the icon appears in the proper category in the dash you have to edit the desktop file with gedit and add the line "Category=whatever category desired;"

---

### Post by corncob on 2011-11-29
> **beew said:**
> Are you sure it is /usr/bin? I think .desktop files are usually in /usr/share/applications, or if you create them yourself with alacarte they will be ~/.local/share/applications. I think you can  change the generic diamond by going to properties and choose allow to execute as program (something like that, forget the exact words)


I guess they must be links or something in /usr/bin.  Dragging them to the Desktop folder copies (not moves) them.  They're already marked as executable and they are working.  Good info about /usr/share/applications.  I even see Google Earth there.  However, permission denied to drag it to the desktop.  Opening Nautilus with gksudo drags it to root's desktop.  I was able to get it to my desktop by opening a second nautilus window but the executable option was ghosted out.  I know about chown and chmod but I'm going to take a break for now.

---

### Post by corncob on 2011-12-31
I finally solved the problem very neatly.  I followed instructions at [http://ubuntuforums.org/showthread.php?t=1901543](http://ubuntuforums.org/showthread.php?t=1901543) 6th post and installed the indicator for the classic menu on the top panel (a launcher for the classic menu also comes with cairo dock).  I can now simply drag apps from the menu to the desktop.

---

