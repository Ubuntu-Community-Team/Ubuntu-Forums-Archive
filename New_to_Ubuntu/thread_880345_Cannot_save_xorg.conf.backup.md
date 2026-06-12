---
title: "Cannot save xorg.conf.backup"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jcameron89 on 2008-08-04
I'm trying to save the xorg.conf file, after making some changes in the nvidia-settings tool. However, whenever I attempt to save the new file, it prompts me with the following message in terminal:

"ERROR: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

I can't even manually go into the x11 folder and save a copy of the file. I'm trying to use nvidia-settings to utilize both of my monitors. The tool recognizes my second monitor, and even provides all of the relevant information for it (native resolution it will use, refresh rate, etc) but I can't save the xorg.conf file. Anyone have any ideas?

---

### Post by ConMan318 on 2008-08-04
Open nvidia-settings with
```

sudo nvidia-settings

```
and it should let you save it.

If you just want to back it up, use
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

---

### Post by jcameron89 on 2008-08-04
I'm just curious; when I'm using "Separate X Screen" on the second monitor, is it running a second instance of GNOME or something? If so, is there any way to simply do a standard shared desktop space, similar to what Windows or Mac OS usually sets up?

---

### Post by ConMan318 on 2008-08-04
Try hitting 'configure' at the X server display config window and select 'disabled'.  That might do it, but I am not sure.  Try that, hit 'apply' and then log out/back in.

It might just disable the monitor, not disable the separate configuration.

---

### Post by Paqman on 2008-08-04
> **ConMan318 said:**
> Open nvidia-settings with
```

sudo nvidia-settings

```


That should probably be:
```

gksu nvidia-settings

```
by the way. Always use gksu or gksudo for graphical apps on Gnome. It's kdesu for KDE.

---

