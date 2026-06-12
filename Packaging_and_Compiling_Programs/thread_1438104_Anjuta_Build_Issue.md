---
title: "Anjuta Build Issue"
date: 2010-03-24
forum: Packaging and Compiling Programs
---

### Post by JaMartini on 2010-03-24
Hello,  I am trying to get Anjuta IDE working on Ubuntu. I followed the directions for the initial build but I get the following:  configure: creating ./config.status config.status: error: cannot find input file: `Makefile.in' Completed unsuccessfully   Anyone have any ideas what this means? Im new to Linux/Ubuntu so I'm not sure if this is a problem with my Anjuta settings or I am missing something in Ubuntu.  Thanks for the help!

---

### Post by MadCow108 on 2010-03-26
why not install it over the package manager?
sudo apt-get install anjuta

@ your problem:
do you have the build dependencies installed (especially autoconf/automake)?
if not sure execute:
sudo apt-get build-dep anjuta

have you executed ./autogen.sh before running configure?

---

