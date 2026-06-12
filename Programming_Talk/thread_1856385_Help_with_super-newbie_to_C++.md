---
title: "Help with super-newbie to C++"
date: 2011-10-08
forum: Programming Talk
---

### Post by TheBetrayer142 on 2011-10-08
Hey all,

Wanted to start by saying that I'm in love with C++ having only started learning any programming at all 5 weeks ago (all C++).

Now, here's my problem. I'm trying to create a basic ball-bouncing function using animation loops but I keep getting the

"invalid operands of types `double' and `int' to binary `
   operator^"
error code.

The Program:
> 
// Directives:
#include <cmath>
#include <cstdlib>
#include <iostream>
#include <graphics.h>
using namespace std;

// Constants:

const int S = 500;
const int FPS = 30;

// Prototypes:
void ball(double x, double y, double d);

// --------------------------------------------------------------------------
// Main Function:
int main()
{
    double t = 0; // time in seconds
    double x = 0, y = 0; // starting point for ball

    initwindow(S, S, "Extremelly Low Kinetic Energy Loss", 0, 0, true);

    while(true)
    {
	// Calculations
	t+= 1.0/FPS;
	x = 50*t;
	
	while(0 < x < S/4)
	{
	    [COLOR="Red"]y = (-4*x^2 + S/8) + S/2;[/COLOR]
	}
	
	while(S/4 <= x < S/2) 
	{
	    [COLOR="Red"]y = (-4*x^2 + (3*S/8)) + S/2;[/COLOR]
	}
	
	while(S/2 <= x < 3*S/4)
	{
	   [COLOR="Red"]y = (-4*x^2 + (5*S/8)) + S/2;[/COLOR]
	}

	while (3*S/4 <= x <= S)
        {
	   [COLOR="Red"]y = (-4*x^2 + (7*S/8)) + S/2;[/COLOR]
	}
	
	// Next Frame
	clearviewport();
	ball(x, y, S/50);

	// Swap Buffers and Delay
	swapbuffers();
	delay(1000/FPS);	


    }
    delay(5000);

    return EXIT_SUCCESS;

}
// -------------------------------------------------------------------------

// -------------------------------------------------------------------------
void ball(double x, double y, double d)
{
    circle(int (x), int (y), int (d));
}
// -------------------------------------------------------------------------


Those stupid smiley faces are supposed to be 8s.


THE ERRORS:

> 
ball.cxx: In function `int main()':
ball.cxx:38: error: invalid operands of types `double' and `int' to binary `
   operator^'
ball.cxx:43: error: invalid operands of types `double' and `int' to binary `
   operator^'
ball.cxx:48: error: invalid operands of types `double' and `int' to binary `
   operator^'
ball.cxx:53: error: invalid operands of types `double' and `int' to binary `
   operator^'


The above errors are each assigned to the y functions within each of those loops.

I know it's really simple, but I'm just trying to make a solid foundation to go off of!

THANK YOU ALL VERY MUCH!

---

### Post by matt_symes on 2011-10-08
Hi

Are you trying to use the ^ operator as a power operator ? If so then use the pow(,) function.

Also, calculate all your constants outside your loops. I.E. S/4 etc. Don't have a calculation in the loops condition if you can help it.

Kind regards

---

### Post by TheBetrayer142 on 2011-10-08
> **matt_symes said:**
> Hi

Are you trying to use the ^ operator as a power operator ? If so then use the pow(,) function.

Also, calculate all your constants outside your loops. I.E. S/4 etc. Don't have a calculation in the loops condition if you can help it.

Kind regards

Alright, I used the pow function and it compiled correctly. However, when I open the program itself, nothing shows up?

Could it be a error within the multiple "while" loops I used?

Understand that I want the ball to move in 4 parabolic methods (1 for each 1/4th of the x line until x=S, or 500 pixels)

What happened?

Thanks again!

---

### Post by matt_symes on 2011-10-08
Hi

> **TheBetrayer142 said:**
> Alright, I used the pow function and it compiled correctly. However, when I open the program itself, nothing shows up?

Could it be a error within the multiple "while" loops I used?

Understand that I want the ball to move in 4 parabolic methods (1 for each 1/4th of the x line until x=S, or 500 pixels)

What happened?

Thanks again!

Part of the craft of writing good software is knowing how to debug it.

This will be a really good exercise for you. Spend some time trying to track down the problem. It will benefit you hugely.

Kind regards

---

### Post by PaulM1985 on 2011-10-08
> **TheBetrayer142 said:**
> Alright, I used the pow function and it compiled correctly. However, when I open the program itself, nothing shows up?

Could it be a error within the multiple "while" loops I used?

Understand that I want the ball to move in 4 parabolic methods (1 for each 1/4th of the x line until x=S, or 500 pixels)

What happened?

Thanks again!

I would say yes, it is an issue with your while loops.  Think how while loops work, while the condition is true in the "(..)" it will continue to execute the code in the "{...}".  Can you see any while loops where the condition will remain the same?

As an example, if I have in my program:
```

int max_loops = 100;
int i =0;
while (i < max_loops)
{
   i++;     // increment i
}

```
I know that the condition in the while loop will eventually be false.

But if I have:
```

int max_loops = 100;
int i = 0;
int j = 0;
while (i < max_loops)
{
   j = i + 30;
}

```
Will this loop ever end?  Do the variables in the condition change?

Also, I would recommend using a statement like this:
```

if (0 <= x **&&** x <= some_number)

```

rather than:
```

if (0 <= x <= some_number)

```

because I think (and someone please correct me if I am wrong), in this second statement, it will be evaluated as follows:
Assume x = 10 and some_number = 20,
```
if (0 <= x <= some_number)
```
becomes
```
if (true <= some_number) - (o <= x) evaluated to "true"
```
becomes
```
if (1 <= some_number) - "true" gets promoted to an integer which is 1 (false is 0)
```
becomes:
```
if (true)
```

Imagine if x was 100 and some_number was 20.  (0 <= x) would become true (and get promoted to 1), then we would have (true <= some_number).  Which is not what you want.

If you use if(0 <= x && x <= some_number) it would evaluated each part separately, so you don't get this problem.

Does this make sense?

Paul

---

### Post by TheBetrayer142 on 2011-10-08
Alright, I understand what you're saying and I added the "&&" code lines to my while statements, but it still shows just a black screen!

A couple of things I think might be wrong:

1) I'm using the standard pixel coordinate system (y goes from top down, x still goes from left to right). Could I have used a bad equation for my y?

2) I'm sure I used the pow function correctly, but am I implimenting it wrong?

I want the equation of (-4x^2 + S/8) + S/2
for the first while loop and I want to shift the same parabola S/4 to the left for each loop.

here's my latest code:

> 
// Main Function:
int main()
{
    double t = 0; // time in seconds
    double x = 0, y = 0; // starting point for ball

    initwindow(S, S, "Extremelly Low Kinetic Energy Loss", 0, 0, true);

    while(true)
    {
	// Calculations
	t+= 1.0/FPS;
	x = 50*t;
	
	while(0 < x && x < S/4)
	{
	    y = (-4*(pow(x,2)) + S/8) + S/2;
	}
	
	while(S/4 <= x && x < S/2) 
	{
	    y = (-4*(pow(x,2)) + (3*S/8)) + S/2;
	}
	
	while(S/2 <= x && x < 3*S/4)
	{
	    y = (-4*(pow(x,2)) + (5*S/8)) + S/2;
	}

	while (3*S/4 <= x && x <= S)
        {
	    y = (-4*(pow(x,2)) + (7*S/8)) + S/2;
	}
	
	// Next Frame
	clearviewport();
	ball(x, y, S/50);
	
	// Swap Buffers and Delay
	swapbuffers();
	delay(1000/FPS);	


    }
    delay(5000);

    return EXIT_SUCCESS;


---

### Post by Vaphell on 2011-10-08
use [code] tags not [quote] tags to embed your program

---

### Post by muteXe on 2011-10-08
You only ever go into the first while loop.
As far as i can see the value of x never changes? It's always 1.6666666, which is between 0 and your S/4 condition, but that's it.

---

### Post by gardnan on 2011-10-08
Your program appears to enter an infinite loop at the first inner while statement.
```

while(0 < x && x < S/4)
    {
        y = (-4*(pow(x,2)) + S/8) + S/2;
    }
```The condition for this loop depends on x, but x is never changing within the loop: the only statement is an assignment for the variable y. 

It appears that you are directly translating mathematical statements to a computer program. If you want the program to work correctly, you have to change the variable x at some point, as opposed to math, where the value x is any value in the domain of a function. Keep in mind that expressions in a programming language are different than those in math. Specifying that y = ( -4x² + S/8 ) + S/2 where 0 < x < S/4 is a valid equation for a parabolic function, but in programming, that just assigns the the value of the expression on the right hand side to the variable y, without changing the x coordinate of the image you are drawing. 

What I imagine you want is  basically 

```
while ( x <= S )
{
     if ( x > 0 && x < S/4)
     {
         y = (-4*pow(x,2) + S/8 ) + S/2;
     }
     else if ( x > S/4 && x < S/2 )
     {
         y = (-4*(pow(x,2)) + ( 3*S/8 ) + S/2;
     }
     else if ( x > S/2 )
    {
        y = (-4*(pow(x,2)) + ( 7*S/8 ) + S/2;
     }
     clearviewport();
     ball(x, y, S/50);
     swapbuffers();
     x++;
     delay(1000/FPS);
}
```

---

### Post by TheBetrayer142 on 2011-10-08
> **gardnan said:**
> Your program appears to enter an infinite loop at the first inner while statement.
```

while(0 < x && x < S/4)
    {
        y = (-4*(pow(x,2)) + S/8) + S/2;
    }
```The condition for this loop depends on x, but x is never changing within the loop: the only statement is an assignment for the variable y. 

It appears that you are directly translating mathematical statements to a computer program. If you want the program to work correctly, you have to change the variable x at some point, as opposed to math, where the value x is any value in the domain a function. Keep in mind that expressions in a programming language are different than those in math. Specifying that y = ( -4x² + S/8 ) + S/2 where 0 < x < S/4 is a valid equation for a parabolic function, but in programming, that just assigns the the value of the expression on the right hand side to the variable y, without changing the x coordinate of the image you are drawing. 

What I imagine you want is a basically 

```
while ( x <= S )
{
     if ( x > 0 && x < S/4)
     {
         y = (-4*pow(x,2) + S/8 ) + S/2;
     }
     else if ( x > S/4 && x < S/2 )
     {
         y = (-4*(pow(x,2)) + ( 3*S/8 ) + S/2;
     }
     else if ( x > S/2 )
    {
        y = (-4*(pow(x,2)) + ( 7*S/8 ) + S/2;
     }
     clearviewport();
     ball(x, y, S/50);
     swapbuffers();
     x++;
     delay(1000/FPS);
}
```

Alright, I tried adding the "x++" statement and modifying my loop statements to what was above, but it still did not show the animation. Is it still getting stuck in the first loop? Is it because I set my x variable to compute 50*t above the loop in the main function?

---

### Post by Vaphell on 2011-10-08
can't you sprinkle your code with std::cout liberally so you get to know where in the program you are exactly?
i commented out everything graphics.h related and added **cout << "while_id x=" << x " y=" << y << endl;** here and there and all i see is (on older version of your code):
```

...
(0 < x < S/4) x=1.66667 y=300.889
(0 < x < S/4) x=1.66667 y=300.889
(0 < x < S/4) x=1.66667 y=300.889
...

```

either way do the same, print something out to the console so you know anything. Forget about graphics for now, get things straight in core algorithm.

---

### Post by MG&amp;TL on 2011-10-08
Run it from the command-line:

```
cd <folder containing program>
./programname
```If the command completes, it's not doing anything for whatever reason. If it doesn't it's getting stuck somewhere.

also, use g++'s debugger:

```
g++ -g -o <name> <source files.cpp>
gdb <name>
run
```

---

### Post by TheBetrayer142 on 2011-10-08
> **MG&TL said:**
> Run it from the command-line:

```
cd <folder containing program>
./programname
```If the command completes, it's not doing anything for whatever reason. If it doesn't it's getting stuck somewhere.

also, use g++'s debugger:

```
g++ -g -o <name> <source files.cpp>
gdb <name>
run
```

I tried running it and debugging, but I couldn't get far with debugger because I couldn't get it to work.

let me write my whole code and see if anyone else can at least point out the reason that it keeps returning x as 1.66666667 every time even though I have x set to increase.

```

// Directives:
#include <cmath>
#include <cstdlib>
#include <iostream>
#include <graphics.h>
using namespace std;

// Constants:

const int S = 500;
const int FPS = 30;

// Prototypes:
void ball(double x, double y, double d);

// --------------------------------------------------------------------------
// Main Function:
int main()
{
    double t = 0; // time in seconds
    double x = 0, y = S; // starting point for ball

    initwindow(S, S, "Extremelly Low Kinetic Energy Loss", 0, 0, true);

    while(x <= S)
    {
	// Calculations
	t+= 1.0/FPS;
	x ++;
	
	if(x > 0 && x < S/4)
	{
	    y = (-4*(pow(x,2)) + S/8) + S/2;
	}
	
	else if(x > S/4 && x < S/2) 
	{
	    y = (-4*(pow(x,2)) + (3*S/8)) + S/2;
	}
	
	else if(x > S/2 && x < 3*S/4)
	{
	    y = (-4*(pow(x,2)) + (5*S/8)) + S/2;
	}

	else if(x > 3*S/4 && x <= S)
        {
	    y = (-4*(pow(x,2)) + (7*S/8)) + S/2;
	}
	
	// Next Frame
	clearviewport();
	ball(x, y, S/50);
	
	// Swap Buffers and Delay
	swapbuffers();
	delay(1000/FPS);	


    }
    delay(5000);

    return EXIT_SUCCESS;

}
// -------------------------------------------------------------------------

// -------------------------------------------------------------------------
void ball(double x, double y, double d)
{
    circle(int (x), int (y), int (d));
}
// -------------------------------------------------------------------------


```

Also I apologize to those who know the incredibly obvious answer for my lack of knowledge. Transferring mathematical statements to something that can be processed by C++ seems to be a decent learning curve.

---

### Post by Vaphell on 2011-10-08
add a variable f to count frames
```
  int f = 0;
```
and below the if-else block
```
cout << "frame #" << f++ << " x=" << x << " y=" << y << endl;
```

run your program from terminal.
you will see that values change but y goes down from 300 to a very_low_negative_number very fast.

```
frame #0 x=1 y=308
frame #1 x=2 y=296
frame #2 x=3 y=276
frame #3 x=4 y=248
frame #4 x=5 y=212
frame #5 x=6 y=168
frame #6 x=7 y=116
frame #7 x=8 y=56
frame #8 x=9 y=-12
frame #9 x=10 y=-88
frame #10 x=11 y=-172
frame #11 x=12 y=-264
frame #12 x=13 y=-364
frame #13 x=14 y=-472
...
frame #147 x=148 y=-87179
frame #148 x=149 y=-88367
frame #149 x=150 y=-89563

```

---

### Post by TheBetrayer142 on 2011-10-08
Ah alright, I see that. It seems like I'm just not typing in the function correctly in the way that I want within each "if" statement.

I also noticed this visually when the ball just shot up the left side of the window.

Thanks, and I will try to write an accurate parabolic function for each "if" statement.

Any other tips on writing the actual line so that it displays the ball as if it's bouncing from left to right?

Thanks again!

---

### Post by Vaphell on 2011-10-08
how do you run your program? what one should do to get the graphics.h part? (i commented it out because i lack this header)
also what are the starting conditions? angle, velocity, starting point? constraints for x and y?

---

