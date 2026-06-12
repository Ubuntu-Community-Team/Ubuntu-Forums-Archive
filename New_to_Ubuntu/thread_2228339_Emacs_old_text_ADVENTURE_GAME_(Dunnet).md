---
title: "Emacs old text ADVENTURE GAME (Dunnet)"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-06-06
Howdy,
I can access the game directly from Emacs, however, calling up help says to run it in the batch mode:
emacs -batch -l dunnet
However when I try this I  get an error message:
~$ emacs -batch -l dunnet
Loading 00debian-vars...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Error while loading 50dictionaries-common: Symbol's value as variable is void: debian-aspell-only-dictionary-alist
Symbol's value as variable is void: dunnet\.el

BTW, it was working when I was running Debian rather than ubuntu earlier today.  I don't know if this is a debian or a ubuntu concern.  Netting around had shown that this had been a problem, but debian says it was fixed some time ago, and seeing as how it was working, I can't but help believe it.
I got and installed it via the software center
GNU Emacs 24.3.1 (i686-pc-linux-gnu, GTK+ Version 3.10.7)
 of 2014-03-07 on toyol, modified by Debian

Does anyone know what is going on, fix etc. 
Thank you

---

### Post by Ron_Schnell on 2014-06-08
This was a bug in 50dictionaries-common.el that was fixed in May, apparently.

#Ron (author of Dunnet)

---

