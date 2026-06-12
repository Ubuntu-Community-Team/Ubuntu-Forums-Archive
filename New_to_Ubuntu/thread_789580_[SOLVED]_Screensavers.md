---
title: "[SOLVED] Screensavers?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-10
I didn't know where to put this.

I am looking for a simple screensaver that will show a clock or the time. I have googled for one but haven't found any. I find a lot for windows. 

Also, where would be a good place to look if I would like to make my own? What do I need to know first?

---

### Post by drs305 on 2008-05-10
Here is one option - modify the GLText screensaver (System, Preferences, Screensaver, GLText). It's not an analog or digital clock, but it does show the time.

First, backup the gltext.desktop file which contains the text displayed on the screensaver:
```
sudo cp /usr/share/applications/screensavers/gltext.desktop /usr/share/applications/screensavers/gltext.desktop.bak
```

Next, open the gltext.desktop file:
```
gksu gedit /usr/share/applications/screensavers/gltext.desktop
```


Change the line:
Exec=gltext -root

To:
Exec=gltext -root -front -text '%l:%M:%S %p'

You can modify the above to include various switches to suit your preferences.

Save and enjoy. If you don't like the result, just delete gltext.desktop and rename the backup file back to the original.

Note: assembled from various sources...

---

### Post by chk9 on 2009-03-23
Found an Analog clock as screensaver :D

> [http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html](http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html)


I needed to add this lib to make it work:
> sudo apt-get install libgtk2.0-dev


Cool ;)
Have Fun

_____________
Found it via thread:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46548](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46548)

---

