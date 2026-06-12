---
title: "In the&#12298;Begin Linux Programming &#12299;,something I can't understand! help me"
date: 2008-07-18
forum: Programming Talk
---

### Post by kingwangone on 2008-07-18
The book write:

Let&#8217;s create our own small library containing two functions and then use one of them in an example program.
The functions are called fred and bill and just print greetings.
1. First, we&#8217;ll create separate source files (imaginatively called fred.c and bill.c) for each of
them. Here&#8217;s the first:


```
#include <stdio.h>
void fred(int arg)
{
printf(&#8220;fred: you passed %d\n&#8221;, arg);
}

```

And here&#8217;s the second:

```
#include <stdio.h>
void bill(char *arg)
{
printf(&#8220;bill: you passed %s\n&#8221;, arg);
}
```


2. We can compile these functions individually to produce object files ready for inclusion into a
library. We do this by invoking the C compiler with the -c option, which prevents the compiler
from trying to create a complete program. Trying to create a complete program would fail
because we haven&#8217;t defined a function called main.

```
$ gcc -c bill.c fred.c
$ ls *.o
bill.o fred.o
```


3. Now let&#8217;s write a program that calls the function bill. First, it&#8217;s a good idea to create a header
file for our library. This will declare the functions in our library and should be included by all
applications that wish to use our library. It&#8217;s a good idea to include the header file in the files
fred.c and bill.c too. This will help the compiler pick up any errors.

```
/*
This is lib.h. It declares the functions fred and bill for users
*/
void bill(char *);
void fred(int);
```


4. The calling program (program.c) can be very simple. It includes the library header file and
calls one of the functions from the library.

```
#include &#8220;lib.h&#8221;
int main()
{
bill(&#8220;Hello World&#8221;);
exit(0);
}
```


5. We can now compile the program and test it. For now, we&#8217;ll specify the object files explicitly to
the compiler, asking it to compile our file and link it with the previously compiled object module bill.o.

```
$ cgcc -c program.c
$ gcc -o program program.o bill.o
$ ./program
bill: we passed Hello World
```

look here

```
/*
This is lib.h. It declares the functions fred and bill for users
*/
void bill(char *);
void fred(int);
```

I don't know that it's create a header in the new program,or write in program.c 

I write to this code in program.c,and compile the program,but it's return

cgcc:command not found

What's cgcc?

How to create a header about lib.h

---

### Post by geraldm on 2008-07-18
I have no idea what cgcc is unless it is misspelled.
Use gcc instead of cgcc OR else try cc

Gerald

---

### Post by Bachstelze on 2008-07-18
> **kingwangone said:**
> 
look here

```
/*
This is lib.h. It declares the functions fred and bill for users
*/
void bill(char *);
void fred(int);
```

I don't know that it's create a header in the new program,or write in program.c 

I write to this code in program.c,and compile the program,but it's return

cgcc:command not found

What's cgcc?

How to create a header about lib.h

You should put that in a new file called lib.h. And there is indeed a typo about gcc ;)

---

### Post by dwhitney67 on 2008-07-18
Also, don't use exit(0) to return from the main() function... use return(0).

If you insist on using exit(0), then #include <stdlib.h>.

For more critical analysis of your programs, compile using the following:
```
gcc -Wall -pedantic -c myFile.c
```

---

### Post by Kadrus on 2008-07-21
CGCC Does exist if I am not mistaken,so correct me if I am wrong :)
cgcc provides a wrapper around a C compiler, which also invokes the Sparse static analysis tool.

---

