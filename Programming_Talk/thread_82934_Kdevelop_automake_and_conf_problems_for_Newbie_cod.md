---
title: "Kdevelop automake and conf problems for Newbie coder"
date: 2005-10-27
forum: Programming Talk
---

### Post by blastradius on 2005-10-27
I'm just starting to have a go at C++,  i've read a good book and have a reasonable understanding of C.
I've installed Kdevelop on my Ubuntu+Kubuntu desktop but when i try to compile a program (even one of the default hello world type) i get:-

cd '/home/eric/code/hellowprld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/home/eric/code/hellowprld/debug' && CXXFLAGS="-O0 -g3" "/home/eric/code/hellowprld/configure" --enable-debug=full && cd '/home/eric/code/hellowprld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/bin/sh: make: command not found
*** Exited with status: 127 ***

I've checked and automake and autoconf is installed, i've even reinstalled Kdevelop but still the same problem.

Please help, i just want to write some code and compile and (hopefully) execute it!!  I'll worry about major projects (ultima maybe!) later on.

Thanks

Eric

---

### Post by noigeaR on 2005-10-27
looks like you don't have make installed (not automake, just make).
have you installed the build-essential package?

**sudo apt-get install build-essential**

this installs make, gcc, etc.
you can also use synaptic or adept (on kubuntu) to install this package.

---

### Post by blastradius on 2005-10-28
[QUOTE=noigeaR]looks like you don't have make installed (not automake, just make).
have you installed the build-essential package?

**sudo apt-get install build-essential**

this installs make, gcc, etc.
you can also use synaptic or adept (on kubuntu) to install this package.[/QUOTE]

Thank you very much!

 it works now and my sanity is restored.
Why on Earth isn't it installed along with Kdevelop? surely Kdevelop is useless without it, at least it should pop up an error and tell you to install the package, if you're a new programmer like me you're immediately  stuck on your first program!

---

### Post by David Marrs on 2005-10-28
I'd have thought that too. Perhaps it's worth mentioning to the package maintainer.

---

