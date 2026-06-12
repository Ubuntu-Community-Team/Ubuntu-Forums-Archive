---
title: "Eclipse PATH problem"
date: 2010-03-04
forum: Programming Talk
---

### Post by RocketRanger on 2010-03-04
Hi 

Eclipse is being weird on me! I have installed an arm cross-compiler and added it to my path. Now I am trying to get eclipse to use it.

If I give eclipse the complete path to it (under project properties/C-C++ Build/Settings/Tool Settings). I.e. changing g++ to path_to/arm-none-linux-gnueabi-g++.

The system can see it though and I can tab-complete the command so what's wrong with eclipse?

---

### Post by doas777 on 2010-03-04
iirc, you configure the autocomplete in a differant spot that you do the path, but it's been a while since I worked with eclipse. 
hth

---

### Post by aurel_26 on 2010-07-08
Hi RocketRanger,

the same things happened to me.
I'm working on an Ubuntu 10.04 host for x86, and cross-compiling for an arm9 target (arm-linux-gcc).

More over, I was working well with the previous version of Ubuntu (9.10) or with the previous version of eclipse, I don't remember, but it was working, without even writing down the full path in Eclipse option (properties/C-C++ Build/Settings/Tool Settings).

Did you find out a way to solve your (and my ;)) problem.

Thanks

Aurel.

---

