---
title: "Using math expressions in C"
date: 2013-11-25
forum: Programming Talk
---

### Post by achuthpnr on 2013-11-25
I am wondering which is the preffered way of programming in C, if one is using the same math expressions very often
1. Use the math function/expression each time
2. Precalculate the expression and store it to a variable and use the variable instead

My questions are:
1. Will there be any difference in the execution time?
2. When a call is made to a variable to which the expression is stored, is it actually calculating the expression or just retrieving the value of that expression?

I hope the questions are clear. 

Thanks.

---

### Post by Bachstelze on 2013-11-25
The answers to your questions depend on the compiler used, and probably also the optimisation settings. Storing the result in a variable seems to be the best way to ensure the best performance, but it might hurt readability, especially if you name your variables poorly. Personally I would do it only if performance is critical, and even then only if it does indeed make a difference on the compiler used.

---

### Post by w.w.milner on 2013-11-25
Answers to your questions
1. Yes
2. Just retrieving the value.

If you evaluate teh same expression often, you should make it a function ie
x= some expression;
y= some expression;
z = some expression;
the someexpression should be a function:
double f(double a, double b)
{
..
return result;
}
Since then you can
1. Do less typing
2. Test easier
3. Implement in a better way with little change.
For more effciency, uses memoization. You need to Google that. Basically whne you caluculate teh function, you store teh result as well. On a future call you look it up, not repeat teh calculation.

---

