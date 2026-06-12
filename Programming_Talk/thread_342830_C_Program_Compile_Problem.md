---
title: "C Program Compile Problem"
date: 2007-01-20
forum: Programming Talk
---

### Post by indylarry on 2007-01-20
I am new to C programming. I am working on some examples out of a book and I am having problems with this code.

```
#include <stdio.h>

int main()
{
   int integer1, integer2, sum;

   printf( "Enter first integer\n" );
   scanf( "%d", &integer1 );
   printf( "Enter second integer\n" );
   scanf( "%d", &integer2 );
   sum = integer1 + integer2;
   printf( "Sum is %d\n", sum );

   return 0;
}
```

I used this command to compile:

```
cc -g  FIG02_05.C -o fig02_05.C
```

I am getting this output:

```
/tmp/ccQBJaAM.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

What am I doing wrong?

I am sure someone can help me with this and I appreciate the assistance.

---

### Post by Wybiral on 2007-01-20
Why don't you use "gcc FIG02_05.C -o Test"

I just compiled it... No problems.

I'm not entirely sure what "__gxx_personality_v0" but I've seen that from trying to compile C++ code in a C program... I have no idea why that program would cause it... And it didn't for me. Perhaps compiling a C program to a ".C" file isn't the best idea...

---

### Post by indylarry on 2007-01-20
Thanks

These are from the "C How To Program" CD.

I tried it again without the ".c" and still got the same output.  Then, I copied "FIG02_05.C" to "0205.c" and it worked like a charm.  I had problems with other files and I changed their names using the same convention as above and they now work as well.

Does GCC not like capitalized file names?

---

### Post by Mirrorball on 2007-01-20
An uppercase C is an extension for C++ files, that must have caused your error.

---

### Post by indylarry on 2007-01-20
You're right Mirrorball.  I uncapitalized the "C" and they work fine.  <sarcasm>Now all I have to do is rename every example file to make them work<sarcasm>.

---

### Post by Grey on 2007-01-21
Try using gcc rather than cc.  It should compile as C rather than detecting by extension.

---

### Post by indylarry on 2007-01-21
That didn't work.  I got the same output as I did earlier.  Once I uncapitalized the "C" it worked.  It did work fine when I used g++.

---

### Post by runningwithscissors on 2007-01-21
> **indylarry said:**
> You're right Mirrorball.  I uncapitalized the "C" and they work fine.  <sarcasm>Now all I have to do is rename every example file to make them work<sarcasm>.

Change to the directory where your c files are and run this at the bash prompt:

$ for i in ./*; do mv ${i} ${i/.C/.c}; done;

Problem solved!

---

### Post by Note360 on 2007-01-21
Try this.

```

gcc -x c 0205.C -o 0205.o

```

-x sets the language to c so that it doesnt read by file extesion.

---

