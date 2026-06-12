---
title: "HOWTO: Better GDM integration for XFCE4"
date: 2006-01-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2006-01-23
Be nice, this is my first Howto.

[CENTER][SIZE="5"]**Better GDM integration for XFCE4**[/SIZE]
or
[SIZE="5"]**A Guide to a lighter GNOME**[/SIZE][/CENTER]

XFCE4 doesn't have its own login manager, so it uses whatever the system has installed, on an Ubuntu system that is mostly GDM, for this reason xfce asks for your password every time you want to restart or shut the computer down. This howto is meant to help you fix that.

For this, we will need an existing Gnome installation. if you don't already have gnome installed you can just:

apt-get install ubuntu-desktop

to get it.

Now, logout of your XFCE session and log into gnome. 
We will do a complete remodeling of your current gnome-setup. First of, the window manager.

**1.** By default XFCE4 uses xfwm4 as its window manager, gnome uses metacity.
We would want to change that (if you prefer metacity, skip this step)
to do this, follow [theine's tutorial](http://www.ubuntuforums.org/showthread.php?t=88393&highlight=xfwm4)

**2.** Now, we want to get rid of Nautilus and the Gnome-Panel. Go To:
System -> Preferences -> Sessions then to the “Current Session” tab. Select nautilus and gnome-panel (gnome-volume-manager is optional, its a good thing to keep though) then click remove and apply. Optionally you can remove other non-vital things to fit your liking. If you like desktop icons, keep nautilus (requires more memory).

Now press ALT + F2 and after a box appears type “xftaskbar4” then repeat the same thing but type “xfce4-panel” and again with “xfdesktop”. Now you should start to feel a bit more at home.
Return to the sessions window that we opened earlier and change the style for: xfwm4, xftaskbar4, xfce4-panel and xfdesktop to “Restart” followed by apply. 
Now we are done with the Sessions window.

**3.** Now, the xfce4 control center will no longer work, so we have no further use of it. Right click on the Settings icon and change the command field to “gnome-control-center”, in the future, when you want to change GTK Themes (amoung other things) this is where you do it.

Now when you restart or shut your computer down, xfce will use the Gnome logout dialog and it wount ask for your password.

---

### Post by Iandefor on 2006-01-28
Tricky. Running an XFCE session using the gnome-session-manager? I'd never have thought of it.

---

### Post by blair on 2006-05-19
If I understand the above correctly, it assumes you have added xfce on top of the standard Ubuntu install which includes Gnome.  An alternative approach if you don't want Gnome installed and want a straight xfce system is to do the sequence below. I reference other posts, but the below brings a bunch of disparate things together into the complete solution:


1. To install xfce only follow these instructions (more or less):

[http://www.ubuntuforums.org/showthread.php?t=75971](http://www.ubuntuforums.org/showthread.php?t=75971)


2. To automate login (i.e. to boot straight into the desktop and bypass a manual login and manual startx/startxfce4 command: 

[http://ubuntuforums.org/showthread.php?t=152274](http://ubuntuforums.org/showthread.php?t=152274)

A reminder that this configuration is for a single user system where login security is not a hard requirement. If you want a multi-user system that displays a GUI login screen, this is not the solution for you. 


3. To automate logout/shutdown (i.e. not be prompted for a password) add the following line to the end of the /etc/sudoers file as root:

ALL ALL = NOPASSWD: /usr/sbin/xfsm-shutdown-helper

---

### Post by blair on 2006-05-19
.

---

### Post by TroelsB on 2008-08-10
There's also another advantage. Somehow (guess there are a couple of daemons running) my HP quckbuttons are working this way. If I can get the Xfce panels to work properly, then the Gnome-ones will be replaced :)

---

