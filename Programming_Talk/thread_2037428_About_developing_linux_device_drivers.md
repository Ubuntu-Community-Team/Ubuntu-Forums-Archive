---
title: "About developing linux device drivers"
date: 2012-08-04
forum: Programming Talk
---

### Post by ZelAlex on 2012-08-04
I am just beginning to write device drivers. I am following a book. It said this:
```

The example modules should work with almost any 2.6.x kernel, including those
provided by distribution vendors. However, we recommend that you obtain a &#8220;main-
line&#8221; kernel directly from the kernel.org mirror network, and install it on your sys-
tem. Vendor kernels can be heavily patched and divergent from the mainline; at
times, vendor patches can change the kernel API as seen by device drivers. If you are
writing a driver that must work on a particular distribution, you will certainly want
to build and test against the relevant kernels. But, for the purpose of learning about
driver writing, a standard kernel is best.

```What is a mainline kernel?

I have kernel number 3.2.0-23 on my ubuntu 12.04LTS. Which Mainline kernel should I install? Any suggestions?

---

### Post by xb12x on 2012-08-04
A mainline kernel has not been patched and modified for a specific Linux distro.

If you have enough disk space, installing (dual-booting) another, older Ubuntu release might be the best way to proceed, rather than trying to downgrade the kernel of your current working installation. 

Ubuntu 10.4 (Lucid Lynx) is an LTS release which came with kernel 2.6.32. The desktop version is supported until April 2013.

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by ZelAlex on 2012-08-04
Is it possible to install a mainline kernel **without** installing another version of O.S. ??

If not then:
how to install 2 of these? I have WIndows 7 as my main O.S. and have installed ubuntu **inside** Window and when I tried to install another one the same way I needed to uninstall the previous i.e. my 12.04

---

### Post by xb12x on 2012-08-04
> **ZelAlex said:**
> Is it possible to install a mainline kernel **without** installing another version of O.S. ??

If not then:
how to install 2 of these? I have WIndows 7 as my main O.S. and have installed ubuntu **inside** Window and when I tried to install another one the same way I needed to uninstall the previous i.e. my 12.04

I suspect that if you tried to replace the 3.x.x kernel of your current 12.04 installation with an older 2.x.x kernel, you would have all kinds of problems. It might break the display driver, or might not even boot at all.

Have you tried running the examples with your current 12.04?

---

### Post by ZelAlex on 2012-08-04
No I haven't tried. I guess I'll have to start that.

---

