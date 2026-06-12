---
title: "Simple C program help =)"
date: 2009-10-25
forum: Programming Talk
---

### Post by mickmouse13 on 2009-10-25
third post with this program XD and its not getting far... anyway I keep getting the error "‘else’ without a previous ‘if’"while compileing. I understand what this means but i dont see why it does not see what im doing.. i have 3 modules, the middle on breaks off into another module but even though there is something after the second one i don't know why the third one is not recognised.. any help? 
PS. i tried to work on my "Style" hope its readable.

code
```

#include <stdio.h>

int main()
{        /*starting main function.*/
char zombie;

printf ( "a man approaches you; His face hidden in the shadows\n" );
printf ( "'are you  a zombie?'\n (y/n)\n" );        /*asks for a yes or no answer*/
scanf ( "%c", &zombie );        /*waits for input*/
if (zombie =='y' ){        /*if you said yes*/
    printf( "you have obviously already lost\n" );
    }
else if (zombie == 'n'){        /*if you answered no it will start the next "level" of the game.*/
    printf ( "The man comes into the light; His face rotten and maggot-filled, He mumbles as he lumbers to you 'You ought to run than'\n" );
}
char ch;
while((ch = getc(stdin)) != EOF && ch != '\n'){        /*these two lines are supposed to clear the %c char? */
    continue;
}                                        /* so that I can reuse it for the "run" command (i did not write this)*/
    char run;
    scanf ("%c", &run );
    if (run == 'r' ){
        printf ( "you run just fast enough to outrun him and make it into a safe room\n" );
    }
    
    else {
        printf ( "You are to slow and got eaten.\n" );
    }        

else {        /*This is what happens if you did not press Y or N in the beginning.*/
    printf ( "you fail... I SAID YES OR NO!!\n" );
}

    
}        /*ending main function*/

```

---

### Post by MadCow108 on 2009-10-25
this else:
else {        /*This is what happens if you did not press Y or N in the beginning.*/
    printf ( "you fail... I SAID YES OR NO!!\n" );
}
has no matching if.
every if clause is closed before this is reached
I'm guessing the else { should be after the else if (zombie == 'n'){?

an editor with bracket matching and proper indentation is very useful for these kind of things

---

### Post by mickmouse13 on 2009-10-25
i actually figured it out. I took out the ending bracket of the "(if zombie == 'n') and moved it closer to the bottom thus causing the things i wanted to be inside this function.

what would you suggest? im using gedit and that has bracket matching and it will CONTINUE an indent.. if im indented and press inter it will stay that much indented. but this is not auto indention.

---

