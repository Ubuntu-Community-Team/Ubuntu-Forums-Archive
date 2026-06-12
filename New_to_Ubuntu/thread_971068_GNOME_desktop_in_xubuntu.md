---
title: "GNOME desktop in xubuntu?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by orwellus on 2008-11-04
Hello:

I've been trying to get into xubuntu for awhile now. I like Thunar. I like that it is for low spec systems (I have a laptop with 256 RAM). The thing that is stopping me, though, is just a couple of minor things. First, I don't like the menu editor in xubuntu. The menu is a little cluttered, and I want to hide some of those apps, but I can't figure out how to do that using the menu editor. I also, would like to be able to add things to the desktop or to a panel, and I'm having trouble getting that to work on xubuntu (right clicking just opens the application in xubuntu). 

So is there a way to install, like a basic GNOME desktop in the place of Xfce, but still keep things like Thunar and the rest of Xubuntu? I would like to install Xubuntu Hardy on my laptop if I can get this GNOME/Xfce combo working.

---

### Post by dracayr on 2008-11-04
install ubuntu hardy, and then install thunar on it :P

dracayr

---

### Post by hewhowatches on 2008-11-04
I have Xubuntu installed on a 500Mhz PIII laptop with 160MB. Originally, I installed it with both XFCE and Gnome.

Gnome ran quite well considering the age of the equipment, but XFCE ran much quicker overall.

I believe this will do what you want:
```
sudo apt-get install gnome
```

You should be able to choose which window manager you want to login to on the login screen.

---

### Post by DGortze380 on 2008-11-04
> **orwellus said:**
> Hello:

I've been trying to get into xubuntu for awhile now. I like Thunar. I like that it is for low spec systems (I have a laptop with 256 RAM). The thing that is stopping me, though, is just a couple of minor things. First, I don't like the menu editor in xubuntu. The menu is a little cluttered, and I want to hide some of those apps, but I can't figure out how to do that using the menu editor. I also, would like to be able to add things to the desktop or to a panel, and I'm having trouble getting that to work on xubuntu (right clicking just opens the application in xubuntu). 

So is there a way to install, like a basic GNOME desktop in the place of Xfce, but still keep things like Thunar and the rest of Xubuntu? I would like to install Xubuntu Hardy on my laptop if I can get this GNOME/Xfce combo working.

GNOME and XFCE are desktops. Both work on Ubuntu. Sometimes you can installs applications designed for one in another. You can try to install GNOME, then your Prefered applications from XFCE, but you can not run GNOME and XFCE at the same time. I think GNOME is going to be painful on a laptop with 256mb of RAM.

---

### Post by bodhi.zazen on 2008-11-04
> **orwellus said:**
> Hello:

I've been trying to get into xubuntu for awhile now. I like Thunar. I like that it is for low spec systems (I have a laptop with 256 RAM). The thing that is stopping me, though, is just a couple of minor things. First, I don't like the menu editor in xubuntu. The menu is a little cluttered, and I want to hide some of those apps, but I can't figure out how to do that using the menu editor. I also, would like to be able to add things to the desktop or to a panel, and I'm having trouble getting that to work on xubuntu (right clicking just opens the application in xubuntu). 

So is there a way to install, like a basic GNOME desktop in the place of Xfce, but still keep things like Thunar and the rest of Xubuntu? I would like to install Xubuntu Hardy on my laptop if I can get this GNOME/Xfce combo working.

To be honest, sounds like your two best options are either :

1. fluxbox (with a custom menu). The fluxbox menu is much cleaner and easier, it is a text file.

2. Just make a custom menu in XFCE :)

---

### Post by hewhowatches on 2008-11-04
> If you want to use the root menu and/or the window list, the corresponding options have to be selected in the settings dialog.

A right-click on the desktop backdrop opens a menu that allows you to start some applications. Its configuration file, menu.xml, can be found under the path $sysconfdir/xdg/xfce4/menu.xml. For binary packages, $sysconfdir is often /etc and for source compiles, it defaults to /usr/local/etc.

While it is possible to edit the file manually, the recommended method for editing the menu.xml file is via the Xfce 4 Menu Editor, which can be started by running xfce4-menueditor, or using the "Edit desktop menu" button available from the Menu tab of the Desktop settings dialog. The menu editor also supports drag'n'drop from a file manager.

If you've edited the menu via xfce4-menueditor, the user-customized menu file will be saved to $XDG_CONFIG_HOME/xfce4/desktop/menu.xml. $XDG_CONFIG_HOME usually defaults to ~/.config. If editing the file manually, copying it to this location first is the preferred method.

From:

[http://www.xfce.org/documentation/4.2/manuals/xfdesktop]("http://www.xfce.org/documentation/4.2/manuals/xfdesktop")

---

