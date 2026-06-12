---
title: "Shared Library Loading problem"
date: 2007-07-27
forum: Programming Talk
---

### Post by kogut on 2007-07-27
I have some 3rd-party (don't have the source code) shared libraries that do not follow the shared library naming convention.  (They do not start with "lib")

This hasn't been a problem before yesterday, but suddenly neither ldconfig nor ld.so are recognizing these files as shared libraries.  Here is a sample of running ldd on a library which depends on these mis-named libraries:

        libmx.so => /home/kogut/CODE/lib/libmx.so (0xb7527000)
        libsfLMfns.so => /home/kogut/CODE/lib/libsfLMfns.so (0xb7525000)
        libut.so => /home/kogut/CODE/lib/libut.so (0xb745b000)
        sfLMcall.so => not found
        sfLMfns.so => not found
        sfMatcall.so => not found
        lapack.so => not found
        libstdc++-libc6.1-2.so.3 => /home/kogut/CODElib/libstdc++-libc6.1-2.so.3 (0xb7415000)
        atlas_PIII.so => not found
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb73fe000)
        libsaphiracompat.so => /home/kogut/CODE/libsaphiracompat.so (0xb73a7000)


As you can see any library not starting with "lib" is not found.  This is not an LD_LIBRARY_PATH issue, as I've used LD_LIBRARY_PATH as well as ld.so.conf with ldconfig to properly point to the library locations (the mis-named libraries are in the same directory as all the others that are found)

Are there any ideas on what's going on, and why this should suddenly happen?

Thanks,
Greg

---

### Post by Mr. C. on 2007-07-29
A library (static or shared) can be named anything; even the .so is by convention.

Obvious question, but do the files exist and if so, what are their permissions as well as the directories leading to them?

MrC

---

### Post by the_unforgiven on 2007-07-29
There is one more artifact of shared libraries which is important - especially, for ELF binaries; it's the internal library name - commonly known as ELF SO_NAME (or SONAME? :confused:).
Is that correct in your case?

EDIT:
The following paper is an excellent read on DSOs:
[http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf)

---

### Post by kogut on 2007-07-30
The libraries exist, and the permissions are permissive.

In fact ldd has no problem with them, and correctly returns all their dependencies.

Greg




> **Mr. C. said:**
> A library (static or shared) can be named anything; even the .so is by convention.

Obvious question, but do the files exist and if so, what are their permissions as well as the directories leading to them?

MrC

---

### Post by kogut on 2007-07-30
...and file gives the correct type:


```
>file sfLMcall.so 
sfLMcall.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped

```

> **kogut said:**
> The libraries exist, and the permissions are permissive.

In fact ldd has no problem with them, and correctly returns all their dependencies.

Greg

---

### Post by ankey4u on 2008-03-10
Hi all, pls help me out

when i executed ldd a.out

output says:

libclntsh.so.10.1 => /lib/libclntsh.so.8.0

in /lib folder there are two links
libclntsh.so.8.0->libclntsh.so.10.1
libclntsh.so.10.1->/usr/oracle8/product/817/lib/libclntsh.so.10.1

Can anyone clearify why it is picking up the library from /lib/libclntsh.so.8.0 while there is a link by the name libclntsh.so.10.1???

Thanks
ankey4u

---

### Post by Mr. C. on 2008-03-10
Are there any other libclntsh* files in /lib ?
Has there been updated software that includes this shared library since the a.out was built ?

The numbers at the end of the libraries indicate interface versions; this allows developers to change the library conventions without affecting existing programs, which use the older versions.

It appears the a.out was linked to include the recent libclntsh.so.10.1 version, but the library that it links to is not in LD_PATH or LD_LIBRARY_PATH.  The sym links in /lib should reference files in /lib.  I'm not certain what happens when they do not, but perhaps you are seeing the result.

Try setting LD_PATH and/or LD_LIBRARY_PATH and doing your ldd and/or recompiling.

---

### Post by ankey4u on 2008-03-10
Thanks for the immediate reply Mr.C

On my system LD_LIBRARY_PATH = DEFAULT:/lib
and there was no other libclntsh file or link in that /lib directory other then libclntsh.so.8.0 and libclntsh.so.10.1.

I am not sure about any updated software
Well yes it's kind of confusing for me too.

Mr. C. can you tell me that is there any way to find out the soname of a library on a Tru64 unix machine.

One more thing i would like to know that left hand side of ldd output shows the true/soname of the library required by the executable,
so like is there any way someone had changed the soname of libclntsh.so.8.0 to libclntsh.so.10.1 so that now at the loading time a.out is searching for libclntsh.so.8.0???

Thanks
ankey4u

---

### Post by Mr. C. on 2008-03-11
The rules for how shared libraries are specified, found, linked, and loaded are a little to complex too describe here in brief.

Since you are using third party libraries, you should learn more about the process:

```
man ldconfig
man ld.so
```

I know near nothing about tru64; typically programs used to determine executable program sections and libraries are:

```
ldd
nm
objdump
dump

```

The LHS of ldd shows the name of the shared library that was linked into the executable at link time.   I suppose it is a possibility that "someone" could have changed the library (or link).  Without further investigation, all we can say now is that the binary requires a shared library (version) which isn't present in the library path.

To avoid security risks, the shared library loader will only look in designated locations (otherwise, consider how user's could run-time replace system libraries with those in their own directories).

Try running your app after setting:

```
LD_LIBRARY_PATH = $LD_LIBRARY_PATH:/usr/oracle8/product/817/lib
export LD_LIBRARY_PATH
```

Also, you mentioned your app was an "a.out".  Is that the executable format, or just the filename ?  See the various *_AOUT_* environment variables in man ld.so as well.

**LD_DEBUG** may be a useful environment variable as well.

---

