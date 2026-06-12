---
title: "emacs strange char when running Compile..."
date: 2007-11-28
forum: Programming Talk
---

### Post by monkeyking on 2007-11-28
Hi, I have some problems displaying some chars in emacs, when I run compile.
Some charetars look like, " â\200\230 ". and when I mouse copy paste into the browser it will turn into something like "â€˜ "


```

-*- mode: compilation; default-directory: "~/Desktop/dev/pack/src/" -*-
Compilation started at Wed Nov 28 16:05:29

make -k 
g++ -c -m32  relateHMM.cpp  -g
temp.cpp: In member function â€˜double* relateHMM::full_optim(double*)â€™:
temp.cpp:824: error: ISO C++ forbids taking the address of an unqualified or parenthesized non-static member function to form a pointer to member function.  Say â€˜&relateHMM::full_optim_funâ€™
temp.cpp:824: error: cannot convert â€˜double (temp::*)(double*)â€™ to â€˜double (*)(double*)â€™ for argument â€˜3â€™ to â€˜double findmax_bfgs(int, double*, double (*)(double*), void (*)(double*, double*), double*, double*, int*, int)â€™
r

```

Thanks in advance

---

### Post by mssever on 2007-11-28
I don't use emacs, so can't help you there, but what you describe is a classic character set issue. Make sure that all your tools are using the same character set.

---

