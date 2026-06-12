---
title: "subfolder screenlet"
date: 2008-01-15
forum: Programming Talk
---

### Post by InGunsWeTrust on 2008-01-15
I want a screenlet that doesn't exist anywhere, but I don't know python at all! Don't send me to Python.org either because I can't figure it out for the life of me! I want a very generous soul to code it for me!

General Description: When I click the screenlet it will drop down a list of links to subfolders in a specified folder. In the options I should be able to specify which folder it will do. I want the icon for the screenlet to be the attached image. Basically I have a bunch of classes at school that have different types of work in it and I want to be able to open up a copy of the screenlet for each class and be able to quickly go directly to the subfolders in the folder for the class.

Normal Flow of Events:

1. Click on the screenlet
2. A box of a generic style drops down
3. Click the name of the sub folder
4. The folder opens in nautalis.

---

### Post by chewearn on 2008-01-16
You can use a drawer applet.  No programming required, just some initial effort/time to set it up.

Right-click on one of the gnome-panel (top or bottom, which ever you prefer), select "Add to Panel", locate Drawer, click Add, and Close.

Right-click on the Drawer, select Properties; click on "no icon" button, browse and select your favorite icon.

Then click on the Drawer, the "drawer" will pop open.  Right-click on the drawer, select "Add to Drawer".

Click on "Custom Application Launcher".  Fill in the Name (in your case, can be the school class).  For command, use "nautilus <folder path>".

---

### Post by InGunsWeTrust on 2008-01-16
I sort of like the screenlet thing, although I will surely be using the drawer aplet now until I can either code or have coded my screenlet

---

