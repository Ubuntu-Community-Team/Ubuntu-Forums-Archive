---
title: "imfilter for Octave"
date: 2007-03-09
forum: Programming Talk
---

### Post by Curtisc on 2007-03-09
I can't seem to find an implementation of the MatLab function imfilter for Octave.  Has anyone written an equivalent?

---

### Post by zgornel on 2007-03-11
Imfilter performs the a simple 2d convolution between 2 matrixes. Use conv2 in octave ;) .

---

### Post by wangji on 2008-04-02
> **Curtisc said:**
> I can't seem to find an implementation of the MatLab function imfilter for Octave.  Has anyone written an equivalent?

you need to install image-1.0.5.tar.gz  as octave-forge package
just download it then pkg install image-1.0.5.tar.gz from inside octave

---

