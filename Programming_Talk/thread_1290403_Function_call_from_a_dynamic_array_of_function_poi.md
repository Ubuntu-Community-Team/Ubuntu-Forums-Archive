---
title: "Function call from a dynamic array of function pointers - C++"
date: 2009-10-13
forum: Programming Talk
---

### Post by shynthriir on 2009-10-13
Easist if shown by example...

```
int **FunctionArrayPtr;
```

```
FunctionArrayPtr is new (int *[NUMBER])();
```

How do I call a function from this array? I know if it is not a dynamicly set array, its a simple

```
FunctionArrayPtr[0]();
FunctionArrayPtr[1]();
// etc..
```

I've been trying something along the lines of

```
(*FunctionArrayPtr)[0]();
```

But it won't compile like that. Any help?

---

### Post by MadCow108 on 2009-10-13
```

typedef void (*function)(void);
...
function* funcarray = new function[2];
funcarray[0] = &sumefunc;
funcarray[1] = &otherfunc;
funcarray[0]();
funcarray[1]();

```

---

### Post by shynthriir on 2009-10-13
Awesome, that works.

I've never dealt with typedefs before, I'll have to look into them.
Thanks!

---

### Post by MadCow108 on 2009-10-13
for completeness, without typedef it would like something like that:
void (**funcarray)(void)=(void (**)(void)) new void*[2];
a nice line to confuse beginners :)

---

