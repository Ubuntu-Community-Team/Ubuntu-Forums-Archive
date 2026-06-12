---
title: "python headache: running python in C"
date: 2008-11-19
forum: Programming Talk
---

### Post by yilin on 2008-11-19
I got the following code from web and like to try on my newly installed ubuntu:

#include <stdio.h>
#include <Python.h>
#include <pythonrun.h>
int main(int argc, char *argv[]) {
  Py_Initialize();
  PyRun_SimpleString("from time import time,ctime\n"
"print 'Today is',ctime(time())\n");
Py_Finalize();
return 0;
}

Here is the msg from gcc: 

$ gcc py.c -o py -I/usr//include/python2.5/
/tmp/ccwzN4bX.o: In function `main':
py.c: (.text+0x12): undefined reference to `Py_Initialize'
py.c: (.text+0x26): undefined reference to `PyRun_SimpleStringFlags'
py.c: (.text+0x2b): undefined reference to `Py_Finalize'

collect2: ld returned 1 exit status


I don't know how to make the code working. Any ideas? 
I really need to see how c can invoke python...


[email]el.debian@gmail.com[/email]

---

### Post by en0f on 2008-11-19
```
$ gcc test.c -o test -lpython2.5 -lm -L/usr/lib/python2.5/config/ -I/usr/include/python2.5/
$ ./test
Today is Thu Nov 20 01:05:17 2008
```

---

### Post by yilin on 2008-11-19
> **en0f said:**
> ```
$ gcc test.c -o test -lpython2.5 -lm -L/usr/lib/python2.5/config/ -I/usr/include/python2.5/
$ ./test
Today is Thu Nov 20 01:05:17 2008
```

Thanks a lot enOf! It works.

---

