---
title: "wallpaper tray how to"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by golgo13 on 2008-05-22
total noob and getting used to this directory thing
I have installed wallpaper tray so I can change the wallpaper at regular intervals 
when I try to open it in the drop down applications menu or in usr/bin/wallpaper tray I get this message:
"No wallpapers were found, please update your configuration to include at least one valid directory, or add some wallpapers to your existing directory."
The wallpapers I want are in my pictures folder
My question is therefore quite simple:
How do I get copies of my pictures into the wallpaper folder so it will work?

---

### Post by skip mcshwang on 2008-05-22
When you run wallpaper-tray, a square should appear in the notification area of your panel, you can right-click that and click Configuration, then add the directories of your wallpapers.

---

### Post by golgo13 on 2008-05-23
I don't get that just the message described in my original post

---

### Post by CLEARviewF on 2008-06-13
Hi!
I suggest this, do this in the terminal:

sudo apt-get remove --purge wallpaper-tray
sudo apt-get install wallpaper-tray

Then you can run wallpaper tray again.
It has to be shown in the tray section. Right click and choose a directory to load the wallpapers.

I am looking for a way to fix one big problem in Wallpaper Tray, i would like to set wallpaper tray to Alphabetical mode, it is not possible, this is a known problem from so many months ago and it is not solved yet for Ubuntu, Wallpaper tray is in its 0.5.5 version and the package for ubuntu Hardy is still 0.4.6, what happen? nobody cares about wallpaper tray?

Maybe you want to try [[COLOR="Blue"]_Wallpapoz_[/COLOR]]("http://wallpapoz.akbarhome.com/"), this is a good project and works fine for me, but i dont like it because it does not let me delete wallpapers i dont like from the program itself. If you want to install Wallpapoz try [[COLOR="Blue"]_here_[/COLOR]]("http://maketecheasier.com/ubuntu-how-to-change-wallpaper-easily-with-wallpapoz/2008/02/29").

Bye....

---

### Post by cbbnewbie on 2010-05-07
hi I'm having a problem in wallpaper tray i cant seem to add a directory in it when i click on add nothing happens i cant drag a folder into it and cant change any configuration in it,, i dont know if its broken or what?

---

### Post by CLEARviewF on 2010-05-12
Wallpaper-tray is a dead project, Just try to remove it and all its configuration files and then install it again. In my Karmic it works fine.

Bye

---

### Post by BkkBonanza on 2010-06-22
Is there any way to make it NOT use the default /usr/share/backgrounds directory?

I added my new directory but it still uses the default one and I don't want to delete the default one - just not use it any more... seems kind of silly to me.

---

### Post by CLEARviewF on 2010-06-22
That happens all the time for me. Typical for that application. And It is a dead project, so, If you want to use it, just use it as it works or try to change its behavior by yourself.
Maybe you could find somebody who make that ofr you, good luck!!
:D
Or maybe you could check out its configuration files and try to figure out how to change its behavior.

Bye!!!!!!

---

