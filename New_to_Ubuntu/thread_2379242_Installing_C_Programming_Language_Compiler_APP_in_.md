---
title: "Installing C Programming Language Compiler APP in Lubuntu"
date: 2017-12-02
forum: New to Ubuntu
---

### Post by meongggg on 2017-12-02
I just installed Lubuntu on my old laptop, and i want to install all kinds of app in this laptop especialy c compiler (like devcpp or visual studio in windows). Anyone can help me? thank you

---

### Post by Topsiho on 2017-12-03
You may try install build-essential. It contains the gcc-compiler, which compiles c- and other programs.
I'm not sure whether you need to install other packages as well, as I turned to programming in Python, and not in C++ anymore.

Topsiho

---

### Post by Impavidus on 2017-12-03
**build-essential** wasn't really meant as the way to turn your computer into a development platform and it contains some stuff you won't need, but it's an easy way to get all the essential stuff, like compiler and the most important header files. You can also separately install packages like **gcc** (the C compiler), **g++** (the C++ compiler), **gdb** (the debugger), **make** (a great tool to automate compiling and linking) and **libc6-dev** (essential header files). You may have to install other header files. For example, to get the header files of library *foo*, install the package **libfoo-dev**. And of course a decent text editor with syntax highlighting. I prefer **vim**.

You can also install an IDE. There are some in the repositories I believe, but I never used one. I think that the separate tools work together well enough.

---

### Post by genericvii143 on 2017-12-03
Try Codeblock or Netbeans.

---

