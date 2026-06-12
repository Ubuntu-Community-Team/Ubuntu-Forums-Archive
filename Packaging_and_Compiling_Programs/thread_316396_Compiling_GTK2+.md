---
title: "Compiling GTK2+"
date: 2006-12-10
forum: Packaging and Compiling Programs
---

### Post by juantovarm on 2006-12-10
I have been trying to compile gtk2++, and after a long time resolving dependencies, i get this error

checking for XRRUpdateConfiguration in -lXrandr... yes
checking for X11/extensions/Xrandr.h... yes
checking Pango flags... configure: error:
*** Pango not found. Pango built with Cairo support is required
*** to build GTK+. See [http://www.pango.org](http://www.pango.org) for Pango information.

I have already installed Pango...

juan@juan-desktop:~/Desktop/gtk+-2.10.6$ whereis pango
pango: /etc/pango /usr/lib/pango /usr/local/etc/pango /usr/local/lib/pango

any ideas???:confused: ](*,) :-k

---

### Post by engla on 2006-12-11
Make sure you have installed the package `libpango1.0-dev`. Always look out for the **-dev** packages when satisfying build-dependends!

This command should return something if pango is installed for development:
`pkg-config --cflags --libs pango`

---

### Post by juantovarm on 2006-12-11
i had that package already installed, i ran the command and got this

juan@juan-desktop:~/Desktop/todo/gtk+-2.10.6$ pkg-config --cflags --libs pango
-I/usr/local/include/pango-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include  -L/usr/local/lib -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  

I then reinstalled all the pango dependencies and tried to configure gtk2+ and got the same error ](*,) ](*,) ](*,) ](*,)

---

### Post by engla on 2006-12-11
I'm sorry for not knowing how to solve this then. This should be a lead: "Pango built with Cairo support" -- I don't know about that, but you can search/google for that error.

---

