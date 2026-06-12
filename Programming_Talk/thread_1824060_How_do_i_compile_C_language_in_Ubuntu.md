---
title: "How do i compile C language in Ubuntu?"
date: 2011-08-13
forum: Programming Talk
---

### Post by marshall1349 on 2011-08-13
There's some description in a book on how to create and compile apps in Linux...
The program was a basic one(helloworld)...
But I didn't understand how to compile,link and run

$ gcc -o hello hello.c
$ ./hello
Hello World
$

This is what was written in the book...but my program just didn't compile...
P.S. I already installed gcc

---

### Post by lisati on 2011-08-13
*Thread moved to **Programming Talk**.*

Have you installed build-essential? Did you get an error message?

---

### Post by marshall1349 on 2011-08-13
Yes,I have installed build essential.I tried compiling from the directory where i saved the .c file."gcc -o hello.c" gives the error "gcc: no input files".

---

### Post by schauerlich on 2011-08-13
You use -o to name the output file. So in your line above, GCC thought you named the output "hello.c", but never gave it an input file. 

So, if you want to name your program "hello", you would do:

```
$ gcc -Wall hello.c -o hello
```

You can then run your program with

```
$ ./hello
```

---

### Post by marshall1349 on 2011-08-13
Done!Thanks a lot guys for your support....

---

### Post by Bachstelze on 2011-08-13
Wait, what? gcc -o output source.c is how I always do it. :o

*EDIT:* Never mind, the line was changed...

---

