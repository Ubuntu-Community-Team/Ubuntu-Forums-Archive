---
title: "How to use the Intel C++ Compiler with Eclipse in Edgy?"
date: 2007-01-08
forum: Programming Talk
---

### Post by PeterSchnitzel on 2007-01-08
Hi everybody, 
I have installed the Intel C++ Compiler (v. 9.1.045) on Ubuntu Edgy. After changing the dash to bash and setting the correct PATH variables I’m able to compile my programs in the shell.

But my Eclipse (v. 3.2.1) with the current CDT Plugin (v. 3.1.1.20060927) don’t compile anything with the icpc nor the icc.
If I put my Makefile together, I always get the following error message:
Make: icpc: Command not found.

But the same command does work in the Shell!

What have I to do, that everything works fine and I’m able to use my icc/icpc in my Eclipse?

I read about the iccec. Eclipse configuration program delivered with the compiler package. But it says always Eclipse* is not available.

I'd really appreciate any advice anyone can give me on this.
Peter

---

### Post by leohart on 2007-11-02
I think the reason that icpc is not found is because it is not in your PATH. Eclipse is start in X without settings the PATH variables as you normally get when using the commandline.

Try running eclipse from the command line
> eclipse

Then try again, it should then work. Have you had any luck in this matter so far? I am trying to get Intel Compiler to run with Gutsy. It has been a long time, I think Intel should really get their act together and release a working deb package for Ubuntu.

---

