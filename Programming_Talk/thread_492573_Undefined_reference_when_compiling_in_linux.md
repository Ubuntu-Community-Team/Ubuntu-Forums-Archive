---
title: "Undefined reference when compiling in linux"
date: 2007-07-04
forum: Programming Talk
---

### Post by nonoykevin on 2007-07-04
when i compile my program in linux (ubuntu) there is no error but it shows "undefined reference to a specified function, i use thid command when i compile (g++ LoaderControl.cpp -o LoaderControl). But if i'm goin to compile using gcc -c LoaderControl.cpp, there is no error... can anybody explain me why? any answer to this question pls....thanks

---

### Post by slavik on 2007-07-05
without seeing exact errors and source code, we can't really help you ...

---

### Post by geraldm on 2007-07-05
>compile using gcc -c LoaderControl.cpp
There is no error, because the error comes when the source is linked,
and linking was not done.  BTW: use g++ to compile *.cpp source, not
gcc.

---

### Post by nonoykevin on 2007-07-05
here's the sample result when i compile my source code in g++...

file.cpp: (.text + 0xc50): undefined reference to 'Cfile::Open()'
....
....

thanks...

---

### Post by nonoykevin on 2007-07-05
that's why when i used the g++ then the result comes undefined reference..but when i compile in gcc there's no error...

---

### Post by slavik on 2007-07-05
did you include the proper files, did you link the proper libraries?

---

### Post by nonoykevin on 2007-07-06
i already check my source code and all include files were linked together...the only problem was that the classes of one of my linked source was undefined reference to the one i compiled...

---

