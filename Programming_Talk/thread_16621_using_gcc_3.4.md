---
title: "using gcc 3.4"
date: 2005-02-22
forum: Programming Talk
---

### Post by lgoss007 on 2005-02-22
I keep running into this problem:

```
g++: Internal error: Killed (program cclplus)
```

And I noticed that Ubuntu uses gcc/g++ 3.3 by default. Is there a way or a make option, besides setting it in the makefile, to compile with gcc/g++ 3.4 by default?

---

### Post by dataw0lf on 2005-02-23
Run a memtest for me. And tell me how much memory you have to start with.
dataw0lf

---

### Post by lgoss007 on 2005-02-24
```
bash: memtest: command not found.
```

Are you talking about the memtest that can be run on boot? memtest86+?

256M, no failures.

I eventually got 3.3 to work by just doing make over and over again. Why is gcc 3.3 the default and not 3.4?

---

### Post by dataw0lf on 2005-02-24
The reason why I asked about memory is that the error you listed is one associated with too little memory and/or bad memory.  
dataw0lf

---

### Post by tbair on 2006-08-10
I was able to solve this error but doing:

apt-get install  build-essential

---

### Post by neilp85 on 2006-08-13
As a follow up, you can set your default compiler to any gcc version you want with the following commands:

export CC='gcc-<version num>'
export CXX='g++-<version num>'

This works well with any program that's built with an autoconfiguration tool that actually uses these variables but not so well with makefiles that are coded by hand. I've yet to find a way to easily change those.

---

### Post by DoktorSeven on 2006-08-14
> **neilp85 said:**
> This works well with any program that's built with an autoconfiguration tool that actually uses these variables but not so well with makefiles that are coded by hand. I've yet to find a way to easily change those.

Continuing to unearth an old thread, there is usually a line at the beginning of hand-coded makefiles that specify the compiler, usually

CC=gcc

Change that to 

CC=gcc-3.4

---

