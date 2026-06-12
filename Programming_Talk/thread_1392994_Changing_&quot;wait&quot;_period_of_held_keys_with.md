---
title: "Changing &quot;wait&quot; period of held keys with NCurses?"
date: 2010-01-28
forum: Programming Talk
---

### Post by Buuntu on 2010-01-28
I am just learning NCurses and am trying to make simple terminal games.  Right now I'm currently trying to finish a pong game.  The language I am using is C (not C++, but C).

Anyways, my problem is with how holding a key is processed.  
In most applications, there is a delay from the time when you hold the key, to the time it registers as you holding it and begins writing the key very quickly.  I need to shorten this "waiting period", since for pong it's pretty essential that you be able to hold keys and that there is no delay when switching between two keys to change directions.  

Could someone point me in the right direction for a function or other method of changing this?

Thanks

---

### Post by dwhitney67 on 2010-01-28
I wish I could help you specifically with ncurses, however I have not used it in nearly 10 years.  However, I think what you want is to be able to set up non-blocking I/O, such that there is no delay between obtaining a keystroke from the user.

I know that ncurses offers this feature; it's touted all of the time on this forum.  If you need to overcome this hurdle immediately, and yet standby for a 'better' solution, for now you should be able to use something like this to setup your input-stream to be non-blocking:
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

  /* setup stdin to be non-blocking */
  if (tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &tmp))
  {
    return -1;
  }

  /* get input */
  ch = getchar();

  /* re-enable stdin blocking */
  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);

  return ch;
}

```
I'm not stating this is exactly what you need, but it is close.  It is probably best to turn-off (disable) blocking one time in your code, then from there, acquire input using getchar().  When you app is done, if you need, you can restore, or turn-on, blocking again.

---

### Post by Buuntu on 2010-01-28
Sorry for not being clear, but that isn't what I need.

I don't need it to not stop at input commands, I already know how to do that (with nodelay(stdscr,TRUE)).  What I'm trying to do is get rid of the delay after you press a key for it to register as being held.

An example is better:  
Go to anywhere where you can type and see your text as it is being typed (text editor, URL bar, chat, etc...).  Now hold down the letter 'T'.  Do you see how it displays the letter T once, waits about .5 seconds, then starts displaying 'T's really fast?  THAT is what I'm trying to get rid of.  I want it to display 'T's really fast to start with(obviously not necessarily Ts, that's just an example).

---

### Post by itcotbtoemik on 2010-01-29
That's a lower-level feature, which xset would control,
for xterm, etc.

---

### Post by Buuntu on 2010-01-29
There is no way to change that from within the C program then?

---

### Post by wmcbrine on 2010-01-29
It's outside the scope of ncurses. You might be able to change it from a program, but not via ncurses, and not in a way that would be portable between (for example) Gnome Terminal and the virtual console.

---

