---
title: "fgets()...curious question"
date: 2008-02-07
forum: Programming Talk
---

### Post by S15_88 on 2008-02-07
I've made a program that prints 100 randomly generated numbers to a text file:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    FILE * file;
    int a, i;

    file = fopen("/home/alain/numbers.txt", "w");

    if( file != NULL )
    {
        for(i=0; i<100; i++)
        {
            a = rand();
            fprintf( file, "%d\n", a);
        }
    }
    fclose(file);
    return 0;
}


```

What i'm wondering is if it is possible to grab all those numbers, but to assign them to their own variable, ie. num1, num2, num3...

What i was thinking of doing was fgets() all of it to a string then sscanf() each number to a variable.

now do i need to physically type out long int num1, num2, num3....
then again sscanf(stringName, "%d %d %d...(100 times)", &num1, &num2(until num100)...);

or 

can i loop it somehow with a for loop?

Any Help Would Be Greatly Appreciated,
Thanks, Alain

---

### Post by cb951303 on 2008-02-07
you can create a dynamic array and create a for loop to assign values with sscanf

---

### Post by S15_88 on 2008-02-07
right..dynamically create it with malloc(), now if i wanted to add all those numbers it would be as simple as taking the array they're stored in and running it through a for loop 100 times with a long int += array...

sounds good i'll give it a try!

Thanks, Alain

---

### Post by cb951303 on 2008-02-08
actually if its always 100 numbers then there is no need to allocate memory  dinamically, but I thought since you get them from a text file you might want to have the flexiblity to change the number.

cheers mate

---

