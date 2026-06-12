---
title: "pointer question c"
date: 2014-04-26
forum: Programming Talk
---

### Post by wingnut2626 on 2014-04-26
Lets say i have 

t```
ypedef struct{
   int age;
   int some_random_number;
   char first_name[80];
   char last_name[80;
   } Human;

Human *human1;
```

why is sizeof(human1) == 8???? What is that pointing to?

---

### Post by dwhitney67 on 2014-04-27
'human1' is just a variable, that has been defined as a pointer.  On a 64-bit architecture, it *can* store an 8-byte address; on a 32-bit architecture, it can only store a 4-byte address.

You have not initialized 'human1' to point to anything, thus it could be pointing to any location in your system's memory.  Where it is currently pointing to does not affect the size of the pointer.

---

### Post by ofnuts on 2014-04-27
```

typedef struct{
   int age;
   int some_random_number;
   char first_name[80];
   char last_name[80;
   } Human;

Human *human_ptr;
Human human;

```

You will see he difference between "sizeof human" and "sizeof human_ptr" (*).

(*) sizeof is an operator and not a function. The parentheses are not necessary.

---

