---
title: "Something about Intel's C++ Compiler"
date: 2006-09-24
forum: Programming Talk
---

### Post by angkel07 on 2006-09-24
Will G++, Make and other building tools use Intel's C++ Compiler when it's installed?

Do I still have to do something before it uses it?

Is there a better guide on installing Intel C++ Compiler?

---

### Post by maubp on 2006-09-25
First do a "make clean" to start from fresh.

Try setting the environment variables (which are probably blank, or set to gcc and g++ at the moment),

export CC=icc
export CXX=icpc

Then re-run configure and make.

Double check your make file too, in case it uses CFLAGS to specify gcc style options which may not work.

P.S. I think intel provide a script to do this stuff for you, where you run "source ..." - they suggest you stick this line in your .bashrc to happen automatically if you will always use icc

---

### Post by angkel07 on 2006-09-25
CXX is a real variable? or does the XX thing corresponds to something else?

---

### Post by maubp on 2006-09-26
Are you familiar with environment variables?  PATH is the most commonly used one.

And yes, CXX is exactly as typed - its a way of representing C++ using only upper case letters.

The idea is to setup environment variables specifying which C and C++ compilers should be used.

I think if you are using a configure script, you can also specify these as arguments.

If you are using a Makefile, then you could specify the compilers there - otherwise it usually defaults to the environment variables (?) or gcc.

P.S. The official instructions should say something like this:

Setup the Intel C++ compiler related environment variables by executing the iccvars.sh (or .csh) script:



source /opt/intel/cc/9.1.xxx/bin/iccvars.sh


(where "xxx" is the version number)

This will setup the PATH, LD_LIBRARY_PATH, MANPATH, INTEL_LICENSE_FILE environment variables - which you may also need.

---

