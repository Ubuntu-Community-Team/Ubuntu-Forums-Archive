---
title: "what does -&gt; mean in C?"
date: 2007-11-08
forum: Programming Talk
---

### Post by nite owl on 2007-11-08
Hi just looking through some tutorials and came across this symbol:

```

->

```
just wondering what it means, thanks.

---

### Post by yabbadabbadont on 2007-11-08
It is used when you have a pointer to a structure and you want to dereference one of the stuct's fields.

```
typedef struct
{
char a;
int b;
} mystruct;

mystruct example;
mystruct *ptr;

ptr = &example;

ptr->a = 'A';
ptr->b = 1;

(*ptr).a = 'B';
(*ptr).b = 2;

```

---

### Post by hod139 on 2007-11-08
In case it isn't clear from yabbadabbadont's post, the 
"->" syntax is syntactic sugar for "(*ptr)." . 
```

ptr->
(*ptr).

```

are equivalent, where the former was introduced strictly for convenience.

---

