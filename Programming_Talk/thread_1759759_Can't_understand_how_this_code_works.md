---
title: "Can't understand how this code works?"
date: 2011-05-16
forum: Programming Talk
---

### Post by hugom on 2011-05-16
Hi there,

I'm trying to teach myself C programming while I'm injured and I have a book for beginners but I have got a bit confused at this point.

This program is meant to count the number of characters in something, but when I compile and run it it just comes up with a blank terminal window.

I know this might be a pretty stupid question but would really like to know what to do. This is the code I use here ..

#include <stdio.h>

/* count characters in input; 1st version */

main()
{
 long nc;

 nc = 0;
 while (getchar() != EOF)
    ++nc;
 printf("%ld\n", nc);
}

Any help would be hugely appreciated, Cheers.

---

### Post by Tony Flury on 2011-05-16
it does exactly what it is supposed to.

In the "blank window" type in a load of characters (it does not provide any sort of prompt) - followed by "Ctrl-D" (which is the keypress for EOF). The program will then tell you how many characters you type.

I have provided comments to the code - it is pretty simple:

```

#include <stdio.h>  /* --- Standard IO Library --- */

/* count characters in input; 1st version */

main()
{
long nc;

nc = 0; /* --- Always make sure the count is zero -- */
/* -----
A tight loop - get and count every character entered until the user enters EOF (CTRL-D) 
The "++nc;" is within the loop and increments the nc Count
---- */
while (getchar() != EOF)
   ++nc;
/* ---- Output the count formatted as a long decimal --- */
printf("%ld\n", nc);
}


```

---

### Post by hugom on 2011-05-16
Ctrl D, that's what I needed to know.

Thank you very much Tony great help!

---

