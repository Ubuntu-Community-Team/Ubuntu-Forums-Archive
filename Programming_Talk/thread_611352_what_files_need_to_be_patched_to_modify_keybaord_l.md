---
title: "what files need to be patched to modify keybaord layout preferences"
date: 2007-11-12
forum: Programming Talk
---

### Post by DoubleClicker on 2007-11-12
Someone made a request for some  new features in the keybaord layout options preferences in this thread:
[http://ubuntuforums.org/showthread.php?t=610223](http://ubuntuforums.org/showthread.php?t=610223)

I agreed to work on it but i really don't have time to learn my way around the ubuntu/gnome source tree.

could someone give me an overview of what files I would need to patch, where they are located and what package they belong to in the standard ubuntu install?

---

### Post by geraldm on 2007-11-13
Generally, the files are under /etc/X11/  
file xorg.conf is general, there is a section on keyboards
see /etc/X11/xkb/rules/xorg for some Mac <-> x86 keyboard
changes.  
That may be enough if you are just looking at some
key exchanges.  There really should be a better reference for
how to make changes, but I do not see it yet.  There should be
a more detailed description for how to change the individual keys
from one language/layout to a foreign language layout.  I still need
to do more research on keys.

Geald

---

### Post by DoubleClicker on 2007-11-14
Thanks for the reply but i'm actually looking for the source files for the source files for the keybaord layout options preferences in gnome.  I'm trying to modify the program not just create a modified config file.  if I was less busy, or more motivated i would do the research to find them myself, but I'm not really a linux person, I just wanted to help out with a request because i like the posts from the requester, and give something to the community.  But I have to confess, i'm only motivated to do what's easy, so I'm asking someone who knows the source tree to give me a head start.

---

