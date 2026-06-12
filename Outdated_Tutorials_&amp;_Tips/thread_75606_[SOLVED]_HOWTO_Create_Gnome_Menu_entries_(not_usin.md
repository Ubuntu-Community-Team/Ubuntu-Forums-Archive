---
title: "[SOLVED] HOWTO: Create Gnome Menu entries (not using smeg)"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
**CAVEAT:** After u install a new app, u might think that the menu entry to that app is missing. Before u read any more, just log out and log back in. If the menu entry still isnt there, then follow this HowTo. Otherwise, u might overwrite the existing newly created menu entry or have duplicate entries.

**Part 1**
Well, I thought about writing this HowTo many months back but I somehow let it go. However, looking at the number of posts which say "wherez my menu entry? why is smeg crashing?", I have decided to write this one. This will be particularly useful to newbs and intermediate users.
Alright I dont use smeg. I will illustrate how I add a Gnome menu entry by giving an example. let us say I have downloaded the game called Nexuiz in my home folder and I want to make a menu entry. herez how I do it: 
```
sudo gedit /usr/share/applications/nexuiz.desktop
```
save this and close it. Now I have a neat menu entry under games in Gnome menu called "Nexuiz"
Now I will explain what I have done though most of it is self-explanatory.
1) u need to choose a filename (lets say "xyz.desktop") insteadof nexuiz.desktop depending on how u want to name the file. however, it will be at the same location (/usr/share/applications/)
2) Now about the entries in the file:
The first 3 lines will be the same for all applications ie.,
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
```
**Exec** will contain the path of the executable
**Icon** will contain the path of the icon u want to choose for the menu entry (try to make sure its a .png or .xpm file)
**Terminal** will have a value of ***true*** if u want to run the application in a terminal window. Most GUI apps u would NOT want to run in terminal, so u can keep it as ***false***
**Name** and **Comment** are self explanatory
**Categories** is the crucial one.
here u CANT put in anything u want (u are restricted by certain keywords)
Make the first word **Application; (the semicolon is important)**
The second word can be one of the following depending on where u want your app to appear in the menu:
```
 GNOME MENU
Menu Entry ---> second word that u have to put in category **(followed by semicolon)**
----------------------------------------------------------------------------------
Accessories --> Utility;
Edutainment --> Education;
Games --> Game;
Graphics --> Graphics;
Internet --> Network;
Office --> Office;
Programming --> Development;
Sound & Video -->AudioVideo;
System Tools --> System;
Others --> Other;
```
Now u are all set. save and exit. u will immediately have a new entry in your Gnome menu.

**Part 2**
there are certain apps that will not run till u execute them from the folder in which they reside (in other words u have to cd to that folder or open that folder in nautilus and execute it. These are generally binary files which u have downloaded and u run them directly without installing. Example: The game CUBE.
How do u add a menu entry in this case? If u add a menu entry just like u did in part 1, the app wont run because u are not running it from its folder. even creating a shortcut doesnt work.
In this case this is what u do:
u make a small script by doing: 
```
sudo gedit /usr/bin/cube.sh
```
which looks like this:
```
cd /home/arnie/cube/
./cube_unix
```
save and close. then, to make it executable, do a
```
sudo chmod 755 /usr/bin/cube.sh
```
thats it! u are all set. Now point to this shell script in ur desktop menu entry. Thus for this case **Exec** in *xyz.desktop* will look like:
```
Exec=/usr/bin/cube.sh
```

---

### Post by johnhedge on 2006-01-17
Thanks for the 'Howto' Arnieboy. It took me one step further along the path to understanding how to manage the menu items.

Unfortunately it doesn't quite go far enough for me.

I've apt-get'd Gambas. Using either your approach or Alacarte I can get Gambas to appear in 'Programming' (Development). My problem is I cannot get Programming to appear in the Applications menu.

If you can help it'll stop my hair loss :-)

John

---

### Post by NESFreak on 2006-03-12
you can use the "killall gnome-panel" command to reload the panel, wich goes faster then log out and in

---

### Post by vtrac on 2006-11-21
For Gnome 2.14 (in Gentoo, actually), I had to add:

Type=Application

for it to show up.

---

### Post by bsmith on 2007-08-05
Sorry to bring up this old post, but is there a way to add new folders within menus for further sorting of entries, without using alacarte.

eg, I want to place all the little gnome games in one folder in the games menu, and action games in another, strategy in another etc.

Thanks

---

### Post by neurostu on 2008-07-07
bsmith: did you ever figure out how to add folders?

---

### Post by iyo on 2009-07-11
> **neurostu said:**
> bsmith: did you ever figure out how to add folders?

I figure out how to add folders. I wrote down complex tutorial how to add new folder + items to it:

[http://wiki.matusov.sk/howto/gnome-menu-edit](http://wiki.matusov.sk/howto/gnome-menu-edit)

I used information from:
[http://library.gnome.org/devel/menu-spec/](http://library.gnome.org/devel/menu-spec/)
[http://ubuntufs.wordpress.com/2007/05/15/add-menu-items-in-gnome/](http://ubuntufs.wordpress.com/2007/05/15/add-menu-items-in-gnome/)

---

