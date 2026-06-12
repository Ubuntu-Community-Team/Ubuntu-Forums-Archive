---
title: "[SOLVED] Turn off touchpad scrolling?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by baruch60610 on 2008-11-15
I have a laptop with a touchpad for a "mouse".  I am always accidentally scrolling text when all I want to do is move the cursor.  Since I don't use the scrolling feature of this touchpad, I would love to turn it off.

I once saw an article describing exactly how to do this, but all my Googling hasn't led me back to that article.

I recall there is some sort of a configuration file somewhere, containing a magical line that can be changed.  I would love to find this wonderful file again.  Could someone please help me?

Thanks.

---

### Post by talsemgeest on 2008-11-15
In versions of Ubuntu/Kubuntu 8.10 all of that stuff was controlled by the file /etc/X11/xorg.conf , however in 8.10 much of the job of the xorg.conf has been moved elsewhere.
However, there is still a chance that the options might be there.

To read the configuration file: ```
gedit /etc/X11/xorg.conf
```

To edit it: ```
gksudo gedit /etc/X11/xorg.conf
```

Hope this helps :)

---

### Post by baruch60610 on 2008-11-15
[Update: /etc/X11/xorg.conf was, indeed, the correct file.  Many thanks to talsemgeest!]
Hi, thanks for your response.  My 8.10 upgrade was an unmitigated disaster, so I reinstalled 8.04.  I actually looked in the xorg.conf file, and couldn't find any lines referring to scrolling.

As I recall, I needed to set some parameter such as 'VertScroll' to zero, but I cannot for the life of me remember which file that was in.

It wouldn't bother me so much, except that I already had found this article and then lost it (lost my bookmarks).  Knowing there is a fix that works just irritates me even more.

Anyway, thanks for your suggestion.

---

### Post by baruch60610 on 2008-11-15
Just to clarify how this was solved:

Using:

sudo nano /etc/X11/xorg.conf

you find where your input device (in this case a touchpad) is described.  For my computer it was:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
EndSection

```
In order to turn off the scrolling, you change "HorizEdgeScroll" and "VertEdgeScroll" to "0".  Then save and restart the X server (log out, then log back in).

I am grateful to talsemgeest for pointing me in the right direction.

---

### Post by talsemgeest on 2008-11-15
Awesome, I am glad you got it fixed.

---

