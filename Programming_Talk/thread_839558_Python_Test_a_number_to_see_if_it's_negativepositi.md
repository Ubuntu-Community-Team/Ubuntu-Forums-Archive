---
title: "Python: Test a number to see if it's negative/positive"
date: 2008-06-24
forum: Programming Talk
---

### Post by secondstage on 2008-06-24
Is there a way in Python to test a number to see if it's negative or positive? What I'm trying to do it make it change x = 3 into x-3 = 0, or 
x = .25 to 4x = 0. Any other ideas on how to to this, would be greatly appreciated:

---

### Post by suprfish on 2008-06-24
hint: less than, greater than

---

### Post by secondstage on 2008-06-24
My bad for not think of that, I'm just really out of it today. #-o

---

### Post by secondstage on 2008-06-24
And how is zero negative?

---

### Post by WW on 2008-06-24
> 
What I'm trying to do it make it change x = 3 into x-3 = 0, or
x = .25 to 4x = 0.

Sorry, I still don't understand what you are trying to do.

Do you need something more complicated than this?
```

if x > 0:
    print "x is positive"
elif x < 0:
    print "x is negative"
else:
    print "x is zero"

```

---

### Post by geirha on 2008-06-24
> **secondstage said:**
> And how is zero negative?

It may be if you are using floats. Floats are not exact. [http://docs.python.org/tut/node16.html](http://docs.python.org/tut/node16.html)

---

### Post by secondstage on 2008-06-24
@WW: What I'm actually trying to do is write a program to find the factors of a quadratic equation, using the quadratic formula, which looks like (-(b)[plus or minus](math.sqrt((b**2)-(4*a*c))))/(2*a). I know, I used alot of parenthesis, but that is beside the point. When you plug-in 1 for a, 2 for b, and 1 for c, which is the equavilent of saying 1x^2 + 2x + 1, the program finds the Xs (-1, and -1). Now I need to convert that to x+1=0. Because when you convert that, you get x+1, and x+1. And when those are multiplied together, you get 1x^2 + 2x + 1. So for another situation, the Xs are (0.5 and -1). The computer needs to find out how what to do with these Xs (with the help of ifs and elses).

All of this work is so that I have a program to my math homework for me. All I would have to do is plug-in a, b, and c. If you want to see what I have already done, I'll be putting an attachment up of the program.

> x = .25 to 4x = 0
is supposed to be 'to 4x-1 = 0'.

---

### Post by secondstage on 2008-06-24
Here's the attachment.

---

### Post by slavik on 2008-06-24
for something that specific, prolog is a better tool, since this is more of a constraint programming problem.

---

### Post by Can+~ on 2008-06-24
> **secondstage said:**
> @WW: What I'm actually trying to do is write a program to find the factors of a quadratic equation, using the quadratic formula, which looks like (-(b)[plus or minus](math.sqrt((b**2)-(4*a*c))))/(2*a). I know, I used alot of parenthesis, but that is beside the point. When you plug-in 1 for a, 2 for b, and 1 for c, which is the equavilent of saying 1x^2 + 2x + 1, the program finds the Xs (-1, and -1). Now I need to convert that to x+1=0. Because when you convert that, you get x+1, and x+1. And when those are multiplied together, you get 1x^2 + 2x + 1. So for another situation, the Xs are (0.5 and -1). The computer needs to find out how what to do with these Xs (with the help of ifs and elses).

All of this work is so that I have a program to my math homework for me. All I would have to do is plug-in a, b, and c. If you want to see what I have already done, I'll be putting an attachment up of the program.


is supposed to be 'to 4x-1 = 0'.

Very unclear your explanation. You're using the general formula for quadratics:

[IMG]http://upload.wikimedia.org/math/3/e/a/3ea647783b5121989cd87ca3bb558916.png[/IMG]

Get the +x and -x if the root is not complex, and insert those numbers in the original equation to get the coordinates?

You could have your homework done by now...

---

### Post by secondstage on 2008-06-27
The goal of this is to be able to understand how to write a program for this, so that I can write it in BASIC, so that it can be transferred onto the calculator. And finally, so I won;t have to plug it in myself. Try to sae time, and annoy teachers.

---

