---
title: "GCC problem"
date: 2005-08-15
forum: Programming Talk
---

### Post by jsimmons on 2005-08-15
According to synaptic, I have gcc installed. However, when I go into a terminal and type "gcc -v", I get an error message (don't remember exact text, but I think its' something akin to the old dos error "bad command or file name".

What am I doing wrong?

---

### Post by thumper on 2005-08-15
[QUOTE=jsimmons]According to synaptic, I have gcc installed. However, when I go into a terminal and type "gcc -v", I get an error message (don't remember exact text, but I think its' something akin to the old dos error "bad command or file name".

What am I doing wrong?[/QUOTE]
I have recollections that when I installed gcc 3.4.x through synaptic it didn't have a symlink to gcc, but it did have something like /usr/bin/gcc-3.4 and I manually linked gcc to that (and g++).

Have a look in /usr/bin for gcc*

---

### Post by kwane on 2005-08-15
[QUOTE=jsimmons]According to synaptic, I have gcc installed. However, when I go into a terminal and type "gcc -v", I get an error message (don't remember exact text, but I think its' something akin to the old dos error "bad command or file name".

What am I doing wrong?[/QUOTE]
 How I did it was to type

sudo aptitude install build-essential

---

