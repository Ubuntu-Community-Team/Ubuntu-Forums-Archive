---
title: "dlerror:libQtGui.so.4: cannot open shared object file"
date: 2013-10-20
forum: Programming Talk
---

### Post by MikeCyber on 2013-10-20
Hi
michael@michael-Ubuntu:/usr/lib/x86_64-linux-gnu$ ls -la libQtGui*
-rw-r--r-- 1 root root      708 Okt 13 15:18 libQtGui.prl
lrwxrwxrwx 1 root root       17 Okt 13 15:18 libQtGui.so -> libQtGui.so.4.8.4
lrwxrwxrwx 1 root root       17 Okt 13 15:18 libQtGui.so.4 -> libQtGui.so.4.8.4
lrwxrwxrwx 1 root root       17 Okt 13 15:18 libQtGui.so.4.8 -> libQtGui.so.4.8.4
-rw-r--r-- 1 root root 11200352 Okt 13 15:31 libQtGui.so.4.8.4

Why can't it find libQtGui in 13.10?
Thanks

PS: tried sudo ldconfig -v without success

---

### Post by spjackson on 2013-10-20
You've not given us much to go on. What are you trying to run? Is it a 32-bit executable? Was libqt installed via the package manager? If not, it might have unsatisfied dependencies.

---

### Post by MikeCyber on 2013-10-20
yes, i might need the 32bit qt libs on my 64bit machine.

---

