---
title: "Problem installing pysparse"
date: 2010-01-14
forum: Programming Talk
---

### Post by C++buntu on 2010-01-14
Hi everyone, 

I'm trying to install FiPy under my Ubuntu 9.04 box. First, I need to install the pysparse v1.1 version, I obtain the following error:

```

steeve@laptop:~/pysparse-1.1$ sudo python setup.py install
[sudo] password for steeve: 
running install
running build
running build_py
creating build
creating build/lib.linux-i686-2.6
creating build/lib.linux-i686-2.6/pysparse
copying Lib/__version__.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/spmatrix_util.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/__init__.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/sparseMatrix.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/directSolver.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/pysparseMatrix.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/pysparseUmfpack.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/itsolvers_util.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/poisson_vec.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/pysparseSuperLU.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/poisson.py -> build/lib.linux-i686-2.6/pysparse
copying Lib/sparray.py -> build/lib.linux-i686-2.6/pysparse
running build_ext
building 'pysparse.spmatrix' extension
creating build/temp.linux-i686-2.6
creating build/temp.linux-i686-2.6/Src
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -DLENFUNC_OK=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/spmatrixmodule.c -o build/temp.linux-i686-2.6/Src/spmatrixmodule.o
In file included from Src/spmatrixmodule.c:23:
Src/mmio_patched.c: In function ‘mm_read_unsymmetric_sparse’:
Src/mmio_patched.c:77: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
Src/spmatrixmodule.c: At top level:
Src/ll_mat.c:887: warning: ‘clear_submatrix’ defined but not used
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.6/Src/spmatrixmodule.o -o build/lib.linux-i686-2.6/pysparse/spmatrix.so
building 'pysparse.itsolvers' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/itsolversmodule.c -o build/temp.linux-i686-2.6/Src/itsolversmodule.o
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/pcg.c -o build/temp.linux-i686-2.6/Src/pcg.o
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/gmres.c -o build/temp.linux-i686-2.6/Src/gmres.o
Src/gmres.c: In function ‘Itsolvers_gmres_kernel’:
Src/gmres.c:89: warning: ‘resid0’ may be used uninitialized in this function
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/minres.c -o build/temp.linux-i686-2.6/Src/minres.o
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/qmrs.c -o build/temp.linux-i686-2.6/Src/qmrs.o
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/bicgstab.c -o build/temp.linux-i686-2.6/Src/bicgstab.o
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DNUMPY=1 -IInclude -I/usr/lib/python2.6/dist-packages/numpy/core/include -I/usr/include/python2.6 -c Src/cgs.c -o build/temp.linux-i686-2.6/Src/cgs.o
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.6/Src/itsolversmodule.o build/temp.linux-i686-2.6/Src/pcg.o build/temp.linux-i686-2.6/Src/gmres.o build/temp.linux-i686-2.6/Src/minres.o build/temp.linux-i686-2.6/Src/qmrs.o build/temp.linux-i686-2.6/Src/bicgstab.o build/temp.linux-i686-2.6/Src/cgs.o -llapack -lblas -lg2c -o build/lib.linux-i686-2.6/pysparse/itsolvers.so
/usr/bin/ld: cannot find -lg2c
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1

```

I've checked and i've installed the libg2c...so what's the problem with pysparse?

Any ideas?

Thanks,

C++buntu

---

### Post by TheStatsMan on 2010-01-14
I think you should be using lgfortran rather than lg2c. You have to modify setup.py to give the location of blas, lapack (and atlas if you are using it, you should be using some kind of optimised blas).

For example in my setup I had

library_dirs_list= ['/usr/lib/atlas']
libraries_list = ['lapack', 'blas', 'gfortran']

---

