---
title: "GTK list widget"
date: 2010-04-28
forum: Programming Talk
---

### Post by lexe-cc on 2010-04-28
Hi everyone,

I've searched and tried multiple things to program the following thing:

I'd like to display pictures in a list and I need the possibility to select one picture if neccesary in that list. You can compare it with the background selector of the ubuntu OS. 
Also, I will need a second list widget that only has one row. But I guess this would only need the same widget but with another configuration of it.

I tried a gtk.table but this gave me no possibility to select the pictures.
I tried a gtk.treeview but this gave me no possibility to select only one pictures. (the whole row gets selected)

Thanks in advance!
Lexe

---

### Post by steeleyuk on 2010-04-28
gtk.IconView is the one used to select images in the GNOME appearance properties dialog.

---

### Post by lexe-cc on 2010-04-28
Thanks for your quick reply, I will have a look at it :)

---

### Post by lexe-cc on 2010-04-28
Okay this is exactly what I'm looking for. However, is it possible to have the widget placed in a scrolled window, and let it expand ONLY horizontally? (I only need one row ..)

---

