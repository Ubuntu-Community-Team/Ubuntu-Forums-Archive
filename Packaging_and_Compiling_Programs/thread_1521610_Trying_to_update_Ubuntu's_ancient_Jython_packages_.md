---
title: "Trying to update Ubuntu's ancient Jython packages - installer requires X11?"
date: 2010-07-01
forum: Packaging and Compiling Programs
---

### Post by victorhooi on 2010-07-01
heya,

I'm trying to use django-jython on a Ubuntu server in Amazon's EC2 cloud.

The only issue is that Ubuntu's version of Jython is terribly outdated - it's version 2.2.1, from around 2007.

[https://bugs.launchpad.net/ubuntu/+source/jython/+bug/390403](https://bugs.launchpad.net/ubuntu/+source/jython/+bug/390403)
[https://bugs.launchpad.net/ubuntu/+source/jython/+bug/574839](https://bugs.launchpad.net/ubuntu/+source/jython/+bug/574839)

Anyhow, I've downloaded the Jython 2.5.1 installer, and run it in headless mode.

I've installed it to /opt/jython

When I try to run /opt/jython/bin/jython, I get:

```
victorhooi@ip-10-195-113-207:/opt/jython/bin$ ./jython
Jul 1, 2010 4:30:37 p.m. org.python.google.common.base.internal.Finalizer getInheritableThreadLocalsField
INFO: Couldn't access Thread.inheritableThreadLocals. Reference finalizer threads will inherit thread local values.
Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.10)
   at org.python.core.PySystemState.initStaticFields(PySystemState.java:865)
   at org.python.core.PySystemState.doInitialize(PySystemState.java:837)
   at org.python.core.PySystemState.initialize(PySystemState.java:755)
   at org.python.core.PySystemState.initialize(PySystemState.java:705)
   at org.python.core.PySystemState.initialize(PySystemState.java:698)
   at org.python.util.jython.run(jython.java:150)
   at org.python.util.jython.main(jython.java:129)
Caused by: java.lang.NullPointerException
   at org.python.core.PyObject._cmpeq_unsafe(PyObject.java:1362)
   at org.python.core.PyObject._eq(PyObject.java:1456)
   at org.python.core.PyObject.equals(PyObject.java:244)
   at java.util.AbstractMap.equals(libgcj.so.10)
   at java.util.HashMap.put(libgcj.so.10)
   at java.util.HashSet.add(libgcj.so.10)
   at org.python.core.PyType.fromClass(PyType.java:1313)
   at org.python.core.PyType.fromClass(PyType.java:1271)
   at org.python.core.PyFrozenSet.<clinit>(PyFrozenSet.java:15)
   at java.lang.Class.initializeClass(libgcj.so.10)
   ...7 more
victorhooi@ip-10-195-113-207:/opt/jython/bin$
```

Has anybody been successful in manually installing Jython, from the console? Or anybody who's providing newer packages of Jython for Ubuntu? I couldn't seem to find any PPAs at all.

Cheers,
Victor

---

### Post by SevenMachines on 2010-07-05
no problem here on lucid using default-jre(openjre)
what versions of ubuntu/java are you using?

---

