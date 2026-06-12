---
title: "Scipy on Python3: BLAS Libraries not found"
date: 2012-01-04
forum: Programming Talk
---

### Post by kramer65 on 2012-01-04
Hello,


I've got Ubuntu 11.10 running with Python3.2 installed. I now want to install numpy and scipy on Python3. With Numpy there was no problem, but when I run the installer script for scipy (*python3 setup.py install --user*) I get an error saying:
```
numpy.distutils.system_info.BlasNotFoundError: 
    Blas (http://www.netlib.org/blas/) libraries not found.
    Directories to search for the libraries can be specified in the
    numpy/distutils/site.cfg file (section [blas]) or by setting
    the BLAS environment variable.
```

As far as I know I installed BLAS using synaptic. I have no clue where it is located though.

Does anybody have any idea how I can solve this?

---

### Post by kramer65 on 2012-01-04
Nevermind!

I now see I also needed to install "libblas-dev". After a second try the same accounted for "liblapack-dev".

Thanks anyway!

---

