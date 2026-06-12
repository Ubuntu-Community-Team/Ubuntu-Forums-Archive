---
title: "Basic C programming"
date: 2009-08-04
forum: Programming Talk
---

### Post by munky99999 on 2009-08-04
Hey guys, I'm teaching myself how to program. I'm having an unusual issue with my program.

```
#include <stdio.h>
#include <stdlib.h>

float epic(float x);

   float input, answer;

   main()
   {
     printf("Enter the # zero dawg: ");
     scanf("%d", &input);
     answer = epic(input);
     printf("\nThe root of %ld is %ld.\n", input, answer);
     printf("\nYou divided by 0 yo.\n");

     return 0;
  }

  float epic(float x)
  {
     float x_divided;

     x_divided = x / x;
     return x_divided;
  }

```

You CAN divide by ZERO.

---

### Post by kayvortex on 2009-08-04
And here, sir, is your Fields Medal...

---

### Post by Ferrat on 2009-08-04
You don't get the root by dividing x with x? x/x = 1 except to 0 where it's 0?

edit: 
To stop 0 from working just do a 
```

if ( input <= 0 ) 
    printf("\nYou divided by 0 yo.\n");
else
    {
     answer = epic(input);
     printf("\nThe root of %ld is %ld.\n", input, answer);
    };

```

---

### Post by munky99999 on 2009-08-04
> **kayvortex said:**
> And here, sir, is your Fields Medal...

So where do I claim the prize of $15,000?

> You don't get the root by dividing x with x? x/x = 1 except to 0 where it's 0?
well i wasnt really trying to get the root. Just dividing by zero.

[Dividing by zero is bad.]("http://halshop.files.wordpress.com/2007/03/phpw9jvl0pm.jpg")

:o

---

### Post by kayvortex on 2009-08-04
> So where do I claim the prize of $15,000?

Well, first there's the very minor matter of a $100 mailing fee, which will be reimbursed back to you, of course...

---

### Post by howlingmadhowie on 2009-08-04
you should get a warning when you compile it for using %ld in printf for a float.  what is actually displayed is pretty much random. if you instead use %f as the format you will get the correct response according to ieee 754: nan (not a number).

hope this clears it up a bit.

howie

---

### Post by kayvortex on 2009-08-04
Just out of interest, what does happen if you divide by zero in C? I've never actually tried it for fear of being sucked into the resulting event horizon.

Edit: Ok, a compile-time error, or else unexpected run-time behaviour: incidentally, the answer to *all* questions about C.

---

### Post by harry2006 on 2009-08-04
> **munky99999 said:**
> Hey guys, I'm teaching myself how to program. I'm having an unusual issue with my program.

```
#include <stdio.h>
#include <stdlib.h>

float epic(float x);

   float input, answer;

   main()
   {
     printf("Enter the # zero dawg: ");
     scanf("%d", &input);
     answer = epic(input);
     printf("\nThe root of %ld is %ld.\n", input, answer);
     printf("\nYou divided by 0 yo.\n");

     return 0;
  }

  float epic(float x)
  {
     float x_divided;

     x_divided = x / x;
     return x_divided;
  }

```

You CAN divide by ZERO.
! million dollar question.....lol

---

### Post by veda87 on 2009-08-04
So It means that only ```
somevalue/0
```only cause a division by zero error....
and ```
int i=0; somevalue/i
``` doesn't cause an error...

I think, may be, during compilation only the correctness of the code is beingchecked and the values are substituted later on...

---

### Post by munky99999 on 2009-08-04
> **kayvortex said:**
> Just out of interest, what does happen if you divide by zero in C? I've never actually tried it for fear of being sucked into the resulting event horizon.

Edit: Ok, a compile-time error, or else unexpected run-time behaviour: incidentally, the answer to *all* questions about C.

heh. The way im compiling/debugging i get lots of warnings with things i do. If you did this in C++ or didnt use float but instead long or int... it just doesnt work. Crashing or giving an error.

I tried. I'm just teaching myself how to program and the original program was just cubing the Number. I just changes a bunch of things. Then I wondered what the different, float vs int vs long... like what they do with regards to the code. I had tried float last. Then I changed the function basically to instead divide by the number inserted. Which would be 0. Just to see what would happen. Oddly it worked and gave an answer lol.

Ofcoarse I editted in the dawg and epic and such :) just to see if you could.

---

### Post by kayvortex on 2009-08-04
Yeah, generally in C(++) you need to be very careful in checking that any inputs you get are what you expect them to be or else very strange things can happen (like being put into an infinite loop, as it once happened to me when I was a little more naive in C++!).

---

### Post by soltanis on 2009-08-04
When you divide by zero using floating point numbers, you will get the value +/- Infinity (a constant in float.h I think) and a divide-by-zero floating point exception.

Compare: divide by zero with an integer and your computer explodes.

---

