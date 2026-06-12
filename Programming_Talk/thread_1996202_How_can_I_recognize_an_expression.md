---
title: "How can I recognize an expression ?"
date: 2012-06-04
forum: Programming Talk
---

### Post by DaviesX on 2012-06-04
I want to make a simple scientific calculator, but I have come up with a question, how can I recognize and calculate an expression from an inputting string as a compiler does ?

It should know how the priority should be like, and parenthesis too.
For example, 1+2x3 = 1+6 = 7
And if the input string is a function, what is the way to store it ?

Can you tell me what algorithm I need to use ?
Thank you :)

---

### Post by lisati on 2012-06-04
You might want to look into using something like a recursive descent parser. Although I'm familiar with the basics, how they work is beyond my abilities to explain clearly. No doubt someone more experienced in parsing expressions than myself will be able to help.

---

### Post by DaviesX on 2012-06-04
Oh, thanks anyway, I just need the name of that algorithm

---

### Post by Bachstelze on 2012-06-04
This is *a lot* more complicated than you make it sound. It's not "Google the name of an algorithm, get some pseudocode and implement it". Unless you do a copypasta of some existing code (from e.g. bc), you will have a lot of thinking to do. This is a project for a CS major in college (and not a freshman).

---

### Post by the_unforgiven on 2012-06-04
[Reverse Polish Notation]("http://en.wikipedia.org/wiki/Reverse_Polish_Notation")?

This may also help:
[http://en.wikipedia.org/wiki/Operator-precedence_parser](http://en.wikipedia.org/wiki/Operator-precedence_parser)
which is a specialization of recursive-descent parser mentioned by lisati above.

A simple RPN evaluator should do the job. ;)

---

### Post by lisati on 2012-06-04
> **the_unforgiven said:**
> 
A simple RPN evaluator should do the job. ;)
D'oh! Why didn't I think of that? :D

As has been noted up-thread, there's more to evaluating something like 1+2x3 and coming up with the right answer than might meet the eye.

---

### Post by the_unforgiven on 2012-06-04
> **lisati said:**
> D'oh! Why didn't I think of that? :D

As has been noted up-thread, there's more to evaluating something like 1+2x3 and coming up with the right answer than might meet the eye.
Actually, arithmetic evaluation in itself is not all that complex - at least integer arithmetic within the range of INT_MIN and INT_MAX isn't :p.

Almost all of the complexity in a scientific calculator lies in handling arbitrary precision and maybe floating-point arithmetic.

---

### Post by schauerlich on 2012-06-04
You might find [this](http://ubuntuforums.org/showthread.php?t=1441700) helpful. A common way of evaluating infix expressions (like a calculator would use) is to convert it to what's called Reverse Polish Notation (aka postfix) with Dijkstra's Shunting Yard algorithm, and then evaluate the RPN expression directly. The thread I linked to earlier has a bunch of implementations of RPN evaluators in various languages, and even some infix evaluators. If you know what a stack is and you can read pseudocode, [this](http://en.wikipedia.org/wiki/Shunting-yard_algorithm) page will be useful. Also check out [Rosetta Code](http://rosettacode.org/wiki/Parsing/Shunting-yard_algorithm) for some complete examples.

---

### Post by schauerlich on 2012-06-04
> **Bachstelze said:**
> This is *a lot* more complicated than you make it sound. It's not "Google the name of an algorithm, get some pseudocode and implement it". Unless you do a copypasta of some existing code (from e.g. bc), you will have a lot of thinking to do. This is a project for a CS major in college (and not a freshman).

For simple expressions, and with guidance from Wikipedia, I think it's certainly doable by someone with a bit of programming experience. Of course, a more complete calculator with complex expressions would take a full-on interpreter, which is beyond the beginner level.

---

### Post by Bachstelze on 2012-06-04
Okay, I stand corrected. Parsing algorithms are not my forte. :p

---

### Post by Barrucadu on 2012-06-04
You need to first specify your grammar in BNF or something, and then write a parser for it. Recursive descent parsers are pretty easy, but with backtracking can be *very* inefficient, and so I'd recommend a lookahead parser (admittedly, this may not be necessary at all in your case depending on what exactly you want to parse). You will also need some way of specifying operator precedence. You can either transform the grammar to reflect this, or perform some rotations on the parse tree to get the same result. Personally, I prefer the tree rotation method as it keeps the grammar cleaner, although this does add extra complexity to the parsing code.

Once you have your parse tree, evaluating it should be trivial.

---

### Post by 11jmb on 2012-06-04
The cool thing about the Shunting Yard Algorithm is that you can build an unambiguous operator tree, which can be traversed to generate any notation you wish.

This should be a simple enough task for anybody with a basic understanding of data structures.

---

### Post by DaviesX on 2012-06-04
Thank you very much :) I'll go read it

---

### Post by xytron on 2012-06-05
It seems difficult to find tutorials or in-depth information about the procedures used to create an expression parser.   A recursive descent parser can be good enough for many projects.

You could also just use an expression parsing library such as MuParser (free) or bcparser (very reasonable pricing).

---

### Post by DaviesX on 2012-06-05
Oh, I think there is a very detailed one on Wikipedia, 
[http://en.wikipedia.org/wiki/Shunting-yard_algorithm]("http://en.wikipedia.org/wiki/Shunting-yard_algorithm")

---

### Post by DaviesX on 2012-06-09
I have a question, why can't sscanf deal with ',' ?

For example,
```
 
main:   (1, 5)
format: (%d, %d) 

```
and sscanf seems doesn't work
What is the reason ?
And if I have to write my sscanf to achieve that ?

Thank you. :)

---

### Post by DaviesX on 2012-06-09
Now, I have finished an definite integration calculator with RPN algorithm.
[https://m20tyg.bay.livefilestore.com/y1ps-vbnJBFjEjhpZwNr802GK0Yi3DsqntOyDDlPLx3DUe4BPXq4HJXuhpIpYGRn_3MyQBCD8Q7_SSLUB-mXubetA/Integrator.zip?download&psid=1]("https://m20tyg.bay.livefilestore.com/y1ps-vbnJBFjEjhpZwNr802GK0Yi3DsqntOyDDlPLx3DUe4BPXq4HJXuhpIpYGRn_3MyQBCD8Q7_SSLUB-mXubetA/Integrator.zip?download&psid=1")
But it can't process negative sign, I don't know how to deal with unary operator :mad:

---

