---
title: "linux/module.h problem"
date: 2007-06-11
forum: Programming Talk
---

### Post by gizmoarena on 2007-06-11
im just trying to compile this code 

> #define MODULE
#include <linux/module.h>

int init_module (void) /* Loads a module in the kernel */
{
printk("Hello kernel n");
return 0;
}

void cleanup_module(void) /* Removes module from kernel */
{
printk("GoodBye Kerneln");
}


the compiler is showing this error

> gizmo@ubuntu:~/driver$ sudo gcc -c hello.c
hello.c:2:26:[COLOR="Red"] error: linux/module.h: No such file or directory[/COLOR]


i'm using ubuntu 7.04. i have installed kernel source, build essentials and linux-header-386 from repository. still i'm getting this error.

can anyone help me please?

---

### Post by daou on 2007-06-11
Compiling modules for kernel 2.6: [http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

Replace the KDIR with the path where your linux sources are.

---

### Post by daou on 2007-06-11
> compile the kernel first (run "make" at least to the point until all "HOSTCC  scripts/" stuff is done - this will configure your kernel and allows external module compilation)

make sure to do that part if you haven't

---

### Post by gizmoarena on 2007-06-11
Thanks for your quick reply :)

Is there anyway I can compile modules for kernel 'without' compiling the kernel itself?
That would be very helpful.

---

### Post by daou on 2007-06-11
This doesn't actually compile everything in the kernel (like modules, etc) which takes forever. The make command should just configure the kernel with a couple of important parameters and be done in a couple of seconds.

---

### Post by MichiGreat on 2011-10-10
> **gizmoarena said:**
> Thanks for your quick reply :)

Is there anyway I can compile modules for kernel 'without' compiling the kernel itself?
That would be very helpful.

Well, your question is four years back, but in case you still need that:

[http://michigreat.a.wiki-site.com/index.php/Linux_Module](http://michigreat.a.wiki-site.com/index.php/Linux_Module)

May be that helps you.

Best regards

Michael

---

### Post by sisco311 on 2011-10-13
Necromancing.

Thread closed.

---

