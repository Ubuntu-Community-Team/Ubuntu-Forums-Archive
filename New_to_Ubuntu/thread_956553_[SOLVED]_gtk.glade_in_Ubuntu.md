---
title: "[SOLVED] gtk.glade in Ubuntu"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by FruitCase on 2008-10-23
Hi list,

it's probably me, but each time i read in Python related software the word 'easy' i get nervous. I am trying to install something - can't figure out how or what it should be - to repair the message 
'ImportError: No module named glade' popping up when i try to start the program 'meld'.

I have two python versions (2.4 and 2.5). There are a number of eggs around, site-packages and all kinds of other magic, but after the Ubuntu meld install i get this 'no glade' message. I have tried a lot of things, like changing the standard python (from 2.4 to 2.5), install pygtk through easy_install (which wasn't easy, despite the reassuring program title), find something akin to glade in eggs on pypi but to no avail.

I have used apt-get install python-gtk2 python-glade2
Even that doesn't help.

Which magic incantation should i use to be able to import gtk.glade in python 2.5 or python 2.4 prompts?

Thank you for helping me out!

---

### Post by FruitCase on 2008-12-01
It's not easy to be too stupid for ubuntu, python gtk.glade. But i manage it nicely.
Just for fun, trying to get glade working somehow . .. :)

> python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/lib/python2.5/site-packages/setuptools-0.6c9-py2.5.egg', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/local/lib/python2.5/site-packages/gtk-2.0', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/gst-0.10', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5', '/var/lib/python-support/python2.5/gtk-2.0', '/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode']

> meld .
Traceback (most recent call last):
  File "/usr/bin/meld", line 93, in <module>
    import meldapp
  File "/usr/lib/meld/meldapp.py", line 23, in <module>
    import gtk.glade
ImportError: No module named glade

Okay, so i need something called glade in python. Where can i get glade?
Glade is imported like so, import gtk.glade, so maybe it's part of the gtk package. Lets try and get gtk in python::

>>> import gtk
>>>

But gtk.glade, no dice.
K, so, gtk and python, perhaps pygtk should be reinstalled as it is clearly not complete for there is no gtk.glade?

Lets try:
Get pygtk, [http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/](http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/)

tar -zvxf pygtk-2.12.1.tar.gz, ./configure
The following modules will be built:

atk
pango
pangocairo
gtk with 2.12 API
gtk.unixprint

The following modules will NOT be built:

gtk.glade

Aaggghhhh, never mind. Why will it not build gtk.glade?
...
checking for LIBGLADE... no
...
Okay, so what is libglade? See [http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/), nice description but i just want meld to work. So, what do i do? Download, pffew ... [http://ftp.gnome.org/pub/GNOME/sources/libglade/2.0/](http://ftp.gnome.org/pub/GNOME/sources/libglade/2.0/)

> ./congigure
looks nice, so onward:
> make
libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'

Aaaaggghhhhh, never mind. Why, what should i do?
Perhaps this will help: sudo apt-get install libglade2-dev

No dice. Stumped again. Sob, i just want meld to work ...
But, there is something called libglade2-dev, so perhaps simply doing sudo apt-get install libglade2 might do the trick. Where can i find it?

Somewhere there is something called libglade-gnome0 and libglade-gnome0-dev, so perhaps that's it? Nope. Might it be libglade2-0?

libglade2-0 is already the newest version. Sigh, stumped again. Aaaaggghhh, what to do now? Perhaps libglade-2.0.0 does work?
Nope, same problem. It must be me, nobody has this hassle with just wanting to run meld, otherwise it wouldn't exist.
Perhaps a later version, so i try libglade-2.6.3.
./configure (fingers crossed), make, install. It worked.

Back to pygtk.
./configure
The following modules will be built:

atk
pango
pangocairo
gtk with 2.12 API
gtk.glade
gtk.unixprint

Victory at last. A huge amount of warnings later. Looks scary.
make, make install

Right. So far so good.
> python

>>> import gtk
>>> import gtk.glade 


Pffew, finaly.

meld .

Ah, thank you ubuntu for the update of python :)

---

### Post by vyomhere on 2009-02-04
Hi 
Thanks a lot for this post,
I was trying to install linphone from source on ubuntu intrepid, which eventually lead me to install libglade,
I was stuck with the same error,
> glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'

As per your post I tried libglade2.6.3 and it worked.

Thanks a lot.

---

