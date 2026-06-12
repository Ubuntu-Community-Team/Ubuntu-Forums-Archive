---
title: "pointers and arrays"
date: 2007-03-28
forum: Programming Talk
---

### Post by byrddw on 2007-03-28
I am not taking a C programming course, and I thought that I was doing o.k. until my current section.  I am to write a program that has a declaration in main () to store seven numbers in an array named channels.  There should be a function call to display () that accepts the channels as an argument named channels and then desplays the numbers using the pointer notation *(channels + i).    

This sounded straight foward, I thought, but it is not working so well for me.  This is what I have come up with so far:




#include <stdio.h>
#include <stdlib.h>
#define NUMELS 7

int display (int[], int);

int main(int argc, char *argv[])
{
    int channels [] = {2, 4, 5, 7, 9, 11, 13};

    
    printf ("%d are the channels.\n", display (channels, NUMELS));
  
  system("PAUSE");	
  return 0;
}

int display ( int channels [], int nums)
{
    int i, chan = channels [0];
    for (i = 0; i < nums; i++)
    printf ("%i ", *(channels + i));
}



When I run the program I get the following output "2 4 5 7 9 11 13 7 are the channels."

I do not understand how to get rid of the "7" in the output.  whenever I drop the "NUMELS" from the function call, I get an error message stating "syntax error before ')' token"  I would appreciate any help that anyone can offer.

---

### Post by lloyd_b on 2007-03-28
That extra "7" is coming from here:
```
printf ("%d are the channels.\n", display (channels, NUMELS));
```

display() is coded as returning type int.  You do not explicitly set a return value for the function, so it's picking up the last value on the stack (in this case, 7).

Properly, this function should be type "void", rather than "int", since it isn't actually returning a value:

```

#include <stdio.h>
#include <stdlib.h>
#define NUMELS 7

void display (int[], int);

int main(int argc, char *argv[])
{
     int channels [] = {2, 4, 5, 7, 9, 11, 13};

     display(channels, NUMELS);
     printf("are the channels\n");

     system("PAUSE");
     return 0;
}

void display ( int channels [], int nums)
{
     int i;
     for (i = 0; i < nums; i++)
          printf ("%i ", channels[i]);
}
```

Note: I changed your "*(channels + i)" to "channels[i]", as it is much easier to understand, and removed the unused "chan" variable.

Lloyd B.

---

### Post by Jmccaffrey on 2007-03-28
Yea to support his claim, channels[i] is equal to *(channels + i) and infact you can test this yourself with the following expression:
```

#include <stdio.h>

int 
main(void)
{
  int list[] = { 1, 2, 3 };
  2[list] = 4;
  printf("list[2] = %d\n", list[2]);
  
  return 0;
}

```

```

jmccaffrey@windy:~/mywork$ ./test
list[2] = 4

```

---

