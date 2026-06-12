---
title: "same include file for C and python"
date: 2008-09-12
forum: Programming Talk
---

### Post by ruudvdmeer on 2008-09-12
Hi all,

I want to use constants which have the same values in a C program and in a python script. For this I like to make one single 'include/import' file which is used by both environments. Who can tell me how to do this?

<myinclude.h>
--
#define apple 3
#define banana 7
---

---

### Post by pmasiar on 2008-09-12
> **ruudvdmeer said:**
> I want to use constants which have the same values in a C program and in a python script. For this I like to make one single 'include/import' file which is used by both environments. Who can tell me how to do this?

Of course you cannot have one file: syntax is different. What you can do is create a  little program (in Python) which will parse python version of the include and generate C version as part of make.

---

