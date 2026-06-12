---
title: "c:1:18: fatal error: apue.h: No such file or directory"
date: 2016-02-20
forum: Programming Talk
---

### Post by Ramya_Guduru on 2016-02-20
hi Gurus,
I'm compiling a very basic C program in Linux

I have stored the 'hello.c' file on the Desktop. The file contains:

```
#include "apue.h"

int
main(void)
{
    printf("uid = %d, gid = %d\n", getuid(), getgid());
    exit(0);
}

```
In Linux Ubuntu, when I entered 
```
username@ubuntu/Desktop$ gcc hello.c

I'm receiving the following error:

hello.c:1:18: fatal error: apue.h: No such file or directory
 #include "apue.h"
                  ^
compilation terminated.
```

Please help

---

### Post by steeldriver on 2016-02-20
Hello and welcome to the forums

The missing file appears to be specific to the [Advanced Programming in the UNIX® Environment]("http://www.apuebook.com/apue3e.html") book - did you download / unpack their software from the website?

---

### Post by Ramya_Guduru on 2016-02-20
hi steeldriver,

I have downloaded and unpaced the apue.3e in the Downloads folder. 
I'm trying to run the very basic 'hello world' program that came along with the downloaded software.

```
ramyag@ubuntu:~/Downloads/apue.3e/intro$ gcc hello.c
hello.c:1:18: fatal error: apue.h: No such file or directory
 #include "apue.h"
                  ^
compilation terminated.
```

---

### Post by lisati on 2016-02-20
*Thread moved to **Programming Talk**.*
The compiler won't automatically know where to find the file if it's in your Downloads folder. One solution might be to copy it to the same folder as your hello.c file.

I've also added [noparse]```
 and 
```[/noparse] tags to your posts as it helps improve readability of program listings.

---

### Post by steeldriver on 2016-02-20
Try
```

gcc -I../include hello.c

```

---

