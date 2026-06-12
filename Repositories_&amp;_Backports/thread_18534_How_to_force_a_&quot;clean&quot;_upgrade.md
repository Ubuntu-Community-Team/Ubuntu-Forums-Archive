---
title: "How to force a &quot;clean&quot; upgrade?"
date: 2005-03-07
forum: Repositories &amp; Backports
---

### Post by AndyGates on 2005-03-07
I've been bad.  I've been silly.  I've messed up my Ubuntu build with stuff from mixed repositories, including a Debian one and some random coder people.  As a result, my last *apt-get upgrade* resulted in a bit of a mess.

I've lost the workspaces, gnome-panel is hilariously unstable, and file manipulation is, er, random and exciting.   :-D 

I'd like to force a clean "repair" build - well, repair is what Windows people call it - and splat the latest stable release over the tangle I've got.  but I can't just flatten and rebuild, 'cos I have a lot of data in my home folders that would be expensive to replace.  I've also got a few nonstandard apps (gaim-vv, mame, climateprediction.net) and I would prefer to preserve them too.  But hey, if breaking my toys means fixing my machine, so be it.

So, er... where do I start?  I've already done *apt-get upgrade --fix-missing* with only the Hoary stable repositories.  What next?

---

### Post by AndyGates on 2005-03-24
A little more patience and investigation shows every "problem" app giving the same errors:

```
(gtkpod:8657): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gtkpod:8657): Pango-CRITICAL **: _pango_engine_shape_covers: assertion `PANGO_IS_FONT (font)' failed

```

(That's for gtkpod, but the errors are the same for Nautilus, Gnome-panel, Totem, Sound Juicer and so on...)

I have libpango 1.8.1 (main, common and dev) and libgtk 2.0 (2.6.4-0ubuntu1).  Any ideas what I might need to do to fix this?

---

### Post by az on 2005-03-24
Try
sudo apt-get remove libgnome2.0
sudo apt-get install ubuntu-desktop.


If removing libgnome2.0 is too scary, try just installing the ubuntu-desktop to see if that helps...

---

### Post by AndyGates on 2005-03-25
Thanks - I tried that (I am the Man Without Fear) but it had no effect.  The same errors come up with the same apps.  If that was the whole desktop... I'm baffled!

---

### Post by maqi on 2005-03-25
Hey Andy,

ubuntu-desktop is a metapackage. It just tells apt what all of the packages in the official Ubuntu desktop are. The second you remove an official gnome app that package is removed too. And once you've got ubuntu up and running you don't really need it any more. It just makes it easier to do the original install.

And if you've already got all or most of the packages specified reinstalling it won't do much at all. Unless ... you set your apt sources and preferences correctly. Have a look [here](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin). You can get quite complex with it - for instance you can force packages to stay at a certain version, or only get one package from a particular repository, eg, maybe debian has a particular app you need, or there's a bleeding edge version of an app you just *have* to have.

Hope this helps :)

---

