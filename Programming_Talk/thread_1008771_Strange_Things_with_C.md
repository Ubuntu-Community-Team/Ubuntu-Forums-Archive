---
title: "Strange Things with C"
date: 2008-12-11
forum: Programming Talk
---

### Post by DBQ on 2008-12-11
Hi everybody, could somebody let me know what is wrong please?

I wrote this function to check whether the fopen command opened the file:

```


void fcheck(FILE* fp, char* name)
{
       if(fp == NULL)
       {
           fprintf("<ERROR MESSAGE>");
           exit(1);
       } 
}


```

Now if I have a stamement FILE* fp = fopen("noSuchFile","r"), and do if(fp==NULL){.....print error} the NULL is picked up.  When I do fcheck(fp,"noSuchFile") the NULL value is not picked up why???

---

### Post by dwhitney67 on 2008-12-11
Is the code you posted the "real" code, or something that you typed for your query?  You are missing an arg to the fprintf() call; namely a pointer to a FILE (perhaps stdout or stderr?).

As for the function, it should work, presuming of course you performed an fopen() prior to the function call, and passed the file-pointer returned by the fopen() call.

---

### Post by DBQ on 2008-12-11
The code is something I types for the query.  I will look at it more and see why this behavior is happening.

---

### Post by PandaGoat on 2008-12-11
When you call fcheck, are you sure you are not actually passing a pointer to the pointer (&fp if fp is defined as FILE* fp)?

As far as I know, with the code you gave, it does what you want, except for misusing fprintf.

---

