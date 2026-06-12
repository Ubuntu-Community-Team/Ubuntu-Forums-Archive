---
title: "Need to fix very small font size"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-05-12
It's like this: I installed Ubuntu then tweaked the settings a bit. It works fine. When I installed XFCE, the fonts in the Applications, Panel, almost everything except Firefox is very small. 

Where can I adjust the font size and select fonts? Thanks!

---

### Post by dizee on 2008-05-12
Applications > Settings > Settings Manager - click on User Interface and the font options are there. Perhaps putting the font to size 10 instead of the default 9 will help.

If you installed only a core version of Xfce and not Xubuntu desktop, install "xfce4-mcs-manager", "xfce4-mcs-plugins" and "xfce-mcs-plugins-extra" first.

---

### Post by JazonEsti on 2008-05-13
Did that, but then for some odd reason it doesn't seem to scale well. The menu in Firefox (including File, Edit, etc) is definitely Arial 16, but the rest of the system's fonts is still very small. The font size does change, but not much.

The font size in Kontact does not seem to be affected, though. It's so small its almost unreadable. 

I'd like to take a screenshot, only screenshot doesn't seem to work unlike in GNOME.

---

### Post by dizee on 2008-05-13
There is a screenshot plugin for the Xfce panel. It should be there when you right-click the panel and select "Add New Item". If it isn't install "xfce4-screenshooter-plugin".

What resolution is your screen? It might be that Xfce is selecting the wrong font DPI - have a play around with that setting.

---

### Post by JazonEsti on 2008-05-13
Resolution is at 1024x768 in my 17" monitor (which is the ideal resolution). I have set the fonts in the User Interface and Window Manager to Arial 16. Please look at the screenshots I have attached here. 

In desktop1.png, it's shown that KOrganizer's fonts are very small. That's certainly not Arial 16

In desktop2.png, you can see Firefox and the Menu looks like it's Arial 16, but the one on top (PinoyPC - Home - Mozilla Forefox)does not look like Arial 16

Desktop3.png compares the Applications Menu with Firefox's Menu fonts. There's certainly a discrepancy.

On all 3 screenshots, the fonts at the bottom of the screen are also small.

---

### Post by dizee on 2008-05-13
That is very strange.

This post may be of use: [http://ubuntuforums.org/showpost.php?p=2441482&postcount=5](http://ubuntuforums.org/showpost.php?p=2441482&postcount=5)

Run this to check the current DPI: ```

xdpyinfo | grep resolution
```

---

### Post by JazonEsti on 2008-05-13
The result is:
```

resolution:    59x59 dots per inch

```

Is this the problem?

---

### Post by dizee on 2008-05-13
Probably yes. For example on my 1024×768 15.4" screen it returns ```
  resolution:    86x84 dots per inch

```

The Font DPI in the Xfce Settings Manager > User Interface dialog is set to 75 on mine. Try changing that - you will need to logout and login again each time you change it.

---

### Post by JazonEsti on 2008-05-13
I cannot seem to find the Font DPI in the said location. Do I have to install something first?

---

### Post by dizee on 2008-05-13
Have you installed "xfce4-mcs-plugins" and "xfce-mcs-plugins-extra"?

It should look like the dialog below.

If you can't find it there, try [this](http://ubuntuforums.org/showpost.php?p=2441482&postcount=5) if you haven't already:
[quote=fwojciec]Edit /home/*username*/.config/xfce4/Xft.xrdb
Add "Xft.dpi: 96" to the end of the file - that assumes that your DPI is set to 96 in Gnome/KDE, the idea is to make the DPI setting consistent in all desktop environments.
Restart XFCE (don't save the session - just in case XFCE overwrites this setting - or just edit the file while in Gnome session).

That should fix it.
[/quote]

---

### Post by JazonEsti on 2008-05-16
Sorry for the late reply, I was busy. 

I cannot find xfce-mcs-plugins-extra. xfce-mcs-plugins is already installed.

Is it safe to follow the commands in the post you put here? Thanks!

---

### Post by dizee on 2008-05-16
Sorry that should have been "xfce4-mcs-plugins-extra". 

Those instructions should be perfectly safe to follow as well.

---

### Post by JazonEsti on 2008-05-16
Search does not reveal it. Do I have to allow some repository or something?

---

### Post by dizee on 2008-05-16
Just try the other instructions then. I don't think the extra plugins have the font dpi setting in them, but it was just to be sure.

If that doesn't help, have a look at this thread: [http://ubuntuforums.org/showthread.php?t=220502](http://ubuntuforums.org/showthread.php?t=220502)

Seems to be a similar issue.

---

