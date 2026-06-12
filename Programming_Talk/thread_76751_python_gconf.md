---
title: "python gconf"
date: 2005-10-15
forum: Programming Talk
---

### Post by c2483 on 2005-10-15
I'm fairly new to python but i''ve been programming for awhile.
i found one example python script that would change the desktop wallpaper.
it uses the gconf module.  When I try to run it however, I get
 line 4: import: command not found

i tried installing some other packages, maybe not the right one

i have other modules working with import such as
import os

how do i get this working

---

### Post by pavpan on 2007-06-27
did you install python-gconf?

---

### Post by duff on 2007-06-27
that sounds like you aren't using the python interpreter.  Make sure the script starts with the line ```
#!/usr/bin/env python
```That has to be the very first line, no line breaks or comments are allowed before that line.

---

### Post by altonbr on 2008-01-15
> **c2483 said:**
> I'm fairly new to python but i''ve been programming for awhile.
i found one example python script that would change the desktop wallpaper.
it uses the gconf module.  When I try to run it however, I get
 line 4: import: command not found

i tried installing some other packages, maybe not the right one

i have other modules working with import such as
import os

how do i get this working

Hey c2483, what tutorial is this? I'm new to Python and would like to know how to edit gconf as well...

---

### Post by Cherry Cotton on 2008-07-03
> **altonbr said:**
> Hey c2483, what tutorial is this? I'm new to Python and would like to know how to edit gconf as well...

I think it's here: [http://therning.org/magnus/archives/57](http://therning.org/magnus/archives/57)

EDIT: Also, if you have python-gconf installed, you can look in /usr/share/doc/python-gconf/examples/ for some example scripts.

---

