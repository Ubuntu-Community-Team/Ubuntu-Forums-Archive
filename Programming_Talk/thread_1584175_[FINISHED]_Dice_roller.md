---
title: "[FINISHED] Dice roller"
date: 2010-09-28
forum: Programming Talk
---

### Post by Kareta on 2010-09-28
Following code is written in C.

Thanks to all the people in this thread: [Thread]("http://ubuntuforums.org/showthread.php?t=1581874").

Y'all helped a lot. 

```
[COLOR=black]/*
 * 13-sided Die Roller.
 *                Completed on 9/28/10 
 * 
 *                                  */

#include <stdio.h>
#include <time.h> // time
#include <stdlib.h> // srand

int main(void){

   int ProgLoop = 1;
         while(ProgLoop >= 1){



   int cont = 0;

   int w; //Number of rolls generated/displayed
   int x = 0;
   int y;
   int z;


   printf("Press 1 to run program.\n");

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
         while (cont <= 1){
            x = 0;
            w = 0;

            if (cont == 0){
                        printf("Reroll? 1[REROLL]/2[QUIT]");
                                          scanf("%d", &cont);
                                          if(cont != 1 && cont !=2){
                                             printf("Please enter a valid argument.");
                                                cont = 0;
                                 }
                     }

            if (cont == 1) {
               printf("Enter number of times you would like to roll:");
                        scanf("%d", &w);
                        srand(time(NULL));
                        while(x<w){
                           printf("%d\n", 1+rand()%13);
                           x++;
                        }
                  --cont;
                  }
            if (cont == 2){
                        printf("Program terminated.\n");
                        cont = 2;
                     }

            }



      break;

      case 2:
         printf("Program terminated.\n");
      break;

      case 3:
         printf("This program will roll a 13-sided die by $X amount of times.\n\n");

         printf("Press 1 to run program.\n");

         printf("Press 2 to cancel.\n");
         scanf("%d", &z);
         if(z == 1){
            printf("Enter number of times you would like to roll:");
                     scanf("%d", &w);
                     srand(time(NULL));
                     while(x<w){
                        printf("%d\n", 1+rand()%13);
                        x++;
                     }
                     while (cont <= 1){
                                 x = 0;
                                 w = 0;

                                 if (cont == 0){
                                             printf("Reroll? 1[REROLL]/2[QUIT]\n");
                                                               scanf("%d", &cont);
                                                               if(cont != 1 && cont !=2){
                                                                  printf("Please enter a valid argument.");
                                                                  cont = 0;
                                                               }
                                          }

                                 if (cont == 1) {
                                    printf("Enter number of times you would like to roll:");
                                             scanf("%d", &w);
                                             srand(time(NULL));
                                             while(x<w){
                                                printf("%d\n", 1+rand()%13);
                                                x++;
                                             }
                                       --cont;
                                       }
                                 if (cont == 2){
                                             printf("Program terminated.\n");
                                             cont = 2;
                                          }

                                 }
                        }
         if(z == 2){
            printf("Program terminated.\n");
         }if (z != 1 && z != 2){
         printf("Please enter a valid argument [PROGRAM TERMINATED].\n\n");
         ++ProgLoop;
         }
      break;

      default:
         if (y != 1 && z !=2)
         {
         printf("Please enter a valid argument. [PROGRAM TERMINATED]\n\n");
         ++ProgLoop;
         }
      break;
         }
            --ProgLoop;

      }
   }[/COLOR]
```[COLOR=black]
(Worked on my indenting, :P)

I'm a beginner, please tell me what you think of the program ([Constructive] Criticism) and/or how it can be improved. 


I appreciate all feedback, thanks.

In action:
[IMG]http://i54.tinypic.com/300eiox.jpg[/IMG]

[IMG]http://i51.tinypic.com/20z4n6f.jpg[/IMG]
[/COLOR]

---

### Post by Bachstelze on 2010-09-28
The indentig is better, but could still be improved.  Also, you have exactly the same code in two places, that's generally (read, always) not needed.  Try to find a way to reuse the code instead of rewriting it (no gotos).

---

### Post by Kareta on 2010-09-28
> **Bachstelze said:**
> The indentig is better, but could still be improved.  Also, you have exactly the same code in two places, that's generally (read, always) not needed.  Try to find a way to reuse the code instead of rewriting it (no gotos).

A function?

---

### Post by Bachstelze on 2010-09-28
Your program says:

```
Press 3 for more information.
```

However, when the user types 3, your program not only displays the info, but it also does the whole dice rolling again. You could do somethig like

```

exit := false
while exit == false
    display prompt
    ask for input
    if input == 1
        roll
        ask if user wants to reroll
        if no
            exit := true
    else if input == 2
        exit := true
    else if input == 3
        display more info
    else
        display error

```

---

### Post by worksofcraft on 2010-09-28
Nice work :)

I noticed some people mentioned indentation and it is very much a matter of personal preferences. See in this  [long running thread on the subject]("http://ubuntuforums.org/showthread.php?p=9878604#post9878604") for instance, where I comment on my preference to show the structure of the program rather than to look nice.

I see you are sort of also following the old masters Kernighan and Ritchie and Stroustrup too in their braces style, but it helps when you indent the code within those block so it's easy to see where each one starts and where it ends.

Often that can result in many levels of indentation and one way to avoid going off the other edge of the screen is to break the code up into separate functions. For instance you could write something like:
```

   printf("Press 1 to run program.\n");
   printf("Press 2 to cancel.\n");
   printf("Press 3 for more information.\n");
   scanf("%d", &y);

   switch(y) {
      case 1: run_program(); break;
      case 2: return finished();
      case 3: more_info(); break;
      default: bad_option();
   }

```
Then it's easy to follow at this level and if you do likewise in each of those next level functions they too will be easy to follow.

---

