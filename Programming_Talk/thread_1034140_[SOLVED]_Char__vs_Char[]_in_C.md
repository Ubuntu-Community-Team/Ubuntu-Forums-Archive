---
title: "[SOLVED] Char * vs Char[] in C"
date: 2009-01-08
forum: Programming Talk
---

### Post by ooobooontooo on 2009-01-08
Hi,

So I was wondering what the difference is between creating a string through a char * or a char[]...I can't really think of anything...they're even interchangeable aren't they?

Also, I have this weird problem regarding the difference between char * and char[].

This first piece of code will only send 4 bytes:
```
char *var = "blahblah";
send(socknum, var, sizeof(var), 0);
```

This second code will send all 8 bytes:
```
char var[] = "blahblah";
send(socknum, var, sizeof(var), 0);
```

---

### Post by CptPicard on 2009-01-08
Well, that's the difference... arrays and pointers are not completely interchangeable, although "arrays degrade to pointers", meaning that an array can be used as a pointer (to first element), and that passing arrays to functions happens by passing just this pointer to the first element.

When you take sizeof(char*), you get the size of the pointer type, not the size or length or anything of the array... actually, the pointer has no idea whether it is pointing just a single char or an array of chars.

Then again if you take the size of a *fixed size array* the size of which is known by the compiler, such as in your case when you are taking sizeof a static string, then you know how much memory storing that array requires, so you get 9 for "blahblah" (it's  9 because there is the null-terminator byte you're not seeing).

On the other hand if we don't know the size of the array sizeof returns again just the pointer's size in bytes... try this

```

#include <stdio.h>


void func(char p[]) {

  printf("%i\n", sizeof(p));  // p could be any size, sizeof returns pointer size

}


int main() {

  char a[] = "foobar";
  printf("%i\n", sizeof(a)); // known size

  func(a);

}



```

---

### Post by Bachstelze on 2009-01-08
That looks very much like a difference, doesn't it? ;)

Since you are using a 32bit OS, the [font="monospace"]sizeof()[/font] of a pointer will *always* be 4 bytes (32 bits). Always. An initialized, fixed-width array, on the other hand, will have the size of all its elements put together (here, 9*sizeof(char), i.e. 9).

Another very important difference is that pointer names are variables but array names are not. In other words, you can change the location a pointer points to, but this is not true for an array name. For example, this will work:

```
char* s = "hello";
char* t = "world";
t = s;
printf("%s\n", t);
```

But this will not:

```
char s[] = "hello";
char t[] = "world";
t = s;
printf("%s\n", t);
```

---

### Post by ooobooontooo on 2009-01-08
Aah. Thanks. So basically when I call sizeof(char *) it returns the size of the pointer..basically 4 bytes because a pointer can be thought of as an unsigned int...right?

EDIT: This first part was answered by HymnToLife

Then I have another question. When you allocate space using char[]like:
```
char var[256];
```
Then will it clear all 256 bytes in the stack for var? I ask because when I tried having var filled up by recv() and using printf to see the contents of var, it showed a lot of weird symbols. I'm sure the stack was not overwritten in any way and when I memset() the 256 bytes to be used by var, the weird symbols went away.

---

### Post by Liviu-Theodor on 2009-01-08
> **ooobooontooo said:**
> Then I have another question. When you allocate space using char[]like:
```
char var[256];
```
Then will it clear all 256 bytes in the stack for var? I ask because when I tried having var filled up by recv() and using printf to see the contents of var, it showed a lot of weird symbols. I'm sure the stack was not overwritten in any way and when I memset() the 256 bytes to be used by var, the weird symbols went away.

The short answer is no. The long answer is that is no default rule for the compiler in this case, so *maybe* it will clear the bytes, but don't count on it, most probably you will have anything there before the allocaton of memory. If you want to be sure, just set the bytes yourself, in a for statement.

---

### Post by Bachstelze on 2009-01-08
*EDIT: never mind, I misunderstood the question.*

---

### Post by ooobooontooo on 2009-01-08
Uhh..One of you said yes...one of you said no...

@HymnToLife
I'm inclined to believe your side because...I think I was taught somewhere that declaring variables automatically clears the space in the stack...though I think it may have been for Java...
So I'm guessing that you're saying the problem with the weird signals is unrelated to how C declares its string variables?

I'm also assuming the difference you were talking about is that:
char[] var would create space in stack and
char *var = malloc(256*sizeof(char)) allocates space in the heap...

EDIT: uhh...I guess now I'm inclined to believe Liviu-Theodor...

---

### Post by Liviu-Theodor on 2009-01-08
I met one specific C compiler that initialized global arrays with 0's, but did not with local arrays, but that was specified in its documentation, mentioning that it was not the default behaviour for all compilers.

---

### Post by ooobooontooo on 2009-01-10
Thanks for all the help. I'll be sure to memset all my arrays from now on.

---

### Post by dwhitney67 on 2009-01-10
> **ooobooontooo said:**
> Thanks for all the help. I'll be sure to memset all my arrays from now on.

You can also do something like the following to set the array to be all nulls:
```

char var[256] = {0};

```
Note, the initialization style shown above will not work for non-zero (non-null) values; for those, you would need to use memset() or just iterate over each element of the array.

---

### Post by Bachstelze on 2009-01-10
> **dwhitney67 said:**
> You can also do something like the following to set the array to be all nulls:
```

char var[256] = {0};

```


Or use [font="monospace"]calloc()[/font]:

```
char* var = calloc(256, sizeof(char));
```

---

### Post by Sockerdrickan on 2009-01-11
> **HymnToLife said:**
> Or use [FONT=monospace]calloc()[/FONT]:

```
char* var = calloc(256, sizeof(char));
```
sizeof(char) is redundant just put a 1 there!

---

### Post by Bachstelze on 2009-01-11
> **Tux0r said:**
> sizeof(char) is redundant just put a 1 there!

It would be redundant if all the compilers followed the standard. Sadly, this is not true...

---

### Post by ooobooontooo on 2009-01-11
But won't calloc() and malloc() allocate space in the heap? Whereas, declaring char var[256] = {0} would allocate space in the stack...At least that's the way I was taught...I guess for general purposes that wouldn't matter, but in my case it does... Thanks for all the extra input though. :p

---

### Post by Liviu-Theodor on 2009-01-14
You could use also the memset function in your program.

---

### Post by eye208 on 2009-01-14
> **Tux0r said:**
> sizeof(char) is redundant just put a 1 there!
This is a very bad idea.

If you hardcode buffer or type sizes like that, your code will be hard to maintain and prone to buffer overflows.

For example, imagine you have to implement wide character support in existing code. If the code uses "sizeof(char)", all you need to do is search & replace all "char" with "wchar_t". However, if the code uses "1" instead ... well, good luck! ):P

---

