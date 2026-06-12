---
title: "I installed a load of new ubuntu icons and its changed my firefox - help?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by g2bandrew on 2008-07-15
I installed a load of ubuntu icons and its changed my firefox icons. The annoying thing is that its changed the close tab button and i preffered that as it was before. Is there anyway to change the buttons back to default? It's set to be the default at the minute and its still showing those.

---

### Post by BandD on 2008-07-15
Firefox 3.0 uses the system icon set for it's icons--or at least tries to.

If you want the close tab icon fro your previous icon set then you will either have to use that icon set, or find out where the original icon is stored (probably either /home/USER/.icons or /usr/share/icons) and take that icon in every size that it exists within the original icon set and copy/replace it into the icon set you are currently using (probably located in /home/USER/.icons).

i.e. usually there are a bunch of folders in the icon set folder labeled by size (24x24, 48x48 etc) and within those are 'category folders (actions, places etc).  You will be interested in the actions folder.  Look for any icons called gtk-close.png (or .svg), stock_colse.png (or .svg), and window-close.png (or .svg).

Hopefully that makes sense.

---

### Post by g2bandrew on 2008-07-15
Do you know what they use for the close tab bit and what that image is called because i've looked through all of the theme's images and i can't find it.

---

### Post by BandD on 2008-07-16
I'm pretty sure that it is in the ACTIONS folder and a file called one of three names:

gtk-close.png
stock_close.png
window-close.png

try this in a terminal:

```
locate gtk-close.png
```

Post the results back here.

---

