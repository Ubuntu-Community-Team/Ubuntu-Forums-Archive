---
title: "Dice roller"
date: 2010-09-24
forum: Programming Talk
---

### Post by Kareta on 2010-09-24
Just wondering if there's anyway to use characters instead of numbers, and what argument denotes a character variable? (Like %d denotes an integer) Or even an easier way to right the code below


Following code is in C:```
/*
 * 13-sided Die Roller. 
 */

#include <stdio.h>

int main(void){

    int x=0;
    int y;
    int z;

    printf("Press 1 to run program\n");

    printf("Press 2 to cancel.\n");

    printf("Press 3 for more information.\n");
    scanf("%d", &y);

    switch(y){

    case 1:
    srand(time(NULL));
    while(x<1){
    printf("%d\n", 1+rand()%13);
    x++;
    }
    break;
    case 2:
    printf("Program terminated.");
    break;
    case 3:
    printf("This program will roll a 13 sided die once.\n\n");
    switch(z){
    default:
        printf("Press 1 to run program:");
        scanf("%d", &z);

        srand(time(NULL));
        while(x<1){
        printf("%d\n", 1+rand()%13);
        x++;
        }
        break;
    }
    break;
    default:
    printf("Please enter a correct argument.");
    break;
    }
    return 0;
}
```Also, how would I be able to 'infinitively" loop the program? Like, as soon as it's finished, start from the beginning or have a line of text that says "Press 1 to reroll" and another that says "Press 2 to cancel", but loops infinitively.

Sorry if the question was confusing or stupid.


EDIT (see below): Changed the code, but I'd still like to know how to infinitively loop program.
```
/*
 * 13-sided Die Roller.
 */

#include <stdio.h>

int main(void){

    int w;

    int x=0;
    int y;
    int z;

    printf("Press 1 to run program\n");

    printf("Press 2 to cancel.\n");

    printf("Press 3 for more information.\n");
    scanf("%d", &y);

    switch(y){

    case 1:
    printf("Enter number of times you would like to roll:");
    scanf("%d", &w);
    srand(time(NULL));
    while(x<w){
    printf("%d\n", 1+rand()%13);
    x++;
    }
    break;
    case 2:
    printf("Program terminated.");
    break;
    case 3:
    printf("This program will roll a 13 sided die once.\n\n");
    switch(z){
    default:
        printf("Press 1 to run program:");
        scanf("%d", &z);
        if(z == 1){

            printf("Enter number of times you would like to roll:");
                scanf("%d", &w);
                srand(time(NULL));
                while(x<w){
                printf("%d\n", 1+rand()%13);
                x++;
        }
        }
        else
        {
            printf("Please enter a correct argument:");
        }
        break;
    }
    break;
    default:
    printf("Please enter a correct argument.");
    break;
    }
    return 20;
}
```

---

### Post by Bachstelze on 2010-09-25
[Don't use scanf]("http://c-faq.com/stdio/scanfprobs.html")

To loop infinitely:

```
for (;;) {
    /* Your stuff. */
    if (key_pressed == 2)
        break;
}
```

Or

```
int continue = 1;
while (continue) {
    /* Your stuff. */

    if (key_pressed == 2)
        continue = 0;
}
```

---

