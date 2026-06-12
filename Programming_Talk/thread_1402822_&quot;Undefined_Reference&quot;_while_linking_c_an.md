---
title: "&quot;Undefined Reference&quot; while linking c and fortran"
date: 2010-02-09
forum: Programming Talk
---

### Post by determined on 2010-02-09
Hi,

I am trying to compile a program with C and Fortran.  I start out by compiling the seperate files individually:

```

gfortran -DM10 -DIO64 -ffixed-line-length-none  -O -c mdx.F
gcc -DM10 -O -DIO64  -I/usr/include/ -c graphx_mdx.c
gfortran -DM10 -DIO64 -ffixed-line-length-none  -O -c rdf_reader_subs.f

```There are a lot of warnings that don't seem important.  Then the snag,

```

gfortran --verbose mdx.o  graphx_mdx.o rdf_reader_subs.o -o mdx  -force_flat_namespace -I/usr/include/ -L/usr/lib -lXm -lXt -lX11 -lm

```results in,

```

mdx.o: In function `create_dsp_':
mdx.F:(.text+0xb109): undefined reference to `init_gx_'
mdx.o: In function `init_dsp_':
mdx.F:(.text+0xb22b): undefined reference to `init_gx_'
mdx.o: In function `MAIN__':
mdx.F:(.text+0xf17d): undefined reference to `version_gx_'
mdx.F:(.text+0xf886): undefined reference to `iargc_'
mdx.F:(.text+0x120c5): undefined reference to  ... [LOTS MORE undef'd ref...]
...
collect2: ld returned 1 exit status
make: *** [mdx] Error 1

```

This seems simple enough.  I don't understand why these references aren't well defined.  Any help would be appreciated.

---

### Post by CaKiwi on 2010-02-09
If init_gx is in one of the C files, my guess is that the C compiler is not adding an underscore to the symbol it is creating in the object file. There is probably an option to get it to do this. Or maybe try adding an underscore manually to the name in the C file.

---

### Post by pbrane on 2010-02-09
Here are a couple of links that may help

[http://www.fnal.gov/docs/UNIX/unix_at_fermilab/htmldoc/rev1997/uatf-107.html]("http://www.fnal.gov/docs/UNIX/unix_at_fermilab/htmldoc/rev1997/uatf-107.html")

[http://astro.berkeley.edu/~wright/f2c.html]("http://astro.berkeley.edu/~wright/f2c.html")

[http://www.yolinux.com/TUTORIALS/LinuxTutorialMixingFortranAndC.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialMixingFortranAndC.html")

And I assume you know that fortran arguments are passed by reference and C args are passed by value. That needs to be taken into account. As well as array indexing and storage. And....

---

