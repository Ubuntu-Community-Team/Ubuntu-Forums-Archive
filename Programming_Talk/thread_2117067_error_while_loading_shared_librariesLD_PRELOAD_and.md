---
title: "error while loading shared libraries:LD_PRELOAD and rpath method"
date: 2013-02-17
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-17
Hello,
I am getting a **./exe: error while loading shared libraries: libfoo.so:** error, when I try using the LD_PRELOAD and rpath method, but works using the LD_LIBRARY_PATH. This is what I have done.

_steps_
[b]1. Created 2 files called main.c and lib.c
2. gcc -c -fPIC lib.c
3. gcc -shared -o libfoo.so lib.o
4. gcc -o exe main.c -lfoo -L./
5. LD_PRELOAD=$PWD/libfoo.so ./exe
Also tried using export LD_PRELOAD=$PWD/libfoo.so and then ./exe
[/b]

_output_
**./exe: error while loading shared libraries: libfoo.so: cannot open shared object file: No such file or directory**

_output when done using export LD_LIBRARY_PATH=$PWD:$LD_LIBRARY_PATH and ./exe_
**a == [1], b == [2]**


I'm also not able to do it using rpath, please advise.

Thanks.

---

### Post by spjackson on 2013-02-17
> **IAMTubby said:**
> 
I'm also not able to do it using rpath, please advise.

I don't know about LD_PRELOAD, I've never had a need for it. But rpath works like this:
```

$ gcc -o exe main.c -lfoo -L./ -Xlinker -rpath=$PWD
$ ./exe

```
Doesn't that work for you?

---

### Post by IAMTubby on 2013-02-23
> **spjackson said:**
> 
Doesn't that work for you?
spjackson, sorry for the late reply. I was travelling. Shall reply to your question shortly. Doing some background work before I reply.
Thanks.

---

