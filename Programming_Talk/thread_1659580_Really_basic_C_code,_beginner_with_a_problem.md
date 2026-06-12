---
title: "Really basic C code, beginner with a problem"
date: 2011-01-04
forum: Programming Talk
---

### Post by CaptainMark on 2011-01-04
Hi, im learning C at the moment (really early days, please be patient) 
My code is this: ```
// number guessing
// a game to demonstrate the isdigit function and if conditions
// mark skinner 
// created - 04/01/2011

#include<stdio.h>
#include<ctype.h>

main()
{

// variable declaration
char cResponse;
int iRandomNumber;

srand(time(0));

printf("\nI am thinking of a number between 1 and 10. "); 
printf("\nWhat do you think the number is? ");
scanf("%c",&cResponse);

iRandomNumber=(rand()%10)+1;

if (isdigit(cResponse))
    {
    printf("Thank you.\n");
    if (cResponse==iRandomNumber)
        printf("Well done the number was %d.\n",iRandomNumber);
    else
        {
        printf("Im sorry that was not the number I was thinking of.\n");
        printf("I was thinking of %d.\n",iRandomNumber);
        } // end else [4 lines]
    } //end if [10 lines]
else 
    printf("That was not a number.\n");
} // end main
```I have a few questions, the book Im learning from seems a bit odd and googling brings up things way above my level right now.
1. The book says to use;

if (isdigit(cResponse) == 1)

instead of

if (isdigit(cResponse) 

for the first If statement, I was under the impression from the book that  isdigit() returns a 1 if true and a 0 if false, so if isdigit(cResponse) is true then it should also equal 1, however when I compile it with isdigit(cResponse)==1 then I always get told, That was not an number. Please help me understand what Im missing

2. Once I changed the line in quesition 1 so it works okay even if i guess the correct number i get told it is the wrong number by the 1st else statement , is this something to do with the fact that im comparing a character (even if its a digit) to an integer. The book hasnt mentioned so far if you can change a variable type halfway through a program so i didnt want to get ahead of myself and start looking to do that, i figured i could just start with an integer type variable but that would make the isdigit function pointless to use here. Is there something I havent thought of that the book is expecting me to realise??

Thanks for any tips,
Mark

---

### Post by PaulM1985 on 2011-01-04
Hi

I have done some googling for your problem.  Here is a useful link:
[http://www.cplusplus.com/reference/clibrary/cctype/isdigit/](http://www.cplusplus.com/reference/clibrary/cctype/isdigit/)

It looks like the function "isdigit" returns a 0 for false and something which is not 0 for true.

For your second problem, I think this is because you are comparing a "char" type and an "int" type. You should convert your char to an int before comparing.  If you look at the link, it suggests converting the char using the "atoi" function.

Hope this solves your problems.

Paul

---

### Post by Arndt on 2011-01-04
> **CaptainMark said:**
> Hi, im learning C at the moment (really early days, please be patient) 
My code is this: ```
// number guessing
// a game to demonstrate the isdigit function and if conditions
// mark skinner 
// created - 04/01/2011

#include<stdio.h>
#include<ctype.h>

main()
{

// variable declaration
char cResponse;
int iRandomNumber;

srand(time(0));

printf("\nI am thinking of a number between 1 and 10. "); 
printf("\nWhat do you think the number is? ");
scanf("%c",&cResponse);

iRandomNumber=(rand()%10)+1;

if (isdigit(cResponse))
    {
    printf("Thank you.\n");
    if (cResponse==iRandomNumber)
        printf("Well done the number was %d.\n",iRandomNumber);
    else
        {
        printf("Im sorry that was not the number I was thinking of.\n");
        printf("I was thinking of %d.\n",iRandomNumber);
        } // end else [4 lines]
    } //end if [10 lines]
else 
    printf("That was not a number.\n");
} // end main
```I have a few questions, the book Im learning from seems a bit odd and googling brings up things way above my level right now.
1. The book says to use;

if (isdigit(cResponse) == 1)

instead of

if (isdigit(cResponse) 

for the first If statement, I was under the impression from the book that  isdigit() returns a 1 if true and a 0 if false, so if isdigit(cResponse) is true then it should also equal 1, however when I compile it with isdigit(cResponse)==1 then I always get told, That was not an number. Please help me understand what Im missing

2. Once I changed the line in quesition 1 so it works okay even if i guess the correct number i get told it is the wrong number by the 1st else statement , is this something to do with the fact that im comparing a character (even if its a digit) to an integer. The book hasnt mentioned so far if you can change a variable type halfway through a program so i didnt want to get ahead of myself and start looking to do that, i figured i could just start with an integer type variable but that would make the isdigit function pointless to use here. Is there something I havent thought of that the book is expecting me to realise??

Thanks for any tips,
Mark

You are right to use "if (isdigit(cResponse))". Even if you know that the returned true value is in fact 1 (it can be any non-zero number), it makes no sense to compare it to 1. Just use boolean entities directly in tests.

In this case, it's even worse, since 'isdigit' doesn't necessarily return 1 for true. It may be implemented as bit masking, and then you get whatever the implementors chose to be the bit for "digit". If your book recommends comparing with 1, I would be inclined to distrust everything else the book says.

You are right that comparing a character with a number is the cause of the later problems. If you read in the character '1', the number in the variable will not be 1, but 49, since that is the ASCII code for '1'.

It's probably better to read in the number as an int, using %d. Then scanf takes care of the checking (as long as you check its return value), and you don't need the later 'isdigit'. Also, the case when the hidden number happens to be 10 will work - it can't now, since you only read one digit.

---

### Post by CaptainMark on 2011-01-04
Thanks that totally cleared things up, i concluded this book is trash and propose a trip to the library to get another, its a shame because i have the python book from the same series and it was brilliant. I think ill use scanf() with a %d conversion specifier and forget isdigit() for this test.

---

### Post by odyniec on 2011-01-04
> **CaptainMark said:**
> 1. The book says to use;

if (isdigit(cResponse) == 1)

You might want to look into the isdigit() man page. Here's what it says:

> **RETURN VALUE**
       The values returned are nonzero if the character c falls into the tested class, and a zero value if not.

So the value is nonzero, but not necessarily 1 -- so apparently the book is wrong on this. What book is it, by the way?

---

### Post by CaptainMark on 2011-01-04
where do i find the man pages for specific functions?

edit: never mind i found them, i had no idea you could fetch man pages for program functions through a terminal i thought it was for program man pages only, you live and learn

2nd edit: the book is called c programming for the absolute beginner, on closer inspection it says to use if isdigit(cResponse)==0 and then work the if and else code in reverse, still i feel this isnt explained very well for beginners and still doesnt forgive the fact that it expects you to compare an int type and char type variable without explaining the problems this would cause,

---

### Post by trent.josephsen on 2011-01-04
N.B. Library manpages are usually in section 3, whereas most user commands are in section 1.  If there's a conflict, the first matching page will be displayed.  For example, typing `man printf` will give you the command printf(1), not the function printf(3).

To see all the manpages named "printf" one after the other, use `man -a printf`.  That will display printf(1), followed by printf(3).  If you know you want the man page in a particular section, you can put it as the first argument to man, like `man 3 printf`.

(I find myself referring to printf(3) fairly often, but I didn't know that printf(1) existed before I accidentally called up its manpage by the command above.)

---

