---
title: "free()ing multidimensional arrays"
date: 2006-10-11
forum: Programming Talk
---

### Post by cronholio on 2006-10-11
I initialize a 2-dimensional array using this function (the array is global):

```
#define PIXEL unsigned char

void init_img(int xm, int ym) {
  int i;
  img=(PIXEL**) calloc(sizeof(PIXEL*), ym);
  if (img==NULL) {
          fprintf(stderr, "Out of memory.\n");
          exit(-1);
  }
  for(i=0; i<ym; i++)
  {
    img[i]=(PIXEL*) calloc(sizeof(PIXEL), xm);
    if(img[i]==NULL) {
            fprintf(stderr, "Out of memory.\n");
            exit(-1);
    }
  }
}
```

Okay, now when I free() it, I first free() the column pointers and then the array itself:

```
void free_img(ym) {
  int i;
  for(i=0; i<ym; i++) free(img[i]);
  free(img);
}
```

The weird thing is that code like this

```
init_img(some_value, some_other_value);
free_img(some_other_value);
```

returns a glibc error "free(): Invalid next size" at runtime (during the for loop of free_img). "some_value" obviously is the number of elements in an array row that I want to use. However, the error does not appear if I add something to this value, so I allocate more space per row than needed:

```
init_img(some_value+8, some_other_value);
free_img(some_other_value);
```

Does anyone have a clue as to why this happens? The row size shouldn't have anything to do with it, so this error seems pretty strange to me. AFAIK, "invalid next size" is the confusing way of glibc to tell me that I am trying to mess with non-allocated space.

---

### Post by Guido Loupias on 2006-10-11
EDIT: disregard what I'm saying in this post... I wasn't reading properly...

Try narrowing down the bug. i.e. does it continue to give
you the error when you comment out the *free(img)* function call?

Try this and running the program again:

```
void free_img(ym) {
  int i;
  for(i=0; i<ym; i++) free(img[i]);
  /*free(img);*/
}
```

---

### Post by cronholio on 2006-10-11
No, I am sure it is part of the for loop. I don't get an error if I comment it out:

> void free_img(ym) {
  int i;
  //for(i=0; i<ym; i++) free(img[i]);
  free(img);
}

---

### Post by MWAAAHAAA on 2006-10-11
1. You really should consider using wrapper functions for *alloc, which will do the NULL checking for you, it makes your code much more legible (xmalloc, xcalloc, and xrealloc are commonly used for this purpose).

2. From my manual page:

void *calloc(size_t nmemb, size_t size);

Your usage of calloc is reversed, as you substitute the size of a PIXEL* for the nmemb (number of members), and the number of PIXEL* for the size (size of each member).

3. I tried running the following:

```

#include <stdio.h>
#include <stdlib.h>

#define PIXEL unsigned char

PIXEL **img;

void init_img(int xm, int ym) {
  int i;
  img=(PIXEL**) calloc(sizeof(PIXEL*), ym);
  if (img==NULL) {
          fprintf(stderr, "Out of memory.\n");
          exit(-1);
  }
  for(i=0; i<ym; i++)
  {
    img[i]=(PIXEL*) calloc(sizeof(PIXEL), xm);
    if(img[i]==NULL) {
            fprintf(stderr, "Out of memory.\n");
            exit(-1);
    }
  }
}

void free_img(ym) {
  int i;
  for(i=0; i<ym; i++) free(img[i]);
  free(img);
}

int
main(int argc, char **argv)
{
	init_img(100, 200);
	free_img(200);
	
	return 0;
}

```

Which runs perfectly fine on my system. Are you doing something else with your 'img' between calls to init_img and free_img? What is your setup? What compiler and library version are you running?

4. You might want to try a C specific forum, such as the ones provided at cprogramming.com.

---

### Post by pragmatine on 2006-10-11
You are passing the parameters to calloc in the wrong order:

From ```
man 3 calloc
```:
```
void *calloc(size_t nmemb, size_t size);

 calloc()  allocates memory for an array of nmemb elements of size bytes
 each and returns a pointer to the allocated memory. 
```

---

### Post by cronholio on 2006-10-11
> 1. You really should consider using wrapper functions for *alloc, which will do the NULL checking for you, it makes your code much more legible

Actually my program was supposed to be for the Obfuscated C Contest. :D
No, seriously, it's probably a good idea.

> Your usage of calloc is reversed

You are right, I changed it. Shouldn't matter though since the 2 values are multiplied anyway.

> Which runs perfectly fine on my system.

If I copy and paste this code, it runs without error on my machine as well. I use GCC 4.0.3 and Glibc 1.2.10.

> Are you doing something else with your 'img' between calls to init_img and free_img?

Basically I'm loading image data and manipulate it. The reason must lie between the 2 calls obviously, because if I don't do anything in between, I don't get an error. Unfortunately what I'm doing is far too much to post here, so I'll try to narrow it down a little further.

It's confusing for me though because I can't see how anything that I'm doing between those calls could be the cause of this error - it's basically just array data reads and writes.

---

### Post by cronholio on 2006-10-11
@pragmatine: Thanks, MWAAAHAAA pointed it out before and I changed it.

---

### Post by Guido Loupias on 2006-10-11
Then I guess the error is somewhere else in your program.
Another function that corrupts the data while manipulating it.

---

### Post by cronholio on 2006-10-12
I found the error: I was writing more bytes per row than allocated. But still I am wondering why I get this message when calling free() in the end. Shouldn't the program already fail at the time I address unallocated space? :-k

---

### Post by po0f on 2006-10-12
cronholio,

The program might crash immediately after writing to unallocated memory.  It can also lead to weird bugs that have no explanation.  You were lucky enough to catch this bug early in development (or maybe not so early).  ;)

---

### Post by Arndt on 2006-10-12
> **cronholio said:**
> I found the error: I was writing more bytes per row than allocated. But still I am wondering why I get this message when calling free() in the end. Shouldn't the program already fail at the time I address unallocated space? :-k

Not "should"; there is no way to be sure what happens when you write to unallocated memory. In this case, what happened was probably that the bookkeeping data kept in the allocated block (near the end or beginning of it) was corrupted, and so 'free' noticed it, but no other parts of your code.

A really good tool to use is 'valgrind'. It tells you when the program does illegal memory operations, among other things. It's very easy to use.

---

