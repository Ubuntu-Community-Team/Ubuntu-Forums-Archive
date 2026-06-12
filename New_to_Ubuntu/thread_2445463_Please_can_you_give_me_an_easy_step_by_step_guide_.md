---
title: "Please can you give me an easy step by step guide to installing icons to dock"
date: 2020-06-14
forum: New to Ubuntu
---

### Post by gavingilbert2 on 2020-06-14
Hi there - this is my problem - I have got Dash to Dock on Ubuntu 20.04 installed but cannot install icons to be placed on there. At the moment I have a theme (candy icons) that I have unpacked in the downloads folder. I then click on the candy-icons packet within the downloads folder. What do I do from here, as I have tried to left click on an icon and move it to the dock but it does not stay. Please tell me what I am doing wrong as I am very new to this

Thanks,

Gavin Gilbert.

---

### Post by Dennis N on 2020-06-14
Copy the icon theme folder to /usr/share/icons. Then use Tweaks utility to select this new icon theme in the Appearance tab. The icons in the dock will change.

---

### Post by gavingilbert2 on 2020-06-15
Thank you for your answer but it doesn't really help me. All I want to do is download an icon pack, open it, and drag and drop the icon (for instance a power off button) onto the Dock. I don't know anything about copying files to /urs/share/icons. I am struggling very hard with this and I would like a very simple step by step guide.

Thankyou.

---

### Post by CelticWarrior on 2020-06-15
How you want to do it can't be done.
The way to do it is how it was suggested in the step-by-step guide in the previous comment.

---

### Post by Holger_Gehrke on 2020-06-15
To give you a bit of background to what Dennis N and CelticWarrior have written:

The connection between an icon and the program to be called when the icon is clicked is a lot looser on Linux desktops than it is on Windows. Windows-programs have an icon stored in the program file, Linux programs don't. So the icons you downloaded are just images with no direct connection to programs (or actions on a toolbar or whatever else these icons are supposed to represent). 

The connection between a program and an icon is created by a file with the extension '.desktop'. These are simple text files which contain a lot of information including (but not limited to) the name to be displayed for the program possibly in multiple languages, a short description (again optionally with translations), the path and name for the program file and - of course - the icon to use for the program. The icon can be given in two ways: as a full path and filename or just as a name. If you give a full path and name to an image file that image will be used, independent of what icon set (or theme) is used. If you give just a name, then the currently active theme will be searched for an icon of that name (with no regards to extension, so icons can be in any file format the desktop system can read and named according to the convention for that file type).

So the thing you want to do is actually two things: getting a program into the dock and assigning the icon you want to that dock-item. 

To get a program into the dock you just add it to the dash by opening the Activities overview, finding the program, right clicking on it and selecting "Add to favourites". The program should be on the dash then and Dash to Dock should add it to the dock. 

How to change the icon(s) depends on whether you want to change just the icon for one program or you want to switch the whole set. In the latter case Dennis' advice applies. For just one program you'd find the desktop file for the program (those are in /usr/share/applications for system wide files and in $HOME/.local/share/applications for user specific ones;  user specific .desktop files override the system wide ones). I'd leave the system wide ones alone and copy the desktop file you want to change to a user specific one and then edit that changing the line that begins with "Icon=" to give the path and name for your icon.

Holger

---

