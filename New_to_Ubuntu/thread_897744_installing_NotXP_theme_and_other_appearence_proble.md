---
title: "installing NotXP theme and other appearence problem"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Falc7 on 2008-08-22
I am trying to install the not XP theme for my mum
In the instructions for installation it says:
--------------------------------------
The configuration editor opens, then open these folders in the left pane (apps>panel>objects)

You will see a list of objects in the pane locate the one that says (menu_object) next to object_type in the right pane.

Once this is located scroll down and locate the use custom icon entry and select it.

Scroll back up and double click the custom icon entry, this will open a new window asking for the path to the icon you wish to use. Enter the path in the value field and click OK

/home/USERNAME/.themes/NotXP/start.png
-----------------------------------------


However, it dosen't specify which folder under 'objects' that i should change the value for. I would have thought it would be under menu bar theme, but selecting it dosen't give any options in the right pane of the configuration editor.


So i tried to follow this guide:
[http://ubuntuforums.org/showpost.php?p=381182&postcount=4](http://ubuntuforums.org/showpost.php?p=381182&postcount=4)
I set the 'custom icon' value as the location of the picture i wanted for my start bar. However it still dosen't change the icon.


Also, in menu bars in open office, the fonts are white, as are the menu background, which means i am unable to read the writing without putting the mouse over it. I tried changing the font colour to black in options-> appearance, but it didn't help.


A related problem is that i get these errors in the terminal when i try to do the change the main menu icon as written above:



mum2@mj-desktop:~$ gconf-editor

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/shadows/frame1.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/shadows/shadow-none.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/shadows/frame1.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/shadows/shadow-in.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/lines/line-v.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: Invalid borders specified for theme pixmap:
        /home/mum2/.themes/NotXP/gtk-2.0/lines/line-h.png,
borders don't fit within the image

** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient


** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient


** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient


** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient


** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient


** (gconf-editor:8259): WARNING **: invalid source position for vertical gradient

---

### Post by amazingtaters on 2008-08-22
So, I'm a little confused, have you installed the theme and are now trying to install a custom icon in addition to that? The theme install should be as easy as dragging the .tar.gz that the theme came in (assuming it was packaged this way) into the list of themes under System>>Preferences>>Appearance

---

### Post by Falc7 on 2008-08-22
Hi
Yep I have installed the theme okay, but installing the theme dosen't change the main menu icon, i have to do that manually, which is where i am getting all the trouble.

This is the theme i am trying to install:
[http://gnome-look.org/content/show.php/NotXP?content=73782](http://gnome-look.org/content/show.php/NotXP?content=73782)

---

### Post by ajgreeny on 2008-08-22
As amazingtaters says, just right click on the desktop, go to Change Desktop Background, then change to Theme tab and there click Install and navigate to the tar.gz you downloaded.  Your theme will magically change before your eyes.

EDIT:
You're right, I hadn't noticed that!

---

### Post by amazingtaters on 2008-08-22
Okay, what that looks like is the main menu item for the panel. It does the same thing as the menubar (the default install way which splits Applications, Places, and System into seperate menus) but with one menu, like you see there. So, right click on your panel over any part of the menubar (eg the words applications, places, or system) and click remove from panel. Then right click on the panel and click add to panel, and add main menu. That may solve your issue.

---

### Post by Falc7 on 2008-08-23
yep i followed the instructions and it told me to do that, however the start menu still looks like the ubuntu symbol, rather than the ubuntu/start-button-menu that i am aiming for; and downloaded in the theme

---

