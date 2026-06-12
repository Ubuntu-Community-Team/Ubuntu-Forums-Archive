---
title: "arc4random usage"
date: 2009-05-30
forum: Programming Talk
---

### Post by gtmarks on 2009-05-30
[SIZE=3][FONT=Courier New]I am having trouble with arc4random on Ubuntu 9.04.  I installed the libbsd-dev package, and "man arc4random" does bring up the man page.  But if I try to compile this program:

#include <stdio.h>
#include <stdlib.h>

main()
{
  int x;
  x=arc4random();
  printf("%i\n", x);
  return 0;
}

I get the following result:

56$gcc -o test test.c 
/tmp/ccq9tscj.o: In function `main':
test.c:(.text+0xe): undefined reference to `arc4random'
collect2: ld returned 1 exit status

What am I doing wrong?


[/FONT][/SIZE]

---

### Post by gtmarks on 2009-05-31
My question has been answered by osor at LinuxQuestions.org: in order to use arc4random() in a C program one must link to libbsd when compiling: "gcc -lbsd -o command filename.c"

---

