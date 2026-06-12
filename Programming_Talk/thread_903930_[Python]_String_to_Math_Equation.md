---
title: "[Python] String to Math Equation"
date: 2008-08-28
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-28
Hello,

I was wondering if there was a simple way to turn the text (as an example):
**(1+2)/3+4**
into that exact representation in python. (the output would be **5**

then there could be something more advanced:
**(1+2+3!)/3+sqrt(4)**
that would do the same thing and return the answer **5**

I start thinking about it logically but then get confuesd when i come into contact with a set of brackets.

Thanks
~Cody Woolaver

---

### Post by shifty2 on 2008-08-28
```

>> a = input("enter your sum: ")
enter your sum: 1 + 2
>> a
3

```

To do functions that aren't built into python it would require some more work, but shouldn't be too hard - you would just have to make a factorial() or sqrt() function and the user could then enter: 1 + sqrt(factorial(6)) or similar

EDIT:
Obviously sqrt is built in (4**0.5)...but to get it in the format he wants would require the creation of a sqrt() function.

---

### Post by Alasdair on 2008-08-28
Assuming you have a function that can evaluate a mathematical expression without brackets, all you need to do when you encounter them is to recursively call your expression parser function on the contents of the brackets.

---

### Post by generalguy on 2008-08-28
[PHP]

>>>eval ("(1+2)/3+4")
 5
[/PHP]

eval works for strings that are valid python only. If you want your own new operators, like factorial and stuff with different bindings, you'll need to write a parser. Look into BNF, yacc/lex if you want to get fancy. ANTLR is also very good (and can output python).

---

### Post by kjohansen on 2008-08-28
I did something like this once in C#.

What I did to handle brackets was to find the last open bracket (when reading from left to right) then find its closing match.  I broke out the expression inbetween the brackets and replaced it with its evaluation.  So 10*(3+5) would become 10*8.  Call this until all brackets are replaced and then evaluating the new expression should be straight forawrd.

---

### Post by cbdonohue on 2008-08-28
A popular algorithm to solve this problem is to use a stack.  As you go through the expression, every time you come across an operand, push it to the stack.  When you come to an operator you evaluate it with the top two elements of the stack and push the result back on.  You will have one item left in the stack at the end...which is your answer.  This would only work with binary operators tho.

---

### Post by Erdaron on 2008-08-28
Would [SymPy]("http://code.google.com/p/sympy/") do what you need? It's a symbolic algebra system for Python.

---

### Post by ssam on 2008-08-29
use eval().

in some programs you may want to take precautions to limit what the user can put in the string. 
[http://lybniz2.sourceforge.net/safeeval.html](http://lybniz2.sourceforge.net/safeeval.html)

---

