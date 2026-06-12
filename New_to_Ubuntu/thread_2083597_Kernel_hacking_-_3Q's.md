---
title: "Kernel hacking - 3Q's"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by XBMC old School on 2012-11-13
1) I have recompiled my kernel to be a low-latency desktop kernel and was wonder is there a way to put my own custom name on it without the kernel prefix? the terminal command i use to create the image and headers is as follows;

fakeroot make-kpkg --initrd --append-to-version=-inappropriate-comment-here  kernel_image kernel_headers

2)There are a few driver devices in the "make menuconfig" option. They are all marked as modularized features. Can Some be excluded? What is the drawback of having driver modules you don't need?

There is stuff in there that are for features my board doesn't have or for out dated hardware that my install will never see.

i would like to skim it out if i can(for fun) but i don't want to blind hack and slash at it. Is there a rule of thumb (if it ain't broke & if you don't know, are not acceptible). The help function doesn't give guidance on every item.

3) There is alot of x86 features. If i have a amd64 install, can i exclude them all? It won't affect any software 32bit software will it?

---

### Post by XBMC old School on 2012-11-13
bump

---

### Post by XBMC old School on 2012-11-15
bump

---

