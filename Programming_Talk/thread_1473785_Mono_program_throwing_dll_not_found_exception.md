---
title: "Mono program throwing dll not found exception"
date: 2010-05-05
forum: Programming Talk
---

### Post by lionsnob on 2010-05-05
Hi all -

Trying to migrate our server at work to 10.04.  I installed the Oracle instant client as detailed [here]("http://grouchgeek.blogspot.com/2008/08/oracle-instant-client-ubuntu-revisited.html"), which worked fine in the 9.10 install.  I noticed the DllNotFoundException and followed the instructions at [the Mono web site]("http://www.mono-project.com/DllNotFoundException").  When I ran

```
ldconfig -p |grep libclntsh
```

I got

```
spharrin@orlinux:~$ ldconfig -p |grep libclntsh
	libclntsh.so.11.1 (libc6) => /opt/oracle/client/libclntsh.so.11.1
	libclntsh.so (libc6) => /opt/oracle/client/libclntsh.so

```

so I thought I'd be okay, but I still get the same exception. libclntsh.so is the "dll" that can't be found, by the way.

If this helps, the output of

```
MONO_LOG_LEVEL="debug" MONO_LOG_MASK="dll" mono oratest.exe
```

is

```
Mono-INFO: DllImport attempting to load: 'libclntsh.so'.
Mono-INFO: DllImport loading location: 'libclntsh.so.so'.
Mono-INFO: DllImport error loading library: 'libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libclntsh.so.so'.
Mono-INFO: DllImport error loading library './libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libclntsh.so'.
Mono-INFO: DllImport error loading library 'libaio.so.1: cannot open shared object file: No such file or directory'.

(oratest.exe:1631): Mono-WARNING **: DllImport unable to load library 'libaio.so.1: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport attempting to load: 'libclntsh.so'.
Mono-INFO: DllImport loading location: 'libclntsh.so.so'.
Mono-INFO: DllImport error loading library: 'libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libclntsh.so.so'.
Mono-INFO: DllImport error loading library './libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libclntsh.so'.
Mono-INFO: DllImport error loading library 'libaio.so.1: cannot open shared object file: No such file or directory'.

(oratest.exe:1631): Mono-WARNING **: DllImport unable to load library 'libaio.so.1: cannot open shared object file: No such file or directory'.
DLL: libclntsh.so
Mono-INFO: DllImport attempting to load: 'libclntsh.so'.
Mono-INFO: DllImport loading location: 'libclntsh.so.so'.
Mono-INFO: DllImport error loading library: 'libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libclntsh.so.so'.
Mono-INFO: DllImport error loading library './libclntsh.so.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libclntsh.so'.
Mono-INFO: DllImport error loading library 'libaio.so.1: cannot open shared object file: No such file or directory'.

(oratest.exe:1631): Mono-WARNING **: DllImport unable to load library 'libaio.so.1: cannot open shared object file: No such file or directory'.

```

Can anyone help?  I've been banging my head against this for hours!
Thanks!

---

### Post by lionsnob on 2010-05-05
Solved.

The exception was a tad misleading - the actual culprit was libaio, which I installed via Synaptic and now all is well.  Thanks for reading :)

---

