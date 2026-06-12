---
title: "Semaphore dought"
date: 2009-09-10
forum: Programming Talk
---

### Post by rahul_shilps on 2009-09-10
I have a dought.

In Linux C programming semaphore what is **sem_t** data type.

what is actually content of datatype **sem_t**.

Please help.:confused:

---

### Post by MadCow108 on 2009-09-10
it should say in your /usr/include/semaphore.h

on my system it is:
```

#if __WORDSIZE == 64
# define __SIZEOF_SEM_T	32
#else
# define __SIZEOF_SEM_T	16
#endif

typedef union
{
  char __size[__SIZEOF_SEM_T];
  long int __align;
} sem_t;

```

---

### Post by fct on 2009-09-10
The content of sem_t changes even among different linux versions, let alone different UNIX systems.

Only the semaphore.h functions are intended to manipulate its contents, not the application developer. That's why it isn't documented in the manual pages.

---

