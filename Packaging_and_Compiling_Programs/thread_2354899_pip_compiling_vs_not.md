---
title: "pip compiling vs not"
date: 2017-03-07
forum: Packaging and Compiling Programs
---

### Post by b44xi on 2017-03-07
I am in an environment where we are constantly bringing up and spinning down virtual environments, all with different sets of pip installed packages. Works well enough.

Except I would like to know a little more about what is going on behind the scenes. Sometimes pip install launches a lengthy compilation process. Sometimes it does not. This is most notably seen with numpy, mostly because it takes significant time to compile but is negligible time when installing binaries. I have an Ubuntu 14 machine where it always compiles numpy, and an Ubuntu 16 machine where it never compiles numpy.

I assumed that Ubuntu 14 packages were no longer available or something. But then I launched a brand new VM with this same older OS, and pip install numpy, went super fast (no compiling). So clearly it is not simply the OS version impacting me. What is going on here?

Thanks for any help!

---

