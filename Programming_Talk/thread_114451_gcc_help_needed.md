---
title: "gcc help needed"
date: 2006-01-08
forum: Programming Talk
---

### Post by Rubbing Alcohol on 2006-01-08
I just loaded breezy on my laptop. Im having some issues installing a few things from source.

I've got all the utilities I need (gcc, make, etc) and I've got the latest kernel headers. The problem comes when I try to make, the gcc version seems to mismatch

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/julien/acerhk-0.5.31 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: c ommand not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: c ommand not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/julien/acerhk-0.5.31/acerhk.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/julien/acerhk-0.5.31/acerhk.o] Error 127
make[1]: *** [_module_/home/julien/acerhk-0.5.31] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [acerhk.ko] Error 2
```

ie the GCC version returned by the kernel comes up as "command not found".

Any help would be appreciated, 

Thanks

julien

---

### Post by lnostdal on 2006-01-08
apt-get install gcc-3.4

..should do the trick

---

### Post by coredump on 2006-01-08
This is peculiar.  The Makefile seems to be invoking 'gcc' as 'gcc-3.4', as if it needs a specific version.  I presume that if you simply invoke 'gcc' from the command line, i.e.

```
gcc -v
```

that it works OK?  And prints a reasonable version number?

If so, then take a look in the Makefile and see if there's a line like this near the top:

```
CC=gcc-3.4
```

and try changing it to:

```
CC=gcc
```

---

### Post by toojays on 2006-01-08
No, gcc-3.4 is correct. The breezy kernel was compiled with gcc-3.4, and so modules must be compiled with this same compiler.

---

### Post by Rubbing Alcohol on 2006-01-08
so manually installing gcc-3.4 seems to have done the trick.  Kinda odd because I was sure it was installed.

Maybe I just can't read...

Thanks, folks

---

