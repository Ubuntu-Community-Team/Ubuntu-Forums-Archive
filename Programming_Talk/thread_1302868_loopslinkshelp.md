---
title: "loops?links?help?"
date: 2009-10-27
forum: Programming Talk
---

### Post by mickmouse13 on 2009-10-27
I'm trying to learn loops in C but I'm having a bit of trouble due to the simple samples given by my tutorial [http://www.cprogramming.com/tutorial/c/lesson3.html](http://www.cprogramming.com/tutorial/c/lesson3.html) Its a good tutorial but I need a few other things. 

If anyone has time to add a loop to the run part of my program that would be AMAZING. i would want a variable named rtime (runtime) and i want the text to pop up that you need to run while also having 1 added to rtime. when the player hits the 'r' key i want the timer to stop and for the program to check rtime if rtime is more than a few seconds you loose if its not than you move on. (hope that's enough)

or any links to places where I can download some good source code to weed through would be cool too. anyway thanks for what ever help you can give! basically I'm looking for anything to help me see how loops are used in practical code. the loop for my program will help most because I can see the changes but anything is welcome.

```
#include <stdio.h>

int main()
{        /*starting main function.*/
char zombie;

printf ( "a man apreaches you; His face hidden in the shadows\n" );
printf ( "'are you  a zombie?'\n (y/n)\n" );        /*asks for a yes or no answer*/
scanf ( "%c", &zombie );        /*waits for input*/
if (zombie =='y' ){        /*if you said yes*/
    printf( "you have obviously already lost\n" );
    }
else if (zombie == 'n'){        /*if you answered no it will start the lext "level" of the game.*/
    printf ( "The man comes into the light; His face rotten and maggot-filled, He mumbles as he lumbers to you 'You ought to run than'\n (press r to run\n" );

char ch;
while((ch = getc(stdin)) != EOF && ch != '\n'){        /*these two lines are supposed to clear the %c char? */
    continue;
}                                        /* so that i can reuse it for the "run" command (i did not write this)*/
    char run;
    scanf ("%c", &run );
    if (run == 'r' ){
        printf ( "you run just fastenough to outrun him and make it into a safe room\n" );
    }
    
    else {
        printf ( "You are to slow and got eaten.\n" );
    }}        

else {        /*This is what happens if you did not press Y or N in the beguinning.*/
    printf ( "you fail... I SAID YES OR NO!!\n" );
}

    
}        /*ending main function*/
```

---

### Post by mickmouse13 on 2009-10-27
Im thinking one answer might be to add in a loop and then a break.. like
do 
    rtime++
while
    rtime=<100
break if R is pressed. or something XD

---

