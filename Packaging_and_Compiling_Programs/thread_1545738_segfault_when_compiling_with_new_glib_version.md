---
title: "segfault when compiling with new glib version"
date: 2010-08-04
forum: Packaging and Compiling Programs
---

### Post by clebersantz on 2010-08-04
Hi, 

   I'm trying compile a code maked for glib2.4 using ubuntu 10.04(glib2.11) all compilation seems fine (configure, make, make install), but when a run the program i get "segmentation fault":

```
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff482a10d in freeVSA_CONFIG (pp_config=0x7fffffffdfd8)
    at vsclam.c:1277
1277	            if ((*pp_config)->pInitParams->pInitParam[i].tType == VS_TYPE_CHAR &&
(gdb) bt full
#0  0x00007ffff482a10d in freeVSA_CONFIG (pp_config=0x7fffffffdfd8)
    at vsclam.c:1277
        i = 2998
#1  0x00007ffff482a2a2 in VsaEnd (pp_init=0x7fffffffdfd0, 
    pp_config=0x7fffffffdfd8) at vsclam.c:1015
        rc = <value optimized out>
#2  0x0000000000424144 in VsiEnd ()
No symbol table info available.
#3  0x0000000000415bc1 in nlsui_main ()
No symbol table info available.
#4  0x0000000000416769 in main ()
No symbol table info available.
```

There any parameter that must be added in compilation, any change in code ?

PS.: i'm a noob ;)

Best regards,
Cleber Santz.

---

### Post by SevenMachines on 2010-08-06
you'll probably want this moved to '[Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")' ubuntu forum, and post some code for the c++ whizzes over there :)

---

