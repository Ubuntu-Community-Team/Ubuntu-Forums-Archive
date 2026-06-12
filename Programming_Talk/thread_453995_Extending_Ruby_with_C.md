---
title: "Extending Ruby with C"
date: 2007-05-25
forum: Programming Talk
---

### Post by NevilleS on 2007-05-25
Hello everyone. I've been learning Ruby lately after being brought up on C, C++ and Java, and am quite enjoying myself. However I'm quite intrigued with the ability to write Ruby extensions in C so I can implement low level stuff in C and control it in Ruby. I wanted to do a little proof-of-concept project which was nothing more than a bloated Hello World, but ran into my first problem: I don't seem to have the necessary file "ruby.h" that provides all the framework for the C-side of things. Why is this? I installed the "ruby1.8" package using apt, so I thought I would have everything, but it seems otherwise.

I think the problem is that I'm missing the source code for this package. Where should it be located, so I can double-check if it's truly missing, and how can I get it if it's missing? (I don't see an obvious package in the package manager for the source code).

---

### Post by WW on 2007-05-25
Install **ruby1.8-dev**

---

