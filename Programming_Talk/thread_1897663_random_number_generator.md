---
title: "random number generator"
date: 2011-12-19
forum: Programming Talk
---

### Post by Lilykos on 2011-12-19
hello everyone i want to make a random number generator in c but i have no idea how to do it because i want the numbers to be inside specific limits! for example i need the generator to create a number between 0 and 120...how is that possible?i have googled it but unfortunately all the answers are about srand which gives completely random numbers....any ideas?

---

### Post by Petrolea on 2011-12-19
You can use /dev/random. [http://en.wikipedia.org/wiki//dev/random](http://en.wikipedia.org/wiki//dev/random)

It's hard to make a good random generator by yourself. You must understand that NOTHING is random.
You have to choose some source which doesn't give constant results, for example speed of reading/writing to disk and convert it to desired numbers. The source should be something that rarely passes the same value and isn't very predictable.

---

### Post by cgroza on 2011-12-19
Do you want to create a random number generator like srand from scratch or you just want to get the numbers in a specific range?

If the former, you can easily do it with a modulus operation:
```

srand() %  100; //returns number in the range 0 .. 99

```

---

### Post by pbrane on 2011-12-19
If you want to implement a random number generator you should have a look at this: [http://www.haoli.org/nr/bookcpdf.html]("http://www.haoli.org/nr/bookcpdf.html"), scroll down to the random numbers section.

To properly get a value between 0 and 120 you could try something like this.
```

#include <stdlib.h>
...

j = (int) (121.0 * rand() / (RAND_MAX + 1.0));

...

```

---

### Post by Arndt on 2011-12-20
> **pbrane said:**
> If you want to implement a random number generator you should have a look at this: [http://www.haoli.org/nr/bookcpdf.html]("http://www.haoli.org/nr/bookcpdf.html"), scroll down to the random numbers section.

To properly get a value between 0 and 120 you could try something like this.
```

#include <stdlib.h>
...

j = (int) (121.0 * rand() / (RAND_MAX + 1.0));

...

```

What's the +1.0 for?

---

### Post by Tony Flury on 2011-12-20
The challenge as always with things like srand is that they are actually psuedo-random - they look random enough, but they are actually based on repeated application of a mathematical formula and are therefore predictable.

The predicatbility can have it's uses - srand has with it the ability to seed the generator - so long as you seed the generator each time the sequence is utterly predictable (which is great for things like testing, or re-creating semmingly random landscapes (without having to store all the details of the landscape - you just store the seed).

If you want complete randomness (i.e. untirely unpredictable), then you have to use some of the techniques mentioned by Petrolea.

---

### Post by pbrane on 2011-12-20
> **Arndt said:**
> What's the +1.0 for?

You should read the random number chapter in the link I posted.

---

### Post by Arndt on 2011-12-20
> **pbrane said:**
> You should read the random number chapter in the link I posted.

Page 275 ends with the promising "If you want a random float value between 0.0 and 1.0, you get it by an expression like"

but on the next page another section starts, so we don't get to see what that expression is.

---

### Post by Lilykos on 2011-12-20
thanks a lot everone all these were really helpful!!!

---

### Post by pbrane on 2011-12-20
> **Arndt said:**
> Page 275 ends with the promising "If you want a random float value between 0.0 and 1.0, you get it by an expression like"

but on the next page another section starts, so we don't get to see what that expression is.

The next page shows this expression:
```

x = rand()/(RAND_MAX+1.0);

```

I'm not sure why you can't see the other pages. I actually have the book but I can view all the pages on line.

EDIT: Oh I think I see why. You have to view each section as a separate pdf. the Introduction section has the beginning of the next section on that last page. If you open the next section called *Uniform Deviates* you can see the whole section.

---

