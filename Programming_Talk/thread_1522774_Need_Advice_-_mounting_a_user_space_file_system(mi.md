---
title: "Need Advice - mounting a user space file system(mimicking one :-) ) as a FileSystem"
date: 2010-07-02
forum: Programming Talk
---

### Post by chethan123 on 2010-07-02
Hi Guys,

I have a piece of C code, which with a chunk of memory(static array) can mimic file operations (It has APIs similar to fopen/fclose etc). So, any code that is compiled with this mimicking FileSystem can use these APIs as a FileSystem for all their needs :)

But I was wondering, if its possible somehow to register these APIs with Linux system/mouning this File system, and hence enabling any client to use this FS by using normal FileSystem calls (without any need of statically linking it with the My_FileSystem).


While searching for a solution, I came across this idea of making my_FileSystem as a Driver!!! => Is it possible to compile my code as a device driver (with the memory chunk in the driver) and mount this File_system @ say "/mnt/MyFs", and divert FileSystem calls like USB drivers do? (If this can be done, can you please explain how its done or point me to somewhere I can read about this).


I don't want to add these as new System calls and recompile the kernel (And making life of ppl wanting to use this difficult).

Thank You :)


PS: This is question is not meant to be only for Ubuntu platform but Linux in general (Embedded systems included)...

---

### Post by soltanis on 2010-07-02
[File System in User Space]("http://fuse.sourceforge.net/").

---

