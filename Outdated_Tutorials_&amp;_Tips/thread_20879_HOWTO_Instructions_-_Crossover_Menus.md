---
title: "HOWTO: Instructions - Crossover Menus"
date: 2005-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by joshmachine on 2005-03-19
Hello All,

As I'm sure everyone with crossover office installed (or who wants to customize their menu) must know by know, Gnome 2.10 has some shortcomings in the old menu arena.  After a lot of investigation I have established a decent workaround while the world catches up to Gnome. Still a hack though, and will only be useful for single-user machines.


Quick instructions:

Using your favorite package manager install
[list]
[*]menu
[*]menu-xdg
[/list]  

as your local user run 'update-menus'  (crossover I believe runs this when you install a new application, or recreate any of the menus)

update menus creates the following files

.config/menus/debian-menu.menu
This file defines the menu directory structure for the "Debian" menu (these files are in an xml vocab which isn't too difficult to figure out, and the menu heirarchy is defined by the element heirarchy of menu elements.

.local/share/applications/menu-xdg
This contains all of the application .desktop files which defines icons, application to run etc.

.local/share/desktop-directories/menu-xdg
This contains all of the menu containers (pseudo directories), defines what icons they should use, defines the Categories they accept.


create a symlink in /etc/xdg/menus  to ~/.config/menus/debian-menu.menu (you may have to delete a pre-existing link to the debian-menu.menu that is generated when 'update-menus' is run as root.

logout and log back in and you should have a "Debian" menu.  "Crossover" and "Windows Applications"  will be there, and will be continued to be updated as you add and remove apps (although you may have to restart gnome to get them)

If you want details about the format these files take you can have fun reading through documentation at [http://www.freedesktop.org](http://www.freedesktop.org)

---

### Post by denjin on 2005-03-25
Thanks for this guide!

However, when I do this, I have double menu entries for every application in my new debian menu.  Any ideas?

I did do this at the end:
rm ~/.config/menus/debian-menu.menu
cassie@cassiepc:/etc/xdg $ ln -sf /etc/xdg/menus ~/.config/menus/debian-menu.menu
update-menus

---

### Post by Lord C on 2005-04-01
[QUOTE=joshmachine]Hello All,

As I'm sure everyone with crossover office installed (or who wants to customize their menu) must know by know, Gnome 2.10 has some shortcomings in the old menu arena.  After a lot of investigation I have established a decent workaround while the world catches up to Gnome. Still a hack though, and will only be useful for single-user machines.


Quick instructions:

Using your favorite package manager install
[list]
[*]menu
[*]menu-xdg
[/list]  

as your local user run 'update-menus'  (crossover I believe runs this when you install a new application, or recreate any of the menus)

update menus creates the following files

.config/menus/debian-menu.menu
This file defines the menu directory structure for the "Debian" menu (these files are in an xml vocab which isn't too difficult to figure out, and the menu heirarchy is defined by the element heirarchy of menu elements.

.local/share/applications/menu-xdg
This contains all of the application .desktop files which defines icons, application to run etc.

.local/share/desktop-directories/menu-xdg
This contains all of the menu containers (pseudo directories), defines what icons they should use, defines the Categories they accept.


create a symlink in /etc/xdg/menus  to ~/.config/menus/debian-menu.menu (you may have to delete a pre-existing link to the debian-menu.menu that is generated when 'update-menus' is run as root.

logout and log back in and you should have a "Debian" menu.  "Crossover" and "Windows Applications"  will be there, and will be continued to be updated as you add and remove apps (although you may have to restart gnome to get them)

If you want details about the format these files take you can have fun reading through documentation at [http://www.freedesktop.org](http://www.freedesktop.org)[/QUOTE]
 After running 'update-menus' I get CrossOver and Debian menus.

Why does everything in the Debian menu duplicate? I see everything twice :(

---

### Post by scaltro on 2005-04-01
Same problem!
 :cry:

All the entry in the Debian Menu are duplicate. 
How it can be fixed?

---

### Post by Telep on 2005-04-01
I went through all those steps and it doesn't seem to have any effect. No Debian menu, no Crossover menu. :(

---

### Post by kurros on 2005-04-01
This should be fixed in Crossover Office 4.2 Final

---

### Post by emperor on 2005-04-03
[QUOTE=kurros]This should be fixed in Crossover Office 4.2 Final[/QUOTE]

The Gnome 2.10 menu problem did not get fixed in CX4.2

---

### Post by kurros on 2005-04-03
[QUOTE=emperor]The Gnome 2.10 menu problem did not get fixed in CX4.2[/QUOTE]

[img]http://members.arstechnica.com/x/kurros/cxmenus.png[/img]

I'm not sure why I have these menus under a fresh install of 5.04 Release Candidate and CrossOver Office 4.2, then. I have not changed any configuration files or menu packages.

---

### Post by bored2k on 2005-04-03
I tried it and worked. But I forgot why I installed it in the first place :-S .

---

### Post by emperor on 2005-04-04
The menus were not created when I updated to CX4.2, even when manually requested the menus be re-created in the CX setup utility. Even a fresh install of CX4.2 does NOT create the menus.However, apparently the menus are created on other Gnome 2.10 Hoary installations. Very strange behavior!

---

### Post by joshmachine on 2005-04-06
For me the double menus went away when i deleted the link "/etc/xdg/menu/debian-menu.menu"  and linked to my local user menu  (i.e.  "~/.config/menus/debian-menu.menu"

/etc/xdg/menu/debian-menu.menu --> ~/.config/menus/debian-menu.menu

denjin:  I think you did the linking backwards.

The double menus seem to appear when you don't do this because it is loading the menu entries from /var/lib/menu-xdg as well as the entries from ~/.local/share/applications/menu-xdg

You have to force it to use your local entries otherwise it won't pick up the *actual* windows applications you have installed. 

Also I've tried reinstalling some of the afflicted apps and don't get the nice setup that Kuros got.   

Cheers

---

### Post by denjin on 2005-04-07
Ok, hang in there with me, as I keep doing this early in the morning.  Am I doing something wrong?

cassie@cassiepc:~ $ sudo rm /etc/xdg/menus/debian-menu.menu
cassie@cassiepc:~ $ sudo ln -sf /etc/xdg-menus/debian-menu.menu /home/cassie/.config/menus/debian-menu.menu
cassie@cassiepc:~ $ update-menus

I still have doubled menus.
[QUOTE=joshmachine]For me the double menus went away when i deleted the link "/etc/xdg/menu/debian-menu.menu" and linked to my local user menu (i.e. "~/.config/menus/debian-menu.menu"

/etc/xdg/menu/debian-menu.menu --> ~/.config/menus/debian-menu.menu

denjin:  I think you did the linking backwards.

The double menus seem to appear when you don't do this because it is loading the menu entries from /var/lib/menu-xdg as well as the entries from ~/.local/share/applications/menu-xdg

You have to force it to use your local entries otherwise it won't pick up the *actual* windows applications you have installed. 

Also I've tried reinstalling some of the afflicted apps and don't get the nice setup that Kuros got.   

Cheers[/QUOTE]

---

### Post by joshmachine on 2005-04-07
Alas denjin.
I notice a couple of things you are doing wrong.  
One is the linking (see example of how to do it below). The other is the ink you are creating is to /etc/xdg-menus/debian-menu.menu.  I don't have such a directory on my  machine so not sure about that one.

You also don't need to keep running update-menus. It's won't do anything unless you've installed new software, and when you do, crossover seems to run it as well so the stuff appears on your machine.

Note: with "ln"   the command is "ln target link"

try the following:

sudo rm /etc/xdg/menu/debian-menu.menu
sudo ln -s /home/cassie/.config/menus/debian-menu.menu /etc/xdg-menus/debian-menu.menu

logout, log back in (or I usually just give a "killall gnome-panel" and that seems to force it to restart/reload) and it should just work.  

If it's STILL not working.  just delete "/var/lib/menu-xdg"  (or rename it if deleting it freaks you out. Not me.  I love deleting stuff. No crappy ass recyling bin safety net for me.)  Anyways that will work as well although installing or upgrading packages *may* make "update-menus" be run as root which is what creates the directory in the first place.   

If it's **STILL** not working. I'll put up an AIM account and walk you through it. 

But one of the two above (creating the proper link or deleting the /var/lib/menu-xdg directory) should definitely work.  Hopefully when there is a release this will all be wasted effort because we'll all have pretty "windows applications" menus like lucky kurros.

I love linux, and I know it's always a work in progress, but I am amazed at how something as small as doubled menus can really piss me off.  

Cheers,
Josh

---

