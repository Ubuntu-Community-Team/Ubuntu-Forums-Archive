---
title: "java program call my kernel module"
date: 2009-06-09
forum: Programming Talk
---

### Post by anonmars on 2009-06-09
Hello,

I've written a basic kernel module (mostly as a learning exercise) now I want to write a Java program that "calls/executes" the kernel module function. Does anyone have a pointer to a good resource on how to do this?

Thanks.

---

### Post by SSTwinrova on 2009-06-09
I think JNI is what you need to look into: [http://en.wikipedia.org/wiki/Java_Native_Interface](http://en.wikipedia.org/wiki/Java_Native_Interface)

---

### Post by randallecook on 2009-06-11
SSTwinrova is right. JNI will get you from Java to C, then from C you should be able to reach your kernel module, but I don't know exactly how.

---

