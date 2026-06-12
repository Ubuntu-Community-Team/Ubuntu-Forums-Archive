---
title: "gprof memory error"
date: 2011-10-17
forum: Programming Talk
---

### Post by 11jmb on 2011-10-17
I have been getting the following error while trying to profile a project:

```
gprof: out of memory allocating 3738233032 bytes after a total of 13393920 bytes
```

I am not great with gprof, and Google has not been my friend on this one. I know that gprof goes through and allocates memory based on your program's call tree, but 3 GB seems like a lot.

Does anybody have any idea what could be causing such a huge memory requirement?

---

### Post by karlson on 2011-10-17
> **11jmb said:**
> I have been getting the following error while trying to profile a project:

```
gprof: out of memory allocating 3738233032 bytes after a total of 13393920 bytes
```

I am not great with gprof, and Google has not been my friend on this one. I know that gprof goes through and allocates memory based on your program's call tree, but 3 GB seems like a lot.

Does anybody have any idea what could be causing such a huge memory requirement?

Can you post what you did?

Found this from awhile back
[http://www.archivum.info/gnu.gcc.help/2007-08/00081/gprof-out-of-memory-allocating.html](http://www.archivum.info/gnu.gcc.help/2007-08/00081/gprof-out-of-memory-allocating.html)

---

### Post by 11jmb on 2011-10-17
Thanks for the link. I have been going through the manual for a while now, and have not come up with anything yet.

here is what i did:

CC="gcc -pg" CXX="g++ -pg" ./configure
make

then to run the executable:
./a.out
gprof ./a.out

---

