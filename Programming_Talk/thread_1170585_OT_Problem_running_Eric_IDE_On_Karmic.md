---
title: "OT: Problem running Eric IDE On Karmic"
date: 2009-05-26
forum: Programming Talk
---

### Post by fifth on 2009-05-26
Hoping someone can shed some light on this. At the moment, running Eric on Karmic gives the following output;

```

Traceback (most recent call last):
  File "/usr/share/eric/modules/eric4.py", line 43, in <module>
    from KdeQt.KQApplication import KQApplication
  File "/usr/share/eric/modules/KdeQt/__init__.py", line 20, in <module>
    import Preferences
  File "/usr/share/eric/modules/Preferences/__init__.py", line 26, in <module>
    from PyQt4 import Qsci
ImportError: cannot import name Qsci

```

I know its just a current packaging problem and involves the (Q)Scintilla packages and will probably be resolved soon. But i've trying to work out the issue and don't know where to start looking for the problem?

---

### Post by theLegend on 2009-08-22
I'm having the same problem as you but with trying to get Autokey to work. I did have it working in a previous version (0.54 I think) but now its not and I get the same error as above.
I'm sure its to do with Qscintilla2 and have tried to reinstall this and autokey but no luck so far.
I do manage to run other python programs with no trouble so this is a little annoying!

Any help would be greatly appreciated.

The Legend

---

