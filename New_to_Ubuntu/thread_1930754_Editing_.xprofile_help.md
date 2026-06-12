---
title: "Editing .xprofile help"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by ianhoyle on 2012-02-24
Im trying to use a tutorial to set my screen resolution to 1366x768 and I get to a part where I need to edit .xprofile to make the changes run every time I boot. I'm new to Linux, just came from Win7 about a week ago. here is my problem.

I run:
```
sudo gedit ~/.xprofile
```

input password.. get output
```
(gedit:2246): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ALLX9V': No such file or directory

(gedit:2246): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

and .xprofile opens up in gedit.

I then put the following lines on .xprofile
```
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync

xrandr --addmode VGA1 1366x768_60.00 

xrandr --output VGA1 --mode 1366x768_60.00
```

and hit save. as soon as I click save Terminal kicks out another line:

```
(gedit:2246): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

and these 2 more when I close it:
```
(gedit:2246): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3E6HAW': No such file or directory

(gedit:2246): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

I had done this before and it worked perfectly but since a re-install of ubuntu (decided to wipe it all to get rid of the windows partition)in wont work..

It acts like it is switching the resolution when it starts to boot.. my screen blinks to "no signal" then returns with the log-in splash screen shifted weird (like it use to when it all worked smoothly) then flickers right back.. 

once booted I run:
```
xrandr
``` 

just to verify the resolution and it has gone back to default.

however running:
```
xrandr --output VGA1 --mode 1366x768_60.00
```

will easily restore me to the res I want.

any advice? I'm not exactly sure how .xprofile works but i'm guessing it is some sort of ".exe"(windows,I know)telling the system a series of code to run on boot? I can't remember if I got the "gtk-WARNING" output before when it worked but I feel like my problem lies in that somewhere.

---

### Post by ajgreeny on 2012-02-24
What tutorial was this?  It seems an unusual way to deal with a resolution problem.  There is also no need to use gedit with root permissions for a file in your /home, so just use **gedit**, not **sudo gedit**.

Incidentally it should be **gksu gedit **or **gksudo gedit** not sudo gedit; sudo is for terminal command line applications, not GUI applications such as gedit.

---

### Post by ianhoyle on 2012-02-24
thanks for the reply [_[COLOR="Blue"][SIZE="2"]HERE[/SIZE][/COLOR]_]("http://www.myapitips.com/2011/11/02/how-to-change-monitor-resolution-in-ubuntu-11-10/") is a link to the tutorial. if you know a better way i'd love to know it... i'm new to linux so be easy on me.

---

### Post by ianhoyle on 2012-02-25
Bump!.. still having trouble with this

---

