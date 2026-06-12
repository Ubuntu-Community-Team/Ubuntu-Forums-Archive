---
title: "[SOLVED] [C++] - warning: left-hand operand of comma has no effect"
date: 2008-07-06
forum: Programming Talk
---

### Post by HunterSBuntu on 2008-07-06
I've written the following function to calculate the greatest common divisor using recursion(yes, the cliche textbook example, haha):

```
int gcd_recursive(int m, int n)
{
	if (n == 0)   //Base case of recursion
	{
		return m;
	}
	else         //Keep calling the function
	{
		return(n, gcd_recursive(n, m % n));
	}
}
```

When I build the program that uses this function I get a warning saying "warning: left-hand operand of comma has no effect" for this line of code:

```
return(n, gcd_recursive(n, m % n));
```

What does this warning mean?  The program functions correctly as far as I can tell.  I've tried changing my parentheses around but it still comes up.

Thanks.

---

### Post by gnusci on 2008-07-06
It is very clear... look your function is declared as

[PHP]
int gcd_recursive(int m, int n)
{
	if (n == 0)   //Base case of recursion
	{
		return m;
	}
	else         //Keep calling the function
	{
		return(n, gcd_recursive(n, m % n));
	}
}[/PHP]

as you can see it can return only a **int** value, here I repeat the declaration

[PHP]int gcd_recursive(int m, int n)[/PHP]

and you can not return two as in the line

[PHP]return(n, gcd_recursive(n, m % n));[/PHP]

There is no way to return two values in this way.

pay attention that **return** can only return the type of data defined when the function is declare, for instance the following function:

[PHP]type function(foo){
   type r;
   return r;
}[/PHP]


can only return a data of type **type**.

---

### Post by HunterSBuntu on 2008-07-06
Silly me.  

Thanks. :)

---

### Post by cwj753357 on 2013-03-31
[COLOR=#000000]"Never make a calculation until you know the answer." -- Wheeler, Spacetime Physics, pg 60.[/COLOR]

[COLOR=#000000]Is this truth ?[/COLOR]

---

