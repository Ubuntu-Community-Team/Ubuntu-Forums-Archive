---
title: "Problem compiling pgasync module"
date: 2007-05-17
forum: Programming Talk
---

### Post by aek82 on 2007-05-17
Hello, 

I'm fairly new to developing Python and on the Linux platform in general. My latest problem is getting a PostgreSQL data adapter, [pgasync,]("http://jamwt.com/pgasync/") to install on the python interpreter.

According to the instructions for installation, I'm suppose to type the following to initiate setup.

```
sudo python setup.py install
```

The following errors are given after running that command.

```
running install
running build
running build_py
running build_ext
building 'pgasync.cache' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c pgasync/cache.c -o build/temp.linux-i686-2.5/pgasync/cache.o
pgasync/cache.c:4:20: error: Python.h: No such file or directory
pgasync/cache.c:5:26: error: structmember.h: No such file or directory
In file included from pgasync/cache.c:22:
pgasync/convert.h:5:24: error: netinet/in.h: No such file or directory
pgasync/cache.c:23:20: error: stdlib.h: No such file or directory
pgasync/cache.c:24:20: error: string.h: No such file or directory
pgasync/cache.c:27: error: expected specifier-qualifier-list before ‘PyObject’
pgasync/cache.c:28: error: expected specifier-qualifier-list before ‘PyObject’
pgasync/cache.c:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:30: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:31: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:33: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:37: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:38: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:39: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:43: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:44: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:62: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pgasync/cache.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:72: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:73: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:104: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:145: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:147: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:283: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:284: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:331: error: ‘__pyx_n_append’ undeclared here (not in a function)
pgasync/cache.c:331: warning: excess elements in struct initializer
pgasync/cache.c:331: warning: (near initialization for ‘__pyx_intern_tab[0]’)
pgasync/cache.c:331: warning: excess elements in struct initializer
pgasync/cache.c:331: warning: (near initialization for ‘__pyx_intern_tab[0]’)
pgasync/cache.c:332: error: ‘__pyx_n_realloc’ undeclared here (not in a function)
pgasync/cache.c:332: warning: excess elements in struct initializer
pgasync/cache.c:332: warning: (near initialization for ‘__pyx_intern_tab[1]’)
pgasync/cache.c:332: warning: excess elements in struct initializer
pgasync/cache.c:332: warning: (near initialization for ‘__pyx_intern_tab[1]’)
pgasync/cache.c:333: warning: excess elements in struct initializer
pgasync/cache.c:333: warning: (near initialization for ‘__pyx_intern_tab[2]’)
pgasync/cache.c:333: warning: excess elements in struct initializer
pgasync/cache.c:333: warning: (near initialization for ‘__pyx_intern_tab[2]’)
pgasync/cache.c:336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:346: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:352: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:361: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:368: error: array type has incomplete element type
pgasync/cache.c:369: error: ‘PyCFunction’ undeclared here (not in a function)
pgasync/cache.c:369: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_realloc’
pgasync/cache.c:370: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_add’
pgasync/cache.c:371: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_finish’
pgasync/cache.c:375: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_Cache’
pgasync/cache.c:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_Cache’
pgasync/cache.c:429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_Cache’
pgasync/cache.c:435: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_Cache’
pgasync/cache.c:442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_5cache_Cache’
pgasync/cache.c:491: error: array type has incomplete element type
pgasync/cache.c:497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initcache’
pgasync/cache.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initcache’
pgasync/cache.c: In function ‘__Pyx_InternStrings’:
pgasync/cache.c:528: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:529: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:529: warning: implicit declaration of function ‘PyString_InternFromString’
pgasync/cache.c:529: error: ‘__Pyx_InternTabEntry’ has no member named ‘s’
pgasync/cache.c:529: warning: assignment makes pointer from integer without a cast
pgasync/cache.c:530: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:537:21: error: compile.h: No such file or directory
pgasync/cache.c:538:25: error: frameobject.h: No such file or directory
pgasync/cache.c:539:23: error: traceback.h: No such file or directory
pgasync/cache.c: In function ‘__Pyx_AddTraceback’:
pgasync/cache.c:542: error: ‘PyObject’ undeclared (first use in this function)
pgasync/cache.c:542: error: (Each undeclared identifier is reported only once
pgasync/cache.c:542: error: for each function it appears in.)
pgasync/cache.c:542: error: ‘py_srcfile’ undeclared (first use in this function)
pgasync/cache.c:542: error: invalid operands to binary *
pgasync/cache.c:542: warning: statement with no effect
pgasync/cache.c:543: error: ‘py_funcname’ undeclared (first use in this function)
pgasync/cache.c:543: error: invalid operands to binary *
pgasync/cache.c:543: warning: statement with no effect
pgasync/cache.c:544: error: ‘py_globals’ undeclared (first use in this function)
pgasync/cache.c:544: error: invalid operands to binary *
pgasync/cache.c:544: warning: statement with no effect
pgasync/cache.c:545: error: ‘empty_tuple’ undeclared (first use in this function)
pgasync/cache.c:545: error: invalid operands to binary *
pgasync/cache.c:545: warning: statement with no effect
pgasync/cache.c:546: error: ‘empty_string’ undeclared (first use in this function)
pgasync/cache.c:546: error: invalid operands to binary *
pgasync/cache.c:546: warning: statement with no effect
pgasync/cache.c:547: error: ‘PyCodeObject’ undeclared (first use in this function)
pgasync/cache.c:547: error: ‘py_code’ undeclared (first use in this function)
pgasync/cache.c:547: error: invalid operands to binary *
pgasync/cache.c:547: warning: statement with no effect
pgasync/cache.c:548: error: ‘PyFrameObject’ undeclared (first use in this function)
pgasync/cache.c:548: error: ‘py_frame’ undeclared (first use in this function)
pgasync/cache.c:548: error: invalid operands to binary *
pgasync/cache.c:548: warning: statement with no effect
pgasync/cache.c:550: warning: implicit declaration of function ‘PyString_FromString’
pgasync/cache.c:550: warning: statement with no effect
pgasync/cache.c:552: warning: statement with no effect
pgasync/cache.c:554: warning: implicit declaration of function ‘PyModule_GetDict’
pgasync/cache.c:554: error: ‘__pyx_m’ undeclared (first use in this function)
pgasync/cache.c:554: warning: statement with no effect
pgasync/cache.c:556: warning: implicit declaration of function ‘PyTuple_New’
pgasync/cache.c:556: warning: statement with no effect
pgasync/cache.c:558: warning: statement with no effect
pgasync/cache.c:560: warning: implicit declaration of function ‘PyCode_New’
pgasync/cache.c:575: warning: statement with no effect
pgasync/cache.c:577: warning: implicit declaration of function ‘PyFrame_New’
pgasync/cache.c:578: warning: implicit declaration of function ‘PyThreadState_Get’
pgasync/cache.c:582: warning: statement with no effect
pgasync/cache.c:584: error: request for member ‘f_lineno’ in something not a structure or union
pgasync/cache.c:584: warning: statement with no effect
pgasync/cache.c:585: warning: implicit declaration of function ‘PyTraceBack_Here’
pgasync/cache.c:587: warning: implicit declaration of function ‘Py_XDECREF’
error: command 'gcc' failed with exit status 1
```

Now the README says to set a flag, REBUILD_PYREX, to true in the setup.py file if you encounter problems compiling the 'cache.o', which i did, except this error occurs after attempting installation with the aforementioned install command.

```

running install
running build
running build_py
running build_ext
building 'pgasync.cache' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c pgasync/cache.c -o build/temp.linux-i686-2.5/pgasync/cache.o
pgasync/cache.c:4:20: error: Python.h: No such file or directory
pgasync/cache.c:5:26: error: structmember.h: No such file or directory
In file included from pgasync/cache.c:22:
pgasync/convert.h:5:24: error: netinet/in.h: No such file or directory
pgasync/cache.c:23:20: error: stdlib.h: No such file or directory
pgasync/cache.c:24:20: error: string.h: No such file or directory
pgasync/cache.c:27: error: expected specifier-qualifier-list before ‘PyObject’
pgasync/cache.c:28: error: expected specifier-qualifier-list before ‘PyObject’
pgasync/cache.c:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:30: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:31: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:33: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:37: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:38: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:39: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:43: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:44: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:62: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
pgasync/cache.c:68: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:72: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:73: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:104: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:145: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:147: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:283: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:284: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:331: error: ‘__pyx_n_append’ undeclared here (not in a function)
pgasync/cache.c:331: warning: excess elements in struct initializer
pgasync/cache.c:331: warning: (near initialization for ‘__pyx_intern_tab[0]’)
pgasync/cache.c:331: warning: excess elements in struct initializer
pgasync/cache.c:331: warning: (near initialization for ‘__pyx_intern_tab[0]’)
pgasync/cache.c:332: error: ‘__pyx_n_realloc’ undeclared here (not in a function)
pgasync/cache.c:332: warning: excess elements in struct initializer
pgasync/cache.c:332: warning: (near initialization for ‘__pyx_intern_tab[1]’)
pgasync/cache.c:332: warning: excess elements in struct initializer
pgasync/cache.c:332: warning: (near initialization for ‘__pyx_intern_tab[1]’)
pgasync/cache.c:333: warning: excess elements in struct initializer
pgasync/cache.c:333: warning: (near initialization for ‘__pyx_intern_tab[2]’)
pgasync/cache.c:333: warning: excess elements in struct initializer
pgasync/cache.c:333: warning: (near initialization for ‘__pyx_intern_tab[2]’)
pgasync/cache.c:336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
pgasync/cache.c:346: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:352: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:361: error: expected ‘)’ before ‘*’ token
pgasync/cache.c:368: error: array type has incomplete element type
pgasync/cache.c:369: error: ‘PyCFunction’ undeclared here (not in a function)
pgasync/cache.c:369: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_realloc’
pgasync/cache.c:370: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_add’
pgasync/cache.c:371: error: expected ‘}’ before ‘__pyx_f_5cache_5Cache_finish’
pgasync/cache.c:375: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_number_Cache’
pgasync/cache.c:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_sequence_Cache’
pgasync/cache.c:429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_mapping_Cache’
pgasync/cache.c:435: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_tp_as_buffer_Cache’
pgasync/cache.c:442: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__pyx_type_5cache_Cache’
pgasync/cache.c:491: error: array type has incomplete element type
pgasync/cache.c:497: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initcache’
pgasync/cache.c:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initcache’
pgasync/cache.c: In function ‘__Pyx_InternStrings’:
pgasync/cache.c:528: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:529: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:529: warning: implicit declaration of function ‘PyString_InternFromString’
pgasync/cache.c:529: error: ‘__Pyx_InternTabEntry’ has no member named ‘s’
pgasync/cache.c:529: warning: assignment makes pointer from integer without a cast
pgasync/cache.c:530: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
pgasync/cache.c:537:21: error: compile.h: No such file or directory
pgasync/cache.c:538:25: error: frameobject.h: No such file or directory
pgasync/cache.c:539:23: error: traceback.h: No such file or directory
pgasync/cache.c: In function ‘__Pyx_AddTraceback’:
pgasync/cache.c:542: error: ‘PyObject’ undeclared (first use in this function)
pgasync/cache.c:542: error: (Each undeclared identifier is reported only once
pgasync/cache.c:542: error: for each function it appears in.)
pgasync/cache.c:542: error: ‘py_srcfile’ undeclared (first use in this function)
pgasync/cache.c:542: error: invalid operands to binary *
pgasync/cache.c:542: warning: statement with no effect
pgasync/cache.c:543: error: ‘py_funcname’ undeclared (first use in this function)
pgasync/cache.c:543: error: invalid operands to binary *
pgasync/cache.c:543: warning: statement with no effect
pgasync/cache.c:544: error: ‘py_globals’ undeclared (first use in this function)
pgasync/cache.c:544: error: invalid operands to binary *
pgasync/cache.c:544: warning: statement with no effect
pgasync/cache.c:545: error: ‘empty_tuple’ undeclared (first use in this function)
pgasync/cache.c:545: error: invalid operands to binary *
pgasync/cache.c:545: warning: statement with no effect
pgasync/cache.c:546: error: ‘empty_string’ undeclared (first use in this function)
pgasync/cache.c:546: error: invalid operands to binary *
pgasync/cache.c:546: warning: statement with no effect
pgasync/cache.c:547: error: ‘PyCodeObject’ undeclared (first use in this function)
pgasync/cache.c:547: error: ‘py_code’ undeclared (first use in this function)
pgasync/cache.c:547: error: invalid operands to binary *
pgasync/cache.c:547: warning: statement with no effect
pgasync/cache.c:548: error: ‘PyFrameObject’ undeclared (first use in this function)
pgasync/cache.c:548: error: ‘py_frame’ undeclared (first use in this function)
pgasync/cache.c:548: error: invalid operands to binary *
pgasync/cache.c:548: warning: statement with no effect
pgasync/cache.c:550: warning: implicit declaration of function ‘PyString_FromString’
pgasync/cache.c:550: warning: statement with no effect
pgasync/cache.c:552: warning: statement with no effect
pgasync/cache.c:554: warning: implicit declaration of function ‘PyModule_GetDict’
pgasync/cache.c:554: error: ‘__pyx_m’ undeclared (first use in this function)
pgasync/cache.c:554: warning: statement with no effect
pgasync/cache.c:556: warning: implicit declaration of function ‘PyTuple_New’
pgasync/cache.c:556: warning: statement with no effect
pgasync/cache.c:558: warning: statement with no effect
pgasync/cache.c:560: warning: implicit declaration of function ‘PyCode_New’
pgasync/cache.c:575: warning: statement with no effect
pgasync/cache.c:577: warning: implicit declaration of function ‘PyFrame_New’
pgasync/cache.c:578: warning: implicit declaration of function ‘PyThreadState_Get’
pgasync/cache.c:582: warning: statement with no effect
pgasync/cache.c:584: error: request for member ‘f_lineno’ in something not a structure or union
pgasync/cache.c:584: warning: statement with no effect
pgasync/cache.c:585: warning: implicit declaration of function ‘PyTraceBack_Here’
pgasync/cache.c:587: warning: implicit declaration of function ‘Py_XDECREF’
error: command 'gcc' failed with exit status 1
```

Any help would be appreciated. Thanks.

Alex

---

### Post by WW on 2007-05-17
The first error says you are missing "Python.h"; you need to install the package **python-dev**:
```

sudo apt-get install python-dev

```

---

### Post by aek82 on 2007-05-17
Alright, i installed the python-dev package, but I'm still getting errors. It seems like I'm missing alot of other files.

Here's the updated error list:

```
running install
running build
running build_py
running build_ext
building 'pgasync.cache' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c pgasync/cache.c -o build/temp.linux-i686-2.5/pgasync/cache.o
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from /usr/include/python2.5/Python.h:18,
                 from pgasync/cache.c:3:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from pgasync/cache.c:3:
/usr/include/python2.5/Python.h:32:19: error: stdio.h: No such file or directory
/usr/include/python2.5/Python.h:34:5: error: #error "Python.h requires that stdio.h define NULL."
/usr/include/python2.5/Python.h:37:20: error: string.h: No such file or directory
/usr/include/python2.5/Python.h:39:19: error: errno.h: No such file or directory
/usr/include/python2.5/Python.h:41:20: error: stdlib.h: No such file or directory
/usr/include/python2.5/Python.h:43:20: error: unistd.h: No such file or directory
/usr/include/python2.5/Python.h:55:20: error: assert.h: No such file or directory
In file included from /usr/include/python2.5/Python.h:57,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyport.h:7:20: error: stdint.h: No such file or directory
In file included from /usr/include/python2.5/Python.h:57,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyport.h:73: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Py_uintptr_t&#8217;
/usr/include/python2.5/pyport.h:74: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Py_intptr_t&#8217;
/usr/include/python2.5/pyport.h:97: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Py_ssize_t&#8217;
/usr/include/python2.5/pyport.h:204:76: error: math.h: No such file or directory
/usr/include/python2.5/pyport.h:211:22: error: sys/time.h: No such file or directory
/usr/include/python2.5/pyport.h:212:18: error: time.h: No such file or directory
/usr/include/python2.5/pyport.h:230:24: error: sys/select.h: No such file or directory
/usr/include/python2.5/pyport.h:269:22: error: sys/stat.h: No such file or directory
In file included from /usr/include/python2.5/Python.h:76,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pymem.h:50: warning: parameter names (without types) in function declaration
/usr/include/python2.5/pymem.h:51: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/python2.5/Python.h:78,
                 from pgasync/cache.c:3:
/usr/include/python2.5/object.h:104: error: expected specifier-qualifier-list before &#8216;Py_ssize_t&#8217;
/usr/include/python2.5/object.h:108: error: expected specifier-qualifier-list before &#8216;Py_ssize_t&#8217;
/usr/include/python2.5/object.h:131: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/object.h:131: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;Py_ssize_t&#8217;
/usr/include/python2.5/object.h:131: error: &#8216;Py_ssize_t&#8217; declared as function returning a function
/usr/include/python2.5/object.h:131: warning: function declaration isn&#8217;t a prototype
/usr/include/python2.5/object.h:149: error: &#8216;readbufferproc&#8217; declared as function returning a function
/usr/include/python2.5/object.h:150: error: &#8216;writebufferproc&#8217; declared as function returning a function
/usr/include/python2.5/object.h:151: error: &#8216;segcountproc&#8217; declared as function returning a function
/usr/include/python2.5/object.h:152: error: &#8216;charbufferproc&#8217; declared as function returning a function
/usr/include/python2.5/object.h:215: error: expected specifier-qualifier-list before &#8216;lenfunc&#8217;
/usr/include/python2.5/object.h:229: error: expected specifier-qualifier-list before &#8216;lenfunc&#8217;
/usr/include/python2.5/object.h:244: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
/usr/include/python2.5/object.h:258: warning: &#8216;struct _typeobject&#8217; declared inside parameter list
/usr/include/python2.5/object.h:258: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/include/python2.5/object.h:259: warning: &#8216;struct _typeobject&#8217; declared inside parameter list
/usr/include/python2.5/object.h:262: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/object.h:262: error: field &#8216;ob_size&#8217; declared as a function
/usr/include/python2.5/object.h:264: error: field &#8216;tp_basicsize&#8217; declared as a function
/usr/include/python2.5/object.h:264: error: field &#8216;tp_itemsize&#8217; declared as a function
/usr/include/python2.5/object.h:309: error: field &#8216;tp_weaklistoffset&#8217; declared as a function
/usr/include/python2.5/object.h:324: error: field &#8216;tp_dictoffset&#8217; declared as a function
/usr/include/python2.5/object.h:389: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
In file included from /usr/include/python2.5/Python.h:79,
                 from pgasync/cache.c:3:
/usr/include/python2.5/objimpl.h:97: warning: parameter names (without types) in function declaration
/usr/include/python2.5/objimpl.h:98: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/python2.5/objimpl.h:228: error: &#8216;PyGC_Collect&#8217; declared as function returning a function
/usr/include/python2.5/objimpl.h:249: error: field &#8216;gc_refs&#8217; declared as a function
/usr/include/python2.5/objimpl.h:288: warning: parameter names (without types) in function declaration
In file included from /usr/include/python2.5/Python.h:83,
                 from pgasync/cache.c:3:
/usr/include/python2.5/unicodeobject.h:55:19: error: ctype.h: No such file or directory
/usr/include/python2.5/unicodeobject.h:118:21: error: wchar.h: No such file or directory
In file included from /usr/include/python2.5/Python.h:83,
                 from pgasync/cache.c:3:
/usr/include/python2.5/unicodeobject.h:384: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/unicodeobject.h:385: error: field &#8216;length&#8217; declared as a function
/usr/include/python2.5/unicodeobject.h:447: error: &#8216;PyUnicodeUCS4_GetSize&#8217; declared as function returning a function
/usr/include/python2.5/unicodeobject.h:521: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;wchar_t&#8217;
/usr/include/python2.5/unicodeobject.h:521: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/unicodeobject.h:539: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;wchar_t&#8217;
/usr/include/python2.5/unicodeobject.h:539: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/unicodeobject.h:1102: error: &#8216;PyUnicodeUCS4_Tailmatch&#8217; declared as function returning a function
/usr/include/python2.5/unicodeobject.h:1114: error: &#8216;PyUnicodeUCS4_Find&#8217; declared as function returning a function
/usr/include/python2.5/unicodeobject.h:1123: error: &#8216;PyUnicodeUCS4_Count&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:84,
                 from pgasync/cache.c:3:
/usr/include/python2.5/intobject.h:24: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/intobject.h:38: warning: parameter names (without types) in function declaration
/usr/include/python2.5/intobject.h:41: error: &#8216;PyInt_AsSsize_t&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:86,
                 from pgasync/cache.c:3:
/usr/include/python2.5/longobject.h:25: error: &#8216;_PyLong_AsSsize_t&#8217; declared as function returning a function
/usr/include/python2.5/longobject.h:26: warning: parameter names (without types) in function declaration
/usr/include/python2.5/longobject.h:69: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;_PyLong_NumBits&#8217;
/usr/include/python2.5/longobject.h:85: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/python2.5/longobject.h:108: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/python2.5/Python.h:87,
                 from pgasync/cache.c:3:
/usr/include/python2.5/floatobject.h:15: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:89,
                 from pgasync/cache.c:3:
/usr/include/python2.5/complexobject.h:39: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:92,
                 from pgasync/cache.c:3:
/usr/include/python2.5/stringobject.h:36: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/stringobject.h:36: error: field &#8216;ob_size&#8217; declared as a function
/usr/include/python2.5/stringobject.h:67: error: &#8216;PyString_Size&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:94,
                 from pgasync/cache.c:3:
/usr/include/python2.5/tupleobject.h:25: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/tupleobject.h:25: error: field &#8216;ob_size&#8217; declared as a function
/usr/include/python2.5/tupleobject.h:40: error: &#8216;PyTuple_Size&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:95,
                 from pgasync/cache.c:3:
/usr/include/python2.5/listobject.h:23: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/listobject.h:23: error: field &#8216;ob_size&#8217; declared as a function
/usr/include/python2.5/listobject.h:38: error: field &#8216;allocated&#8217; declared as a function
/usr/include/python2.5/listobject.h:47: error: &#8216;PyList_Size&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:96,
                 from pgasync/cache.c:3:
/usr/include/python2.5/dictobject.h:55: error: field &#8216;me_hash&#8217; declared as a function
/usr/include/python2.5/dictobject.h:71: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/dictobject.h:72: error: field &#8216;ma_fill&#8217; declared as a function
/usr/include/python2.5/dictobject.h:73: error: field &#8216;ma_used&#8217; declared as a function
/usr/include/python2.5/dictobject.h:79: error: field &#8216;ma_mask&#8217; declared as a function
/usr/include/python2.5/dictobject.h:108: error: &#8216;PyDict_Size&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:98,
                 from pgasync/cache.c:3:
/usr/include/python2.5/setobject.h:36: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/setobject.h:38: error: field &#8216;fill&#8217; declared as a function
/usr/include/python2.5/setobject.h:39: error: field &#8216;used&#8217; declared as a function
/usr/include/python2.5/setobject.h:45: error: field &#8216;mask&#8217; declared as a function
/usr/include/python2.5/setobject.h:79: error: &#8216;PySet_Size&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:99,
                 from pgasync/cache.c:3:
/usr/include/python2.5/methodobject.h:82: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:101,
                 from pgasync/cache.c:3:
/usr/include/python2.5/funcobject.h:22: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:102,
                 from pgasync/cache.c:3:
/usr/include/python2.5/classobject.h:13: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/classobject.h:24: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/classobject.h:31: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:103,
                 from pgasync/cache.c:3:
/usr/include/python2.5/fileobject.h:11: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/fileobject.h:12: error: expected specifier-qualifier-list before &#8216;FILE&#8217;
/usr/include/python2.5/fileobject.h:38: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/fileobject.h:40: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/fileobject.h:57: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
/usr/include/python2.5/fileobject.h:58: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;Py_UniversalNewlineFread&#8217;
In file included from /usr/include/python2.5/Python.h:105,
                 from pgasync/cache.c:3:
/usr/include/python2.5/traceback.h:13: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:106,
                 from pgasync/cache.c:3:
/usr/include/python2.5/sliceobject.h:23: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:107,
                 from pgasync/cache.c:3:
/usr/include/python2.5/cellobject.h:10: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:109,
                 from pgasync/cache.c:3:
/usr/include/python2.5/genobject.h:13: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:110,
                 from pgasync/cache.c:3:
/usr/include/python2.5/descrobject.h:46: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/descrobject.h:50: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/descrobject.h:55: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/descrobject.h:60: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/descrobject.h:65: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:111,
                 from pgasync/cache.c:3:
/usr/include/python2.5/weakrefobject.h:16: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/weakrefobject.h:65: error: &#8216;_PyWeakref_GetWeakrefCount&#8217; declared as function returning a function
In file included from /usr/include/python2.5/Python.h:114,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyerrors.h:10: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/pyerrors.h:17: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/pyerrors.h:31: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/pyerrors.h:44: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/pyerrors.h:52: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/pyerrors.h:326: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/python2.5/pyerrors.h:327: error: format string argument not a string type
/usr/include/python2.5/pyerrors.h:328: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/python2.5/Python.h:118,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyarena.h:50: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/python2.5/Python.h:120,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pythonrun.h:34: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:35: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:37: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:38: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:39: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:44: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:54: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:60: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:77: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:142: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
/usr/include/python2.5/pythonrun.h:144: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from /usr/include/python2.5/Python.h:122,
                 from pgasync/cache.c:3:
/usr/include/python2.5/sysmodule.h:12: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from /usr/include/python2.5/Python.h:124,
                 from pgasync/cache.c:3:
/usr/include/python2.5/import.h:33: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/include/python2.5/import.h:33: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;FILE&#8217;
In file included from /usr/include/python2.5/Python.h:126,
                 from pgasync/cache.c:3:
/usr/include/python2.5/abstract.h:421: error: &#8216;PyObject_Size&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:433: error: &#8216;PyObject_Length&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:436: error: &#8216;_PyObject_LengthHint&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:774: error: &#8216;PyNumber_AsSsize_t&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:947: error: &#8216;PySequence_Size&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:956: error: &#8216;PySequence_Length&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:1078: error: &#8216;PySequence_Count&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:1097: error: &#8216;_PySequence_IterSearch&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:1122: error: &#8216;PySequence_Index&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:1161: error: &#8216;PyMapping_Size&#8217; declared as function returning a function
/usr/include/python2.5/abstract.h:1171: error: &#8216;PyMapping_Length&#8217; declared as function returning a function
In file included from /usr/include/python2.5/compile.h:5,
                 from /usr/include/python2.5/Python.h:128,
                 from pgasync/cache.c:3:
/usr/include/python2.5/code.h:11: error: field &#8216;ob_refcnt&#8217; declared as a function
In file included from /usr/include/python2.5/Python.h:131,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pystrtod.h:11: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/include/python2.5/Python.h:151,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyfpe.h:129:20: error: signal.h: No such file or directory
/usr/include/python2.5/pyfpe.h:130:20: error: setjmp.h: No such file or directory
In file included from /usr/include/python2.5/Python.h:151,
                 from pgasync/cache.c:3:
/usr/include/python2.5/pyfpe.h:132: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;PyFPE_jbuf&#8217;
In file included from pgasync/cache.c:4:
/usr/include/python2.5/structmember.h:40: error: field &#8216;offset&#8217; declared as a function
In file included from pgasync/cache.c:8:
pgasync/convert.h:5:24: error: netinet/in.h: No such file or directory
pgasync/cache.c:49: error: field &#8216;ob_refcnt&#8217; declared as a function
pgasync/cache.c: In function &#8216;__pyx_f_5cache_5Cache___new__&#8217;:
pgasync/cache.c:65: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:75: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:75: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:82: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:82: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:86: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:86: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c: In function &#8216;__pyx_f_5cache_5Cache_realloc&#8217;:
pgasync/cache.c:96: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:112: warning: implicit declaration of function &#8216;free&#8217;
pgasync/cache.c:117: warning: implicit declaration of function &#8216;malloc&#8217;
pgasync/cache.c:117: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
pgasync/cache.c:119: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:125: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:125: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:121: warning: label &#8216;__pyx_L1&#8217; defined but not used
pgasync/cache.c: In function &#8216;__pyx_f_5cache_5Cache_add&#8217;:
pgasync/cache.c:151: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:152: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:153: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:154: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:162: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:162: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:175: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:175: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:191: warning: passing argument 1 of &#8216;PyTuple_New&#8217; makes pointer from integer without a cast
pgasync/cache.c:192: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:195: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:195: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:196: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:196: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:197: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:197: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:215: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:215: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:216: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:216: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:217: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:217: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:222: warning: implicit declaration of function &#8216;strncpy&#8217;
pgasync/cache.c:222: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
pgasync/cache.c:230: warning: passing argument 1 of &#8216;PyTuple_New&#8217; makes pointer from integer without a cast
pgasync/cache.c:234: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:234: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:235: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:235: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:236: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:236: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:246: warning: passing argument 1 of &#8216;PyTuple_New&#8217; makes pointer from integer without a cast
pgasync/cache.c:247: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:250: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:250: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:251: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:251: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:252: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:252: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:254: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:257: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:257: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:258: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:258: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:259: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:259: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:263: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:263: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:264: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:264: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:265: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:265: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:266: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:266: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:242: warning: label &#8216;__pyx_L3&#8217; defined but not used
pgasync/cache.c:219: warning: label &#8216;__pyx_L6&#8217; defined but not used
pgasync/cache.c:207: warning: label &#8216;__pyx_L5&#8217; defined but not used
pgasync/cache.c:139: warning: unused variable &#8216;__pyx_v_bitset&#8217;
pgasync/cache.c: In function &#8216;__pyx_f_5cache_5Cache_finish&#8217;:
pgasync/cache.c:277: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:278: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:290: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:291: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:291: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:296: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:296: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:301: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:305: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:308: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:308: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:312: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:312: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:313: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:313: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c: In function &#8216;__pyx_tp_new_5cache_Cache&#8217;:
pgasync/cache.c:324: warning: passing argument 1 of &#8216;t->tp_alloc&#8217; from incompatible pointer type
pgasync/cache.c:326: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:328: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:328: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c: In function &#8216;__pyx_tp_dealloc_5cache_Cache&#8217;:
pgasync/cache.c:335: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:335: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:336: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c: In function &#8216;__pyx_tp_clear_5cache_Cache&#8217;:
pgasync/cache.c:350: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:350: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:351: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c: At top level:
pgasync/cache.c:404: warning: excess elements in struct initializer
pgasync/cache.c:404: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:405: warning: excess elements in struct initializer
pgasync/cache.c:405: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:406: warning: excess elements in struct initializer
pgasync/cache.c:406: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:407: warning: excess elements in struct initializer
pgasync/cache.c:407: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:408: warning: excess elements in struct initializer
pgasync/cache.c:408: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:409: warning: excess elements in struct initializer
pgasync/cache.c:409: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:410: warning: excess elements in struct initializer
pgasync/cache.c:410: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:411: warning: excess elements in struct initializer
pgasync/cache.c:411: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:412: warning: excess elements in struct initializer
pgasync/cache.c:412: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:413: warning: excess elements in struct initializer
pgasync/cache.c:413: warning: (near initialization for &#8216;__pyx_tp_as_sequence_Cache&#8217;)
pgasync/cache.c:417: warning: excess elements in struct initializer
pgasync/cache.c:417: warning: (near initialization for &#8216;__pyx_tp_as_mapping_Cache&#8217;)
pgasync/cache.c:418: warning: excess elements in struct initializer
pgasync/cache.c:418: warning: (near initialization for &#8216;__pyx_tp_as_mapping_Cache&#8217;)
pgasync/cache.c:419: warning: excess elements in struct initializer
pgasync/cache.c:419: warning: (near initialization for &#8216;__pyx_tp_as_mapping_Cache&#8217;)
pgasync/cache.c:430: warning: initialization makes pointer from integer without a cast
pgasync/cache.c:433: warning: initialization makes pointer from integer without a cast
pgasync/cache.c:468: warning: initialization from incompatible pointer type
In file included from pgasync/cache.c:519:
/usr/include/python2.5/frameobject.h:17: error: field &#8216;ob_refcnt&#8217; declared as a function
/usr/include/python2.5/frameobject.h:17: error: field &#8216;ob_size&#8217; declared as a function
pgasync/cache.c: In function &#8216;__Pyx_AddTraceback&#8217;:
pgasync/cache.c:568: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:568: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:569: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:569: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:570: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:570: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:571: error: &#8216;PyObject&#8217; has no member named &#8216;ob_refcnt&#8217;
pgasync/cache.c:571: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:572: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
pgasync/cache.c:573: error: &#8216;PyObject&#8217; has no member named &#8216;ob_type&#8217;
error: command 'gcc' failed with exit status 1

```

I thought that the rest of these errors might be a permissions problem, but i'm running the install command as 'sudo python setup.py install'. So im assuming permissions shouldn't be an issue.

Also, the following errors after regarding missing references to Python.h are founded. There are no files called stdlib.h, assert.h,etc. on my computer. Any ideas where to get these files? I'm guessing the missing references in Python.h and all the other files can be downloaded from another source.

---

### Post by WW on 2007-05-17
I guess you don't have the C compiler installed.  Install the package **build-essential**:
```

sudo apt-get install build-essential

```

---

### Post by aek82 on 2007-05-17
That seemed to fix the last problem. Pretty sure it worked. Still got a gazilion warnings, but as long as it works. 

Here is what I think is the success message.

```
py install
running install
running build
running build_py
running build_ext
building 'pgasync.cache' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c pgasync/cache.c -o build/temp.linux-i686-2.5/pgasync/cache.o
pgasync/cache.c: In function ‘__pyx_f_5cache_5Cache_realloc’:
pgasync/cache.c:121: warning: label ‘__pyx_L1’ defined but not used
pgasync/cache.c: In function ‘__pyx_f_5cache_5Cache_add’:
pgasync/cache.c:242: warning: label ‘__pyx_L3’ defined but not used
pgasync/cache.c:219: warning: label ‘__pyx_L6’ defined but not used
pgasync/cache.c:207: warning: label ‘__pyx_L5’ defined but not used
pgasync/cache.c:139: warning: unused variable ‘__pyx_v_bitset’
pgasync/cache.c: At top level:
pgasync/cache.c:15: warning: ‘__Pyx_UnpackItem’ declared ‘static’ but never defined
pgasync/cache.c:16: warning: ‘__Pyx_EndUnpack’ declared ‘static’ but never defined
pgasync/cache.c:17: warning: ‘__Pyx_PrintItem’ declared ‘static’ but never defined
pgasync/cache.c:18: warning: ‘__Pyx_PrintNewline’ declared ‘static’ but never defined
pgasync/cache.c:19: warning: ‘__Pyx_Raise’ declared ‘static’ but never defined
pgasync/cache.c:20: warning: ‘__Pyx_ReRaise’ declared ‘static’ but never defined
pgasync/cache.c:21: warning: ‘__Pyx_Import’ declared ‘static’ but never defined
pgasync/cache.c:22: warning: ‘__Pyx_GetExcValue’ declared ‘static’ but never defined
pgasync/cache.c:23: warning: ‘__Pyx_ArgTypeTest’ declared ‘static’ but never defined
pgasync/cache.c:24: warning: ‘__Pyx_TypeTest’ declared ‘static’ but never defined
pgasync/cache.c:25: warning: ‘__Pyx_GetStarArgs’ declared ‘static’ but never defined
pgasync/cache.c:26: warning: ‘__Pyx_WriteUnraisable’ declared ‘static’ but never defined
pgasync/cache.c:28: warning: ‘__Pyx_ImportType’ declared ‘static’ but never defined
pgasync/cache.c:29: warning: ‘__Pyx_SetVtable’ declared ‘static’ but never defined
pgasync/cache.c:30: warning: ‘__Pyx_GetVtable’ declared ‘static’ but never defined
pgasync/cache.c:31: warning: ‘__Pyx_CreateClass’ declared ‘static’ but never defined
pgasync/cache.c:33: warning: ‘__Pyx_InitStrings’ declared ‘static’ but never defined
pgasync/cache.c:34: warning: ‘__Pyx_GetName’ declared ‘static’ but never defined
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c pgasync/convert.c -o build/temp.linux-i686-2.5/pgasync/convert.o
gcc -pthread -shared -Wl,-O1 build/temp.linux-i686-2.5/pgasync/cache.o build/temp.linux-i686-2.5/pgasync/convert.o -o build/lib.linux-i686-2.5/pgasync/cache.so
running install_lib
creating /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/errors.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/pgtypes.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/util.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/format.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/net.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/pool.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/cache.so -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/__init__.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/protocol.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/fe.py -> /usr/lib/python2.5/site-packages/pgasync
copying build/lib.linux-i686-2.5/pgasync/registry.py -> /usr/lib/python2.5/site-packages/pgasync
byte-compiling /usr/lib/python2.5/site-packages/pgasync/errors.py to errors.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/pgtypes.py to pgtypes.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/util.py to util.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/format.py to format.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/net.py to net.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/pool.py to pool.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/__init__.py to __init__.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/protocol.py to protocol.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/fe.py to fe.pyc
byte-compiling /usr/lib/python2.5/site-packages/pgasync/registry.py to registry.pyc
running install_egg_info
Writing /usr/lib/python2.5/site-packages/pgasync-2.01.egg-info
```

Thank you for the prompt replys WW. I appreciate all the help.

---

