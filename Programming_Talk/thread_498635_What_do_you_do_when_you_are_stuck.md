---
title: "What do you do when you are stuck?"
date: 2007-07-11
forum: Programming Talk
---

### Post by TreeFinger on 2007-07-11
I am currently reading, 'Practical C Programming, 3rd Edition'. I am on the 7th Chapter, not very far.

I am on the review questions and I am just completely stuck on one. It is getting me frustrated. The problem asks to write a program to perform date arithmetic such as how many days are there between 6/6/90 and 4/3/92.

I can't figure out a way to do it with total amount of days. I've been just straight thinking in my head how I could do this but I can't.

So my question to you all is what do you do when you are stuck with a problem and can't figure out how to do it? Is asking for help bad to do when you are learning programming?

For this problem all I know I would have to do is say for the above example is subtract 1992 - 1990 = 2. So the amount of days from just the year portion would be 2 * 365. The days would be 6-3 = 3 days. The month is where I run into trouble. 6 - 4 is of course 2 months but each month has a different amount of days! How the hell can I write a program to figure this out?

---

### Post by AlexThomson_NZ on 2007-07-11
The way I would do it is by having a 12-element array with the number of days in each month.

Make sure you allow for leap-years though! :)

---

### Post by aks44 on 2007-07-11
> **TreeFinger said:**
> So my question to you all is what do you do when you are stuck with a problem and can't figure out how to do it?
I then ask for help...(see below)

> **TreeFinger said:**
> Is asking for help bad to do when you are learning programming?
Sure it is not bad asking for help. No one knows all, information and knowledge have to be exchanged.

Just don't expect other people to do your own work, they are only here to "enlighten" you. When you ask for help, don't attempt to be spoon fed, but rather explain: "*here's my goal, I tried this and that, with such and such results, any ideas about what I am doing wrong?*". Don't forget that when learning programming, you're the one that is the most likely to be wrong (and I can tell you it stills hold true even after 10+ years of practice ;))

As far as you're concerned, I'd say you're on the good way. Presenting your question like you did is a sign that you didn't just think "*well it is boring me, let's just ask*" but instead really tried to solve your problem and came to a dead end.


Concerning the problem at hand... here's a tip: doesn't C provide 2 representations (read: types) for a date/time value, and the associated functions to convert between them?

I'll let you try to figure it out by yourself for a while, as you seem to be inclined to solve it by yourself. Just ask again here if you still are stuck ;)

---

### Post by rekahsoft on 2007-07-11
What do you do when you get stuck?

* Ask on apropriate mailing lists,IRC, and of course the Ubuntu Forums
* Relax, take a break and rest your mind.
* If you have been working for a long time or are tired...you will function better when u are alert and awake :P

---

### Post by AlexThomson_NZ on 2007-07-11
> **aks44 said:**
> 
Concerning the problem at hand... here's a tip: doesn't C provide 2 representations (read: types) for a date/time value, and the associated functions to convert between them?

Ahh of course, forgot about that! :)  Don't do it my way...

---

### Post by regomodo on 2007-07-11
what the 2nd poster said. I could write a bit in vhdl but i doubt that'll help

---

### Post by TreeFinger on 2007-07-11
Well I have been thinking about this program for most of the day and had just recently started to do some coding a little while ago. I am going to use the 12 element array because since I am following a book I only want to use the knowledge that was taught in the book so far to complete the exercise.

So right now I am working on problems that would be in the same year. Here is the code I have so far :) Seems to work pretty good as long as you enter the most recent date first.

```

/* Programming exercises. Chapter 7-2
*  Created by Samuel Chodur Jr.
*  Program: Performs Date Arithmitic
*/

#include <stdio.h>

char input[100];
int day_one, day_two; /* Inputs from user */
int month_one, month_two; /* Inputs from user */
int year_one, year_two; /* Inputs from user */

int days_in_month[12]; /* How many days in a certain month */

int month_count; /* while counter */

int total_days; /* Output to display for user */

int main() {
/* Assigning the days in a month to days_in_month array */
days_in_month[0] = 31; /* Days in January */
days_in_month[1] = 28; /* Feb */
days_in_month[2] = 31; /* March */
days_in_month[3] = 30; /* April */
days_in_month[4] = 31; /* May */
days_in_month[5] = 30; /* June */
days_in_month[6] = 31; /* July */
days_in_month[7] = 31; /* August */
days_in_month[8] = 30; /* September */
days_in_month[9] = 31; /* October */
days_in_month[10] = 30; /* November */
days_in_month[11] = 31; /* December */

total_days = 0;

	/* Tell user what program does */
	printf("I will give you the total amount of days between two dates.\n");
	printf("You will enter dates in dd mm yy form. For example, July 11 2007 would be 11 7 2007.\n");

	/* Get First date from user */
	printf("Enter most recent date now: ");
	fgets(input, sizeof(input), stdin);
	sscanf(input, "%d %d %d", &day_one, &month_one, &year_one);

	/* Get second date from user */
	printf("Enter second date now: ");
	fgets(input, sizeof(input), stdin);
	sscanf(input, "%d %d %d", &day_two, &month_two, &year_two);

	/* Finding Amount of days */
	if ( ( year_one == year_two ) && ( month_one != month_two ) ) { /* If two different months in same year */
		total_days = days_in_month[month_two-1] - day_two; /* Finds total days that are left in current month */
		month_count = ++month_two; /* Goes to the next month */

		while ( month_count <= month_one ) { /* Loop ends when lesser month is greater */
			if ( month_count == month_one ) { /* Happens when while loop is on last run */
				total_days = total_days + day_one;
				++month_count;
			}
			else { /* Happens when while loop first starts */
				total_days = total_days + days_in_month[month_count-1];
				month_count = ++month_two;
			}
		}
	}
	printf("Total days is %d\n", total_days);

return 0;
}

```

Well for now I am off to the movies, hopefully I can finish the program tonight or tomorrow!

Thanks for all the replies!

---

### Post by samjh on 2007-07-11
When I'm stuck on producing an algorithm to solve a problem, I do this:[list=1][*]Think about how I'd solve the problem in my head.[*]Write down those steps on a piece of paper, detailing every single mental process.[*]Try to translate those processes into pseudo-code.[*]Try to translate the pseudo-code into the programming language I'm using[/list]That strategy works for about 90% of programming problems.

For the other 10%, I use:[list][*]Google[*]Ask on a forum or mailing list.[/list]

So for your particular problem:> I am on the review questions and I am just completely stuck on one. It is getting me frustrated. The problem asks to write a program to perform date arithmetic such as how many days are there between 6/6/90 and 4/3/92.I would calculate the number of days from 6/6/90 to 31/12/90.  Then I'd calculate the number of days from 31/12/90 to 1/1/92.  Then I'd calculate the number of days from 1/1/92 to 4/3/92.  Then I'd add the three values together to reach the final sum.

That's a very general outline, so I'd have to dig deeper into details to make it work.  So how would I calculate the number of days within a month?  Within a year?  I could hard-code the number of days for each month into my program.  Or alternatively calculate the number of days in a given month programmatically, thus:
```
If month is 1 OR 3 OR 5 OR 7 OR 8 OR 10 OR 12 then
    Days_in_Month = 31
If month is 2 AND year is not Leap_Year then
    Days_in_Month = 28
If month is 2 AND year is Leap_Year then
    Days_in_Month = 29
If month is 4 OR 6 OR 9 OR 11 then
    Days_in_Month = 30
```
To calculate the number of days between two dates within a month, I could do something like:
```
If Month and Year in Date1 = month and Year in Date2 then
    Num_of_Days = Day in Date2 - Day in Date1
```
There you go, some example pseudo-code for you to play with.  Think some more stuff yourself and see how they can be fitted into your program.

Start with a big mental process, and then break those processes down into smaller ones until you have nutted out the details.  Then you can put that into code.

---

### Post by AlexenderReez on 2007-07-11
hm....for me python is more interesting and easier than c......i learned c before python.....

---

### Post by TreeFinger on 2007-07-11
> **samjh said:**
> When I'm stuck on producing an algorithm to solve a problem, I do this:[list=1][*]Think about how I'd solve the problem in my head.[*]Write down those steps on a piece of paper, detailing every single mental process.[*]Try to translate those processes into pseudo-code.[*]Try to translate the pseudo-code into the programming language I'm using[/list]That strategy works for about 90% of programming problems.

For the other 10%, I use:[list][*]Google[*]Ask on a forum or mailing list.[/list]

Thanks for detailing the process you would use. Your post is very helpful to beginner programmers. I am going to save it for future reference.

---

### Post by bashologist on 2007-07-11
When I'm reading a book and get stuck I sometimes will cheat!! Look near the back of the book and there's usually an answer. As long as you understand that's all that really matters.

---

### Post by samjh on 2007-07-11
> **TreeFinger said:**
> Thanks for detailing the process you would use. Your post is very helpful to beginner programmers. I am going to save it for future reference.

I've elaborated my post a bit further to see if I can give you a kick-start. ;)

---

### Post by AlexThomson_NZ on 2007-07-11
It looks like you are making good progress TreeFInger.

In case you are wondering about the "easy" way, I think there is a function that, given a date, will return the number of seconds (or milliseconds?) since a certain date (can't remember what it is off-hand).  If you know these two values, you can simply subtract them and get the difference.

Are you allowed to use stddate?  Isn't there a function there, difftime()?

---

### Post by Wim Sturkenboom on 2007-07-12
Asking for help is not bad; you will never learn if you don't ask. One of the problems is that while learning, you don't know 90% of the functions.

With regards to the problem:
Read up on the **mktime** function; it takes a date (in some way) and converts it to seconds since the first of januari 1970.

So calculate the seconds for the first date, calculate the seconds for the second date, subtract them, divide by 60 to get minutes, by 60 again to get hours and by 24 to get days.
By the way, easier to divide the difference by 86400 straight away :).

---

### Post by AlexThomson_NZ on 2007-07-12
> **Wim Sturkenboom said:**
> Asking for help is not bad; you will never learn if you don't ask.

With regards to the problem:
Read up on the **mktime** function; it takes a date (in some way) and converts it to seconds since the first of januari 1970.

So calculate the seconds for the first date, calculate the seconds for the second date, subtract them, divide by 60 to get minutes, by 60 again to get hours and by 24 to get days.
By the way, easier to divide the difference by 86400 straight away :).

Ahh thanks Wim, that clarifies my half-@rsed post :)

---

### Post by runningwithscissors on 2007-07-12
I never do examples from books. I find that they usually require you to come up with mathematical algorithms, and I'm woeful at maths.

Pick a project and learn-as-you-go is more my style. If I get stuck in there somewhere, I ask for help on the 'net.

---

### Post by c174 on 2007-07-12
Another point of view is what kind of code you want to generate. Should it be

1) Fast
2) Easy to understand
3) Easy to program
4) ... or something else

I think an easy way to find the number of days between to dates is to use a simple counter:

- start at the current DAY
- increase DAY and COUNTER until the month flips over
- reset DAY and increase MONTH
- ....
- keep increasing DAY, MONTH, YEAR, and COUNTER until the final date is reached

Now the number of days is given by COUNTER (perhaps minus 1). It should be easy to account for leap years and the uneven number of days in a month.

Cons: The program will take longer time, if the dates a far apart. Not constant computing time.
Pro: Very easy to implement. For "normal" requests the computing time is vanishing on a modern computer

---

