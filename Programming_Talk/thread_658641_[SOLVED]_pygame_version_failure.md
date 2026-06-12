---
title: "[SOLVED] pygame version failure"
date: 2008-01-04
forum: Programming Talk
---

### Post by oooooops on 2008-01-04
Hi,

I'm new to both Python and Pygame but thought Pygame might provide me a "fun" way to learn a little about game programming and Python.

I've already hit an issue.  I installed pygame by doing 

```
sudo aptitude install python-pygame
```

it says it installs fine.  

However this very simple test gives me an error that I don't quite understand

```

Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32)
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> print pygame.version
<module 'pygame.version' from '/usr/lib/python2.5/site-packages/pygame/version.pyc'>

```

whereas the output should be the actual version of pygame (in this case I think 'it's 1.7.1)

Anyone have any idea what the problem might be?

I have already removed/installed quite a few times. I even tried a restart to see if that would help (it didn't no big surprise there).

Thanks

---

### Post by Peyton on 2008-01-04
(Accidental double post.)

---

### Post by Peyton on 2008-01-04
Try this:
[PHP]print pygame.version.ver[/PHP]
As your result indicates, pygame.verison is actually a module.

For more information:
[http://www.pygame.org/docs/ref/pygame.html#pygame.version](http://www.pygame.org/docs/ref/pygame.html#pygame.version)

---

### Post by oooooops on 2008-01-04
:mad:  Thank you that's what the issue was.  You don't want to know how much time I spent on that.  I hang my head in shame.

---

