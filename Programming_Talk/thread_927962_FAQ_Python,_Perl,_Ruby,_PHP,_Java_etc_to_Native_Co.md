---
title: "FAQ: Python, Perl, Ruby, PHP, Java etc to Native Code"
date: 2008-09-23
forum: Programming Talk
---

### Post by LaRoza on 2008-09-23
Asking if Python can be compiled to native code is a hit in this forum.

The answer: sort of.

The who point of using a high level language like Python is to avoid the problems with native code. It is fully cross platform. It is compiled to byte code and is run on an optimized platform. If speed (like that) mattered, you wouldn't write it in Python in the first place, but in C (or Fortran, etc). Speed-wise, you can prototype in Python then rewrite in C et al, write the speed hungry parts in C and use them in the Python program, use the ctypes and other Python methods of getting the C like features in a Python program, or not use Python all together. <chorus>Or not use Python</chorus>

If your goal is distribution, usually wanting to use Python to write a program, but not require people to install Python to use, the [ActivePython](http://www.activestate.com/Products/activepython/index.mhtml) installer is extremely easy to use. Most libraries have Windows installers as well. Python is pre-installed on the other platforms most of the time. Anyone not using an OS (which isn't Windows) and doesn't have Python, probably knows how to install it. If you still want to compile it, you can use several methods, but remember, only do it if you really need it. It won't be any faster doing this (probably), as it essentially bundles the Python runtime with the code. If your concerns are speed, make sure they are well founded and it is optimal at the algorithmic level already before saying such a language isn't suitable. Speed is usually over estimated.

Here will be a list of ways to negate the requirement of a separate runtime installation in various languages, suggestions welcome (because I am only going to add one link)

**Python**
[list]
[*] [Compiling Python Code]("http://effbot.org/zone/python-compile.htm"): Older, but many of the links are still valid I know.
[/list]

---

