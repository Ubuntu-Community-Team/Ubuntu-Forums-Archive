---
title: "Getting F2PY installed correctly"
date: 2012-02-05
forum: Packaging and Compiling Programs
---

### Post by brushman on 2012-02-05
I'm using Python 2.7.2+ (default, Oct  4 2011, 20:06:09) and the GNU Fortran 95 compiler (4.6.1-9).

From the F2py site, under 'usage', I am following the directions to see if F2py is installed correctly.
[http://www.scipy.org/F2py](http://www.scipy.org/F2py)

The commands 'f2py' and 'f2py -c --help-fcompiler' both run fine, however 'f2py -c -m hello hello.f' doesn't. 

Here is what I get:


```
ben@ben-desktop:~/scratch$ f2py -c -m hello hello.f
running build
running config_cc
unifing config_cc, config, build_clib, build_ext, build commands --compiler options
running config_fc
unifing config_fc, config, build_clib, build_ext, build commands --fcompiler options
running build_src
build_src
building extension "hello" sources
f2py options: []
f2py:> /tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c
creating /tmp/tmpaB6kt8
creating /tmp/tmpaB6kt8/src.linux-x86_64-2.7
Reading fortran codes...
    Reading file 'hello.f' (format:fix,strict)
Post-processing...
    Block: hello
            Block: foo
Post-processing (stage 2)...
Building modules...
    Building module "hello"...
        Constructing wrapper function "foo"...
          foo(a)
    Wrote C/API module "hello" to file "/tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c"
  adding '/tmp/tmpaB6kt8/src.linux-x86_64-2.7/fortranobject.c' to sources.
  adding '/tmp/tmpaB6kt8/src.linux-x86_64-2.7' to include_dirs.
copying /usr/lib/pymodules/python2.7/numpy/f2py/src/fortranobject.c -> /tmp/tmpaB6kt8/src.linux-x86_64-2.7
copying /usr/lib/pymodules/python2.7/numpy/f2py/src/fortranobject.h -> /tmp/tmpaB6kt8/src.linux-x86_64-2.7
build_src: building npy-pkg config files
running build_ext
customize UnixCCompiler
customize UnixCCompiler using build_ext
customize GnuFCompiler
Could not locate executable g77
Found executable /usr/bin/f77
gnu: no Fortran 90 compiler found
gnu: no Fortran 90 compiler found
customize IntelFCompiler
Could not locate executable ifort
Could not locate executable ifc
customize LaheyFCompiler
Could not locate executable lf95
customize PGroupFCompiler
Could not locate executable pgf90
Could not locate executable pgf77
customize AbsoftFCompiler
Could not locate executable f90
absoft: no Fortran 90 compiler found
absoft: no Fortran 90 compiler found
customize NAGFCompiler
Found executable /usr/bin/f95
customize VastFCompiler
customize CompaqFCompiler
Could not locate executable fort
customize IntelItaniumFCompiler
Could not locate executable efort
Could not locate executable efc
customize IntelEM64TFCompiler
customize Gnu95FCompiler
Found executable /usr/bin/gfortran
customize Gnu95FCompiler
customize Gnu95FCompiler using build_ext
building 'hello' extension
compiling C sources
C compiler: gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC

creating /tmp/tmpaB6kt8/tmp
creating /tmp/tmpaB6kt8/tmp/tmpaB6kt8
creating /tmp/tmpaB6kt8/tmp/tmpaB6kt8/src.linux-x86_64-2.7
compile options: '-I/tmp/tmpaB6kt8/src.linux-x86_64-2.7 -I/usr/lib/pymodules/python2.7/numpy/core/include -I/usr/include/python2.7 -c'
gcc: /tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c
/tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c:16:20: fatal error: Python.h: No such file or directory
compilation terminated.
/tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c:16:20: fatal error: Python.h: No such file or directory
compilation terminated.
error: Command "gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/tmp/tmpaB6kt8/src.linux-x86_64-2.7 -I/usr/lib/pymodules/python2.7/numpy/core/include -I/usr/include/python2.7 -c /tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.c -o /tmp/tmpaB6kt8/tmp/tmpaB6kt8/src.linux-x86_64-2.7/hellomodule.o" failed with exit status 1
ben@ben-desktop:~/scratch$ 

```

Any ideas on how to fix this?
Thanks.

---

### Post by MadCow108 on 2012-02-05
you need to install python2.7-dev
```
sudo apt-get install python2.7-dev
```

---

