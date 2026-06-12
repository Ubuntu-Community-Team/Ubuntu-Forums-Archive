---
title: "[SOLVED] building from the ground up"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-04
how hard is it to build from the group up with a distro?

I understand that one can make their own but I don't believe I have the know how or experience to do that.

Is there a way to strip a distro down and put in only the programs one wants?  

What files are necessary?  Is there any universal file that is necessary to different distros (ie. ubuntu/pcfluxboxos/DSL) or do they all have different needs and requirements?

---

### Post by tdrusk on 2008-06-04
> **AnLGP said:**
> how hard is it to build from the group up with a distro?

I understand that one can make their own but I don't believe I have the know how or experience to do that.

Can one find a distro and install what they want or do anything similar?

I hope that's coming across right.
Just grab the minimal Ubuntu CD and have at it. It starts you off with a command line and you sudo apt-get everything you want/need.

---

### Post by nick_h on 2008-06-04
Have a look at [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

It might not be what you want but it will increase your understanding.

---

### Post by InfinityCircuit on 2008-06-04
If you want to strip ubuntu down to the bare essentials,

```
sudo apt-get remove --purge x11-common perl python && sudo apt-get autoremove --purge
```

This will leave you with a bare command line system.

---

### Post by AnLGP on 2008-06-04
I'll have to look into everything.  Thanks guys you hit the nail on the head :)

---

