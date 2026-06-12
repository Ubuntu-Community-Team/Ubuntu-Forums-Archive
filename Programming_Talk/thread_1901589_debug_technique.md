---
title: "debug technique"
date: 2011-12-28
forum: Programming Talk
---

### Post by chuchi on 2011-12-28
Hi  friends!! I just want to know is this debugging technique is  recommended. It consists in to put a preprocessor directive which  indicates whether show an error or not. For example:

```

#define DEBUG 1 . . . char *c=(char*)malloc(8); #if DEBUG == 1 if(!c) printf("error on malloc in function myfunction\n");  #endif

```

What I only want to know is if this is a good practice for  debugging a program, if you recommend me this. When the version is to  release, of course it has to be compiled with DEBUG=0

Thank you very much!!

---

### Post by Barrucadu on 2011-12-28
You should always check the return value of malloc, as it may return NULL at any time there is an error - not just during development.

---

### Post by ofnuts on 2011-12-29
> **chuchi said:**
> Hi  friends!! I just want to know is this debugging technique is  recommended. It consists in to put a preprocessor directive which  indicates whether show an error or not. For example:

```

#define DEBUG 1 . . . char *c=(char*)malloc(8); #if DEBUG == 1 if(!c) printf("error on malloc in function myfunction\n");  #endif

```What I only want to know is if this is a good practice for  debugging a program, if you recommend me this. When the version is to  release, of course it has to be compiled with DEBUG=0

Thank you very much!!
The usually technique is to use an assert(). Bar that, it's better for the eyes to define a macro that has two different forms for debug and runtime. This macro can use the __FILE__, __LINE__ and __func__ processor variables to print debug information.

---

