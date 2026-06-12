---
title: "C++ problem"
date: 2017-03-18
forum: Programming Talk
---

### Post by ghidan on 2017-03-18
Hi guys, i have a problem with the iostream library on ubuntu 16.10, when i start to compile a code with the library iostream i have a fatal error (iostream: no such file or directory #include <iostream>).
I have already installed the build-essential but nothing changed, please help me and if you want more details tell me what you want to know (i have the 16.10 version of ubuntu).

---

### Post by steeldriver on 2017-03-18
How exactly are you trying to compile your code? make sure you are using the C++ compiler not the C compiler

The iostream header file should be installed as a dependency of build-essential (build-essential depends on g++ which depends on g++-6 which depends on libstdc++-6-dev for example)

---

