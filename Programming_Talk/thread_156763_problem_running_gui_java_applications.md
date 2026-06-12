---
title: "problem running gui java applications"
date: 2006-04-07
forum: Programming Talk
---

### Post by darth_vector on 2006-04-07
i am trying to run an application with some swing stuff in it. it compiles fine, and i know it works because i have run it on other machines without a problem. when i try to run it on my machine i get the following> ** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted
anyone have any ideas on what could be causing this and how to fix it?

cheers

---

### Post by darth_vector on 2006-04-07
i found [http://199.232.76.165/archive/html/bug-classpath/2005-08/msg00128.html](http://199.232.76.165/archive/html/bug-classpath/2005-08/msg00128.html) which refers to the problem as a know bug, but no fixes are given.

funny it says its a debian issue, it runs fine on the debian machines at uni.

---

