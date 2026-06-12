---
title: "make: *** No rule to make target `install'. Stop."
date: 2008-10-13
forum: New to Ubuntu
---

### Post by themusicalduck on 2008-10-13
Hey,
I'm trying to install Scintilla from source. I'm basically following the readme file, which says to install using these commands:

cd scite/gtk
make
make install

make seems to work fine, but when I try make install, I get the error message - make: *** No rule to make target `install'. Stop.

build-essentials is installed, and trying to do a ./configure before all comes up with - ./configure: No such file or directory

any ideas what might be happening?

---

### Post by DrSantos on 2008-10-13
I don;t know this particular package, but this is the message you usually get when there is know "install" rule in your makefile. You might want to look if there is smth like 
**INSTALL:**
and then some code in the Makefile you are trying to run.

---

