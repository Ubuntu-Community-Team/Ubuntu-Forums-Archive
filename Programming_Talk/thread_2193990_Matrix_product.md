---
title: "Matrix product"
date: 2013-12-15
forum: Programming Talk
---

### Post by kangaba on 2013-12-15
Hi,
A book on 3D math explains how translation * rotation * inverse of a translation matrices are multiplied. Problem is, I seem to get a different resulting matrix.
Mine on the left, book on the right. The results are surrounded by red lines. Image attached.

What am I doing wrong?

---

### Post by tgalati4 on 2013-12-15
It's been a few years since I've seen affine transformations.  But I think steeldriver is correct, you missed a term.  Your notation shows **P** but the book uses p to represent "4th street".

---

### Post by steeldriver on 2013-12-15
The lower left element of your TR4x4 is wrong I think - remember you are multiplying row vector -p = -(p_x, p_y, p_z) down each column of R3x3 so you end up a row vector equal to -(p_x*r_11 + p_y*r_21 + p_z*r_31), -(p_x*r_12 + p_y*r_22 + p_z*r_32), -(p_x*r_13 + p_y*r_23 + p_z*r_33) - or in matrix form, **-p** x **R**3x3 (not just **-p**)

---

### Post by kangaba on 2013-12-16
That explains it, thanks.

---

