---
title: "problem in accessing data file"
date: 2008-08-06
forum: Programming Talk
---

### Post by S N RAY on 2008-08-06
I am unable to access data file to run fortran77 programs in fedora. Is it a problem of the sub directory mismatch. whether the data and the program should both be in the same sub-directory. Otherwise the program has compiled successfully and the execute command produces a window where is the comment "press enter continue" is seen. However, if Enter is pressed , the window dissapears, leaving me to wonder what to do next.

snray

---

### Post by Zugzwang on 2008-08-06
You can just run the program from the directory in which the data file is present.

So if for example the data is in /foo/bar and the program is in /foo/program, then you type "cd /foo/bar" in the terminal and run the program using ../program/EXECUTABLE_FILE_NAME".

With respect to the behaviour of the program: That's likely to be application-specific behaviour. Without even telling us what you are running, there's only the advice to read the manual.

---

