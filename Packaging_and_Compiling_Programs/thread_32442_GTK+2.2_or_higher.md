---
title: "GTK+2.2 or higher"
date: 2005-05-07
forum: Packaging and Compiling Programs
---

### Post by Psquared on 2005-05-07
GTK+ is now up to version 2.6.7 but Hoary comes with 2.0. I need at least 2.2 to compile the new rox-filer. [http://rox.sourceforge.net/phpwiki/index.php/InstallFromSource](http://rox.sourceforge.net/phpwiki/index.php/InstallFromSource)

Has anyone done this in Ubuntu? I searched for GTK+ and did not find any mention of it. The source package is available, but I don't want to break anything.

[I.E., somebody else be the guinea pig. :D ]

---

### Post by Ironi on 2005-05-07
The GTK2 packages only contain 2.0 in the names; they're not actually at that version:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/)

As to why the names include gtk+2.0 (source) and libgtk2.0-0 ... who knows. Maybe you can bug someone about renaming them to something sane. :p

---

### Post by Psquared on 2005-05-07
I did some research and Fedora, Mandrake and a few other distros are using (or have available) versions 2.2 and higher. Maybe I will ask Jdong about backporting it from Breezy - if that is a higher version.

---

