---
title: "Broken Upgrade"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-09-28
I was updating Kubuntu when I encountered an error message and found that these three have not been upgraded and one is broken:

GDB
The GNU Debugger (upgradeable)
GDB is a source-level debugger, capable of breaking programs at any specific line, displaying variable values, and determining where errors occurred. Currently, it works for C, C++, Fortran, Modula 2 and Java programs. A must-have for any serious programmer.

libc6-i686 (BROKEN, upgradeable)
GNU C Library: Shared libraries [i686 optimized]
Contains the standard libraries that are used by nearly all programs on the system. This package includes shared versions of the standard C library and the standard math library, as well as many others.
This set of libraries is optimized for i686 machines, and will only be used if you are running a 2.6 kernel on an i686 class CPU (check the output of `uname -m'). This includes Pentium Pro, Pentium II/III/IV, Celeron CPU's and similar class CPU's (including clones such as AMD Athlon/Opteron, VIA C3 Nehemiah, but not VIA C3 Ezra).

python-gtkhtml2 (upgradeable)
Python bindings for the GtkHTML2 library
This archive contains a module that allows you to write Python programs that use the GtkHTML2 library.

My PC's processor is an Athlon XP 2400+. 


What should I do? Thanks!

---

### Post by Pro-reason on 2008-09-29
Try this from the command line:

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

```

Just an idea.

---

### Post by nowshining on 2008-09-29
try also

sudo apt-get install -f
sudo apt-get autoremove

if all else fails

sudo apt-get clean and then try upgrading again.. all commands are to be put in the terminal...and ur pw won't show as you type...

---

