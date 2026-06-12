---
title: "Segmentation fault in malloc.c"
date: 2011-01-02
forum: Programming Talk
---

### Post by DBQ on 2011-01-02
Hello Everybody.

My program has segmentation fault when I use new to allocate memory. According to GDB there is a SIGSEGV in malloc.c library. I.e.

```

0x002d3939 in _int_malloc (av=0x3bf3c0, bytes=20) at malloc.c:4249
4249	malloc.c: No such file or directory.
	in malloc.c


```

What are the usual causes for something so bizzare?

---

### Post by worksofcraft on 2011-01-03
> **DBQ said:**
> 
What are the usual causes for something so bizzare?

Usually it is when your program writes outside allocated memory blocks. Typically this corrupts pointers recorded block sizes and other data structures that are used to organize the heap.

---

### Post by DBQ on 2011-01-03
Thanks. Could something like this also happen from overflowing the heap i.e. if I keep dynamically allocating memory without freeing it?

---

### Post by worksofcraft on 2011-01-03
> **DBQ said:**
> Thanks. Could something like this also happen from overflowing the heap i.e. if I keep dynamically allocating memory without freeing it?

TBH I thought malloc returns NULL when the heap is exhausted and that if you used that NULL as were it a valid heap address then sure it could segfault... I think you can also set it up to throw some kind of out of memory exception in C++... however just assuming you didn't do any of that I tried it:

[php]
// g++ malloctest.cpp
#include <cstdio>
#include <stdlib.h>

int main(int argc, char *argv[], char *envp[]) {
	char *pMem;
	long i = 0;
	do {
		printf("Mb allocated:%ld\n", ++i);
//		pMem = (char *) malloc(1000000);
		pMem = new char[1000000];
	} while (pMem);

	printf("heap exhausted after %ld Mbyte mallocs\n", i);
	return !printf("exits normally\n");
}
[/php]

and now IDK cuz it just kept running allocating way more memory than I have total disk space even and I had to ^C to get out :shock:

---

### Post by Lootbox on 2011-01-03
If you're using the malloc function itself, it'll return NULL if the heap is out of memory. In C++, if you're using the new keyword, it'll either:
- throw a std::bad_alloc exception
- if you set your own new-handler function, it will call that
- if you defined operator new for the class that you're allocating memory for, it will take whatever action you take there when malloc returns NULL
- if your compiler is old enough, it may just return NULL for backwards-compatibility

These shouldn't be leading to a segmentation fault in malloc itself, so the problem probably isn't a heap overflow.

---

### Post by nvteighen on 2011-01-03
Please, show us some short code where this happens.

---

### Post by Arndt on 2011-01-03
> **DBQ said:**
> Hello Everybody.

My program has segmentation fault when I use new to allocate memory. According to GDB there is a SIGSEGV in malloc.c library. I.e.

```

0x002d3939 in _int_malloc (av=0x3bf3c0, bytes=20) at malloc.c:4249
4249	malloc.c: No such file or directory.
	in malloc.c


```

What are the usual causes for something so bizzare?

Have you tried using 'valgrind' with the program?

---

