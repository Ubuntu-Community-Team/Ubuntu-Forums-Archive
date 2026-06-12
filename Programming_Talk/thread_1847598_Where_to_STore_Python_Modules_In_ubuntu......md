---
title: "Where to STore Python Modules In ubuntu....."
date: 2011-09-21
forum: Programming Talk
---

### Post by asad393 on 2011-09-21
**[SIZE=4]I  am a Linux ubuntu User...I was learning python from a person who was  using windows..everything is fine but i have a problem where should i[COLOR=SeaGreen]  store[/COLOR] [COLOR=Red][B]modules.**[/COLOR]..as windows users store Modules in python folder..i dont  know where[COLOR=Red] python[/COLOR] is in linux..Please help..[/SIZE][/B]

---

### Post by Smart Viking on 2011-09-21
The simplest is to just store the module in your project folder.

Apart from that, you can store it in any of the folders that you see when you launch this:

```
>>> import sys
>>> sys.path

```Don't use such big font size and strong colors :(

---

### Post by cgroza on 2011-09-21
Or if it a library, use the setup.py to install it in your python setup.

---

### Post by nvteighen on 2011-09-21
> **cgroza said:**
> Or if it a library, use the setup.py to install it in your python setup.

Yeah, if this is about installing modules you've written, the best thing is to use distutils (which is what cgroza is referring to, actually). Specially because it ensures cross-platform compatibility... e.g. IIRC, Debian and Ubuntu use a different directory scheme for Python modules.

Look at these docs: [http://docs.python.org/library/distutils.html](http://docs.python.org/library/distutils.html)

---

