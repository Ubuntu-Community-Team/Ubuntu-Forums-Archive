---
title: "Parsing using Flex and C (or C++)"
date: 2009-03-15
forum: Programming Talk
---

### Post by bcuriel on 2009-03-15
Hello all!

I have a programming assignment due soon about parsing expressions using NOTHING more than Flex and C (or C++ if it is easier).
Yacc (or Bison) are not allowed.

The assignment is as follows:

Use Flex and C++ to parse a mathematical expression which may include parentheses, +, -, *, / with their respective arithmetic precedence. 
Use Flex as a token recognizer and C or C++ to write the parser.

YACC (OR BISON) IS NOT ALLOWED!

The output should be MIPS assembly language which will be fed to the SPIM simulator to evaluate the expression.


My question is.... HOW!?!?!

Any help will be very much appreciated! This is my second time using Flex, and I know how to write regular expressions and everything, but I don't know what to do in C (or C++) to generate the Assembly language according to the mathematical operators that the parser encounters.

---

### Post by rich1939 on 2009-03-15
[QUOTE=bcuriel;6901171]Hello all!
Use Flex and C++ to parse a mathematical expression which may include parentheses, +, -, *, / with their respective arithmetic precedence. 
Use Flex as a token recognizer and C or C++ to write the parser.

For expressions, I'd recommend that you use just C for the whole works. Globbing tokens isn't all that difficult using just C and flex will just make the whole process less efficient and much more complex, IMO.

---

### Post by bcuriel on 2009-03-15
How would I go about doing that, though?

We are supposed to calculate the First and Follow sets so that we have a predictive parser (Isn't that done in Flex?). But Even though I can do that on paper, I am having an incredibly hard time coding it.

And, like I said, the professor is asking us to use Flex as a token recognizer, I am not quite sure if he will take points off for not using it. Maybe it isn't as efficient, but I think that he is trying to evaluate our use of Regular Expressions in Flex. It's just a guess... maybe he won't even care if I don't use Flex, but I was just trying to stick to the instructions.

Thank you for replying!

---

### Post by Berserker v7 on 2009-03-16
Using C alone would be ideal.

With flex, well i have some untested suggestions, but i see no reason why they should not work ;)... will leave that to you

So, flex code has three sections, right? use the global and function declaration sections to design a stack... prototypes, function declarations, etc in the global section and the function definitions in the function section.

Now, in the middle section, give appropriate rules to pass/evaluate the lexemes into/within the stack, instead of passing tokens... this way, you will still be using flex and yet, your program will be that of an ordinary calculator program using stack written in c... hope this helps

---

### Post by bcuriel on 2009-03-16
Thanks!

You guys were mighty helpful!:D

--B

---

### Post by Berserker v7 on 2009-03-17
So, did you get it working? if yes, i would be dilighted to get a copy of your work :)

---

### Post by bcuriel on 2009-03-17
Sorry about that, Spring break got in the way lol.

If you are still interested in looking at my assignment, send me a private message with your email and I can send you my files containing the working code. Do note, however, that there are a few bugs in it. But if you enter a valid expression, it will parse it and output MIPS Assembly code for its evaluation. This MIPS code can then be fed into SPIM (or XSPIM) and once you run it there, you will get the evaluation to the expression.

Thank you all for your help!


--B

---

### Post by rahul.tapali on 2010-10-19
Hello,
   I have chosen topic called "simulation of any complex regular expression" for my system software mini-project.But I don't know much about building simulator please if anyone know about simulation help me in getting into this.
   Thank you...

---

