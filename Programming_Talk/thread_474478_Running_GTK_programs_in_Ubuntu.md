---
title: "Running GTK programs in Ubuntu"
date: 2007-06-15
forum: Programming Talk
---

### Post by deepank on 2007-06-15
Hi, I made a standard hello world program in GTK and then tried to compile it using the command : 
gcc hello.c -o base `pkg-config --cflags --libs gtk+-2.0`
But I get the error : 
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

Please tell me what should I do in order to get the program running.

---

### Post by Gannin on 2007-06-15
I know this is an obvious question, but, do you have the GTK2+ dev libraries installed?

---

