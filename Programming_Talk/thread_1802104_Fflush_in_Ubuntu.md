---
title: "Fflush in Ubuntu"
date: 2011-07-11
forum: Programming Talk
---

### Post by Fat_Bastard on 2011-07-11
Hi! I just began learning to program in C. I have this exercise that I did with no problems in Windows, but it doesen't work in Ubuntu, because of the fflush() function. I was told that fpurge() worked on Linux, but I've tried it and the compiler doesen't admit it.

```


#include<stdio.h>

int main ()
{
    char a,b;
    
    printf ("Insert a letter:");
    scanf ("%s", &a);
    fflush (stdin);

    printf ("Insert another letter:");
    scanf ("%s", &b);
    
    printf ("You wrote %s and %s\n", &a, &b);
    printf ("\n");

return (0);
    
}


```When I run it, it gets a blank space between "wrote" and "and", instead of the first letter.

Thanks in advance for your answer. :D

---

### Post by Bachstelze on 2011-07-11
[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392)

---

### Post by Bachstelze on 2011-07-11
Also do not use scanf(), ever. [http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

---

### Post by Fat_Bastard on 2011-07-12
Thanks for your help! :)

---

### Post by nvteighen on 2011-07-13
> **Bachstelze said:**
> Also do not use scanf(), ever. [http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

I disagree: (f/s)scanf is perfectly *safe* when used for %d, %c, %f... AFAIK, it's impossible to produce a buffer overflow with any of those format instructions (?), but only with %s.

The other problems of (f/s)scanf, e.g. that it doesn't tell you where it failed, are not safety issues, but just a poor interface... in a language with very poor string support :P

---

### Post by Bachstelze on 2011-07-13
No one said they were not *safe*, but even though a program behaving unpredictably is not as bad as a buffer overflow, it's still not desirable, is it? When sscanf() fails, you don't really need to know where, you can just try another conversion, or do something else with the input. If scanf() fails, the input is gone, and you don't even know exactly how much of it.

---

### Post by nvteighen on 2011-07-13
> **Bachstelze said:**
> Also do not use scanf(), ever. [http://c-faq.com/stdio/scanfprobs.html](http://c-faq.com/stdio/scanfprobs.html)

Uh... forget my last post. I think I've now understood what you meant: that even in the safe cases, scanf suffers from a lot of other problems, some of which I wasn't even aware. Thanks for the link, it was quite informative... and my apologies.

---

