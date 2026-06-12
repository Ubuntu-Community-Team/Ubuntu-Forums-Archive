---
title: "problem with SWIG"
date: 2010-07-08
forum: Programming Talk
---

### Post by miak on 2010-07-08
Hi I'm trying to use SWIG to incorporate some of my C code into a python software, but have some problems in doing so. When I got problems I went to basics and tried to use SWIG with very basic example,..... factorial! :) Here is my code for factorial in c
```
/*myModule.c */
#include <stdio.h>

int fact(int n) {
    if(n==0) {
        return 1;
    }else{
        return n*fact(n-1);
    }
}

```Here is the code for interface 
```
/*myModule.i*/
%module myModule
%{
extern int fact( int n);
%}

extern int fact(int n);
```after writing this pieces of code I followed instructions in [here]("http://www.dabeaz.com/cgi-bin/wiki.pl?SwigFaqLinuxSharedLibraries") , link to which I followed from [swig.org]("http://www.swig.org/tutorial.html"). Instructions from tutorial on swing.org was using python2.1 and when I tried I get about the same errors(never checked thoroughly) for you convenience here are the instructions:
```
 If you are using GCC 4.x under Ubuntu and using python 2.6 try the  following 
    $ swig -python module.i
    $ gcc -fpic -I/usr/include/python2.6 -c module_wrap.c
    $ gcc -shared module_wrap.o -o module.so

```First i did 
```
swig -python myModule.i
``` and everything was ok, but after ```
gcc -fpic -I/usr/include/python2.6 -c myModule_wrap.c
``` i get the following error message:
```
myModule_wrap.c:125:20: error: Python.h: No such file or directory
myModule_wrap.c:756: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:780: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:806: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:860: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:881: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c: In function ‘SWIG_Python_AddErrorMsg’:
myModule_wrap.c:928: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:928: error: (Each undeclared identifier is reported only once
myModule_wrap.c:928: error: for each function it appears in.)
myModule_wrap.c:928: error: ‘type’ undeclared (first use in this function)
myModule_wrap.c:929: error: ‘value’ undeclared (first use in this function)
myModule_wrap.c:930: error: ‘traceback’ undeclared (first use in this function)
myModule_wrap.c:935: error: ‘old_str’ undeclared (first use in this function)
myModule_wrap.c:944: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:1049: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1124: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1132: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1143: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1196: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1298: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1309: error: expected specifier-qualifier-list before ‘PyObject’
myModule_wrap.c: In function ‘SWIG_Python_CheckImplicit’:
myModule_wrap.c:1321: error: ‘SwigPyClientData’ has no member named ‘implicitconv’
myModule_wrap.c: At top level:
myModule_wrap.c:1324: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1333: error: expected ‘)’ before ‘*’ token
myModule_wrap.c: In function ‘SwigPyClientData_Del’:
myModule_wrap.c:1388: error: ‘SwigPyClientData’ has no member named ‘newraw’
myModule_wrap.c:1389: error: ‘SwigPyClientData’ has no member named ‘newargs’
myModule_wrap.c:1390: error: ‘SwigPyClientData’ has no member named ‘destroy’
myModule_wrap.c: At top level:
myModule_wrap.c:1396: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
myModule_wrap.c:1403: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1409: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1431: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1443: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1471: error: expected declaration specifiers or ‘...’ before ‘FILE’
myModule_wrap.c: In function ‘SwigPyObject_print’:
myModule_wrap.c:1477: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:1477: error: ‘repr’ undeclared (first use in this function)
myModule_wrap.c:1481: error: ‘fp’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:1490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c: In function ‘SwigPyObject_compare’:
myModule_wrap.c:1501: error: ‘SwigPyObject’ has no member named ‘ptr’
myModule_wrap.c:1502: error: ‘SwigPyObject’ has no member named ‘ptr’
myModule_wrap.c: At top level:
myModule_wrap.c:1507: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1524: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1526: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1533: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1538: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1542: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1576: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1593: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1609: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1633: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1681: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘swigobject_methods’
myModule_wrap.c:1693: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1700: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1833: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1851: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
myModule_wrap.c:1858: error: expected declaration specifiers or ‘...’ before ‘FILE’
myModule_wrap.c: In function ‘SwigPyPacked_print’:
myModule_wrap.c:1861: error: ‘fp’ undeclared (first use in this function)
myModule_wrap.c:1862: error: ‘SwigPyPacked’ has no member named ‘pack’
myModule_wrap.c:1862: error: ‘SwigPyPacked’ has no member named ‘size’
myModule_wrap.c:1866: error: ‘SwigPyPacked’ has no member named ‘ty’
myModule_wrap.c: At top level:
myModule_wrap.c:1871: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1882: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c: In function ‘SwigPyPacked_compare’:
myModule_wrap.c:1896: error: ‘SwigPyPacked’ has no member named ‘size’
myModule_wrap.c:1897: error: ‘SwigPyPacked’ has no member named ‘size’
myModule_wrap.c:1899: error: ‘SwigPyPacked’ has no member named ‘pack’
myModule_wrap.c:1899: error: ‘SwigPyPacked’ has no member named ‘pack’
myModule_wrap.c:1899: error: ‘SwigPyPacked’ has no member named ‘size’
myModule_wrap.c: At top level:
myModule_wrap.c:1902: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1904: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:1911: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1917: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:1926: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2008: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2028: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2044: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2050: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2065: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2116: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2131: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2222: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2254: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2346: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2367: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2406: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c: In function ‘SWIG_Python_GetModule’:
myModule_wrap.c:2428: warning: assignment makes pointer from integer without a cast
myModule_wrap.c: At top level:
myModule_wrap.c:2442: error: expected ‘)’ before ‘*’ token
myModule_wrap.c: In function ‘SWIG_Python_SetModule’:
myModule_wrap.c:2488: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘swig_empty_runtime_method_table’
myModule_wrap.c:2488: error: ‘swig_empty_runtime_method_table’ undeclared (first use in this function)
myModule_wrap.c:2488: error: expected expression before ‘]’ token
myModule_wrap.c:2494: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:2494: error: ‘module’ undeclared (first use in this function)
myModule_wrap.c:2497: error: ‘pointer’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:2506: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c: In function ‘SWIG_Python_TypeQuery’:
myModule_wrap.c:2515: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:2515: error: ‘cache’ undeclared (first use in this function)
myModule_wrap.c:2516: error: ‘key’ undeclared (first use in this function)
myModule_wrap.c:2517: error: ‘obj’ undeclared (first use in this function)
myModule_wrap.c: In function ‘SWIG_Python_AddErrMesg’:
myModule_wrap.c:2545: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:2545: error: ‘type’ undeclared (first use in this function)
myModule_wrap.c:2546: error: ‘value’ undeclared (first use in this function)
myModule_wrap.c:2547: error: ‘traceback’ undeclared (first use in this function)
myModule_wrap.c:2551: error: ‘old_str’ undeclared (first use in this function)
myModule_wrap.c: In function ‘SWIG_Python_ArgFail’:
myModule_wrap.c:2574: warning: incompatible implicit declaration of built-in function ‘snprintf’
myModule_wrap.c: At top level:
myModule_wrap.c:2582: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2590: error: expected declaration specifiers or ‘...’ before ‘PyObject’
myModule_wrap.c: In function ‘SWIG_Python_TypeError’:
myModule_wrap.c:2604: error: ‘obj’ undeclared (first use in this function)
myModule_wrap.c:2606: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:2606: error: ‘str’ undeclared (first use in this function)
myModule_wrap.c:2609: error: ‘PyExc_TypeError’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:2629: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2671:4: error: #error "This python version requires swig to be run with the '-classic' option"
myModule_wrap.c:2709: error: expected ‘)’ before ‘*’ token
myModule_wrap.c: In function ‘SWIG_CanCastAsInteger’:
myModule_wrap.c:2765: error: ‘errno’ undeclared (first use in this function)
myModule_wrap.c:2765: error: ‘EDOM’ undeclared (first use in this function)
myModule_wrap.c:2765: error: ‘ERANGE’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:2789: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2828: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:2846: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2855: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:2877: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SwigMethods’
myModule_wrap.c:3161: error: expected specifier-qualifier-list before ‘PyObject’
myModule_wrap.c:3167: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
myModule_wrap.c:3171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3219: error: expected declaration specifiers or ‘...’ before ‘FILE’
myModule_wrap.c: In function ‘swig_varlink_print’:
myModule_wrap.c:3221: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:3221: error: ‘str’ undeclared (first use in this function)
myModule_wrap.c:3222: warning: incompatible implicit declaration of built-in function ‘fprintf’
myModule_wrap.c:3222: error: ‘fp’ undeclared (first use in this function)
myModule_wrap.c: In function ‘swig_varlink_dealloc’:
myModule_wrap.c:3231: error: ‘swig_varlinkobject’ has no member named ‘vars’
myModule_wrap.c:3233: error: ‘swig_globalvar’ has no member named ‘next’
myModule_wrap.c:3234: warning: incompatible implicit declaration of built-in function ‘free’
myModule_wrap.c: At top level:
myModule_wrap.c:3240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3258: error: expected declaration specifiers or ‘...’ before ‘PyObject’
myModule_wrap.c: In function ‘swig_varlink_setattr’:
myModule_wrap.c:3260: error: ‘swig_varlinkobject’ has no member named ‘vars’
myModule_wrap.c:3263: error: ‘swig_globalvar’ has no member named ‘set_attr’
myModule_wrap.c:3263: error: ‘p’ undeclared (first use in this function)
myModule_wrap.c:3266: error: ‘swig_globalvar’ has no member named ‘next’
myModule_wrap.c:3269: error: ‘PyExc_NameError’ undeclared (first use in this function)
myModule_wrap.c: At top level:
myModule_wrap.c:3274: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3334: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3344: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:3360: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
myModule_wrap.c:3373: error: expected ‘)’ before ‘*’ token
myModule_wrap.c:3400: error: expected ‘)’ before ‘*’ token
myModule_wrap.c: In function ‘init_myModule’:
myModule_wrap.c:3460: error: ‘PyObject’ undeclared (first use in this function)
myModule_wrap.c:3460: error: ‘m’ undeclared (first use in this function)
myModule_wrap.c:3460: error: ‘d’ undeclared (first use in this function)
myModule_wrap.c:3476: error: ‘SwigMethods’ undeclared (first use in this function)

```Any Ideas what's going wrong? Am i doing something wrong?

btw, I'm have:
SWIG Version 1.3.40
gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3
and I'm running 64bit Ubuntu 10.04

Thanks,
miak

---

### Post by miak on 2010-07-09
Can anyone point out to a tutorial that they know produces results that work??
Anyone got swig working?????

---

### Post by johnl on 2010-07-09
I suspect that you are either missing some required packages or you are pointing to the wrong version of python headers.

Off the top of my head, I would suggest making sure you have the 'python-dev' package installed, and try:

```

gcc -fpic -I/usr/include/python2.8 -c module_wrap.c

```

---

### Post by miak on 2010-07-09
Hi,

Thanks for the reply,
It turned out I didn't have python-dev, or python2.6-dev, in my case. 
I have python 2.6.5 installed so that shouldn't be a problem.
After that I still had some error trying it that way(build went without errors but I was getting errors when importing myModule)(sorry for not showing the error message, but I don't think i kept it :( )

Good news is that I found the way to compile this basic application.
There is a something called "distutils" in every python distribution(since 1.something) it turns out to be a really good tool for doing this kind of job.
You create a setup.py file in the same directory, here is my setup.py 
```
#!/usr/bin/env python

"""
setup.py file for myModule SWIG module
"""

from distutils.core import setup, Extension

myModule = Extension('_myModule', sources=['myModule_wrap.c', 'myModule.c'],)

setup ( name = 'myModule',
        version = '0.1',
        author = 'miak',
        description = """Simple example module""",
        ext_modules = [myModule],
        py_modules = ["myModule"],
        )
```and then using this two lines you get your module in python:
```
$ swig -python example.i
$ python setup.py build_ext --inplace

```I found out this by reading documentation on swig found in "swig-doc" package.
Haven't tried anything with GTK which is my primary goal, but hope that it works

---

