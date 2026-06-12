---
title: "How to find a file pointer position using a file descriptor"
date: 2008-09-09
forum: Programming Talk
---

### Post by mentallysilent on 2008-09-09
Hello, 

How do I find out the position of a file pointer using a file descriptor? I'm trying to port some windows code to Linux and the code calls _ftell which comes from io.h
What is the equivalent in Linux? ftell doesn't seem to be it since it doesn't take a file descriptor. 

Thanks very much

---

### Post by kjohansen on 2008-09-09
You can do:

```

#include <fildes.h>
int fd=open(....);        //file descriptor
FILE *f = fileptr( fd );  //file pointer

```

---

### Post by mentallysilent on 2008-09-09
Where does 'fileptr(int)' come from?

---

### Post by kjohansen on 2008-09-09
[http://www.thinkage.ca/english/gcos/expl/c/lib/filept.html](http://www.thinkage.ca/english/gcos/expl/c/lib/filept.html)

---

### Post by mentallysilent on 2008-09-09
Thanks very muuch.

I don't seem to have this header file tho. The include line causes an error:

error: filedes.h: No such file or directory

---

### Post by kjohansen on 2008-09-09
what compiler are you using? And what system are you on?

---

### Post by mentallysilent on 2008-09-09
uname -a: 2.6.22-14-generic #1 SMP i686 GNU/Linux
gcc --version: gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

---

### Post by kjohansen on 2008-09-09
The <fildes.h> solution I grabbed from an old lab from school that ran on the school's unix systems, but I get an error on my ubuntu distro.

My office mate suggested:
```

#include<stdio.h>
FILE * filePTR=fdopen(int fildes, const char *mode); 

```

mode ='r', 'w'...

---

### Post by Zugzwang on 2008-09-09
You can use the lseek/fseek functions:
```

int ptr = fseek(file, 0, SEEK_CUR);

```

---

### Post by mentallysilent on 2008-09-09
fseek takes a FILE* pointer. I only a have an integer file descriptor :(

---

### Post by mentallysilent on 2008-09-09
Thanks. That compiled successfully.

---

