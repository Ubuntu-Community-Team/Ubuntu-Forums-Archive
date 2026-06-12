---
title: "Getting a program to type into another program"
date: 2013-04-22
forum: Programming Talk
---

### Post by usernamer on 2013-04-22
I have a program, test, in which you need to enter the character 'y', followed by pressing <enter>.
I have a second program which runs the program, test, in the terminal, but I'm having serious issues of entering the character 'y' (and the enter)...:(

This is as close as I've got so far:
```
#include <stdio.h>
#include <unistd.h>

int main(void)
{
    FILE *terminal;
    char *name;

    name = ttyname(0);
    terminal = fopen( ttyname(0), "w" );

    system( "./test %s", name );
    fprintf( terminal, "y\r" );

    fclose(terminal);

    return 0;
}

```

- This will run the correct program to the correct terminal, and then print 'y' once you exit the program.
- Is there any way to get it to type the 'y' in the program (as though you open up the program, then hit 'y' and <enter> on the keyboard)?

Cheers for any light shed on the issue.

---

### Post by ofnuts on 2013-04-22
[http://jineshkj.wordpress.com/2006/12/22/how-to-capture-stdin-stdout-and-stderr-of-child-program/](http://jineshkj.wordpress.com/2006/12/22/how-to-capture-stdin-stdout-and-stderr-of-child-program/)

Then you write a "y" to the right file descriptor (and don't forget to fflush()).

---

### Post by usernamer on 2013-04-23
Thanks a lot, I'll look into that.

---

