---
title: "C or Pascal? (Funny MS source code)"
date: 2006-10-12
forum: Programming Talk
---

### Post by kinghajj on 2006-10-12
If you haven't heard the news, the source code to MS-DOS 6 (or 5?) is on Google Code Search. Someone dugg up this little gem.

from *cmd/fdisk/profile.h*
```

/*                                                                          */
/****************************************************************************/
/* Define statements                                                        */
/****************************************************************************/
/*                                                                          */

#define BEGIN    {
#define END      }

```

from *cmd/fdisk/profile.c*
```

void    main()

BEGIN

unsigned i;

        /* Main Menu */
        clear_screen(0,0,24,79);
// ...
        for (i=0;i < 92;i++)
           BEGIN
            insert[i] = 'x';
           END

```

I got a good laugh from it.

---

### Post by coder_ on 2006-10-13
What the heck!?  :P
Silly M$.

---

### Post by Arndt on 2006-10-13
> **coder_ said:**
> What the heck!?  :P
Silly M$.

Look at the original source code for the Bourne shell, if you can find it.

---

### Post by wieman01 on 2006-10-13
Sweet. I still remember the fdisk menu/screen for some reason. :-) Unsigned integers, defines, void main()'s... Long, long time ago, I still do remember...

---

### Post by coder_ on 2006-10-13
arndt: I found it - [http://minnie.tuhs.org/UnixTree/V7/usr/src/cmd/sh/](http://minnie.tuhs.org/UnixTree/V7/usr/src/cmd/sh/)
That's really odd! :P

ALGOL68 styled it looks?  Which seems to be what the Bourne Shell's syntax was based off of too.  Very interesting :P

---

### Post by Lord Illidan on 2006-10-13
Why is it funny? I am not too good in C...

---

