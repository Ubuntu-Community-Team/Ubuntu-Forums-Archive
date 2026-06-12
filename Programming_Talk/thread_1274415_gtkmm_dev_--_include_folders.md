---
title: "gtkmm dev -- include folders??"
date: 2009-09-24
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-09-24
I am new to GTK development, but I am very comfortable with C++ overall (I am currently developing a couple game projects in SDL).

I want to use the gtkmm library, but I simply cannot get anything to work. I added the gtkmm folder to my include-folders list, but it still misses many header files. I started adding more and more folders based on the missing header files, but it would never end. I have to be doing something wrong.

Which include folders should I target? What libraries should I link to? I've downloaded gtkmm samples that claim to work, but my configuration is simply wrong. (I am using Code::Blocks to do this.)

---

### Post by MadCow108 on 2009-09-24
use pkg-config to get the needed flags:
pkg-config --libs --cflags gtkmm-2.4

---

### Post by TheBuzzSaw on 2009-09-24
I'll give that a try. I just have one other question: while I do most of my development in Ubuntu, will I need to link mingw32 in Windows as I do for SDL?

---

