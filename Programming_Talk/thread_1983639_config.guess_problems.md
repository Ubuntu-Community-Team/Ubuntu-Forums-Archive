---
title: "config.guess problems"
date: 2012-05-20
forum: Programming Talk
---

### Post by EricDallal on 2012-05-20
Hello,
I am attempting to compile some C source files on my computer by running make bin-dist. The make file doesn't call the compiler itself. Instead, it executes the line:

tar cf - $(VERSION) | gzip > $(VERSION)-$(HOST_OS).tar.gz

where:

HOST_OS := $(shell ./config.guess)

and VERSION is just a string. I am completely confused as to what the ./config.guess file does (it has over a thousand of lines). I am getting errors of the form:

error: expected expression before ‘/’ token

which are caused by the use of // comments (as oppose to /* */ comments). The compilation is being executed as:

gcc -g -O -Wall -ansi -DHASH_TABLE_NAMES

However, when I search through the ./config.guess file, I do not find Wall or ansi anywhere and so I have no idea how to compile this so that I don't get this error. Please help me.

---

### Post by steeldriver on 2012-05-20
did you actually  ./configure before tying to 'make'?

it sounds like you are confused about the whole build process

the compile error is because the compiler is being given the 'ansi' flag - which disallows C++ style commenting - my guess is if your ./configure ran properly it would not do that

also the tar command is nothing to do with compiling - it is probably some kind of post-build re-distribution packaging

without knowing WHAT you are trying to build it is hard to be more specific, but likely you should type

```
./configure
```and then once that has run

```
make
```with no 'target' i.e. don't tell it to 'make bin-dist' let it choose the default target, at least at first

---

### Post by EricDallal on 2012-05-20
There is no configure script in the directory, and the make command gives the error:
Can only make bin-dist or src-dist from here.
if I try to just run make. I suspect that having the make file call config.guess to do the compilation was some cheap hack to compile things in some platform independent way but I don't know enough to say for sure. I think I am just going to build a list of all the .c files and then write a script which compiles each one with different options (most likely, I will just not use the -ansi flag). Now if I could just remember the shell script commands for that...

---

### Post by EricDallal on 2012-05-20
actually, it turns out the make file was calling another make file which had the -ansi flag as one of the options. I removed it and everything works now.

---

