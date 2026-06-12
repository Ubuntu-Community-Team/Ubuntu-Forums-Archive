---
title: "gtkmm programming"
date: 2006-09-02
forum: Programming Talk
---

### Post by u-foka on 2006-09-02
I'm trying to find a C++ programming enviroment in which I would be able to program with gtkmm-2.4. I've tried all the different envirements I could find (anjuta, kdevelop, eclipse) and none of them could be used to compile programs using this package.

Thanks for the help!

---

### Post by JonahRowley on 2006-09-02
All of those are capable of compiling gtkmm projects.  If you post specific error messages, someone might be able to help you configure a project to successfully compile your project.

---

### Post by Loffe_ on 2006-09-03
Maybe you need to install the libgtkmm-2.4-dev package?

---

### Post by u-foka on 2006-09-03
I've had problems installing the dev package for gtkmm-2.0 and the documentation on the net is for the 2.4 version so I tried installing that one, but Anjuta (which worked for 2.0) couldnt use it (and I run into problems with each of the programs mentioned above). Now I could solve this problem by rewriting the configure.in file to say "gtkmm-2.4" instead of "gtkmm-2.0", ran the autoconf and the ./configure and now it compiles correctly, and seems that all is well.

Thanks anyway!

---

