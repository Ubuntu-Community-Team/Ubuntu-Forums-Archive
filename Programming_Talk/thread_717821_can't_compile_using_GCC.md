---
title: "can't compile using GCC"
date: 2008-03-07
forum: Programming Talk
---

### Post by Raaj on 2008-03-07
everytime I am trying to compile a source code, asdf.c using:
```
gcc asdf.c
```
 i get the error :
```
asdf.c: In function ‘main’:
asdf.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

```

note, the simple asdf.c  file is :

```
main()
{
        printf("Hello World");
}

```

---

### Post by lnostdal on 2008-03-07
```

$ sudo aptitude install build-essential
$ cat hello.c

#include <stdio.h>

int main()
{
  printf("hello world\n");
  return 0;
}

$ gcc -g -Wall -o hello hello.c
$ ./hello
hello world
$

```

---

### Post by LaRoza on 2008-03-07
Two problems:

[php]
#include <stdio.h>
int main()
{
    printf("Hello World");
    return 0;
}
[/php]

And make sure you have build-essential installed.

```

sudo aptitude install build-essential

```

---

### Post by lnostdal on 2008-03-07
hah! .. i beat you to it ..

---

### Post by LaRoza on 2008-03-07
> **lnostdal said:**
> hah! .. i beat you to it ..

I know, we were both beat technically as the **sticky** has this information.

---

### Post by lnostdal on 2008-03-07
hehe, yeah .. the OP is a lazy bum .. you hear that, OP? :}

---

