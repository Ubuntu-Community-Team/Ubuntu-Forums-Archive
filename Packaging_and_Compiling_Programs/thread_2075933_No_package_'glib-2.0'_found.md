---
title: "No package 'glib-2.0' found?"
date: 2012-10-24
forum: Packaging and Compiling Programs
---

### Post by Coyotemg on 2012-10-24
Im new to ubuntu. Im going to start programming Python and i will use GTK+ 3
I've tried lots of times to install the gtk+-3.4.4 following the tutorial and when i try the $ ./configure i got this error:

configure: error: Package requirements (glib-2.0 >= 2.32.0    atk >= 2.2.0    pango >= 1.30.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.26.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

How do i solve this?

---

### Post by Herby Pepper on 2012-10-25
I would try to do what ubuntu wants.
install required packages:
sudo apt-get install glib-2.0 atk pango cairo cairo-gobject gdk-pixbuf-2.0

---

### Post by Coyotemg on 2012-10-26
I've started installing the dependencies. Installed glib,atk,cairo,cairo-gobject but when i try to install pango i get this error: "Must have at least one backend to build Pango". I'm looking for some help but nothing i found solved it.

---

### Post by oldos2er on 2012-10-26
Moved to Packaging and Compiling Programs.

---

### Post by scottstensland on 2013-02-13
when U issue this at command line :

```

sudo apt-get install pango

```it just says its not found - not too helpful,
more verbose way to install or browse is :
Synaptic Package Manager which U install using :

```

sudo apt-get install synaptic

```to launch it tap the meta key (microsoft emblem or apple key)
which brings up ubuntu Dash where you can search for synaptic.
Or from command  issue :  

```

sudo apt-get install gir1.2-pango-1.0

```

If you're compiling code and it needs some package,
typically U need that package's headers which will be
in a package with dev suffix as in xxxxx-dev

---

