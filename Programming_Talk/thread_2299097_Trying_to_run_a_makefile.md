---
title: "Trying to run a makefile"
date: 2015-10-15
forum: Programming Talk
---

### Post by Chris_Laskaris on 2015-10-15
I have some source code and a makefile (named make_node00) for Linux, and I am trying to use the makefile to compile the program from source. Which command do I have to use to do this? I am posting the beginning of the makefile here:

```
#------------------------------------------------------
# Makefile for compiling on linux
#------------------------------------------------------

SHELL = /bin/sh

.SUFFIXES: .F .c .o

# [and so on, commands for compiling the program follow after this]
```

I have tried **sh make_node00** and **./make_node00**, but I am getting error messages (**SHELL: not found**, or **SHELL: command not found**, and the same for all the other commands in the makefile).

I feel I should be able to get the makefile to work if I only find the right command for it, and it's probably very easy. But I am new to using such makefiles.

Thank you for your help!

---

### Post by steeldriver on 2015-10-15
```

make -f make_node00

```

Although it would be more usual to use a default name such as Makefile or makefile so that you only need to type

```

make

```

---

### Post by Chris_Laskaris on 2015-10-15
Thank you! That did it.

---

### Post by dwhitney67 on 2015-10-22
> **Chris_Laskaris said:**
> Thank you! That did it.

Btw, your Makefile does not require the executable bit enabled on it.  Typically a Makefile only has read-write permissions.  Earlier when you indicated that when you ran your Makefile such as ./make_node00, you should have seen an error indicating "permission denied".

---

