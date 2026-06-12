---
title: "Postfix converter question[C++]"
date: 2008-04-12
forum: Programming Talk
---

### Post by baumgc on 2008-04-12
I had a thread earlier with a different question relating to this question, but i figured everything out real easy.

Now I have hit a new roadblock.
I can't think of a way to add/subtract/multiply/divide more than two numbers and an operator.

Ex:
3 5 +
5 10.3 /
32.3 39 *
0.01 77 -

I just pop twice, then atof(first pop), atof(second pop), then have some nested if else statements like this:
[PHP]if (operator == "+")
{
	pushthis = second pop + first pop
	push(pushthis)
}	else if (operator == "-")
	{
		pushthis = second pop - firstpop
		push(pushthis)
	}
		//etc.
		//pseudocode of course[/PHP]

These I can handle. 
Once it starts doing stuff like the following:

2 3 4 + * 6 1 + 2 4 - 3 3 * + / *
11 1 2 * - 3 * 9 3 / / 1 12 14 -  + 1 + *

I can't think about how to go about this. I've thought about doing something like I did above, pushing the result, but I can't think about how to pop it back up and work with it again.

Last, I have no method of detecting malformed postfix expressions. Everything goes through and it makes some pretty hilarious outputs.

Anyway, appreciate the help. If you want my code and header, I'll put them up.

---

### Post by aks44 on 2008-04-12
Hint: what is the relation between infix and postfix notations (as far as the data structure goes)?
Also: recursion.

;)

---

### Post by WW on 2008-04-12
> **baumgc said:**
> I
Once it starts doing stuff like the following:

2 3 4 + * 6 1 + 2 4 - 3 3 * + / *
11 1 2 * - 3 * 9 3 / / 1 12 14 -  + 1 + *

I can't think about how to go about this.

What is it supposed to do with these inputs?  You call it a "converter".  Is it supposed to convert the input into something else?  Or is it a postfix calculator?  What is it supposed to output, and when is it supposed to output it?

---

### Post by dwhitney67 on 2008-04-12
It's real "simple"... use the stack as you have previously, however each time you encounter an operator, you need to pop two values off of the stack and perform the operation.  The result then needs to be placed back onto the stack.

So, if you have input (whether from the keyboard or file) of an operation like this:  5 4 + 6 7 * +

Your stack will look as the following:

```
5                 // insert first value
5 4               // insert second value
5 4 +             // got an operator (do not push onto the stack; just calculate)
9                 // pop two values from stack; perform calculation, push result back to stack
9 6 7 *           // continue adding to stack until next operator received
9 42              // perform operation, and place result on the stack
9 42 +            // look for the next operator
51                // perform calculation and place result on the stack
```

All done.. pop the last value off of the stack and you are done.  The answer is 51.

If you are done, and your stack has two or more numbers on the stack, but no more operators, then you have an error in the postfix equation.

P.S. Read the entire postfix equation from the keyboard or file in one swoop, then perform the calculation.

---

### Post by baumgc on 2008-04-13
Sorry. I should have clarified a bit more.

It converts a postfix equation to an infix then solves it and outputs everything, ex:

Postfix Entered:  4 5 +
Infix Converstion: (4 + 5)
Answer: 9

Thanks for the help.

---

### Post by WW on 2008-04-13
I was going to outline a possible solution in pseudo-code, but what I came up with was so close to a Python program that it only took a few tweaks of the pseudo-code to convert it into a working Python program. (In particular, the append() function acts like a push() function; the split() function splits a string into individual words).   Think of this as working pseudo-code that lets you see how your C++ program might be structured.

**postfix_demo.py**
[php]
#
# Demonstrate postfix to infix conversion, and postfix evaluation.
#
# The code doesn't check for errors!  For example, after finding an
# operator, the code should check that there are at least two items on
# the stack before trying to pop them.  At the end of the processing loop,
# it should check that only one item remains on the stack.
#
# The evaluation part of the code uses int(word) to convert the
# string word to an integer; change this to float(word) to allow floating
# point numbers.

str = "19 5 11 3 - + * 100 /"

#
# Do the conversion of the *formula* from postfix to infix.
# stack is a list of strings.
#
stack = []
for word in str.split():
    if word == '+':
        x = stack.pop()
        y = stack.pop()
        z = "(" + y + "+" + x + ")"
        stack.append(z)
    elif word == '-':
        x = stack.pop()
        y = stack.pop()
        z = "(" + y + "-" + x + ")"
        stack.append(z)
    elif word == '*':
        x = stack.pop()
        y = stack.pop()
        z = "(" + y + "*" + x + ")"
        stack.append(z)
    elif word == '/':
        x = stack.pop()
        y = stack.pop()
        z = "(" + y + "/" + x + ")"
        stack.append(z)
    else:
        stack.append(word)
final = stack.pop()
print "Postfix: ", str
print "Infix:   ", final

#
# Evaluate the *value* of the postfix formula.
# In this part, numstack is a list of numbers.
# (This part could be merged with the code above
# to do the whole thing in one loop; I have separated
# them for clarity.)
#
numstack = []
for word in str.split():
    if word == '+':
        x = numstack.pop()
        y = numstack.pop()
        z = y + x
        numstack.append(z)
    elif word == '-':
        x = numstack.pop()
        y = numstack.pop()
        z = y - x
        numstack.append(z)
    elif word == '*':
        x = numstack.pop()
        y = numstack.pop()
        z = y * x
        numstack.append(z)
    elif word == '/':
        x = numstack.pop()
        y = numstack.pop()
        z = y / x
        numstack.append(z)
    else:
        numstack.append(int(word))
final = numstack.pop()
print "Value:   ", final
[/php]

Sample run:
[php]
$ python postfix_demo.py 
Postfix:  19 5 11 3 - + * 100 /
Infix:    ((19*(5+(11-3)))/100)
Value:    2
$ 
[/php]

---

