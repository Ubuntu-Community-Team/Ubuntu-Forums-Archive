---
title: "Change the background settings (options) from terminal"
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by hakermania on 2011-07-25
In 11.04 and former it was:
```
gconftool-2 --type string --set /desktop/gnome/background/picture_options zoom/center/scaled/etc
```What about now :) ?

EDIT:
Also, if anyone knows how to change the lock screen wallpaper :)
The 11.04 and former was:
```

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set /desktop/gnome/background/picture_filename --type string /path/to/picture

```

EDIT2: Found the first one!
It is:
gsettings set org.gnome.desktop.background picture-options zoom/etc
What about the lock screen?

---

### Post by drs305 on 2011-07-25
You can change the Desktop background with the following command. I've placed the default filename into the command:
```

gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/warty-final-ubuntu.png
```

If you want to change it via the GUI, open dconf-editor (install dconf-tools) and navigate to /org/gnome/desktop/background

---

### Post by hakermania on 2011-07-26
Thanks for your answer. I know how to change the current wallpaper :)
I need to know how to change lockscreen...

---

