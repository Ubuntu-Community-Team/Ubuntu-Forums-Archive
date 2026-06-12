---
title: "Python + GTK (PyGTK) + Glade tutorials?"
date: 2005-05-10
forum: Programming Talk
---

### Post by felipe on 2005-05-10
Hi, i am searching for a python tutorial on how to create simple projects in PyGTK/PyGNOME + Glade.

the ones I found on google are a bit contraddictory because i think they are targeted towards different versions of glade or pygtk or python etc...

i'd just like to:

1) design a simple interface in glade
2) use the glade interface to write some really simple python app like:

```

#!/usr/bin/env python

import <something _anyone_ has already installed by default or similar>

def MyCoolFunction():
        bla bla bla #most notably write and read (xml) config files

widgetTree = <the_magic_word_here>("project.glade")

dic = { "on_cool_event" : MyCoolFunction }

widgetTree.signal_autoconnect (dic)

gtk.main ()

``` 

Any clue? I'd like to write some simple frontends to (not-only)Ubuntu/GNOME common user configuration tasks, so i need some commented examples glued in a nice tutorial :)

so far i found:

[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/) #cool, but it relies on the SimpleGladeApp.py library... Bad (for my needs)

[http://www.arson-network.com/index.php?class=tutorial&subargs=430](http://www.arson-network.com/index.php?class=tutorial&subargs=430) #too little info, just a small page

[http://sjbrown.users.geeky.net/metagame-sector/tutorial.html](http://sjbrown.users.geeky.net/metagame-sector/tutorial.html) #very nice, but guess it's oriented towards an older version of glade/pygtk/whatever because it doesn't work :/

thanks for your help

---

### Post by bihe on 2005-05-11
[QUOTE=felipe]
[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/) #cool, but it relies on the SimpleGladeApp.py library... Bad (for my needs)
[/QUOTE]

why is this bad for your needs. SimpleGladeApp.py is just one small python class,
which loads the glade.xml file and auto-connects the signals ...

```

29 class SimpleGladeApp(dict):
30     def __init__(self, glade_filename, main_widget_name=None, domain=None):
31         gtk.glade.set_custom_handler(self.custom_handler)
32         if os.path.isfile(glade_filename):
33             self.glade_path = glade_filename
34         else:
35             glade_dir = os.path.split( sys.argv[0] )[0]
36             self.glade_path = os.path.join(glade_dir, glade_filename)
37         self.glade = gtk.glade.XML(self.glade_path, main_widget_name, domain)
38         if main_widget_name:
39             self.main_widget = self.glade.get_widget(main_widget_name)
40         else:
41             self.main_widget = None
42         self.signal_autoconnect()
43         self.new()

```

the important line is 
  37  self.glade = gtk.glade.XML(self.glade_path, main_widget_name, domain)
where the glade.xml file is loaded. i've just started to do a little python and i find the SimpleGladeApp rather usefull. there is no magic involved ;)

---

### Post by felipe on 2005-05-13
i didn't mean it's "bad", really.

i'd just thought it would be better not to add that class to my scripts, and i'm not even sure what would be the best way to do it :)

thanks for you reply anyway

---

### Post by iNs4ne on 2005-05-13
OK, i have just started looking at python / GTK / Glade ...

i looked at this extremely simple example:
[http://www.arson-network.com/index.php?class=tutorial&subargs=430](http://www.arson-network.com/index.php?class=tutorial&subargs=430)

dunno if it helps tbh, but it got me started...

Cheers,
Joao Inacio

---

### Post by poster_nutbag on 2005-05-15
I know you just want to jump in and learn Glade+Gtk, but I highly suggest you at least make some programs in Gtk *without* Glade, otherwise you end up learning Glade, GTK and some kinda wrapper library all at once.

Trust me, I tried using Glade with pyGtk at first, but didn't really progress until I went through the pygtk tutorials.

---

### Post by nobodysbusiness on 2005-05-16
Here's a tutorial that helped me out:

[http://www.serpia.com/wxGlade_tutorial/wxGlade_tutorial.htm](http://www.serpia.com/wxGlade_tutorial/wxGlade_tutorial.htm) 

The SPE python editor is pretty cool, and has wxGlade built in. Check it out here:

[http://spe.pycs.net/](http://spe.pycs.net/)

---

### Post by Moobert on 2006-01-13
for an updated version of (using gtk2):
[http://sjbrown.users.geeky.net/metagame-sector/tutorial.html](http://sjbrown.users.geeky.net/metagame-sector/tutorial.html)

check out:
[http://jmoiron.net/docs/python/glade1/](http://jmoiron.net/docs/python/glade1/)

A few good links:

[http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/apc.html](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/apc.html)

4 good examples of libglade, showing the code in c, c++, perl, and most importantly python :)

[http://handhelds.org/~nelson/pyglade/pyglade-tutorial](http://handhelds.org/~nelson/pyglade/pyglade-tutorial)

a good starting point. It is for gtk1, but can use gtk2 if you swap the libglade import for:

import gtk.glade

then the libglade.GladeXML call, for:

gtk.glade.XML

finaly:

[http://www.ukuug.org/events/linux2001/papers/html/CEgli/Gnome-Talk.html](http://www.ukuug.org/events/linux2001/papers/html/CEgli/Gnome-Talk.html)

a more complex gtk1/gnome eg

---

### Post by stani on 2006-01-20
[QUOTE=nobodysbusiness]Here's a tutorial that helped me out:

[http://www.serpia.com/wxGlade_tutorial/wxGlade_tutorial.htm](http://www.serpia.com/wxGlade_tutorial/wxGlade_tutorial.htm) 

The SPE python editor is pretty cool, and has wxGlade built in. Check it out here:

[http://spe.pycs.net/](http://spe.pycs.net/)[/QUOTE]

The pycs website is deprecated. Don't get SPE with the package manager, download latest version at [http://pythonide.stani.be](http://pythonide.stani.be) From release 0.8.1.e SPE will be optimized for Ubuntu, see [http://pythonide.stani.be/blog](http://pythonide.stani.be/blog). Help is welcome.

---

