---
title: "HOWTO: Change Gnome-screensaver back to Xscreensaver"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by NobodySpecial on 2006-06-03
Those who have just migrated from Breezy to Dapper may not be aware of the [controversy]("http://www.ubuntuforums.org/showthread.php?t=137408") surrounding the Gnome Developers' decision to change Xscreensaver to Gnome-screensaver.  For those who prefer to bring back the beauty and customizability of Xscreensaver, read on.

```
System -> Preferences -> Power Management -> Move the two sliders all the way to the right
```
```
System -> Preferences -> Screensaver -> Unclick all options
```
In the terminal:
```
sudo chmod -x /usr/bin/gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```
Run xscreensaver once to start the daemon, then exit:
```
Alt-F2 (Run Application): xscreensaver

```
Make screensaver start with bootup:
```
System > Preferences > Sessions click on the "Startup Programs" tab, click "Add" and enter "xscreensaver -nosplash"
```
Fix the menu settings:
```
Applications -> Accessories -> Alacarte Menu Editor
System -> Preferences -> right click on Screensaver & select Properties
Change "command" box to "xscreensaver-demo"
Click "Close"

```
Now configure your screensavers:
```
System -> Preferences -> Screensaver
```
One final issue is that the "Lock Screen" function still points to gnome-screensaver.
In the terminal:
```
sudo cp /usr/share/icons/gnome/24x24/apps/gnome-lockscreen.png /usr/share/pixmaps
```
Add launcher to panel:
```
Right-click on panel -> Custom Application Launcher -> Name "Lock Screen", Command "xscreensaver-command --lock", Icon "gnome-lockscreen.png"
```

Enjoy!  8) 

Thanks also to [Abandon.]("http://www.ubuntuforums.org/showthread.php?t=166269")

Edited:
6/4/06  Added "-nosplash" to startup.

---

### Post by Elephantman5 on 2008-08-31
Now that I've totally messed up my system following your guide, the lockscreen doesn't work, and the last part of your tutorial doesn't work, 

Do you want to tell me how to undo everything you just told me how to do?

---

### Post by kellemes on 2008-08-31
> **Elephantman5 said:**
> Now that I've totally  up my system following your guide, the lockscreen doesn't work, and the last part of your tutorial doesn't work, 

Do you want to tell me how to undo everything you just told me how to do?

Don't blame him, you chose to follow a 2 year old tutorial, not the brightest of ideas.

---

### Post by Rhubarb on 2008-08-31
To undo this tutorial, the following should work fine for you in Ubuntu 8.04:


[SIZE="4"]Get rid of lock-screen launcher in panel:[/SIZE]
Right click on it, remove from panel.


[SIZE="4"]Delete the icon you copied for the launcher:[/SIZE]
```
sudo rm /usr/share/pixmaps/gnome-lockscreen.png
```


[SIZE="4"]Un-fix the menu settings:[/SIZE]
Applications -> Accessories -> Alacarte Menu Editor
System -> Preferences -> right click on Screensaver & select Properties
Change "command" box to "gnome-screensaver-preferences"
Click "Close"


[SIZE="4"]Remove the xscreensaver from starting on bootup:[/SIZE]
System > Preferences > Sessions click on the "Startup Programs" tab, select "xscreensaver -nosplash" then press the Remove button.


[SIZE="4"]Allow gnome-screensaver to be executable again:[/SIZE]
```
sudo chmod +x /usr/bin/gnome-screensaver
```


[SIZE="4"]Remove xscreensaver packages:[/SIZE]
```
sudo apt-get remove xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```


[SIZE="4"]Configure gnome-screensaver they way you like it[/SIZE]
Activate when idle if you wish
System -> Preferences -> Screensaver -> Click options you want


[SIZE="4"]Change Power Management back the way you want it:[/SIZE]
System -> Preferences -> Power Management -> Move the two sliders to your preferred settings


If you wish to lock the screen from your panel, you may add it yourself:
Right Click on the panel where you want the lock screen icon to appear, Select "Add to Panel".
Scroll down and select "Lock Screen", then Press the "Add" button.

You may have to restart Ubuntu for all these changes to take effect, but you may not have to, as I haven't tested this myself.

---

### Post by Elephantman5 on 2008-08-31
> **Rhubarb said:**
> To undo this tutorial, the following should work fine for you in Ubuntu 8.04:


...


If you wish to lock the screen from your panel, you may add it yourself:
Right Click on the panel where you want the lock screen icon to appear, Select "Add to Panel".
Scroll down and select "Lock Screen", then Press the "Add" button.

You may have to restart Ubuntu for all these changes to take effect, but you may not have to, as I haven't tested this myself.

I appreciate you writing this out.
Baby steps, for the layman, slow mind. 

sudo chmod +x /usr/bin/gnome-screensaver was what bothered me. (Or the other version of it.) Meh.

I was tired, thanks for the interesting tutorial though, Nobody Special. It was late, and now I know what the xscreensavers look like. ;)

---

### Post by ktechman on 2008-09-09
This worked on two out of three rigs, the *New* laptop with the ATI graphics card *cho-o-o-o-ked*, froze every time and the cheap on-board Nvidia graphics works like a charm.

---

