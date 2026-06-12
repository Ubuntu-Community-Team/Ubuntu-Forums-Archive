---
title: "Simple seg-fault question"
date: 2010-08-09
forum: Programming Talk
---

### Post by vik_2010 on 2010-08-09
I'm getting a seg fault with this simple program. I'm experimenting with function pointers and don't know why I'm getting it (yah, i need to use gdb, but it's been a while and i've forgotten how to use it. does anyone know any good tutorials?)

thanks.
[PHP]
#include<stdio.h>
#include<stdlib.h>

typedef struct {
  int var;
  void (*func)(void);
}test_struct;

int main(int argc, char *argv[]) 
{
  test_struct *x = malloc(sizeof(test_struct));
  x->func();
  printf("DONE\n");
  return 0;
}

void func(){
  char *x = "HELLO WORLD!";
  printf("%s\n",x);
 
}

[/PHP]

---

### Post by Bachstelze on 2010-08-09
Null pointer dereference, you do not initialize x.

```
11	    test_struct *x = malloc(sizeof(test_struct));
(gdb) step
12	    x->func();
(gdb) print *x
$1 = {
  var = 0, 
  func = 0
}

```

```
firas@tsukino ~ % cat test.c                             
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int var;
    void (*func) (void);
} test_struct;

void func(void);

int main(int argc, char *argv[]) 
{
    test_struct *x = malloc(sizeof(test_struct));
    x->func = func;
    x->func();
    printf("DONE\n");
    free(x);
    return 0;
}

void func(void)
{
    char *x = "HELLO WORLD!";
    printf("%s\n",x);
}
 
firas@tsukino ~ % cc -ansi -Wall -pedantic -o test test.c
firas@tsukino ~ % ./test                                 
HELLO WORLD!
DONE

```

malloc() without free() is bad.

gdb tutorial: [http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html)

---

### Post by vik_2010 on 2010-08-09
ah ok thanks.

---

