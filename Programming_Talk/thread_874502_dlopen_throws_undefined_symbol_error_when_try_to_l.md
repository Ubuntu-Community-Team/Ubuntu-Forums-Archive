---
title: "dlopen throws undefined symbol error when try to load shared library"
date: 2008-07-30
forum: Programming Talk
---

### Post by ankushjain79 on 2008-07-30
Hi,

I am trying to develop a plugin which will display video in the mozilla firefox browser much like Youtube. 
For this I am using PWLIB and OPAL libaries for the video plugins. But when I try to load the video plugins using dlopen system call, it returns an error of undefined symbol _ZNK13PAbstractList7CompareERK7PObject. 
This class is present in another shared library libpt_linux_x86_r.so.1.10.10. I have tried using the RTLD_NOW and RTLD_LAZY flags but none of them solved the problem.
The library libpt_linux_x86_r.so.1.10.10 is loaded by firefox plugin which in turn try to load the video plugin library which fails.
If somebody can tell me what could be reason for this error.
Also any other approach to get the streaming in browser will be of great help.

Thanks in advance.

Ankush

---

