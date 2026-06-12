---
title: "Reduce padding in GTK"
date: 2009-09-23
forum: Programming Talk
---

### Post by spupy on 2009-09-23
Maybe it's part of GNOME's HIG, but GTK has ridiculous padding on some widgets. I've edited the gtkrc file of the current theme that I'm using, trying to reduce the unused space, but I was not very successful. Next I will dive into the code of the Murrine engine (that I mostly use), and try to see what I can do there. (I guess the padding is more due to the rendering engine (that is the theme engine), rather than gtk itself. Am I correct?)
Have any of you done anything in that direction?

(To further illustrate the excessiveness, compare GTK with Aqua.)

---

### Post by SledgeHammer_999 on 2009-09-23
Are you looking for a theme like [this?](http://gnome-look.org/content/show.php/human_ultracompact?content=81128&PHPSESSID=45f7cc85864c132d7e10fbe91b0b2ab7)

If yes, then take a look at it's "code". Similar themes on gnome-look are named "compact".(I think)

---

