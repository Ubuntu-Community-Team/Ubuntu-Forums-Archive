---
title: "Installing numpy on ubuntu"
date: 2007-10-03
forum: Programming Talk
---

### Post by anupamme on 2007-10-03
Hi everyone, I am trying to install python-numpy on ubuntu. But I am not able to do so because it requires libraries like;

blas, atlas, lapack, mkl

and it cannot locate these libraries. I have installed these debian packages:

atlas3-3dnow
lapack3

using apt-get. blas is not available in the list of deb packages. 

Now when I install python-numpy using apt-get, I get a broken numpy because it doesnt run the test: python -c 'import numpy; numpy.test()'
successfully and gives errors like failed to import some files.

Alternatively, when i install numpy using the package at sourceforge using python setup.py install, I get various warnings like atlas, blas, lapack etc are missing. But, it passes the test: python -c 'import numpy; numpy.test()'

So, my question is how to install numpy? If sourceforge package is the suggested way then what are the suggested ways of installing its required packages like lapack, blas, atlas etc.

thanks
anupam

---

### Post by pmasiar on 2007-10-03
> **anupamme said:**
> 
Alternatively, when i install numpy using the package at sourceforge using python setup.py install, I get various warnings like atlas, blas, lapack etc are missing. But, it passes the test: python -c 'import numpy; numpy.test()'


Do you need atlas, blas, lapack? If you do, can you install them separately, either before or after numpy - check the doc?

In my experience with turbogears, installer from website worked correctly and apt-get did not - some wrong dependencies. Maybe something like that is happening with numpy?

---

### Post by insyzygy on 2007-10-03
Numpy does not require atlas, blas etc.

Blas stands for basic linear algebra supprograms.
There are many implementations of the blas standard.
Atlas in particular is very optimize blas that is commonly used.
So if you have atlas you have a blas.

Numpy will build its own minimal implementation of blas and other linear algebra libraries
if it can't find them on your system, so even though it didn't find them, the numpy you built is fully functional.

Unless you specifically want to use numpy to do large scale numerical linear algebra, you probably are ok with the numpy you have built.

If you do want to build it against atlas, there is a file 
site.cfg in the directory (relative to the top of the source) 
numpy/distutils/site.cfg.

In that file you will need to specify the path to your ATLAS library.

---

### Post by anupamme on 2007-10-03
> **insyzygy said:**
> Numpy does not require atlas, blas etc.

Blas stands for basic linear algebra supprograms.
There are many implementations of the blas standard.
Atlas in particular is very optimize blas that is commonly used.
So if you have atlas you have a blas.

Numpy will build its own minimal implementation of blas and other linear algebra libraries
if it can't find them on your system, so even though it didn't find them, the numpy you built is fully functional.

Unless you specifically want to use numpy to do large scale numerical linear algebra, you probably are ok with the numpy you have built.

If you do want to build it against atlas, there is a file 
site.cfg in the directory (relative to the top of the source) 
numpy/distutils/site.cfg.

In that file you will need to specify the path to your ATLAS library.

I think I should be fine with the minimal implementation of numerical linear algebra using numpy. I installed numpy using apt-get install python-numpy. Now when in a program I write: from pylab import *, I get an error: ImportError: cannot import Int8, UInt8.

When from python prompt, I run: from numpy import Int8, I get the following error message:

RuntimeError: module compiled against version 1000009 of C-API but this version of numpy is 1000002
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/numpy/__init__.py", line 40, in ?
    import linalg
  File "/usr/lib/python2.4/site-packages/numpy/linalg/__init__.py", line 4, in ?
    from linalg import *
  File "/usr/lib/python2.4/site-packages/numpy/linalg/linalg.py", line 25, in ?
    from numpy.linalg import lapack_lite
ImportError: numpy.core.multiarray failed to import
--

Looks like there is a version mismatch. Alternatively, I tried installing numpy from sourceforge, but when I install it I get numerous warnings messages like:

/home/pompey/numpy-1.0.3.1/numpy/distutils/system_info.py:1221: UserWarning: 
    Atlas ([http://math-atlas.sourceforge.net/](http://math-atlas.sourceforge.net/)) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [atlas]) or by setting
    the ATLAS environment variable.
  warnings.warn(AtlasNotFoundError.__doc__)
/home/pompey/numpy-1.0.3.1/numpy/distutils/system_info.py:1232: UserWarning: 
    Lapack ([http://www.netlib.org/lapack/](http://www.netlib.org/lapack/)) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [lapack]) or by setting
    the LAPACK environment variable.
  warnings.warn(LapackNotFoundError.__doc__)
/home/pompey/numpy-1.0.3.1/numpy/distutils/system_info.py:1235: UserWarning: 
    Lapack ([http://www.netlib.org/lapack/](http://www.netlib.org/lapack/)) sources not found.
    Directories to search for the sources can be specified in the
    numpy/distutils/site.cfg file (section [lapack_src]) or by setting
    the LAPACK_SRC environment variable.
  warnings.warn(LapackSrcNotFoundError.__doc__)
--

Now, when I run: from numpy import Int8, I get an import error.

So, I do not know how to install numpy so that I can use it properly and one indication of this would be that if I run: from numpy import Int8, it should run fine. So, any suggestions?

---

### Post by insyzygy on 2007-10-04
The problem is that you are trying to use an older  binary version of matplotlib with the newest version of numpy which you just compiled. 

You will need to either go back to the version of numpy in the respositories using apt-get. (The fact that some tests failed doesn't mean its totally broken its probably things like lapack, atlas-base, etc not on your system). If you installed atlas from debian and not ubuntu, then ubuntus numpy won't link against it ( I don't think).

Or you need to install the newest matplotlib from source which hopefully has changed to accomodate the newest version of numpy. 

What are you trying to accomplish exactly, you appear to be trying to plot some things. You might look at 
[http://sage.math.washington.edu/sage/]("http://sage.math.washington.edu/sage/")
It is a self contained computer algebra system built on python that includes numpy and matplotlib, pylab, and many more things. Just download the binary and extract it and you can run it. There is a graphical interface to it via your web browser or you can just use the console.

For example to plot I just did
sage: import numpy
sage: import pylab
sage: RealNumber=float
sage: Integer=int
sage: t=numpy.arange(0.0,2.0.0.01)
sage: s=numpy.sin(2*numpy.pi*t)
sage: pylab.plot(t,s,linewidth=1.0)
sage: pylab.savefig('test')

---

### Post by Imas on 2009-02-02
> **insyzygy said:**
> 
sage: import numpy
sage: import pylab
sage: RealNumber=float
sage: Integer=int
sage: t=numpy.arange(0.0,2.0.0.01)
sage: s=numpy.sin(2*numpy.pi*t)
sage: pylab.plot(t,s,linewidth=1.0)
sage: pylab.savefig('test')

I get the following error:
Syntax Error:
   s = numpy.sin(2*numpy.pi*t)

Do you know why?

---

