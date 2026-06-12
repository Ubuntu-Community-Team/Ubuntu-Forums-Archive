---
title: "Nightmare attempting to compile Gnofract4d-3.3"
date: 2007-04-19
forum: Packaging and Compiling Programs
---

### Post by crash test dummy on 2007-04-19
alternative title : How to install Gnofract4d in 72 hours (or more)

i usually don't post on forums, but i feel the time has come for me to be the stupid noob asking a horrible question. (Preliminary note : i have followed various other forum suggestions and the official site for Gnofract4d - all with no luck). i have tried running synaptic and installing various packages (gcc, gcc-c++, gtk2-dev, gconf-2.0, etc.) which were dependencies but i'm still getting the same error message upon trying to build.

Now some specs : i386 machine, Ubuntu 6.10, 1.7ghz, and Gnome wm

I just want to ask has anyone compiled Gnofract4d on a similar setup? Is this even possible?
I can't tell if the problem is with my Python or C++ any ideas????

Here's the error :
mynamehere@computer:~/Desktop/gnofract4d-3.3$ ./setup.py build
NO JPEG HEADERS FOUND
running build
running build_py
running my_build_ext
compiling with None
building 'fract4d.fract4dc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT=1 -DGCONF_ENABLED=1 -DPNG_ENABLED=1 -UNDEBUG -Ifract4d/c -I/usr/include/python2.4 -c fract4d/c/fract4dmodule.cpp -o build/temp.linux-i686-2.4/fract4d/c/fract4dmodule.o -O0 -Wall -I/usr/include/libpng12
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
fract4d/c/fract4dmodule.cpp:14:20: error: Python.h: No such file or directory
fract4d/c/fract4dmodule.cpp:38: error: expected constructor, destructor, or type conversion before ‘*’ token
fract4d/c/fract4dmodule.cpp: In function ‘int ensure_cmap_loaded()’:
fract4d/c/fract4dmodule.cpp:60: error: ‘PATH_MAX’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:68: error: ‘pymod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:68: error: ‘PyModule_GetFilename’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:70: error: ‘strrchr’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:73: error: ‘cwd’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:73: error: ‘getcwd’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:74: error: ‘strlen’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:77: error: ‘strlen’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:80: error: ‘malloc’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:81: error: ‘strncpy’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:83: error: ‘strcat’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:90: error: ‘PyExc_ValueError’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:90: error: ‘PyErr_SetString’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:96: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:125: error: ISO C++ forbids declaration of ‘PyObject’ with no type
fract4d/c/fract4dmodule.cpp:125: error: expected ‘;’ before ‘*’ token
fract4d/c/fract4dmodule.cpp: In function ‘void pf_delete(void*)’:
fract4d/c/fract4dmodule.cpp:137: error: ‘struct pfHandle’ has no member named ‘pyhandle’
fract4d/c/fract4dmodule.cpp:137: error: ‘Py_DECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:138: error: ‘free’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:141: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:177: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:177: error: ‘pyitem’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:177: error: expected primary-expression before ‘char’
fract4d/c/fract4dmodule.cpp:177: error: expected primary-expression before ‘double’
fract4d/c/fract4dmodule.cpp:177: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:178: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:193: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:193: error: ‘pyitem’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:193: error: expected primary-expression before ‘char’
fract4d/c/fract4dmodule.cpp:193: error: expected primary-expression before ‘double’
fract4d/c/fract4dmodule.cpp:193: error: expected primary-expression before ‘int’
fract4d/c/fract4dmodule.cpp:193: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:194: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:233: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:233: error: ‘pyitem’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:233: error: expected primary-expression before ‘char’
fract4d/c/fract4dmodule.cpp:233: error: expected primary-expression before ‘int’
fract4d/c/fract4dmodule.cpp:233: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:234: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:248: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:248: error: ‘pyarray’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:249: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:304: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:338: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:338: error: ‘py_posparams’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:338: error: expected primary-expression before ‘double’
fract4d/c/fract4dmodule.cpp:338: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:339: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:373: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:373: error: ‘pyarray’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:373: error: expected primary-expression before ‘int’
fract4d/c/fract4dmodule.cpp:373: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:374: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:473: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:518: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:550: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:599: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:642: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:701: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:725: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:750: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:776: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:815: error: expected `)' before ‘*’ token
fract4d/c/fract4dmodule.cpp:950: error: ISO C++ forbids declaration of ‘PyObject’ with no type
fract4d/c/fract4dmodule.cpp:950: error: expected ‘;’ before ‘*’ token
fract4d/c/fract4dmodule.cpp: In member function ‘virtual void PySite::iters_changed(int)’:
fract4d/c/fract4dmodule.cpp:828: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:828: error: ‘ret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:829: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:832: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:833: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘virtual void PySite::image_changed(int, int, int, int)’:
fract4d/c/fract4dmodule.cpp:841: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:841: error: ‘ret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:842: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:844: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:845: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘virtual void PySite::progress_changed(float)’:
fract4d/c/fract4dmodule.cpp:854: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:854: error: ‘ret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:855: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:857: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:858: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘virtual void PySite::status_changed(int)’:
fract4d/c/fract4dmodule.cpp:864: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:868: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:868: error: ‘ret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:871: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:873: error: ‘PyErr_Occurred’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:876: error: ‘PyErr_Print’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:878: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘virtual bool PySite::is_interrupted()’:
fract4d/c/fract4dmodule.cpp:886: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:886: error: ‘pyret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:887: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:888: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:891: error: ‘PyInt_Check’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:893: error: ‘PyInt_AsLong’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:898: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘virtual void PySite::pixel_changed(const double*, int, int, int, int, int, double, int, int, int, int, int, int)’:
fract4d/c/fract4dmodule.cpp:913: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:913: error: ‘pyret’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:914: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:921: error: ‘PyObject_CallMethod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:923: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In destructor ‘virtual PySite::~PySite()’:
fract4d/c/fract4dmodule.cpp:945: error: ‘site’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:945: error: ‘Py_DECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:982: error: ISO C++ forbids declaration of ‘PyObject’ with no type
fract4d/c/fract4dmodule.cpp:982: error: expected ‘;’ before ‘*’ token
fract4d/c/fract4dmodule.cpp:1004: error: ‘PyObject’ has not been declared
fract4d/c/fract4dmodule.cpp:1011: error: ‘PyObject’ has not been declared
fract4d/c/fract4dmodule.cpp:1019: error: ‘PyObject’ has not been declared
fract4d/c/fract4dmodule.cpp:1025: error: ‘PyObject’ has not been declared
fract4d/c/fract4dmodule.cpp: In constructor ‘calc_args::calc_args()’:
fract4d/c/fract4dmodule.cpp:988: error: ‘pycmap’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:989: error: ‘pypfo’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:990: error: ‘pyim’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:991: error: ‘pysite’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘void calc_args::set_cmap(int*)’:
fract4d/c/fract4dmodule.cpp:1006: error: ‘pycmap’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1007: error: ‘PyCObject_AsVoidPtr’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1008: error: ‘Py_XINCREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘void calc_args::set_pfo(int*)’:
fract4d/c/fract4dmodule.cpp:1013: error: ‘pypfo’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1015: error: ‘PyCObject_AsVoidPtr’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1016: error: ‘Py_XINCREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘void calc_args::set_im(int*)’:
fract4d/c/fract4dmodule.cpp:1021: error: ‘pyim’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1022: error: ‘PyCObject_AsVoidPtr’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1023: error: ‘Py_XINCREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘void calc_args::set_site(int*)’:
fract4d/c/fract4dmodule.cpp:1027: error: ‘pysite’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1028: error: ‘PyCObject_AsVoidPtr’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1029: error: ‘Py_XINCREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In destructor ‘calc_args::~calc_args()’:
fract4d/c/fract4dmodule.cpp:1037: error: ‘pycmap’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1037: error: ‘Py_XDECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1038: error: ‘pypfo’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1039: error: ‘pyim’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1040: error: ‘pysite’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In member function ‘void FDSite::send(msg_t*)’:
fract4d/c/fract4dmodule.cpp:1060: error: ‘write’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: In destructor ‘virtual FDSite::~FDSite()’:
fract4d/c/fract4dmodule.cpp:1170: error: ‘close’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:1194: error: ISO C++ forbids declaration of ‘PyObject’ with no type
fract4d/c/fract4dmodule.cpp:1194: error: expected ‘;’ before ‘*’ token
fract4d/c/fract4dmodule.cpp: In function ‘void ff_delete(ffHandle*)’:
fract4d/c/fract4dmodule.cpp:1205: error: ‘struct ffHandle’ has no member named ‘pyhandle’
fract4d/c/fract4dmodule.cpp:1205: error: ‘Py_DECREF’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:1209: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1229: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1245: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1269: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1315: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1335: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1355: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1378: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1478: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1478: error: ‘args’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1478: error: ‘PyObject’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1478: error: ‘kwds’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:1478: error: initializer expression list treated as compound expression
fract4d/c/fract4dmodule.cpp:1479: error: expected ‘,’ or ‘;’ before ‘{’ token
fract4d/c/fract4dmodule.cpp:1570: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1635: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1663: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1693: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1723: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1751: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1779: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1816: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1837: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1858: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1879: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1917: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1953: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:1986: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2025: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2050: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2072: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2122: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2155: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2174: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2193: error: expected initializer before ‘*’ token
fract4d/c/fract4dmodule.cpp:2212: error: ‘PyMethodDef’ does not name a type
fract4d/c/fract4dmodule.cpp: In function ‘void initfract4dc()’:
fract4d/c/fract4dmodule.cpp:2314: error: ‘pymod’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:2314: error: ‘PfMethods’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:2314: error: ‘Py_InitModule’ was not declared in this scope
fract4d/c/fract4dmodule.cpp:2317: error: ‘PyModule_AddIntConstant’ was not declared in this scope
fract4d/c/fract4dmodule.cpp: At global scope:
fract4d/c/fract4dmodule.cpp:49: warning: ‘void pf_unload(void*)’ defined but not used
fract4d/c/fract4dmodule.cpp:58: warning: ‘int ensure_cmap_loaded()’ defined but not used
fract4d/c/fract4dmodule.cpp:130: warning: ‘void pf_delete(void*)’ defined but not used
fract4d/c/fract4dmodule.cpp:248: warning: ‘cmap_from_pyobject’ defined but not used
fract4d/c/fract4dmodule.cpp:338: warning: ‘parse_posparams’ defined but not used
fract4d/c/fract4dmodule.cpp:373: warning: ‘parse_params’ defined but not used
fract4d/c/fract4dmodule.cpp:1181: warning: ‘void site_delete(IFractalSite*)’ defined but not used
fract4d/c/fract4dmodule.cpp:1187: warning: ‘void fw_delete(IFractWorker*)’ defined but not used
fract4d/c/fract4dmodule.cpp:1199: warning: ‘void ff_delete(ffHandle*)’ defined but not used
fract4d/c/fract4dmodule.cpp:1455: warning: ‘void* calculation_thread(void*)’ defined but not used
fract4d/c/fract4dmodule.cpp:1478: warning: ‘parse_calc_args’ defined but not used
fract4d/c/fract4dmodule.cpp:1627: warning: ‘void image_delete(IImage*)’ defined but not used
fract4d/c/fract4dmodule.cpp:1774: warning: ‘void image_writer_delete(ImageWriter*)’ defined but not used
error: command 'gcc' failed with exit status 1


sorry if this isn't the right place to ask this question....
any suggestions are appreciated, thanks for your time!

---

### Post by WW on 2007-04-19
I am running dapper.  I downloaded gnofract4d-3.3, and "./setup.py build" finished successfully.  In order to get all the tests in "./test.py" to succeed, I had to install **transcode**.  Since I already have a lot of -dev packages installed, I'm not sure which packages you are missing, but a quick browse through setup.py suggests that you should at least install **libjpeg62-dev**, **python2.4-dev**, and **transcode**.

---

### Post by JohanL on 2007-05-07
Thanks WW. I had the exact same problem as the original poster. Your solution worked and gnofract is running fine. I'm on Feisty.

Thanks!:)

---

### Post by christhemonkey on 2007-05-07
**@crash test dummy** The line: > fract4d/c/fract4dmodule.cpp:14:20: error: Python.h: No such file or directory Suggests that you need the package python-dev.
```
sudo apt-get install python-dev 
```

Then try compiling again and it should remove most (if not all) of those errors.

---

