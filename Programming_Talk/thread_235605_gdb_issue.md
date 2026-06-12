---
title: "gdb issue"
date: 2006-08-13
forum: Programming Talk
---

### Post by baldmountain on 2006-08-13
Hi,

I'm having a problem starting gdb to build a project configured with autoconf and automake. I get the error:

This GDB was configured as "i486-linux-gnu"..."/home/clements/work/tekhne/trunk/samples/pingpong/pong": not in executable format: File format not recognized

The program is compiled with -g and runs OK, (until it segfaults.) Any pointers on how to get GDB to recognize this application?

Sorry if this is a silly question, I'm relatively new to Linux programming.

---

### Post by baldmountain on 2006-08-13
A little more info... I orignally used Anjuta to build the projects. A shared library and the application were seperate projects. I decided to not use Anjuta and so removed a good bunch of stuff Anjuta created. It looks like the Anjuta Makefile.am and configure.in use libtool. Could it be that libtool is linking the file in a format that gdb doesn't inderstand? I also see that the shared library is actually a pseudo library with a .la extension.

I guess it is time to dive into autconf, automake and libtool a bit more deeply and rewrite configure.in and Makefile.am...

---

### Post by baldmountain on 2006-08-13
Well, a little more info...

It looks like the executable itself is in a hidden directory called .libs. gdb can read that executable. Rather than starting the executable:

gdb ./ping

you start it like:

gdb .libs/ping

---

### Post by baldmountain on 2006-08-13
I still need to learn a bit more about libtool and what exactly it creates, but I made a new target app that links everything statically and gdb has not problem loading that.

---

