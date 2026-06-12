---
title: "wxPython Unable To Create Menu Bars In 12.04"
date: 2012-06-15
forum: Programming Talk
---

### Post by CosmicFlux on 2012-06-15
Hey,

I've been using wxPython to create an interface but I'm having the following problems:

[LIST=1]
[*]No menu bar is visible
[*]When I close the frame I get an error message
[/LIST]

The error message reads:

**LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.**

The code I'm using works absolutely fine in earlier versions of Ubuntu, this problem has just sprung up in Pangolin. 

Anyone know what's the issue here?


Cosmic

---

### Post by TheRealGuyMontag on 2012-08-21
I've been having the exact same problem - anyone have any solutions?

OK so I finally found something on the web that helped. I followed the instructions from this post:

[https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/948944](https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/948944)

and now I see a menubar, but I still get the child/parent error


The short version:
reinstall wxpython, but not with version 2.6

open a terminal
sudo apt-get autoremove python-wxgtk2.6 python-wxgtk2.8 python-wxversion

sudo apt-get install python-wxgtk2.8
sudo apt-get update

---

### Post by seanpary on 2012-08-24
Try looking for solution on    [Computer   Programmers]("http://www.ranker.com/list/most-influential-software-programmers-of-all-time/ready-to-startup") Here You have entire programming solutions. I myself refer here every-time I am lost in programming.

---

### Post by tkro on 2012-11-01
Have exactly the same problem with Ubuntu 12.04.1 LTS 64-bit, vanilla + update/upgrade + a collection of python, python3, wx, matplotlib, wxmpl, etc installed. The ZetCode menu examples do not display menus, and the warning appears on exit.

Checked wx-version, it was already 2.8.12. Tried the uninstall/install above, now have wx 2.8.12.1, and the problem remains. Currently using python 2.7.3 with the Spyder IDE.

The bug appears not fixed, or has reappeared?

---

### Post by tkro on 2012-11-01
The UNITY desktop by default "steals" all menu bars, and displays the active window's menu bar in the top panel (this is called "Global menu", and it pops up when you move the cursor over the top panel). Probably useful and elegant once you get used to it... When trying to learn wxpython (without knowing Unity), it was however utterly confusing. Moreover, this may not be a logical layout for the application I want to build. With several frames or panels in an application window I guess I need menus to stay put in the frame (or pop-up window) the user is focused on. Need to learn more before I can decide.

Tried Unsettings - it claims the Global menu feature has been switched off. I've applied the change, logged out and in, rebooted several times - NO CHANGE. The global menu is still active. According to Florian Diesch, this is probably because the current version of Unsettings cannot change global settings (anything that requires root privileges).

Also tried to install Gnome fallback. At first it did not appear to work - make sure you disable automatic login. The classic Gnome desktop does display menues where I expect them, but the warning still appears on exit (LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.)

HOWEVER - logged out and started new UNITY session. Now Firefox displays its menu bar in the global top panel, but Spyder has its menu bar locally, and so do the wxpython example windows run from Spyder. On top of all this, the wxpython example windows can now be closed without the above warning! 

I have no idea whether Unsettings did this, or my switcjing to Gnome and back, or a combination of these two...

---

