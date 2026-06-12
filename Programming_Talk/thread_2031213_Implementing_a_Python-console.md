---
title: "Implementing a Python-console"
date: 2012-07-21
forum: Programming Talk
---

### Post by DarkAmbient on 2012-07-21
Hiya!

I'm building a Gtk/Python application which has a integrated console. I'm using Vte.Terminal which works just fine.

The thing is that I would like it to be a python-only console. A quick workaround could be to call python directly after creating the object. But then the user could just call quit() from the console to get back to the system-environment. 

Any ideas about this? Could really use some help. 

Thanks

---

### Post by MadCow108 on 2012-07-21
you could just use an already existing embeddable python console (as the default one really sucks)
e.g. ipython or bpython

check out accerciser, it has a builtin ipython console in gtk (make sure to base your code on the trunk version, the one in precise is a little old and has some issues)
the spyder ide does something similar for both python and ipython (also gtk I think)

ipython also ships the qtconsole which is en essence a python console on steroids easily embeddable in qt apps.

---

### Post by DarkAmbient on 2012-07-21
Hi, thanks a bunch for your help!

Found this gtk implementation of IPython [http://wiki.ipython.org/Old_Embedding/GTK#ipython_view.py]("http://wiki.ipython.org/Old_Embedding/GTK#ipython_view.py") A modified version of that Accerciser-project you mentioned. 

The only annoying thing is that its written with the old 'gtk', not the new 'Gtk' imported from the gi.repository in Ubuntu. (2-3 weeks old to Gtk and python so I've yet to learn alot) But I'm gonna try to rework that script to use Gtk instead. (I guess it's needed atleast, I'm not sure on the difference between gi.repository.Gtk and "old gtk", other than some syntax and staticsnames)

---

### Post by MadCow108 on 2012-07-21
the page is titled old for a reason, it also won't work with newer ipython versions.

use the one from their git repository (not svn):
[http://git.gnome.org/browse/accerciser/tree/plugins/ipython_view.py](http://git.gnome.org/browse/accerciser/tree/plugins/ipython_view.py)
[http://git.gnome.org/browse/accerciser/](http://git.gnome.org/browse/accerciser/)

it also uses the gi repository.

---

### Post by DarkAmbient on 2012-07-22
> **MadCow108 said:**
> the page is titled old for a reason, it also won't work with newer ipython versions.

use the one from their git repository (not svn):
[http://git.gnome.org/browse/accerciser/tree/plugins/ipython_view.py](http://git.gnome.org/browse/accerciser/tree/plugins/ipython_view.py)
[http://git.gnome.org/browse/accerciser/](http://git.gnome.org/browse/accerciser/)

it also uses the gi repository.

Ah, right :oops: Thanks to one of your links I got a working pythonconsole! Will try edit it some to replace the prefix with something else, as the numbering in the "prefix" keeps increasing. The colours is a bit of as well. 

I'll try editing it some more tonight. :) Great stuff never the less! Thanks

---

