---
title: "gdb option to see from a memory address onwards?"
date: 2014-10-22
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-22
Hello,
 I was wondering if there is an option in gdb to see from a particular memory address **onwards**. I normally print out the values using
```

(gdb) p *A1
(gdb) p *(A1+1)
(gdb) p *(A1+2)
(gdb) p *(A1+3)

```

Is there something where I can see the contents of the next **n** memory locations starting from A1?

_Use Case : _
I define my arrays using pointers.
So I would have something like
```

int* A1;
A1= malloc(10 * sizeof(int));

for(i=0;i<10;i++)
 *(A1 + i) = i+1;

```

Now I want to see the array contents using gdb.

Please advise.
Thanks.

---

### Post by spjackson on 2014-10-23
```

(gdb) p *A1@10
$2 = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

```
See [http://ftp.gnu.org/old-gnu/Manuals/gdb/html_chapter/gdb_9.html#SEC54](http://ftp.gnu.org/old-gnu/Manuals/gdb/html_chapter/gdb_9.html#SEC54)

---

### Post by IAMTubby on 2014-10-24
> **spjackson said:**
> ```

(gdb) p *A1@10
$2 = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

```
See [http://ftp.gnu.org/old-gnu/Manuals/gdb/html_chapter/gdb_9.html#SEC54](http://ftp.gnu.org/old-gnu/Manuals/gdb/html_chapter/gdb_9.html#SEC54)
spjackson, haha, this is insane :D

---

