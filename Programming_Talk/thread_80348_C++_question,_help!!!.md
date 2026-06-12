---
title: "C++ question, help!!!"
date: 2005-10-22
forum: Programming Talk
---

### Post by dcarpenter on 2005-10-22
Hi guys.

I am taking a c++ class in college and one of my assignments is as follows:

create a program which gathers a user inputted number and multiplies the number by 1001 using only nested loops (for or while). 

Yes i know this is rediculous but we have to do it so I am here asking you guys what I am doing wrong!

my code thus far is as follows:

```
#include <iostream>
using namespace std;

int main()
{
    double n, t;
    int i, j, k;

    cout << "Input a number: ";
    cin >> n;

    for (i = 1; i <= 13; i++)
    {   
        for (j = 1; j <= 11; j++)
        {
            for (k = 1; k <= 7; k++)
            {
                t = n + t;
            }
        }
    }   
    cout << t << endl;
    return 0;
}
```

I am trying to get the number "n" to add in to its self 1001 times and I can't see what I am doing wrong.  

the program compiles fine but when I input a number, the output is always:
-7.40945e+304

Any advice or solutions would be greatly appreciated!

---

### Post by toojays on 2005-10-22
What is the value of t before you enter the loop?


:)

---

### Post by Stereotypical Rage on 2005-10-22
Double data types have a max value of: 	1.7E +/- 308 (15 digits)
t= n(i*j*k);

I think I could be wrong. Might even have to: t=n(i*j*k)+n;

I'm not sure though.

---

### Post by dcarpenter on 2005-10-22
Toojays:  I dont think I am following what you are trying to say.  

Should T have a value before entering the loop or is t defined by the loop?

---

### Post by heimo on 2005-10-22
[quote=dcarpenter]
Should T have a value before entering the loop or is t defined by the loop?[/quote]

Let me use my mad vorlon c++ skills to answer this question: Yes.

;) Seriously: Always initialize your variables.

---

### Post by dcarpenter on 2005-10-22
as you can see, i am very new to c++ lol.  

i thought declaring T as a double was initializing it?  if I am wrong, then what should t be = to then?

---

### Post by toojays on 2005-10-22
You should give t a value before you enter the loop. Otherwise, the first time you do "t = n + t", you can't be sure of what you're going to get.

I tried this one on my machine, because I thought that gcc should issue a warning about it. Interestingly I found that gcc will only warn about uninitialised variables if optimisation is turned on (this is documented in the gcc manual).

I suggest you compile your programs with the options "-W -Wall -O", so that gcc can help you find errors and stylistic issues in your code.

---

### Post by dcarpenter on 2005-10-22
i am actually ssh'ed into my schools server and using the g++ command to compile my programs on there.  

good news tho!  I got it to work, i think lol

double t = i * j * k;

and the program output the right numbers!

edit:  however im not sure if this is allowed within the assignment?   

heres the actual instructions:
   Do the following problem: &#8220;Assembly languages for some microprocessors do not
have a multiply operation. While there are sophisticated algorithms for performing
multiplication in such cases, a simple method multiplies by repeated addition. Using this
information write a C++ program that multiplies a user- input value by 1001 using a nest
of three loops and then displays the result. You may use either while or for loops for
your implementation." (Hint 1001 = 7 * 11 * 13)

---

### Post by dcarpenter on 2005-10-22
heres what worked:

```
#include <iostream>
using namespace std;

int main()
{
    int i, j, k;
    double n;
    double t = i * j * k;

    cout << "Input a number: ";
    cin >> n;

    for (i = 1; i <= 13; i++)
    {   
        for (j = 1; j <= 11; j++)
        {
            for (k = 1; k <= 7; k++)
            {
                t = n + t;
            }
        }
    }   
    cout << t << endl;
    return 0;
}
```

---

### Post by heimo on 2005-10-22
I'm not fully awake yet, but I was thinking something like t=0; Those i, j, k get their initial values at those for loops, you're using t to count user input 1001 times and I believe it should be set to 0 at the beginning.

---

### Post by toojays on 2005-10-22
You can pass those warning options I mentioned to g++ as well. That would've caught both the incorrect solutions you've posted.

---

### Post by dcarpenter on 2005-10-22
hehe, yes.. 0 works wonderfuly as well.  After realizing i*j*k was now how i should be doing it i tried t = 1; and this gave me correct numbers except for the fact that they were 1 higher than they should be.  So i tried t = 0; and it worked like a charm.

thanks to all you guys for helping me out!  I just needed a little nudge in the right direction. 
:)

---

### Post by thumper on 2005-10-22
Not sure if you really want petantic picky comments, but I figure best to get people off on the right foot early.

Declare your variables as close to first use as possible.  For your loop counters that means declaring them in the loop.  Also it is more a C++ idiom to use loops from zero, so...

```
for (i = 1; i <= 13; i++)
```
becomes
```
for (int i = 0; i < 13; ++i)
```
The prefix ++ operator is used to follow the "say what you mean" style thingy.

That's the main point.  Also the compiler flags **-ansi** and **-pedantic** can be good too.

---

