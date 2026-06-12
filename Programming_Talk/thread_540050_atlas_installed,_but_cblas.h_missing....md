---
title: "atlas installed, but cblas.h missing..."
date: 2007-09-01
forum: Programming Talk
---

### Post by scho on 2007-09-01
Hi, I installed atlas for matrix vector multiplication before...and I programmed a code, but I couldn't remember how I installed the atlas...

Right now, I installed it through synaptic package manager (atlas3-base, atlas3-base-dev, atlas3-headers), but couldn't compile my previous code because of the "cblas.h" file missing....

Any idea for this ?

---

### Post by lloyd_b on 2007-09-01
> **scho said:**
> Hi, I installed atlas for matrix vector multiplication before...and I programmed a code, but I couldn't remember how I installed the atlas...

Right now, I installed it through synaptic package manager (atlas3-base, atlas3-base-dev, atlas3-headers), but couldn't compile my previous code because of the "cblas.h" file missing....

Any idea for this ?

A *very* useful tool in this case is "apt-file" (install the package of the same name to get it).  Here's some info on "cblas.h":
```
lloyd@laptop:~$ apt-file search cblas.h
libgsl0-dev: usr/include/gsl/gsl_cblas.h
refblas3-dev: usr/include/cblas.h
```

So I'm guessing from this that you need to install the package "refblas3-dev"

Lloyd B.

---

