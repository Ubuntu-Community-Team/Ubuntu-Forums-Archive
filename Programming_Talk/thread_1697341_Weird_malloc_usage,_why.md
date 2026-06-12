---
title: "Weird malloc usage, why"
date: 2011-02-28
forum: Programming Talk
---

### Post by t1497f35 on 2011-02-28
Hi,
does the bold code from:
char *buffer = (char*) malloc (**sizeof(char)***lSize);
make any sense?
Any cases when **char** is not 1 byte or am i missing something

I found it here:
[http://www.cplusplus.com/reference/clibrary/cstdio/fread/](http://www.cplusplus.com/reference/clibrary/cstdio/fread/)

---

### Post by ve4cib on 2011-02-28
As far as I know a char is always 1 byte on any system (assuming a standard compiler), but it's usually good form to always include the sizeof(whatever) in your malloc calls.

This ensures that on the off-chance that someone is using a weird compiler where a char is a 16-bit character instead of a single byte your program will still compile and work properly without segfaulting.  It's less of an issue with chars than it is with ints (which are usually 4 bytes, but can sometimes be only 2), or structs (which can be of any size).

---

### Post by ibuclaw on 2011-02-28
> **t1497f35 said:**
> Hi,
does the bold code from:
char *buffer = (char*) malloc (**sizeof(char)***lSize);
make any sense?
Any cases when **char** is not 1 byte or am i missing something

I found it here:
[http://www.cplusplus.com/reference/clibrary/cstdio/fread/](http://www.cplusplus.com/reference/clibrary/cstdio/fread/)
It's just good practice, that's all. And ensures that people who read it will understand what it does.

ie:
```

int * a = malloc(20);  // actual size not immediately obvious.

```

So thinking of allocating a 4 length char and int array as:
```

char * var = {char, char, char, char};
int * var2 = {int, int, int, int};

```

You can see why people use:
```

char * var = malloc(sizeof(char) * 4);
int * var2 = malloc(sizeof(int) * 4);

```

Regards

---

### Post by t1497f35 on 2011-02-28
Thanks, it looks like (very) few people do this in actual apps.

---

