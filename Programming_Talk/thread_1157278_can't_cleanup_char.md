---
title: "can't cleanup char**"
date: 2009-05-12
forum: Programming Talk
---

### Post by monkeyking on 2009-05-12
How do I cleanup the following datastructure

[PHP]
#include <cstring>

void allocs(int lens,char*** strs){
  (*strs) = new char*[lens];
  for(int i=0; i<lens ; i++)
    (*strs)[i] =strdup("ddd");
}

int main(){
  char **st;
  int len = 10;
  allocs(len,&st);
  //now I want to deallocate the st structure
  for(int i =0 ;i<len;i++)
    delete st[i];
  delete [] st;
}
[/PHP]

thanks in advance

---

### Post by hanniph on 2009-05-12
Your code releases all the memory you allocated but valgrind complains about errors:
```

==3445== Mismatched free() / delete / delete []
==3445==    at 0x40239DA: operator delete(void*) (in /usr/lib/valgrind/x86-linux/vgpreload_memcheck.so)
==3445==    by 0x804871B: main (in /home/hanniph/Code/forums/a.out)
==3445==  Address 0x42b4080 is 0 bytes inside a block of size 4 alloc'd
==3445==    at 0x402501E: malloc (in /usr/lib/valgrind/x86-linux/vgpreload_memcheck.so)
==3445==    by 0x41DDD8F: strdup (in /lib/libc-2.9.so)
==3445==    by 0x80486BE: allocs(int, char***) (in /home/hanniph/Code/forums/a.out)
==3445==    by 0x80486FC: main (in /home/hanniph/Code/forums/a.out)
==3445== 
==3445== ERROR SUMMARY: 10 errors from 1 contexts (suppressed: 19 from 1)
==3445== malloc/free: in use at exit: 0 bytes in 0 blocks.
==3445== malloc/free: 11 allocs, 11 frees, 80 bytes allocated.
==3445== For counts of detected errors, rerun with: -v
==3445== All heap blocks were freed -- no leaks are possible.
```
I think it is because of using delete operator on memory that was allocated with malloc() (in strdup()). So instead of using the delete operator call the free() function on each string in array.
```

for(int i =0 ;i<len;i++)
    free(st[i]); 

```
This gives no complaints from valgrind:
```
 ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 19 from 1)
==3453== malloc/free: in use at exit: 0 bytes in 0 blocks.
==3453== malloc/free: 11 allocs, 11 frees, 80 bytes allocated.
==3453== For counts of detected errors, rerun with: -v
==3453== All heap blocks were freed -- no leaks are possible.

```

---

### Post by monkeyking on 2009-05-12
Cheers,
thanks,
I hadn't thought about strdup using malloc.

---

