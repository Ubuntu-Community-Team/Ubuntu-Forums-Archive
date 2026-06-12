---
title: "GNAT Ada FLOAT Precision"
date: 2012-02-03
forum: Programming Talk
---

### Post by DRMCG on 2012-02-03
I am porting a legacy Ada application from VAX/Alpha platform to XP using GNAT GPL Ada on XP (but the HP compiler on the VAX). When comparing outputs, I noticed that the XP version had slightly better accuracy using FLOATs. Both applications are using IEEE_FLOAT. My suspicion is that because, ultimately, there is a C compiler involved that, under XP, the FLOATs are being promoted to double precision (as would happen in C) for arithmetic and then converted back to single precision. I have observed that there is a switch on the C compiler to override the promotion of single precision FLOATs (-fallow-single-precision) but cannot see how to achieve the same effect via the GNAT Ada front end. I feel certain that nobody would normally complain about a gain in accuracy but the rules of the Ada language appear to be being broken in this implementation and I would like both versions to match for acceptance purposes.

---

