---
title: "Different ways to load kernel modules. What is the difference?"
date: 2010-03-17
forum: Programming Talk
---

### Post by vksingh on 2010-03-17
Hi All,

I got two ways to load the kernel modules,

[COLOR=#000000]    insmod /lib/modules/2.5.1/kernel/fs/fat/fat.o
    insmod /lib/modules/2.5.1/kernel/fs/msdos/msdos.o
	[/COLOR]or just run "**modprobe -a msdos**".


What is the difference between the above two ways?


Thanks,


Vivek

---

### Post by falconindy on 2010-03-17
modprobe is both smarter and safer than insmod.

---

### Post by ssam on 2010-03-17
ismod loads a module from the full path.
modprode finds the module by its name, and also loads any dependency modules.

see
man insmod
man modprobe

(its a bit like the difference between dpkg and apt-get)

---

