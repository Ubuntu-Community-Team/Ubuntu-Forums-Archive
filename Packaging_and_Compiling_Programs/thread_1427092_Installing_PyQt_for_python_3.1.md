---
title: "Installing PyQt for python 3.1"
date: 2010-03-11
forum: Packaging and Compiling Programs
---

### Post by eranga1988 on 2010-03-11
Guyz 
I tried to install PyQt4 for Python 3.1 but I couldnt do it. First I had to install sip-4.10. I followed the following commands.

```
senzeh@senzeh-laptop:~/sip-4.10$ python3.1 configure.py
This is SIP 4.10 for Python 3.1.1+ on linux2.
The SIP code generator will be installed in /usr/bin.
The SIP module will be installed in /usr/lib/python3.1/dist-packages.
The SIP header file will be installed in /usr/include/python3.1.
The default directory to install .sip files in is /usr/share/sip.
The platform/compiler configuration is linux-g++.
Creating sipconfig.py...
Creating top level Makefile...
Creating sip code generator Makefile...
Creating sip module Makefile...
senzeh@senzeh-laptop:~/sip-4.10$ 

```Then I typed ```
sudo make
```Then I got lot of errors like:

```

senzeh@senzeh-laptop:~/sip-4.10$ sudo make
.....
.....
.....
siplib.c:9487: error: expected ‘)’ before ‘*’ token
siplib.c:9500: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:9521: error: expected ‘)’ before ‘*’ token
siplib.c:9547: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sipSimpleWrapper_getset’
siplib.c:9562: error: extra brace group at end of initializer
siplib.c:9562: error: (near initialization for ‘sipSimpleWrapper_Type’)
siplib.c:9564: error: extra brace group at end of initializer
siplib.c:9564: error: (near initialization for ‘sipSimpleWrapper_Type’)
siplib.c:9565: error: ‘sipWrapperType_Type’ undeclared here (not in a function)
siplib.c:9565: error: expected ‘}’ before numeric constant
siplib.c: In function ‘sipWrapper_clear’:
siplib.c:9629: error: ‘sipSimpleWrapper’ has no member named ‘flags’
siplib.c:9657: error: ‘sipSimpleWrapper’ has no member named ‘flags’
siplib.c: In function ‘sipWrapper_dealloc’:
siplib.c:9680: error: ‘PyBaseObject_Type’ undeclared (first use in this function)
siplib.c:9680: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:9680: error: expected expression before ‘)’ token
siplib.c: At top level:
siplib.c:9687: error: expected declaration specifiers or ‘...’ before ‘visitproc’
siplib.c: In function ‘sipWrapper_traverse’:
siplib.c:9693: error: ‘visit’ undeclared (first use in this function)
siplib.c:9693: error: too many arguments to function ‘sipSimpleWrapper_traverse’
siplib.c:9708: error: too many arguments to function ‘sip_api_visit_slot’
siplib.c:9726: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:9726: error: expected expression before ‘)’ token
siplib.c: At top level:
siplib.c:9739: error: extra brace group at end of initializer
siplib.c:9739: error: (near initialization for ‘sipWrapper_Type’)
siplib.c:9741: error: extra brace group at end of initializer
siplib.c:9741: error: (near initialization for ‘sipWrapper_Type’)
siplib.c:9742: error: expected ‘}’ before numeric constant
siplib.c: In function ‘addClassSlots’:
siplib.c:9803: error: ‘sipClassTypeDef’ has no member named ‘ctd_readbuffer’
siplib.c:9807: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:9807: error: ‘getreadbufferproc’ undeclared (first use in this function)
siplib.c:9807: error: expected ‘;’ before ‘sipSimpleWrapper_getreadbuffer’
siplib.c:9810: error: ‘sipClassTypeDef’ has no member named ‘ctd_writebuffer’
siplib.c:9814: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:9814: error: ‘getwritebufferproc’ undeclared (first use in this function)
siplib.c:9814: error: expected ‘;’ before ‘sipSimpleWrapper_getwritebuffer’
siplib.c:9817: error: ‘sipClassTypeDef’ has no member named ‘ctd_segcount’
siplib.c:9821: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:9821: error: ‘getsegcountproc’ undeclared (first use in this function)
siplib.c:9821: error: expected ‘;’ before ‘sipSimpleWrapper_getsegcount’
siplib.c:9824: error: ‘sipClassTypeDef’ has no member named ‘ctd_charbuffer’
siplib.c:9828: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c:9828: error: ‘getcharbufferproc’ undeclared (first use in this function)
siplib.c:9828: error: expected ‘;’ before ‘sipSimpleWrapper_getcharbuffer’
siplib.c:9834: error: ‘sipWrapperType’ has no member named ‘super’
siplib.c: At top level:
siplib.c:9841: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘forgetObject’:
siplib.c:10158: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:10158: error: expected expression before ‘)’ token
siplib.c:10175: error: ‘sipClassTypeDef’ has no member named ‘ctd_dealloc’
siplib.c:10176: error: ‘sipClassTypeDef’ has no member named ‘ctd_dealloc’
siplib.c: In function ‘sip_api_resolve_typedef’:
siplib.c:10196: error: ‘sipExportedModuleDef’ has no member named ‘em_nrtypedefs’
siplib.c:10200: error: ‘sipExportedModuleDef’ has no member named ‘em_typedefs’
siplib.c:10201: error: ‘sipExportedModuleDef’ has no member named ‘em_nrtypedefs’
siplib.c: At top level:
siplib.c:10226: error: expected declaration specifiers or ‘...’ before ‘PyObject’
siplib.c: In function ‘addPyObjectToList’:
siplib.c:10233: error: ‘sipPyObject’ has no member named ‘object’
siplib.c:10233: error: ‘object’ undeclared (first use in this function)
siplib.c:10234: error: ‘sipPyObject’ has no member named ‘next’
siplib.c: At top level:
siplib.c:10286: error: expected declaration specifiers or ‘...’ before ‘visitproc’
siplib.c: In function ‘sip_api_visit_slot’:
siplib.c:10289: error: ‘sipSlot’ has no member named ‘weakSlot’
siplib.c:10289: error: ‘Py_True’ undeclared (first use in this function)
siplib.c:10289: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c:10289: error: ‘Py_None’ undeclared (first use in this function)
siplib.c:10290: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c: In function ‘sip_api_clear_any_slot_reference’:
siplib.c:10302: error: ‘sipSlot’ has no member named ‘weakSlot’
siplib.c:10302: error: ‘Py_True’ undeclared (first use in this function)
siplib.c:10304: error: ‘PyObject’ undeclared (first use in this function)
siplib.c:10304: error: ‘xref’ undeclared (first use in this function)
siplib.c:10304: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c:10310: error: ‘Py_None’ undeclared (first use in this function)
siplib.c:10311: error: ‘sipSlot’ has no member named ‘pyobj’
siplib.c: At top level:
siplib.c:10322: error: expected ‘)’ before ‘*’ token
siplib.c:10347: error: expected ‘)’ before ‘*’ token
siplib.c:10372: error: expected ‘)’ before ‘*’ token
siplib.c:10398: error: expected ‘)’ before ‘*’ token
siplib.c:10408: error: expected ‘)’ before ‘*’ token
siplib.c:10434: error: expected ‘)’ before ‘*’ token
siplib.c:10444: error: expected ‘)’ before ‘*’ token
siplib.c:10470: error: expected ‘)’ before ‘*’ token
siplib.c:10479: error: expected ‘)’ before ‘*’ token
siplib.c:10511: error: expected ‘)’ before ‘*’ token
siplib.c:10539: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10550: error: expected ‘)’ before ‘*’ token
siplib.c:10578: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10589: error: expected ‘)’ before ‘*’ token
siplib.c:10617: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10627: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10651: error: expected ‘)’ before ‘*’ token
siplib.c:10674: error: expected ‘)’ before ‘*’ token
siplib.c:10699: error: expected ‘)’ before ‘*’ token
siplib.c:10933: error: expected ‘)’ before ‘*’ token
siplib.c:10944: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘raiseNoWChar’:
siplib.c:10957: error: ‘PyExc_SystemError’ undeclared (first use in this function)
siplib.c: At top level:
siplib.c:10966: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make[1]: *** [siplib.o] Error 1
make[1]: Leaving directory `/home/senzeh/sip-4.10/siplib'
make: *** [all] Error 2
senzeh@senzeh-laptop:~/sip-4.10$ 

```
So please help me to install sip and PyQt4 for ***Python 3.1***

---

### Post by SevenMachines on 2010-03-11
you'll need the python headers to compile sip, 
try,
$sudo apt-get install python-dev

although if you can use python-sip from the repositories then i'd try that first

---

### Post by eranga1988 on 2010-03-12
> **SevenMachines said:**
> you'll need the python headers to compile sip, 
try,
$sudo apt-get install python-dev

although if you can use python-sip from the repositories then i'd try that first

Thank you very much. installing python3.1-dev i could solve it.
Can't use repositories as the sip for python3.1 is not included.
thanx again.;)

---

