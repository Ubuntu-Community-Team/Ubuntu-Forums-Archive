---
title: "Play between 2 Process"
date: 2014-05-02
forum: Programming Talk
---

### Post by one_girl on 2014-05-02
this game is run by the user ,I need the game run between two process the one guess and the other sleep ,until get the result .I need the answer by use the sleep and weak up.


```



#include <stdlib.h>
#include <stdio.h>
#include <time.h>
 
#define GAME_LOWER_LIMIT 0
#define GAME_UPPER_LIMIT 100
 
int main(){
  int  number;
    int  done = 0;
    char line[32];
    int  numGuesses = 0;


    srand(time(0));
    number = GAME_LOWER_LIMIT + rand() % (GAME_UPPER_LIMIT - GAME_LOWER_LIMIT + 1);


    while (!done)
    {
        printf("Guess a number between %d and %d: ", GAME_LOWER_LIMIT, GAME_UPPER_LIMIT);


        if (fgets(line, sizeof(line), stdin) != NULL)
        {
            int guess;


            if (sscanf(line, "%d", &guess) == 1)
            {
                if (number == guess)
                {
                    printf( "\nYou guessed correctly after %d times!\n\n", numGuesses);
                    done = 1;
                }
                else
                {
                    printf("Your guess was too %s.\nTry again: ", number < guess ? "high" : "low");
                    numGuesses++;
                }
            }
            else
            {
                printf("\nIllegal input; try again...\n\n");
            }
        }
        else
        {
            printf("\nIllegal input; try again...\n\n");
        }
    }


}



```

---

### Post by ofnuts on 2014-05-02
Three solutions: 

1) The "player" is a parent process, starts the "game" process, and [prints to the game stdin and reads from the game stdout.]("http://cse.yeditepe.edu.tr/~kserdaroglu/spring2014/cse331/labnotes/WEEK%204%20-%20IPC/Pipes.html")
2) Variant of 1): there is a general parent process that starts both player and game processes and interconnects their input/output
3) You create [named pipes (aka "fifo"s)]("http://www.linuxjournal.com/article/2156") in your file system and a script starts both game and player process after connecting their stdin/out to the fifos.

---

### Post by one_girl on 2014-05-02
thanks Allot,,
because I did not take the PIPES 
I need the code run with the (sleep) and (weak up)

can any one help me

---

### Post by one_girl on 2014-05-03
I will explain what I need

---

### Post by one_girl on 2014-05-04
ok please can any one solved with the pipes
or give me any hint to help me.

I want the first process guess the answer if it is not correct sleep this process and allow to the second process guess the answer if it right answer terminate the game ,if it is wrong sleep process two and weak up process one to guess the new answer and so as,,,

---

### Post by ofnuts on 2014-05-04
You mean you have three processes, one "game" and two players? And the players must play in turn? And both player processes also see the other player guesses as well at the game process answers to that?

---

### Post by one_girl on 2014-05-04
Yes, you are right 
The two player one is the parent , and the second is the child

parent is start guess and then sleep
and child guess and sleep
the parent will weak up and guess
and so on until one of them write the correct number

---

### Post by ofnuts on 2014-05-05
Hmm. That's still different... both processes try to gues the number from the other one?

---

### Post by one_girl on 2014-05-05
try to guess the number between 1 and 100 like the original code above 
from where, and how it will be come I doooooo not know :( :(

---

### Post by mörgæs on 2014-05-05
Closed like your other homework thread.

---

