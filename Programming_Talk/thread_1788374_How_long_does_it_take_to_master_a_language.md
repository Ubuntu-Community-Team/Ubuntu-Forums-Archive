---
title: "How long does it take to master a language?"
date: 2011-06-22
forum: Programming Talk
---

### Post by eagles99 on 2011-06-22
Im a high school student takin a programming class in school. For our summer assignment I just have to define boring terms. Instead of doing that, I just decided
to start programming in C. I know C is not that best language to start off with but I like it the best. I used one of my dad's books called practical c programming. So far in the first month I am enjoying the language but its been nothing more than using control statements to print text. All I know so far is basic assignment statements, variables and arrays.
 
I know I am new to all this so I wanted to ask how long will it take me to learn the basics and then go on to master the language? Also how long will it take me to learn how to code games?
 
This is the best code I can come up with right now maybe it can serve as an indicator.
What do you think of the style? Any advice? oh and Dont laught at it haha :p
 
```

 
/* Simple currency converter. Converts USD to Euros and vice versa */
 
#include <stdio.h>
char input[100];
char input_dollars[100];
char input_euros[100];
int option;
float dollars;
float euros;
 
int main()
{
printf("***********Currency Converter*********\n\n");
printf("Enter 1 for euros to usd or 2 for usd to euros: ");
 
fgets(input, sizeof(input), stdin);
sscanf(input, "%d", &option);
 
if (option == 1)
{
printf("Enter euros amount: ");
fgets(input_euros, sizeof(input_euros), stdin);
sscanf(input_euros, "%f", &euros);
 
dollars = euros * 1.4413;
 
printf("%f euros is %f dollars\n", euros, dollars);
}
 
else if (option == 2)
{
printf("Enter dollar amount: ");
fgets(input_dollars, sizeof(input_dollars), stdin);
sscanf(input_dollars, "%f", &dollars);
 
euros = dollars * .7007;
 
printf("%f dollars is %f euros\n", dollars, euros);
}
else
{
printf("Only 1 and 2 are options\n");
}
 
while (option < 3) /* loops */
{
printf("Enter 1 for euros to usd or 2 for usd to euros: ");
 
fgets(input, sizeof(input), stdin);
sscanf(input, "%d", &option);
 
if (option == 1)
{
printf("Enter euros amount: ");
fgets(input_euros, sizeof(input_euros), stdin);
sscanf(input_euros, "%f", &euros);
 
dollars = euros * 1.4413;
 
printf("%f euros is %f dollars\n", euros, dollars);
}
 
else if (option == 2)
{
printf("Enter dollar amount: ");
fgets(input_dollars, sizeof(input_dollars), stdin);
sscanf(input_dollars, "%f", &dollars);
 
euros = dollars * .7007;
 
printf("%f dollars is %f euros\n", dollars, euros);
}
else
{
printf("Only 1 and 2 are options\n");
}
}
return(0);
} 
```

---

### Post by eagles99 on 2011-06-22
bump

---

### Post by cgroza on 2011-06-22
Putting your code in code tags "```
 //code 
```" makes it a lot more readable.

Now, that is no easy question. Some say that you never master a language, that there is always some little tricks or things that you still have to find out about.

I guess being comfortable with the language and being able to achieve whatever you want in it is a sign that you have it under control.

Also, in your code, a switch statement would be more appropriate to replace all those ifs.
And your currency values, it would be better to put them all in const variables and if they change, you only have to change that in one place.
Or, you could define a macro. Something like:
```
 #define EURO_CUR 0.707 
```

---

### Post by simeon87 on 2011-06-22
It takes 10 years: [source]("http://norvig.com/21-days.html"). Or 10,000 hours. Either way a pretty long while. But you can make a lot of nice things in a shorter period of time, including games :)

---

### Post by eagles99 on 2011-06-22
> **simeon87 said:**
> It takes 10 years: [source]("http://norvig.com/21-days.html"). Or 10,000 hours. Either way a pretty long while. But you can make a lot of nice things in a shorter period of time, including games :)
 
10 years! I got a long way to go haha!

---

### Post by eagles99 on 2011-06-22
Im doing an exercise in my book. Basically I have to make a program which takes an amount of money less than 1 dollar and outputs the exact number of quarters, pennies or dimes needed. For example for .57 cents the program might say two quarters, 1 nickle, 2 pennies. I made the program but it's, its not so great. I first ask the user to input the first digit and then the second digit. With the two digits I use alot of control statements, infact too many control statements. How would you improve it?
 
```

 
#include <stdio.h>
char input_1[100];
char input_2[100];
float amount_1;
float amount_2;
 
    printf("Enter change less than 1 dollar \n\n");
 
    printf("Enter first digit wit out decimal point: ");
    fgets(input_1, sizeof(input_1), stdin);
    sscanf(input_1, "%f", &amount_1);
 
 
    printf("Enter second digit: ");
    fgets(input_2, sizeof(input_2), stdin);
    sscanf(input_2, "%f", &amount_2);
 
    if (amount_1 == .0)
    {
       printf("zero quarters, dimes, and nickles, ");
       }
 
    else if (amount_1 == 1)
    {
         printf("1 dimes, ");
         }
 
 else if (amount_1 == 2)
    {
         printf("4 nickles, ");
         }
 
    else if (amount_1 == 3)
    {
         printf("1 quarter, 1 nickle, ");
         }
 
    else if (amount_1 == 4)
    {
         printf("1 quarter, 1 dimes, 1 nickle, ");
         }
 
    else if (amount_1 == 5)
    {
         printf("2 quarters, ");
         }
 
    else if (amount_1 == 6)
    {
         printf("2 quarters, 1 dime, ");
         }
 
    else if (amount_1 == 7)
    {
         printf("2 quarters, 2 dimes, ");
         }
 
    else if (amount_1 == 8)
    {
         printf("3 quarters, 1 nickle, ");
         }
 
    else if (amount_1 == 9)
    {
         printf("3 quarters, 1 dime, 1 nickle, ");
         }
 
    else
    {
        printf("Error ");
        }
 
    if (amount_2 == 0)
    {
       printf("nothing more. ");
       }
 
    if (amount_2 == 1)
    {
       printf("1 pennie. ");
       }
 
    else if (amount_2 == 2)
    {
         printf("2 pennies. ");
         }
 
    else if (amount_2 == 3)
    {
         printf("3 pennies. ");
         }
 
    else if (amount_2 == 4)
    {
         printf("4 pennies. ");
         }
 
    else if (amount_2 == 5)
    {
         printf("1 nickle. ");
         }
 
    else if (amount_2 == 6)
    {
         printf("1 nickle, 1 pennies. ");
         }
 
    else if (amount_2 == 7)
    {
         printf("1 nickle, 2 pennies. ");
         }
 
    else if (amount_2 == 8)
    {
         printf("1 nickle, 3 pennies. ");
         }
 
     else if (amount_2 == 9)
    {
         printf("1 nickle, 4 pennies. ");
         }
 
    else
    {
        printf("Error ");
        }
 
system("PAUSE");
}
```

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
> **eagles99 said:**
> Im doing an exercise in my book. Basically I have to make a program which takes an amount of money less than 1 dollar and outputs the exact number of quarters, pennies or dimes needed. For example for .57 cents the program might say two quarters, 1 nickle, 2 pennies. I made the program but it's, its not so great. I first ask the user to input the first digit and then the second digit. With the two digits I use alot of control statements, infact too many control statements. How would you improve it?
 
```

 
#include <stdio.h>
char input_1[100];
char input_2[100];
float amount_1;
float amount_2;
 
    printf("Enter change less than 1 dollar \n\n");
 
    printf("Enter first digit wit out decimal point: ");
    fgets(input_1, sizeof(input_1), stdin);
    sscanf(input_1, "%f", &amount_1);
 
 
    printf("Enter second digit: ");
    fgets(input_2, sizeof(input_2), stdin);
    sscanf(input_2, "%f", &amount_2);
 
    if (amount_1 == .0)
    {
       printf("zero quarters, dimes, and nickles, ");
       }
 
    else if (amount_1 == 1)
    {
         printf("1 dimes, ");
         }
 
 else if (amount_1 == 2)
    {
         printf("4 nickles, ");
         }
 
    else if (amount_1 == 3)
    {
         printf("1 quarter, 1 nickle, ");
         }
 
    else if (amount_1 == 4)
    {
         printf("1 quarter, 1 dimes, 1 nickle, ");
         }
 
    else if (amount_1 == 5)
    {
         printf("2 quarters, ");
         }
 
    else if (amount_1 == 6)
    {
         printf("2 quarters, 1 dime, ");
         }
 
    else if (amount_1 == 7)
    {
         printf("2 quarters, 2 dimes, ");
         }
 
    else if (amount_1 == 8)
    {
         printf("3 quarters, 1 nickle, ");
         }
 
    else if (amount_1 == 9)
    {
         printf("3 quarters, 1 dime, 1 nickle, ");
         }
 
    else
    {
        printf("Error ");
        }
 
    if (amount_2 == 0)
    {
       printf("nothing more. ");
       }
 
    if (amount_2 == 1)
    {
       printf("1 pennie. ");
       }
 
    else if (amount_2 == 2)
    {
         printf("2 pennies. ");
         }
 
    else if (amount_2 == 3)
    {
         printf("3 pennies. ");
         }
 
    else if (amount_2 == 4)
    {
         printf("4 pennies. ");
         }
 
    else if (amount_2 == 5)
    {
         printf("1 nickle. ");
         }
 
    else if (amount_2 == 6)
    {
         printf("1 nickle, 1 pennies. ");
         }
 
    else if (amount_2 == 7)
    {
         printf("1 nickle, 2 pennies. ");
         }
 
    else if (amount_2 == 8)
    {
         printf("1 nickle, 3 pennies. ");
         }
 
     else if (amount_2 == 9)
    {
         printf("1 nickle, 4 pennies. ");
         }
 
    else
    {
        printf("Error ");
        }
 
system("PAUSE");
}
```
That depends on ur pace and ur urge to learn....u may get experienced in a language...but i dont think u can know everything about a language....thre r always some tricks or question that make u think how much u still have to learn...

C is a gud start....after that i recommend C++ not hard if u hv ur C concepts intact....then i say u move on to Python or Java...

If u like programming...go for Python....beautiful language....and gud luck :)


and for ur code u may use switches to get rid of those cumbersome if-elses....

---

### Post by ziekfiguur on 2011-06-22
I think a part of your code is missing, as i don't see the beginning of the main function.

Instead of all the `if ... else if' you could use a switch statement which will make your code a lot more compact and readable, however, i think the real challenge here is to compute the amount of coins, not hardcode every possibility.
Also, if you only have one statement after an if, for or while, you don't have to use the {}, the {} are just a way tom make it clear to the compiler that that block should be treated as one statement.
Third, system("PAUSE") is rather nasty, you are starting a separate program just to make sure this one doesn't terminate. Why not use another fgets and discard the result, the effect would be the same.

If you want to do more exercises, a lot of people are using [project euler]("http://projecteuler.net/") as a source of fun yet challenging exercises, by doing that you will also learn something about algorithms and datatypes.
And, though simeon87 is right about the 10 years, a decent course can take you a long way, and usually faster than you learn by yourself.

---

### Post by Bradburts on 2011-06-22
Hi,
To answer your programming problem then something like:
 
```
 
 
int NumberOfCoins( int a_Total )
{
int quaters, dimes, pennies;
 
quaters = a_Total /25;
dimes = (a_Total % 25) / 10;
pennies = (a_Total % 25) % 10;
 
return quaters+dimes+pennies;
}
 

``` 
You can add the sscanf and printf stuff yourself.
As the previous poster says, its good practice to avoid if statements as well as case statements. A decision is a test point and testing is not fun. 
I think that with hard work you can teach yourself to program well within a year. 
I wrote my first moon lander game program within 6 months and many others did similar things. 
The key is to be motivated, to have a target, it doesn't matter what. Games are a good focus.
I wonder if an introspective language/development environment might be a better starting point.
If I weren't in a Ubuntu forum then I would say C# Developer Express. You could then drag and drop and link with short code.
Anyone have a recommendation for Unix reflective programming environment?
C is a great language though and will teach you a lot.
 
PS c if you can figure out how to calculate the number of nickles.

---

### Post by eagles99 on 2011-06-22
> **ziekfiguur said:**
>  Third, system("PAUSE") is rather nasty, you are starting a separate program just to make sure this one doesn't terminate.
 
when I dont use system the program runs for one second and then closes.

---

### Post by cgroza on 2011-06-22
> **eagles99 said:**
> [QUOTE=ziekfiguur;10968832]Third, system("PAUSE") is rather nasty, you are starting a separate program just to make sure this one doesn't terminate.[\QUOTE]
 
when I dont use system the program runs for one second and then closes.
Plus, that is Windows only.

---

### Post by Petrolea on 2011-06-22
> **eagles99 said:**
> [QUOTE=ziekfiguur;10968832]Third, system("PAUSE") is rather nasty, you are starting a separate program just to make sure this one doesn't terminate.[\QUOTE]
 
when I dont use system the program runs for one second and then closes.

Use getchar() (+ this is portable).

---

### Post by andrew1992 on 2011-06-22
Or run it the cool way - through the command line.

---

### Post by ziekfiguur on 2011-06-22
> **andrew1992 said:**
> Or run it the cool way - through the command line.

You really should do this anyway, when you're learning to program you should learn to use the compiler, which means coming up with the right command yourself instead of letting some IDE do it.

---

### Post by eagles99 on 2011-06-22
> **ziekfiguur said:**
> You really should do this anyway, when you're learning to program you should learn to use the compiler, which means coming up with the right command yourself instead of letting some IDE do it.
 
haha I know. I have an IDE and vim text editor but I chose the IDE for now.

---

### Post by andrew1992 on 2011-06-22
Completely agreed. I feel IDEs should be reserved for larger projects only, and only after you gain an understanding of what the compiler actually does (not just some magic).

---

### Post by slavik on 2011-06-23
1. use the macros as was mentioned
2. don't use pauses of any kind, they are stupid and worthless. if you need to keep terminal open, run it in a terminal.
3. your next step will be to learn the following items in the C language:
- struct
- union
- bit operations
- all 30+ of C's keywords (everything else is fair game as far as variable names)

Once #3 is done, start learning about data structures. What is a stack, queue, list? How are they different? How are they the same? Implement each one.

With that, you will have 2 legs up on anyone who yells that Python is the next best thing since sliced bread. (We all know it's Perl).

---

### Post by CptPicard on 2011-06-23
> **weatherlife said:**
>   They say if you really wnat to pick up the language is to visit the country of the native language and stay a while...

I wonder if there is a country for native Clojure or Haskell speakers...

---

### Post by zobayer1 on 2011-06-23
> **Petrolea said:**
> [QUOTE=eagles99;10969176]

Use getchar() (+ this is portable).

90% of times, getchar() will not solve your problem. For example, if you use scanf before it... Cause, then enter you hit to feed to scanf, will also feed getchar().

And to master something is quite a relative phrase, it is almost impossible to keep in memory all the C functions, (stands for all other languages as well). To me, mastering is, if you give me a problem, I will solve it using my language, but here comes the beautiful thing, algorithms, so mastering a language is nothing in fact. You should master the algorithms, then, you can convert them to code with any of you fav language, cause references are available in the net... and in books

---

### Post by eagles99 on 2011-06-23
> **slavik said:**
> 1. use the macros as was mentioned
2. don't use pauses of any kind, they are stupid and worthless. if you need to keep terminal open, run it in a terminal.
3. your next step will be to learn the following items in the C language:
- struct
- union
- bit operations
- all 30+ of C's keywords (everything else is fair game as far as variable names)
 
Once #3 is done, start learning about data structures. What is a stack, queue, list? How are they different? How are they the same? Implement each one.
 
With that, you will have 2 legs up on anyone who yells that Python is the next best thing since sliced bread. (We all know it's Perl).
 
thanks for the tips im gonna follow them

---

### Post by eagles99 on 2011-06-23
> **zobayer1 said:**
> [QUOTE=Petrolea;10969329]
 
90% of times, getchar() will not solve your problem. For example, if you use scanf before it... Cause, then enter you hit to feed to scanf, will also feed getchar().
 
And to master something is quite a relative phrase, it is almost impossible to keep in memory all the C functions, (stands for all other languages as well). To me, mastering is, if you give me a problem, I will solve it using my language, but here comes the beautiful thing, algorithms, so mastering a language is nothing in fact. You should master the algorithms, then, you can convert them to code with any of you fav language, cause references are available in the net... and in books
 
I have a question. Why is it better to use fgets than scanf. My book gave detailed reasons but I couldnt really grasp the concept.

---

### Post by slavik on 2011-06-23
> **zobayer1 said:**
> 
 
I have a question. Why is it better to use fgets than scanf. My book gave detailed reasons but I couldnt really grasp the concept.
scanf has no bound checking and you are asking a stack overflow exploit.

---

