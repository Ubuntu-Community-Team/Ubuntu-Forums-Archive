---
title: "integration of PyQt/PySide issue"
date: 2013-01-23
forum: Programming Talk
---

### Post by itkalenko on 2013-01-23
There is an application (Salome) that includes interpretor Python and Qt and PyQt libs.
 Also there is a module for this application written on Python.
 Specially for this module we need to include additional version of PyQt or PySide that will be distributed with our module.
 It doesn’t really matter whether it will be PyQt (commercial, modified with the help of Vendor ID utility) or PySide.

 The problem is when i try to load any of those libs in Salome, i get the next import error message.
 PyQt: undefined symbol: _ZN10QTableView13doItemsLayoutEv
 PySide: undefined symbol: _ZN9QMetaType15registerTypedefEPKci 

 When importing those modules the same way in test script and running it through interpretor installed in the system everything is working fine.

 Also we tried to recompile the Python 2.6.6 and rebuild PyQt/PySide, but got the same errors.

 Please advise what can cause such problem and how can it be solved.

 P.S: in case with integration of PySide there is another problem: PySide is referring to a lib that has to be located in the system folder
 /usr/lib/i386-linux-gnu/libpyside-python2.7.so, while in our case all paths should be relative. 

 Any help or advice will be appreciated!

---

### Post by itkalenko on 2013-01-25
The problem was due to mismatch of Qt libs versions.
After that we solved issues with incompatibility of libs that are coming along with Salome (sip) and those that were installed
in the system.

But we still have some issues: We cannot pack commercial PyQt with VendorID in the hidden library.
If i get it right, there is a mention of this possibility in the oficial document "VendorID - Signing Python Interpreters and Modules"
(p.3.1 Creating Restricted Extension Modules).

To figure out how Vedor ID works i created foo.py script that contained couple of functions,
1 class and also foomodule.c file (identical to the one in example Reference Guide  3.1 Creating Restricted Extension Modules)

After that we tried to create a library with the help of commands:

>> python ~/VendorID-1.0.0/sib/sib.py -u foo.py

the folder build_foo is created with files  makefile, __main__.c, frozen.c in it

>> make

And we got the next message in the terminal:

gcc -pthread  -Xlinker -export-dynamic __main__.o foo.o frozen.o -o foo -lpthread -ldl  -lutil -lm  -L/usr/local/lib -lpython2.6
/usr/local/lib/libpython2.6.a(dynload_shlib.o): In function
`_PyImport_GetDynLoadFunc':
/home/modeller/Python-2.6.6/Python/dynload_shlib.c:94: undefined reference to `dlsym'
/home/modeller/Python-2.6.6/Python/dynload_shlib.c:130: undefined reference to `dlopen'
/home/modeller/Python-2.6.6/Python/dynload_shlib.c:141: undefined reference to `dlsym'
/home/modeller/Python-2.6.6/Python/dynload_shlib.c:133: undefined reference to `dlerror'
...
/home/modeller/Python-2.6.6/Objects/floatobject.c:972: undefined reference to `pow'
/usr/local/lib/libpython2.6.a(longobject.o): In function
`PyLong_FromString':
/home/modeller/Python-2.6.6/Objects/longobject.c:1610: undefined reference to `log'
/home/modeller/Python-2.6.6/Objects/longobject.c:1610: undefined reference to `log'
collect2: executing lt finished with return code 1
make: *** [foo] Error 1


The issue with PySide still remains: PySide is referring to a lib that has to be located in the system folder /usr/lib/i386-linux-gnu/libpyside-python2.7.so, while in our case all paths should be relative.

---

