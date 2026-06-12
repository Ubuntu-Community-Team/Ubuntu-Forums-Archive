---
title: "SIGALRM doesn't work when using termios"
date: 2009-05-21
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-05-21
Hello,

Does anyone have a clue why using setitimer() and SIGALRM won't work if you modify the terminal using termios.h?

Every time I run it I get segfault or the original signal handler (not the one I set).

Just having  ```
  struct termios oldTerm, newTerm;
``` seems to cause trouble.

If I remove that code, it seems to behave just fine.

Anyone have a clue?

---

### Post by stroyan on 2009-05-21
You may have a bad call to set your signal handler.
If you have a mistake in the arguments it could still work some of the time when uninitialized memory is being used that contains values that are accidentally acceptable.  Those new variables may take up space in the data area or stack thereby disturbing that unlikely 'good' behavior.

Watch for compiler warnings about parameter mismatches.

You could also run your program under the strace command to report the arguments and results of all system calls that your program makes.  That can often make problems more visible to you than rereading your own source code.

---

### Post by MR.UNOWEN on 2009-05-21
Well it looks like that may be the cause of it...

I added char a[5111111]; and it now works fine.

I ran strace on it, I don't know what to exactly to look for...

All my calls to sigaction() look fine.

---

### Post by dwhitney67 on 2009-05-21
Well, we could help you troubleshoot the problem, but it will be extremely difficult unless you post your code.

To test the setitimer/sigaction combo, I conjured up this simple program which demonstrates them in action; perhaps it can assist you.
```

#include <signal.h>
#include <sys/time.h>
#include <termios.h>

#include <unistd.h>
#include <string.h>
#include <stdbool.h>
#include <stdio.h>

bool done = false;

void sighandler(int signo)
{
  if (signo == SIGALRM || signo == SIGINT) {
    done = true;
  }
}

int getch();


int main()
{
  /* setup signals */
  struct sigaction act;

  memset(&act, 0, sizeof(struct sigaction));
  act.sa_handler = sighandler;

  sigaction(SIGINT,  &act, 0);
  sigaction(SIGALRM, &act, 0);

  /* setup timer */
  const int THIRTY = 30;
  struct itimerval value = { {0, 0}, {THIRTY, 0} };
  setitimer(ITIMER_REAL, &value, 0);

  /* main loop */
  int  ch_typed  = 0;
  char str[1024] = {0};

  printf("get ready to test your typing proficiency.\n");
  printf("press enter to begin the test...\n");
  getchar();
  printf("type --> ");

  while (!done) {
    int ch = getch();

    if (ch != -1) {
      str[ch_typed++] = ch;
    }
  }
  printf("\n\nTIMES UP!\n\n");
  printf("you typed %d character(s) in %d seconds\n", ch_typed, THIRTY);
  printf("this is what you typed: '%s'\n", str);
}


int getch()
{
  int            ch;
  struct termios old;
  struct termios tmp;

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

  ch = getchar();

  if (ch != -1) {
    putc(ch, stdout);
  }

  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);

  return ch;
}

```

---

