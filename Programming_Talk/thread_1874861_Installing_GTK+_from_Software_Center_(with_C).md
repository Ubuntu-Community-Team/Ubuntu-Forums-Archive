---
title: "Installing GTK+ from Software Center (with C)"
date: 2011-11-03
forum: Programming Talk
---

### Post by gnometorule on 2011-11-03
I've searched the forum and found many references to similar sounding Titles, but what I saw didn't seem to answer the basics I am looking for. I went to the GTK+ project page and saw that GTK+ needs the libraries (provided there as tar files - these the most recent versions as of today):

[LIST]
[*][GTK+ 3.0]("http://ftp.gnome.org/pub/gnome/sources/gtk+/3.0/")
[*][GLib 2.28]("http://ftp.gnome.org/pub/gnome/sources/glib/2.28/")
[*][Pango 1.28]("http://ftp.gnome.org/pub/gnome/sources/pango/1.28/")
[*][Gdk-Pixbuf 2.24]("http://ftp.gnome.org/pub/gnome/sources/gdk-pixbuf/2.24/")
[*][ATK 2.0]("http://ftp.gnome.org/pub/gnome/sources/atk/2.0/")
[/LIST]
However, given the importance of GTK, I assume that it is pre-installed with my OS - developer version I mean, not just runtime libs for apps. I was able to find what seems to be python binding libs, but intend to work with C as I prefer it, and as it's native to GTK+. 

**Questions:**

(1) do I (probably) have the above libraries already installed (under a different/same name) ? I'm usually fine with whatever older version Ubuntu is kind enough to offer via this route - rather than deal with dependencies myself

(2) if not, or if I do but other libs need to be installed to develop: what else do I need to install, again, much preferably from the Software Center?

(3) less important: I read that once I get more serious GLADE is recommended for the obvious reason (I did find GLADE in the Software Center). Anything else I should consider installing?

Many thanks. 

My system:

Toshiba netbook
Ubuntu 10.04
Kernel version 2.32ish
Gnome based system

---

### Post by Bachstelze on 2011-11-03
For GTK you need libgtk2.0-dev, it should install all you need. Not sure about Glade, though...

---

### Post by gnometorule on 2011-11-03
Awesome! Glade pops separately on the Software Center, so is easy too. Many thanks as usual, BS.

---

### Post by gsmanners on 2011-11-03
If you haven't already, you should consider also:

libgtk2.0-doc
devhelp

That way, you don't have to hammer on Gnome's doc site all the time for a reference.

---

### Post by gnometorule on 2011-11-04
Downloaded those too, thank you very much.

---

