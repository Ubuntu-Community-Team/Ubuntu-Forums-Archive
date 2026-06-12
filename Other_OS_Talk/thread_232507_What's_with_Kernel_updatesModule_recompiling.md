---
title: "What's with Kernel updates/Module recompiling?"
date: 2006-08-08
forum: Other OS Talk
---

### Post by Iandefor on 2006-08-08
This is something I've been wondering about for a while. Why is it that, when the kernel updates, I have to get recompiled modules for the specific updated kernel release? For instance, if I upgrade from 2.6.15 to 2.6.17, why do all the kernel modules need to be recompiled against the new kernel?

I occasionally feel like a newb, asking questions like that :-/.

---

### Post by ember on 2006-08-09
I believe it is because interfaces may change and there modules are checked against the kernel version to avoid potential crashes.

---

### Post by tseliot on 2006-08-09
> Loadable kernel modules are often called just kernel modules or just modules, but those are rather misleading terms because there are lots of kinds of modules in the world and various pieces built into the base kernel can easily be called modules. We use the term loadable kernel module or LKM for the particular kinds of modules this HOWTO is about.

Some people think of LKMs as outside of the kernel. They speak of LKMs communicating with the kernel. This is a mistake; LKMs (when loaded) are very much part of the kernel. The correct term for the part of the kernel that is bound into the image that you boot, i.e. all of the kernel except the LKMs, is "base kernel." LKMs communicate with the base kernel.

In some other operating systems, the equivalent of a Linux LKM is called a "kernel extension."

You can read the rest here:
[http://www.tldp.org/HOWTO/Module-HOWTO/x68.html](http://www.tldp.org/HOWTO/Module-HOWTO/x68.html)

If you consider them extension of the kernel (or, even  better, parts of the kernel) you'll see why you have to recompile the modules for each kernel (or maybe not ;)  ).

---

### Post by Iandefor on 2006-08-11
I see. Thanks!

---

