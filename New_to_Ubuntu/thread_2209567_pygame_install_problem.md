---
title: "pygame install problem"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by Nabeel Abbas on 2014-03-06
I am trying to install pygame for python3 . after installation this comes up when i try to import it in python3

```

Traceback (most recent call last):  File "<pyshell#0>", line 1, in <module>
    import pygame
  File "/usr/local/lib/python3.3/dist-packages/pygame/__init__.py", line 95, in <module>
    from pygame.base import *
ImportError: /usr/local/lib/python3.3/dist-packages/pygame/base.cpython-33m.so: undefined symbol: PyCObject_Check

```

---

### Post by Nabeel Abbas on 2014-03-06
Well I finally sorted it out. here's what I followed [http://ubuntuforums.org/showthread.php?t=1960262](http://ubuntuforums.org/showthread.php?t=1960262)

---

