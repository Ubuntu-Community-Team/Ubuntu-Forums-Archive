---
title: "Implement system(char *command) in C"
date: 2008-05-01
forum: Programming Talk
---

### Post by adityakavoor on 2008-05-01
I am looking for a C code for the implementation of the system() call.

I have to implement that function in C language as a challenge posed in my college.

I need help in converting the character string into respective arguments to be passed to the system() where I need to call the *exec*.

Any idea?

---

### Post by scourge on 2008-05-01
This page has a code sample of how to implement the system() function: [http://www.opengroup.org/onlinepubs/000095399/functions/system.html](http://www.opengroup.org/onlinepubs/000095399/functions/system.html)


> I need help in converting the character string into respective arguments to be passed to the system() where I need to call the exec.

I'm not sure I understand. Do you mean that you need to tokenize a string? Then strtok_r is your friend.

---

### Post by slavik on 2008-05-01
Your problem is a typical homework in a workstation programming class. I assume that you know about the basic shell process (fork, exec/wait).

system() pseudocode:

```

int system(char *) {
  int f_ret;
  switch (f_ret: fork()) {
    case -1: perror(); break;
    case 0:
      //split up the string, then call the shell with the string for it to be executed
    case default: waitpid(f_ret);
  }
}

```

I believe the above should be good enough to get you started.

---

### Post by adityakavoor on 2008-05-01
> split up the string, then call the shell with the string for it to be executed


I want to know how this is achieved

---

### Post by engla on 2008-05-01
strtok could split the string for you. I'm sure there are more convenient methods, but this is from standard C.

from "man strtok" (install 'manpages-posix-dev' for such manpages)

```
#include <string.h>
char *strtok(char *str, const char *delim);

The strtok() function parses a string into a sequence  of  tokens.   On
the  first call to strtok() the string to be parsed should be specified
in str.  In each subsequent call that should parse the same string, str
should be NULL.
...

```

edit: I noticed those docs actually advices the programmer to avoid using strtok, since it has some quirks.

---

### Post by scourge on 2008-05-01
> **engla said:**
> edit: I noticed those docs actually advices the programmer to avoid using strtok, since it has some quirks.

It's not thread-safe, which is why I suggested the use of strtok_r instead.

---

### Post by engla on 2008-05-03
> **scourge said:**
> It's not thread-safe, which is why I suggested the use of strtok_r instead.

ah, I see. It's even worse than that though, it seems strtok can only be invoked for one string at any given time, nested invokations would break totally. However for very simple uses, use of strtok should be safe. And it seems strtok_r (where the r is for reentrant) is an extension as is not in any C standard (but in POSIX) according to the man page I read.

---

