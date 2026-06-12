---
title: "Intrepid EeePC-lean kernel"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by yeehi on 2008-11-10
What is the benefit of using this (still experimental) kernel on an eeePC?

Will it give longer battery life? When is this kernel due to be stable?

---

### Post by th89 on 2008-11-10
> The eeepc-lean kernel is an experimental package that strips out all the extra crap from eeepc and the generic kernel (like macintosh support, nvidia modules, idsn and x.25 connectivity, etc) and the remaining eeepc-specific modules are compiled directly in the kernel
([http://forum.eeeuser.com/viewtopic.php?id=46649](http://forum.eeeuser.com/viewtopic.php?id=46649))

Basically, it looks like it is quite a bit smaller, and dosent load all the modules that you dont need. I would imagine you would have better battery life, as you dont need to run all the extra stuff, as well as a decent amount of extra HDD space.

EDIT: It also looks like you have a bootup speed increase of 20-30%

---

