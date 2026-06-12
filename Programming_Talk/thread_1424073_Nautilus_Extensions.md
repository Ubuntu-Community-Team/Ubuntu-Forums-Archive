---
title: "Nautilus Extensions"
date: 2010-03-07
forum: Programming Talk
---

### Post by Penguin Guy on 2010-03-07
[QUOTE="__init__"]
Are you sure you killed nautilus completely (with "killall nautilus" in terminal, for example), not just closed it's window?
[/QUOTE]
- Thanks, that did it.

----------------------------------------

I want to write my own Nautilus extension, so I took a look at the [Gnome guide to Nautilus extensions]("http://live.gnome.org/Nautilus/Development/Extensions#Example_extensions").

I installed [FONT="Courier New"][python-nautilus]("apt:python-nautilus")[/FONT] and downloaded [one of the example nautilus extensions]("http://svn.gnome.org/viewvc/nautilus-python/trunk/examples/md5sum-property-page.py?view=markup"). But when I put it in [FONT="Courier New"]~/.nautilus/python-extensions/[/FONT] and restarted nautilus, nothing happened. What's going on?

---

### Post by __init__ on 2010-03-08
Just tried it and it works for me. Are you sure you killed nautilus completely (with "killall nautilus" in terminal, for example), not just closed it's window?

---

### Post by __init__ on 2010-03-08
By the way, thanks for useful link. :)

I've created handy extension I often missed. You select few (or a lot of) files, enter regexp and substitution patterns and instantly get all this files renamed so you don't even need to open a terminal.

Posting it here in case it will be useful for someone.

---

### Post by Penguin Guy on 2010-03-09
Thanks, that fixed it. Now I just have to figure out the GTK interface.

---

