---
title: "AWN Stopped working"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Matuku on 2008-08-07
My Avant Window Navigator has suddenly stopped working; it should load at boot but doesn't and clicking on the icon does nothing. If I try and load it from the terminal I get:

```

user@user-desktop:~$ awn
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/showdesktop.desktop
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/showdesktop/showdesktop.py", line 19, in <module>
    import pygtk
ImportError: No module named pygtk
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/amsn.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/gnome-system-monitor.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
APPLET : /usr/share/avant-window-navigator/applets/separator.desktop
APPLET : /usr/share/avant-window-navigator/applets/weather.desktop
APPLET : /usr/share/avant-window-navigator/applets/shinyswitcher.desktop
APPLET : /usr/share/avant-window-navigator/applets/trasher.desktop
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/weather/weather.py", line 25, in <module>
    from awn.extras import AWNLib
ImportError: No module named awn.extras
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/stacks/stacks_applet.py", line 22, in <module>
    import gtk
ImportError: No module named gtk
WM=compiz
ShinySwitcher Message:  compiz detected
ShinySwitcher Message:  viewport/compiz detected.. using existing workspace config
cols = 1,  rows=1 

```

and it will load now but parts of it are missing (certain applets) and sometimes it will disappear again upon pressing any button.

---

### Post by glennric on 2008-08-07
First, when you run awn from the terminal you should run it with the command
```
avant-window-navigator &
```

You should also try uninstalling awn completely and then reinstalling it.  If that still doesn't help then you have a problem with your personal configuration.  Try moving the directory ~/.config/awn somewhere else temporarily and see if awn runs better then.

---

### Post by Matuku on 2008-08-07
Moving the AWN .config folder didn't help but I get a different error when using the way you told me:

```

user@user-desktop:~$ avant-window-navigator &
[1] 6791
user@user-desktop:~$ Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/awn-applets-migration.py", line 3, in <module>
    import awn
ImportError: No module named awn

```

---

### Post by glennric on 2008-08-07
Did you uninstall and reinstall?  

If that still doesn't help then how are you installing awn?  Where are you getting it from?  The ubuntu repos, the bzr repos, or are you compiling it yourself?

---

### Post by Matuku on 2008-08-07
Tried uninstall and re-install but no cigar; I'm using the bzr ones I believe, the ones which all have "trunk" in the name in synaptic. I think it may be something to do with python, I've been having troubles with other *.py files.

---

### Post by glennric on 2008-08-07
Check to see that you have the packages "python-awn-trunk", "python-gnome2", and "python-gnome2-desktop".

---

### Post by Matuku on 2008-08-07
Each of those is present and accounted for; any other thoughts?

---

### Post by glennric on 2008-08-07
When you uninstalled awn how did you do it?  Try using the following:
```
sudo apt-get remove --purge avant-window-navigator-trunk awn-manager-trunk libawn0-trunk python-awn-trunk vala-awn-trunk awn-extras-applets-trunk avant-window-navigator-data-trunk
```

Then reinstall all of those packages and remove (or move to another place) the directory ~/.config/awn.

---

### Post by Matuku on 2008-08-07
No luck, still the same issue.

---

### Post by glennric on 2008-08-07
It is possible that this is an issue of not having a python package installed that is needed, but is for some reason not in the dependencies.  I have encountered this before with awn.  Check that you have "python-gtk2" and perhaps "python-all" installed.

---

### Post by Matuku on 2008-08-07
python-all was not installed but it doesn't appear to affected the situation having done so. python-gtk2 was already installed.

---

### Post by glennric on 2008-08-07
Just to check, you do have compiz (or another compositing desktop manager) running don't you?

Besides trying various python packages I am not sure what else to tell you.

---

### Post by Matuku on 2008-08-07
Yep, rotating between multiple desktops as I type this; something must have gone wrong, I may well just have to re-install Ubuntu. Thank you for all your help!

---

