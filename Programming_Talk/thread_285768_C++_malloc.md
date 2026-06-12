---
title: "C++ malloc"
date: 2006-10-27
forum: Programming Talk
---

### Post by Lster on 2006-10-27
Hi... Im finding C memory allocation hard to learn.

...

Im really looking to understand both pieces of code. Can anyone explain?

Thanks,
Lster

---

### Post by amo-ej1 on 2006-10-27
C allows you to do certain things that aren't right, this is the advantage of C you have a lot of freedom and you might be allowed to do some things that look wrong at first but are correct in the environment/hardware.

But what you did is wrong, in your first example malloc returns a pointer. And since it's a pointer you can easily write to it, this is what you do with strcpy, you place data in a location but you place much more data in it than which you actually reserved (since you reserver nothing :D) BUT this means you are potentially messing up some other part of your memory which can be used by anything, another variable ? your stack ? .... 

So if you first example worked as your suspected, you were lucky ;) and the same goes for your second example. But code like that will break eventually.

---

### Post by Lster on 2006-10-27
...

---

### Post by shining on 2006-10-27
That would be better, assuming the x value you choose is big enough.

By the way, I see C++ in the thread name, but the code you pasted looks very much like C. Maybe you should correct the thread name?

If it's C you're willing to learn, I would suggest getting a book, like The C Programming Language, from the C authors (Kernighan & Ritchie):
[http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628)

---

### Post by tzulberti on 2006-10-27
In C++ you could use new
char* pChar;
pChar = new char...
This take take of the sizeof, which is simplier than malloc... For deleting you could use delete
delete pChar;

---

### Post by amo-ej1 on 2006-10-29
In C++:

alloc a single variable:

```

int * p;
p = new int;
delete p;

```

And alloc a multiple instances of the same type (an array)

[CODE]
int * p;
p = new int[10];
delete [] p;
[CODE}
allocates an array of 10 integers pointed to by p. Mind the extra  []'s before the delete.

---

