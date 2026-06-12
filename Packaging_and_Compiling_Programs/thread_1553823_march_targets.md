---
title: "march targets"
date: 2010-08-15
forum: Packaging and Compiling Programs
---

### Post by davidogg on 2010-08-15
is there any functional difference between Athlon64-sse3 and k8-sse3? When would one be used over the other?

---

### Post by davidogg on 2010-08-15
gcc -Q --help=target -march=k8-sse3

returns the same as

 gcc -Q --help=target -march=Athlon64-sse3

So I guess they are the same. it's "native" that isn't behaving as expected

 gcc -Q --help=target -march=native 

isn't setting all the flags it should be...

nevermind :P

---

