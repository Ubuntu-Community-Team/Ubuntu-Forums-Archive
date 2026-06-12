---
title: "SWIG Profiling"
date: 2011-10-11
forum: Programming Talk
---

### Post by 11jmb on 2011-10-11
Anybody have any experience profiling applications that use SWIG?

I am looking to profile code that is written in c++ with a Python/SWIG wrapper. If I use gprof, is it enough to just compile the c++ code with -pg or will I have to recompile Python/SWIG/NumPy/etc?

If I use something like oprofile will SWIG obfuscate the profiling process?

---

### Post by 11jmb on 2011-10-12
bump/update

oprofile only does call graph profiling for x86, and the code that I need to profile is specifically 64-bit

All of the c++ code is called by python, so I am currently re-compiling my Python library (and swig, just for good measure). 


does anybody have any insight?

---

### Post by Zugzwang on 2011-10-13
You can try running "valgrind --tool=callgrind" on the python process from which you call your c++ code. Here, it doesn't matter if the python interpreter itself does not have debugging symbols. Later, when looking at the results using "kcachegring", you can order the display by binary module and only care about the ones corresponding to your new code. So give it a try! Still, it is wise to compile your c++ code with "-g" to get the debugging symbols in place.

---

