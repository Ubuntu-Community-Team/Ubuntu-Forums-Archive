---
title: "[c++] formula to determine time to destination"
date: 2009-12-10
forum: Programming Talk
---

### Post by karimruan on 2009-12-10
I am writing a small program that takes two inputs from the user;

1. mph you plan on travelling;
2. miles to travel;

the problem: I suck at math, and cannot determine the formula for calculating how long the travel will be.

I think it is mph / miles = hours of travel;

but, if i input 35 mph and input 7 miles, i get the result 5. 

5 minutes doesn't seem right, and 5 hours doesn't seem right. 

Any ideas?

here is my code;

```



#include <iostream>
using namespace std;
int main()
{
	
	int mph;
	int miles;
	cout << "Please enter the MPH: ";
	cin >> (mph);
	cout << "Please enter total miles to drive: ";
	cin >> (miles);
	cout << endl << endl << "It will take you " << mph / miles << " hours to get to your " << endl;
	cout << "destination.";
	
	return 0;
}


```

---

### Post by cholericfun on 2009-12-10
> 1. mph you plan on travelling;
2. miles to travel;

the problem: I suck at math, and cannot determine the formula for calculating how long the travel will be.

I think it is mph / miles = hours of travel;

but, if i input 35 mph and input 7 miles, i get the result 5. 

5 minutes doesn't seem right, and 5 hours doesn't seem right. 

Any ideas?

OMG theres really no helping you!

so speed = miles/h
time = h
distance = m

so distance/speed turns into time

oh yes, and wheter its minutes or hours or years depends on the units you use. and stay in these units!
i.e. miles and hours and you'll get hours...

---

### Post by dwhitney67 on 2009-12-10
This is first...

```

35 Miles       7 Miles
--------  =  ----------
 1 Hour           x


```
What is the value of 'x'??

Cross-multiply....

35x = 7
x = 7 / 35
x = 1 / 5
x = 0.20

Either way, 1/5 of an hour is

```

60 min        m
------  =  ------
1 hour     0.2 hour

```
Again...

0.2 * 60 = m * 1
m = 12 minutes    <------- Final answer!

---

### Post by karimruan on 2009-12-10
I got it on my own. Like I said, math evades me. Unless I am converting decimal to binary, i am pretty much lost. Especially when it comes to formulas...

anyway, new problem. I built and compiled the revised code fine in geany.

I used ```
 g++ howlong.cpp -o howlong 
``` but it shows nothing!

I am very new to compiled languages, so I am probably doing something wrong.
I know there is an executable in my home directory (a result of my compiling it I believe), so how do i run that. 

Clicking on it does nothing, not even asking to run in terminal or run, display, whatever. 

So, new question, how do i run my c++ executable?

---

### Post by dwhitney67 on 2009-12-10
From the terminal, go to where the executable resides.  Then type in the following:
```

./howlong

```

---

### Post by karimruan on 2009-12-10
> **dwhitney67 said:**
> From the terminal, go to where the executable resides.  Then type in the following:
```

./howlong

```

thanks, i just figured it out!

---

### Post by Arndt on 2009-12-11
> **karimruan said:**
> I am writing a small program that takes two inputs from the user;

1. mph you plan on travelling;
2. miles to travel;

the problem: I suck at math, and cannot determine the formula for calculating how long the travel will be.

I think it is mph / miles = hours of travel;

but, if i input 35 mph and input 7 miles, i get the result 5. 

5 minutes doesn't seem right, and 5 hours doesn't seem right. 

Any ideas?

here is my code;

```



#include <iostream>
using namespace std;
int main()
{
	
	int mph;
	int miles;
	cout << "Please enter the MPH: ";
	cin >> (mph);
	cout << "Please enter total miles to drive: ";
	cin >> (miles);
	cout << endl << endl << "It will take you " << mph / miles << " hours to get to your " << endl;
	cout << "destination.";
	
	return 0;
}


```

This is almost like "I owe you 1000 dollars, I'll pay 100 dollars a month, when will I have paid the debt", and you can't figure out when? This is actually useful in daily life, you know. I suggest you take a book with such problems and really work through them, it will be worth it. No programming, not even paper, just thinking.

---

### Post by karimruan on 2009-12-12
> **Arndt said:**
> This is almost like "I owe you 1000 dollars, I'll pay 100 dollars a month, when will I have paid the debt", and you can't figure out when? This is actually useful in daily life, you know. I suggest you take a book with such problems and really work through them, it will be worth it. No programming, not even paper, just thinking.

If I put math into money terms, it is easier. I had been working a lot lately and my mind was utterly dead. Add that to the fact that I really just don't get math besides adding, multiplying or dividing and there you have it. 

It seems a lot of people on here want to knock someone for not being as proficient in math as they are. It doesn't stop me from working, I get a long fine, but when it comes down to writing a program (i fix computers, not code for a living) that is based on math, well, then I need a little help. 

Not everybody is good at everything, math is my weakness. But, troubleshooting windoze issues is my STRONG point, and it enables me to make my money. 

I barely cared during school, I wasn't the learning type, i was the druggie. I was a hopeless troublemaker. I didn't learn anything in school really, so what I am able to do now is a result of me working my butt off to correct the mistakes of my past.

Thanks to all those who gave their constructive criticism, and sorry for the long tale of why I suck at math. I just felt it needed to be said, if only for my sake.

---

