---
title: "[SOLVED] Disable F Spot"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by DanOrr123567 on 2008-11-06
HI ,

I have been trying to stop fspot opening when ever i plug in my camera. I have tried the following:

places>homefolder>edit>preferences>media and then selecting do nothing for photos.

But.... it still does it. I think it likes the attention.

Help

Cheers

---

### Post by alienexplorers on 2008-11-06
I got rid of it by removing it using synaptic.  I am happy just using gthumb to download and view my files.

---

### Post by the yawner on 2008-11-06
You only changed the preferences for Nautilus, the file manager. Try this instead: On the menu bar, click System > Preferences > Removable Drives and Media. The first tab is Cameras and under Digital Cameras the default is set to import digital photographs with F-Spot. Just uncheck the option if you want to stop importing.

---

### Post by roadowl on 2008-12-11
I can confirm that, on Hardy,  removing any entry for a digital camera in
system > preferences > Removable Drives and Media
nor deselecting this option, nor removing f-spot import (or some such)
from within gconf-editor (that was the first thing I tried) worked to
disbable f-spot.

The thing kept popping up.  Most annoying,

I have now resorted to the sledgehammer solution, i.e. purge f-spot
entirely.  If you don't hear from me again, that worked.

Meanwhile, this is definitely a bug.
Such persistence for any application has no place on FOSS systems.

---

