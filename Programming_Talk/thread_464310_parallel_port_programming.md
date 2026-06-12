---
title: "parallel port programming"
date: 2007-06-04
forum: Programming Talk
---

### Post by vertex78 on 2007-06-04
I am trying to learn how to use the parallel port for programming projects. I found this thread [http://ubuntuforums.org/showthread.php?t=400420&highlight=parapin&page=2](http://ubuntuforums.org/showthread.php?t=400420&highlight=parapin&page=2) and tried an example program in there:

> 
#include <stdio.h>
#include <stdlib.h>
#include <sys/io.h>
#include <unistd.h>
#include <sys/time.h>

#define PORT 0x378 /* use your port address here */

int main(int argc, char *argv[])
{
  int r;
  double l;

  if (iopl(3)) /* you could also use ioperm(PORT, 1, 1) */
    {
      fprintf(stderr, "couldn't get ports,\ntry running as root\n");
      exit(1);
    }

  srand(time(NULL));
  while(1) /*use Ctrl+C to exit */
    {
      l = (double)rand()/(double)RAND_MAX*256;
      r = (int)l;
      outb(r, PORT);
      usleep(500000);
    }

  return 0;
}


but when I try to compile with g++ I get these errors:

portTest.c: In function ‘int main(int, char**)’:
portTest.c:20: error: ‘time’ was not declared in this scope

What am I doing wrong here?

---

### Post by metroplex on 2007-06-04
I'm not 100% sure about this, but try:

#include <time.h>

..among the other #includes done.

And also, don't use g++ since your code seems to be written in C, not C++. Use gcc instead.

---

