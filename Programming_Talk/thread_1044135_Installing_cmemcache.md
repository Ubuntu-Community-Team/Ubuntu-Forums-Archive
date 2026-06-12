---
title: "Installing cmemcache"
date: 2009-01-19
forum: Programming Talk
---

### Post by robtotheb on 2009-01-19
Trying to install cmemcache and getting this error. Any ideas?

```
rob@ubuntu:~/Desktop/cmemcache-0.95$ sudo python setup.py install
running install
running build
running build_py
running build_ext
building '_cmemcache' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/local/include -I/usr/include/python2.5 -c _cmemcache.c -o build/temp.linux-i686-2.5/_cmemcache.o -Wall
_cmemcache.c:7:20: error: Python.h: No such file or directory
_cmemcache.c:8:22: error: memcache.h: No such file or directory
_cmemcache.c:14: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:21: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
_cmemcache.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mcErr’
_cmemcache.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘expParamToExpTime’
_cmemcache.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘errFunc’
_cmemcache.c:114: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_cmemcache.c: In function ‘do_set_servers’:
_cmemcache.c:118: warning: implicit declaration of function ‘PySequence_Check’
_cmemcache.c:118: error: ‘servers’ undeclared (first use in this function)
_cmemcache.c:118: error: (Each undeclared identifier is reported only once
_cmemcache.c:118: error: for each function it appears in.)
_cmemcache.c:120: warning: implicit declaration of function ‘PyErr_BadArgument’
_cmemcache.c:127: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:129: warning: implicit declaration of function ‘mcm_free’
_cmemcache.c:129: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:129: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:130: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:130: error: ‘NULL’ undeclared (first use in this function)
_cmemcache.c:132: warning: implicit declaration of function ‘assert’
_cmemcache.c:132: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:135: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:135: warning: implicit declaration of function ‘mcm_new’
_cmemcache.c:135: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:137: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:139: warning: implicit declaration of function ‘PyErr_NoMemory’
_cmemcache.c:144: warning: implicit declaration of function ‘PySequence_Size’
_cmemcache.c:148: error: ‘PyObject’ undeclared (first use in this function)
_cmemcache.c:148: error: ‘item’ undeclared (first use in this function)
_cmemcache.c:148: warning: implicit declaration of function ‘PySequence_GetItem’
_cmemcache.c:151: error: ‘name’ undeclared (first use in this function)
_cmemcache.c:154: warning: implicit declaration of function ‘PyString_Check’
_cmemcache.c:158: warning: implicit declaration of function ‘PyTuple_Check’
_cmemcache.c:160: warning: implicit declaration of function ‘PyArg_ParseTuple’
_cmemcache.c:164: warning: implicit declaration of function ‘PyString_AsString’
_cmemcache.c:164: warning: initialisation makes pointer from integer without a cast
_cmemcache.c:169: warning: implicit declaration of function ‘strstr’
_cmemcache.c:169: warning: incompatible implicit declaration of built-in function ‘strstr’
_cmemcache.c:171: warning: implicit declaration of function ‘PyErr_Format’
_cmemcache.c:171: error: ‘PyExc_TypeError’ undeclared (first use in this function)
_cmemcache.c:182: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
_cmemcache.c:186: warning: implicit declaration of function ‘mcm_server_add4’
_cmemcache.c:186: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:186: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:189: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
_cmemcache.c:197: warning: implicit declaration of function ‘Py_DECREF’
_cmemcache.c:202: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:202: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:203: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c: At top level:
_cmemcache.c:212: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_cmemcache.c:212: error: expected declaration specifiers or ‘...’ before ‘PyObject’
_cmemcache.c: In function ‘cmemcache_init’:
_cmemcache.c:214: error: ‘PyObject’ undeclared (first use in this function)
_cmemcache.c:214: error: ‘servers’ undeclared (first use in this function)
_cmemcache.c:214: error: ‘NULL’ undeclared (first use in this function)
_cmemcache.c:217: error: ‘args’ undeclared (first use in this function)
_cmemcache.c:220: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:220: warning: implicit declaration of function ‘mcMemNewCtxt’
_cmemcache.c:220: error: ‘free’ undeclared (first use in this function)
_cmemcache.c:220: error: ‘malloc’ undeclared (first use in this function)
_cmemcache.c:220: error: ‘realloc’ undeclared (first use in this function)
_cmemcache.c:221: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:226: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:227: error: ‘CmemcacheObject’ has no member named ‘mcErr’
_cmemcache.c:227: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:231: error: ‘mcErr’ undeclared (first use in this function)
_cmemcache.c:232: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:236: warning: implicit declaration of function ‘mcErrSetupCtxt’
_cmemcache.c:236: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:236: error: ‘errFunc’ undeclared (first use in this function)
_cmemcache.c:246: warning: implicit declaration of function ‘mcm_err_filter_add’
_cmemcache.c:246: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:246: error: ‘MCM_ERR_LVL_INFO’ undeclared (first use in this function)
_cmemcache.c:247: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:247: error: ‘MCM_ERR_LVL_NOTICE’ undeclared (first use in this function)
_cmemcache.c:248: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:248: error: ‘MCM_ERR_LVL_WARN’ undeclared (first use in this function)
_cmemcache.c:253: error: ‘CmemcacheObject’ has no member named ‘debug’
_cmemcache.c:254: error: ‘CmemcacheObject’ has no member named ‘throwException’
_cmemcache.c:255: error: ‘CmemcacheObject’ has no member named ‘exceptionStr’
_cmemcache.c:258: error: too many arguments to function ‘do_set_servers’
_cmemcache.c: At top level:
_cmemcache.c:263: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c: In function ‘cmemcache_dealloc’:
_cmemcache.c:284: error: ‘Py_BEGIN_ALLOW_THREADS’ undeclared (first use in this function)
_cmemcache.c:285: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:287: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:287: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:288: error: ‘CmemcacheObject’ has no member named ‘mc’
_cmemcache.c:290: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:292: warning: implicit declaration of function ‘mcMemFreeCtxt’
_cmemcache.c:292: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:293: error: ‘CmemcacheObject’ has no member named ‘mc_ctxt’
_cmemcache.c:295: error: ‘Py_END_ALLOW_THREADS’ undeclared (first use in this function)
_cmemcache.c: At top level:
_cmemcache.c:307: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:358: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:366: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:374: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:382: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:435: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:443: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:451: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:530: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:633: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:665: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:706: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:714: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:722: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:807: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:827: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_cmemcache.c:844: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmemcache_methods’
_cmemcache.c:980: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmemcache_CmemcacheType’
_cmemcache.c:1022: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cmemcache_module_methods’
_cmemcache.c: In function ‘init_cmemcache’:
_cmemcache.c:1032: error: ‘PyObject’ undeclared (first use in this function)
_cmemcache.c:1032: error: ‘m’ undeclared (first use in this function)
_cmemcache.c:1036: error: ‘cmemcache_CmemcacheType’ undeclared (first use in this function)
_cmemcache.c:1036: error: ‘PyType_GenericNew’ undeclared (first use in this function)
_cmemcache.c:1037: warning: implicit declaration of function ‘PyType_Ready’
_cmemcache.c:1040: warning: implicit declaration of function ‘Py_InitModule3’
_cmemcache.c:1040: error: ‘cmemcache_module_methods’ undeclared (first use in this function)
_cmemcache.c:1043: error: ‘picklemodule’ undeclared (first use in this function)
_cmemcache.c:1043: warning: implicit declaration of function ‘PyImport_ImportModule’
_cmemcache.c:1045: warning: implicit declaration of function ‘PyErr_Clear’
_cmemcache.c:1051: error: ‘loads’ undeclared (first use in this function)
_cmemcache.c:1051: warning: implicit declaration of function ‘PyObject_GetAttrString’
_cmemcache.c:1056: warning: implicit declaration of function ‘Py_INCREF’
_cmemcache.c:1057: warning: implicit declaration of function ‘PyModule_AddObject’
_cmemcache.c:1057: error: expected expression before ‘)’ token
error: command 'gcc' failed with exit status 1

```

---

### Post by Zugzwang on 2009-01-19
Dear OP (original poster),

[LIST]
[*] When trying to fix problems with C/C++ compilation, try to fix the first error first and forget about the rest until the first error is fixed: "error: Python.h: No such file or directory"
[*] You have ran into the problem that some files are missing on your system. This can be seen more or less directly from the error message. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.
[/LIST]

---

### Post by louisr on 2009-02-06
Hey,
I'm in the process of trying to install cmemcache/memcache etc.

```
sudo apt-get install build-essential python-dev memcached libmemcache-dev python-dev
cd /opt/
sudo wget http://gijsbert.org/downloads/cmemcache/cmemcache-0.95.tar.bz2
sudo tar -xvjf cmemcache-0.95.tar.bz2
cd cmemcache-0.95
sudo python setup.py install
memcached -d -m 1024 -l 127.0.0.1 -p 11211
```

That seemed to clear up any compiling errors. However, when I run the "python test.py" file in cmemcache-0.95/  I get FAILED tests.

```
louis@louis-laptop:/opt/cmemcache-0.95$ python test.py
ip 127.0.0.1 port 11211
<module '_cmemcache' from '/usr/lib/python2.5/site-packages/_cmemcache.so'>
testing <StringClient object at 0x8210518> version $Revision: 431 $ 
	from <module 'cmemcache' from '/opt/cmemcache-0.95/cmemcache.pyc'>
[NOTICE@1233907775.681072] mcm_storage_cmd():3339: unable to store value: Operation now in progress: add 
[NOTICE@1233907775.681421] mcm_storage_cmd():3339: unable to store value: Operation now in progress: replace 
[WARN@1233907775.681982] mcm_server_stats():3027: unknown stat variable: pointer_size
F
======================================================================
FAIL: test_memcache (__main__.TestCmemcache)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "test.py", line 254, in test_memcache
    self._test_base(cmemcache, cmemcache.StringClient(self.servers), ok=1)
  File "test.py", line 132, in _test_base
    self.failUnlessEqual(len(stats), 1)
AssertionError: 0 != 1

----------------------------------------------------------------------
Ran 1 test in 0.005s

FAILED (failures=1)

```

---

