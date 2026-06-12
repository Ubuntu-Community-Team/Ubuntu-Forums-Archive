---
title: "Python3.2 missing tkinter??"
date: 2012-07-20
forum: Programming Talk
---

### Post by ki4jgt on 2012-07-20
I just did a dist upgrade, afterwards tkinter stopped working in Python3.2. Whenever I try to use it I get this "No module named _tkinter, please install the python-tk package" I tried installing it but apt says it's already installed.

---

### Post by lykwydchykyn on 2012-07-20
Is the package "python3-tk" installed?  I would guess python-tk installs the library for python 2.x.

---

### Post by ki4jgt on 2012-07-20
> **lykwydchykyn said:**
> Is the package "python3-tk" installed?  I would guess python-tk installs the library for python 2.x.

It works. How did that get uninstalled anyways? I thought python always came with tkinter.

---

### Post by Bachstelze on 2012-07-20
> **ki4jgt said:**
> I thought python always came with tkinter.

In the source distribution it does, but Debian/Ubuntu puts it in a separate package.

---

### Post by lykwydchykyn on 2012-07-20
> **ki4jgt said:**
> It works. How did that get uninstalled anyways? I thought python always came with tkinter.

Who can fathom the wild and mysterious ways of APT?

---

