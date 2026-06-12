---
title: "C question"
date: 2011-02-14
forum: Programming Talk
---

### Post by Peter76 on 2011-02-14
Hello,

I'm studying a C book at the moment and as an example there is this addressbook app. The following is in the headerfile:

```

typedef struct {
	char *name;
	char *address;
} Person;

Person* AllocPerson();
```

What i don't understand is what the asterisk does or means in ```
Person* AllocPerson();
```.

Can someone enlighten me on this?

Thanks in advance.

---

### Post by cgroza on 2011-02-14
That asterix is the syntax used to create a pointer. Read about pointers in C.

---

### Post by johnl on 2011-02-14
Has your book covered pointers yet?  In a variable declaration, an asterisk means that the variable is a pointer.

e.g.

```

int* a; /* a is a pointer to an int */
int *a, b, *c; /* a and c are pointers to an int, b is an int */

``` 

In your case, you have declared a function named **AllocPerson** with a return type of **pointer to a Person**.

If your book hasn't covered pointers yet, the gist of it is this:  a pointer is a variable that holds a memory address.  When you **dereference** a pointer, you retrieve the value at the memory address the pointer 'points to.'

e.g.,

```

int num = 10;
int* ptr = &value;  /* &num means 'address of num'. so store the 
                       memory address of num in ptr */

/* now we can retrieve the value of num via '*ptr' */
printf("num's memory address is %p and num is %d\n", ptr, *ptr);

```

Hopefully your book will or has explained this in more depth.

---

### Post by Peter76 on 2011-02-14
Thanks for the quick replies.
I am aware of pointers, but I never saw this construction before, Iwas thinking along the lines of what Johnl was saying, that I declared a function whith a return type of pointer, but how I understood it, is that the asterisk should be _before_ the variable you want to become a pointer, and not after it.
That made me think it had to do with the function, and not with Person.
But long story short, this means it is a function with a return type of a pointer to Person?

Thanks

---

### Post by schauerlich on 2011-02-14
> **Peter76 said:**
> Thanks for the quick replies.
I am aware of pointers, but I never saw this construction before, Iwas thinking along the lines of what Johnl was saying, that I declared a function whith a return type of pointer, but how I understood it, is that the asterisk should be _before_ the variable you want to become a pointer, and not after it.
That made me think it had to do with the function, and not with Person.
But long story short, this means it is a function with a return type of a pointer to Person?

Thanks

Person is not a variable, it is a type, just like 'int' or 'char'.

```
int *foo(char a);
Person *bar(char a);
```

The first declares a function 'foo' that takes a char and returns a pointer to an int. The second declares a function 'bar' that takes a character and returns a pointer to a Person.

---

### Post by Peter76 on 2011-02-14
> **schauerlich said:**
> Person is not a variable, it is a type, just like 'int' or 'char'.

Sorry, my mistake, didn't put that very well.

> The first declares a function 'foo' that takes a char and returns a pointer to an int. The second declares a function 'bar' that takes a character and returns a pointer to a Person.

ANd again thanks for more clarification

---

### Post by Vaphell on 2011-02-14
* position is somewhat flexible
int *a;
int* a;
both lines are valid and at least for me the 2nd one is more intuitive - 'a is of pointer-to-int type' as opposed to 'a-points-to int therefore a is a pointer to int'. I don't like the indirection hidden in such declaration. My preferred approach fails though in few cases, like in mentioned int *a, b, *c;

---

### Post by StephenF on 2011-02-14
> **Vaphell said:**
> * position is somewhat flexible
int *a;
'a-points-to int therefore a is a pointer to int'. I don't like the indirection hidden in such declaration.
Maybe because you are reading it wrong?

I'm getting *a is an int therefore 'a' sans indirection operator is a pointer to an int.

---

### Post by Vaphell on 2011-02-14
isn't that the same? all i am saying is that you get what a is through implication not through direct declaration.
I don't like the lack of consistency because such construct doesn't follow clean <type> <variable_name> separation - but it's only a matter of taste.
I don't mind it much now, but when i started i simply hated int *a; version and i can see it being confusing for some beginners.

---

### Post by worksofcraft on 2011-02-14
> **Vaphell said:**
> isn't that the same? all i am saying is that you get what a is through implication not through direct declaration.
I don't like the lack of consistency because such construct doesn't follow clean <type> <variable_name> separation - but it's only a matter of taste.
I don't mind it much now, but when i started i simply hated int *a; version and i can see it being confusing for some beginners.

What you say about consistency is true, and some people do things like:
```

typedef int * intptr;

```

However I have really come to hate that kind of thing because when names are poorly chosen you totally lose track of what is a pointer and what isn't and have no idea of what they point to...

Many other programming languages simply don't have this problem because they do not support the concept of pointers in the first place, but if we are going to have pointer types I quite like the fact that they stand out like a sore thumb.

p.s. Personally if I had been Kernighan or Ritchie I would have chosen the @ symbol instead of the * (which is obviously already taken as diadic multiplication operator).

---

