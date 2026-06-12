---
title: "How to change fonts using a bash script?"
date: 2005-10-08
forum: Programming Talk
---

### Post by mangar on 2005-10-08
I'm writing a script for Ubuntu 5.10, that is supposed to automaticaly
set up common preferences for users of my locale.
(such as w32codecs, plugins for firefox, etc)
The Script is based on easyUbuntu.

link:
[http://www.ubuntuforums.org/showthread.php?t=70794](http://www.ubuntuforums.org/showthread.php?t=70794)

My question is:
How do I change the Gnome's fonts using the command line, for all the
users of the current machine? (and maybe firefox's ?)
(The default ones, well, suck)

Thanks in advance!

P.S. it's a bash script

---

### Post by ow50 on 2005-10-08
The fonts seem to be defined in gconf keys in /desktop/gnome/interface. Use command line tool "gconftool-2" to change the values of the keys. Check the exact keys with the gconf editor and read the gconftool-2 man pages.

---

### Post by mangar on 2005-10-08
Thanks for your reply!
I will see to it.

---

