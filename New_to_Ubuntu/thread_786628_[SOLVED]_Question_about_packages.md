---
title: "[SOLVED] Question about packages"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by unimatrix on 2008-05-08
I can't count myself as an absolute beginner, but I think this question certainly belongs here. Somehow I never really found the answer to it...

What is the actual (content) difference between ordinary and -dev packages in Ubuntu?
And is this package naming scheme Ubuntu-specific or do all distros use it (or just the Debian based ones)?

---

### Post by hyper_ch on 2008-05-08
the -dev packages, as far as I understand it, sort of contain rather instructions on how to use the actual ones.

They are often required when you want to compile a program on your own.

I think it's for all debian based one the same.

---

### Post by Monicker on 2008-05-08
Other distros, such as Fedora/Red Hat, also have separate dev packages.

---

### Post by Achetar on 2008-05-08
The -dev packages contain the resources to compile programs that require that specific package. One example is compiling Battle for Wesnoth. You must have libsdl1.2 (or something like that) installed to play the one from the repos, but you need libsdl1.2-dev to compile the latest version of it from source code.

---

### Post by Joeb454 on 2008-05-08
It's true - if you are looking to compile something, it will tell you what dependencies are missing, so you tend to install <package>-dev which will allow the header files etc. for compiling :)

It's quite fun/useful if you need it :)

---

### Post by unimatrix on 2008-05-08
So, to clarify this further, I've looked into the package content using Synaptic. 
The -dev packages do NOT contain any source code. Merely the header (.h) files, documentation (for development?), and the .so and .a files. What exactly are the .so/.a files?

---

### Post by lemming465 on 2008-05-08
Source packages contain source code trees and patches to adapt them to Debian or Ubuntu.  Compiling the source requires include files for dependent library headers and stuff; that where the -dev packages come in.  .a files are library archives; see "man ar".  .so files are shared library archives, which can be dynamically loaded at runtime rather than having to be statically added to each program separately at compile and link time.

---

