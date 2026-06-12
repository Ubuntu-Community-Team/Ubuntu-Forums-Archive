---
title: "Add new moudle at system starup"
date: 2008-12-23
forum: Programming Talk
---

### Post by davir on 2008-12-23
hello
I develop kernel module.
i would like to load the module at startup.
i understand i need to add the module to /etc/modules
but where do i put the file ( Which Directory).
thank

---

### Post by squaregoldfish on 2008-12-23
There's a directory /lib/modules/<kernel-name>/extra, where you can put new kernel modules.

Naturally, when you update your kernel, your module may (will?) have to be recompiled against the new kernel sources, and the new version placed in the appropriate directory.

Steve.

---

### Post by davir on 2008-12-23
thank for the fast replay.
i didn't have the directory extra.
so i created one.
edit the file /etc/modules (Add a line with the name of the module)
it didn't work
Any other suggestion (what am i doing wrong)

---

### Post by dwhitney67 on 2008-12-23
You could insert you module (name) into /etc/modules.

Btw, you did not specify where you had installed your kernel module.  In other words, where did you place the <kmodule>.ko file?

P.S.  Not all *nix systems are setup the same.  I assume you are using Ubuntu.  If not, please indicate which system you are using.

---

### Post by davir on 2008-12-23
I use ubuntu.
if you can see my first question, i asked where to put the <module>.ko
file , Where /etc/modules look for external modules

---

### Post by davir on 2008-12-23
thanks for all the replies
problem solved

---

### Post by squaregoldfish on 2008-12-23
How did you solve your problem? It'll help anyone else who stumbles across this thread in the future.

Steve.

---

### Post by frozila on 2008-12-23
To be continue

---

### Post by davir on 2008-12-24
The Way i solved the problem
1. Compile the module against the relevant kernel version.
2. create new directory in /lib/module/KERENL-VERSION/updates
3. The run depmod
4. update /etc/modules - Add a line with the name of the modules.
5. If your driver as input parameters you can use the /etc/modprobe.d/options For Example options module_name param_1=2

---

