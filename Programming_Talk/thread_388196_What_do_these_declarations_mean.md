---
title: "What do these declarations mean ?"
date: 2007-03-19
forum: Programming Talk
---

### Post by akudewan on 2007-03-19
Hi,

I have a list of questions given to me, and I can't figure out a few of them. I looked up in some books, but I still can't get it...

What do the following declarations mean ?:

```
1) char sample(int (*pf)(char a, char b));
2) int(*pf)(void);
3) int(*pf)(char a, char b);
4) int(*pf)(char *a, char *b);

```

Edit: There's one more:
```

void fn(int a[])

```

Thanks in advance

---

### Post by hod139 on 2007-03-19
> **akudewan said:**
> 

What do the following declarations mean ?:

```
1) char sample(int (*pf)(char a, char b));
2) int(*pf)(void);
3) int(*pf)(char a, char b);
4) int(*pf)(char *a, char *b);

```
These are function pointers (I'm geussing pf stands for "pointer to function").  pf is a function pointer and points to a function that takes:
1) <strike>2 chars and returns an int</strike> **Edit:** The function sample takes for a parameter a function pointer which points to a function that takes 2 chars and returns an int.  The function sample returns a char.
2) a void (no parameters) and returns an int
3) 2 chars and returns an int
4) 2 pointers to two chars, and returns an int

See the [function pointer tutorial]("http://www.newty.de/fpt/index.html") for more help.
> 
Edit: There's one more:
```

void fn(int a[])

```This is a function that takes an integer array.

---

### Post by akudewan on 2007-03-20
Cool. Thanks :)

---

