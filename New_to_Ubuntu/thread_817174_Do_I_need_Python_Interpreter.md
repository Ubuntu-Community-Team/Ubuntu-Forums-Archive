---
title: "Do I need Python Interpreter?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by vikramaditya on 2008-06-03
I'm using Hardy, but have no desire learn programming.  Is the Python Interpreter thingy necessary?  Can it be uninstalled without breaking the OS or internet functionality?

In order to dodge the sneers of elitest disdain, I'll take my answer off the air. :) Thanks!

---

### Post by Monicker on 2008-06-03
A lot of the OS functionality depends on it, iirc.  I would not advise removing it.

If you want to get an idea of what depends on it, do the following from a terminal prompt.

```
sudo apt-get -s remove python
```


The -s tells it to just simulate a removal, and it will just show what other packages would be removed.

---

### Post by Eclipse. on 2008-06-03
Yeah, alot of programs are coded in python so you basically be removing half of your system.;)

Plus python itself doesnt really take up much space.

---

