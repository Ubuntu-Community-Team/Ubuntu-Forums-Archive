---
title: "Lisp on Ubuntu/Debian"
date: 2008-12-06
forum: Programming Talk
---

### Post by wtwood on 2008-12-06
I am brand new to Ubuntu and Debian but familiar with lisp programming on other platforms.  After using Synaptic to get  SBCL I was poking around and tripped across the "common-lisp-controller" mechanism.  I found some developer-oriented docs on the Debian site but I haven't found anything about how to set up one's personal file structure to work most harmoniously with the mechanism.  Are there conventions for dot files (I saw reference to a ".clc" but no info on what should be put therein)?  I like the idea of having the cl libraries available to more than one common lisp implementation, but I am in the dark as to how that can be made to happen.  Any hints?

Thanks,

 -- Bill

---

### Post by nvteighen on 2008-12-07
I'm more a Schemer, but I'm almost sure Common Lisp files are usually referred to as .lisp

---

### Post by wtwood on 2008-12-10
Thanks for the thought but I was thinking of initialization files like ~/.cmucl-init.lisp for a CMU Common Lisp init file.  The Debian community seems to have a fairly well thought-out set of conventions for library placement along with initialization files.  I'm trying to find out about them from the user perspective.

---

