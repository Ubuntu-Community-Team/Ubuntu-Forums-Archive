---
title: "Compiling specific modules in Linux kernel"
date: 2014-04-17
forum: Programming Talk
---

### Post by akshay-sulakhe on 2014-04-17
Hello friends,
                   I am currently working on SELinux and I need to make changes in it. I wanted to know if it is possible that I only download SELinux, make the modifications I want to and compile only SELinux. I am currently using Ubuntu 13.10x64. If it is possible, then do I have to download Ubuntu patched SELinux. Kindly let me know. Thank you for your help. If you have any doubts, please reply I will clarify to my best ability.

---

### Post by ofnuts on 2014-04-18
Hmm. SELinux is integrated in the kernels used by Ubuntu (and in practice in the kernels of all major distros). But do you want to modify the kernel or the user tools? If your target is the kernel, then you'll find plenty of howto's about recompiling a Linux kernel on the web. 

But given that you seem to be completely new at this, what are the odds that you won't introduce a security hole?

---

