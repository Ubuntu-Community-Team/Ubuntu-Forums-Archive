---
title: "Python: Adding decimals produces error"
date: 2008-05-29
forum: Programming Talk
---

### Post by Nexusx6 on 2008-05-29
Oh man, I feel stupid for actually having to make a post over this x_x

I'm trying to get python to do simple addition for a script I'm writing. 
Here's the gist of the problem::
```
>>> 5+4.99
9.9900000000000002
```
Were the heck are those trailing zero's coming from, with that last 2?! Even with 5.00+4.99 this happens.

_**The longer, but not necessarily required version-**_
I'm writing a tax program for work so that all I need to do is put the employee's name, and how many hours they worked, and the script can figure out all the other taxes for me and all I need to do is pen it to a check stub. Federal and State taxes work on a piecewise functions ie.
> Tax=$5 if{$100< paycheck <$105}
Tax=$6 if{$105< paycheck <$110}
etc... 

So to handle this, this is the code I wrote. Keep in mind, I'm still a pretty amateurish coder, so if the code looks atrocious, my apologies :oops:  
This snipit builds the lists up to 500 dollars. 
```
class Taxbracket(object):
    def __init__(self, a=0, b=None, count=100, taxbracketA=[0], taxbracketB=[]):
        print "test"
        self.taxbracketA = taxbracketA
        self.taxbracketB = taxbracketB        
        while count != 0:
           a += 5.00
           b = a + 4.99
           self.taxbracketA.append(a)
           self.taxbracketB.append(b)
           count -= 1
```
Later I'm going to make a function to try taxbracketA<paycheck<taxbracketB until the statement is true and return a tax value, but I can't do that until I don't have these weird decimals coming up. I just want taxbracktB to always be exactly $4.99 more than taxbracketB

Thanks for the help :x

---

### Post by pointone on 2008-05-29
[http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

---

### Post by Nexusx6 on 2008-05-29
> **pointone said:**
> [http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

Seriously... *Python can't add decimal places?* Not even 5+4.99 to get 9.99? There's no way to build a taxbracketB to the accuracy I need??

---

### Post by lisati on 2008-05-29
> **pointone said:**
> [http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

+1: 

The extra stuff is due to what's called a "rounding error" - with floating point arithmetic there's no guarantee that the way number is stored will be exact.

---

### Post by lisati on 2008-05-29
> **Nexusx6 said:**
> Seriously... *Python can't add decimal places?* Not even 5+4.99 to get 9.99? There's no way to build a taxbracketB to the accuracy I need??

One way, which will need a little extra programming effort, might be to hold the whole-number portion and the fraction portion separately - if the range of possible values is sufficiently small an regular integer variable for each will suffice. For more ambitious arithmetic an integer array might work.

I'm not a Python programmer so I don't know how to implement it in Python....

---

### Post by pmasiar on 2008-05-29
> **Nexusx6 said:**
> Seriously... *Python can't add decimal places?* Not even 5+4.99 to get 9.99? There's no way to build a taxbracketB to the accuracy I need??

Excuse me? It is not problem of Python, but you not understanding the concept of variable type. Try doing anything in Java, C or C++, to see how much stuff is dome for you.

Summary: you used float. Use [http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html) instead.

Python was designed for scientists. If defaults do not satisfy you, it's not problem of defaults, but not learning enough.

---

### Post by Nexusx6 on 2008-05-29
I just realized that the paycheck value which is just Wage*hours worked will almost never produce values with more than 2 decimal places thankfully, so this ugly problem shouldn't effect me right now.

For future reference, is there some way to tell python to round anything past a certain number of decimals up or down?

> One way, which will need a little extra programming effort, might be to hold the whole-number portion and the fraction portion separately - if the range of possible values is sufficiently small an regular integer variable for each will suffice. For more ambitious arithmetic an integer array might work.

I'm not a Python programmer so I don't know how to implement it in Python.... 

Hmm..I think I know what you're saying, but I don't know how to implement it either :-k

---

### Post by Tuna-Fish on 2008-05-29
Short answer is that using floats to count money is terminally stupid.

Long answer is to use integers, and set "1" to be the smallest sensible value, usually one cent (or one hundredth of a cent, whatever), and just remember this convention when taking values in and when printing values.

Python has a long() type, that can hold an arbitrarily long integer, and normal integers get silently cast into it when needed, so you don't have to worry about running out of space.

---

### Post by LaRoza on 2008-05-29
> **Tuna-Fish said:**
> 
Long answer is to use integers, and set "1" to be the smallest sensible value, usually one cent (or one hundredth of a cent, whatever), and just remember this convention when taking values in and when printing values.

Or this as stated above: [http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html)

---

### Post by Nexusx6 on 2008-05-29
> **pmasiar said:**
> Excuse me? It is not problem of Python, but you not understanding the concept of variable type. Try doing anything in Java, C or C++, to see how much stuff is dome for you.

Summary: you used float. Use [http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html) instead.

Python was designed for scientists. If defaults do not satisfy you, it's not problem of defaults, but not learning enough.

Which is why I was so shocked. I couldn't honestly believe that Python would have such a glaring problem going un-fixed for as old as Python is.

That being said, Decimal fixes everything, thanks for the solution.

---

### Post by LaRoza on 2008-05-29
> **Nexusx6 said:**
> Which is why I was so shocked. I couldn't honestly believe that Python would have such a glaring problem going un-fixed for as old as Python is.


It has nothing to do with Python. It isn't a problem; it is reality that every language faces.

---

### Post by geirha on 2008-05-30
What lisati means is that instead of using for instance 4.99$ as float, you use 499¢ as int when calculating. Then, whenever you need to print one of the ammounts or anything, convert it to a float and divide by 100.
```

taxbracketA= [x*500 for x in range(100)]
taxbracketB= [x+499 for x in taxbracketA]
print '%6.2f' % (taxbracketB[-1]/100.0, )

```

---

### Post by days_of_ruin on 2008-05-30
```
a = 5+4.99
print a
```
That prints 9.99.Wheres the problem?

---

### Post by WW on 2008-05-30
> **days_of_ruin said:**
> ```
a = 5+4.99
print a
```
That prints 9.99.Wheres the problem?

Take a look at the [Programming Challenge 10](http://ubuntuforums.org/showthread.php?p=4891535) thread for more examples and discussion.

---

### Post by days_of_ruin on 2008-05-30
> **WW said:**
> Take a look at the [Programming Challenge 10](http://ubuntuforums.org/showthread.php?p=4891535) thread for more examples and discussion.
IIRC that has nothing to do with floats.Its pythons internal code.

---

### Post by geirha on 2008-05-30
> **days_of_ruin said:**
> IIRC that has nothing to do with floats.Its pythons internal code.

You get the same result in c:
```

$ echo 'main(){ printf("%.20f\n", .1+.2); }' | gcc -x c - 2>/dev/null && ./a.out
0.30000000000000004441
$ python -c 'print "%.20f" % (.1+.2, )'
0.30000000000000004441

```

---

### Post by days_of_ruin on 2008-05-30
> **geirha said:**
> You get the same result in c:
```

$ echo 'main(){ printf("%.20f\n", .1+.2); }' | gcc -x c - 2>/dev/null && ./a.out
0.30000000000000004441
$ python -c 'print "%.20f" % (.1+.2, )'
0.30000000000000004441

```
Python is written in C so that probably has something to do with it.

Regardless it doesn't seem to have any effect on computation
```
>>>a = 4+5.99
>>>a
9.9900000000000002
>>>a * 2
19.98
>>>if not a > 9.99:
...    print "True"
...
True

```

---

### Post by WW on 2008-05-30
> **days_of_ruin said:**
> 
Regardless it doesn't seem to have any effect on computation

It can have an effect if you don't handle floating point numbers correctly.  For example, you would expect 0.1+0.2 to be equal to 0.3, but...
```

>>> a = 0.1+0.2
>>> a == 0.3
False
>>> 

```

---

### Post by days_of_ruin on 2008-05-30
> **WW said:**
> It can have an effect if you don't handle floating point numbers correctly.  For example, you would expect 0.1+0.2 to be equal to 0.3, but...
```

>>> a = 0.1+0.2
>>> a == 0.3
False
>>> 

```
Wierd.I stand corrected.:lolflag:

---

### Post by kragen on 2008-05-30
> **pointone said:**
> [http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems](http://en.wikipedia.org/wiki/Floating_point#Accuracy_problems)

Unless there is something I'm missing, this isn't a rounding error. A rounding error is when you try to enter or computer a number which has too many decimal places to store it with 100% accuracy.

This on the other hand is something different, because as far as I'm aware both '5', '4.99' and '9.99' can be represented with 100% accuracy in a float. 
What gives?

When I first saw this I was surprised but it didn't bother me that much, but the more I think about it the more I cant understand why this error occurs, or why people would bother to use floats with such a fundamental flaw!

Surely the C/Python implementation of float doesn't meet the standard?
[http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)

(Please someone explain!)

---

### Post by pmasiar on 2008-05-30
In mathematics, numbers form continuum. Computers have limited memory and register size, so all calculations are approximated. It is trivial to write a program to calculate smallest number epsilon which, when added to 1, makes 1. Do it. It is programming (practical, engineering task), not theoretical math problem. But for science inaccuracy does not matter, because all values measured in real world are approximate, too. You always need to know what is your measurement tolerance error, and it is always >0.

It always helps to use proper tool (and in this case, proper data type). Dynamic typing does not absolve programmer from thinking and understanding.

---

### Post by geirha on 2008-05-30
This one covers it fairly well I think:

[http://www.cprogramming.com/tutorial/floating_point/understanding_floating_point.html](http://www.cprogramming.com/tutorial/floating_point/understanding_floating_point.html)

---

### Post by Can+~ on 2008-05-30
> **Nexusx6 said:**
> Which is why I was so shocked. I couldn't honestly believe that Python would have such a glaring problem going un-fixed for as old as Python is.
[PHP]
/*C source file*/

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
	float num1=0.1, num2=0.2;
	
	printf("%.20f", num1+num2);
	return 0;
}[/PHP]

Answer:
```
0.30000000447034835815
```


A better solution for your problem, would be to create a class that holds (or function that returns) an integer for the money, and take the last to digits as the cents:

123456789 = $1,234,567.89

A nice approach would be to use inheritance from the [FONT="Courier New"]int[/FONT] class, and override the printing functions so it prints nicely formatted value/100.value%100; also making sure that a sum with a float returns it as the type of your new class.

---

### Post by Bichromat on 2008-05-31
> **kragen said:**
> Unless there is something I'm missing, this isn't a rounding error. A rounding error is when you try to enter or computer a number which has too many decimal places to store it with 100% accuracy.

This on the other hand is something different, because as far as I'm aware both '5', '4.99' and '9.99' can be represented with 100% accuracy in a float. 
What gives?

It is a rounding error, in *binary*. Because in *binary* 0.1 has an infinite expansion, just like 1/3 in decimal. You can only store a finite amount of digits: 52 bits in double precision, which is equivalent to approx. 16 decimal digits.
That's why you should never, in any language, test the equality of 2 floats, but instead should verify that abs(a-b)<epsilon.

> **kragen said:**
> When I first saw this I was surprised but it didn't bother me that much, but the more I think about it the more I cant understand why this error occurs, or why people would bother to use floats with such a fundamental flaw!

Surely the C/Python implementation of float doesn't meet the standard?
[http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)

(Please someone explain!)

This is a "problem" with the standard, not a language. It was designed to be efficient and "good enough" for a lot of people. If you want arbitrary precision, you need to use GMP, or the Decimal module in Python for example. But keep in mind that it will be slow!

---

### Post by slavik on 2008-05-31
> **Bichromat said:**
> It is a rounding error, in *binary*. Because in *binary* 0.1 has an infinite expansion, just like 1/3 in decimal. You can only store a finite amount of digits: 52 bits in double precision, which is equivalent to approx. 16 decimal digits.
That's why you should never, in any language, test the equality of 2 floats, but instead should verify that abs(a-b)<epsilon.



This is a "problem" with the standard, not a language. It was designed to be efficient and "good enough" for a lot of people. If you want arbitrary precision, you need to use GMP, or the Decimal module in Python for example. But keep in mind that it will be slow!
or Haskell :)

---

### Post by Bichromat on 2008-05-31
I've just checked Haskell. You're talking about rationals ? Lisp has them too ;)

---

### Post by kragen on 2008-05-31
> **Bichromat said:**
> It is a rounding error, in *binary*. Because in *binary* 0.1 has an infinite expansion, just like 1/3 in decimal. You can only store a finite amount of digits: 52 bits in double precision, which is equivalent to approx. 16 decimal digits.
That's why you should never, in any language, test the equality of 2 floats, but instead should verify that abs(a-b)<epsilon.

Thanks, that does explain it.
I didn't read the article properly and assumed that the exponent was normalised before it was converted to base 2.

How does addition work with floats anyway? I cant find any information on the standards for addition subtraction or multiplication.

---

