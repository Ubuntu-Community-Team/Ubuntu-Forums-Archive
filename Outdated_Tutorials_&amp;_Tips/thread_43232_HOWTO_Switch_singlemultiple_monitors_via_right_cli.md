---
title: "HOWTO: Switch single/multiple monitors via right click"
date: 2005-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by huwshimi on 2005-06-21
I have my laptop attached to a second monitor when it is at home, however when I take it anywhere some applications get put where that monitor used to be. Hopefully in the future someone will make a nice GUI to switch between one or two monitors (or it'll happen behind the scenes like magic). Until then, this is my solution that uses a right click script and a restart of X.

A warning. During this process you are going to edit your xorg.conf. If you break this then you may not have any graphical interface. However, I assume that anyone who has gotten past the stage of setting up a multiple monitor desktop is well aware of the risks involved.

First we need to assume that you have your xorg.conf set for multiple monitors (to do so search these forums). Next you need to create copies of your xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_multiple_monitors.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_single_monitor.conf
```
Now we edit xorg_single_monitor.conf for use with only one monitor (if you have a backup of the original you might be able to use that). As above we are assuming you're xorg_multiple_monitors.conf is already set up correctly.

```
sudo gedit /etc/X11/xorg_single_monitor.conf
```
Having created the copies of xorg.conf, we can now make the scripts.

```
gedit $HOME/.gnome2/nautilus-scripts/Single\ \(duplicate\)\ desktop
```

Enter the following into the new file:

```
sudo cp /etc/X11/xorg_single_monitor.conf /etc/X11/xorg.conf
```
Save that file, and do the same for multiple monitor setup.

```
gedit $HOME/.gnome2/nautilus-scripts/Extend\ desktop\ to\ second\ monitor
```
Enter the following into the new file:

```
sudo cp /etc/X11/xorg_multiple_monitors.conf /etc/X11/xorg.conf
```
Save again. Now we make these scripts show in the menu.

```
chmod +x $HOME/.gnome2/nautilus-scripts/Single\ \(duplicate\)\ desktop

chmod +x $HOME/.gnome2/nautilus-scripts/Extend\ desktop\ to\ second\ monitor
```
Now when you want to switch between the two setups, you right click on the desktop or in a folder, go to: Scripts - > Extend desktop to second monitor, or Scripts - > Single (duplicate) desktop. Select the appropriate one of these options and hit Control-Alt-Backspace. And (hopefully) there you have it.

Now another word of warning. This process replaces your xorg.conf, so when you make a change to one file you HAVE to make it to the others. Also I have not really tested this, so use it at your own risk.
If what I have written is wrong or is going to break something, would someone please tell me.

---

### Post by Ninnghizidha on 2005-06-21
Ever thought of the ServerLayout-Section?

```

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.


```

---

### Post by huwshimi on 2005-06-21
[QUOTE=Ninnghizidha]Ever thought of the ServerLayout-Section?

```

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.


```[/QUOTE]

Ok. So maybe I'll do a bit more research into a better method. If anyone knows of a better way then please let me know. For now I'll look into ServerLayouts. My original method is REALLY ugly. Thanks for letting me know Ninnghizidha.

---

### Post by Sionide on 2005-06-22
I've still not been able to get dual-mons working - anyone know of a good HOWTO or something for it? It'll be using the one gfx card on my laptop. At the moment, all I can do is make the other monitor replicate the laptops which is annoying - the screen I want to use also has a higher resolution, although I have a spare one of the same res.

---

