---
title: "Need help with compiling C++ program"
date: 2013-06-16
forum: Programming Talk
---

### Post by zobayer1 on 2013-06-16
I have written a C++ program that first generates a random serial number into a file and then reads the serial number from the file and use it in some other logic. Now I want to compile this into a binary file that the secret code will be available within the program as a constant value. Is it possible to set variables or macro's at compile time with values external to the program? Thanks in advance.

---

### Post by r-senior on 2013-06-16
You can define macros at compile time with the -D option to g++:

```
g++ -o myprogram -DANSWER=42 myprogram.cc
```

This is the same as doing a #define in your program:

```
#define ANSWER 42
```

The value on the command line doesn't have to be a constant, it could be the output of a program:

```
g++ -o myprogram -DDATE="\"$(date)\"" myprogram.cc
```

The quoting gets a bit messy with strings.

---

### Post by r-senior on 2013-06-16
You can define macros at compile time with the -D option to g++:

```
g++ -o myprogram -DANSWER=42 myprogram.cc
```

This is the same as doing a #define in your program:

```
#define ANSWER 42
```

The value on the command line doesn't have to be a constant, it could be the output of a program:

```
g++ -o myprogram -DDATE="\"$(date)\"" myprogram.cc
```

The quoting gets a bit messy with strings.

---

### Post by zobayer1 on 2013-06-16
> **r-senior said:**
> You can define macros at compile time with the -D option to g++:

```
g++ -o myprogram -DANSWER=42 myprogram.cc
```

This is the same as doing a #define in your program:

```
#define ANSWER 42
```

The value on the command line doesn't have to be a constant, it could be the output of a program:

```
g++ -o myprogram -DDATE="\"$(date)\"" myprogram.cc
```

The quoting gets a bit messy with strings.

Thanks, trying that way. However, multiple words causing a bit trouble.

---

### Post by MG&amp;TL on 2013-06-18
> **zobayer1 said:**
> However, multiple words causing a bit trouble.

Try e.g

```
-DSOMEVAR='"Some words here"' [...]
```

To set a macro *SOMEVAR* to a string *"Some words here"*.

---

### Post by zobayer1 on 2013-06-18
> **MG&TL said:**
> Try e.g

```
-DSOMEVAR='"Some words here"' [...]
```

To set a macro *SOMEVAR* to a string *"Some words here"*.

Thanks, it's much simpler, I was thinking about putting spaces after some escape characters, but looks like single quotes does it.

---

