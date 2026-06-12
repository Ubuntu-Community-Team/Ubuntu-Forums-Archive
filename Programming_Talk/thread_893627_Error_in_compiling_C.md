---
title: "Error in compiling C"
date: 2008-08-18
forum: Programming Talk
---

### Post by basukinjal on 2008-08-18
Hello, Im pretty new to linux.

Whenever I try to cc search.c, I get:
search.c:1:19: error: stdio.h: No such file or directory
search.c: In function ‘main’:
search.c:7: warning: incompatible implicit declaration of built-in function ‘printf’

What do i need to do??
Please help!

---

### Post by dwhitney67 on 2008-08-18
You should be including stdio.h such as:
[PHP]#include <stdio.h>[/PHP]
As for the rest of your program, I have no idea what you are doing, but it appears that you are calling printf().
[PHP]int main()
{
  printf( "Hello world!\n" );
  return 0;
}[/PHP]
If you are still having trouble, maybe it is because you have not installed the compiler.  Try:
```
$ sudo apt-get install build-essential
```

---

### Post by Kadrus on 2008-08-18
Have you installed build-essential?
```
sudo apt-get install build-essential
```
and please post the output when you type : **cc** in terminal.

---

