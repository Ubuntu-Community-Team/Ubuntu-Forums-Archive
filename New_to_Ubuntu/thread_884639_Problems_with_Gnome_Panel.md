---
title: "Problems with Gnome Panel"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by pete-the-meat on 2008-08-09
Whenever I log into my gnome session I get the following three error messages in little pop up boxes:

The panel encountered a problem while loading OAFIID:GNOME_Panel_TrashApplet".
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

I have tried the following approaches:

```
sudo dpkg-reconfigure xserver-xorg
sudo aptitude-reinstall gnome-applets gnome-applets-data
```

and backing up my /etc/X11/Xsession to a copy from quite a few months ago I had kicking around.

I am now fresh out of ideas and really could do with some help for while this error continues I cannot get access to yeahconsole, the screenlets manager or any of the screenlets or any of the effects i set up in compizfusion.

Can anyone help?

Thanks in advance :)

Pete

---

### Post by pete-the-meat on 2008-08-09
Polite bump

The solving of this problem is essential to my continued sanity ;)

---

### Post by SunnyRabbiera on 2008-08-09
I have had issues like this, its just best not to reload the apps and then when re loading gnome put the apps back in.
I remember the trash applet having big issues for me

---

### Post by pete-the-meat on 2008-08-10
Reloading gnome doesn't solve the problem for me - I used killall gnome-panels and when it reloaded the error message reoccured. I accidentally clicked the "Delete" button instead of the "Do not Delete" button on the error dialogs so the message won't crop up again, but I am no closer to getting the applets back. :(

---

### Post by sidewalkcynic on 2009-02-09
I'm having this problem with the StickyNotes and SystemMonitor applettes

Anybody come up with a solution?

---

### Post by LowSky on 2009-02-09
Delete your gnome config file form within nautilus.

/home/.gnome2 (I think)

that should reset your panels



remember if you break it you get to keep both pieces

---

### Post by kender42 on 2009-02-09
I tried all the sugesstions here, since I am having the same problem, but none of them have worked. I need fast user switcher and the volume control to work for my business. Also the Power button no longer allows me to shut down or restart. The only options I have now are Log out and switch user. How do I fix these problems.

---

### Post by sidewalkcynic on 2009-02-09
> **LowSky said:**
> Delete your gnome config file form within nautilus.

/home/.gnome2 (I think)

that should reset your panels

remember if you break it you get to keep both pieces
Hold on here, you're making me nervous. In /.gnome2 there is no config file, but there is a session file that has the names of the applications on my panel.

So, I'm seeing that if I delete the /.gnome2, I'll have to re-do my panel and background etc, And that should fix the applette problem???

There is a /.config directory in my Home directory, but it doesn't seem to have anything regaurding the panels???

---

### Post by sidewalkcynic on 2009-02-11
Well, I didn't do anything like deleting or editing any files, but somehow the applettes are loading now without any problems. Maybe, I replaced them on the panel in seperate sessions - I cannot remember for sure. And/or, maybe I replaced them on the panel in a different order.???

Anyway, it seems to be working okay, and I have added another applette, as well.

---

