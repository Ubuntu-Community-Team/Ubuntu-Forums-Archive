---
title: "Castnig malloc() result."
date: 2011-08-18
forum: Programming Talk
---

### Post by cgroza on 2011-08-18
Hello,
I am learning C and I have seen code snippets that cast the malloc result and others that don't.
So should I:
```

int* num = (int*) malloc(sizeof *num));

```Or just:
```

int* num = malloc(sizeof *num));

```I wish to keep my C code compatible with C++ too.

---

### Post by NovaAesa on 2011-08-18
Casting the result of malloc in C is a very bad thing to do. This is because the result will hide the error caused by failing to prototype malloc (this can cause bugs that don't show up on all systems, and can be VERY difficult to track down).

Unfortunately (or fortunately depending on how you look at it) it doesn't work that way in C++. In C++ you always need to cast, although you shouldn't really be using malloc in C++ code anyway.

---

### Post by GeneralZod on 2011-08-19
> **NovaAesa said:**
> Casting the result of malloc in C is a very bad thing to do. This is because the result will hide the error caused by failing to prototype malloc (this can cause bugs that don't show up on all systems, and can be VERY difficult to track down).


Failing to prototype malloc in C++ would be a compile error, so if cgroza is occassionally compiling with g++ (as I presume he will be), this would be a non-issue.  Go for the cast, I say :)

---

### Post by NovaAesa on 2011-08-19
That doesn't help cgroza if he forgets to prototype malloc in C code though :P IMO, either write C code or write C++ code, the languages aren't a subset of each other.

---

### Post by Bachstelze on 2011-08-19
I say don't cast, simply because it's useless. Also no matter how much you wish it were, C is not C++. You have to choose one or the other.

---

### Post by MadCow108 on 2011-08-19
> **cgroza said:**
> I wish to keep my C code compatible with C++ too.

you answered your own question. Cast it.
Casting it does **not** disable detecting implicit declaration with recent versions of gcc:

```
cat test.c
int main(int argc, char * argv[], char *envp[])
{
  int * a = (int*) malloc(4);
  return 0;
}
gcc test.c
test.c:4:20: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217; [enabled by default]

```

---

### Post by Arndt on 2011-08-19
> **Bachstelze said:**
> I say don't cast, simply because it's useless. Also no matter how much you wish it were, C is not C++. You have to choose one or the other.

It can easily happen that you have a program written in C, and later while writing a C++ program, you want to reuse source code from the C program.

For a given program, it makes sense to choose only one of them, but you don't necessarily choose one for life and stick to it, although it makes perfect sense to choose one for the next task because you are more used to it.

Being aware of the differences is the most important thing, if you sometimes use one and sometimes the other.

Taking meticulous care to keep source code as compatible as possible between them is not a good idea, though, in my opinion - to that extent I agree with Bachstelze.

---

### Post by dwhitney67 on 2011-08-19
> **NovaAesa said:**
> ... although you shouldn't really be using malloc in C++ code anyway.

Correct!  Why cgroza ever brought up the notion of using malloc() in a C++ application is what should be critiqued.

For C++, 'new' should aways be used when allocating; unlike malloc(), 'new' will call the constructor for the object being allocated.  Conversely, 'delete' will call the destructor; free() will not.

As for casting the return value of malloc(), I personally do not do it because with GCC, it is superfluous.  However, someone recently pointed out to me that it is (still) required by Visual Studio (I cannot independently verify this).

---

### Post by cgroza on 2011-08-19
So I guess I will not cast the result, unless I am writing some sort of library and will want to use it in the future in C++.

Thank you.

---

### Post by dwhitney67 on 2011-08-19
> **cgroza said:**
> So I guess I will not cast the result, unless I am writing some sort of library and will want to use it in the future in C++.

Thank you.

If you develop a library in C, then you should use gcc.  You should not rely on g++, even if the C library might be used by a C++ application.

Nevertheless, I've seen some people use g++ when compiling C programs because it is a bit stricter.  However this can be achieved with 'gcc' by using the options -Wall -pedantic and possibly even -ansi.

P.S.  As far as building a C++ program that relies on a C library, by the time the two are linked together, the notion of whether malloc() was casted when used in the library is a moot issue.  The library was compiled prior to ever reaching the link stage.

---

### Post by cgroza on 2011-08-19
> **dwhitney67 said:**
> If you develop a library in C, then you should use gcc.  You should not rely on g++, even if the C library might be used by a C++ application.

Nevertheless, I've seen some people use g++ when compiling C programs because it is a bit stricter.  However this can be achieved with 'gcc' by using the options -Wall -pedantic and possibly even -ansi.

P.S.  As far as building a C++ program that relies on a C library, by the time the two are linked together, the notion of whether malloc() was casted when used in the library is a moot issue.  The library was compiled prior to ever reaching the link stage.
Thanks for the clarification. So, no more casting for me :D.

---

