---
title: "character input from stdin"
date: 2010-08-13
forum: Programming Talk
---

### Post by rockom on 2010-08-13
Hello,

Most of my experience is in micros, dos, and windows.  So, I'm missing something really basic here when working with a terminal console. 

I'm trying to use getc to get some user input.  They are not passed from the terminal unless I hit the carriage return.  I need to poll for a string of characters entered from the keyboard but I'll never get a CR.  I'm using a barcode scanner...

I've been playing with all kinds of functions...scanf, getc, getchar, ect....
What am I missing?

Thanks,
-Rocko

---

### Post by dwhitney67 on 2010-08-13
You need to setup the stdin stream to be non-blocking.

Here's a simple example of how one can do that:
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <string.h>

// For yesOrNo, 1 is to enable non-blocking, 0 to disable (ie blocking).
int enableNonBlocking(int yesOrNo, int fileno)
{
   static struct termios old;

   if (yesOrNo)
   {
      struct termios tmp;

      if (tcgetattr(fileno, &old))
      {
         return -1;
      }

      memcpy(&tmp, &old, sizeof(old));

      tmp.c_lflag &= ~ICANON & ~ECHO;

      if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
      {
         return -1;
      }
  }
  else
  {
     tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
  }

  return 0;
}


int main()
{
   enableNonBlocking(1, STDIN_FILENO);

   printf("Enter a sentence ending with a .:\n");

   int ch = -1;

   while ((ch = getchar()) != '.')
   {
      putchar(ch);
   }
   puts(".");

   enableNonBlocking(0, STDIN_FILENO);

   return 0;
}

```

P.S.  Bear in mind that enableNonBlocking() is not re-entrant.  Modify it if you need to deal with multiple streams.

---

### Post by rockom on 2010-08-13
dwhitney67,

That rocks!  Thanks for your help.
Only thing I needed to do was a slight change to your while loop.
I found the need for an IF.

```
while ((ch = getchar()) != '.')
   {
      if (ch != -1)
        putchar(ch);
   }
```

This will easily adapt into my application.

Thanks again,
-Rocko

---

