---
title: "very basic C issue with char's and Scanf"
date: 2011-02-03
forum: Programming Talk
---

### Post by VanillaCone on 2011-02-03
[PHP]printf("Enter guess for Cup 1 ('Y' for a marble, 'N' for no marble): ");
        scanf("%c", &cup1);

        printf("Enter guess for Cup 2 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup2);

        printf("Enter guess for Cup 3 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup3);

        printf("Enter guess for Cup 4 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup4);[/PHP]

to save time i didnt paste the whole program just the portion that is having trouble.

The above portion works fine if the user inputs characters. If the user inputs nothing and merely hits enter, the second scan gets stuck and infinitly accepts return characters.

i THINK (im bad at C) it has to do with the scanf buffer, and the fact that its just getting loaded up on return characters.

please advise, ive speant hours scouring google to no avail. (the reason i need it to accept blank space is because thats how the tester for this assignment runs...)

---

### Post by worksofcraft on 2011-02-03
> **VanillaCone said:**
> [PHP]printf("Enter guess for Cup 1 ('Y' for a marble, 'N' for no marble): ");
        scanf("%c", &cup1);

        printf("Enter guess for Cup 2 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup2);

        printf("Enter guess for Cup 3 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup3);

        printf("Enter guess for Cup 4 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup4);[/PHP]

to save time i didnt paste the whole program just the portion that is having trouble.

The above portion works fine if the user inputs characters. If the user inputs nothing and merely hits enter, the second scan gets stuck and infinitly accepts return characters.

i THINK (im bad at C) it has to do with the scanf buffer, and the fact that its just getting loaded up on return characters.

please advise, ive speant hours scouring google to no avail. (the reason i need it to accept blank space is because thats how the tester for this assignment runs...)

I suspect it is because your format contains a space before the %c, so it tries to match it to a character before reading...
brb... I'll check

---

### Post by VanillaCone on 2011-02-03
if theres no space then it doesnt read characters like Y, or N Properly :P, its a vicious cycle

edit: sorry i guess it would be useful to post the WHOLE file incase you want to just test it directly

[PHP]#import <stdio.h>
#import <stdbool.h>



int main(void)
{

    // The user's guess for each cup.
    // These are true if the user guessed there is a marble in that cup, and
    // false is the user guessed that there is not a marble in that cup.
    bool cup1, cup2, cup3, cup4;
    bool mode_checking = false;


    /*
     * Begin Changes Here.
     */

    // Read the user's guesses, and store the appropriate values in
    // cup1 through cup4.
        printf("Enter guess for Cup 1 ('Y' for a marble, 'N' for no marble): ");
        scanf("%c", &cup1);

        printf("Enter guess for Cup 2 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup2);

        printf("Enter guess for Cup 3 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup3);

        printf("Enter guess for Cup 4 ('Y' for a marble, 'N' for no marble): ");
        scanf(" %c", &cup4);


        printf("%c\n", cup1);
        printf("%c\n", cup2);
        printf("%c\n", cup3);
        printf("%c\n", cup4);

         if(cup1 == 'N')
                {
                    cup1 = false;
                }
                else
                    cup1 = true;
         if(cup2 == 'N')
                {
                    cup2 = false;
                }
                else
                    cup2 = true;
         if(cup3 == 'N')
                {
                    cup3 = false;
                }
                else
                    cup3 = true;
         if(cup4 == 'N')
                {
                    cup4 = false;
                }
                else
                    cup4 = true;

    /*
     * End Changes Here.
     */

    // Now, we define our boolean expressions for each clue.

    bool clue1 = (cup1 || cup2 || cup3 || cup4);


    bool clue2 = (cup1 && cup2 == false && cup4 == false) || (cup1 == false && cup2 && cup4 == false) || (cup1 == false && cup2 == false && cup4);



    bool clue3 = (cup3 == false || cup4 == false);

    bool clue4 = (cup1 == cup4);

    bool clue5 = (cup3);


    // Next, we write an expression that is true when all of the clues are satisfied.

    bool isValidGuess = (clue1 && clue2 && clue3 && clue4 && clue5);


    /*
     * Begin Changes Here.
     */

    // Print out the result of applying each clue to aid in debugging.

    if(mode_checking)
    {
        printf("Clue 1 = %d\n", clue1);
        printf("Clue 2 = %d\n", clue2);
        printf("Clue 3 = %d\n", clue3);
        printf("Clue 4 = %d\n", clue4);
        printf("Clue 5 = %d\n", clue5);
        printf("your guess is valid %d\n", isValidGuess);
    }
    /*
     * End Changes Here.
     */






    /*
     * Begin Changes Here.
     */

     if(isValidGuess)
        {
            printf("Your guess is correct.\n");
        }
        else
            printf("Your guess is not correct.\n");

    // Print out whether the user's guess was correct




    /*
     * End Changes Here.
     */


    return 0;
}
[/PHP]

---

### Post by brunolabs on 2011-02-03
Add "fflush(stdin);" after each scanf. And remove the space before %c.

scanf("%c", &cup1);
fflush(stdin);
...

---

### Post by VanillaCone on 2011-02-03
to be honest that was the first thing i tried and it didnt work, and besides i dont want to use fflush, ive read all the negative arguements about it

---

### Post by worksofcraft on 2011-02-03
> **VanillaCone said:**
> to be honest that was the first thing i tried and it didnt work, and besides i dont want to use fflush, ive read all the negative arguements about it

you are right, I can't get it to work either.
Perhaps use fgets or getline to read a whole line at a time?

---

### Post by VanillaCone on 2011-02-03
We havent gotten that far in the course yet, i think id get a talking to if i used things out of my chapter range. But regardless, OTHER people have got it to work just fine.. which makes me even more curious to understand how on earth...

---

### Post by lisati on 2011-02-03
I'm not much of a C programmer, so there's probably a better way of accepting single character input than this: I'd be tempted to use something like getch() in preference scanf().....

---

### Post by bouncingwilf on 2011-02-03
getc() will grab the next character from stdin  - it won't even bother to wait for a return.


Bouncingwilf

---

### Post by dwhitney67 on 2011-02-03
> **VanillaCone said:**
> We havent gotten that far in the course yet, i think id get a talking to if i used things out of my chapter range. But regardless, OTHER people have got it to work just fine.. which makes me even more curious to understand how on earth...

An example:
```

#include <stdio.h>

int main()
{
   char ans[3];
   int  i;

   for (i = 0; i < 3; ++i)
   {
      printf("Enter Y or N: ");

      ans[i] = getchar();

      getchar(); // get and discard newline
   }

   printf("answer 1: %c, answer 2: %c, answer 3: %c\n", ans[0], ans[1], ans[2]);

   return 0;
}

```

P.S.  Note that getchar() returns an int; thus if you expect that the operator of your program will do something nefarious (e.g. enter ctrl-d), then you better do some error checking before assuming that you have the correct data.

---

### Post by dwhitney67 on 2011-02-03
> **bouncingwilf said:**
> getc() will grab the next character from stdin  - it won't even bother to wait for a return.


Bouncingwilf

Wrong.

---

### Post by trent.josephsen on 2011-02-03
So much misinformation... where to start...

fflush isn't defined on input streams, and could possibly do bad things, or nothing at all.  I don't know where so many people get the idea -- probably from Turbo C, along with half the other bad habits new C programmers invariably pick up.

getc() and getchar() are standard.  getch() is not.

bouncingwilf's statement about getc() is incorrect (or at least misleading), as line buffering is a feature of the terminal and has nothing to do with how you pull characters in your program.

dwhitney67's post correctly shows one way to read single characters, and I suggest you imitate it.

---

