---
title: "Lapack import error from scipy in virtualenv"
date: 2013-01-23
forum: Programming Talk
---

### Post by jazzvibes on 2013-01-23
Hi Ubuntu forums,


I have installed numpy and scipy into a virtualenv using pip but I  have import errors in the linalg libraries that prevent me from  continuing to make SimpleCV work. Does anyone know where I can start to try and resolve this issue?


running numpy.test() prints out no big messages like this.

running scipy.test() prints out the following. Importantly, some of the clapack and flapack routines are missing.



 I am using Ubuntu 12.10 64-bit on my laptop, and I prepared for this  installation by using "sudo apt-get build-dep numpy scipy". 


Thanks in advance

Regards,
Jonathan

======================================================================
ERROR:  Failure: ImportError  (/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/clapack.so:  undefined symbol: clapack_sgesv)
 ----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
     addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
    return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/interpolate/__init__.py",  line 154, in <module>
    from rbf import Rbf
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/interpolate/rbf.py", line 49, in <module>
    from scipy import linalg
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
     from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
    from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 15, in <module>
     from scipy.linalg import clapack
ImportError:  /home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/clapack.so:  undefined symbol: clapack_sgesv

======================================================================
 ERROR: Failure: ImportError  (/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/lib/lapack/clapack.so:  undefined symbol: clapack_sgesv)
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
    addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
     return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/lib/lapack/__init__.py",  line 148, in <module>
    import clapack
ImportError:  /home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/lib/lapack/clapack.so:  undefined symbol: clapack_sgesv

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
----------------------------------------------------------------------
Traceback (most recent call last):
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
    addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
     return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
    from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
     from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
    from scipy.linalg import flapack
 ImportError: cannot import name flapack

======================================================================
ERROR: test_common.test_pade_trivial
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/tests/test_common.py",  line 9, in test_pade_trivial
     nump, denomp = pade([1.0], 0)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/common.py", line 371, in pade
    from scipy import linalg
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
     from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
    from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
     from scipy.linalg import flapack
ImportError: cannot import name flapack

======================================================================
ERROR: test_common.test_pade_4term_exp
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/tests/test_common.py",  line 18, in test_pade_4term_exp
     nump, denomp = pade(an, 0)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/common.py", line 371, in pade
    from scipy import linalg
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
     from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
    from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
     from scipy.linalg import flapack
ImportError: cannot import name flapack

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
 ----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
     addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
    return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/optimize/__init__.py",  line 146, in <module>
    from _root import *
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/optimize/_root.py", line 17, in <module>
    import nonlin
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/optimize/nonlin.py",  line 116, in <module>
     from scipy.linalg import norm, solve, inv, qr, svd, lstsq, LinAlgError
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
     from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
    from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
     from scipy.linalg import flapack
ImportError: cannot import name flapack

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
 ----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
     addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
    return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/signal/__init__.py",  line 218, in <module>
    from cont2discrete import *
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/signal/cont2discrete.py",  line 9, in <module>
    from scipy import linalg
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
     from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
    from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
     from scipy.linalg import flapack
ImportError: cannot import name flapack

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
 ----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
     addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
    return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/__init__.py",  line 90, in <module>
    from isolve import *
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/isolve/__init__.py",  line 6, in <module>
    from lgmres import lgmres
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/isolve/lgmres.py",  line 5, in <module>
     from scipy.linalg import get_blas_funcs
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
    from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
     from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
    from scipy.linalg import flapack
 ImportError: cannot import name flapack

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
    addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
     return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/tests/test_base.py",  line 34, in <module>
    from scipy.sparse.linalg import splu
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/__init__.py",  line 90, in <module>
     from isolve import *
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/isolve/__init__.py",  line 6, in <module>
    from lgmres import lgmres
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/sparse/linalg/isolve/lgmres.py",  line 5, in <module>
     from scipy.linalg import get_blas_funcs
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
    from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
     from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
    from scipy.linalg import flapack
 ImportError: cannot import name flapack

======================================================================
ERROR: Failure: ImportError (cannot import name flapack)
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/loader.py", line 390, in loadTestsFromName
    addr.filename, addr.module)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 39, in importFromPath
     return self.importFromDir(dir_path, fqname)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/importer.py", line 86, in importFromDir
    mod = load_module(part_fqname, fh, filename, desc)
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/stats/__init__.py", line 321, in <module>
    from stats import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/stats/stats.py", line 194, in <module>
     import scipy.linalg as linalg
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/__init__.py",  line 133, in <module>
    from basic import *
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/basic.py", line 12, in <module>
     from lapack import get_lapack_funcs
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/lapack.py", line 14, in <module>
    from scipy.linalg import flapack
 ImportError: cannot import name flapack

======================================================================
FAIL: Test generator for parametric tests
----------------------------------------------------------------------
 Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/tests/test_pilutil.py",  line 52, in tst_fromimage
     assert_(img.min() >= imin)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/utils.py", line 34, in assert_
    raise AssertionError(msg)
AssertionError

======================================================================
FAIL: Test generator for parametric tests
----------------------------------------------------------------------
Traceback (most recent call last):
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/tests/test_pilutil.py",  line 52, in tst_fromimage
     assert_(img.min() >= imin)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/utils.py", line 34, in assert_
    raise AssertionError(msg)
AssertionError

======================================================================
FAIL: Test generator for parametric tests
----------------------------------------------------------------------
Traceback (most recent call last):
   File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/misc/tests/test_pilutil.py",  line 52, in tst_fromimage
     assert_(img.min() >= imin)
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/utils.py", line 34, in assert_
    raise AssertionError(msg)
AssertionError

======================================================================
FAIL: test_io.test_imread
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/nose/case.py", line 197, in runTest
     self.test(*self.arg)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/decorators.py",  line 146, in skipper_func
    return f(*args, **kwargs)
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/ndimage/tests/test_io.py",  line 16, in test_imread
     assert_array_equal(img.shape, (300, 420, 3))
  File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/utils.py",  line 707, in assert_array_equal
    verbose=verbose, header='Arrays are not equal')
   File  "/home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/numpy/testing/utils.py",  line 600, in assert_array_compare
    raise AssertionError(msg)
AssertionError: 
Arrays are not equal

(shapes (0,), (3,) mismatch)
 x: array([], dtype=float64)
 y: array([300, 420,   3])

----------------------------------------------------------------------
Ran 2446 tests in 24.397s

FAILED (KNOWNFAIL=7, SKIP=7, errors=10, failures=4)
 Out[2]: <nose.result.TextTestResult run=2446 errors=10 failures=4>

---

### Post by MadCow108 on 2013-01-24
can you show the output of this:
```
ldd /home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/clapack.so
```

my guess is that you have a libatlas-base-dev or libopenblas-base-dev package installed, so it linked against these

in debian/ubuntu these libraries are installed in subfolders and pulled in via the alternatives mechanism setting libblas.so.3 to the right place

either remove all -dev packages besides libblas-dev or export BLAS=/usr/lib/libblas/libblas.so.3 before building

or set LD_LIBRARY_PATH to the right path (e.g. /usr/lib/atlas-base/atlas/ or /usr/lib/openblas-base/) at runtime

---

### Post by jazzvibes on 2013-01-25
```

ldd /home/jonathan/.virtualenvs/py27/local/lib/python2.7/site-packages/scipy/linalg/clapack.so
    linux-vdso.so.1 =>  (0x00007fffbb7ff000)
    liblapack.so.3 => /usr/lib/liblapack.so.3 (0x00007f2a807c5000)
    libatlas.so.3 => /usr/lib/libatlas.so.3 (0x00007f2a7ffa1000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2a7fbe1000)
    libblas.so.3 => /usr/lib/libblas.so.3 (0x00007f2a7f38b000)
    libgfortran.so.3 => /usr/lib/x86_64-linux-gnu/libgfortran.so.3 (0x00007f2a7f077000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f2a7ed7a000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f2a7eb64000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f2a7e947000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f2a816f5000)
    libquadmath.so.0 => /usr/lib/x86_64-linux-gnu/libquadmath.so.0 (0x00007f2a7e710000)

```

so I tried "export BLAS=/usr/lib/libblas.so.3" and "export LD_LIBRARY_PATH=/usr/lib" which didn't work unfortunately.

Specifically which packages would be conflicting ... ?
I don't have  openblas at all 
I have these which i think may be relevant
[B]libblas3
libblas-dev 
libatlas3-base
libatlas-base-dev
libatlas-dev[/B]

Does this help?

---

### Post by MadCow108 on 2013-01-26
have you done a custom install of atlas?
/usr/lib/libatlas.so.3 clapack.so finds does not exist in the package archive
what does /usr/lib/libblas.so.3 link to?

try building without libatlas-base-dev and libatlas-dev installed

---

