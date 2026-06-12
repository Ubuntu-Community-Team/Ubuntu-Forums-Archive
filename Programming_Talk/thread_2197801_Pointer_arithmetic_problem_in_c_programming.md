---
title: "Pointer arithmetic problem in c programming"
date: 2014-01-05
forum: Programming Talk
---

### Post by Ravi_Chander_Jha on 2014-01-05
First of all Happy New Year to all of you,

I am working on assignments published by Harvard CS61 and i am facing an arithmetic problem in my pointer.
 
ptr = malloc(x)       // ie ptr = 0x804b008
ptr += 3;               // now ptr must be 0x804b011 but it is 0x804b014

So please let me know the solution of this undetermined problem that why pointer arithmetic is wrong.

---

### Post by spjackson on 2014-01-05
It depends on the type that ptr points to. If ptr is char * , you will get what you are expecting. If ptr is int * (and int is 4-bytes) then you will get what you are seeing.

---

### Post by Ravi_Chander_Jha on 2014-01-05
Thanz to replying my question but i want to say that it does not work
i have tried pointer of type chat but still not doing arithmetic operation sucessfully

---

### Post by Ravi_Chander_Jha on 2014-01-05
// please look into the code below, these r code for memory allocator

```
unsigned long long update = 0;
unsigned long long nactive = 0;
unsigned long long active_size = 0;
unsigned long long ntotal = 0;
unsigned long long total_size = 0;
unsigned long long nfail = 0;
unsigned long long fail_size = 0;
void *m61_malloc(size_t sz, const char *file, int line) {
    char *ptr = NULL;
    (void) file, (void) line;   // avoid uninitialized variable warnings
    if(ptr = malloc(sz))
    {
        ptr[0] = sz;
//        printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,ptr[0]);
        ptr += 4;
        nactive++;
        active_size += sz;
        ntotal++;
        total_size += sz;
    }
    else
    {
        nfail++;
        fail_size += sz;
    }
    return ptr;
}


void m61_free(void *ptr, const char *file, int line) {
    (void) file, (void) line;   // avoid uninitialized variable warnings
    // Your code here.
    char *fptr = ptr;
    size_t sz;
    if(ptr)
    {
        fptr -= 4;
        sz = fptr[0];
//            printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,sz);
        active_size -= sz;
        nactive--;
    }
    free(ptr);
}
```

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Programming Talk**.*

---

### Post by trent.josephsen on 2014-01-05
The first thing that leaps out at me is that in m61_malloc, you obtain a pointer (ptr) with malloc(), then return (ptr + 4). But in m61_free, you call free(ptr), which is unallowable -- you can only pass to free() the exact pointer you got from malloc(). Perhaps you meant free(fptr)?

I haven't tried to divine the meaning of everything in your code, but one other thing that might not do what you expect is the printf()s (the ones you have commented out) -- if you uncomment them, they will only print values in the range [-128,127]. Is that what you want?

As for the pointer arithmetic, though, it all looks ok to me. Can you post a small compilable example that shows the incorrect behavior?

---

### Post by spjackson on 2014-01-05
> **Ravi_Chander_Jha said:**
> Thanz to replying my question but i want to say that it does not work
i have tried pointer of type chat but still not doing arithmetic operation sucessfully
Really? Here's a demonstration that the information I gave you is correct.
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    char * p = malloc(10);
    int *  q = (int *) p;

    printf("p and q are the same %p,%p\n", p, q);
    p += 3;
    q += 3;
    printf("p and q are different %p,%p\n", p, q);

    return 0;
}

```Output
```

p and q are the same 0x2170010,0x2170010
p and q are different 0x2170013,0x217001c

```
You can see that p has increased by an offset of 3 bytes, and q has increased by an offset of 12 bytes.

---

### Post by spjackson on 2014-01-05
> **Ravi_Chander_Jha said:**
> // please look into the code below, these r code for memory allocator

```
unsigned long long update = 0;
unsigned long long nactive = 0;
unsigned long long active_size = 0;
unsigned long long ntotal = 0;
unsigned long long total_size = 0;
unsigned long long nfail = 0;
unsigned long long fail_size = 0;
void *m61_malloc(size_t sz, const char *file, int line) {
    char *ptr = NULL;
    (void) file, (void) line;   // avoid uninitialized variable warnings
    if(ptr = malloc(sz)) [COLOR=#ff0000]//bug[/COLOR]
    {
        ptr[0] = sz; [COLOR=#ff0000]//bug[/COLOR]
//        printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,ptr[0]);
        ptr += 4;  [COLOR=#ff0000]// non-portable. think in terms of sizeof(?)[/COLOR]
        nactive++;
        active_size += sz;
        ntotal++;
        total_size += sz;
    }
    else
    {
        nfail++;
        fail_size += sz;
    }
    return ptr;
}


void m61_free(void *ptr, const char *file, int line) {
    (void) file, (void) line;   // avoid uninitialized variable warnings
    // Your code here.
    char *fptr = ptr;
    size_t sz;
    if(ptr)
    {
        fptr -= 4; [COLOR=#ff0000]// non-portable. think in terms of sizeof(?)[/COLOR]
        sz = fptr[0];
//            printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,sz);
        active_size -= sz;
        nactive--;
    }
    free(ptr); [COLOR=#ff0000]//bug[/COLOR]
}
```
In addition to trent.josephsen's remarks, I've marked where I think there are faults in your code. I don't want to explain why at this point, as this is an assignment.

---

### Post by xb12x2 on 2014-01-05
> **Ravi_Chander_Jha said:**
> ptr = malloc(x)       // ie ptr = 0x804b008
ptr += 3;               // now ptr must be 0x804b011 but it is 0x804b014

Your first mistake:

Since the address of ptr is expressed as a _*hexadecimal*_ number 

0x804b008 + 3 does **NOT** equal 0x804b011

0x804b008 + 3 equals 0x804b00b 

_***Hexadecimal***_ arithmetic

---

### Post by trent.josephsen on 2014-01-05
> **spjackson said:**
> ```
    if(ptr = malloc(sz)) [COLOR="#FF0000"]//bug[/COLOR]
```

I beg to differ -- I think the actual behavior is the intended behavior for this particular line. But I would rewrite it; it's far too easy to read wrong.

(Unless you're thinking of a bug I overlooked.)

Edit: I'm wrong, it does have a serious bug.

---

### Post by spjackson on 2014-01-05
> **trent.josephsen said:**
> I beg to differ -- I think the actual behavior is the intended behavior for this particular line. But I would rewrite it; it's far to easy to read wrong.

(Unless you're thinking of a bug I overlooked.)
If I understand the intent correctly (which perhaps I haven't), then I think the caller of the function wants sz bytes to be available to it. Hence m61_malloc needs to allocate sz + "the size of the thing in which we are going to write the value of sz". As it stands, if sz is 10 and you malloc 10 then return the address + 4 bytes, then the caller only has 6 bytes available in which to write before hitting undefined behaviour. No?

---

### Post by trent.josephsen on 2014-01-05
*facepalm*

Of course, yes. I thought you were referring to the possible confusion of = and ==.

---

### Post by ofnuts on 2014-01-05
> **spjackson said:**
> In addition to trent.josephsen's remarks, I've marked where I think there are faults in your code. I don't want to explain why at this point, as this is an assignment.

Also one there:
```
sz = fptr[0]
```

---

### Post by Ravi_Chander_Jha on 2014-01-06
Thanz guys the bug is solved now.

resultant codes luks like:-
unsigned long long update = 0;
unsigned long long nactive = 0;
unsigned long long active_size = 0;
unsigned long long ntotal = 0;
unsigned long long total_size = 0;
unsigned long long nfail = 0;
unsigned long long fail_size = 0;
void *m61_malloc(size_t sz, const char *file, int line) {
    size_t *ptr = NULL;
    (void) file, (void) line;   // avoid uninitialized variable warnings
    if(ptr =(size_t*) malloc(sz))
    {
        ptr[0] = sz;
//        printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,ptr[0]);
        ptr += sizeof(size_t);
        nactive++;
        active_size += sz;
        ntotal++;
        total_size += sz;
    }
    else
    {
        nfail++;
        fail_size += sz;
    }
    return ptr;
}


void m61_free(void *ptr, const char *file, int line) {
    (void) file, (void) line;   // avoid uninitialized variable warnings
    // Your code here.
    size_t *fptr = (size_t*) ptr;
    size_t sz;
    if(ptr)
    {
        fptr -= sizeof(size_t);
        sz = fptr[0];
//            printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,sz);
        active_size -= sz;
        nactive--;
        free(fptr);
        return ;
    }
    free(ptr);
}

---

### Post by ofnuts on 2014-01-06
No, you have just replaced it by a set of new ones... your liberal use of size_t is wrong. Fundamentally, when you do:

```

pointer_to_type+=N;

```

C computes

```

pointer_to_type=(pointer_to_type *)(((char *) pointer_to_type)+ N*sizeof(type))

```

Ie, "N" is understood as "as many bytes to fit N times the type".

So when you do:
```

size_t *ptr;
ptr += sizeof(size_t);

```

Your pointer goes a lot farther than you think because the bare address was incremented by size_t * size_t.

---

### Post by Ravi_Chander_Jha on 2014-01-07
Guys now again i have stucked in this code in calloc part:

//m61.c
#define M61_DISABLE 1
#include "m61.h"
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <inttypes.h>
unsigned long long update = 0;
unsigned long long nactive = 0;
unsigned long long active_size = 0;
unsigned long long ntotal = 0;
unsigned long long total_size = 0;
unsigned long long nfail = 0;
unsigned long long fail_size = 0;
void *m61_malloc(size_t sz, const char *file, int line) {
	size_t *ptr = NULL;
	(void) file, (void) line;   // avoid uninitialized variable warnings
	if(sz & 0x80000000)
	{
		nfail++;
		fail_size += (int) sz;
	}
	else if(ptr =(size_t*) malloc(sz + sizeof(size_t)))
	{
		ptr[0] = sz;
//		printf("aaaaaaa%llutttttt%llusssssss%d", active_size,total_size,ptr[0]);
		ptr++;
		nactive++;
		active_size += sz;
		ntotal++;
		total_size += sz;
	}
	else
	{
		nfail++;
		fail_size += sz;
	}
	return ptr;
}


void m61_free(void *ptr, const char *file, int line) {
    (void) file, (void) line;   // avoid uninitialized variable warnings
    // Your code here.
	size_t *fptr = (size_t*) ptr;
	size_t sz;
	if(ptr)
	{
		fptr--;
		sz = fptr[0];
		active_size -= sz;
		nactive--;
		free(fptr);
		return ;
	}
    free(ptr);
}


void *m61_realloc(void *ptr, size_t sz, const char *file, int line) {
	size_t *new_ptr = NULL;
	size_t *ptr1 = (size_t*)ptr;
	size_t old_sz;
	if (sz)
		new_ptr = m61_malloc(sz, file, line);
	if (ptr != NULL && new_ptr != NULL)
	{
		ptr1--;
		old_sz = ptr1[0];
		if (old_sz < sz)
		     memcpy(new_ptr, ptr, old_sz);
		else
		     memcpy(new_ptr, ptr, sz);
	}
    // Oops! In order to copy the data from `ptr` into `new_ptr`, we need
    // to know how much data there was in `ptr`. That requires work.
    // Your code here (to fix test008).
    m61_free(ptr, file, line);
    return new_ptr;
}
	
void *m61_calloc(size_t nmemb, size_t sz, const char *file, int line) {
    // Your code here (to fix test010).
    void *ptr = m61_malloc(nmemb * sz, file, line);
    if (ptr)
        memset(ptr, 0, nmemb * sz);
    return ptr;
}


void m61_getstatistics(struct m61_statistics *stats) {
    // Stub: set all statistics to enormous numbers
	stats->nactive = nactive;
	stats->active_size = active_size;
	stats->ntotal = ntotal;
	stats->total_size = total_size;
	stats->nfail = nfail;
	stats->fail_size = fail_size;
/*	if(update)
	    memset(stats, mstats, sizeof(struct m61_statistics));
	else
	{
	    memset(stats, 0, sizeof(struct m61_statistics));
	    update = 1;
	}*/
    // Your code here.
}


void m61_printstatistics(void) {
    struct m61_statistics stats;
    m61_getstatistics(&stats);


    printf("malloc count: active %10llu   total %10llu   fail %10llu\n",
           stats.nactive, stats.ntotal, stats.nfail);
    printf("malloc size:  active %10llu   total %10llu   fail %10llu\n",
           stats.active_size, stats.total_size, stats.fail_size);
}


void m61_printleakreport(void) {
    // Your code here.
}

****************************************************************************

test010.c

#include "m61.h"
#include <stdio.h>
#include <assert.h>
#include <string.h>
// Diabolical calloc.


int main() {
    size_t very_large_nmemb = (size_t) -1 / 100;
    char *p = (char *) calloc(very_large_nmemb, 101);
    assert(p == NULL);
    m61_printstatistics();
}


//! malloc count: active          0   total          0   fail          1
//! malloc size:  active          0   total          0   fail        ???



my codes are in m61.c

it cant pass test case 10  i.e test010.c

size_t very_large_nmemb = (size_t) -1 / 100; // here very_large_nmemb must be 0 but it is not

please let me know where is the bug.

---

### Post by Ravi_Chander_Jha on 2014-01-07
Please let me know how could i track the intergeral overflow in size_t

---

### Post by spjackson on 2014-01-07
> **Ravi_Chander_Jha said:**
> 
size_t very_large_nmemb = (size_t) -1 / 100; // here very_large_nmemb must be 0 but it is not

I'm not sure I follow everything you are saying. However, why do you think that very_large_nmemb must be 0? The value on the righthand side of the = is not 0, so why would you expect very_large_nmemb to be 0?

---

