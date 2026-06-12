---
title: "Mathematics Problem"
date: 2009-04-20
forum: Programming Talk
---

### Post by dudude on 2009-04-20
I have a question about general mathematics that I can't seem to find an answer to through searches on Google.

My question is how to solve equations where one of the variables is known to be an integer, but the value of the variable is unknown.

An example of this is:

x^2 + y = 17

where x is an integer and y is completely unknown.

I know that this can be accomplished on my ti-89 graphing calculator by saying "x = @1" which means that x is a multiple of 1.

What I would like to know is how to find solutions to those equations either by hand or through programming, efficiently.


Oh, and sorry if I should have posted this in a different part of the forum.

---

### Post by sekinto on 2009-04-20
> **dudude said:**
> I have a question about general mathematics that I can't seem to find an answer to through searches on Google.

My question is how to solve equations where one of the variables is known to be an integer, but the value of the variable is unknown.

An example of this is:

x^2 + y = 17

where x is an integer and y is completely unknown.

I know that this can be accomplished on my ti-89 graphing calculator by saying "x = @1" which means that x is a multiple of 1.

What I would like to know is how to find solutions to those equations either by hand or through programming, efficiently.


Oh, and sorry if I should have posted this in a different part of the forum.

Move x^2 to the other side:
y = 17 - x^2
Insert value for x (ex. 5):
y = 17 - 5^2
Solve:
y = 17 - 25
y = -8

If you wanted to do it in Python for a range of numbers you could do something like:
```
for x in range(1,11):
    print 'When x is ' + str(x) + ' y is ' + str(-(x**2) + 17)
```
Which would return:
```
When x is 1 y is 16
When x is 2 y is 13
When x is 3 y is 8
When x is 4 y is 1
When x is 5 y is -8
When x is 6 y is -19
When x is 7 y is -32
When x is 8 y is -47
When x is 9 y is -64
When x is 10 y is -83
```
You could also do it for a set of values like:
```
for x in [-4,2,11]:
    print 'When x is ' + str(x) + ' y is ' + str(17 - x**2)
```
Which would return:
```
When x is -4 y is 1
When x is 2 y is 13
When x is 11 y is -104
```


I just used the "When x" format as an example, you could really format the output any way you wanted. If you wanted a nice table you could do something like:
```
print 'x\t|  y\n-----------------'
for x in [1,2,5,11,42]:
    print str(x) + '\t|  ' + str(17 - x**2)
```
Which would return:
```
x	|  y
-----------------
1	|  16
2	|  13
5	|  -8
11	|  -104
42	|  -1747

```

---

### Post by lvleph on 2009-04-20
I can't think of any particular way to solve it except through reason. You will end up with a set of solutions. 
{y = 17 - 2n^2: n = 0, 1, ...}
Sorry if that is not much help.

---

### Post by lisati on 2009-04-20
> **lvleph said:**
> I can't think of any particular way to solve it except through reason. You will end up with a set of solutions. 
{y = 17 - 2n^2: n = 0, 1, ...}
Sorry if that is not much help.

Ah! Edited! I was about to comment on something that has been edited out.

---

### Post by lvleph on 2009-04-20
Yeah, I have been drinking. I am a mathematician which makes it really sad that I said that.

---

### Post by dudude on 2009-04-21
Thanks sekinto, that was exactly what I was looking for.

---

### Post by Arndt on 2009-04-21
> **dudude said:**
> I have a question about general mathematics that I can't seem to find an answer to through searches on Google.

My question is how to solve equations where one of the variables is known to be an integer, but the value of the variable is unknown.


Equations where all the unknowns are required to be integers are generally called "diophantine". This may help your searching. There is no general way to solve completely arbitrary diophantine equations, but of course special cases have known algorithms.

Searching for "integer programming" may also turn up something useful.

---

### Post by s.fox on 2009-04-21
> **Arndt said:**
> Searching for "integer programming" may also turn up something useful.

I agree with integer programming as the way forward.  This could be solved by using linear programming.  Unfortunately I have not been able to get any applications that solve linear programming problems working under Ubuntu :(

In Microsoft Windows I can use an program called The Management Scientist  to solve these types of problems.

-Ash R

---

### Post by ajackson on 2009-04-21
There is an application called Maxima that is in the Ubuntu reps, that should be able to solve problems like this.

---

### Post by JDahl on 2009-04-21
> **Ash R said:**
> I agree with integer programming as the way forward.  This could be solved by using linear programming.  Unfortunately I have not been able to get any applications that solve linear programming problems working under Ubuntu :(

In Microsoft Windows I can use an program called The Management Scientist  to solve these types of problems.

-Ash R

For general convex optimization, you can use the Python package 
CVXOPT (python-cvxopt in apt).
[http://abel.ee.ucla.edu/cvxopt](http://abel.ee.ucla.edu/cvxopt)

For integer linear programming, CVXOPT includes wrappers for GLPK.

---

