---
title: "Get Pygame to work"
date: 2010-10-02
forum: Programming Talk
---

### Post by Dlom on 2010-10-02
Back when I still used windows (ugh), I tried a little bit of python programming.  Fast forward to now, and I'm playing Frets on Fire, and I remember that it's written in Pygame.  I decide to try it out, so I install it. ```
sudo aptitude install python-pygame
```
Afterwards, I open up terminal, start python (with the python command), and that works.  Then I try to import Pygame (per the tutorial):
```
>>>import pygame
```
I get this error:
```
>>> import pygame
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named pygame

```

I check in the Ubuntu Software Center, and Pygame is listed as installed (Green check mark).  I have Ubuntu 10.04.  Help please!

---

### Post by luke83 on 2010-11-19
Hello, im working thru a training book on python and i tried to install pygame thru the synaptic manager and i too have the same error. Help Please

---

### Post by dhtseany on 2010-11-19
[http://packages.ubuntu.com/maverick/python/python-pygame](http://packages.ubuntu.com/maverick/python/python-pygame)

At least it's a starting point instead of getting ignored. Next time you're having issues finding packages, packages.ubuntu.com is real in depth at listing everything currently in the normal repos.

Hope this kinda helped.

Peace
Sean

---

