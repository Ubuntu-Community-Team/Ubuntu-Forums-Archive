---
title: "(codeblocks) No /EHs or /Zi file or directory"
date: 2012-09-17
forum: Programming Talk
---

### Post by Aftrumpet on 2012-09-17
I just started programming with Code Blocks and I am trying to run the basic "Hello World" console application, but I get these two error lines:

g++: error: /EHs: no such file or directory
g++: error: /Zi: no such file or directory
Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings

How do I fix this?

---

### Post by dwhitney67 on 2012-09-18
Remove those compiler options (/EHs and /Zi); they mean nothing to GCC (g++).

---

### Post by andaryfaysal on 2012-11-18
HI,

I am having the same problem. I managed to get rid of /Zi by removing it from Project -> Build Options, but I couldn't find /EHs to remove it, and I am still getting it in the error. Could someone point me in its direction?

Thanks in advance.

---

