---
title: "why gets is dangerous"
date: 2010-12-20
forum: Programming Talk
---

### Post by c2tarun on 2010-12-20
I have some queries:
1. Why gets is dangerous? ( i guess it is  because we cannot limit the input size)
2. fgets also stores the new line character, is there any other function better than gets that doesn't store the new line character.
3. Please look at the following code:
```


int main(void)
{
     char *a;
     char *b;
     int na=100;
     size_t nb=100;
     fgets(a,na,stdin);
     getline(&b,&nb,stdin);
}


```

both a and b are same type of variables, but when we try to make any changes to b (like b[2]='*';) we get segmentation. In this forum only I have been told that *b is like Read Only and we cannot change it. Then how can we change a???
Thanx

---

### Post by dwhitney67 on 2010-12-20
Your example *may* not work, since you have not initialize the 'a' pointer!  In fact, I would expect that a segmentation fault would occur.

A proper example would be:
```

char a[100];

fgets(a, sizeof(a), stdin);

```
or
```

char* a = malloc(100);

fgets(a, 100, stdin);

free(a);

```

gets() isn't "dangerous" (eg. it won't bite you), but it is considered "un-safe" due to the possibility of facilitating a buffer overrun, which could then potentially compromise your application.

For example, if your application was safe-guarding a system by querying the user for a userid/password, and the operator enters a lengthy string, it could crash your app, and thus allow the operator to get access to the system.

As for your newline question, both getline() and fgets() will store the newline.  However, in the case of fgets(), if the string that is entered is longer than the buffer size, then the newline is NOT stored; only N-1 characters are stored, with the last being a null-character.

To strip a newline from the buffer, this can be used:
```

char* newline = strchr(a, '\n');

if (newline)
{
   *newline = '\0';
}

```

---

### Post by c2tarun on 2010-12-20
> **dwhitney67 said:**
> Your example *may* not work, since you have not initialize the 'a' pointer!  In fact, I would expect that a segmentation fault would occur.

A proper example would be:
```

char a[100];

fgets(a, sizeof(a), stdin);

```or
```

char* a = malloc(100);

fgets(a, 100, stdin);

free(a);

```gets() isn't "dangerous" (eg. it won't bite you), but it is considered "un-safe" due to the possibility of facilitating a buffer overrun, which could then potentially compromise your application.

For example, if your application was safe-guarding a system by querying the user for a userid/password, and the operator enters a lengthy string, it could crash your app, and thus allow the operator to get access to the system.

As for your newline question, both getline() and fgets() will store the newline.  However, in the case of fgets(), if the string that is entered is longer than the buffer size, then the newline is NOT stored; only N-1 characters are stored, with the last being a null-character.

To strip a newline from the buffer, this can be used:
```

char* newline = strchr(a, '\n');

if (newline)
{
   *newline = '\0';
}

```

Thanks, and sorry! I realized later that the code I posted will not work. fgets reads the buffer and points the pointer to that buffer if no memory is allocated to pointer. I read this in manual later. sorry and Thanks once again

---

### Post by StephenF on 2010-12-20
b is wrong as well. It's uninitialised and needs to be set to either NULL or malloc(nb). When b is set to null the value of nb is ignored.

---

### Post by trent.josephsen on 2010-12-20
A quick clarification:  the reason fgets stores a newline and gets doesn't is that with fgets, reading stops after N characters regardless of whether a newline has been encountered.  The existence of '\n' in the buffer after a call to fgets tells you that *that* line has been completely read, and future calls to fgets will get other lines.  If no newline appears in the buffer, you know that future calls to fgets will yield more characters of the *same* line.

gets (because it doesn't stop reading until a newline appears) doesn't suffer from this ambiguity, and therefore it's not necessary to include the newline in the string -- you can infer its existence.

If it bothers you, you could always write your own pseudo-gets that allocates space as necessary... I've seen several of those.

---

