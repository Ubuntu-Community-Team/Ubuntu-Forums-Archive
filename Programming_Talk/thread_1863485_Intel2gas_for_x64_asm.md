---
title: "Intel2gas for x64 asm"
date: 2011-10-17
forum: Programming Talk
---

### Post by emiller12345 on 2011-10-17
I've been looking at the program Intel2gas but it hasn't been updated in about 10 years, and is definitely not 64-bit compatible. This is a start to get 64-bit asm to work...

```
--- intel2gas.orig.cc    2011-10-17 20:54:56.163979616 -0400
+++ intel2gas.cc    2011-10-17 20:53:06.142735043 -0400
@@ -545,14 +545,14 @@
     char *reg;
     int   mask;
   } reglist[] = {
-    {"bp",0x40000},{"ebp",0xc0000},
-    {"sp",0x10000},{"esp",0x20000},
-    {"si",0x4000},{"esi",0xc000},
-    {"di",0x1000},{"edi",0x3000},
-    {"dl",0x200},{"dh",0x400},{"dx",0x600},{"edx",0xe00},
-    {"cl",0x040},{"ch",0x080},{"cx",0x0c0},{"ecx",0x1c0},
-    {"bl",0x008},{"bh",0x010},{"bx",0x018},{"ebx",0x038},
-    {"al",0x001},{"ah",0x002},{"ax",0x003},{"eax",0x007},
+    {"bp",0x2000000},{"ebp",0x6000000},{"rbp",0xe000000},
+    {"sp",0x400000},{"esp",0xc00000},{"rsp",0x1c00000},
+    {"si",0x80000},{"esi",0x180000},{"rsi",0x380000},
+    {"di",0x10000},{"edi",0x30000},{"rdi",0x70000},
+    {"dl",0x1000},{"dh",0x2000},{"dx",0x3000},{"edx",0x7000},{"rdx",0xf000},
+    {"cl",0x0100},{"ch",0x0200},{"cx",0x0300},{"ecx",0x0700},{"rcx",0x0f00},
+    {"bl",0x0010},{"bh",0x0020},{"bx",0x0030},{"ebx",0x0070},{"rbx",0x00f0},
+    {"al",0x0001},{"ah",0x0002},{"ax",0x0003},{"eax",0x0007},{"rax",0x000f},
   };
   int const reglist_size = sizeof(reglist)/sizeof(reglist[0]);
   int regs=0,mmregs=0;

```

./i2g/reg.20.list
```
# All 64 bit registers, that force the instruction to be expanded with 'q'
# The r-1 and r-2 are stored so previous 'register width' values in parse
# line can be accessed
@r-2=<r-1>
@r-1=<r>
@r=q
-
rax
rbx
rcx
rdx
rsi
rdi
rsp
rbp
```

link i2g/reg.20.list to g2i/
```

cd ./g2i/
ln -s ../i2g/reg.20.list .

```

---

### Post by emiller12345 on 2011-10-21
Does anyone know about how to add an update to a program like this? It's in the repos...

---

### Post by gsmanners on 2011-10-21
You could email az at debian.org or maybe try ubuntu-devel-discuss at lists.ubuntu.com and see what they think.

---

