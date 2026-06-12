---
title: "How to make numpy use ATLAS?"
date: 2010-10-08
forum: Programming Talk
---

### Post by stair314 on 2010-10-08
Can anyone explain how to get numpy to recognize atlas? I have atlas built and installed, and I put what I thought should be sufficient, based on numpy's INSTALL.TXT, to make numpy use atlas in my site.cfg then ran python setup.py install. The resulting build is incredibly slow. Multiplying a 1,000 x 1,000 matrix takes 8 seconds. The default packages take .8 . On a computer at work with a similar but slower cpu to mine, it only takes .2, so I know I should be able to get a lot more speed out of numpy.

This is my site.cfg:

[atlas]
atlas_libs = lapack, f77blas, cblas, atlas

[DEFAULT]
library_dirs = /usr/local/atlas/lib
include_dir = /usr/local/atlas/include

---

