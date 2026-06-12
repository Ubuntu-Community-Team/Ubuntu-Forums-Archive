---
title: "Is there a way to speed up this?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Vicfred on 2008-05-30
Well, this is the problem, I have a directory with 11,000 images when I open it on gnome it takes too much to load the complete folder, is there a way to reduce the image thumbnail quality or something? even with the 50% thumbs the folder is taking too much time :(

---

### Post by drs305 on 2008-05-30
Are you using nautilus? 

Edit > Preferences > Views > There are some Icon View settings that may help.

There is also a setting to limit any thumbnail over a certain number of bytes (5242880 is the default). I don't think this is really what you are looking for but you could reduce the size. However, I think if the image is below the limit you set it won't display at all. You can also turn them all off here.

If you want to take a look, open gconf-editor and go to:
/apps/nautilus/preferences/thumbnail_limit

---

