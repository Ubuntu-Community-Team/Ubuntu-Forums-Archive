---
title: "GTK won't compile - missing GLIB?"
date: 2011-02-14
forum: Programming Talk
---

### Post by searchfgold6789 on 2011-02-14
Hi. I hope someone can help me with this rather sticky problem.
I recently downloaded a Texas Instruments TI-84 Graphing calculator emulator because I need a graphing calculator for school. I entered the directory for the tool, it was somewhere deep in the labyrinth of my home directory, and fount out that it needed GTK+ in order to do its thing.
So I googled GTK+ and downloaded a copy of it. I entered that directory, tried ./configure, and found out it need Glib to do its thing. It also gave me the website to download Glib, which saved me about 3 seconds of googling.
I went and installed Glib.
So here's the problem - Now, when I go back into the GTK+ directory and try ./configure again, it gives me the error:```
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: 
*** GLIB 1.2.0 or better is required. The latest version of GLIB
*** is always available from ftp://ftp.gtk.org/.
```I figured out how to point it to Glib, but I don't know where Glib is installed. Does anyone know what I should do? I would really appreciate help because I need the emulator instead of going out to buy a $100 graphing calculator :(
 - search

---

### Post by searchfgold6789 on 2011-02-14
UPDATE: I found out that the emulator had one other dependency, but I downloaded and compiled that successfully. Now the only thing it needs is GTK+, and the only thing that needs is Glib, which I installed but it isn't finding.

---

### Post by johnl on 2011-02-14
Hi, 

You don't need to chase down and compile all the prerequisites for the emulator; you can get these from the Ubuntu repositories like so:
```

sudo apt-get install libgtk2.0-dev # installs the gtk2.0 development files

```


Try this, then run your emulator's configure script again.  If it complains about other dependencies, you can install those in the same manner. (try sudo apt-get 'install lib<DEPENDENCYNAME>' and hit tab twice, then choose the appropriate -dev package). 

For example, if it complains that it needs foobar 1.4, try 'sudo apt-get install libfoobar1.4-dev'

---

### Post by searchfgold6789 on 2011-02-14
:shock: Oh.
Will try that nao -
EDIT: It worked! thank you.

---

