---
title: "What Am I Doing Wrong With This CODE?"
date: 2011-03-22
forum: Programming Talk
---

### Post by KAISER91 on 2011-03-22
So basically I am attempting to compute the Moment of Inertia (I);

r = radius
I = Moment of Inertia 

I have defined them as follows;


float I,r;
const double PI = 3.1415926;

```
case 1: cout << "Enter the radius of the circle in meters: ";
		cin >> r;
		I = ((PI/8)-(8/9*PI))*("r ^ 4 = %lf\n", pow (r,4));
		cout << "Moment of Inertia = " << I << endl;
		break;
```

This is not the full code but the portion that I seem to be having trouble with. 

I think I have done the formula incorrectly. Here is the formula;

[IMG]http://oi56.tinypic.com/do8ad2.jpg[/IMG]


Any help will be appreciated.

---

### Post by surfer on 2011-03-22
im not an expert, but check what c++ does with 8/9. i figure it does integer division and returns 0.

if so, try: "8/9." ; notice the dot at the end. 9. will be treated as a float; and so will "8/9.".

---

### Post by PaulM1985 on 2011-03-22
I am not sure what you are looking to do here:

```

I = ((PI/8)-(8/9*PI))*("r ^ 4 = %lf\n", pow (r,4));

```

You seem to be combining floats, strings and some sort of print statement all in one line.  I think if you remove all the stuff related to a string, you might avoid the compiler error (which I am assuming is your problem) and it would compute I.  I don't know equations for inertia off the top of my head, so I don't know if the formula is correct.

Can you give a description of what is actually going wrong in future.  It would make it easier for people to help you.

Paul

---

### Post by KAISER91 on 2011-03-22
Well, Paul, the problem is I think I typed the formula incorrectly, which I included in my opening post;

[IMG]http://oi56.tinypic.com/do8ad2.jpg[/IMG]

^^^ That is the correct formula but I am having trouble translating that into the code for use.


If the radius of a circle is 5, the moment of inertia should be 68.5977.

Instead I keep getting this number 245.437


Thanks.

---

### Post by KAISER91 on 2011-03-22
I guess my main problem is I don't know how to type r^4 in code.

---

### Post by KAISER91 on 2011-03-22
> **surfer said:**
> im not an expert, but check what c++ does with 8/9. i figure it does integer division and returns 0.

if so, try: "8/9." ; notice the dot at the end. 9. will be treated as a float; and so will "8/9.".
Still the same problem. LOL

---

### Post by KAISER91 on 2011-03-22
Well, I seem to have solved the problem, the correct way to type the formula was;


> I = (( PI /8 ) - (8/(9 * PI))) * pow(r,4);


Thanks.

---

### Post by JupiterV2 on 2011-03-22
> **KAISER91 said:**
> I = (( PI /8 ) - (8/(9 * PI))) * pow(r,4); 

Unfortunately, this would still give you a rounding error.

```
float x = 1 / 2;
float y = 1.0 / 2.0;

x != y
```

(1 / 2) are integer values which are then cast to a float but the equation would be evaluated as an integer first.

Your equation should be:
```
double I = (( PI / 8.0) - (8.0/(9.0 * PI))) * pow(r,4.0); 
```

---

### Post by PaulM1985 on 2011-03-22
Thats what I was getting at.  Remove the string stuff, eg everything between " ".

Paul

---

### Post by Arndt on 2011-03-22
> **JupiterV2 said:**
> Unfortunately, this would still give you a rounding error.

```
float x = 1 / 2;
float y = 1.0 / 2.0;

x != y
```

(1 / 2) are integer values which are then cast to a float but the equation would be evaluated as an integer first.

Your equation should be:
```
double I = (( PI / 8.0) - (8.0/(9.0 * PI))) * pow(r,4.0); 
```

8/(9*PI) ought to be alright, since the divisor will be a floating point number. But it's certainly a good idea to just use floats everywhere - then truncation errors cannot occur.

And I'd like to point out that, although it is not likely to matter in this computation, PI to seven places is 3.1415927, not 3.1415926.

---

### Post by trent.josephsen on 2011-03-22
> **KAISER91 said:**
> Well, Paul, the problem is I think I typed the formula incorrectly, which I included in my opening post;

[IMG]http://oi56.tinypic.com/do8ad2.jpg[/IMG]

^^^ That is the correct formula but I am having trouble translating that into the code for use.


If the radius of a circle is 5, the moment of inertia should be 68.5977.

Instead I keep getting this number 245.437


Thanks.
Unless pi/8 - 8/(9pi) has units of mass per area, there's something very weird about that formula that piques my interest.

If you don't mind my asking, what kind of object are you finding the moment of inertia of, and about what axis?

---

