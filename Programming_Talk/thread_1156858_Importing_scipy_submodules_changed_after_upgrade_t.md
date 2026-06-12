---
title: "Importing scipy submodules changed after upgrade to 9.04 (jaunty)?"
date: 2009-05-12
forum: Programming Talk
---

### Post by lckarssen on 2009-05-12
I've got two installs here, one ubuntu 8.10 and another ubuntu 8.10, recently upgraded to 9.04. 

When running ipython I noticed that *ipython -p scipy* doesn't seem the load the scipy.special module anymore on the 9.04 machine. I need to import it by hand. The same holds for example for scipy.fftpack. 

Also when running the program from the command line the same problem exists. For example:
```
#!/usr/bin/env python

from scipy import *

def main():
    print special.sph_harm(1,1, 0,0)

if __name__ == '__main__':
    main()

```
works on 8.10, but on 9.04 I need to write:
```
#!/usr/bin/env python

from scipy.special import *

def main():
    print sph_harm(1,1, 0,0)

if __name__ == '__main__':
    main()

```

I tried to find out how the modules are loaded on the two systems and I found in the python manual that the __init__.py file in /usr/lib/python2.5/site-packages/scipy/ (for 8.10) and /usr/lib/python2.6/dist-packages/scipy (for 9.04) should contain an *__all__ = ["list with packages to be loaded here"]* line. In fact, on both releases the tag exists: *__all__ = ['pkgload','test']*. And since the function *scipy.pkgload()* should load all packages (and a quick test in ipython shows that it does on 9.04) I don't understand why it doesn't seem to load all submodules when importing scipy on 9.04.

Anybody experiencing this as well?

---

