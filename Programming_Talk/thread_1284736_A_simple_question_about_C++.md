---
title: "A simple question about C++"
date: 2009-10-06
forum: Programming Talk
---

### Post by jianan77818 on 2009-10-06
I am just starting to learn the C++ this quarter in my college. And when I doing the self-work in the textbook, I got one question that I don't know how to do it. Can someone here to tell me how to do that?   Here's the question:
Write a program that reads in an integer that is greater than 1,000 and less than 1,000,000.  Recall that the number must be entered without a comma.  Display the number with a comma inserted where it belongs. (Hint: use the % operator.)

I am just a beginner, so please tell the simplest way to do it. Thank you. :)

---

### Post by Reiger on 2009-10-06
Ouch! That is probably done &#8216;easiest&#8217; by skipping the ++ bit in C, and sticking to the C-style idiom. [http://en.wikipedia.org/wiki/Scanf](http://en.wikipedia.org/wiki/Scanf)

---

### Post by jianan77818 on 2009-10-06
But I wanted it in C++ language. Thanks for your reply anyway. :)

---

### Post by TheBuzzSaw on 2009-10-07
Don't listen to Reiger. C++ will do the job just fine.

What part are you struggling with exactly? C++ syntax? The math involved?

---

### Post by kavon89 on 2009-10-07
My bad, thought the assignment requested formatted output.

Which part of the question are you having trouble with?

---

### Post by jianan77818 on 2009-10-07
Actually, I have question for both...
I don't really get this question, so I don't know how to start it.
><

---

### Post by TheBuzzSaw on 2009-10-07
The question is telling you that the user will type, for example, **42863**. Your job is to take that user input and format it properly by inserting commas into the proper locations. So, that input will become output as **42,863**. Input as **1000000** should result in output of **1,000,000**.

Make sense?

---

### Post by kavon89 on 2009-10-07
> **TheBuzzSaw said:**
> The question is telling you that the user will type, for example, **42863**. Your job is to take that user input and format it properly by inserting commas into the proper locations. So, that input will become output as **42,863**. Input as **1000000** should result in output of **1,000,000**.

Make sense?

Ah, OK. So jianan77818, look into iomanip (it's a header file, those include things) to format output, cin to get input, and if statements to check the size of the input.

EDIT: I'm too sleepy to read clearly... your assignment suggests using the modulus (%) operator instead of iomanip to figure out where to put commas, and I forgot the math behind that practice method. I thought you'd covered iomanip like my C++ class.

---

### Post by jianan77818 on 2009-10-07
I have try to do it, but it still having some error. Can you check it out for me?

# include <iostream>
using namespace std;

void main()
{
  
  int number; 
  
  if ((number >= 1000000) && (number <= 1000)) 
    { 
      if (number % 1000 == 0) 
        { 
            cout << "Please enter an integer between 1,000 and 1,000,000: "; 
            cin >> number; 
        } 
      else 
        { 
          cout << number / 1000 << ',' << number % 1000 << endl; 
        }
    } 

}

---

### Post by TheBuzzSaw on 2009-10-07
OK, you're onto a good start. Let's address a few things.

First off, please put your code inside the [**code**] tag.
```
cout << "This will make code more readable." << endl;
```

Make sure to always initialize your variables. Leaving them uninitialized will result in garbage values.
```
int x = 0;
```

Next, what is this if statement here for?
```
if ((number >= 1000000) && (number <= 1000)) 
```
I'm not sure what you are checking here. It also appears to be impossible to satisfy: how can a number be above a million *and* below one thousand at the same time?

You're off to good start. Think through the problem.

---

### Post by jianan77818 on 2009-10-07
How about this one? Is this one right?

# include <iostream>
using namespace std;

void main()
{
  
  int number; 

  cout << "Please enter an integer between 1,000 and 1,000,000: "; 
  cin >> number; 
  
  if ((number >= 1000000) || (number <= 1000)) 
    { 

            cout << "Please enter an integer between 1,000 and 1,000,000: "; 
            cin >> number; 

    } 

  if (number % 1000 == 0) 
        { 
          cout << number / 1000 << ",000" << endl; 
        }
  else 
        { 
          cout << number / 1000 << ',' << number % 1000 << endl; 
        }

}

---

### Post by MadCow108 on 2009-10-07
you still truncate these cases:
1,000,063 results in 1000,63 (because 1,000,063 % 1000 = 63 not 063)
(your also missing one comma in the allowed 1,000,000 case. Use a loop to do this in a general fashion)

use the iomanip headers and the setw and setfill functions of streams to set minimum output size to 3 (setw) and fill the rest with zeros (setfill)

[http://www.cplusplus.com/reference/iostream/manipulators/](http://www.cplusplus.com/reference/iostream/manipulators/)

---

### Post by forrestcupp on 2009-10-07
You're also supposed to instruct the user to not use commas in their entry.

But are we really supposed to do people's homework for them?  Maybe you guys can write a report for me while you're at it.

---

### Post by TheBuzzSaw on 2009-10-07
> **forrestcupp said:**
> You're also supposed to instruct the user to not use commas in their entry.

But are we really supposed to do people's homework for them?  Maybe you guys can write a report for me while you're at it.

We're not "doing the homework for them". If that were the case, I would have posted up the solution code yesterday. He is still having to do all the work even if we say "you need to fix this".

---

### Post by forrestcupp on 2009-10-07
> **TheBuzzSaw said:**
> We're not "doing the homework for them". If that were the case, I would have posted up the solution code yesterday. He is still having to do all the work even if we say "you need to fix this".

Sorry.  I didn't pay close enough attention to realize that the posts with code were posted by the OP.

---

### Post by TheBuzzSaw on 2009-10-07
According to the assignment, he is dealing with numbers *less than* a million. So, he only has to ever deal with one comma (1,000 to 999,999).

---

### Post by MadCow108 on 2009-10-07
it doesn't harm to generalize, especially when you're learning

---

### Post by TheBuzzSaw on 2009-10-07
> **MadCow108 said:**
> it doesn't harm to generalize, especially when you're learning

Agreed, but he really ought to get the assignment done correctly before learning extra stuff. :P

---

### Post by jianan77818 on 2009-10-07
So... Anything that I still have to fix? Or this one is what the question wanted? ^^?

---

### Post by Muffinabus on 2009-10-07
You've almost got it with the last code you posted.  You'll need to add another if statement and your first if statement doesn't work properly, it should be a loop.

I retract my last statement, you'll require at least TWO more if statements.

Think about what your program does when you enter in the numbers 1004 or 1036, for example.

---

### Post by jianan77818 on 2009-10-07
ummm... I have try to fix the first if statement, but I don't really know what should I change. And what else if statement should I add?

---

### Post by MadCow108 on 2009-10-07
better add no if statement and solve it with the stream capabilities c++ provides
just have a look at the page I posted

---

### Post by Muffinabus on 2009-10-07
The result of inputting numbers like 1004 or 10063 are 1,4 and 10,63 with the way that your program is currently setup.  You need to fix that to read 1,004 and 10,063, and so on.

As for your initial if statement, it only checks to see if they've input a number over 1000 and under 1000000 once.  If a user enters the number 10, the program will see that it's not over 1000 and ask to input again.  With the way that you have it setup, is that if the user enters 10 a second time, when prompted, the program then accepts that and continues with the value 10, which is an undesired effect.

> **MadCow108 said:**
> better add no if statement and solve it with the stream capabilities c++ provides
just have a look at the page I posted

Ah yes, that would work too I suppose.  I was just finishing the program in the style he presented it in.

---

### Post by TheBuzzSaw on 2009-10-07
Yeah, don't jump straight to using iomanip. Maybe that is for a future lesson. For the purposes of this assignment, it is probably safe to just use the necessary if-statements.

---

### Post by jianan77818 on 2009-10-07
I change my program in other way. Please check this for me. :)

#include <iostream>
using namespace std;


int main()
{
    
  int number;    //Define number, x, y as int.
  int x;
  int y;
  

  cout << "Please enter an integer between 1,000 and 1,000,000 : ";    //Display the question.
  cin >> number;    //Input the number.
  
  if((number>=1000) && (number<1000000))    //Using if statement to define user's answer.
  {  
     x=number%1000;
     y=((number%1000000)-x)/1000;

     cout<<y<<","<<x<<endl;
  }
  else if (number==1000000)
      cout<<"1,000,000"<<endl;
  else
      cout<<"Out of range"<<endl;



   system("pause");

   return 0;

   

}

---

### Post by MadCow108 on 2009-10-07
input for example 100005 and see what happens
you have still not handled that problem
there are various ways of handling this, most have already been mentioned here:
- c++ stream manipulator
- using C formated print functions (see printf)
- additional if clause
- converting number to string and padding manually
...

also use code tags to format your code in the forum

---

### Post by caelestis2 on 2009-10-07
[PHP]#include <iostream>

using std::cout;
using std::cin;
using std::endl;

int main() {
	int num;
	cout << "Please enter an integer between 1,000 and 1,000,000 : ";
	cin >> num;
	
	int modulus = num%1000;
	if (num >= 1000 && num <1000000) {
		cout << (num-modulus)/1000 << ',';
		if (modulus < 100) cout << '0';
		if (modulus < 10) cout << '0';
		cout << modulus << endl;
	}
	else cout << "out of range" << endl;
	
	cin.get();
	cin.get();
	return 0;
}
[/PHP]

---

### Post by forrestcupp on 2009-10-08
> **Muffinabus said:**
> 
As for your initial if statement, it only checks to see if they've input a number over 1000 and under 1000000 once.  If a user enters the number 10, the program will see that it's not over 1000 and ask to input again.  With the way that you have it setup, is that if the user enters 10 a second time, when prompted, the program then accepts that and continues with the value 10, which is an undesired effect.
Maybe a do while loop if you want to try this again., 

Also, according to your first post, it appears that you are supposed to tell the user not to have commas in their entry.

---

