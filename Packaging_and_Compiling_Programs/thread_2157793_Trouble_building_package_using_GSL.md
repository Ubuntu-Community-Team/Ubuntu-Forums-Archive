---
title: "Trouble building package using GSL"
date: 2013-06-26
forum: Packaging and Compiling Programs
---

### Post by aluchko on 2013-06-26
I've been having trouble building and running [QUB Express]("http://www.qub.buffalo.edu/wiki/index.php/Developers") on Ubuntu machines. I've been able to do so on Fedora and OS X systems, and I've previously been able to build it on one (if not two) of my Ubuntu systems though recently I've been unable to run the built executable.

The problem comes when building one of the libraries using GSL, the build finishes successfully but GSL isn't linked into the shared object, as a result when the app tries to load the library it gets

```
Traceback (most recent call last):
  File "/home/aluchko/.local/lib/python2.7/site-packages/qubopt/qubopt_common.py", line 83, in <module>
    qo = ctypes.CDLL('libqubopt.so') #, mode=ctypes.RTLD_GLOBAL)
  File "/usr/lib/python2.7/ctypes/__init__.py", line 365, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /home/aluchko/.local/lib/libqubopt.so: undefined symbol: gsl_matrix_alloc

```


This is the relevant command from the make and the resulting executable, on other systems gsl and cblas are linked in, any idea why they aren't here, or how I can try to find the problem? 

```
$ g++  -shared -fPIC -lm -L. -lqubtree -lgsl -lgslcblas -g -o libqubopt.so obj/qubopt/ztox.o obj/qubopt/dfpminim.o obj/qubopt/svdecomp.o obj/qubopt/mexp.o obj/qubopt/ExprEval.o obj/qubopt/xtoq.o obj/qubopt/qub_dfilter.o obj/qubopt/mil_eval_tree.o obj/qubopt/qublib.o obj/qubopt/QUB_UniqueArrays.o obj/qubopt/mpl_eval_tree.o obj/qubopt/convolve.o obj/qubopt/metamakv.o obj/qubopt/sparseutil.o obj/qubopt/ioldt.o obj/qubopt/LoadDataCB_Pager.o obj/qubopt/qtomutiq.o obj/qubopt/mdlrep.o obj/qubopt/mvectb.o obj/qubopt/skm_eval_tree.o obj/qubopt/amp_eval_tree.o obj/qubopt/dfp_optimize.o obj/qubopt/histpdf.o obj/qubopt/mbaum.o obj/qubopt/qmatrixutil.o obj/qubopt/modelTree.o obj/qubopt/utility.o obj/qubopt/stat_eval_tree.o obj/qubopt/milutil.o obj/qubopt/eigen.o obj/qubopt/matrixutil.o obj/qubopt/qub_reportstream.o obj/qubopt/mutimakv.o

$ ldd libqubopt.so
          linux-vdso.so.1 =>  (0x00007fffbe522000)
         libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f6b4d090000)
         libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f6b4cd94000)
         libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f6b4cb7d000)
         libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6b4c7be000)
         /lib64/ld-linux-x86-64.so.2 (0x00007f6b4d6aa000)
```

Note the build does complete successfully, it just fails to run due to the missing gsl libraries.

---

### Post by DeathByDenim on 2013-06-26
I just downloaded it as well to test it and I get the exact same error (on Kubuntu 13.04). You might want to file a bug report through their contact form: [http://www.qub.buffalo.edu/contact.html](http://www.qub.buffalo.edu/contact.html)
I don't see anything wrong with the compiling process, since libquopt.so is definitely build with -lgsl, which should be enough.

---

### Post by aluchko on 2013-06-26
I'm in email contact with author but I don't think it's just an issue with the project. I've got back to versions from April (which definitely worked at the time) and the problem remains. It seems like something must have changed in Ubuntu or both my environments in the meanwhile.

---

### Post by aluchko on 2013-06-27
So I've been able to run it by building in Fedora then transferring the shared objects to Ubuntu, and I seem to recall doing so in April. However, I've also gone to QUB versions as far back as September 2011 with the same results, and I'm pretty sure I would have built and ran on those Ubuntu systems in the interim. So the Ubuntu problem remains though there's at least a work around I can use.

---

### Post by DeathByDenim on 2013-06-27
I figured it out. It's really weird and I don't have an explanation for it, but when linking the library libqubopt.so, you need to put all the -l stuff at the end of the command. So, instead of
```
$ g++  -shared -fPIC -lm -L. -lqubtree -lgsl -lgslcblas -g -o libqubopt.so obj/qubopt/ztox.o obj/qubopt/dfpminim.o obj/qubopt/svdecomp.o obj/qubopt/mexp.o obj/qubopt/ExprEval.o obj/qubopt/xtoq.o obj/qubopt/qub_dfilter.o obj/qubopt/mil_eval_tree.o obj/qubopt/qublib.o obj/qubopt/QUB_UniqueArrays.o obj/qubopt/mpl_eval_tree.o obj/qubopt/convolve.o obj/qubopt/metamakv.o obj/qubopt/sparseutil.o obj/qubopt/ioldt.o obj/qubopt/LoadDataCB_Pager.o obj/qubopt/qtomutiq.o obj/qubopt/mdlrep.o obj/qubopt/mvectb.o obj/qubopt/skm_eval_tree.o obj/qubopt/amp_eval_tree.o obj/qubopt/dfp_optimize.o obj/qubopt/histpdf.o obj/qubopt/mbaum.o obj/qubopt/qmatrixutil.o obj/qubopt/modelTree.o obj/qubopt/utility.o obj/qubopt/stat_eval_tree.o obj/qubopt/milutil.o obj/qubopt/eigen.o obj/qubopt/matrixutil.o obj/qubopt/qub_reportstream.o obj/qubopt/mutimakv.o
```
you need
```
$ g++  -shared -fPIC -lm -L. -g -o libqubopt.so obj/qubopt/ztox.o obj/qubopt/dfpminim.o obj/qubopt/svdecomp.o obj/qubopt/mexp.o obj/qubopt/ExprEval.o obj/qubopt/xtoq.o obj/qubopt/qub_dfilter.o obj/qubopt/mil_eval_tree.o obj/qubopt/qublib.o obj/qubopt/QUB_UniqueArrays.o obj/qubopt/mpl_eval_tree.o obj/qubopt/convolve.o obj/qubopt/metamakv.o obj/qubopt/sparseutil.o obj/qubopt/ioldt.o obj/qubopt/LoadDataCB_Pager.o obj/qubopt/qtomutiq.o obj/qubopt/mdlrep.o obj/qubopt/mvectb.o obj/qubopt/skm_eval_tree.o obj/qubopt/amp_eval_tree.o obj/qubopt/dfp_optimize.o obj/qubopt/histpdf.o obj/qubopt/mbaum.o obj/qubopt/qmatrixutil.o obj/qubopt/modelTree.o obj/qubopt/utility.o obj/qubopt/stat_eval_tree.o obj/qubopt/milutil.o obj/qubopt/eigen.o obj/qubopt/matrixutil.o obj/qubopt/qub_reportstream.o obj/qubopt/mutimakv.o -lqubtree -lgsl -lgslcblas
```
Don't ask me why, but after doing that, it works...

---

### Post by aluchko on 2013-06-27
Wow that's weird and awesome. I've done up a quick patch and I'll send it to the maintainer. Thanks a bunch!

---

### Post by aluchko on 2013-06-27
So the author applied the fixes and sent me back this explanation as to the behaviour

"
-l library
It makes a difference where in the command you write this option; the linker searches and processes libraries and object files in the order they are specified. Thus, ‘foo.o -lz bar.o’ searches library ‘z’ after file foo.obut before bar.o. If bar.o refers to functions in ‘z’, those functions may not be loaded.
"

[http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html)

---

### Post by DeathByDenim on 2013-06-27
Ah, I see. That makes sense.
Thanks for clearing that up!

---

