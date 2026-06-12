---
title: "Please help me in  structures in C"
date: 2011-02-09
forum: Programming Talk
---

### Post by prateek.sahu on 2011-02-09
What will be the output of this program please explain???


#include<stdio.h>

int main()
{
    struct emp
    {
        char *n;
        int age;
    };
    struct emp e1 = {"Dravid", 23};
    struct emp e2 = e1;
    strupr(e2.n);
    printf("%s\n", e1.n);
    return 0;
}

---

### Post by trent.josephsen on 2011-02-09
```
% gcc -std=c99 -Wall -Wextra -pedantic prateek.c
prateek.c: In function ‘main’:
prateek.c:12:1: warning: implicit declaration of function ‘strupr’
/tmp/cc24g84K.o: In function `main':
prateek.c:(.text+0x34): undefined reference to `strupr'
collect2: ld returned 1 exit status
```

I don't know what you're trying to do, but it sounds suspiciously like homework.  In any case, if you just wanted to know the output of a simple program like this, the best strategy is to run it and see what happens.  Of course in this case it doesn't even compile.

---

### Post by schauerlich on 2011-02-09
Googling, it seems strupr is a nonstandard function that's supposed to convert a string to upper case. So, to point you in the right direction: will that struct emp be copied when it is assigned? That should give you the answer.

---

### Post by .bang on 2011-02-10
Try defining the structure before the main function.

---

### Post by Rany Albeg on 2011-02-10
strupr is unknown.
you can use something like:

```
void upcase(char *p)
{
	while(*p != '\0')
	{
		if(*p >= 97 && *p <= 122)
			*p -= 32;
		++p;
	}
}
```

to convert a string to uppercase.

EDIT:string must be **NULL terminated**.

---

### Post by Praveen30 on 2011-02-10
> **prateek.sahu said:**
> What will be the output of this program please explain???


#include<stdio.h>

int main()
{
    struct emp
    {
        char *n;
        int age;
    };
    struct emp e1 = {"Dravid", 23};
    struct emp e2 = e1;
    strupr(e2.n);
    printf("%s\n", e1.n);
    return 0;
}

interesting to see this programme is running on turbo c compiler and not on gcc even after adding <string.h>....
First thing define your comiler.
Second thing just ask your doubt not the programme output...run your programme if you are not able to understand the output then ask that...

Definitely the ans will be DRAVID, put the array(n[5]) in place of char *n ....now your output will be Dravid...):P

---

