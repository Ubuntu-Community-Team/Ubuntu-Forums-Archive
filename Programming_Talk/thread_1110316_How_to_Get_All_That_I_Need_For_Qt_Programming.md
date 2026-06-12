---
title: "How to Get All That I Need For Qt Programming?"
date: 2009-03-29
forum: Programming Talk
---

### Post by rich1939 on 2009-03-29
I'd like to start looking at Qt for cross-platform programming. I saw that there were a lot of individual components in Synaptic's list. Is there a single **apt-get install** command that I could use to get all of the Qt libraries and development tools, including a GUI interface developer?

If so, please let me know how to get them.

Thanks

---

### Post by snova on 2009-03-29
These packages, I think:

**libqt4-dev** contains all the headers and development tools.
**qt4-designer** has the graphical window editor.

This is Intrepid, by the way.

---

### Post by rich1939 on 2009-03-29
Thanks very much!

---

### Post by DGortze380 on 2009-03-30
I always suggest apt, but if you can't find it in the repos, I've compiled from source, and it works just fine. Fair Warning: It takes a LONG time to compile... 2+ hours on my Core Duo with 2GB of RAM.

---

### Post by Nevon on 2009-03-30
Or you could get QT Creator, which is available here: [http://bit.ly/qxrO8](http://bit.ly/qxrO8)

---

### Post by Bachstelze on 2009-03-30
Also, there are Qt bindings for other languages than C++. If you begin, you might want to install [font="monospace"]python-qt4[/font] (which as its name implies, will let you program Qt applications in Python). Also, [font="monospace"]qt4-doc[/font] might be useful. ;)

---

### Post by rich1939 on 2009-03-30
> **HymnToLife said:**
> Also, there are Qt bindings for other languages than C++. If you begin, you might want to install [font="monospace"]python-qt4[/font] (which as its name implies, will let you program Qt applications in Python). Also, [font="monospace"]qt4-doc[/font] might be useful. ;)

Thanks for the input. I'm not familiar with Python yet. I've written a few books about object Pascal & C++...but haven't yet gotten to Python. Maybe someday...:)

---

### Post by samjh on 2009-03-30
> **rich1939 said:**
> I'd like to start looking at Qt for cross-platform programming. I saw that there were a lot of individual components in Synaptic's list. Is there a single **apt-get install** command that I could use to get all of the Qt libraries and development tools, including a GUI interface developer?

If so, please let me know how to get them.

Thanks

```
sudo apt-get install qt4-dev-tools qt4-designer
```That will install development libraries, qmake, QT Assistant, QT Linguist, and QT Designer.

---

### Post by rich1939 on 2009-03-31
> **samjh said:**
> ```
sudo apt-get install qt4-dev-tools qt4-designer
```That will install development libraries, qmake, QT Assistant, QT Linguist, and QT Designer.

Thanks very much. It appears that I've now got all of those tools.

---

