---
title: "srand(time(NULL)) error message"
date: 2013-03-08
forum: Programming Talk
---

### Post by seeker.k3 on 2013-03-08
Hi
I'm not a programmer, but I want to get some C code to work for some study that I'm doing in cognitive psychology. It's a mathematical model; it does a calculation and returns a value. The code was written in 1996, and when I try to compile it (I'm typing gcc filename), I get a number of error messages. The main one relates to the random number generator.
The original code was:
```
 #include "ran1.c"
/* random seed */
long     IDUM    = -3;
```

I have replaced only the first line with:

```
#include <time.h>

srand(time(NULL));
int r = rand();
```

but I get this message:
```
43:7: error: expected declaration specifiers or ‘...’ before ‘time’

44:1: error: initialiser element is not constant
```

I think I'm heading in the right direction, but I don't know enough about programming to get it right. I really don't want it to return the wrong value.
Any help would be appreciated. Thank you.

---

### Post by dwhitney67 on 2013-03-08
It would be immensely helpful to see the actual implementation you have versus a snip of code as you have provided.

A simple example of using srand() and rand() would be something like:
```

#include <stdlib.h>
#include <time.h>

const unsigned int MAX_NUM = 1000;

int main()
{
    srand(time(NULL));

    unsigned int num = rand() % MAX_NUM;   // num can range from 0 through (MAX_NUM - 1)
}

```

---

### Post by steeldriver on 2013-03-08
Just a note of caution about PRNGs - based on the name (ran1.c) and the negative-long seed (IDUM) it looks like you are trying to replace the Numerical Recipes implementation? If so, that's a long-period floating point PRNG - depending what your model is doing (and how many times it's doing it) the system rand() may or may not be a suitable replacement.

---

### Post by seeker.k3 on 2013-03-08
Thanks for your helpful comments. Any information I can gather is helpful.
> **dwhitney67 said:**
> It would be immensely helpful to see the actual implementation you have versus a snip of code as you have provided.

Does this make it clearer?
[ATTACH]239943[/ATTACH]
The attached model.txt file is the C code that I think might be relevant. I've just killed about 2/3 of the lines from the middle of the file.

Just to recap, when I tried to compile this, I got an error message in relation to the random generator.
Thank you.

---

### Post by steeldriver on 2013-03-08
Is there any particular reason you need to replace the original Numerical Recipes ran1 implementation? The license terms are not onerous afaik

[http://apps.nrbook.com/c/index.html](http://apps.nrbook.com/c/index.html)

I'd suggest including the necessary declarations and compiling the ran1.c file separately rather than doing #include "ran1.c" though

---

### Post by seeker.k3 on 2013-03-08
ok, Thanks again.
```
rip@Duck:/media/win/arjuna/current_study$ gcc memnew.c
memnew.c:22:18: fatal error: ran1.c: No such file or directory
compilation terminated.
```

Maybe I need to install something. This is Xubuntu Precise.

---

### Post by steeldriver on 2013-03-08
If it's the routine I think it is, you would need to get it from Numerical Recipes

If you buy the book, you can just type it in (it's only ~ 50 lines of code) - or you can get an electronic subscription

[http://www.nr.com/aboutNR3electronic.html](http://www.nr.com/aboutNR3electronic.html)

---

### Post by seeker.k3 on 2013-03-08
Thank you.

---

### Post by seeker.k3 on 2013-03-10
The code I have ran1.c includes:
```
#include "base.h"
```

Where do I look for that? 
Am I on the right track?

> I'd suggest including the necessary declarations and compiling the  ran1.c file separately rather than doing #include "ran1.c" though


I'm not sure what the necessary declarations are. I'm very low level here. As I say, I'm interested in a mathematical model in cognitive psychology, I'm not a programmer.
Thanks again.

---

### Post by seeker.k3 on 2013-03-20
Hello
I'm asking for help with format in C. The code has this line:
```
 fprintf( OUTD , "%s" , SPARAM[ i ] );
```
And the error is:
[HTML]format ‘%s’ expects argument of type ‘char *’, but argument 3 has type ‘struct PARAM’ [-Wformat][/HTML]
And I think you might need to know this:
```
/* strings used by the program */
#define  NPARAM 12
struct PARAM
{
  char *word;
} SPARAM[ NPARAM ] =
{
  "Length          ",
  "Strength        ",
  "Frequency       ",
  "Criterion Used  ",
  "Criterion ROC   ",
```
I've cut it short here, but I think that's enough.

I can see what the problem is, but my programming ability is very low level, and I have no idea about C. I need to change the "%s", right?
 I need to get this old C code working. Fortunately, I've had some good help here, and this is the only error message left. 
Comments gratefully received.

---

### Post by xb12x on 2013-03-20
try changing


 fprintf( OUTD , "%s" , SPARAM[ i ] );

to

 fprintf( OUTD , "%s" , (char *)(SPARAM+i) );

---

### Post by seeker.k3 on 2013-03-20
Thank you! I'm always very grateful for the help I get here. 

I'm VERY happy to get this code working.

---

### Post by spjackson on 2013-03-20
> **xb12x said:**
> try changing


 fprintf( OUTD , "%s" , SPARAM[ i ] );

to

 fprintf( OUTD , "%s" , (char *)(SPARAM+i) );
In my opinion, it is better to avoid casting in C as much as possible. I would regard the following as much cleaner.
```

fprintf( OUTD , "%s" , SPARAM[i].word );

```

---

### Post by seeker.k3 on 2013-03-20
This works better because the fonts in the output file are better now. The previous command produced computer garbage for those few words, even though the code ran through smoothly. I wasn't too worried (because I knew what the words were), but the fonts at output are perfect now.
```

fprintf( OUTD , "%s" , SPARAM[i].word );
```
Thank you.

---

