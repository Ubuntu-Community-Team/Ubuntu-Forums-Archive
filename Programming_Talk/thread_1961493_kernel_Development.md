---
title: "kernel Development?"
date: 2012-04-19
forum: Programming Talk
---

### Post by conradin on 2012-04-19
Hi all Im wandering into kernel developments, 
and trying to get a handle on it with the tutorials at this site:
[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40)
unfortuneately, Im having some problem, or perhaps misunderstanding about what is supposed to happen when i make the module hello-4 from hello-4.c

The program is about giving descriptions in kernel modules. There seems to be no changes in the messages file of /var/log where I typicaly obsurve program opeartions. I tried to use the program objdump, but I see nothing that makes sense to me about how to dump specific objects like author, or license. 

alternatively, running the strings command on the module hello4.ko seems helpful:
```
$ strings hello4.ko
<6>Goodbye, world 4
<6>Hello, world 4
description=A sample driver
author=Peter Jay Salzman <p@dirac.org>
license=GPL
srcversion=9ACA98AD11775A2DCB1EE86
depends=
vermagic=2.6.32.57+drm33.23 SMP mod_unload modversions 586TSC 
module_layout
printk
mcount
hello4

```

But it seems like thats not the right way to go at this, functions, I thought I would be able to see those... 
How would anyone here go about viewing kernel module file descriptors?
Is the program objdump the best thing I should use?
is there something else handy for viewing object data?

---

### Post by pbrane on 2012-04-19
The only thing that is going to print in the logs is the **printk** output.

---

### Post by Gyokuro on 2012-04-19
Hi,

a small description can you get via:

modinfo hello4

for more fun/information you should use objdump --help

objdump --section-headers hello4.ko

and you can find useful information at: [www.kernelnewbies.org](www.kernelnewbies.org)

---

