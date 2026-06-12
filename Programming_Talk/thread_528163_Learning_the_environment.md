---
title: "Learning the environment"
date: 2007-08-17
forum: Programming Talk
---

### Post by dhodgeh on 2007-08-17
What's a good source of information for learning the overall development environment for Ubuntu?

I'm talking library and folder structures, project management, tools and such.

I'm an old C programmer coming in from another platform and would like a better feel for whats available to work with.  

I'm not much of an IDE person - a good editor (i.e. vim) and a set of command line tools is all I need.  However, I do like to know how my tools work.

Thanks in advance 

Don

---

### Post by Mirrorball on 2007-08-17
Ubuntu has more or less the basic Linux layout. Sometimes a program might be installed in different directories in different Linux distros but if you can't find the file you want, Synaptic will tell you where all the installed files are for every installed package.

---

### Post by pmasiar on 2007-08-17
> **Mirrorball said:**
> Synaptic will tell you where all the installed files are for every installed package.

How? :oops:

---

### Post by Mirrorball on 2007-08-17
> **pmasiar said:**
> How? :oops:
Right click the package name, chose Properties, Installed Files. ;)

---

### Post by slavik on 2007-08-17
gcc is the compiler, gdb is the debuger (compile with -g), ddd is a GUI front end to gdb.

gcc -o program -g -Wall program.c

---

### Post by fct on 2007-08-18
If the other platform you're coming from is UNIX, you don't have much to worry about. Ubuntu is linux, that itself is yet another UNIX-based operating system.

Most of the posix documentation is valid.

---

### Post by Jessehk on 2007-08-18
> **pmasiar said:**
> How? :oops:

```

$ dpkg -L <package>

```

---

### Post by Fingolfin on 2007-10-01
> **slavik said:**
> ddd is a GUI front end to gdb.

Perhaps also worth mentioning  xxgdb  which is the classic-style X-windows front-end for gdb  (another alternative could be kdbg?!).

---

