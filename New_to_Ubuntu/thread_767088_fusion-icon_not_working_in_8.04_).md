---
title: "fusion-icon not working in 8.04 :)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by neoMAX on 2008-04-25
Here is the terminal's output of fusion-icon:

```

:~$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
Starting gtk-window-decorator
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

The icon appears in the tray and is functional, but if I close or CTRL-C the terminal, it closes the icon. I expect I should edit the config as the terminal suggests, but I've no clue where to begin. :confused:

---

### Post by Vadi on 2008-04-25
Try doing alt+f2 and "fusion-icon". Then you don't have to worry about the terminal window.

Also, don't worry about the gconf thing, it's not important afaik.

---

