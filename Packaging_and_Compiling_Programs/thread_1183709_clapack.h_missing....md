---
title: "clapack.h missing..."
date: 2009-06-10
forum: Packaging and Compiling Programs
---

### Post by jiapei100 on 2009-06-10
In order to compile loads of other important packages, clapack.h is always required. However, in Ubuntu 9.04 Jaunty, after grabbing liblapack3gf and liblapack-dev, there is no clapack.h at all.

There is a atlas lapack binding, which will install clapack.h, but it is a binding for atlas, which is not the original clapack.h 

So, any suggestions?


I downloaded clapack.h from [http://www.netlib.org/clapack/](http://www.netlib.org/clapack/) and copied it into /usr/include/

However, during compiling, I always obtain the following error messages:

undefined reference to `sgetri_(long*, float*, long*, long*, float*, long*, long*)' 

undefined reference to `sgesv_(long*, long*, float*, long*, long*, float*, long*, long*)'

undefined reference to `dgetrf_(long*, long*, double*, long*, long*, long*)' 

undefined reference to `dgelsd_(long*, long*, long*, double*, long*, double*, long*, double*, double*, long*, double*, long*, long*, long*)' 

....

etc.

BTW, I'm pretty sure that I "#include <f2c.h> "

So, can anybody give me some suggestions?

Thanks in advance.


Best Regards
JIA Pei

---

