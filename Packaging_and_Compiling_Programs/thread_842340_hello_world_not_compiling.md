---
title: "hello world not compiling"
date: 2008-06-27
forum: Packaging and Compiling Programs
---

### Post by enchesss on 2008-06-27
sorry - a noob question

am trying to compile a simple hello world program using cpp

what is giving an error here?


en@en-desktop:~/prog$ cat hello.c
#include <stdio.h>

main()
{
	printf("hello world\n");
}
en@en-desktop:~/prog$ cc -o hello hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
en@en-desktop:~/prog$

---

### Post by ibutho on 2008-06-27
Hi.

Make sure you install the build-essential package and try the code below
```

#include <stdioh.h>
int main(void)
{
    printf ("Hello, World!\n");
    return 0;
}

```
To compile
```
gcc -o hello hello.c
```

---

### Post by enchesss on 2008-06-27
installed essentials and everything works now thanks!

---

