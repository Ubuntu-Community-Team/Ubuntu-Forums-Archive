---
title: "[SOLVED] [C] Understanding a valgrind report"
date: 2008-06-13
forum: Programming Talk
---

### Post by nvteighen on 2008-06-13
Hi there!
Can you please clarify me something in this valgrind report I got? Is valgrind really telling me what function is leaking memory? I ask this because, no matter how many times I re-read my code, I don't find where the issue might be. So, I hope valgrind makes my life a bit easier (err... please don't tell me to forget C and go for Python... :))

Thanks!

```

ugi@UGI:~/Escritorio/bigint$ valgrind --leak-check=full ./test
==11367== Memcheck, a memory error detector.
==11367== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==11367== Using LibVEX rev 1804, a library for dynamic binary translation.
==11367== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==11367== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==11367== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==11367== For more details, rerun with: -v
==11367== 
1
99
==11367== Invalid read of size 1
==11367==    at 0x804888F: bigint_add (math.c:34)
==11367==    by 0x8048A25: main (test.c:17)
==11367==  Address 0x4185069 is 0 bytes after a block of size 1 alloc'd
==11367==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==11367==    by 0x804850B: bigint_cont_alloc (memory.c:13)
==11367==    by 0x8048636: bigint_set (memory.c:63)
==11367==    by 0x80489BB: main (test.c:6)
==11367== 
==11367== Invalid free() / delete / delete[]
==11367==    at 0x402265C: free (vg_replace_malloc.c:323)
==11367==    by 0x80487F2: resize_cont (math.c:13)
==11367==    by 0x8048956: bigint_add (math.c:45)
==11367==    by 0x8048A25: main (test.c:17)
==11367==  Address 0x4185158 is 0 bytes inside a block of size 2 free'd
==11367==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==11367==    by 0x80487D2: resize_cont (math.c:8)
==11367==    by 0x8048956: bigint_add (math.c:45)
==11367==    by 0x8048A25: main (test.c:17)
100
==11367== 
==11367== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 11 from 1)
==11367== malloc/free: in use at exit: 15 bytes in 2 blocks.
==11367== malloc/free: 7 allocs, 6 frees, 44 bytes allocated.
==11367== For counts of detected errors, rerun with: -v
==11367== searching for pointers to 2 not-freed blocks.
==11367== checked 60,652 bytes.
==11367== 
==11367== 
==11367== 15 (12 direct, 3 indirect) bytes in 1 blocks are definitely lost in loss record 2 of 2
==11367==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==11367==    by 0x8048581: bigint_new (memory.c:36)
==11367==    by 0x8048A09: main (test.c:16)
==11367== 
==11367== LEAK SUMMARY:
==11367==    definitely lost: 12 bytes in 1 blocks.
==11367==    indirectly lost: 3 bytes in 1 blocks.
==11367==      possibly lost: 0 bytes in 0 blocks.
==11367==    still reachable: 0 bytes in 0 blocks.
==11367==         suppressed: 0 bytes in 0 blocks.

```

---

### Post by Zugzwang on 2008-06-13
```

==11367== Invalid read of size 1
==11367==    at 0x804888F: bigint_add (math.c:34)
==11367==    by 0x8048A25: main (test.c:17)
==11367==  Address 0x4185069 is 0 bytes after a block of size 1 alloc'd
==11367==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==11367==    by 0x804850B: bigint_cont_alloc (memory.c:13)
==11367==    by 0x8048636: bigint_set (memory.c:63)
==11367==    by 0x80489BB: main (test.c:6)

```

Ok, this means that you are trying to access a memory location you shouldn't. For example:
```

char *foo = malloc(sizeof(char)*1);
foo[0] = 'H';
char bar = foo[1];

```

The location in your code at which you are accessing this region of memory is (math.c:34). The place at which you malloc'ed the memory is (vg_replace_malloc.c:207). There's also the call stack for both cases which might be important for you.

```

==11367== Invalid free() / delete / delete[]
==11367==    at 0x402265C: free (vg_replace_malloc.c:323)
==11367==    by 0x80487F2: resize_cont (math.c:13)
==11367==    by 0x8048956: bigint_add (math.c:45)
==11367==    by 0x8048A25: main (test.c:17)
==11367==  Address 0x4185158 is 0 bytes inside a block of size 2 free'd
==11367==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==11367==    by 0x80487D2: resize_cont (math.c:8)
==11367==    by 0x8048956: bigint_add (math.c:45)
==11367==    by 0x8048A25: main (test.c:17)

```

Ok, this tells you that you are freeing a piece of memory that has already been freed. The messages tell you where that happened.

---

### Post by nvteighen on 2008-06-13
> **Zugzwang said:**
> (...)
Ok, this means that you are trying to access a memory location you shouldn't. For example:
```

char *foo = malloc(sizeof(char)*1);
foo[0] = 'H';
char bar = foo[1];

```

The location in your code at which you are accessing this region of memory is (math.c:34). The place at which you malloc'ed the memory is (vg_replace_malloc.c:207). There's also the call stack for both cases which might be important for you.

Yes, actually the issue is like that, caused by some rewrite I did today... Thank you: I know which variable is being accessed out of its bounds, so I should solve this easily.

> (...)

Ok, this tells you that you are freeing a piece of memory that has already been freed. The messages tell you where that happened.

Here I am a bit confused. This is the code of the function (it increases the size of an allocated block):
[PHP]
/*Copied from header file*/
typedef struct
{
	char sign;
	size_t size;
	char *cont; /*"cont", for "content"*/
} bigint;
/*End header snippet*/

/*math.c snippet*/
static char resize_cont(bigint *num, size_t size)
{
	char *cont_buf = (char *)realloc(num->cont, size);

	if(cont_buf == NULL)
		return 1;
	
	free(num->cont); /*Double free?*/
	num->cont = cont_buf;

	num->size = size;

	return 0;
}
/*End snippet*/
[/PHP]

Does realloc()+free() has something to do there? The problem is that if I remove that free(), I get more memory leaked.

For the curious, this a big integers library... The math.c module is where mathematical operations are defined. I need that resizing function for scenarios like 9+1=10, where both sumands are 1-digit long but the result is 2-digit long. In a remote way, I'm somehow emulating C++ vectors.

---

### Post by raul_ on 2008-06-13
You're realloc'ing something that hasn't been alloc'ed before. I think that's the problem. Try malloc or calloc instead.

What a realloc does is alloc'ing new space, copy the contents to the new space, and free the old one  (I think, but I don't know hot it works with contiguous memory blocks and those kind of things).

Since you didn't malloc anything, realloc is doing an invalid free

---

### Post by nvteighen on 2008-06-13
> **raul_ said:**
> You're realloc'ing something that hasn't been alloc'ed before. I think that's the problem. Try malloc or calloc instead.

What a realloc does is alloc'ing new space, copy the contents to the new space, and free the old one  (I think, but I don't know hot it works with contiguous memory blocks and those kind of things).

Since you didn't malloc anything, realloc is doing an invalid free

Yes, it is malloc'ed, but somewhere else... in other module. In that function, *num is a pointer to some already allocated memory. realloc() is fine: just I didn't know that it free's memory for you. Thanks!

By the way, the memory leak is solved. I was forgetting a free() in the **test suit**!!! (...not the library...) :oops:

So, anything now is reduced to the invalid access, which is easy to solve (I think). If any doubt, I'll ask again.

Thank you all!

---

