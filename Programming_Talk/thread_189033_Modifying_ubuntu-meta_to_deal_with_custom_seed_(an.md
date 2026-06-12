---
title: "Modifying ubuntu-meta to deal with custom seed? (and more distro stuff)"
date: 2006-06-04
forum: Programming Talk
---

### Post by megabyte405 on 2006-06-04
I'm working on a small derived distribution of Ubuntu, with a modified seed file.  I want to produce my own custom "megabyte-desktop" packages and so on, based on the ubuntu-meta package that generates ubuntu-desktop, etc.  I have set up my own automatic apt repository, and have modified my seeds.  However,  I run into a problem in the update script from the -meta package: it supports only one archive.  Most of my packages are from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/), just as in standard Ubuntu, but some of them come from my own repository.  I can't see how to expand/extend the script to handle dual repositories.

Also, if anyone knows which packages do the following, please let me know!  (so I can examine/modify it)
[LIST]
[*]Set the default GDM theme
[*]Set the default GNOME theme (Metacity, GTK, icon)
[*]Install/set up the sources.list file
[/LIST]

Thanks so much for any help!

---

