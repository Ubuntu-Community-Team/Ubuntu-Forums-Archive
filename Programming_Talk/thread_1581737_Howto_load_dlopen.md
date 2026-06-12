---
title: "Howto load dlopen"
date: 2010-09-25
forum: Programming Talk
---

### Post by WitchCraft on 2010-09-25
Question: I want to load a shared library from within an attached process in gdb.

example:
```

gdb
attach <pid>
call dlopen("/path/to/my/dll/libxy.so", 2)
detach

```

It works fine when the application has been linked with -ldl.
that is to say when the linker added libdl.so in the address space...
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00dff000)

My question now:
How can I load libdl.so when the linker has not loaded it ?

---

### Post by WitchCraft on 2010-10-02
bump.

---

### Post by WitchCraft on 2010-10-03
bump.

---

### Post by johnl on 2010-10-03
You can use the LD_PRELOAD environmental variable to cause the loader to load any shared object into the process.  To do it with GDB, you use the "set environment" command before running the executable.  This might even accomplish what you want to do without using GDB.

```

There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
(gdb) **set environment LD_PRELOAD /usr/lib/libdl.so**
(gdb) **file ./mem**
Reading symbols from /home/ledbettj/Projects/mem/mem...done.
(gdb) **break main**
Breakpoint 1 at 0x4007d3: file mem_main.c, line 9.
(gdb) **run**
Starting program: /home/ledbettj/Projects/mem/mem 

Breakpoint 1, main (argc=1, argv=0x7fffffffe328) at mem_main.c:9
9	    if (mempool_init(&pool, 4096, 4096)) {
(gdb) **shared**
Symbols already loaded for /lib64/ld-linux-x86-64.so.2
Symbols already loaded for /usr/lib/libdl.so
Symbols already loaded for /lib/libc.so.6
(gdb) **call dlopen("/path/to/foo.so", 2)**
$1 = 0

```

---

