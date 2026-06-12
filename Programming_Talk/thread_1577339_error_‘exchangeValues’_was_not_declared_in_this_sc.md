---
title: "error: ‘exchangeValues’ was not declared in this scope"
date: 2010-09-18
forum: Programming Talk
---

### Post by techbrainless on 2010-09-18
Hi All,

I am ( working on ubuntu 10.4 desktop) trying to execute the following simple c program

callByReferenceValue.c
```
#include <stdio.h>
#include <stdlib.h>

int main()
{
        system("clear");

        int x,y;
        x=100;
        y=200;

        printf("Before exchange x = %d \t y = %d",x,y);
        exchangeValues(&x,&y);

        printf("After exchange x = %d \t y = %d",x,y);

        return 0;

}
void exchangeValues(int *a, int *b)
{
        int t;
        t = *a;
        *a = *b;
        *b = t;
}
```



but getting the error 

```
callByReferenceValue.c: In function ‘int main()’:
callByReferenceValue.c:13: error: ‘exchangeValues’ was not declared in this scope
```

---

### Post by worksofcraft on 2010-09-18
The C compiler hasn't discovered the definition of exchangeValues yet when you call it from main().

I usually write my programs with main() at the end to avoid this problem, but you can put a forward declaration in if you prefer.

---

