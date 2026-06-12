---
title: "making a gnome-screensaver package"
date: 2011-02-08
forum: Packaging and Compiling Programs
---

### Post by LemursDontExist on 2011-02-08
Hi,

I've written a gnome-screensaver theme which works perfectly on my computer, and I would like to package it to share with the world at large!  I'm not worried about the technical details of packaging(at least not yet), but mostly about where it would be appropriate to install the files.

I've tried to find documentation, but the documentation for gnome-screensaver is absolutely minimal, and I've had no luck on the gnome irc channels either, so I'm appealing to the Ubuntu community!

Basically, I have 4 sorts of files - the primary executable script (the whole screensaver is written in python), numerous auxiliary script files which the main script needs to import, some data files (a couple svg images and some text data), and a .desktop file.

I'm reasonably confident that the .desktop file needs to go in /usr/share/applications/screensavers (more precisely, the output of pkg-config --variable=themesdir gnome-screensaver), but that's all I'm really sure of.

Probably the main executable belongs in /usr/lib/gnome-screensaver/gnome-screensaver (pkg-config --variable=privlibexecdir gnome-screensaver), but maybe that folder is only for those screensavers bundled with gnome-screensaver?  I can't find any indication.  Alternatively I could put it in /usr/bin.  The associated script files need to be somewhere the main script can find them of course, but probably not cluttering the theme engine directory?  I could put them in their own folder in /usr/lib, but they could also live somewhere in /usr/lib/gnome-screensaver.

I've currently got the data files in a folder under /usr/share, and, again, is this right for a screensaver?

I've not got any technical problem - I just don't know what is conventional for distributing a gnome-screensaver theme, so I hope someone here can help me, or at least tell me where I should be asking for help!

---

