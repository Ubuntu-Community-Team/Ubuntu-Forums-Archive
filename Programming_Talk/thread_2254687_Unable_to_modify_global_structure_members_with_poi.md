---
title: "Unable to modify global structure members with pointers"
date: 2014-11-29
forum: Programming Talk
---

### Post by morbs_gt on 2014-11-29
Hello,

I'm trying to learn about these pthreads and semaphores, and I can't seem to find any solutions to the following:

I have 2 global structs, where in a function, depending on some conditions, I'd like to point to either struct and modify member contents.

```

#include <header-files.h>

struct buf_t {
  int buf[SOME_SIZE];
  int var1;
  sem_t full;
  sem_t empty;
  sem_t mutex;
};

struct buf_t buf1;
struct buf_t buf2;

int some_func(){
  struct buf_t *pbuf;
  if (some-condition){
    pbuf = &buf1;
  } else if (some-other-condition){
    pbuf = &buf2;
  }
  **[COLOR=#ff0000]sem_getvalue(&pbuf.full, &var1);[/COLOR]**
  [COLOR=#ff0000]...[/COLOR]
}

int main(){
  sem_init(...
  sem_init(...
  ...
  some_func();
  return 0;
}  

```

I get this when compiling:
```

test.c:179:23: error: request for member ‘full’ in something not a structure or union
   sem_getvalue(&pbuf.full, &var1);
                     ^
```
The funky ^ is under the period of &pbuf.full in case is appears differently on your screen, the error message elaborates on that.

The reason why I'd like to point to either buffer depending on a condition is that I have a lot of code manipulating the buffers, and I'd like to avoid having to copy paste the same code twice.

I've also tried **pbuf->full** to no avail.

Any help is greatly appreciated, let me know if you need more details.

---

### Post by spjackson on 2014-11-29
It looks to me like you want:
```

sem_getvalue(&(pbuf->full), &var1);

```

---

### Post by morbs_gt on 2014-11-29
Yup, Thanks! I wasn't paying attention. Marked solved.

---

