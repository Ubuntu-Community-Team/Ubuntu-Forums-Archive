---
title: "Problem with xmodmap"
date: 2011-06-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Mesanna on 2011-06-12
Does anyone know of any problems with xmodmap in Oneiric?

I have a very simple .xmodmap file that I've been using over the past couple of years. All it really does is swap the functionality of two mouse buttons over. However it isn't loading in Oneiric. I had started from a Natty installation, where the mouse-mapping worked fine, then did an upgrade to Oneiric. But it no longer functions now. I tried removing it and rebooting, then putting it back in my home folder and logging out then back in again, hoping it would be recognised but no luck.

Is xmodmap still in use or has it been replaced by something else that I don't know about? Has anyone else had any problems with an xmodmap file?

---

### Post by vhaarr on 2011-06-13
Try renaming it .Xmodmap :-P
Works for me at least.

---

### Post by Mesanna on 2011-06-13
Nope, that didn't work unfortunately. I've tried .Xmodmap and .xmodmap but neither is recognised.

Any other ideas?

---

### Post by lucazade on 2011-06-13
I usually launch xmodmap from session autostart to configure my logitech mouse, without using the .Xmodmap file..

something like this "xmodmap -e pointer = 1 8 3 4 5 6 7 2"

haven't tried yet xmodmap in OO so I can't confirm if the issue is present.

---

