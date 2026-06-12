---
title: "what is meaning of int (*xyz)[13]"
date: 2010-12-07
forum: Programming Talk
---

### Post by c2tarun on 2010-12-07
what is the meaning of 
```

int (*xyz)[13];

```

what i figured is this is a function pointer which can store the address of 13 functions with no argument.
am i correct???

---

### Post by nvteighen on 2010-12-07
> **c2tarun said:**
> what is the meaning of 
```

int (*xyz)[13];

```

what i figured is this is a function pointer which can store the address of 13 functions with no argument.
am i correct???

cdecl is a nice program in the repos that is very handy for people learning C (and C++) data types. I highly recommend it to you... and to anybody, as it's also useful for seasoned C and C++ programmers (sometimes you are so immersed into the most complex constructs that you tend to forget some of the most obscure and less used pitfalls of pointer declaration syntax... well, at least, that happens to me from time to time :P)

```

ugi@UGI:~$ cdecl explain "int (*xyz)[13]"
declare xyz as pointer to array 13 of int
ugi@UGI:~$ cdecl explain "int (*xyz)()[13]"
declare xyz as pointer to function returning array 13 of int
ugi@UGI:~$ cdecl explain "int (*xyz)[13]()"
declare xyz as pointer to array 13 of function returning int
ugi@UGI:~$ 

```

---

### Post by c2tarun on 2010-12-07
> **nvteighen said:**
> cdecl is a nice program in the repos that is very handy for people learning C (and C++) data types. I highly recommend it to you... and to anybody, as it's also useful for seasoned C and C++ programmers (sometimes you are so immersed into the most complex constructs that you tend to forget some of the most obscure and less used pitfalls of pointer declaration syntax... well, at least, that happens to me from time to time :P)

```

ugi@UGI:~$ cdecl explain "int (*xyz)[13]"
declare xyz as pointer to array 13 of int
ugi@UGI:~$ cdecl explain "int (*xyz)()[13]"
declare xyz as pointer to function returning array 13 of int
ugi@UGI:~$ cdecl explain "int (*xyz)[13]()"
declare xyz as pointer to array 13 of function returning int
ugi@UGI:~$ 

```



wow....   :p
that is something called awesome ....

---

### Post by Krupski on 2010-12-07
> **nvteighen said:**
> cdecl is a nice program in the repos that is very handy for people learning C (and C++) data types.

Wow... just stumbled across this. The time it could have saved me if I knew about it before.......


THANKS!!!!!

-- Roger

---

### Post by rnerwein on 2010-12-07
> **c2tarun said:**
> what is the meaning of 
```

int (*xyz)[13];

```what i figured is this is a function pointer which can store the address of 13 functions with no argument.
am i correct???
hi
before you start with a function pointer array have a look at: --> qsort 
init it:
static  int     (*foo_ptr)(); /* pointer to foo_pp_sort */
static  int     foo_pp_sort(t_stat **, t_stat **);

in main:
foo_ptr = foo_pp_sort;

and then call it:
 qsort((char **)p_proc, i_tasks, sizeof(char **), foo_ptr);

and in the function:

int foo_pp_sort(t_stat  **t1, t_stat **t2)
{

    switch(I_sort) {
        case 0: /* cpu usage */
            return( (*t1)->p_rss < (*t2)->p_rss);
            break;
.............
.....................


ups - what i'm doing there.
i'm sorting an array of pointer to - anything
that means i'm only sorting ony the pointer ( 4 or 8 byte ) - the sesult is the same. but faster then hell.
have fun to understand it.
( for more help send me a private message )
ciao
     richi

---

