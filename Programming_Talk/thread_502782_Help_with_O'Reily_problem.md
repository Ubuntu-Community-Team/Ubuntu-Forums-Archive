---
title: "Help with O'Reily problem"
date: 2007-07-17
forum: Programming Talk
---

### Post by sdmike on 2007-07-17
This summer I have been making it my mission to have C++ down solid.

I have been readin O'Reily's C++ book and it's great.

I make sure after every chapter I do all of the practice problems.

I feel bad now because I'm stuck on a problem and I think I'm making it worse by adding all these lines to it, when he says Keep it Simple Stupid.

So here's my code.

[COLOR="Red"]#include <iostream>

int main()

if (grade <  0){
    break;


if (grade > 90&&91&&92&&93&&94&&95&96&&97&&98&&99&&100)
   std::cout << "Your recieved an A." << '\n';

if (grade > 80&&81&&82&&83&&84&&85&&86&&87&&89&&90)
   std::cout << "You recieved a B." << '\n';
}


return (0);
}[/COLOR]

As you can see I would keep going on forever adding in numbers and more if statements. But I know it can be way more simple than this.

I'm thinking I need to use arrays but I'm having trouble figuring out which control statement to use.

So if anyone has any knowledge to pass on that would be great. Just don't totally give it away to me.

:)

---

### Post by Wybiral on 2007-07-17
OK, my hint will be that the AND (&&) operator doesn't work that way... It performs a boolean and between two values...

For instance, 90 && 91, this would actually be 1 since it is true.

If you use, "if(x > 1 && 2 && 3)" then you're actually checking if x is greater than 1... Not all the numbers. Because, 1 && 2 && 3 evaluated to 1 (because none of them are 0).

But, you could say "if(x > 1 && x < 4)" because if "x > 1" and "x < 4" evaluate to true, then the statement itself is true.

I suggest you do some brushing up on your boolean logic operators.

---

### Post by sdmike on 2007-07-17
So the arrays are my next best bet using a break continue statement?

---

### Post by Wybiral on 2007-07-17
> **sdmike said:**
> So the arrays are my next best bet using a break continue statement?

Do you need to check every number, or just a range of numbers like between 90 and 100?

---

### Post by sdmike on 2007-07-17
Ranging them like:

A = 90-100
B = 80-89
etc
etc

---

### Post by Wybiral on 2007-07-17
> **sdmike said:**
> Ranging them like:

A = 90-100
B = 80-89
etc
etc

Oh, then there is a MUCH easier way then using an array...

Because if X is equal-to-or-greater-than 90 AND X is equal-to-or-less-than-100... Then it fits in the A range. That's my hint.

---

### Post by sdmike on 2007-07-17
I totally get what you are saying. One last question Can I keep doing if statements and then one else at the end?

Is that legal?

---

### Post by Wybiral on 2007-07-17
If you mean something like...

```

if(a)
{
    // Do something
}
else if(b)
{
    // Do something
}
else if(c)
{
    // Do something
}
else
{
    // Do something
}

```

Then yes, absolutely.

---

### Post by sdmike on 2007-07-17
But he hasn't mentioned anything in the book about an else if combined.

So is there another way if not then it would be way easy to do it this way.

Thanks for the help BTW.

:)

---

### Post by Wybiral on 2007-07-17
Well, combining them is really just a cool way to use C/C++'s ability to neglect braces for single statements. The above code is just a shorter form of...

```

if(a)
{
    // Do something
}
else
{
    if(b)
    {
        // Do something
    }
    else
    {
        if(c)
        {
            // Do something
        }
        else
        {
            // Do something
        }
    }
}

```

Of course the first looks much better.

---

### Post by sdmike on 2007-07-17
very true

---

### Post by sdmike on 2007-07-17
> #include <iostream>

int grade;

int main()
{

while(true){
std::cout << "Enter the # of points given.\n";
std::cout << "Any # below zero will stop this program:";
std::cin >> grade;

if (grade < 0)
break;

else if (grade >= 90) && (grade <= 100)
{
std::cout << "You have recieved an A";
}
else if (grade >= 80) && (grade <= 89)
{
std::cout << "You have recieved an B";

}
else if (grade >= 70) && (grade <= 79)
{
std::cout << "You have recieved an C";

}
else if (grade >= 60) && (grade <= 69)
{
std::cout << "You have recieved an D";

}
else (grade >= 0) && (grade <= 59)
{
std::cout << "You have recieved an F";
}

return (0);

}

I've come this close. Am I on track here?

---

### Post by H264 on 2007-07-17
You might also want to get a C only book... C++, Objective-C ect. are supersets of the C language. I am working through Objective-C and I am going to get a second C book (the one I currently have does not cover C like I need it to), knowing a good portion of C will help a lot with your programming.

As for your current problem, I think there are enough hints for you to do what you need to... I would add another small one: (I can't resist, lol) do the if checking inside a loop deincrementing betwe... :-# oops, almost said too much ;)

---

### Post by sdmike on 2007-07-17
I need to be using a gui when programming. I loved using vim with the terminal attached to the bottom.

Right now I'm using putty working on my machine remotely. Using nano to write my code in and it's just not as fun as vim.

it's 12:00AM and I'm going to stop here and start back up in the morning.

Thanks for the help.

When I am done tomorrow I shall upload my working code.

---

### Post by Wybiral on 2007-07-17
Remember that the "if" command expects only 1 statement... So it's...

if(some_statement)

But. using the "&&" operator... (some_statement)&&(some_statement) evaluates down to one statement, so then you can use...

```

if((some_statement)&&(some_statement))
{
   // result
}

```

I hope that wasn't confusing (it's hard to articulate).

There is another way you can do your problem...

```

if(x>=90)
{
    // A
}
else if(x>=80)
{
   // B
}
else if(x>=70)
{
   // C
}

```

Maybe that's what your book is expecting?

EDIT:

My other hint would be this... Try small chunks of code at a time. If you aren't sure how a piece of code works in a larger piece of code, take it out and try it on it's own. This condition is a good example, try it on it's own... Not in the while loop. Until you get it down.

---

### Post by H264 on 2007-07-17
My most productive programming hours are between 9pm and 3am or whenever I just fall asleep, sometimes sooner (1am) and sometimes later... lol. Staying up late programming is fun... some people just don't get it :rolleyes:

good luck :)
PS you might want to try Gvim ;)

---

### Post by Note360 on 2007-07-17
> **H264 said:**
> You might also want to get a C only book... C++, Objective-C ect. are supersets of the C language. I am working through Objective-C and I am going to get a second C book (the one I currently have does not cover C like I need it to), knowing a good portion of C will help a lot with your programming.

As for your current problem, I think there are enough hints for you to do what you need to... I would add another small one: (I can't resist, lol) do the if checking inside a loop deincrementing betwe... :-# oops, almost said too much ;)


What Objective C book are you using. I want to learn it but I cant find a good book that isnt OS X specific.

PS IF you are looking for an editor try emacs, gvim, geany,kate and gedit should be something there you like

---

### Post by sdmike on 2007-07-17
> **Note360 said:**
> What Objective C book are you using. I want to learn it but I cant find a good book that isnt OS X specific.

PS IF you are looking for an editor try emacs, gvim, geany,kate and gedit should be something there you like

I have a few good editors it's just when I'm working strictly in the terminal it kinda sucks at times.

Today I'm working with a gui so......YAY for me.

The book I have does go over C to explain certain things here and there but mostly it's C++.

The book I'm using is "Practical C++ Programming" 2nd Edition by O'Reilly.

I've always enjoyed O'Reilly's books because he explains things really well and gives examples for those who are visual learners.

If anyone has any other great authors when it comes to programming please share.

---

### Post by sdmike on 2007-07-17
[SIZE="6"]DONE![/SIZE]

[COLOR="Red"]And it wasn't as hard as I thought![/COLOR]

> /************************************************************
 *                                                          * 
 *Author: SDMike                                            *
 *                                                          *
 *Purpose: The purpose of this program is to convert numeric*
 *       grades into letter grades.                         *
 *                                                          *
 *Usage: Run the program and enter your numeric grade and   *
 *       yourletter grade shall appear.                     *
 *                                                          *
 ************************************************************/


#include <iostream>

int grade; //The users numeric grade

int main()

{
std::cout << "Enter the # of points given.\n";
std::cout << "Any # below zero will stop this program:";
std::cin >> grade;

if(grade>=90)
{
    std::cout << "You have recieved an A" << '\n';
}
else if(grade>=80)
{
    std::cout << "You have recieved an B" << '\n';
}
else if(grade>=70)
{
    std::cout << "You have recieved an C" << '\n';
}
else if(grade>=60)
{
    std::cout << "You have recieved an D" << '\n';
}
else if(grade<=50)
{
    std::cout << "You have recieved an F" << '\n';
}

return (0);

}

---

### Post by bigboy_pdb on 2007-07-17
sdmike, I figured that you might appreciate the following rewrite of the code. At some point you'll probably learn these things from your book, but it wouldn't hurt to mention it now (and besides someone else might read this and benefit from it).

```

#include <iostream>
using std::cout;
using std::cin;
using std::endl;

#include <string>
using std::string;

int main() {
	int numberGrade;
	
	do {
		cout << "Enter the # of points given." << endl;
		cout << "Any # below zero will stop this program: ";
		cin >> numberGrade;
		
		if (numberGrade < 0)
			break;
		
		string letterGrade(
			(numberGrade >= 90) ? 
				"an A" 
			: (numberGrade >= 80) ? 
				"a B"
			: (numberGrade >= 70) ?
				"a C"
			: (numberGrade >= 60) ?
				"a D"
			: 
				"an F"
		);
		
		cout << "You received " << letterGrade << endl;
	} while(true);
	
	return 0;
}

```

The **#include** statement includes a copy of the contents of a file within the code. The **<>** brackets indicate that the file is a standard header file. The **using** statement allows you to omit the **std** prefix (in this case for **cout**, **cin**, **endl**, and **string**). **cout** is for writing to the standard output stream. **cin** is for reading from the standard input stream. **endl** indicates that a return/enter/newline is to be placed in the position where it occurs.

The following code:
```

(numberGrade >= 90) ? 
	"an A" 
: (numberGrade >= 80) ? 
	"a B"
: (numberGrade >= 70) ?
	"a C"
: (numberGrade >= 60) ?
	"a D"
: 
	"an F"

```

Is similar to:
```

if (numberGrade >= 90) {
	return "an A" 
} else if (numberGrade >= 80) {
	return "a B"
} else if (numberGrade >= 70) {
	return "a C"
} else if (numberGrade >= 60) {
	return "a D"
} else {
	return "an F"
}

```

In other words the **(statment) ? value1 : value2** will check if the statement is true and return value1 or value2 (you can only put variable values in place of value1 and value2). When you combine a series of them, they become like "if/else if/else" statements.

Using **string s( "value" )** creates a new string object s that contains the string "value".

When you combine these two concepts they allow you to avoid writing additional code (such as  ifs, elses, and couts).

So basically the concept is that the conditional statement returns the value that is assigned to the string.

---

### Post by Note360 on 2007-07-17
psst. O'Reilly isnt the author ;) its the company ;)

---

### Post by djhworld on 2007-07-17
I know this soudns banal, but the app at the moment will accept a value greater then 90.

Meaning if the user typed, say, 2000, it'd say they got an "A", it's just isn't that out of bounds of what the problem was asking you (I presume 100 is the maximum)

---

### Post by sdmike on 2007-07-17
Did you use a while loop so you could just keep putting in numerical grades? 

It's funny because at first I was doing a while loop but it kept the memory of the past grade I put in and kept print the past grade with the present grade. So I got frustrated and switched.

I figured once it printed it should end because if you get a score of -32, damn either way you should get an F. lol

Thanks for the quick tip.

---

### Post by bigboy_pdb on 2007-07-17
djhworld, I initially thought the same thing as you (that the grades should probably be between 0 and 100), but sometimes teachers give marks over 100 because of bonus questions.

sdmike, I used a loop since you had originally used a loop (I thought that you wanted to keep getting grades until the program ended).

I should also mention that the only reason why I used a "do while" loop instead of a "while" loop is because I was going to change the loop so that it didn't exit using a break statement (because back in high school I was taught that you should attempt to avoid using break statements), but I decided that doing this might make the adjusted program look too different from the original. In short, using a different loop didn't change the code at all.

I also wanted to mention one more thing. It's been a while since I've programmed using C++ (so someone please correct me if I'm wrong about this) and if I remember correctly, declaring variables outside of the block for the main() function makes them global. If this is the case then it is not a good idea to do this. Variables should usually be declared locally within the blocks that they are to be used within. I will give an example of where not doing this can be problematic.

**NOTE**: A block is any segment of code that occurs within two squiggly brackets **{ }**

Pretend that you've declared the variable **i** as a global variable. Also pretend that the function f() has a for loop that uses **i** to count from 1 to 10 and the function g() has a for loop that uses **i** to count from 1 to 20. If f() does not call g() and vice versa then there would be no problems. However, if f() calls g() (within the loop where **i** is being used) then f() will start off with **i** being 1 and when g() is called **i** will be 1. When g() ends **i** will be 20 and f() will finish executing because **i** is greater than 10, meaning f() will not execute using the values from 2 to 10 for **i**. This can cause unnecessary bugs so you're better off avoiding this practice.

---

### Post by Note360 on 2007-07-17
now make this into a function and make something to calculate averages and find the letter grade.

---

### Post by sdmike on 2007-07-17
Ok now I'm asked to modify the program to add a + or - to it when certain numbers are entered in.

for example:
1-3= -
4-7= <blank>
8-0= +

I tried adding in parts like this
```

if(grade>=91)
{
std::cout << "You have recieved an A-" << '\n';
}
if(grade>=97)
{
std::cout << "You have recieved an A" << '\n';
}
if(grade>=100)
{
std::cout << "You have recieved an A+" << '\n';
}
```

I also tried it with the logical && just to see if it would work. HEH, it did not sadly. So I keep re-reading to see what I'm missing here.

So how do I specify inbetween numbers?

---

### Post by bigboy_pdb on 2007-07-17
If you want to check that a number x is between the numbers y and z (inclusive and where y <= z), you can use the following code:
```

if (y <= x && x <= z) {
	// Do something
}

```

**EDIT**:
For example, if you want print something that indicates whether or not a number is between 1 and 3 you could use the following code:
```

// num is the number that you are checking to see whether or not it is between 1 and 3
if (1 <= num && num <= 3) {
	cout << "Number is between 1 and 3" << endl;
} else {
	cout << "Number is not between 1 and 3 << endl;
}

```

---

### Post by sdmike on 2007-07-17
> **bigboy_pdb said:**
> If you want to check that a number x is between the numbers y and z (inclusive and where y <= z), you can use the following code:
```

if (y <= x && x <= z) {
	// Do something
}

```

**EDIT**:
For example, if you want print something that indicates whether or not a number is between 1 and 3 you could use the following code:
```

// num is the number that you are checking to see whether or not it is between 1 and 3
if (1 <= num && num <= 3) {
	cout << "Number is between 1 and 3" << endl;
} else {
	cout << "Number is not between 1 and 3 << endl;
}

```

Thank you that helped a lot.

---

### Post by sdmike on 2007-07-17
```
#include <iostream>

int grade; //The users numeric grade

int main()

{
std::cout << "Enter the # of points given.\n";
std::cout << "Any # below zero will stop this program:";
std::cin >> grade;

if (grade>=91 && grade<=93)
{
std::cout << "You have recieved an A-" << '\n';
}
else if(grade>=94 && grade<=97)
{
std::cout << "You have recieved an A" << '\n';
}
else if (grade>=98 && grade<=100)
{
std::cout << "You have recieved an A+" << '\n';
}
else if(grade>=80 && grade<=83)
{
std::cout << "You have recieved a B-" << '\n';
}
else if(grade>=84 && grade<=87)
{
std::cout << "You have recieved a B" << '\n';
}
else if(grade>=88 && grade<=90)
{
std::cout << "You have recieved a B+" << '\n';
}
else if(grade<=71 && grade<=73)
{
std::cout << "You have recieved a C-" << '\n';
}
else if(grade<=74 && grade<=77)
{
std::cout << "You have recived a C" << '\n';
}
else if(grade<=78 && grade<=80)
{
std::cout << "You have recived a C+ " << '\n';
}
else if(grade<=61 && grade<=63)
{
std::cout << "You have recived a D-" << '\n';
}
else if(grade<=64 && grade<=67)
{
std::cout << "You have recived a D" << '\n';
}
else if(grade<=68 && grade<=70)
{
std::cout << "You have recived a D+" << '\n';
}
else if(grade < 60)
{
std::cout << "You have recived a F" << '\n';
}

return (0);

}

```

So I thought I was on track first because I changed a couple of lines and it worked. But now it's working and then not working.

It seems like it really likes C-.

What am I missing here?

---

### Post by Note360 on 2007-07-17
What I woudl do would divide it up into A B C D F and inside that then add the - or + signs with an additional layer of + or -. This way you dont have to rewrite your old code.

Also you could write a function that dishes out the + or - by having it scan the 1s place (or wtvr its called). I am not exactly sure how to do this myself though. You would probably turn it into an array of characters (if you can) then select the last character. This may be faulty and I wouldnt try it unless you know how to do it. BTW I can read C++ but honestly I cant write it I can only write C.

---

### Post by bigboy_pdb on 2007-07-17
When using mathematical notation, if you want to say that a number x is between 90 and 100 you would use "90 <= x <= 100". You could also say that "90 <= x and x <= 100" and it would be the same thing. Notice that I used "90 <= x" (90 is less than or equal to x) instead of "x >= 90" (x is greater than or equal to 90) which is the same thing. Similarly I used "x <= 100" instead of "100 >= x". The reason why I did this is because if you're looking through your code "90 <= x and x <= 100" can more easily be read as "90 <= x <= 100" by removing the "and" and one "x". 

You are probably getting confused because you are not using a consistent method for writing your statements. First think of them as statements like "80 <= x <= 90" and then write a second "x" ("80 <= x x <= 90") and then place an and in between them ("80 <= x and x <= 90" or in C++ it would be "80 <= x && x <= 90"). Thinking in this manner will most likely help you to reduce the number of errors that you make when writing statements like these.

Another way that you could do it is:
```

if (90 <= x) {
	/* Do something when x is greater than or equal to 90 */
} else if (80 <= x) {
	/* Do something when x was not greater than or equal to 90 but it is greater than or equal to 80 (which is the same thing as x is between 80 and 90 and not equal to 90) */
} else if (70 <= x) {
	/* Do something when x was not greater than or equal to 90 and not greater than or equal to 80 but it is greater than or equal to 70 (which is the same thing as x is between 70 and 80 and not equal to 80) */
...
} else {
	/* Do something when no other condition was met */
}

```

The reason why you can use the code above is because the first condition is attempted and if it fails the second condition is attempted and if it fails the third condition is attempted and so on. If none of the conditions are met then the condition at the **else** part of the if statement is attempted.

---

### Post by bigboy_pdb on 2007-07-17
Note360, I was actually thinking about doing it the same way when I first saw the problem.

The way to do this is to divide the mark by 10 and drop the decimal by converting to an integer (this number is actually the tens digit) to get the grade. Then you can mod the mark by 10 and check the value (which is actually the ones digit) to find out if a plus/minus sign is necessary.

// This moves the decimal to the left and drops everything after the decimal
int firstDigit = mark / 10;
// This gets the last digit by finding the remainder when you divide by 10
int secondDigit = mark % 10;

You can then check the first digit to assign the letter and then check the second digit to determine whether or not you should add a negative sign after the letter. You would check using the same methods mentioned in my last post (and that you were initially attempting to use).

**EDIT**:
For example, if the mark was 82, firstDigit would be 8 and secondDigit would be 2. Since there's an 8, you know that the mark would be a B and since the second digit is a 2, you know that there would be a minus sign.

---

### Post by Note360 on 2007-07-17
Wow. I didnt think of that. I was trying to approach it not as a math problem but as a string, however that is much simpler. I cant believe I didnt get it. (actualyl I can). If I was looking at it as a math problem I would have though. I always have that problem in math. I approach it by brute force and treat it as a string (mroe or less) rather than an int.

---

### Post by sdmike on 2007-07-18
I still don't get why my program isn't giving me correct outputs for + & - grades.

---

### Post by sdmike on 2007-07-18
```
#include <iostream>

int grade; //The users numeric grade

int main()

{
std::cout << "Enter the # of points given.\n";
std::cout << "Any # below zero will stop this program:";
std::cin >> grade;

if (grade>=91 && grade<=93)
{
std::cout << "You have recieved an A-" << '\n';
}
else if(grade>=94 && grade<=97)
{
std::cout << "You have recieved an A" << '\n';
}
else if (grade>=98 && grade<=100)
{
std::cout << "You have recieved an A+" << '\n';
}
else if(grade>=80 && grade<=83)
{
std::cout << "You have recieved a B-" << '\n';
}
else if(grade>=84 && grade<=87)
{
std::cout << "You have recieved a B" << '\n';
}
else if(grade>=88 && grade<=90)
{
std::cout << "You have recieved a B+" << '\n';
}
else if(grade<=71 && grade<=73)
{
std::cout << "You have recieved a C-" << '\n';
}
else if(grade<=74 && grade<=77)
{
std::cout << "You have recived a C" << '\n';
}
else if(grade<=78 && grade<=80)
{
std::cout << "You have recived a C+ " << '\n';
}
else if(grade<=61 && grade<=63)
{
std::cout << "You have recived a D-" << '\n';
}
else if(grade<=64 && grade<=67)
{
std::cout << "You have recived a D" << '\n';
}
else if(grade<=68 && grade<=70)
{
std::cout << "You have recived a D+" << '\n';
}
else if(grade < 60)
{
std::cout << "You have recived a F" << '\n';
}

return (0);

}
```

I'm still at a loss why this isn't working.

---

### Post by Note360 on 2007-07-18
else if(grade<=61 && grade<=63)

a grade lessthan or equal to 61 and less than or equal to 63 is 63 62 61 60 59 etc

else if(grade>=61 && grade<=63)

61 62 63

---

### Post by sdmike on 2007-07-18
That's what I get for copying and pasting an error.

TY

---

### Post by Note360 on 2007-07-18
idk if that was it, but thats what I saw. Also you can use all the talk of division and mods if you want, but thats only if you understand wht they are doign

(number/10 number%10)

---

### Post by sdmike on 2007-07-18
[COLOR="Red"][SIZE="5"]DONE with the modification![/SIZE][/COLOR]
:o
```

#include <iostream>

int grade; //The users numeric grade

int main()

{
std::cout << "Enter the # of points given.\n";
std::cout << "Any # below zero will stop this program:";
std::cin >> grade;

if (grade>=91 && grade<=93)
{
std::cout << "You have recieved an A-.\n";
}
else if(grade>=94 && grade<=97)
{
std::cout << "You have recieved an A.\n";
}
else if (grade>=98 && grade<=100)
{
std::cout << "You have recieved an A+.\n";
}
else if(grade>=80 && grade<=83)
{
std::cout << "You have recieved a B-.\n";
}
else if(grade>=84 && grade<=87)
{
std::cout << "You have recieved a B.\n";
}
else if(grade>=88 && grade<=90)
{
std::cout << "You have recieved a B+.\n";
}
else if(grade>=71 && grade<=73)
{
std::cout << "You have recieved a C-.\n";
}
else if(grade>=74 && grade<=77)
{
std::cout << "You have recived a C.\n";
}
else if(grade>=78 && grade<=80)
{
std::cout << "You have recived a C+.\n";
}
else if(grade>=61 && grade<=63)
{
std::cout << "You have recived a D-.\n";
}
else if(grade>=64 && grade<=67)
{
std::cout << "You have recived a D.\n";
}
else if(grade>=68 && grade<=70)
{
std::cout << "You have recived a D+.\n";
}
else if(grade < 60)
{
std::cout << "You have recived a F.\n";
}

return (0);

}
```

---

