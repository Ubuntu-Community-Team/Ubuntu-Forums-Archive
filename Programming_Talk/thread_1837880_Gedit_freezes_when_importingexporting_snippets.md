---
title: "Gedit freezes when importing/exporting snippets"
date: 2011-09-02
forum: Programming Talk
---

### Post by Andrew_P on 2011-09-02
I'm running gedit 2.30.3 on Ubuntu 10.04.1 LTS and I've encountered a bug in the Snippets plugin configuration (Edit -> Preferences -> Plugins - Snippets -> Configure Plugin).  I can define new snippets and delete them without problems, but when I click on either the file folder button *(Import snippets)* or hard drive button *(Export selected snippets)*, a Gnome filechooser dialog box pops up and gedit hangs *hard*!  One can still resize the dialog box with the mouse, but none of its buttons or sliders work and one can't edit the file name field.  I need to use System Monitor to kill it, and if I was editing a file, the edits are lost.:(

Customized snippets files are stored in $HOME/.gnome2/gedit/snippets as XML files.  As a work-around, one could archive them here manually or place appropriate XML files extracted from an archive, avoiding use of the Gnome file dialog in the Snippets Manager.

Has anyone else seen this problem recently?  I found a bug report ([#617622]("https://bugzilla.gnome.org/show_bug.cgi?id=617622")) at [Gnome Bugzilla]("https://bugzilla.gnome.org/show_bug.cgi?id=617622"), but as far as I know, nothing has been done on it in well over a year.

---

### Post by gusnan on 2011-09-02
I can reproduce this on Ubuntu 10.04, but it seems fixed in both Ubuntu Natty, and Debian Unstable.

---

