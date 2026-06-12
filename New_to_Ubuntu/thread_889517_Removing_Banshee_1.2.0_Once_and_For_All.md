---
title: "Removing Banshee 1.2.0 Once and For All"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by FlintyVamp on 2008-08-14
Hey,

I'd like to remove Banshee 1.2.0 but it just doesn't seem to want to go. I removed it from Synaptic and it removed it without problems. 

I take a look under Applications -> Sound & Video and it's still listed there. I launch it and it does launch but crashes within a second or two.

I was wondering how I would go about removing these left over fragments so I could go ahead and get the new 1.2.1 version. 

Cheers,

---

### Post by cozmicharlie on 2008-08-14
Most likely you still have a config file in Home/yourname/.banshee.  Go to you Home folder and in the menu go to View>Show Hidden Files and you will probably have a .banshee folder.  Open it and delete everything inside it.  You can leave the folder, since you are going to reinstall 1.2.1.  The menu items may still be there but you can either leave them or remove them.  If you want to remove them, go to the menu>applications and right click>edit menus and a dialog box comes up which is self explanatory.  I would just leave them since you are going to reinstall.  You can double check to see if there are any other files by opening a terminal and typing "whereis banshee".

In the future you can use a purge command to completely remove the files.
sudo apt-get purge banshee

Enjoy

---

### Post by nunofyrbidness on 2011-10-29
Banshee still persists in showing as a possible app in my multimedia folder, and also when I want to open files or a media player. I can't install and uninstall it, because then it shows I have *two* installations. I checked and there are no .banshee folders in the home directory - but I do have files in /usr/share/app-install/desktop. Can I/how do I uninstall these, and will it fix my problem?

Please help!

---

