---
title: "Help with Valgrind's output."
date: 2011-07-06
forum: Programming Talk
---

### Post by Rany Albeg on 2011-07-06
Hello all,
I'm using Valgrind to test a short program I just wrote.
Valgrind say that there are not memory leaks and that the heap summary is fine, which is what I was looking for to see, but it also output some other descriptions starting with "Invalid read of size 1", as you can see here at the full output:
```

==5950== Memcheck, a memory error detector
==5950== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==5950== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==5950== Command: ./test
==5950== 
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x804859D: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b0a6 is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x8048707: vector_add (in /home/rany/Desktop/vectest/test)
==5950==    by 0x8048551: main (in /home/rany/Desktop/vectest/test)
==5950== 
size of hello0 is 6
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x80485CB: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b11e is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x8048707: vector_add (in /home/rany/Desktop/vectest/test)
==5950==    by 0x8048575: main (in /home/rany/Desktop/vectest/test)
==5950== 
size of hello1 is 6
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x80485F4: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b18e is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x80487B9: vector_remove (in /home/rany/Desktop/vectest/test)
==5950==    by 0x80485D7: main (in /home/rany/Desktop/vectest/test)
==5950== 
hello1 has being removed from the vector.
==5950== 
==5950== HEAP SUMMARY:
==5950==     in use at exit: 0 bytes in 0 blocks
==5950==   total heap usage: 7 allocs, 7 frees, 62 bytes allocated
==5950== 
==5950== All heap blocks were freed -- no leaks are possible
==5950== 
==5950== For counts of detected and suppressed errors, rerun with: -v
==5950== ERROR SUMMARY: 3 errors from 3 contexts (suppressed: 12 from 7)
```

I need help understanding that repeating output.
Thank you.

---

### Post by JupiterV2 on 2011-07-06
Without seeing the code in question, I'd have to guess you're checking the status of a variable, perhaps checking for NULL, after freeing the memory allocated to the variable. Did you compile your program with -g to enable debug symbols? Usually valgrind will print out the line number the code is executed from (like with the standard library functions in the output you supplied). A snippet of the code causing the error would help.

---

### Post by Arndt on 2011-07-06
> **Rany Albeg said:**
> Hello all,
I'm using Valgrind to test a short program I just wrote.
Valgrind say that there are not memory leaks and that the heap summary is fine, which is what I was looking for to see, but it also output some other descriptions starting with "Invalid read of size 1", as you can see here at the full output:
```

==5950== Memcheck, a memory error detector
==5950== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==5950== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==5950== Command: ./test
==5950== 
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x804859D: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b0a6 is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x8048707: vector_add (in /home/rany/Desktop/vectest/test)
==5950==    by 0x8048551: main (in /home/rany/Desktop/vectest/test)
==5950== 
size of hello0 is 6
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x80485CB: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b11e is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x8048707: vector_add (in /home/rany/Desktop/vectest/test)
==5950==    by 0x8048575: main (in /home/rany/Desktop/vectest/test)
==5950== 
size of hello1 is 6
==5950== Invalid read of size 1
==5950==    at 0x407F50B: vfprintf (vfprintf.c:1614)
==5950==    by 0x408615F: printf (printf.c:35)
==5950==    by 0x80485F4: main (in /home/rany/Desktop/vectest/test)
==5950==  Address 0x419b18e is 0 bytes after a block of size 6 alloc'd
==5950==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==5950==    by 0x80487B9: vector_remove (in /home/rany/Desktop/vectest/test)
==5950==    by 0x80485D7: main (in /home/rany/Desktop/vectest/test)
==5950== 
hello1 has being removed from the vector.
==5950== 
==5950== HEAP SUMMARY:
==5950==     in use at exit: 0 bytes in 0 blocks
==5950==   total heap usage: 7 allocs, 7 frees, 62 bytes allocated
==5950== 
==5950== All heap blocks were freed -- no leaks are possible
==5950== 
==5950== For counts of detected and suppressed errors, rerun with: -v
==5950== ERROR SUMMARY: 3 errors from 3 contexts (suppressed: 12 from 7)
```

I need help understanding that repeating output.
Thank you.

In my experience, some of the functions in the C library cause these errors. I don't know if they are really errors, and I haven't investigated them, but it's possible to tell valgrind to ignore certain functions.

---

### Post by Rany Albeg on 2011-07-07
Hi, thanks for the feedbacks.
I read here [http://www.cprogramming.com/debugging/valgrind.html](http://www.cprogramming.com/debugging/valgrind.html) , under "Finding Invalid Pointer Use With Valgrind" that the reason to this error is because I'm trying to read 1 units past the allowed amount of memory.

In my program I use two structs in order to represent a vector;

```
typedef struct _vobj
{
	void* data;
	size_t data_size;

} vobj_t;

typedef struct _rds_vector
{
	vobj_t* objs;
	size_t size;
	size_t vp;

} rds_vector_t;
```

And I find that by removing this line from main.c:
```
printf("%s\n", (char*)vec->objs[i].data);
```

the problem disappears.

(Assume that void* data points to a some constant string)

---

### Post by JupiterV2 on 2011-07-07
> **Rany Albeg said:**
> Hi, thanks for the feedbacks.
I read here [http://www.cprogramming.com/debugging/valgrind.html](http://www.cprogramming.com/debugging/valgrind.html) , under "Finding Invalid Pointer Use With Valgrind" that the reason to this error is because I'm trying to read 1 units past the allowed amount of memory.

In my program I use two structs in order to represent a vector;

```
typedef struct _vobj
{
	void* data;
	size_t data_size;

} vobj_t;

typedef struct _rds_vector
{
	vobj_t* objs;
	size_t size;
	size_t vp;

} rds_vector_t;
```

And I find that by removing this line from main.c:
```
printf("%s\n", (char*)vec->objs[i].data);
```

the problem disappears.

(Assume that void* data points to a some constant string)

Unfortunately, without seeing the loop in which your printf() occurs it's hard to help you. My guess is that either you've allocated less memory than you think or your loop is flawed and tries to read one more block of memory than it should.

---

### Post by Bachstelze on 2011-07-07
Are you certain that the strings pointed to by data are always NULL-terminated?

---

### Post by Rany Albeg on 2011-07-07
> Unfortunately, without seeing the loop in which your printf() occurs it's hard to help you. My guess is that either you've allocated less memory than you think or your loop is flawed and tries to read one more block of memory than it should.

This is the loop
```
for(i=0;i<vec->vp;++i)
{
    printf("%s\n",(char*)vec->objs[i].data);
}
```

But, I get same error even if I just printf a single element, say at index 0
```

printf("%s\n",(char*)vec->objs[0].data);
```

---

> Are you certain that the strings pointed to by data are always NULL-terminated?

I guess they are.
This is the function that adds a new object to the vector:

```
void rds_vector_add(rds_vector_t* vec, void* obj, size_t obsize)
{
	if (rds_vector_isfull(vec))
		rds_vector_amortization(vec);

	if((vec->objs[vec->vp].data = malloc(obsize)) == NULL)
		rds_vector_failure(__FILE__, __LINE__, "malloc failed.");

	vec->objs[vec->vp].data_size = obsize;

	memcpy(vec->objs[vec->vp++].data, obj, obsize);
	return;
}
```

And this is how I call it from main.c:
```

rds_vector_add(vec, "hello0", 6);
```

Thank you.

---

### Post by Bachstelze on 2011-07-07
"hello0" is 6 characters. In order to store it plus the terminating null byte, you need to allocate 7 bytes.

Alternatively, since you know the size of the data, you could create a print fonction that only prints the n first bytes of the string, but you can't use printf with just %s, because it expects a terminating NULL byte and will continue reading until it finds one.

---

### Post by Rany Albeg on 2011-07-07
Thank you, this certainly clarifies the problem.
And yes, if I call 'rds_vector_add' with a third parameter equals to 7 Valgrind doesn't give the "Invalid read of size 1" error.

But this is something you should not do in terms of user comfort.
I do not want the client to figure this out by himself and pass a value that is bigger in 1 unit.

So, yes of course I can just simply allocate the requested size + 1 behind the scenes, inside my 'add' function, but will it be reasonable if the actual data is of type void*  ?
```
rds_vector_add(rds_vector_t* vec, **void* obj**, size_t obsize)
```

Thanks again for the help!

---

### Post by Bachstelze on 2011-07-07
> **Rany Albeg said:**
> 
So, yes of course I can just simply allocate the requested size + 1 behind the scenes, inside my 'add' function, but will it be reasonable if the actual data is of type void*  ?

Certainly. Just add +1 in your malloc call. However, will the data always be a string, or can it be any kind of data? If it is always a string, you can omit passing the size altogether and calculate it with strlen:

```
void rds_vector_add(rds_vector_t* vec, void* obj)
{
	if (rds_vector_isfull(vec))
		rds_vector_amortization(vec);

        int obsize = strlen(obj)+1;
	if((vec->objs[vec->vp].data = malloc(obsize)) == NULL)
		rds_vector_failure(__FILE__, __LINE__, "malloc failed.");

	vec->objs[vec->vp].data_size = obsize;

	strncpy(vec->objs[vec->vp++].data, obj, obsize);
	return;
}
```

If however the data can be any kind of data, you will have a problem because you will need to add a terminating NULL byte for strings if you want to print them with printf("%s"), but it may not be desirable to add it if it is some other data.

---

### Post by Rany Albeg on 2011-07-07
I see,
So for conclusion I understand that there is no way to make a generic code both for strings and other data types that will implement 'rds_vecotor_add' ?

I think I should choose another language for this purpose.
C++ maybe, and write a template class.

Thank you very much for your help, I appreciate it very much.
Have a good weekend.

---

### Post by Bachstelze on 2011-07-07
> **Rany Albeg said:**
> I see,
So for conclusion I understand that there is no way to make a generic code both for strings and other data types that will implement 'rds_vecotor_add' ?

Not at all, you can copy a string like any other data as you did first, but then you can't print it with printf("%s").  Basically you can't have it both ways: if you want your code to be able to handle any kind of data, then you can't use things like %s that work only on strings.

---

### Post by Rany Albeg on 2011-07-07
Bachstelze,
You've been very helpful.
Thank you.

---

