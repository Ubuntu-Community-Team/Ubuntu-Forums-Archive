---
title: "cannot compile mamegui"
date: 2012-10-07
forum: Packaging and Compiling Programs
---

### Post by yvhaelst on 2012-10-07
Dear all,

I'm trying to get gmameui to run on ubuntu precise pangolin.
I managed to understand auto-apt, but i'm still stuck in compiling.

Now i get the error:
./configure: line 12209: syntax error near unexpected token `,,:'
./configure: line 12209: `GNOME_DOC_INIT(,,:)'

I do not have any clue how to fix this.
I wouldn't mind understanding a bit more about compiling and stuff
Could someone help me out here?

Also: is there a project going on to get mamegui on precise pangolin?

---

### Post by mhall119 on 2012-10-07
Moved this thread to a more appropriate forum where you might get better help.

---

### Post by SevenMachines on 2012-10-08
probably something like
```
$ sudo apt-get install gnome-doc-utils

```then regenerate the macros to get GNOME_DOC
```
$ autoreconf -fi
$ ./configure
```
might work

---

