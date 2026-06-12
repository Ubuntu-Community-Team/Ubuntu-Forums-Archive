---
title: "make and ./domake"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by prasanmouli on 2012-06-07
I am new to linux and am getting used to working in the shell. 
What's the difference between the commands [FONT=Courier New]make[/FONT] and [FONT=Courier New]./domake[/FONT]?

---

### Post by MG&amp;TL on 2012-06-08
Applications which you want to build from source have many large and complicated build commands. This is made easier for developers & users by using a script or program to do this for you, after having configured said program.

GNU Make is a program which is invoked by running *make*. Make is an exceptionally widely-used program that is used in various (more complete) build systems, such as CMake or Autotools, although it is possible to run make on its own. Make reads a file in the current directory called some permutation of "Makefile", then uses that to execute commands to build the source code.

On the other hand, some build systems and developers will choose to use a script to accomplish their build, the most common of which is called "configure" (part of Autoconf), although you have come across "domake". 

To execute a local script in a shell, you force it to use the current directory for execution, rather than searching the various system directories for scripts. The current directory is "./", so "./domake" means "look for a file called domake in the current directory". If you leave off the "./" you'll probably get 'command not found'.

Hope I explained that alright.

---

