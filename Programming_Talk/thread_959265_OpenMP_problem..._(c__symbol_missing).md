---
title: "OpenMP problem... (c_ symbol missing)"
date: 2008-10-26
forum: Programming Talk
---

### Post by koda on 2008-10-26
Hello!
I'm running ubuntu amd64on an intel xeon machine and i'v installed gcc-snapshot to take advantage of some OpenMP optimizations: in fact i have speed up a numerical fortran program with it!

however when i try to link a library containg some openmp code to an executable, it fails with this error:

```
gfortran-4.3 -pthread -fopenmp -w -pg  -m64 -O2 -march=native -pipe -fPIC -mfpmath=sse  -Wl,-O1  -o bin/sol_micromag.bin source/sol_micromag.for lib/sol_mumag.a lib/sol_micromag.a lib/sol_pint.a lib/matrices.a lib/slap.a lib/sally2sparse.a lib/sparse_sub.a  lib/sparse/lib/sparse.a lib/work.a
lib/sol_pint.a(calc_intmudua.o): In function `calc_intmudua_.omp_fn.0':
calc_intmudua.for:(.text+0x23b): undefined reference to `c_'
collect2: ld returned 1 exit status
make: *** [sol_micromag] Error 1
```

obviously the files compiled and linked successfully without the openmp directives...
i'm really clueless as i cannot find any reference to any "c_" symbol, not even on the internet!

can you help me?
Koda

edit:
you can read the binary main file here: [http://paste.org/index.php?id=4127](http://paste.org/index.php?id=4127)
and the nasty procedure here: [http://paste.org/index.php?id=4126](http://paste.org/index.php?id=4126)

---

