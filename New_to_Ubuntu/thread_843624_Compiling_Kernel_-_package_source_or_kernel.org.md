---
title: "Compiling Kernel - package source or kernel.org?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by titus on 2008-06-28
does anyone have any advice on compiling kernels using the source from kernel.org rather than packages? Are there any common problems that arise from this approach?

Do the ubuntu kernel sources have any special patches for ubuntu applied?

Thanks!

---

### Post by sdennie on 2008-06-28
You can use kernel check [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) or, you can follow a guide like this [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).

Common problems are that you've forgotten to compile modules for your sound or wifi adapters, you've forgotten to link your fimrware or that you don't have graphics drivers because you need to manually install them.  Other than that, it's fairly straightforward.

---

### Post by titus on 2008-06-28
thanks for the reply! 

I'm familiar with compiling for slackware, but need to know if there are any specific ubuntu patches applied to the ubuntu kernel sources.

should i use kernel.org source or do I have to use the ubuntu sources?

ps - that howtoforge link is great, thanks!

---

### Post by sdennie on 2008-06-28
I just use the vanilla kernels from kernel.org and have no problems.  The Ubuntu kernel has many, many patches.  You can get them and have a look with:

```

apt-get source linux-image-`uname -r`

```

---

### Post by titus on 2008-06-28
great! thanks a lot.

---

