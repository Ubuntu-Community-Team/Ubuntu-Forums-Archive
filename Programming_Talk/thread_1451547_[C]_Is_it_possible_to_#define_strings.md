---
title: "[C] Is it possible to #define strings?"
date: 2010-04-10
forum: Programming Talk
---

### Post by durand on 2010-04-10
Hi,

I think the title says it all, but basically, I want to have a filepath at the top of the source so that it is easy to change. Is this possible in any way, maybe not using #define? I don't want to put the fopen() function at the top. I'm pretty new to C so be kind :)

Thanks!

---

### Post by Compyx on 2010-04-10
Sure:
```

#define MY_PATH "/path/to/file"

```

That defines a macro named MY_PATH which gets replaced during preprocessing by the string literal "/path/to/file".

---

### Post by MadCow108 on 2010-04-10
yes you can.
#define MYFILE "file.txt"
but a global variable is better than a macro because you get better typesafety and you can address it
just put this at the top of the file:
const char * gfilename = "file.txt";

if you want it visible only in one file put a static in front

---

### Post by durand on 2010-04-10
> **MadCow108 said:**
> yes you can.
#define MYFILE "file.txt"
but a global variable is better than a macro because you get better typesafety and you can address it
just put this at the top of the file:
const char * gfilename = "file.txt";

if you want it visible only in one file put a static in front

Thanks Compyx, I might use that. But for curiosity's sake, how would you reference gfilename in a printf(). Would it be something like printf("%c")? I thought chars could only be one character long...Thanks MadCow108.

---

### Post by Compyx on 2010-04-10
> **MadCow108 said:**
> yes you can.
#define MYFILE "file.txt"
but a global variable is better than a macro because you get better typesafety and you can address it
just put this at the top of the file:
const char * gfilename = "file.txt";

if you want it visible only in one file put a static in front

Type-safety is the same with a #define, the macro gets replaced with a string literal, which has the type 'pointer to const char', so this:
```

#define MY_PATH "/my/file"

int x = MY_PATH;

```
will generate a compiler warning.

---

### Post by MadCow108 on 2010-04-10
> **durand said:**
> Thanks Compyx, I might use that. But for curiosity's sake, how would you reference gfilename in a printf(). Would it be something like printf("%c")? I thought chars could only be one character long...Thanks MadCow108.

its a pointer to const char, so its a normal c style string literal (which means you can't modify it)
its the same as const char gfile[] = "file";
so you would use it in printf with %s

in case of strings I guess it doesn't really matter if you use a global variable or a macro. Use whatever you like more

---

### Post by Compyx on 2010-04-10
> **durand said:**
> Thanks Compyx, I might use that. But for curiosity's sake, how would you reference gfilename in a printf(). Would it be something like printf("%c")? I thought chars could only be one character long...Thanks MadCow108.

You print a string with %s, so something like this:
```

printf("filename = '%s'\n", MY_PATH);

```
A %c does indeed print a single character. It takes an int as argument and converts that to unsigned char and prints that. You can pass a char to printf if you want, type promotion automagically converts the char to int.

Just remember: %c for single characters, %s for strings.

---

### Post by durand on 2010-04-10
Hmm, I was told that C only supported character arrays and not strings :S I think I'll use #define here as it's simpler to read, but I'll remember the string information for later. Thanks!

---

### Post by Compyx on 2010-04-10
> **durand said:**
> Hmm, I was told that C only supported character arrays and not strings :S I think I'll use #define here as it's simpler to read, but I'll remember the string information for later. Thanks!

True, when a C programmer talks about a `string' he/she actually means 'a pointer to the first of a sequence of char, terminated by nul ('\0'). That's a C-style string. C does not have a string type like C++ or Java.

---

### Post by durand on 2010-04-10
Oh, thanks :) It seems like there is a lot to learn in C :S

---

