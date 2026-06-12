---
title: "What packages to install for GNOME programming ?"
date: 2009-07-10
forum: Programming Talk
---

### Post by Kerubu on 2009-07-10
Hi,

I want to start programming under GNOME and would like to know what developer libraries I need to install or deb packages if they are available.

There's a lot of information about how to program GNOME windows etc, but I haven't found a good clear guide saying what packages I need to install.

I want to program using C++ or (C if I have to).

Many thanks

---

### Post by nvteighen on 2009-07-10
> **Kerubu said:**
> Hi,

I want to start programming under GNOME and would like to know what developer libraries I need to install or deb packages if they are available.

There's a lot of information about how to program GNOME windows etc, but I haven't found a good clear guide saying what packages I need to install.

I want to program using C++ or (C if I have to).

Many thanks

For C: Install libgtk+2.0-dev. For C++: libgtkmm-2.4-dev (hmm... the version may vary; I'm on Debian testing). The dependencies will be satisfied by APT.

But also install libgtk+2.0-doc or otherwise, you'll be lost. And installing the nice devhelper (a documentation browser) never hurts either.

GTK+ is the GUI toolkit used in GNOME and it's originally written in C. GTKmm is an official C++ binding.

---

### Post by JordyD on 2009-07-10
> **nvteighen said:**
> For C: Install libgtk+2.0-dev. For C++: libgtkmm-2.4-dev (hmm... the version may vary; I'm on Debian testing). The dependencies will be satisfied by APT.

But also install libgtk+2.0-doc or otherwise, you'll be lost. And installing the nice devhelper (a documentation browser) never hurts either.

GTK+ is the GUI toolkit used in GNOME and it's originally written in C. GTKmm is an official C++ binding.

Don't forget the build-essential package if you don't already have it.

---

