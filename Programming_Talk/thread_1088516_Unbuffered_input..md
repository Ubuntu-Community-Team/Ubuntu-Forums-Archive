---
title: "Unbuffered input."
date: 2009-03-06
forum: Programming Talk
---

### Post by kcode on 2009-03-06
Hello,
I want a function which on taking a character transfers the control to next line without pressing enter. Something like getch(), which is not included in glibc++(if I'm correct).

Thanks

---

### Post by dwhitney67 on 2009-03-06
I've seen your question asked many times before, and answered too!

Either the search engine on the Ubuntu Forums site is not working, or user's are failing to perform adequate research before posting here.

Here's an implementation for getch() that sets up the input stream to be non-blocking; you can capture one character at a time.
```

#include <stdio.h>
#include <termios.h>
#include <unistd.h>
#include <string.h>

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

  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);

  return ch;
}

```

---

### Post by kcode on 2009-03-06
> **dwhitney67 said:**
> 

Either the search engine on the Ubuntu Forums site is not working, or user's are failing to perform adequate research before posting here.


Was in hurry, never thought. I apologize.

---

