---
title: "how to launch graphic disk usage analyzer?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by 007casper on 2012-02-17
I loaded disk usage analyzer.  How can you launch it through terminal?

---

### Post by yetiman64 on 2012-02-17
> **007casper said:**
> I loaded disk usage analyzer.  How can you launch it through terminal?
```
baobab
``` Will launch it from terminal :)

Edit: only just noted the kubuntu tag, not sure if you are using the same program for "disk usage analyzer", I'm on Unity (11.10).

---

### Post by 007casper on 2012-02-17
I loaded xdiskusage 

[http://xdiskusage.sourceforge.net/](http://xdiskusage.sourceforge.net/)

it just doesnt load.

When I type "disk usage analyzer" in software management, nothing loads.  So, I typed diskusage together, and xdiskusage showed up.

???

> baobab
The program 'baobab' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-utils

---

### Post by yetiman64 on 2012-02-17
> **007casper said:**
> I loaded xdiskusage 

[http://xdiskusage.sourceforge.net/](http://xdiskusage.sourceforge.net/)

it just doesnt load.

When I type "disk usage analyzer" in software management, nothing loads.  So, I typed diskusage together, and xdiskusage showed up.

???


The program 'baobab' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-utils
I don't know about xdiskusage, ignore the baobab command earlier, it is the gnome disk usage analyzer application on the gnome/Unity desktop, though it could be installed in KDE it would likely drag in a few gnome dependencies as well.

Try the command in terminal
```
xdiskusage
```and see if that opens anything, if not post back any terminal output errors.

---

### Post by 007casper on 2012-02-19
awesome!  It works great.

How can I make a short cut icon to run it?... so I can run it without typing a command in terminal

thank you so much

---

### Post by Orcris on 2012-02-19
I personally use FileLight. I don't remember if you need to install it or if it comes with Kubuntu, but it is a good QT-based one.

---

### Post by yetiman64 on 2012-02-19
> **007casper said:**
> awesome!  It works great.

How can I make a short cut icon to run it?... so I can run it without typing a command in terminal

thank you so much

An example of a desktop configuration file I made to stop nautilus under gnome is below, you would need KDE not GTK in the categories field. When using these self made launchers, to set an icon I make a folder (~/.icons) and store .png files for icons, you only need the filename in the Icon= field and this location is checked for it (I am assuming that it is the same in KDE). 

I use this to stop nautilus file manager when needed.
> 
[Desktop Entry]
Type=Application
Name=Stop Nautilus
GenericName=Stop Nautilus
Comment=Kills all running instances of Nautilus
Exec=nautilus -q
Icon=quit-nautilus.png
Categories=GTK;Utility;
NoDisplay=trueYou would likely need something like,
> 
[Desktop Entry]
Type=Application
Name=Xdiskusage
GenericName=Xdiskusage
Comment=Disk usage analyser application.
Exec=xdiskusage
Icon=
Categories=KDE;Utility;
NoDisplay=trueCreate an icon in your home directory icons folder (hidden), put its filename in the launcher above (open a text editor and copy-paste the quote box above into your editor to add the icons name), save the above as *xdiskusage.desktop* and make executable. Now double clicking the *xdiskusage.desktop* file should launch xdiskusage. I usually store these launchers in ~/.local/share/applications as the NoDisplay= tag is set, it won't show in system menus, alter this to suit your situation (can be set to false, which will show the launcher in menus).

P.S. this is all assuming kde and gnome work the same on launchers, I am unfamiliar with kde.:)
Good luck.

---

### Post by 007casper on 2012-02-27
thanks yetiman64, and Orcris.

---

### Post by yetiman64 on 2012-02-27
> **007casper said:**
> thanks
You're welcome. :-)

If all is working ok please remember to mark the thread as solved from the thread tools drop down menu in your browser window. Link #5 in my sig has instructions if needed. Thanks.

---

