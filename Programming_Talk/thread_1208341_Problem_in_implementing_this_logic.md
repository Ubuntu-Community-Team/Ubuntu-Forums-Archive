---
title: "Problem in implementing this logic"
date: 2009-07-09
forum: Programming Talk
---

### Post by codingfreak on 2009-07-09
Hi

I had a problem in implementing the following logic in C.

```
while(1)
{
      <logic>
      printf("HI\n");
}
```What I wanted to do is the while loop should be keep on looping and print "HI" until I give a keypress. But it should not be waiting for the input from stdin which happens if I use a scanf or getchar() functions.

So is there any good solution for it ???

---

### Post by dwhitney67 on 2009-07-09
There is a solution; you would need to use non-blocking input, or alternatively, you can have the application listen for an interrupt, such as SIGINT (ctrl-c).

Since I have time to kill, here's examples of both:
```

#include <stdio.h>
#include <signal.h>

int done = 0;

void sighandler(int signo)
{
   done = 1;
}

int main()
{
  signal(SIGINT, sighandler);

  while (!done)
  {
     printf("Ciao!\n");
  }
  return 0;
}

```

Sorry... this one is lengthy, and probably includes system calls you've never seen before.
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <string.h>
#include <sys/select.h>

struct termios old;
struct termios tmp;

int setupNonBlocking()
{
  if (tcgetattr(STDIN_FILENO, &old))
  {
    return -1;
  }

  memcpy(&tmp, &old, sizeof(old));

  tmp.c_lflag &= ~ICANON & ~ECHO;

  if (tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &tmp))
  {
    return -1;
  }

  return 0;
}

void restoreBlocking()
{
  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);
}

int main()
{
   int done = 0;

   fd_set savefds;
   FD_ZERO(&savefds);
   FD_SET(STDIN_FILENO, &savefds);

   setupNonBlocking();

   while (!done)
   {
      fd_set readfds = savefds;
      struct timeval tv = {0, 100};

      if (select(STDIN_FILENO + 1, &readfds, 0, 0, &tv) > 0)
      {
         if (getchar() == 'q') done = 1;
      }
     
      printf("Ciao!\n");
   }

   restoreBlocking();

   return 0;
}

```

---

### Post by codingfreak on 2009-07-09
Thanks @dwhitney67

I think the first logic is not really a good one. But the second one is quite intresting and I will check that one.

---

