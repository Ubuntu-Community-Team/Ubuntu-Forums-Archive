---
title: "python-mpi/mpichpython/mpi4py"
date: 2009-03-27
forum: Programming Talk
---

### Post by pzs on 2009-03-27
I'm trying to do some parallel programming in Python. I've had mpi4py recommended to me, but this isn't in the Ubuntu repositories. I have found python-mpi as well as some other related packages like mpichpython and lampython. Are any of these mpi4py? Which one should I use?

---

### Post by maddog39 on 2009-03-27
You can really use any library you like, they arent hard to install at all. Download mpi4py as a tarball and unpack it to your desktop or where ever you like. Then open a terminal, change to the directory you unpacked it to and somewhere in the tarball, probably in the root directory should be a file called setup.py. Just run the command
```

sudo python setup.py install

```
It compiles the entire library as bytecode and installs it into your python modules directory. You can now open python and start using it.

---

