---
title: "[SOLVED] Question about how to use shared library"
date: 2008-02-12
forum: Programming Talk
---

### Post by leileicats on 2008-02-12
Hi, everyone. I meet some problems about how to use the shared libraries of Intel Threading Build Block.

I need use the shared library called libtbb.so. so my command line as follows:
```

**g++  tbb.cxx -o tbb -L../lib -ltbb**

```
After compilation, I get the**tbb** executable file.

However, I key in **$./tbb**, then it shows the eorror:
```
./tbb: error while loading shared libraries: libtbb.so: cannot open shared object file: No such file or directory

```
But the libtbb.so is in the directory **../lib**. Does it mean I need explicitly give the path of shared library when I execute it? Should the path information be included during compilation?

thanks.

---

### Post by lnostdal on 2008-02-12
the runtime linker will only look in certain predefined places/directories for libraries (.so files)

you can however force it to load a specific library by using LD_PRELOAD

```

LD_PRELOAD=../libtdd.so ./tbb

```

---

### Post by PaulFr on 2008-02-12
IMHO, two solution are better than LD_PRELOAD:

1. Add the linker flag **-rpath <path_to_library_directory>**. So in your example, assuming your libraries will be installed in the parent directory ../lib, you would add the flag **-Xlinker -rpath -Xlinker ../lib** to your compilation ```
**[B]g++  tbb.cxx -o tbb -Xlinker -rpath -Xlinker ../lib -L../lib -ltbb**[/B]
```See the manual page for g++ for details about -Xlinker flag.

2. Set the environment variable LD_LIBRARY_PATH to refer to a set of directories which need to be searched. So for your example, you would set```
$ export LD_LIBRARY_PATH=../lib:${LD_LIBRARY_PATH}
```.

In general, to figure out which libraries are picked up (or missing) you can use```
ldd <binary>
```.

---

### Post by leileicats on 2008-02-12
Thank you very much for your replies.

I have another easy solution which also works on me. I just copy the shared library** libtbb.so** into the directory **/usr/lib** .

---

