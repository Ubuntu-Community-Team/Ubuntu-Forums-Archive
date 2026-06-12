---
title: "C: Question about getchar()"
date: 2010-02-01
forum: Programming Talk
---

### Post by Sporkman on 2010-02-01
Hi All,

I'm trying out the example on this page:

[http://www.cplusplus.com/reference/clibrary/cstdio/getchar/](http://www.cplusplus.com/reference/clibrary/cstdio/getchar/)

namely:

```
/* getchar example : typewriter */
#include <stdio.h>

int main ()
{
  char c;
  puts ("Enter text. Include a dot ('.') in a sentence to exit:");
  do {
    c=getchar();
    putchar (c);
  } while (c != '.');
  return 0;
}
```

It seems as though it should put stuff to screen as I type it, then once I type "." it should exit, but that's not what's happening - instead it echoes everything I type to screen, including "."s without stopping, then once I hit enter it re-echoes everything up to & including the "." but not beyond...

Does that sound right?

---

### Post by TennTux on 2010-02-01
> **Sporkman said:**
> Hi All,
```
/* getchar example : typewriter */
#include <stdio.h>

int main ()
{
  char c;
  puts ("Enter text. Include a dot ('.') in a sentence to exit:");
  do {
    c=getchar();
    putchar (c);
  } while (c != '.');
  return 0;
}
```
...
Does that sound right?

I believe that getchar() retrieves a character from the input buffer. However, the buffer is not processed until a new line (Return) is entered.

With getchar() you would need to type A<Enter>B<Enter>.<Enter> for it to work as you expect.

Hope this helps.

---

### Post by dwhitney67 on 2010-02-01
And as MadCow drilled into me before, getchar() returns an int, not a char.

Either way, you may want enable non-blocking I/O on stdin if you are looking to retrieve one character at a time until a period (.) is found.  Otherwise, just use fgets() to read in a string.

---

### Post by weresheep on 2010-02-01
> 
I believe that getchar() retrieves a character from the input buffer. However, the buffer is not processed until a new line (Return) is entered.


Yeah, this is how the C I/O library works. The abstraction that it presents to the C programmer is reading and writing entire lines. Getchar and friends simply read from the libraries buffer.

Also, getchar returns an 'int' not a char. It is typical to check the return value of getchar to see if it equals 'EOF' (defined in stdio.h) which is an indication that there is no more data to be read. You may want to change your code to something like this...

```

#include <stdio.h>

int main(void) {
  int c;

  puts("Enter text. Include a dot ('.') in a sentence to exit:");

  c = getchar();

  while (c != EOF && (char)c != '.') {
    putchar(c);
    c = getchar();
  }

  return 0;
}


```

-weresheep

---

### Post by Sporkman on 2010-02-01
**TennTux**: Thanks, that makes sense.

Basically I'm trying to implement a fancy user input functionality, like you'd get with gets() but that also has an initial value & arrow processing (so that the user can press the up arrow, for example, to scroll through previous entries).

**dwhitney67** - I googled nonblocking IO on stdin & found stuff about ncurses, which may be useful for what I want to do.

I'm a bit disappointed though - I usually like to roll my own stuff & wanted to implement this quick & dirty without diving into 3rd party packages.

---

### Post by Gatemaze on 2010-02-01
ehm it smells of homework and it's even in wiki
[http://en.wikipedia.org/wiki/C_file_input/output#The_EOF_pitfall](http://en.wikipedia.org/wiki/C_file_input/output#The_EOF_pitfall)

---

### Post by dwhitney67 on 2010-02-01
> **Sporkman said:**
> **TennTux**: Thanks, that makes sense.

Basically I'm trying to implement a fancy user input functionality, like you'd get with gets() but that also has an initial value & arrow processing (so that the user can press the up arrow, for example, to scroll through previous entries).

Never use gets(); don't even try to implement your own version of it.  Use fgets() instead.

> **Sporkman said:**
> 
**dwhitney67** - I googled nonblocking IO on stdin & found stuff about ncurses, which may be useful for what I want to do.

I'm a bit disappointed though - I usually like to roll my own stuff & wanted to implement this quick & dirty without diving into 3rd party packages.
Roll up to this:
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

int main()
{
   printf("Enter a sentence ending with a .:\n");

   int ch = -1;

   while ((ch = getch()) != '.')
   {
      putchar(ch);
   }
   puts(".");

   return 0;
}

```

P.S.  Normally one would not toggle the non-blocking of the stdin stream on every read; the code above is merely a quickie example.

---

### Post by Sporkman on 2010-02-01
> **dwhitney67 said:**
> Roll up to this:
...the code above is merely a quickie example.

Nice, thanks!

I can work with this - for example, here I am capturing the back arrow:

```
int main()
{
   printf("Enter a sentence ending with a .:\n");

   int ch = -1;

   while ((ch = getch()) != '.')
   {
      if ( ch==27 )
      {
         ch = getch();
         if ( ch==91 )
         {
            ch = getch();
            if ( ch==68 )
            {
               putchar('b');
            }
         }
         continue;
      }
      putchar(ch);
   }
   puts(".");

   return 0;
}

```

Thanks again. 8)

---

