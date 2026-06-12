---
title: "Curses (terminal) programming question"
date: 2009-03-02
forum: Programming Talk
---

### Post by Cracauer on 2009-03-02
What is the easiest way to check from a C program whether the terminal (if any) is currently in line mode (aka shell or non-curses program) or whether it is running a program with a curses user interface?

I have a program that I want to print stuff, but only if there's no UI to mess up at this time.

---

### Post by dwhitney67 on 2009-03-02
When a terminal is being managed by an ncurses program, are you able to write to this terminal using your program?

It has been over 10 years since I wrote an ncurses application (a simple spreadsheet app), and from the best of my recollection, my command line prompt disappeared on me, thus preventing me from launching another application.

---

### Post by wmcbrine on 2009-03-02
I agree, the question doesn't really make sense. The terminal belongs to one app at a time.

---

### Post by dwhitney67 on 2009-03-02
> **wmcbrine said:**
> I agree, the question doesn't really make sense. The terminal belongs to one app at a time.
That's what I'm thinking too, but what if the ncurses app is run as a background process?  Or if the system issues a warning that the system is about to be shutdown?

---

### Post by nvteighen on 2009-03-02
I don't understand the problem either. I mean, why would you need such a thing?

If a terminal port is used by some program, you can't write to it, no matter whether it uses ncurses or not. If there's no available terminal port, then, whatever you try will be useless because the user just doesn't want to have a terminal available... because it's the user who opens new terminals, either through the X-based emulators or the "real" tty consoles.

The only cases something like this could happen would be in the case of a daemon. There, the most sane idea, IMO, is to create a log and output stuff there of needed... the logfile will always be available for use.

But it'd be great if you told us much clearly what you intend to do...

---

### Post by Cracauer on 2009-03-02
Uh?

Simple example:

```

#!/bin/sh
while : ; do
  echo gonzo
  sleep 1
done

```

That will echo "gonzo" just fine every second, even when there's an emacs or mutt running. Disrupting the screen of the foreground program.

What I need is:
```

#!/bin/sh
while : ; do
  if terminalisinlinemode ; then echo gonzo ; fi
  sleep 1
done

```

---

### Post by Cracauer on 2009-03-02
This works perfectly:

```

#! /bin/sh

while : ; do
        stty | grep -q onlcr || echo foobar
        sleep 1
done

```

Now I just need the C equivalent.

---

### Post by dwhitney67 on 2009-03-02
That would be tcgetattr() of the termios family of functions.  I'm still unclear though, how one gets the file-descriptor for the current terminal from within a C program.

P.S.  Maybe this would work?
```

#include <termios.h>
#include <unistd.h>
#include <stdio.h>

int main()
{
  struct termios tios;
  tcgetattr(0, &tios);

  printf("onlcr is %s\n", (tios.c_oflag & ONLCR ? "active" : "inactive"));
}

```

---

### Post by Cracauer on 2009-03-02
I will have to open /dev/tty.

But that is available even if the program is backgrounded from the shell with "&".

It's kind of wasteful but we are talking about human attention span timeframes here, aka 1 second.

---

### Post by dwhitney67 on 2009-03-02
I edited my post to indicate that the file-descriptor of 0 could possibly be used.  I always forget which fd is 0... stdin or stdout... but it applicable to the terminal is it not?

---

### Post by Cracauer on 2009-03-02
> **dwhitney67 said:**
> I edited my post to indicate that the file-descriptor of 0 could possibly be used.  I always forget which fd is 0... stdin or stdout... but it applicable to the terminal is it not?

No, that would break if you do something like

```

someprog | the_prog_discussed_here &

```

... or any invocation of a script containing this.

But you could try fd0 and only if the curses call fails on it you go and open /dev/tty.

Thanks, guys.

---

