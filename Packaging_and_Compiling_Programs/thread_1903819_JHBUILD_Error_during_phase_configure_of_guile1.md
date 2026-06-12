---
title: "JHBUILD: Error during phase configure of guile1"
date: 2012-01-03
forum: Packaging and Compiling Programs
---

### Post by Arrow2Knee on 2012-01-03
Hi everyone,
I am following [this]("http://live.gnome.org/Jhbuild") guide to compile GNOME Shell. With jhbuild sanitycheck, there is some trouble so I run jhbuild bootstrap. I get an error at installing Guile1:

configure: error: libltdl not found.  See README.
***** Error during phase configure of guile1: ########## Error running ./configure --prefix /opt/gnome --libdir '/opt/gnome/lib' --enable-error-on-warning=no --disable-static --disable-gtk-doc  *** [3/4]**

I also tried installing both guile 1.6 and 1.8 using apt-get, without success.

Google search didn't gave me anything.

Thanks already!

EDIT: found it, I installed libtdl-dev package

---

