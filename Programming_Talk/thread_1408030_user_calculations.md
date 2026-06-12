---
title: "user calculations"
date: 2010-02-15
forum: Programming Talk
---

### Post by JDShu on 2010-02-15
Hello everybody again! I feel like I keep asking questions here but you guys are amazingly helpful :D

How would I go about making a function that accepts a calculation as input eg.

(1+2)*3/4-5

and returns the answer?

It seems like a simple task but at the same time monumental from my perspective :( Is there even a simple way?

I'm using C, if thats important to know. Thanks in advance!

---

### Post by unknownPoster on 2010-02-15
I've done something similar in a data structures and algorithms class I took about a year ago.

First of all, you'll need to implement some sort of a string tokenizer.

---

### Post by BenAshton24 on 2010-02-15
I haven't done c in a while so here is a very, very basic implementation with python...

```
#! /usr/bin/env python
from __future__ import division
import sys

if len(sys.argv) == 2:
	print eval(sys.argv[1])
```

Edit: run it like this: python calc.py "(1+2)*3/4-5"

---

### Post by JDShu on 2010-02-15
@unknownPoster

yeah I'm using strtok() though its not a very intelligent way...

@BenAshton24

wow the eval function seems awesome. I guess I'll google up whether C has an equivalent.

---

### Post by maraldi on 2010-02-15
> **JDShu said:**
> @unknownPoster

yeah I'm using strtok() though its not a very intelligent way...

@BenAshton24

wow the eval function seems awesome. I guess I'll google up whether C has an equivalent.


I don't think that is going to work using strtok() if you want to evaluate mathematical formulae during runtime that  will become extremely complicated.

It sounds like to want to implement a mathematical expression parser.

One common method is called a recursive decent parser.

You should be able to find a C library to do this for you.

---

### Post by Some Penguin on 2010-02-16
If you're just looking for integers and not floating-point numbers, the tokenization isn't too brutal -- especially if you use something written for it, like Perl.  Floating point numbers are more of a pain, e.g. -4.6E+7 or so forth.

```

my $FPP = '[\-\+]?(?:[0-9]*\.)?[0-9]+(?:[eE][\-\+]?[0-9]+)?';

```

is decent for finding FPs in Perl, for instance.

If you're just looking for correctness, and you don't care about efficiency or *really* deep expressions (where stack overflow is an issue), here's a really, really simple method:



1.  If string is empty, return it.
2.  If string is a number, return it.  Don't forget about negatives, even if you're not using FPs.
3.  Look for parentheses.  More specifically, look for "(blah)" where blah itself does not
    contain any parentheses (i.e. it's the inner-most).  If found,
         a.  Recurse on blah.
         b.  Substitute the result for (blah).
         c.  Go back to step 1.
4. Look for exponential operator (e.g. ^).
   More specifically, look for leftmost   'a ^ b' where a and b are numbers, and there may be whitespace around the ^..  If found,
         a.  Compute a ^ b.
         b.  Substitute the result.
         c.  Go back to step 1.
5.  Look for leftmost  multiplication operator.  If found, compute, sub, go back.

Etc.

It'll be easier to debug if you print out the results of recursions.  e.g.

```

((4 + 5) ^ 4 - 4 / 2)                       
RECURSE on 4 + 5
ADD:  4 + 5 => 9
PAR:  (4 + 5) => 9
RECURSE on 9 ^ 4 - 4 / 2
POW:  9 ^ 4 => 6561
DIV:  4 / 2 => 2
SUB:  6561 - 2 => 6559
PAR:  (9 ^ 4 - 4 / 2) => 6559
        ANSWER = 6559


4 / 4 / 4 / 4
DIV:  4 / 4 => 1
DIV:  1 / 4 => 0.25
DIV:  0.25 / 4 => 0.0625
        ANSWER = 0.0625


4 / 2 * 2 / 4 * 2
MUL:  2 * 2 => 4
MUL:  4 * 2 => 8
DIV:  4 / 4 => 1
DIV:  1 / 8 => 0.125
        ANSWER = 0.125

-1e+2+2e3
ADD:  -1e+2 + 2e3 => 1900
        ANSWER = 1900

```

(using some simple Perl code, the FP regex I posted above, PPMDAS  precedence).  It's not especially elegant compared to generating a parse tree, but is logically pretty simple.

---

### Post by Tony Flury on 2010-02-16
The last time i coded something like this - after coding the parser to split the string into numbers and operators, I implemented a stack based algorithm which effectively translated the expression into reverse polish - and did the calculations as it went along.
The algorithm uses two stacks - one which contains the numbers, and another which contains the operators.

From what i can remember the algorithm after tokenisation is : 

0) Grab first token 
1) If the token is a number - push it on the number stack
2) If the token is a open parentheses push that to the stack.
3) If the token is a close parentheses then pop each operator off the operator stack in turn and carry out that operation on the values in the number stack - making sure that operands are popped and the results are pushed after every operation, and repeat until you find the first open parentheses. 
4) If the token is an EOL - then treat like a close parentheses but repeat until operator stack is empty.
4) If the token is an operator - compare its precedence with the current token on the top of the operator stack.
4a) If the new operator is higher precedence (i.e. * compared to +) then push that new operator onto the operator stack.
4b) if the new operator is a lower precedence (i.e. + compared to *) then do the operation specificed by the current top of the operator stack (remember to pop the operands of the stack in the right order) and push the result back onto the number stack, and then push the new operator onto the operator stack.
5) Repeat for every token until the operator stack is empty
6) The value on the number stack (there should only be one) is the right answer.

---

### Post by JDShu on 2010-02-16
Hey thanks everybody! You are all awesome. 

So I guess I need to find a way to implement recursive descent parsing (thanks maraldi!), and then pass the result into the algorithm that Tony Flury suggested. Debugging tip is great too, Some Penguin!

So far I can't find a library for recursive descent parsing, but wikipedia does have an example in C, so I guess I can work that into something useful.

---

### Post by ve4cib on 2010-02-16
Slightly less-useful, but you may find it easier to do a post-fix evaluator.  Basically instead of <X> <operator> <Y> for the input you would use <X> <Y> <operator>.  When you see a number push it on the stack.  When you see an operator pop the last two items off the stack, calculate the operation, and push the result back on the stack.

The notation looks a little weird, but it's much easier to work with from a programming perspective.

So in your example formula:

```
(1+2)*3/4-5
```

would translate to:

```
 1 2 + 3 * 4 / 5 - 
```

Evaluating it would look like this:

```
1. [] (start with an empty stack)
2. [1]
3. [1,2]
4. [3] (evaluate the +)
5. [3,3]
6. [9] (evaluate the *)
7. [9,4]
8. [2.25] (evaluate the /)
9. [2.25,5]
10. [-2.75] (evaluate the -, final answer)
```

---

### Post by Sporkman on 2010-02-16
Check out the "simple calculator" example at the "SporkApps" link in my sig...

---

### Post by Zugzwang on 2010-02-16
There are a couple of [compiler compilers]("http://en.wikipedia.org/wiki/Compiler_compiler") for C. Many of them come with examples that implement calculators. One example is the GNU Bison compiler compiler. Maybe you can just take a look at that example and extend it if needed? 

Compiler compilers basically take a definition of some input language and produce code that parses that language.

---

### Post by howlingmadhowie on 2010-02-16
parsing mathematical expressions is needlessly complicated because of precedence. for this reason, things like reverse polish notation are often used.  note that rpn can make some things rather difficult.

let's say we're trying to write a function to calculate a polynomial, like ax^2 + bx + c and the numerical arguments on the stack are in the order a b c x. as well as this you're allowed to use the operations dup, rot, swap, drop, * and +. good luck managing this.

one of the other methods is to use explicit bracketing. this is something scheme and lisp do, so the polynomial above would be written:

```

(+ (* a x x)
   (* b x)
   c)

```

Thus you end up with a tree structure. This is also much easier to program.  

In fact, lots of object oriented languages (such as scala) work by first  comparing the precedence of the different operators (of which there are many) and then adding brackets to create an explicit tree structure.

---

### Post by JDShu on 2010-02-16
My program requires taking mathematical expressions from user input and returning the answer, so using a different format like reverse polish notation is not an option unless I can turn a regular mathematical expression into that format... which I assume defeats the whole purpose.

---

### Post by xeptf4 on 2010-02-16
Read up on converting expressions to postscript.
The act of converting an expression to postscript could be used to evaluate it as well.

Well, the main idea could be to break the expression into a tree - start off with any operator as tree root and operators as its nodes.

So what do you think?

---

### Post by Zugzwang on 2010-02-16
> **JDShu said:**
> My program requires taking mathematical expressions from user input and returning the answer, so using a different format like reverse polish notation is not an option unless I can turn a regular mathematical expression into that format... which I assume defeats the whole purpose.

So did you had a look at GNU Bison or something like that?

---

### Post by Tony Flury on 2010-02-16
Creating a tree is one of way of doing it - but it should be noted that my algorithm takes a natural langauge expression and converts it to postfix in real time - and it is not really that complex.

---

### Post by howlingmadhowie on 2010-02-16
Just to add some more grit to the mill, transforming in real time from "normal" to rpn is not quite trivial. take for example:

3 * (4 + 5)

which is 27

here's how to transform it to rpn (my thoughts are written in bash-style comments):
```

3 * (4 + 5)  # 3 is okay at the start, but then comes a star,
             # that's no good, let's move it to the right
3 ( * 4 + 5) # eek! not good, the * has to go to after the 
             # brackets. let's find the end of the balancing bracket
3 (4 + 5) *  # okay, that's better, but i haven't yet dealt with
             # the bracket. the 4 is okay, but the + isn't
3 (4 5 +) *  # perfect, well sort of.

```

the result should be:
3 4 5 + *

so the transformation requires a bit of checking for brackets and counting to make sure they're balanced and stuff like that. of course you could just recursively descend as soon as you see brackets, but then you are just creating a tree.

---

### Post by Tony Flury on 2010-02-16
@howlingmadhowie - did you read my algorithm - work it through - it copes with brackets etc.

---

### Post by MadCow108 on 2010-02-16
the boost spirit parser uses something like this as an example
[http://www.boost.org/doc/libs/1_42_0/libs/spirit/doc/html/index.html](http://www.boost.org/doc/libs/1_42_0/libs/spirit/doc/html/index.html)
its documentation is also a quite good introduction to parsing grammars.

---

### Post by howlingmadhowie on 2010-02-16
> **Tony Flury said:**
> @howlingmadhowie - did you read my algorithm - work it through - it copes with brackets etc.

yeah it does, once you've already generated rpn. the point of my post was to show that generating rpn is not trivial.

---

### Post by JDShu on 2010-02-16
> **Zugzwang said:**
> So did you had a look at GNU Bison or something like that?

Yeah this seems good to know! At the moment its making my head explode and I've forgotten a lot of the stuff on grammar that I had to learn back in CS class haha.

---

### Post by maraldi on 2010-02-16
Try the open source parsers there are some really good, fast GPL ones.

---

### Post by ve4cib on 2010-02-16
> **howlingmadhowie said:**
> Just to add some more grit to the mill, transforming in real time from "normal" to rpn is not quite trivial. take for example:

3 * (4 + 5)

which is 27

here's how to transform it to rpn (my thoughts are written in bash-style comments):
```

3 * (4 + 5)  # 3 is okay at the start, but then comes a star,
             # that's no good, let's move it to the right
3 ( * 4 + 5) # eek! not good, the * has to go to after the 
             # brackets. let's find the end of the balancing bracket
3 (4 + 5) *  # okay, that's better, but i haven't yet dealt with
             # the bracket. the 4 is okay, but the + isn't
3 (4 5 +) *  # perfect, well sort of.

```

the result should be:
3 4 5 + *


This method will fall apart if you put the operations in a different order though.  For example:

```
3 + 4 * 5    # 3 is good, + isn't, so move it to the right
3 4 + * 5    # not enough arguments for a *, so move it to the right
3 4 + 5 *    # perfect, valid post-fix syntax
7 5 *        # evaluate 3 4 +
35           # evaluate 7 5 *

```

So the answer is 35.  But wait a minute, 3 + 4 * 5 is 23!  Darn that order of operations!

You can't just blindly move things to the right, compensating for parentheses.  You would also need to check for the natural order of operations when building the tree, which adds to the complexity not insignificantly.

---

### Post by JDShu on 2010-02-16
> **maraldi said:**
> 
Here's an example of a very simple C++ recursive decent parser that will do what you wanted.

It is an object oriented program but I'm sure you could modify it to work as a C program if you really have to.


You are the man (or woman)! I (messily) changed your code into something that works in C and its perfect! This is exactly what I wanted.

I'll definitely do more reading up on the theory and computer science-y stuff to get familiar, but this definitely solves my immediate problem. I'm embarrassed to admit that I don't understand it yet, but in the name of knowledge, I shall get to understand it better :D

---

### Post by howlingmadhowie on 2010-02-17
> **ve4cib said:**
> This method will fall apart if you put the operations in a different order though.  For example:

```
3 + 4 * 5    # 3 is good, + isn't, so move it to the right
3 4 + * 5    # not enough arguments for a *, so move it to the right
3 4 + 5 *    # perfect, valid post-fix syntax
7 5 *        # evaluate 3 4 +
35           # evaluate 7 5 *

```

So the answer is 35.  But wait a minute, 3 + 4 * 5 is 23!  Darn that order of operations!

You can't just blindly move things to the right, compensating for parentheses.  You would also need to check for the natural order of operations when building the tree, which adds to the complexity not insignificantly.

indeed, precedence is a terrible thing, which is why i much prefer languages like lisp, smalltalk and forth which have no concept of precedence :) (well, smalltalk does, but it's fairly simple)

oh, and btw, there are rules for evaluating precedence in rpn notation. these were pasted by tony earlier on and give the correct result if you start from the line containing "3 4 + 5 *".

---

### Post by veko on 2010-02-18
This is not really a solution for you, unless you implement the code into your program, but I've just got to mention this command line calculator utility:
[URL="http://www.sourcefiles.org/Productivity_Tools/Calculators/e-0.02718.tar.gz"]http://www.sourcefiles.org/Productivity_Tools/Calculators/e-0.02718.tar.gz
[/URL] 
I don't know who has written it, and I'm not really sure whether it's an example of good or bad coding habits, but in its simple austerity it's really ingenious piece of code.

That page has lots of other calculators with sources too. You might want to look at their code too to get some hints.

---

