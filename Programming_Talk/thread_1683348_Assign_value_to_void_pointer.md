---
title: "Assign value to void pointer?"
date: 2011-02-07
forum: Programming Talk
---

### Post by Pithikos on 2011-02-07
How can you assign a value to a void pointer? My teacher has an [example]("http://www8.cs.umu.se/kurser/5DV108/VT11/ex_queue/") but I can't make sense of it(poor commentation I should say). Here is part of the code:

```
typedef void *datapointer;

typedef struct
{  
   int start;
   int stop;
   int size;
   datapointer data[128];
} queue_t;
```I guess this is an array of 128 void pointers. Is that correct?
From the main.c:
```
queue_t *min_ko=queue_empty();
int *ip=malloc(sizeof(int));
*ip=1;
queue_enqueue(min_ko,ip);
```And here is what queue_enqueue does which I have a really hard time understanding(mostly because of the "->" notation):
```
void queue_enqueue(queue_t *q, datapointer p) {
   if(q->size >= 128) abort();
   q->size++;
   q->stop = (q->stop+1)%128;
   q->data[q->stop] = p;
}
```This program compiles perfect. 
I tryied making my own testing program which gives me warnings:

```
int main() {
    void* data;
    int *int_p=malloc(8);
    *int_p=10;
    *data=*int_p;
    return 0;
}
```

---

### Post by schauerlich on 2011-02-07
I'm going to assume you have a basic understanding of pointers and structs.

You normally access a struct with dot-notation, like so:

```
typedef struct {
  int bar;
} foo_t;

int main(void) {
  foo_t foo;
  foo.bar = 10;

  return 0;
}
```

All the '->' syntax is is a shorthand for dealing with pointers to structs. When you use '->' on a pointer, it dereferences the pointer first, and then accesses the member you specify of the resulting struct.

```
foo.bar = 10;
```

is equivalent to

```
foo_t *blah = &foo;
blah->bar = 10;
```

or

```
(*blah).bar = 10;
```

Now, void pointers. Every pointer in C must have a type. Well, that's not quite accurate. When you DEREFERENCE a pointer, it must have a type. All a void pointer is, is a pointer that doesn't have any "built in" type. At any point, you can make it a pointer to any type just by casting it. However, you can't directly dereference a void pointer - it doesn't have a type. You have to give it a type before you dereference it. In your example, you have to cast the "data" pointer to an int pointer in the assignment, like so:

```
*(int *)data = *int_p;
```

The nifty thing about void pointers is that they let you be generic in certain circumstances. That is, as long as you never try to dereference the void pointer without casting, it can store any pointer value during its lifetime. You'll notice in the queue implementation, the void pointers are never dereferenced by his code - only copied around, which is perfectly valid. It's up to the user of his queue struct to make sure the pointers it returns have a type when they're dereferenced.

---

### Post by schauerlich on 2011-02-07
Also: void pointer don't really let you do anything you couldn't with a normal pointer. Since any pointer type can be cast to any other pointer type, you could just replace every void pointer with a char pointer and get the same effect. The biggest difference is that when you use void pointers, the compiler will warn you if you don't cast them before dereferencing. If you use char pointers instead, the compiler will silently assume you want to dereference to a char even if that's not what you meant.

---

### Post by Pithikos on 2011-02-07
Thanks a lot for your answer(s)! That cleared things a lot :rolleyes:
The code:
```
*(int *)data = *int_p;
```
didn't work though and  I came to the conclusion that I didn't have allocated memory for it to copy the values so instead I copied the pointers:
```
data=int_p;
```
and it worked. 

But I still wonder about something.. When I copied the pointer int_p to pointer data did the latter still remain a void pointer? Can't I change it's type once and for all even if I initially declared it as a void pointer? Do I have to use casting in every line when I want to change or show the value(I guess that's what you mean with dereference) where the pointer points to? Because that makes the code quite bulky.

---

### Post by worksofcraft on 2011-02-07
> **Pithikos said:**
> Thanks a lot for your answer(s)! That cleared things a lot :rolleyes:
The code:
```
*(int *)data = *int_p;
```
didn't work though and  I came to the conclusion that I didn't have allocated memory for it to copy the values so instead I copied the pointers:
```
data=int_p;
```
and it worked. 

But I still wonder about something.. When I copied the pointer int_p to pointer data did the latter still remain a void pointer? Can't I change it's type once and for all even if I initially declared it as a void pointer? Do I have to use casting in every line when I want to change or show the value(I guess that's what you mean with dereference) where the pointer points to? Because that makes the code quite bulky.

I think it is best to declare pointers of the correct type to start with then you won't have to cast it anywhere. I don't think I used a void pointer for years ;)

p.s. simply by changing that first typedef you can make it use int pointers everywhere:
```

typedef int *datapointer

```

---

### Post by schauerlich on 2011-02-07
> **Pithikos said:**
> Thanks a lot for your answer(s)! That cleared things a lot :rolleyes:
The code:
```
*(int *)data = *int_p;
```
didn't work though and  I came to the conclusion that I didn't have allocated memory for it to copy the values so instead I copied the pointers:
```
data=int_p;
```
and it worked. 

There's a big difference between those two things. The first one copies *the value 'int_p' points to* to *the location 'data' points to*. The second make it so that 'data' now points to the same location as 'int_p'. Two very different things.

> But I still wonder about something.. When I copied the pointer int_p to pointer data did the latter still remain a void pointer? Can't I change it's type once and for all even if I initially declared it as a void pointer? Do I have to use casting in every line when I want to change or show the value(I guess that's what you mean with dereference) where the pointer points to? Because that makes the code quite bulky.

In most cases, you should avoid using void pointers. You almost always want a pointer of a specific type. The most common situations where you would use void pointers are both in your original post: a function that returns a pointer to a generic chunk of memory whose type doesn't matter (malloc), and a data structure that can hold a pointer to any data type. If you're familiar with C++, you'd use void pointers in a lot of the same situations as templates. Templates just make it so you don't have to cast so much.

---

### Post by trent.josephsen on 2011-02-07
> **schauerlich said:**
> Also: void pointer don't really let you do anything you couldn't with a normal pointer. Since any pointer type can be cast to any other pointer type, you could just replace every void pointer with an int pointer and get the same effect. The biggest difference is that when you use void pointers, the compiler will warn you if you don't cast them before dereferencing. If you use int pointers instead, the compiler will silently assume you want to dereference to an int even if that's not what you meant.
N.B. pointer-to-int is not a drop-in replacement for pointer-to-void on systems with stricter alignment requirements for int than char -- which is most of them.

Pre-ANSI, pointer-to-char was used as the generic pointer type, because char has no alignment requirements; pointers-to-void were introduced in C89.

---

### Post by schauerlich on 2011-02-07
> **trent.josephsen said:**
> N.B. pointer-to-int is not a drop-in replacement for pointer-to-void on systems with stricter alignment requirements for int than char -- which is most of them.

Pre-ANSI, pointer-to-char was used as the generic pointer type, because char has no alignment requirements; pointers-to-void were introduced in C89.

Right. Updated my earlier post. :)

---

