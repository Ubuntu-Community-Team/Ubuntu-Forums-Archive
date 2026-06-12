---
title: "Python clicking"
date: 2011-05-27
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-05-27
I always thought it would be cool if a program could click on certain pixels of the screen for you. My friend told me that it was possible using the java Robot class. I was wondering if there's an equivalent for the in python?

---

### Post by ziekfiguur on 2011-05-28
For keyboard emulation you can use the virtkey module, which is also used by onboard.
For mouse emulation it looks like [PyMouse]("https://github.com/pepijndevos/PyMouse") is what you need, though I haven't tested that one myself.

---

