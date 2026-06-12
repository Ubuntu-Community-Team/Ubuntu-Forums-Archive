---
title: "Recording a list of values in C"
date: 2010-09-19
forum: Programming Talk
---

### Post by nair on 2010-09-19
Just a quick question regarding the C programming language:

How do you record or create a list of the values that an integer or char has been equal to, (almost like a historical log)?  Would you record a list like that in an array?  If so, how?

---

### Post by schauerlich on 2010-09-19
Make an array of some sufficiently large size (guess, unless you want to get into manual memory management which is a pain) and push it onto the next open spot of the array before you change it.

```
#include <stdio.h>

int main(void) {
  int foo = 0;
  int i;
  int past_values[20];
  int *next_open = &past_values[0];

  for (i = 1; i <= 20; i++) {
    *next_open = foo;
    next_open++;

    foo += i;
  }

  for (i = 0; i < 20; i++)
    printf("%d\n", past_values[i]);

  return 0;
}

```

---

### Post by worksofcraft on 2010-09-20
I would use a linked list. One can simply keep adding new entries to the linked list as required. Here is some very primitive C code to do a linked list. It can be done much neater with the standard template library in C++, but if you want some help with linked lists you only have to ask ;)

```

#include <stdio.h>
#include <stdlib.h>

struct link {
	link * Next;
	int Record;
};

int main() {
	link * List = NULL;

	for (int i = 1964; i < 2010; ++i) {
		link * L = (link *) malloc(sizeof(link)); // bug fixed now

		L->Next = List;
		L->Record = i;
		List = L;
	}

	link * I = List;
	while (I) {
		printf("%d, been there, done that!\n", I->Record);
		I = I->Next;
	}

	return EXIT_SUCCESS;
}

```

---

### Post by Some Penguin on 2010-09-20
> **nair said:**
> Just a quick question regarding the C programming language:

How do you record or create a list of the values that an integer or char has been equal to, (almost like a historical log)?  Would you record a list like that in an array?  If so, how?

Depends on how you're planning on using the data, and how much you'll have.  It's likely not worth doing anything fancy if you're storing just the last 100 values (a simple circular buffer makes sense), but if you need to store a few million previous values and be able to efficiently access arbitrarily far back, then it's worth actually putting time into design.

---

### Post by schauerlich on 2010-09-20
> **worksofcraft said:**
> ```
sizeof(L)
```

should be 

```
sizeof(link)
```

L is a link*, not link.

---

### Post by worksofcraft on 2010-09-20
> **schauerlich said:**
> should be 

```
sizeof(link)
```

L is a link*, not link.
Oops, indeed! Well spotted :shock:

so yes like schauerlich says: It **is** best to allocate the correct amount of memory for each link and not just for a pointer to one. Sometimes it's easy to goof in C, but it was only meant to give an idea of how linked lists work :)

---

### Post by nair on 2010-09-21
None of the example code posted compiles for me, but I believe it has got me thinking in the right direction.

@some penguin.  I am interested in first learning how to handle 100 more than I am 2 million, since I don't know how to do either at the moment (or I haven't gotten them working, rather).  When you refer to a circular buffer, is that basically like an array that, once it is full, starts over from the beginning to rewrite over the elements that it first put there?  It sounds like a very useful concept--from what I briefly read on wiki.  I'd never heard of it until now.

---

### Post by worksofcraft on 2010-09-22
> **nair said:**
> None of the example code posted compiles for me...

z0mg... it should :shock:
```

$> g++ link.c
$> ./a.out
2009, been there, done that!
2008, been there, done that!
... etcetera

```

---

### Post by unknownPoster on 2010-09-22
> **worksofcraft said:**
> z0mg... it should :shock:
```

$> g++ link.c
$> ./a.out
2009, been there, done that!
2008, been there, done that!
... etcetera

```

No it shouldn't, not when compiled with gcc. It's not valid ansi 99 C.

I've posted the corrected code:

```



#include <stdio.h>
#include <stdlib.h>

typedef struct link{
        struct link * Next;
        int Record;
} link;

int main() {
        link * List = NULL;
        int i = 0;
        for (i = 1964; i < 2010; ++i) {
                link * L = (link *) malloc(sizeof(link)); /* bug fixed now */

                L->Next = List;
                L->Record = i;
                List = L;
        }

        link * I = List;
        while (I) {
                printf("%d, been there, done that!\n", I->Record);
                I = I->Next;
        }

        return EXIT_SUCCESS;
}

```

---

### Post by Some Penguin on 2010-09-22
> **nair said:**
> None of the example code posted compiles for me, but I believe it has got me thinking in the right direction.

@some penguin.  I am interested in first learning how to handle 100 more than I am 2 million, since I don't know how to do either at the moment (or I haven't gotten them working, rather).  When you refer to a circular buffer, is that basically like an array that, once it is full, starts over from the beginning to rewrite over the elements that it first put there?  It sounds like a very useful concept--from what I briefly read on wiki.  I'd never heard of it until now.


*shrug*  Wasn't sure what your use case is.  Learning != industrial scale, which is perfectly fine.

Circular buffers basically are that -- they're normally implemented with an array and an index.  The index just gets incremented (modulo the array length, so it wraps around) as you write more items into it.  I mentioned it because while it's obviously a poor choice for keeping a *complete* history, it's a pretty reasonable choice if what you care about is recent history.  Mind you, you also need a way to distinguish between never-written slots; for C, a simple approach would be to set a boolean flag the first time it wraps around.  If it's wrapped around, every slot has a valid value, and if not, whatever's before the index is valid and everything else isn't.  In a multithreaded system you also need to care about race conditions, but it's entirely likely that you're not using multiple threads.

---

