---
title: "Scipy missing curve_fit"
date: 2010-07-21
forum: Programming Talk
---

### Post by madtowneast on 2010-07-21
Hi all,

I am not sure whether to post this in the repository subforum or here, but since I found more scipy threads here, I put it here...

I installed numpy and scipy from the repositories and it all worked handy dandy, until I tried to run by data analysis program (written originally in Enthought numpy/scipy on Mac OS X). I use the curve_fit routine build into the scipy.optimize (included in minpack.py) package to fit a couple curves. When I try to import the curve_fit it says it does not exist. I checked the minpack.py and it does not exist there either. 


I already contacted the scipy user list, but they tell me that it should be included in the repository version of it. Another hint I was given that I should add following file ~/.local/lib/python2.6/site-packages/install.pth where cat ~/.local/lib/python2.6/site-packages/install.pth gives /usr/local/lib/python2.6/dist-packages. Ironically, I seem to be missing the whole /usr/local/lib folder.

I already tried to manually build numpy/scipy with the same result.

My system is a home build AMD 5200+ system with Alternate Ubuntu 10.04 installed.

Thanks for any help.

Cheers

---

### Post by madtowneast on 2010-07-22
Sorry for the bump, but I just installed numpy and scipy from source. curve_fit is still missing. I  ran numpy.test() and scipy.test(). numpy.test ran fine, but scopy.test gave me a couple errors... here is the output:

Running unit tests for scipy
NumPy version 1.4.1
NumPy is installed in /usr/local/lib/python2.6/dist-packages/numpy
SciPy version 0.7.2
SciPy is installed in /usr/local/lib/python2.6/dist-packages/scipy
Python version 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) [GCC 4.4.3]
nose version 0.11.4
............................................................................................................................................................................................................................./usr/local/lib/python2.6/dist-packages/scipy/interpolate/fitpack2.py:498: UserWarning: 
The coefficients of the spline returned have been computed as the
minimal norm least-squares solution of a (numerically) rank deficient
system (deficiency=7). If deficiency is large, the results may be
inaccurate. Deficiency may strongly depend on the value of eps.
  warnings.warn(message)
...../usr/local/lib/python2.6/dist-packages/scipy/interpolate/fitpack2.py:439: UserWarning: 
The required storage space exceeds the available storage space: nxest
or nyest too small, or s too small.
The weighted least-squares spline corresponds to the current set of
knots.
  warnings.warn(message)
...........................................K..K..................................................................................................................................../usr/local/lib/python2.6/dist-packages/scipy/io/matlab/tests/test_mio.py:438: FutureWarning: Using oned_as default value ('column') This will change to 'row' in future versions
  mfw = MatFile5Writer(StringIO())
......../usr/local/lib/python2.6/dist-packages/scipy/io/matlab/mio.py:84: FutureWarning: Using struct_as_record default value (False) This will change to True in future versions
  return MatFile5Reader(byte_stream, **kwargs)
...............................Warning: 1000000 bytes requested, 20 bytes read.
./usr/local/lib/python2.6/dist-packages/numpy/lib/utils.py:140: DeprecationWarning: `write_array` is deprecated!


This function is replaced by numpy.savetxt which allows the same functionality
through a different syntax.

  warnings.warn(depdoc, DeprecationWarning)
/usr/local/lib/python2.6/dist-packages/numpy/lib/utils.py:140: DeprecationWarning: `read_array` is deprecated!

The functionality of read_array is in numpy.loadtxt which allows the same
functionality using different syntax.

  warnings.warn(depdoc, DeprecationWarning)
......................./usr/local/lib/python2.6/dist-packages/numpy/lib/utils.py:140: DeprecationWarning: `npfile` is deprecated!

You can achieve the same effect as using npfile, using ndarray.tofile
and numpy.fromfile.

Even better you can use memory-mapped arrays and data-types to map out a
file format for direct manipulation in NumPy.

  warnings.warn(depdoc, DeprecationWarning)
..........................................F..............................................................................................................SSSSSS......SSSSSS......SSSS....ATLAS version 3.6.0 built by root on Thu Jun  3 21:13:07 UTC 2004:
   UNAME    : Linux ravel 2.6.5 #3 SMP Tue Apr 13 13:41:54 UTC 2004 x86_64 GNU/Linux
   INSTFLG  : 
   MMDEF    : /home/camm/atlas3-3.6.0/CONFIG/ARCHS/HAMMER64SSE2/gcc/gemm
   ARCHDEF  : /home/camm/atlas3-3.6.0/CONFIG/ARCHS/HAMMER64SSE2/gcc/misc
   F2CDEFS  : -DAdd__ -DStringSunStyle
   CACHEEDGE: 720896
   F77      : /home/camm/usr/bin/g77, version GNU Fortran (GCC) 3.3.3 (Debian 20040422)
   F77FLAGS : -fomit-frame-pointer -O -m64
   CC       : /usr/bin/gcc, version gcc (GCC) 3.3.3 (Debian 20040422)
   CC FLAGS : -fomit-frame-pointer -O -mfpmath=387 -m64
   MCC      : /usr/bin/gcc, version gcc (GCC) 3.3.3 (Debian 20040422)
   MCCFLAGS : -fomit-frame-pointer -O -mfpmath=387 -m64
.............................................................................................................../usr/local/lib/python2.6/dist-packages/scipy/linalg/decomp.py:1177: DeprecationWarning: qr econ argument will be removed after scipy 0.7. The economy transform will then be available through the mode='economic' argument.
  "the mode='economic' argument.", DeprecationWarning)
.............................................................................................................................................................................................................................................................................................Result may be inaccurate, approximate err = 1.07436406372e-08
...Result may be inaccurate, approximate err = 1.25504040833e-10
............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................SSSSSSSSSSS...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................K.K.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................../usr/local/lib/python2.6/dist-packages/numpy/lib/function_base.py:185: Warning: 
            The new semantics of histogram is now the default and the `new`
            keyword will be removed in NumPy 2.0.
            
  """, Warning)
....................................................................................S................................................................................../usr/local/lib/python2.6/dist-packages/scipy/stats/stats.py:420: DeprecationWarning: scipy.stats.mean is deprecated; please update your code to use numpy.mean.
Please note that:
    - numpy.mean axis argument defaults to None, not 0
    - numpy.mean has a ddof argument to replace bias in a more general manner.
      scipy.stats.mean(a, bias=True) can be replaced by numpy.mean(x,
axis=0, ddof=1).
  axis=0, ddof=1).""", DeprecationWarning)
./usr/local/lib/python2.6/dist-packages/scipy/stats/stats.py:1329: DeprecationWarning: scipy.stats.std is deprecated; please update your code to use numpy.std.
Please note that:
    - numpy.std axis argument defaults to None, not 0
    - numpy.std has a ddof argument to replace bias in a more general manner.
      scipy.stats.std(a, bias=True) can be replaced by numpy.std(x,
      axis=0, ddof=0), scipy.stats.std(a, bias=False) by numpy.std(x, axis=0,
      ddof=1).
  ddof=1).""", DeprecationWarning)
/usr/local/lib/python2.6/dist-packages/scipy/stats/stats.py:1305: DeprecationWarning: scipy.stats.var is deprecated; please update your code to use numpy.var.
Please note that:
    - numpy.var axis argument defaults to None, not 0
    - numpy.var has a ddof argument to replace bias in a more general manner.
      scipy.stats.var(a, bias=True) can be replaced by numpy.var(x,
      axis=0, ddof=0), scipy.stats.var(a, bias=False) by var(x, axis=0,
      ddof=1).
  ddof=1).""", DeprecationWarning)
./usr/local/lib/python2.6/dist-packages/scipy/stats/morestats.py:603: UserWarning: Ties preclude use of exact statistic.
  warnings.warn("Ties preclude use of exact statistic.")
....../usr/local/lib/python2.6/dist-packages/scipy/stats/stats.py:498: DeprecationWarning: scipy.stats.median is deprecated; please update your code to use numpy.median.
Please note that:
    - numpy.median axis argument defaults to None, not 0
    - numpy.median has a ddof argument to replace bias in a more general manner.
      scipy.stats.median(a, bias=True) can be replaced by numpy.median(x,
axis=0, ddof=1).
  axis=0, ddof=1).""", DeprecationWarning)
....................................................................................................................................................................................................Warning: friedmanchisquare test using Chisquared aproximation
...............warning: specified build_dir '_bad_path_' does not exist or is not writable. Trying default locations
.....warning: specified build_dir '_bad_path_' does not exist or is not writable. Trying default locations
...............................building extensions here: /home/briedel/.python26_compiled/m0
................................................................................................
======================================================================
FAIL: test_x_stride (test_fblas.TestCgemv)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/scipy/lib/blas/tests/test_fblas.py", line 345, in test_x_stride
    assert_array_almost_equal(desired_y,y)
  File "/usr/local/lib/python2.6/dist-packages/numpy/testing/utils.py", line 765, in assert_array_almost_equal
    header='Arrays are not almost equal')
  File "/usr/local/lib/python2.6/dist-packages/numpy/testing/utils.py", line 609, in assert_array_compare
    raise AssertionError(msg)
AssertionError: 
Arrays are not almost equal

(mismatch 33.3333333333%)
 x: array([ -5.18813848 +5.18813848j,   8.80231285 -6.80231285j,
       -18.78035927+22.78035927j], dtype=complex64)
 y: array([ -5.18813848 +5.18813848j,   8.80231285 -6.80231285j,
       -18.78035927+22.78035736j], dtype=complex64)

----------------------------------------------------------------------
Ran 3490 tests in 46.070s

FAILED (KNOWNFAIL=4, SKIP=28, failures=1)
<nose.result.TextTestResult run=3490 errors=0 failures=1>
>>> from scipy.optimize import curve_fit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: cannot import name curve_fit


Any help with this?

Thanks.

---

### Post by yosefmel on 2010-08-19
curve_fit is only available in SciPy 0.8.x.
I don't know why there is no version bump, I see the Maverick package is still 0.7.2 while 0.8.0 is out some time now.

---

