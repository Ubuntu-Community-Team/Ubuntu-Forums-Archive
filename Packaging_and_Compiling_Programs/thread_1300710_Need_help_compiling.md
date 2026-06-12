---
title: "Need help compiling"
date: 2009-10-25
forum: Packaging and Compiling Programs
---

### Post by Blackylol on 2009-10-25
I need to compile this tool (usbtool) so I can use my steering wheel in linux, but i've tried of many ways and I cant make it, it ask me for files idk how to obtain.

file source: [http://filebeam.com/248c6a47e66668cb3e88b45d2b1a9c11](http://filebeam.com/248c6a47e66668cb3e88b45d2b1a9c11)

These are the instructions

Build dependices: libusb, swig (for build python libusb wrapper) 
 
Just unpack tarball and run build.sh 
 
Run dependices: libusb, python 
 
start python usbtool or ./usbtool --list for help

Can anyone help ? thanks

---

### Post by mikeym on 2009-10-25
try:

```

sudo apt-get install libusb-dev swig

```

then run build.sh and see how you do

---

### Post by mikeym on 2009-10-25
Sorry double post - Chromium doesn't like the ubuntuforums :(

---

### Post by Blackylol on 2009-10-25
This is what happens.

```
/usr/include/usb.h:331: Warning(302): Identifier 'usb_device' redefined (ignored),
/usr/include/usb.h:243: Warning(302): previous definition of 'usb_device'.
libusb_wrap.c:124:20: error: Python.h: No existe el fichero ó directorio
libusb_wrap.c:730: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:785: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:806: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c: In function ‘SWIG_Python_AddErrorMsg’:
libusb_wrap.c:853: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:853: error: (Each undeclared identifier is reported only once
libusb_wrap.c:853: error: for each function it appears in.)
libusb_wrap.c:853: error: ‘type’ undeclared (first use in this function)
libusb_wrap.c:854: error: ‘value’ undeclared (first use in this function)
libusb_wrap.c:855: error: ‘traceback’ undeclared (first use in this function)
libusb_wrap.c:857: warning: implicit declaration of function ‘PyErr_Occurred’
libusb_wrap.c:857: warning: implicit declaration of function ‘PyErr_Fetch’
libusb_wrap.c:859: error: ‘old_str’ undeclared (first use in this function)
libusb_wrap.c:859: warning: implicit declaration of function ‘PyObject_Str’
libusb_wrap.c:860: warning: implicit declaration of function ‘PyErr_Clear’
libusb_wrap.c:861: warning: implicit declaration of function ‘Py_XINCREF’
libusb_wrap.c:862: warning: implicit declaration of function ‘PyErr_Format’
libusb_wrap.c:862: warning: implicit declaration of function ‘PyString_AsString’
libusb_wrap.c:863: warning: implicit declaration of function ‘Py_DECREF’
libusb_wrap.c:866: warning: implicit declaration of function ‘PyErr_SetString’
libusb_wrap.c:866: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
libusb_wrap.c: At top level:
libusb_wrap.c:1034: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1042: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1053: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1060: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1106: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1219: error: expected specifier-qualifier-list before ‘PyObject’
libusb_wrap.c: In function ‘SWIG_Python_CheckImplicit’:
libusb_wrap.c:1231: error: ‘PySwigClientData’ has no member named ‘implicitconv’
libusb_wrap.c: At top level:
libusb_wrap.c:1234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1243: error: expected ‘)’ before ‘*’ token
libusb_wrap.c: In function ‘PySwigClientData_Del’:
libusb_wrap.c:1298: warning: implicit declaration of function ‘Py_XDECREF’
libusb_wrap.c:1298: error: ‘PySwigClientData’ has no member named ‘newraw’
libusb_wrap.c:1299: error: ‘PySwigClientData’ has no member named ‘newargs’
libusb_wrap.c:1300: error: ‘PySwigClientData’ has no member named ‘destroy’
libusb_wrap.c: At top level:
libusb_wrap.c:1306: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
libusb_wrap.c:1313: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1319: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1337: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1343: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1349: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1372: error: expected declaration specifiers or ‘...’ before ‘FILE’
libusb_wrap.c: In function ‘PySwigObject_print’:
libusb_wrap.c:1377: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:1377: error: ‘repr’ undeclared (first use in this function)
libusb_wrap.c:1377: warning: implicit declaration of function ‘PySwigObject_repr’
libusb_wrap.c:1380: warning: implicit declaration of function ‘fputs’
libusb_wrap.c:1380: error: ‘fp’ undeclared (first use in this function)
libusb_wrap.c: At top level:
libusb_wrap.c:1388: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c: In function ‘PySwigObject_compare’:
libusb_wrap.c:1399: error: ‘PySwigObject’ has no member named ‘ptr’
libusb_wrap.c:1400: error: ‘PySwigObject’ has no member named ‘ptr’
libusb_wrap.c: At top level:
libusb_wrap.c:1404: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1406: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1413: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1418: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1422: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1456: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1473: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1489: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1501: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1561: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘swigobject_methods’
libusb_wrap.c:1573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1580: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1688: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1706: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
libusb_wrap.c:1713: error: expected declaration specifiers or ‘...’ before ‘FILE’
libusb_wrap.c: In function ‘PySwigPacked_print’:
libusb_wrap.c:1716: error: ‘fp’ undeclared (first use in this function)
libusb_wrap.c:1717: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1717: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1721: error: ‘PySwigPacked’ has no member named ‘ty’
libusb_wrap.c: At top level:
libusb_wrap.c:1726: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1737: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c: In function ‘PySwigPacked_compare’:
libusb_wrap.c:1751: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1752: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’

libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘pack’
libusb_wrap.c:1754: error: ‘PySwigPacked’ has no member named ‘size’
libusb_wrap.c: At top level:
libusb_wrap.c:1757: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1759: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1766: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1772: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1781: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1851: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1871: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1887: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:1903: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1954: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:1969: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2060: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2092: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2178: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2199: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2217: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c: In function ‘SWIG_Python_GetModule’:
libusb_wrap.c:2259: warning: implicit declaration of function ‘PyCObject_Import’
libusb_wrap.c:2260: warning: assignment makes pointer from integer without a cast
libusb_wrap.c: At top level:
libusb_wrap.c:2274: error: expected ‘)’ before ‘*’ token
libusb_wrap.c: In function ‘SWIG_Python_DestroyModule’:
libusb_wrap.c:2315: warning: implicit declaration of function ‘SWIG_This’
libusb_wrap.c: In function ‘SWIG_Python_SetModule’:
libusb_wrap.c:2320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘swig_empty_runtime_method_table’
libusb_wrap.c:2320: error: ‘swig_empty_runtime_method_table’ undeclared (first use in this function)
libusb_wrap.c:2320: error: expected expression before ‘]’ token
libusb_wrap.c:2322: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:2322: error: ‘module’ undeclared (first use in this function)
libusb_wrap.c:2322: warning: implicit declaration of function ‘Py_InitModule’
libusb_wrap.c:2324: error: ‘pointer’ undeclared (first use in this function)
libusb_wrap.c:2324: warning: implicit declaration of function ‘PyCObject_FromVoidPtr’
libusb_wrap.c:2326: warning: implicit declaration of function ‘PyModule_AddObject’
libusb_wrap.c: At top level:
libusb_wrap.c:2333: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c: In function ‘SWIG_Python_TypeQuery’:
libusb_wrap.c:2342: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:2342: error: ‘cache’ undeclared (first use in this function)
libusb_wrap.c:2342: warning: implicit declaration of function ‘SWIG_Python_TypeCache’
libusb_wrap.c:2343: error: ‘key’ undeclared (first use in this function)
libusb_wrap.c:2343: warning: implicit declaration of function ‘PyString_FromString’
libusb_wrap.c:2344: error: ‘obj’ undeclared (first use in this function)
libusb_wrap.c:2344: warning: implicit declaration of function ‘PyDict_GetItem’
libusb_wrap.c:2347: warning: implicit declaration of function ‘PyCObject_AsVoidPtr’
libusb_wrap.c:2353: warning: implicit declaration of function ‘PyDict_SetItem’
libusb_wrap.c: In function ‘SWIG_Python_AddErrMesg’:
libusb_wrap.c:2372: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:2372: error: ‘type’ undeclared (first use in this function)
libusb_wrap.c:2373: error: ‘value’ undeclared (first use in this function)
libusb_wrap.c:2374: error: ‘traceback’ undeclared (first use in this function)
libusb_wrap.c:2377: error: ‘old_str’ undeclared (first use in this function)
libusb_wrap.c: In function ‘SWIG_Python_ArgFail’:
libusb_wrap.c:2399: warning: implicit declaration of function ‘snprintf’
libusb_wrap.c:2399: warning: incompatible implicit declaration of built-in function ‘snprintf’
libusb_wrap.c: At top level:
libusb_wrap.c:2407: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2415: error: expected declaration specifiers or ‘...’ before ‘PyObject’
libusb_wrap.c: In function ‘SWIG_Python_TypeError’:
libusb_wrap.c:2429: error: ‘obj’ undeclared (first use in this function)
libusb_wrap.c:2431: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:2431: error: ‘str’ undeclared (first use in this function)
libusb_wrap.c:2434: error: ‘PyExc_TypeError’ undeclared (first use in this function)
libusb_wrap.c: At top level:
libusb_wrap.c:2453: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2511:4: error: #error "This python version requires swig to be run with the '-classic' option"
libusb_wrap.c: In function ‘usb_bulk_read_wrapped’:
libusb_wrap.c:2537: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
libusb_wrap.c:2538: error: expected ‘;’ before ‘res’
libusb_wrap.c:2539: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
libusb_wrap.c:2540: error: expected ‘;’ before ‘if’
libusb_wrap.c:2542: error: ‘else’ without a previous ‘if’
libusb_wrap.c: In function ‘usb_interrupt_read_wrapped’:
libusb_wrap.c:2550: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
libusb_wrap.c:2551: error: expected ‘;’ before ‘res’
libusb_wrap.c:2552: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
libusb_wrap.c:2553: error: expected ‘;’ before ‘if’
libusb_wrap.c:2555: error: ‘else’ without a previous ‘if’
libusb_wrap.c: At top level:
libusb_wrap.c:2573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2580: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2588: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2595: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2615: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2643: error: expected ‘)’ before ‘*’ token
libusb_wrap.c: In function ‘SWIG_CanCastAsInteger’:
libusb_wrap.c:2699: error: ‘errno’ undeclared (first use in this function)
libusb_wrap.c:2699: error: ‘EDOM’ undeclared (first use in this function)
libusb_wrap.c:2699: error: ‘ERANGE’ undeclared (first use in this function)
libusb_wrap.c: At top level:
libusb_wrap.c:2723: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2762: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2778: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2822: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2832: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2886: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2894: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2910: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:2927: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2949: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2971: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:2984: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3005: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3012: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3034: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3056: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3078: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3091: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3229: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3242: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3263: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3270: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3358: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3446: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3468: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3524: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3597: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3641: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3685: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3707: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3729: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3751: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3773: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3795: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3808: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3829: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3836: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3858: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3880: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3914: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3921: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3943: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3965: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:3987: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4009: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4031: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4053: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4075: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4097: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4119: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4163: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4176: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4197: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4204: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4226: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4270: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4358: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4380: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4446: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4468: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4490: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4512: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4525: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4546: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4597: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4641: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4676: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4697: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4704: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4726: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4748: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4776: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4798: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4820: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4842: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4864: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4886: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4908: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4930: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4943: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4964: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4971: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:4993: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5015: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5043: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5065: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5087: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5150: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:5156: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5164: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5208: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5264: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5311: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5493: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5548: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5609: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5664: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5746: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5777: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5808: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5839: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5870: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5901: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5932: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:5954: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6006: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6037: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6050: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6062: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6083: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6096: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6153: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6273: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6331: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SwigMethods’
libusb_wrap.c:6829: error: expected specifier-qualifier-list before ‘PyObject’
libusb_wrap.c:6835: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
libusb_wrap.c:6839: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6844: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6857: error: expected declaration specifiers or ‘...’ before ‘FILE’
libusb_wrap.c: In function ‘swig_varlink_print’:
libusb_wrap.c:6858: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:6858: error: ‘str’ undeclared (first use in this function)
libusb_wrap.c:6858: warning: implicit declaration of function ‘swig_varlink_str’
libusb_wrap.c:6859: warning: implicit declaration of function ‘fprintf’
libusb_wrap.c:6859: warning: incompatible implicit declaration of built-in function ‘fprintf’
libusb_wrap.c:6859: error: ‘fp’ undeclared (first use in this function)
libusb_wrap.c:6860: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
libusb_wrap.c: In function ‘swig_varlink_dealloc’:
libusb_wrap.c:6867: error: ‘swig_varlinkobject’ has no member named ‘vars’
libusb_wrap.c:6869: error: ‘swig_globalvar’ has no member named ‘next’
libusb_wrap.c: At top level:
libusb_wrap.c:6876: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6894: error: expected declaration specifiers or ‘...’ before ‘PyObject’
libusb_wrap.c: In function ‘swig_varlink_setattr’:
libusb_wrap.c:6896: error: ‘swig_varlinkobject’ has no member named ‘vars’
libusb_wrap.c:6899: error: ‘swig_globalvar’ has no member named ‘set_attr’
libusb_wrap.c:6899: error: ‘p’ undeclared (first use in this function)
libusb_wrap.c:6902: error: ‘swig_globalvar’ has no member named ‘next’
libusb_wrap.c:6905: error: ‘PyExc_NameError’ undeclared (first use in this function)
libusb_wrap.c: At top level:
libusb_wrap.c:6910: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6962: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:6972: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:6988: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libusb_wrap.c:7001: error: expected ‘)’ before ‘*’ token
libusb_wrap.c:7028: error: expected ‘)’ before ‘*’ token
libusb_wrap.c: In function ‘init_libusb’:
libusb_wrap.c:7081: error: ‘PyObject’ undeclared (first use in this function)
libusb_wrap.c:7081: error: ‘m’ undeclared (first use in this function)
libusb_wrap.c:7081: error: ‘d’ undeclared (first use in this function)
libusb_wrap.c:7081: warning: left-hand operand of comma expression has no effect
libusb_wrap.c:7084: warning: implicit declaration of function ‘SWIG_Python_FixMethods’
libusb_wrap.c:7084: error: ‘SwigMethods’ undeclared (first use in this function)
libusb_wrap.c:7087: warning: implicit declaration of function ‘PyModule_GetDict’
libusb_wrap.c:7090: warning: implicit declaration of function ‘SWIG_Python_InstallConstants’
libusb_wrap.c:7093: warning: implicit declaration of function ‘SWIG_Python_SetConstant’
libusb_wrap.c:7093: warning: implicit declaration of function ‘SWIG_From_int’
libusb_wrap.c:7151: warning: implicit declaration of function ‘PyDict_SetItemString’
libusb_wrap.c:7151: warning: implicit declaration of function ‘SWIG_globals’
libusb_wrap.c:7152: warning: implicit declaration of function ‘SWIG_Python_addvarlink’
libusb_wrap.c:7152: error: ‘Swig_var_usb_busses_get’ undeclared (first use in this function)
libusb_wrap.c:7152: error: ‘Swig_var_usb_busses_set’ undeclared (first use in this function)
```

---

### Post by mikeym on 2009-10-25
```
sudo apt-get install python-dev
```

---

### Post by Blackylol on 2009-10-25
same error D:

---

### Post by mikeym on 2009-10-25
OK, got it.

```
sudo apt-get install python2.5-dev
```

---

### Post by Blackylol on 2009-10-25
ok, that worked better, but still shows this 2 errors

/usr/include/usb.h:331: Warning(302): Identifier 'usb_device' redefined (ignored),
/usr/include/usb.h:243: Warning(302): previous definition of 'usb_device'.

---

### Post by mikeym on 2009-10-25
They're just warnings and are normal. 

Since it's not encountered any errors it means that it has compiled. Try running ./usbtool :)

---

### Post by Blackylol on 2009-10-25
weee it worked :P many thanks xD!!!!!!!

Usage: usbtool [options] [command] [command] ...
    examples: 
    usbtool --list
    usbtool --list-commands
    usbtool g25-set-extended-mode
    usbtool f810
    

Options:
  --version        show program's version number and exit
  -h, --help       show this help message and exit
  -v               verbose output
  -d xxxx:yyyy:z   specify device as in 'usbtool --list'
  -l, --list       print list usb devices
  --list-commands  print known commands

---

