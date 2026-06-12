---
title: "Need a better logic...."
date: 2009-08-18
forum: Programming Talk
---

### Post by veda87 on 2009-08-18
I know reading this is bit too lengthy... Sorry for that...

I have coded a game program...game deals with 24 sticks...The game is played between user and the computer... Each of them can take any number of sticks between 1 to 4... who ever gets the last turn losses...

I am bit selfish and i want the computer to always win.... A Cheating I mean... So I edited my code to do that.... So the edited code is...

```
#include <stdio.h>
#include <time.h>

/* Global Declaration */
int array[] = {1,6,11,16,21}; /* These are the numbers which makes computer wins */

/* Description abt the game */
void GameDep()
{
        printf("This program is abt a game.... This game deals with 24 sticks... \
                The game is played between user and the computer... Each of them \
                can take any number of sticks between 1 to 4... who ever gets the\
                last turn losses...\n");
}

int UserInput()
{
        int stick;

        while(1) {
                printf("No of sticks U take...(1 to 4) : ");
                scanf("%d", &stick);
                if(stick > 0 && stick < 5) {
                        return stick;
                } else {
                        printf("Enter the correct input..\n");
                }
        }

}

/* The game */
void Play()
{
        int sticks = 24;
        int UserStick;
        int CompStick;
        int i;
        enum{user,computer}player;

        srand(time(0));
        printf("The game starts\n");

        printf("Total No of sticks = 24 \n" );
        printf("User: make ur first move\n");
        player = user; /* current player */

        while(sticks > 1) {
                UserStick = UserInput();
                sticks -= UserStick;
                printf("No of Sticks Left = %d\n", sticks);
                player = computer;
                if(sticks == 1)
                        break;
                for(i=4; i>=0; i--) {
                        if(sticks > array[i]) {
                                printf("No of sticks I (computer) take.... : %d \n\n", (sticks - array[i]));
                                sticks = array[i];
                                break;
                        } else if(sticks == array[i]) {
                                CompStick = (rand()%(4-1)) + 1;
                                printf("No of sticks I (computer) take.... : %d \n\n", CompStick);
                                sticks -= CompStick;
                                break;
                        }
                }
                printf("No of Sticks Left = %d\n\n", sticks);
                player = user;
        }
        if (player == user) {
                printf("U lose.... Try once again... All The best...\n");
        } else if (player == computer) {
                printf("I lose.... Congrats dude... Good job...\n");
        }


}

/* Program starts here */
int main()
{
        int choice;
        int limitcheck = 0;
        char wish[3];

        while(limitcheck < 10 ) { /* limitcheck is used to check the limit... I gave it to prevent coding while(1) */
                printf(" Welcome to the Game \n");
                printf(" Enter 1: to play \n Enter 2: Help \n Enter 3: To exit \n");

                printf("Enter ur choice: ");
                scanf("%d", &choice);

                switch(choice)
                {
                case 1:
                        Play();
                        break;
                case 2:
                        GameDep();
                        break;
                case 3:
                        printf("Exiting the game && Thanks for playing \n");
                        return 0;
                default:
                        printf("Enter the correct choice....\n");
                        break;
                }
                limitcheck++;
                if(limitcheck == 10) {
                        printf("U have already tired 10 times... \n Do u wish to continue: y or n\n");
                        scanf("%s", wish);
                        if(strcasecmp(wish, "y") == 0) {
                                limitcheck = 0;
                        } else if(strcasecmp(wish, "n") == 0) {
                                printf("Exiting the game && Thanks for playing ");
                                return 0;
                        }
                }
        }
        return 0;
}

```

For all combinations expect one my code win..... 
```
 Welcome to the Game 
 Enter 1: to play 
 Enter 2: Help 
 Enter 3: To exit 
Enter ur choice: 1
The game starts
Total No of sticks = 24 
User: make ur first move
No of sticks U take...(1 to 4) : 3
No of Sticks Left = 21
No of sticks I (computer) take.... : 1 

No of Sticks Left = 20

No of sticks U take...(1 to 4) : 4
No of Sticks Left = 16
No of sticks I (computer) take.... : 1 

No of Sticks Left = 15

No of sticks U take...(1 to 4) : 4
No of Sticks Left = 11
No of sticks I (computer) take.... : 3 

No of Sticks Left = 8

No of sticks U take...(1 to 4) : 2
No of Sticks Left = 6
No of sticks I (computer) take.... : 3 

No of Sticks Left = 3

No of sticks U take...(1 to 4) : 2
No of Sticks Left = 1
I lose.... Congrats dude... Good job...
 Welcome to the Game 
 Enter 1: to play 
 Enter 2: Help 
 Enter 3: To exit 
Enter ur choice: 

```
For this input I loose ( I mean computer).... I now understand that one can't cheat always..:lolflag:

I think my logic is faulty... Can anyone tell me a better one...

---

### Post by suevy Suavae on 2009-08-18
If theres one stick left on the computers turn, it loses (we must avoid this situation).

If there's two sticks take one.

Three sticks take two.

four sticks take three (all pretty simple)

If theres five, it seems like your still in trouble. No matter what you take they can take one less then whats left, and force you to lose again.

The best I can think to do (and maybe this is what your already doing) is to always take three sticks, unless theres four or less (see the earlier logic).

---

### Post by veda87 on 2009-08-18
> **suevy Suavae said:**
> If theres one stick left on the computers turn, it loses (we must avoid this situation).

If there's two sticks take one.

Three sticks take two.

four sticks take three (all pretty simple)

If theres five, it seems like your still in trouble. No matter what you take they can take one less then whats left, and force you to lose again.

I didn't follow this logic... I will tell U my logic... I have a set of numbers {1,6,11,16,21}... these are the number of sticks that should be present after my (computer's) turn [(end of computer's turn)], so that I (computer) can win...
> **suevy Suavae said:**
> 
The best I can think to do (and maybe this is what your already doing) is to always take three sticks, unless theres four or less (see the earlier logic).
I (computer) takes three sticks always, then what is the need for range 1 to 4... The user will get regretted because everytime the computer is going to pick the same number of sticks irrespective of what number he picks....

Even though I (computer) takes three sticks always and if the User is brilliant enough to land in {1,6,11,16,21} at end of his turn... he will win... 

I guess this is an exceptional case where the User tends to win... So the user out smarts the computer and me.... 

But if anyone have a better solution... please tell me...

---

### Post by veda87 on 2009-08-18
Now I understood... My logic was correct... The win depends on the number of sticks used and the maximum value of the range (range means the possible number of sticks taken at a time)

So... here is my cheat free game... Try playing it and enjoy....:lolflag:```
#include <stdio.h>
#include <time.h>

/* global Declaration */
int sticks;
int range;

/* Description abt the game */
void GameDep()
{
        printf("This program is abt a game.... This game deals with 24 sticks... \
                The game is played between user and the computer... Each of them \
                can take any number of sticks between 1 to 4... who ever gets the\
                last turn losses...\n");
}

int UserInput()
{
        int stick;

        while(1) {
                printf("No of sticks U take...(1 to %d) : ", range);
                scanf("%d", &stick);
                if(stick > 0 && stick < (range+1)) {
                        return stick;
                } else {
                        printf("Enter the correct input..\n");
                }
        }

}
/* The game */
void Play()
{
        int UserStick;
        int CompStick;
        int i;
        enum{user,computer}player;

        srand(time(0));
        printf("The game starts\n");

        printf("Total No of sticks = %d \n", sticks);

        printf("User: make ur first move\n");
        player = user; /* current player */

        while(sticks > 1) {
                UserStick = UserInput();
                sticks -= UserStick;
                printf("No of Sticks Left = %d\n", sticks);
                player = computer;
                if(sticks == 1)
                        break;
                CompStick = (rand()%(range-1)) + 1;
                printf("No of sticks I (computer) take.... : %d \n\n", CompStick);
                sticks -= CompStick;
                printf("No of Sticks Left = %d\n\n", sticks);
                player = user;
        }
        if (player == user) {
                printf("U lose.... Try once again... All The best...\n");
        } else if (player == computer) {
                printf("I lose.... Congrats dude... Good job...\n");
        }


}

/* Program starts here */
int main()
{
        int choice;
        int limitcheck = 0;
        char wish[3];

        printf(" Welcome to the Game \n");
        printf("Enter the number of sticks to be used :");
        scanf("%d", &sticks);
        printf("Enter the maximum number of sticks to be taken at a time :");
        scanf("%d", &range);
        while(limitcheck < 10 ) { /* limitcheck is used to check the limit... I gave it to prevent coding while(1) */
                printf(" Welcome to the Game \n");
                printf(" Enter 1: to play \n Enter 2: Help \n Enter 3: To exit \n");
                printf("Enter ur choice: ");
                scanf("%d", &choice);

                switch(choice)
                {
                case 1:
                        Play();
                        break;
                case 2:
                        GameDep();
                        break;
                case 3:
                        printf("Exiting the game && Thanks for playing \n");
                        return 0;
                default:
                        printf("Enter the correct choice....\n");
                        break;
                }
                limitcheck++;
                if(limitcheck == 10) {
                        printf("U have already tired 10 times... \n Do u wish to continue: y or n\n");
                        scanf("%s", wish);
                        if(strcasecmp(wish, "y") == 0) {
                                limitcheck = 0;
                        } else if(strcasecmp(wish, "n") == 0) {
                                printf("Exiting the game && Thanks for playing ");
                                return 0;
                        }
                }
        }
        return 0;
}


```

---

