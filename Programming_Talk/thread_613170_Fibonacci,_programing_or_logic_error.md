---
title: "Fibonacci, programing or logic error"
date: 2007-11-14
forum: Programming Talk
---

### Post by jpittack on 2007-11-14
Am I programming wrong or is my brain scattered (logic error)?

Output from any number other than zero gives a blank line.

---

### Post by Compyx on 2007-11-14
"On my honor as a student of the university of Nebraska at Omaha, I have neither given nore (sic) received unauthorized help on this homework assignment."

I'll give you a hint: learn to indent your code and don't ask us to do your homework.

---

### Post by jpittack on 2007-11-14
I am allowed to use the forums.  Unauthorized help is you giving me the code, not pointing out errors.

My instructor uses these forums.  I know he will see it.

---

### Post by iharrold on 2007-11-14
Your program does nothing with "number" that you pass into fibonnacci thus your in an infinite loop.

---

### Post by LaRoza on 2007-11-14
Logic error, use google to find snippets that work. Sorry, I wouldn't post here the answer.

---

### Post by jpittack on 2007-11-14
I have since revised the code.  I now get -1 everytime and zero returns zero.

---

### Post by CptPicard on 2007-11-14
It's trivial... your fibonacci-printing line is outside of the while block.

And don't use doubles. Fibonacci numbers are integers.

---

### Post by jpittack on 2007-11-14
I was told to use doubles.  It needs to handle the 96th number place.  Why does it matter that the printing line is outside the while block?  If I include it in the while statement, then if I put in zero I get no result.

---

### Post by CptPicard on 2007-11-14
Hmm. I thought that's what it was supposed to do, quitting with 0 and otherwise looping and asking for numbers to print.

What do you mean handling the 96th place? I'm not sure why you're told to use doubles, if I was giving the assignment I wouldn't, as they're floating-point numbers... you CAN use them, but it's ... sort of weird.

---

### Post by jpittack on 2007-11-14
Perhaps my code doesn't explain the assignment.  Put in a number.  This represents the place in the sequence.  0=0 1=1 2=2 3=3 4=5 5=8, etc.  I must handle the 0 place up to the 96th place.

---

### Post by iharrold on 2007-11-14
> **jpittack said:**
> Perhaps my code doesn't explain the assignment.  Put in a number.  This represents the place in the sequence.  0=0 1=1 2=2 3=3 4=5 5=8, etc.  I must handle the 0 place up to the 96th place.

Question for you... In C++ or C for that matter how do you check for equivalence of say if variable x is equivalent to variable z?  I.e. what is the syntax?

---

### Post by CptPicard on 2007-11-14
I'm not sure what your while loop does... isn't the fibonacci function the one that returns the nth place fibonacci number?

---

### Post by jpittack on 2007-11-14
If x == z
set x = z

---

### Post by iharrold on 2007-11-14
> **jpittack said:**
> If x == z
set x = z

Now look at your equivalence test in your code....

---

### Post by jpittack on 2007-11-14
The fibonacci function is to return the number that is in the place of the variable number which represents the place in the sequence.

So...I think you said it right.

---

### Post by CptPicard on 2007-11-14
Could you just post your code within some code tags here, would be easier to check out ;)

---

### Post by jpittack on 2007-11-14
Holy crap!  Some popcorn for iharold :popcorn:

How could that throw off my program that much?  Everything was just showing up as -1.

---

### Post by jpittack on 2007-11-14
I can't use the tags because, well, I don't know how to copy paste out of putty.

---

### Post by CptPicard on 2007-11-14
The difference between = and == is a rather typical source of bugs, especially because something like x = 1 still evaluates as true by virtue of assignment returning the value assigned and nonzero evaluating as true... so no wonder it throws off your code ;)

---

### Post by jpittack on 2007-11-14
Please excuse my stupidity.  I have been awake since 2:30 am and it is now 5:37 pm.  Since we are on the subject, do you know how to get text out of putty?

---

### Post by CptPicard on 2007-11-14
Hmm. How about painting the text by mouse and then pressing Control-C... or isn't that the copy command on Windows (too)?

---

### Post by jpittack on 2007-11-14
That doesn't work.  The computer I am connected to doesn't know what a mouse is.

I am trying to set the precsion of the output.  Here are my notes.  I am getting an eroor saying that setprescion is a variable.

> cout << setprecision (2) << fixed << showpoint;

empty paramter list

()
(void)

Default arugements

(something I can't read over here) (const double & const)

yah, i can't understand it either

---

