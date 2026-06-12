---
title: "Error returned when trying to run C program"
date: 2013-09-17
forum: Programming Talk
---

### Post by Talruk6 on 2013-09-17
I've been getting an error message after trying to run a program I had just compiled.

I used this code saved as "hello.c":



```
#include <stdio.h> int main(void) 
{ 

     printf("A .c is used to end a C program filename.\n");

     return 0;
 
}
```


I used the command line and used:
gcc hello.c 
a.out

This should have compiled the program "hello.c" and then run the program "a.out".  It didn't. Instead it gave the error "a.out: command not found".  Any ideas?


Thanks.

---

### Post by dwhitney67 on 2013-09-17
Run it using
```

./a.out     # note the dot and forward-slash before the a.out

```

---

### Post by Talruk6 on 2013-09-17
> **dwhitney67 said:**
> Run it using
```

./a.out     # note the dot and forward-slash before the a.out

```

That did work, but...what did I just do?

---

### Post by dwhitney67 on 2013-09-17
> **Talruk6 said:**
> That did work, but...what did I just do?

You executed your program.  The dot & slash indicate to the bash shell the relative path to the program you wanted to run.  You could alternative specify the absolute path (e.g. /home/user/myFolder/a.out).

There's always the possibility that more than one program, bearing the same name, appear on your system.  Hence as a security measure, it is always wise NOT to include the current directory (represented by the dot) in your PATH environment variable.  If that dot were present in your PATH, then you would have been able to execute the 'a.out' as you originally attempted.

Some people don't give a rat about security, and if you are one of them, then you can set your PATH environment variable in your ~/.bashrc file with:
```

export PATH=.:$PATH      # this prepends the dot to your existing PATH settings

```

---

### Post by Talruk6 on 2013-09-17
Thanks!

---

