---
title: "Another math.h dilemma"
date: 2012-02-20
forum: Programming Talk
---

### Post by paridhi on 2012-02-20
I am trying to use the sqrt function, and I have tried using the '-lm' flag to compile it.
However I am getting a very peculiar error. Perhaps I am overlooking something obvious but
thanks for helping in advance.

The following is the code snippet I am trying to compile:

```
#include <stdio.h>
#include <math.h>

int main()
{
  char   buf[50];
  double y;
  double a;

  a = (double)4.0;
  y = sqrt(a); <--------------------------
 

  sprintf(buf,"%f",y);
  printf("%s",buf);
  return 0;
}

```
I compile using, gcc -lm file.c, and I get the following error 
/tmp/ccAT3mOV.o: In function `main':
convertintstr.c:(.text+0x3b): undefined reference to `sqrt'
collect2: ld returned 1 exit status

Now, if instead of using the variable "a", i use a constant, I dont get the same error. 
For whatever reason, gcc is able to find the sqrt symbol, when I use pass in a constant as the
argument..
```
int main()
{
  char   buf[50];
  double y;
  double a;

  a = (double)4.0;
  y = sqrt(4.0); <--------------------------
 

  sprintf(buf,"%f",y);
  printf("%s",buf);
  return 0;
}

```
gcc -lm file.c

This compiles fine...? anyone with suggestions ?
Thanks
-Paridhi

---

### Post by Tony Flury on 2012-02-20
try putting the -lm to the end of the compile command line.

The reason it works with a constant, is that the compiler knows that the square root of 4 is 2.0 and therefore does a simple substitution.

---

