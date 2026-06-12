---
title: "Why does this C prog not compile? (Learning C programming, newb stuff)"
date: 2007-04-10
forum: Programming Talk
---

### Post by jakev383 on 2007-04-10
I bought a book to learn C programming on Linux and am starting to work my way through it. I'm on the lesson for constants, and have run into an issue where the code in the book doesn't compile, and I'd like to know why. It makes sense to me, but that's not saying much. Anyway, here's the code:
```

/* Demonstrates variables and constants */
#include <stdio.h>

/* Define a constant to convert from pounds to grams */
#define GRAMS_PER_POUND = 454

/* Define a constant for the start of the next century */
const int TARGET_YEAR = 2010;

/* Declare the needed variables */
int weight_in_grams,weight_in_pounds;
int year_of_birth,age_in_2010;

int main(void)
{
        /* Input data from the user */

        printf("Enter your weight in pounds: ");
        scanf("%d", &weight_in_pounds);
        printf("Enter your year of birth: ");
        scanf("%d", &year_of_birth);

        /* Perform the conversions */

        weight_in_grams = weight_in_pounds * GRAMS_PER_POUND;
        age_in_2010 = TARGET_YEAR - year_of_birth;

        /* Display results on the screen */

        printf("\nYour weight in grams = %d.",weight_in_grams);
        printf("\nIn 2010 you will be %d years old.\n",age_in_2010);

        return 0;
}

```
And here's the error I get when compiling:
listing2.4.c: In function ‘main’:
listing2.4.c:25: error: expected expression before ‘=’ token
(that's this line)
```

weight_in_grams = weight_in_pounds * GRAMS_PER_POUND;

```

I've tried encapsulating the equation portion in ()'s, and changing the order of the equation. The only way I could get it to compile was by changing the constant name GRAMS_PER_POUND in the equation portion to the actual number. But this would make defining constants useless.... I'm assuming that it's just a change that has happened since the book was printed (2000), but it still seems to me that it should work.
Can anyone offer a suggestion as to why it's not working?
Thanks.

---

### Post by amohanty on 2007-04-10
> #define GRAMS_PER_POUND = 454

no **=** required here. actually you should not put an =, just do a 
#define GRAMS_PER_POUND 454

AM

---

### Post by jakev383 on 2007-04-10
> **amohanty said:**
> no **=** required here. actually you should not put an =, just do a 
#define GRAMS_PER_POUND 454

AM
](*,)  It's always the little mistakes.... Like that . in bind configs....
Thanks for the quick reply!

---

