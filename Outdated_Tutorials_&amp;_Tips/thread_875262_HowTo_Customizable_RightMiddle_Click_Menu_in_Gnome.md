---
title: "HowTo: Customizable Right/Middle Click Menu in Gnome"
date: 2008-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by quazi on 2008-07-30
I'm a recent transfer from an XP system where I was running litestep.  For those of you who don't know, litestep has an easily customizable right click menu that basically supplanted the standard windows start menu.  This made getting a customizable menu in Gnome a pretty big priority for me.

Now there are four main ways I found to add this functionality to Gnome nautilus-scripts, nautilus-actions, mygtkmenu (compiz-deskmenu too, but mygtkmenu seems better), and the main gnome menu (my favorite of the four).

I'm currently using mygtkmenu because the main gnome menu is inaccessible without running gnome-panel.

**[SIZE="4"]nautilus-scripts[/SIZE]**
[[IMG]http://img141.imageshack.us/img141/5339/nscriptactal9.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=nscriptactal9.jpg)

Just write a script for the desired action, make it executable, and place the script in 
```
~/.gnome2/nautilus-scripts/
```

A script submenu will then appear in the right click menu when clicking anywhere in nautilus.


**[SIZE="4"]nautilus-actions[/SIZE]**
For this one, we need to start out by installing a new package, nautilus-actions, so open up a terminal and enter:
```
sudo apt-get install nautilus-actions
```

Then to configure the addons to the right-click menu, just enter
```
nautilus-actions-config
```

The menu for adding items is fairly straightforward, but if we want certain items to only show up when right-clicking the desktop, we need to add ```
x-nautilus-desktop
``` under the advanced conditions tab and only click that.  Also check Only folders if we don't want this item to show up when clicking on files in the desktop.

[[IMG]http://img519.imageshack.us/img519/2910/nactjn6.th.jpg[/IMG]](http://img519.imageshack.us/my.php?image=nactjn6.jpg)

Items here appear in the main right-click menu (as seen in the nautilus-scripts image).

**[SIZE="4"]mygtkmenu[/SIZE]**

[[img]http://www.ubuntu-pics.de/thumb/39721/screenshot_003_58jK2i.png[/img]](http://www.ubuntu-pics.de/bild/39721/screenshot_003_58jK2i.png)

We first need to download and extract mygtkmenu:

```

mkdir .mygtkmenu2
cd .mygtkmenu2
wget http://sites.google.com/site/jvinla/myGtkMenu-1.2.1c.tar.gz?attredirects=0 -O mygtkmenu.tar.gz
tar -zxvf mygtkmenu.tar.gz
rm mygtkmenu.tar.gz

```

Now, download the attached menu file (menu.txt) and put it in the same directory.  At the bottom of the file (lines 115/116) change yournamehere to your username.  Editing this file is very simple and the instructions are included in the comments.

To make this menu show up we need to make some changes in the compiz settings.  To bring this up, simply open a terminal and enter ```
ccsm
```

Now we just need to map this to the right mouse button. When in ccsm, click on general options and go under the commands tab and commands dropdown menu. Click on one of these that's unused and set it to:
/home/yournamehere/.mygtkmenu/myGtkMenu /home/yournamehere/.mygtkmenu/menu.txt 

Now go to Viewport switcher and set the Plugin for initiate action to "commands" ("core" for newer versions of Compiz) and the action name for initiate to "run_command#_key", where # is the number of the command corresponding to mygtk2menu. Change initiate plugin action key to Button 3 and now the right mouse button should popup the mygtkmenu. To bring up the gnome menu, hold control as you right-click. To edit the menu, just click on the edit item in the menu.

**[SIZE="4"]Gnome right-click menu[/SIZE]**
[[img]http://www.ubuntu-pics.de/thumb/22316/screenshot_003_lXOd0l.jpg[/img]](http://www.ubuntu-pics.de/bild/22316/screenshot_003_lXOd0l.jpg)
Notice that when you hit Alt+F1 and there's no menu launcher on the panel, the menu opens at your cursor.  What we do here is link the right click on the desktop to the key combination Alt+F1

Here's how it's done: download the 'xautomation' package:
```
sudo aptitude install xautomation
```

Then bring up compiz settings manager with:```
ccsm
```
Go to the commands page and and set up a command as:
```
xte "keydown Alt_L" && xte "key F1" && xte "keyup Alt_L"
```

Now go to Viewport switcher and set the Plugin for initiate action to "commands" ("core" for older versions of Compiz) and the action name for initiate to "run_command#_key", where # is the number of the command corresponding to xautomation.  Change initiate plugin action key to Button 3 and now the right mouse button should popup the compiz deskmenu. To get the gnome right-click menu back, simply hold command when right-clicking

**EDIT: In Jaunty, set "Plugin for initiate action" to "commands".**

---

### Post by bbqsandwich on 2008-08-05
I tried the nautilus-scripts method, but I do not see the Scripts submenu when I right click anywhere. Any thoughts?

---

### Post by quazi on 2008-08-09
Make sure your scripts are located in ```
/home/(your home folder)/.gnome2/nautilus-scripts
``` and are executable (under the permissions tab in the properties menu).

I'm not sure why this would be the case, but it's possible you might need to set the permissions so your account can access the scripts.  To do this, go to the nautilus-scripts directory and run ```
sudo chmod 755 *
```.

---

### Post by loomsen on 2008-10-27
Thanks, compiz deskmenu works just fine.\\:D/=D>

---

### Post by quazi on 2009-01-27
Compiz-deskmenu does have a big drawback in that it doesn't automatically generate menu items, but does have a simple editor very similar to alacarte.

Anyway, to save some time for other users, here's my deskmenu xml file.  It belongs in ~/.config/compiz/deskmenu/

It's an xml file, but I had to rename it to zip because of the strange rules of this forum's attachments.

---

### Post by rick71 on 2009-04-04
Is there a way to add the Gnome menu (or the Application/Places/Admin menus) to the right click?

---

### Post by rppp01a on 2009-04-07
Does Nautilus-Actions work in 8.10? I've installed it, and tried to add something ... anything. Nothing works. 

The install went fine. 
I opened up the panel. 
I tried to add firefox (to test), making the windows match what you've posted.
No luck. I've even restarted nautilus and rebooted my system. 

Any suggestions?

---

### Post by Piraja on 2009-04-09
Thank you quazi!

I have grown so used to Openbox &#8212; and so fond of it, too &#8212; that when I wanted to try Gnome for a change, after quite a while, I kept forgetting that I cannot open a menu by just right-clicking on the desktop. So a moment ago I searched for instructions for installing Compiz-Deskmenu and found yours.

Now I'm having fun &#8212; and better able to work &#8212; also with Gnome again!

---

### Post by quazi on 2009-04-11
> **rick71 said:**
> Is there a way to add the Gnome menu (or the Application/Places/Admin menus) to the right click?

EDIT: Yes there is.

Anyway, download the 'xautomation' package:
```
sudo aptitude install xautomation
```
and set up the command in compiz as 
```
xte "keydown Alt_L" && xte "key F1" && xte "keyup Alt_L"
```

Then follow the instructions in the Compiz-deskmenu section to hook up the right mouse button to that command.

> **rppp01a said:**
> Does Nautilus-Actions work in 8.10? I've installed it, and tried to add something ... anything. Nothing works. 

The install went fine. 
I opened up the panel. 
I tried to add firefox (to test), making the windows match what you've posted.
No luck. I've even restarted nautilus and rebooted my system. 

Any suggestions?

I don't know, it seems kind of finicky (I honestly haven't used it all that much, I prefer compiz-deskmenu).  I've gotten it to work in 9.04, so I would suspect it works in 8.10.

I've attached what I did to get it to work.

---

### Post by rppp01a on 2009-04-14
Actually, I was having issues with sound, and for some reason it was causing this to not work. Works great now. Thank you!

---

### Post by rlillard on 2010-01-05
> **quazi said:**
> EDIT: Yes there is.

Anyway, download the 'xautomation' package:
```
sudo aptitude install xautomation
```
and set up the command in compiz as 
```
xte "keydown Alt_L" && xte "key F1" && xte "keyup Alt_L"
```

Then follow the instructions in the Compiz-deskmenu section to hook up the right mouse button to that command.



I don't know, it seems kind of finicky (I honestly haven't used it all that much, I prefer compiz-deskmenu).  I've gotten it to work in 9.04, so I would suspect it works in 8.10.

I've attached what I did to get it to work.

I've gotten the popup-menu to work and I can edit the menu just fine.  Thank you for the help.  What is missing for me is how do I get the full "Main Menu" to popup from the Compiz-deskmenu?

I hope there is something I can launch as with a terminal window, etc ...  I just want to launch everything I have already customized with alacarte.

---

### Post by quazi on 2010-01-06
> **rlillard said:**
> I've gotten the popup-menu to work and I can edit the menu just fine.  Thank you for the help.  What is missing for me is how do I get the full "Main Menu" to popup from the Compiz-deskmenu?

I hope there is something I can launch as with a terminal window, etc ...  I just want to launch everything I have already customized with alacarte.

I don't know how to do this.  I simply set up the right-click to do the same thing as hitting alt+f1 with your keyboard.  If you don't have a gnome-panel entry for the ubuntu menu, this opens it up where your cursor is.

I actually haven't used compiz-deskmenu in awhile as it doesn't seem to have been updated in some time.

---

