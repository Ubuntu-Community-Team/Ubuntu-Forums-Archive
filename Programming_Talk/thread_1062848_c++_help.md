---
title: "c++ help"
date: 2009-02-07
forum: Programming Talk
---

### Post by Vandorin on 2009-02-07
My assignment is " Write a program that allows the user to enter numbers until a -1 is entered.
The program must print the largest and smallest numbers entered by the user"

and im completely lost, now im not asking anyone to do this for me, since i'll never learn that way, but can someone please point me in the right direction?

---

### Post by Zugzwang on 2009-02-07
Well, you have certainly learned how to set up a basic "Hello world" program. Use this as a starting point. Then, since this is your homework, you have learned how to input a number. Finally use variables and a loop to accomplish your task.

---

### Post by Vandorin on 2009-02-07
I still don't really understand who to make a loop, and how can i also tell them the highest number they've entered, and the lowest? When i think about how to do it, my mind breaks haha.

---

### Post by mgerber on 2009-02-07
> **Vandorin said:**
> I still don't really understand who to make a loop, and how can i also tell them the highest number they've entered, and the lowest? When i think about how to do it, my mind breaks haha.

each time you get a number, check it against two variables (ex: min and max). if it's lower than min, assign the number to min, if it's higher than max, assign the number to max. when -1 is entered, print out the two variables.

this is basic programming !!

---

### Post by Vandorin on 2009-02-07
> **mgerber said:**
> each time you get a number, check it against two variables (ex: min and max). if it's lower than min, assign the number to min, if it's higher than max, assign the number to max. when -1 is entered, print out the two variables.

this is basic programming !!

This is my first class, and my teacher isn't that helpful :(.

---

### Post by mgerber on 2009-02-07
> **Vandorin said:**
> This is my first class, and my teacher isn't that helpful :(.

ok ;)

then you should consider buying a book. at some time, o'reilly books were good books, i don't know now.

---

### Post by Vandorin on 2009-02-07
> **mgerber said:**
> ok ;)

then you should consider buying a book. at some time, o'reilly books were good books, i don't know now.

How do i know what values to assign max and min? like if i did min =10 and max =50 and then did the numentered < min stuff, how could i make it so that it covered all numbers?

---

### Post by stevescripts on 2009-02-07
> **Vandorin said:**
> This is my first class, and my teacher isn't that helpful :(.

Bummer ... (I had some like that in college, way back...)

Have you read the stickies?  Nobody here is going to *do* your
assignment for you, but if you make an honest effort, and post some code, you will likely be pointed in the right direction.

Break it down -

First get your program to print a prompt -

Second assign the user's input to a variable -

Third - print the variable to the screen

When you get that much working, the light will probably come on in you head!


Edit - seeing your last post - start with min and max both assigned to zero ...
Steve

---

### Post by Vandorin on 2009-02-07
```

#include <iostream>
using namespace std;
void main()
{
	float num;
	int min =0;
	int max =0;
	cout << " Please enter a number, enter -1 to quit " << endl;
	cin >> num;
	while ( num >= 0 )
		if ( num >= 0 && num <=10 ){
			cout << num = min << endl;

```

that's all i've got so far, i keep having a lot of trouble with this stuff, I am thinking about just changing my major :'(.

---

### Post by stevescripts on 2009-02-07
Main returns an integer - don't get in the habit of voiding main (yes, I know there is a lot of code out there that does - but it is not right).

Dont use a float for anything yet - restrict input to integers...

Keep hacking ! ;)

Steve

---

### Post by Vandorin on 2009-02-07
ok, I am pretty sure i get most of it. I didn't before, but I went out for a run, and it cleared my mind, and made a lot of what your saying make sense, and I am confident i'll get it.

---

### Post by mgerber on 2009-02-08
> **Vandorin said:**
> ```

#include <iostream>
using namespace std;
void main()
{
	float num;
	int min =0;
	int max =0;
	cout << " Please enter a number, enter -1 to quit " << endl;
	cin >> num;
	while ( num >= 0 )
		if ( num >= 0 && num <=10 ){
			cout << num = min << endl;

```

that's all i've got so far, i keep having a lot of trouble with this stuff, I am thinking about just changing my major :'(.

as your assignment is to quit when -1 is entered (and not all numbers below zero), i wouldn't keep that loop condition...

now perhaps you could check your entered value against the min and max variables ??

---

### Post by issih on 2009-02-08
bear in mind that that curly braces define little sections of code...

so:
```

int i=0;
while(i<10)
{
    cout<<i<<endl;
    i++;
}

```
the curly braces define the code that is being completed in the loop, the same goes for the code within a section of an if statement, and for the code within a method.

Therefore it is important to include the closing brace for every opening one :)

If you leave the braces out of statements like while, for and if then only the immediately following expression (i.e. line of code) is considered part of that flow control statement.

Other than that your code isn't that far off. Just change the while condition to only exit if num == -1 rather than <0 and then put a couple of ifs to check if the current num is greater than the current max or less than the current min and update the stored min/max as necessary.

also, you need to consider where the input line should be in relation to the loop...do you want to ask for an input once or many times?

Don't panic just yet, coding takes a bit of time to get your head into. Until you have a feel for looping structures and control flow it will all seem very alien

Good luck :)

---

### Post by dwhitney67 on 2009-02-08
@ OP -

The first value that is entered by the user should be set to the min and the max values.  Do not assume that the user will enter a '0' as the lowest value; they could enter '1' as their lowest value.

The user could also enter ten values of '1', in which case the min and max values would be the same.

Consider setting min and max after you have acquired the first input value from the user; then the rest is trivial.  You merely have to compare these initial values with the subsequent value(s) entered to determine which is the (new) min and max.

Be aware that in C++, there are built-in functions that you can use to deduce the min and max of a pair of numbers.  These are available if you include <algorithm>.  For example:

[php]
int minVal = std::min(20, 10);   // minVal will be set to 10
int maxVal = std::max(30, 35);   // maxVal will be set to 35
[/php]

---

### Post by stevescripts on 2009-02-09
> **dwhitney67 said:**
> @ OP -

The first value that is entered by the user should be set to the min and the max values.  Do not assume that the user will enter a '0' as the lowest value; they could enter '1' as their lowest value.


I suggested that the OP assign 0 to min and max, based on the desire to keep things simple, and my personal preference/habit
of always initializing variables ...

dwhitney67 is quite correct also, to point out that those variables can be first assigned based on the users input.

Edit:  I forgot to mention my personal dis-like for sentinel values (the use of -1 to end accepting input) - it seems to be far too standard of a practice in beginning college C++ programming classes ...

Steve

---

### Post by mgerber on 2009-02-09
> **stevescripts said:**
> I suggested that the OP assign 0 to min and max, based on the desire to keep things simple, and my personal preference/habit
of always initializing variables ...

dwhitney67 is quite correct also, to point out that those variables can be first assigned based on the users input.

Edit:  I forgot to mention my personal dis-like for sentinel values (the use of -1 to end accepting input) - it seems to be far too standard of a practice in beginning college C++ programming classes ...

Steve

Well i think you cannot teach people interrupts in the first lesson... ;)

---

### Post by stevescripts on 2009-02-09
> **mgerber said:**
> Well i think you cannot teach people interrupts in the first lesson... ;)

:) ... true dat!

---

### Post by Krupski on 2009-02-09
> **Vandorin said:**
> This is my first class, and my teacher isn't that helpful :(.

Sorry buddy... we can't do your homework for you, but I can give you some suggestions that might help.

First reserve your variables, especially "min" and "max".

Setup your program to input numbers. Check for -1, and if found print "min" and "max" then exit. 

After you get each number input (that isn't -1), do these two things:

"if input less than min then min = input"
"if input greater than max then max = input"

This will capture your largest and smallest inputs.

Good luck. Any more and I may as well write the code myself... and I graduated decades ago, so it's your turn now buddy!  :)

-- Roger

---

### Post by Krupski on 2009-02-09
> **mgerber said:**
> this is **basic** programming !!

No it isn't. It's C.  :)

---

### Post by mgerber on 2009-02-09
> **Krupski said:**
> No it isn't. It's C.  :)

wouldn't change anything if it was python or any other easy scripting language... ;)

---

