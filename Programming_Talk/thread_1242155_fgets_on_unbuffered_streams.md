---
title: "fgets on unbuffered streams"
date: 2009-08-16
forum: Programming Talk
---

### Post by soltanis on 2009-08-16
I'm trying to use a C program that basically reads some information from a FIFO pipe (made using mkfifo). What bothers me is that when I pipe information into the program (on stdin) from the terminal, it works perfectly; when I pipe it from another program, it also works perfectly, but for some reason, when I use a FIFO, it does weird things (like repeat characters or lines).

I have a feeling that the problem is caused by buffering. However, I'm also using fgets to read lines at a time; I would think that necessarily, fgets needs to perform line-buffering. The manpages do not define the behavior of the function when buffering is turned off. Any thoughts?

---

### Post by dwhitney67 on 2009-08-16
I have never used a FIFO before, so for grins I wrote two small apps to test it out.  Perhaps the following code can help you sort out the anomaly you are having with your app.

Reader.c:
```

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   // create fifo
   int fifo = mkfifo("./fifo", 0600);

   if (fifo == 0) {
      // open fifo for reading
      FILE* fd = fopen("./fifo", "r");

      if (fd) {
         char buf[256] = {0};

         while (fgets(buf, sizeof(buf), fd)) {
            printf("%s", buf);
         }
      }
      else {
         printf("Failed to open ./fifo for reading.\n");
         return -2;
      }

      unlink("./fifo");
   }
   else {
      printf("Failed to create ./fifo.\n");
      return -1;
   }

   return 0;
}

```


Writer.c:
```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
   // open fifo for writing
   FILE* fd = fopen("./fifo", "w");

   if (fd) {
      const char* msg = "Hello World.\n";   // fgets() of Receiver expects a newline.

      while (1) {
         fputs(msg, fd);
         fflush(fd);       // use this to flush fifo buffer
         sleep(1);
      }
   }
   else {
      printf("Failed to open ./fifo for writing.\n");
      return -1;
   }

   return 0;
}

```

---

### Post by Lux Perpetua on 2009-08-17
If dwhitney67's post didn't help you solve your own problem, you might consider posting some code. We're not telepathic, here, you know; it's kind of hard to diagnose code we can't see!

---

