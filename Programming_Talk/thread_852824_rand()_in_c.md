---
title: "rand() in c"
date: 2008-07-08
forum: Programming Talk
---

### Post by coreofreeality on 2008-07-08
hi

i was trying to write a simple guess the number game in c using a pseudoRNG for the number the user has to guess. 

i've tried to google it, and to look in several places, but they either dont have it, or dump a code and dont really explain how to use it. i've gotten as far as using a value from the system clock to seed srand() and then use rand() to produce an actual random number, but i have no idea how to implement it to store it in a simple integer (lets say int r for the moment)

does anyone know?

---

### Post by LaRoza on 2008-07-08
> **coreofreeality said:**
> 
i was trying to write a simple guess the number game in c using a pseudoRNG for the number the user has to guess. 

does anyone know?

[php]
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int r;
    char guess[4];
    int guessCount = 0;
    srand((unsigned)time(NULL)); 
    r = rand()%100;
    do
    {
        fgets(guess,3,stdin);
        if (atoi(guess) == r)
        {
            printf("You got it in %d tries\n",guessCount);
        }
        else 
        {
            guessCount++;
            if (atoi(guess) > r)
            {
                puts("Too high");
            }
            else
            {
                puts("Too low");
            }
        }
    } while (atoi(guess) != r);
}
[/php]

---

### Post by kavon89 on 2008-07-08
I found [this website]("http://eternallyconfuzzled.com/arts/jsw_art_rand.aspx") to have lots of info and a basic example of rand() and how to implement it so it produces better random numbers.

---

### Post by coreofreeality on 2008-07-08
thanks! thats much simpler then the code i found on the internets (they used all kinds of other stuff)

---

### Post by LaRoza on 2008-07-08
> **coreofreeality said:**
> thanks! thats much simpler then the code i found on the internets (they used all kinds of other stuff)

I updated my code. The game is silly, as it is easy to play. (Think, binary search)

---

### Post by coreofreeality on 2008-07-08
yeah, i was just using it as a little excersise to remember things i learned last semester.

i added things like restricting it to 5 guesses (makes it abit harder) and adding an option from within to play again (instead of having to restart the program.)

---

### Post by coreofreeality on 2008-07-08
by the looks of it, this is an incredibly bloated way of doing what i did,does anyone have advice on how to do it better?

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>


//prototype declarations
int guess(int random);
void winresponse(int win, int r);
void ask();

int main()
{
	int win, loop=1, r;
	printf("wecome to 'guess the number'\n\n");
	printf("you have 5 guesses to guess a randomly generated\n");
	printf("between 1 and 100. see if you can guess it before\nyour guesses run out!\n\n");
	while(loop==1)
	{
		srand((unsigned)time(NULL));
		r = rand()%100;			//gives r a pseudorandom number
		win=guess(r);			//main function controlling guesses
		winresponse(win,r);			//gives a response based on the result
		ask();				//kills program if user return no, only continues if use returns yes.
		continue;
	}
}

int guess(int random)
{
	int i=1, guess, pwn=0;
	while(i<6)				//you have 5 guesses
	{
		printf("guess number %d.\n",i);
		printf("your guess is: ");
		scanf("%d",&guess);
		if(guess<random)
		{
			printf("\n\nhigher\n\n");		//output if guess is too low
		}
		if(guess>random)
		{
			printf("\n\nlower\n\n");		//output if guess is too high
		}
		if(guess==random)
		{
			printf("\n\n");					//if guess is right, this sets it up for the win message
			pwn=1;
			i=12;
		}
	i++;
	}
	return pwn;
}

void winresponse(int win, int r)				//win messages...yay
{
	if(win==1)
	{
		printf("Well Done!!! you won!!\n\n");
	}
	else
	{
		printf("too bad. better luck next time\nthe answer was %d\n\n",r);
	}
}

void ask()						//function to take care of repeated plays, or to exit
{
	char grilled[5];
	int f=1;
	while(f==1)
	{
		printf("Do you want to play again? ");
		scanf("%s",&grilled);
		if(strcmp(grilled,"no")==0)
		{									//user returns no and program exits
			printf("\n\n\n\n");
			exit(1);
		}
		if(strcmp(grilled,"yes")==0)
		{
			f=2    //user returns yes and plays again
		}
		else
		{
			printf("please answer 'yes' or 'no'\n");	//user does not answer yes or no, so program prompts again
		}
		continue;
	}
}
```

---

### Post by Tony Flury on 2008-07-08
A trivial thing - but there is no reason to use "continue" in your While loop in the ask function - it is at the end of the loop anyway.

A good compiler will probably optimise it out anyway - but I would suggest that it ia bad habit to get into (almost as bad as things like goto).

---

### Post by Cygnus on 2008-07-08
As I recall it just using modulo (%) on the number from rand() is not so good (the low order bits of random numbers repeats more regularly than the whole number). Try this instead:

[PHP]
int randint(int min,int max) 
{
  return min+int((max-min+1)*(rand()/(RAND_MAX+1.0)));
}
[/PHP]

---

