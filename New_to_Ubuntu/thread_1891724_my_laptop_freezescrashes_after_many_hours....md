---
title: "my laptop freezes/crashes after many hours...?"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by werty2010 on 2011-12-06
i usually leave it open for downloading in the night and turn it off in the morning.
but very often in the morning after i login through the screenlock(no screensaver installed), although i can move the mouse, nothing else responds,forcing me to "hard" shutdown.
could someone help figure this out?

---

### Post by Ricx94 on 2011-12-06
I'm not sure, but maybe a screensaver would help in this regard.

to uninstall gnome screensaver;
```
sudo apt-get remove gnome-screensaver
```
to install xscreensaver and all extra stuff:
```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod
```
to start xscreensaver configuration tool:
```
xscreensaver-demo
```
Click OK to both prompts asking to turn-off Gnome Daemon and to start xscreensaver-daemon respectively.

To create a rule to start the xscreensaver daemon on login, click on the Dash home launcher and type: startup applications. Click on the Add button and enter a name for the rule and to start XScreenSaver on login use this command:
```
xscreensaver -nosplash
```

(all info came from [http://www.n00bsonubuntu.net/content/how-to-install-and-enable-xscreensaver-on-ubuntu-11-10/](http://www.n00bsonubuntu.net/content/how-to-install-and-enable-xscreensaver-on-ubuntu-11-10/))

---

### Post by Paqman on 2011-12-06
> **werty2010 said:**
> 
could someone help figure this out?

Check in your Log File viewer for whatever the last things the system reported before crashing were. If you need help, post up the contents of the log here inside some [noparse]```

```[/noparse] tags.

---

### Post by davetv on 2011-12-06
deleted by poster

---

### Post by Diametric on 2011-12-06
> **werty2010 said:**
> i usually leave it open for downloading in the night and turn it off in the morning.
but very often in the morning after i login through the screenlock(no screensaver installed), although i can move the mouse, nothing else responds,forcing me to "hard" shutdown.
could someone help figure this out?

Is there is suspend/hibernate setting that you could adjust?

---

