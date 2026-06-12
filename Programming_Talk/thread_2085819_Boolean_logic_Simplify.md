---
title: "Boolean logic: Simplify"
date: 2012-11-19
forum: Programming Talk
---

### Post by Litost on 2012-11-19
I am completely stuck on this question and I'm turning to you very helpful people for some insight! 

This is the question:

> Simplify the following statements. Here, b is a variable of type boolean and n is a vari*
able of type int.
a.	if (n == 0) { b = true; } else { b = false; }
(Hint: What is the value of n==0?)


Now, I've taken numerous logic courses and am no stranger to true/false. Yet I am struggling to understand what they want me to do here and I don't find the hint very helpful. I've reviewed the chapter and cannot find anything helpful there either. How can a simple if statement be made simpler than if n = 0 b = true else b = false? There needs to be some sort of return whether it be true or false, and if there is no else statement would java not consider it an infinite loop? I am clearly missing something painfully obvious, please any insight is appreciated.

---

### Post by bouncingwilf on 2012-11-19
I see your problem, there is a lack clarity in the question however,

In C Bools are ints and ints can be Bools so I suspect the clue the've given where  the case n=0 is a case for reversing true/false i.e. 

 if(!n)
 {.......    
}
should work. 

Bouncingwilf

---

### Post by Abhinav Kumar on 2012-11-19
> **Litost said:**
> I am completely stuck on this question and I'm turning to you very helpful people for some insight! 

This is the question:



Now, I've taken numerous logic courses and am no stranger to true/false. Yet I am struggling to understand what they want me to do here and I don't find the hint very helpful. I've reviewed the chapter and cannot find anything helpful there either. How can a simple if statement be made simpler than if n = 0 b = true else b = false? There needs to be some sort of return whether it be true or false, and if there is no else statement would java not consider it an infinite loop? I am clearly missing something painfully obvious, please any insight is appreciated.
Hi ,

The general logic for if and else statement is 
```

if(expression)
{
 //Executed when expression is true
}
else
{
 //Executed when expression is true
}

```In your case,  the expression to be evaluated is n==0 ( double equality sign is used for comparing, while single equality sign is used for assignment) ie the compiler will see it like
```

if (n is zero is true) // this statement is true when n is zero
{ 
   assign b as true
}
else
{
  assign b as false
}

```

Note that sometimes you only need if. In that case, no else is needed. Compiler then just checks if that statement is true. 
```

if(expression)
{
//Executed when expression is true. 
//Compiler now doesn't do anything if expression is false
}

```Note that if-else or only if are executed only once by the compiler.   They are just the decision constructs. Infinite loops take place when  compiler goes on executing a single statement again and again and can't  come out of the loop.

Regards,
Abhinav

---

### Post by spjackson on 2012-11-19
I think the question is looking for something of the form:
```

b = expression;

```
and I'll leave you to figure out what the expression should be. (The hint is a hint!)

---

### Post by Litost on 2012-11-19
#-o Thanks for not making me feel more stupid than I do already upon realizing the solution.

---

### Post by SledgeHammer_999 on 2012-11-19
For those that still don't get it the solution is:
[php]b = !n;[/php]

Also another interesting solution would be:
[php]b = (n==0) ? true : false; [/php]

EDIT: I assumed that the language is C or C++

---

### Post by trent.josephsen on 2012-11-19
"b = !n" will work in C, but OP didn't specify a language. I'm guessing Java because of "boolean" but it is pretty ambiguous. "b = (n == 0)" (parentheses optional) is probably the "correct" answer.

---

### Post by bouncingwilf on 2012-11-19
> **trent.josephsen said:**
> "b = !n" will work in C, but OP didn't specify a language. I'm guessing Java because of "boolean" but it is pretty ambiguous. "b = (n == 0)" (parentheses optional) is probably the "correct" answer.

Oops! my bad - I naturally assumed C and as the OP wanted the statements "simplified" just used !n - As a former chemist who used to dabble in the other OP's , we used to operate by the motto "minimize assumptions - live longer! " I should follow my own advice!


Bouncingwilf

---

### Post by kevinharper on 2012-11-19
I assumed java b/c the last sentence of the original post makes a reference to the language.

SledgeHammer_999's second code example is what I would have though to answer.

To answer your other questions:

> There needs to be some sort of return whether it be true or false
No. return statements are used to exit functions and return to wherever the current function was called.

> if there is no else statement would java not consider it an infinite loop?
Not Java, nor any other language. An if statement's block of code includes code that is only executed if the the expression (comparison) evaluates to true.

Let's say you own a bar and you program a robot to let people in depending on their age. When someone 21 or older swipes his/her ID, the person is allowed to go in:
```
if ( age >= 21 ){
    //code that allows person into bar
}
```

The code doesn't care at all about anyone under 21 years of age.

Now, let's say that you want the robot to call the police on anyone who is younger than 21. This is when you would add the else portion:
```
if ( age >= 21 ){
    //code that allows person into bar
}
else {
    //code that calls police b/c person is under 21
}
```

---

### Post by SledgeHammer_999 on 2012-11-20
Oops I didn't read it carefully. I assumed that the language was C or C++.

---

### Post by trent.josephsen on 2012-11-20
And the Reading Comprehension award goes to... kevinharper!

---

### Post by kevinharper on 2012-11-22
So does the one for one of the lamest examples ever.

---

### Post by lisati on 2012-11-22
Thread, which has already been marked "solved", closed before things get too silly.

---

