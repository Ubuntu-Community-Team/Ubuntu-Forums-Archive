---
title: "Outputing over the same line in the console?"
date: 2010-04-21
forum: Programming Talk
---

### Post by ownaginatious on 2010-04-21
I've noticed some console based applications in the terminal output to the same line (i.e. how wget will output the loading bar to the same line, as if it just updates the content of that line while downloading).

I was interested in doing the same for a small program I made in C. Is this difficult to do, and how would I go about doing it?

Right now I just output a new line with the percentage complete each time, which I think is a little lame. :p

Thanks

---

### Post by Bachstelze on 2010-04-21
Use the carriage return character ('\r' in C):

[php]#include <stdio.h>
#include <unistd.h>

int main(void)
{
    printf("Hello");
    fflush(stdout);
    sleep(2);
    printf("\r");
    printf("World !\n");
    return 0;
}
[/php]

You need fflush() to flush the output buffer because output by default is line-buffered, so if you omit it, the "Hello" part will not appear.

---

### Post by ownaginatious on 2010-04-21
> **Bachstelze said:**
> Use the carriage return character ('\r' in C):

[php]#include <stdio.h>
#include <unistd.h>

int main(void)
{
    printf("Hello");
    fflush(stdout);
    sleep(2);
    printf("\r");
    printf("World !\n");
    return 0;
}
[/php]

You need fflush() to flush the output buffer because output by default is line-buffered, so if you omit it, the "Hello" part will not appear.

Awesome, exactly what I want. Thanks :).

Just one more thing though; the cursor sits on-top of my output. Is there a way to make it sit on the line after (or maybe a couple lines after if I want a multi-line updating output)?

Thanks again :)

---

### Post by Bachstelze on 2010-04-21
Multi-line updating output is a lot more complicated. The '\r' character just moves output to the beginning of the current line, it cannot "go up". If you want multi-line updating output, you'll have to use e.g. ncurses.

Of course, you could also just use one very long line in order to give the illusion of multi-line output, since most terminals will wrap it on multiple lines, but it's not trivial either (you'd have to take into account the width of the output terminal, for example).

---

### Post by pconroy on 2010-04-21
> **ownaginatious said:**
>  Is there a way to make it sit on the line after (or maybe a couple lines after if I want a multi-line updating output)?


man ncurses

and Google "curses tutorial".

Note ncurses is a "New" version of curses.  New being relative as its ??10?? years old or so.  You can google for curses or ncurses examples to get started.

---

