---
title: "Ubuntu 11.10 GTK+2 to GTK+3"
date: 2012-01-18
forum: Programming Talk
---

### Post by nickos on 2012-01-18
How can i use GTK3 instead of GTK2?As far as i can see when i type 
```
dpkg -l libgtk[0-9]* | grep ^i i 
``` I get :

```


ii  libgtk2-perl                           2:1.223-1build2                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                            2.24.6-0ubuntu5                         The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.24.6-0ubuntu5                         The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                          2.12.10-2ubuntu1                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                       2.24.6-0ubuntu5                         Common files for the GTK+ graphical user interface library
ii  libgtk2.0-dev                          2.24.6-0ubuntu5                         Development files for the GTK+ library

```

However i can see that some apps like gedit and epiphany seem to be using GTK3.
I installed the gnome shell but im still using GTK2.How can i move to GTK3?

---

