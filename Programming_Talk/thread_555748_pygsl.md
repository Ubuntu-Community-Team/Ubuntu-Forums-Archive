---
title: "pygsl"
date: 2007-09-20
forum: Programming Talk
---

### Post by MarcosCapistran on 2007-09-20
Has anybody successfully installed pygsl in Feisty? There seems to be a problem of unresolved dependencies with the current versions of python, gcc and gsl. I have no clue on how to address this problem.

Someone told me there may be a repository with the binary.

Any lead?

---

### Post by nanotube on 2007-09-20
i don't know about gsl or pygsl... but if they're not working, maybe you could consider numpy and scipy instead?

---

### Post by MarcosCapistran on 2007-09-20
Thank you for the fast reply.

I have both, scipy and numpy installed. However I need the more refined algorithms from gsl (but I dont want to endure the pain of c programming) <-- regard this as a Python ad! :guitar:

By the way I have now figured out how to install pygsl:

The combo that worked for me (I use ubuntu feisty) is
gsl-bin  1.8-3
libgsl0  1.8-3
libgsl-dev 1.8-3
python2.5.1-0
python2.5.1-0
gcc4:4.1.2-1
numpy1:1.0.1-8

plus the pygsl-0.9.0 tar ball from sourceforge

---

### Post by nanotube on 2007-09-20
glad you solved the problem. :)
so what is it that you're doing that requires gsl, if you don't mind me asking? seems like something interesting. :)

---

### Post by MarcosCapistran on 2007-09-21
First of all, there is nothing wrong with scipy. The developers are doing 
a fine job. But gsl (or pygsl) is more developed (and older). Every algorithm in gsl  is documented with research papers. Further,
gsl allows tighter control on parameters and errors. Is more like if you
implemented the algorithms by yourself.

I use gsl for research.

---

### Post by andrecamara on 2007-10-28
Hi!

I don't know if this is the right place to post this, if not please someone tell me where is it
I'm having problems to install pygsl on ubuntu gutsy amd64, and as I'm new to ubuntu, I didn't find any way out of it. 

I have currently installed:
[INDENT]gsl-bin 1.9-3
libgsl0 1.9-3
libgsl-dev 1.9-3
python2.5.1
gcc4:4.1.3[/INDENT]

the output when I try to run 'python setup.py build' is as follows:
```

andre@andre-laptop:~/downloads/pygsl/pygsl-0.9.1$ python setup.py build
Using 'Numeric' as array object
Numeric
running build
running build_py
running build_ext
building 'errno' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -DSWIG_COBJECT_TYPES=1 -DDEBUG=1 -DNUMERIC=1 -DPYGSL_GSL_MAJOR_VERSION=1 -DPYGSL_GSL_MINOR_VERSION=9 -UNDEBUG -I/usr/include -IInclude -I. -I/usr/include/python2.5 -c src/init/errorno.c -o build/temp.linux-x86_64-2.5/src/init/errorno.o
src/init/errorno.c:5:20: error: Python.h: No such file or directory
In file included from src/init/errorno.c:6:
/usr/include/gsl/gsl_errno.h:23:19: error: stdio.h: No such file or directory
/usr/include/gsl/gsl_errno.h:24:19: error: errno.h: No such file or directory
In file included from src/init/errorno.c:6:
/usr/include/gsl/gsl_errno.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/init/errorno.c:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘errornoMethods’
src/init/errorno.c:37: warning: return type defaults to ‘int’
src/init/errorno.c: In function ‘DL_EXPORT’:
src/init/errorno.c:37: error: expected declaration specifiers before ‘initerrno’
src/init/errorno.c:91: error: expected ‘{’ at end of input
error: command 'gcc' failed with exit status 1

```

is there any other more detailed tutorial / how to to install it in ubuntu?

thanks in advance

---

### Post by pmasiar on 2007-10-29
looks like you need build-essential and friends. Is pygsl included in Universe repository? Are you familiar with Synaptic?

---

### Post by andrecamara on 2007-10-30
I guess it isn't, I couldn't find it on synaptic, so I downloaded it from here ([http://pygsl.sourceforge.net/](http://pygsl.sourceforge.net/))

---

### Post by miketaschuk on 2008-03-14
I've successfully installed pygsl under ubuntu with the python2.5-dev and build-essentials packages installed.  

One of your error messages indicates that it wasn't able to find the Python.h, which is supplied by python2.5-dev.  Or 2.4-dev, I expect.

---

### Post by jackdyson31 on 2008-07-29
Hi everybody,
Thanks for the compilation tips, I managed to install pygsl doing the same.

One thing though does anyone get a few test failures in the test runs? And about pygsl.diff, it doesn't exist ! its been renamed I think to pygsl.deriv. Any comments would be appreciated.

Cheers

Jack

---

### Post by jazzgossen on 2008-12-17
I'm also having trouble compiling pygsl, using Ubuntu 8.04 and pygsl-0.9.4 from Sourceforge.

Compilation output:
```
$ python setup.py build

Numeric
Building testing ufuncs!
running build
running build_py
running build_ext
building 'statistics.char' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DSWIG_COBJECT_TYPES=1 -DDEBUG=1 -DNUMERIC=1 -DPYGSL_GSL_MAJOR_VERSION=1 -DPYGSL_GSL_MINOR_VERSION=10 -UNDEBUG -I/usr/include -IInclude -I. -I/usr/include/python2.5 -c src/statistics/charmodule.c -o build/temp.linux-i686-2.5/src/statistics/charmodule.o
In file included from src/statistics/charmodule.c:25:
src/statistics/functions.c: In function 'statistics_t_A':
src/statistics/functions.c:44: error: 'PyArray_BYTE' undeclared (first use in this function)

```

Then I get a lot of the same error about PyArray_BYTE.

I have the following packages installed:
gsl-bin 1.10-4
libgsl0ldbl 1.10-4
libgsl0-dev 1.10-4
python2.5
python2.5-dev
gcc-4.1
gcc-4.2
python-numpy
python-numarray

What else could be missing?

---

