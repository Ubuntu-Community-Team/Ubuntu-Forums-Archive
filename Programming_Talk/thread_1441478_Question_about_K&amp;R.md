---
title: "Question about K&amp;R"
date: 2010-03-28
forum: Programming Talk
---

### Post by superarthur on 2010-03-28
I am now reading The C programming language by K&R
There is a part at the beginning where it teaches character counting.
[PHP]
#include <stdio.h>

main()
{
    long nc;

    nc = 0;
    while (getchar() != EOF)
        ++nc;
    printf("%ld\n", nc);
}
[/PHP]
I compiled and ran it. I assume it counts the number of characters in standard input.
I type something and clicked enter, but nothing happened.
How do I make it show the number of characters?
And I don't understand why is there EOF for standard input. I am not actually giving it a file, how can there be End Of File?

Many thanks in advance,
Arthur

---

### Post by CptPicard on 2010-03-28
Well, there can be an "end of file" for standard-input, because from the UNIX-style operating system perspective, a lot of stuff is a "file" even when it isn't, physically ;)

Try hitting Control-D to send the EOF to stdin, that should terminate your program.

---

### Post by dwhitney67 on 2010-03-28
When you are done inputting your character data, press ctrl-d and that should provide the EOF you seek.  Note that the <return> key will count as one of the characters you enter.

If you do not wish to press <return>, then try entering ctrl-d twice.  I'm not sure why this is required.

P.S.  Your main() function should be declared to return an int (regardless of the dated K&R material).  And because of such, you should actually return a value.

```

...

int main(void)
{
   ...

   return 0;
}

```

---

### Post by superarthur on 2010-03-28
> **CptPicard said:**
> Well, there can be an "end of file" for standard-input, because from the UNIX-style operating system perspective, a lot of stuff is a "file" even when it isn't, physically ;)

Try hitting Control-D to send the EOF to stdin, that should terminate your program.
Thanks a lot.
I tried control-c and control-z
I never realised there is control-d as well
I don't understand why the book doesn't tell me about something so essential to run the programs. :(

btw, what does control-d mean?

---

### Post by rplantz on 2010-03-28
> **superarthur said:**
> 
btw, what does control-d mean?

Control-d is the ASCII code for the control character, End Of Transmission (EOT). You may wish to read the wikipedia entry for ASCII, which explains control characters.

---

### Post by Compyx on 2010-03-29
> **dwhitney67 said:**
> When you are done inputting your character data, press ctrl-d and that should provide the EOF you seek.  Note that the <return> key will count as one of the characters you enter.

If you do not wish to press <return>, then try entering ctrl-d twice.  I'm not sure why this is required.


Since the terminal is line-buffered mode, an EOT (Ctrl-D) only counts as EOF when it's the only character on a line, when used after other characters have been typed, it acts as a linefeed since there's still data in the buffer which needs to be sent.

---

### Post by CptPicard on 2010-03-29
> **superarthur said:**
> 
I don't understand why the book doesn't tell me about something so essential to run the programs. :(


This tells you something about K&R... it's a concise C book, not a UNIX programming tutorial :)

---

### Post by superarthur on 2010-03-29
> **CptPicard said:**
> This tells you something about K&R... it's a concise C book, not a UNIX programming tutorial :)

I wasn't told knowledge about UNIX is required to read this book. :(

---

### Post by Compyx on 2010-03-29
> **superarthur said:**
> I wasn't told knowledge about UNIX is required to read this book. :(

It isn't. It's a book about the C programming language, not about operating systems. The authors assume the reader has some working knowledge of their operating system, at least to the extent of executing programs, invoking the compiler and/or linker and using a text editor. The systems that C and it's library have been ported to are so many and diverse it's just not feasible to include instructions on compiling and running programs for all or some of those systems.

The book predates the world wide web, otherwise the authors probably would have told the reader to look such information up on web. ;)

---

### Post by rabidbadger on 2010-03-29
> **superarthur said:**
> I wasn't told knowledge about UNIX is required to read this book. :(

You don't need to know a lot...

In [the thread]("http://ubuntuforums.org/showthread.php?t=1427382") that you asked for recommendations on a good C book to read, I did [suggest]("http://ubuntuforums.org/showpost.php?p=8960143&postcount=12") that you read [this]("http://c-faq.com/%7Escs/cclass/krnotes/top.html") *alongside* K&R. If you'd done so, you'd have found out about how to send the EOF in [the section]("http://c-faq.com/%7Escs/cclass/krnotes/sx4f.html") talking about page 17/18 in K&R (which you are on) ;)

Stick with it!

---

### Post by superarthur on 2010-03-29
> **rabidbadger said:**
> You don't need to know a lot...

In [the thread]("http://ubuntuforums.org/showthread.php?t=1427382") that you asked for recommendations on a good C book to read, I did [suggest]("http://ubuntuforums.org/showpost.php?p=8960143&postcount=12") that you read [this]("http://c-faq.com/%7Escs/cclass/krnotes/top.html") *alongside* K&R. If you'd done so, you'd have found out about how to send the EOF in [the section]("http://c-faq.com/%7Escs/cclass/krnotes/sx4f.html") talking about page 17/18 in K&R (which you are on) ;)

Stick with it!

Thanks a lot.:D Sorry that I forgot to go back to the thread after I got the book. :P

---

### Post by whoop on 2010-03-29
Maybe you where expecting hitting a couple of keys, than hitting return and letting the program return the result. 
That could be something like this:
```

#include <stdio.h>

main()
{
    long nc;

    
    while (getchar() != EOF){
        nc = 1;
        while (getchar() != '\n')
            ++nc;
        printf("%ld\n", nc);
    }
}  

```

Or if you want the program to exit by itself:
```

#include <stdio.h>

main()
{
    long nc;

    nc = 0;
    while (getchar() != '\n')
        ++nc;
    printf("%ld\n", nc);
}  

```

---

