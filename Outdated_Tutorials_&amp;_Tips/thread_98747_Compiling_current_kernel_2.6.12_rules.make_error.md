---
title: "Compiling current kernel 2.6.12 rules.make error"
date: 2005-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by nexx_ on 2005-12-04
Okay i've done a search around on google and on the ubuntu forums and I can't seem to find out what's happening.

Whenever I try to compile the kernel from source [2.6.12.10] or [2.6.12] it failes whenever i run any make commands, make mrproper, make menuconfig etc and I get an error:
Makefile:544: Rules.make: No such file or directory
make: *** No rule to make target `Rules.make'.  Stop.

I have tried various kernel sources and it seems that 2.6.xx kernels don't seem to include this file?
I read that they might be in the Makefiles?
I also read this guide but nothing seems to work:
[http://doc.gwos.org/index.php/Kernel_Compilation](http://doc.gwos.org/index.php/Kernel_Compilation)

It's really annoying me because it seems that no-one else is getting this problem, 
I can't find any reason why it won't compile and why I don't have Rules.make?

I hope someones can help me, thanks in advance.

---

