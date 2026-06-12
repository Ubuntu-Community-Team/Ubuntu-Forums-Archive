---
title: "C++ math help"
date: 2008-09-02
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-02
i am probably getting really far ahead of my self but its the last day of summer and i am really bored...i want to write a program where you enter an algebraic problem and the computer solves it

i need to know 2 things:

math libs for C++

how i can interpret a string and tell if each character in it is an operator, a variable (any letter), or a number

EDIT: OT noob question:

when you do #include whats the difference between putting <> around a file name and putting "" around the name?

---

### Post by LaRoza on 2008-09-02
> **jimi_hendrix said:**
> 
i need to know 2 things:

math libs for C++

how i can interpret a string and tell if each character in it is an operator, a variable (any letter), or a number

What kind of algebra? A quadratic equation would be easy, a linear very easy. 

What kind of math libs? math.h (or cmath) is a math lib.

You can iterate over a string (or character array) using either C conventions, or C++ methods (I am not up on all the string class's methods. Read the docs).

For quadratic or higher, you'll need to cope with imaginary numbers.
> 
EDIT: OT noob question:

when you do #include whats the difference between putting <> around a file name and putting "" around the name?

Before that is answered, that is an elementary question and would be answered by any C++ reference. 

<> means the preprocessor looks in the include path for the file, and quotes means it looks in the current directory.

---

### Post by jimi_hendrix on 2008-09-02
> **LaRoza said:**
> What kind of algebra? A quadratic equation would be easy, a linear very easy. 

i was thinking general algebra first (4x - x(3x^2 - 5) = 9x)

> What kind of math libs? math.h (or cmath) is a math lib.

basic math lib...math.h is probably ok

> You can iterate over a string (or character array) using either C conventions, or C++ methods (I am not up on all the string class's methods. Read the docs).

i will

> For quadratic or higher, you'll need to cope with imaginary numbers.

wont need that yet

> Before that is answered, that is an elementary question and would be answered by any C++ reference. 

<> means the preprocessor looks in the include path for the file, and quotes means it looks in the current directory.

thank you...i hate when tutorials dont explain things properly

---

### Post by WW on 2008-09-02
> **LaRoza said:**
> 
<> means the preprocessor looks in the include path for the file, and quotes means it looks in the current directory.
Actually the quotes tell the compiler to look in the directory of the file  that contains the #include statement *first*, then move on to the include path if it isn't found there.

---

### Post by LaRoza on 2008-09-02
> **jimi_hendrix said:**
> i was thinking general algebra first (4x - x(3x^2 - 5) = 9x)


It is easiest (best) to have the program solve problems in standard form.

To do that problem, you'd have to essential write a program that puts it in standard form.

---

### Post by jimi_hendrix on 2008-09-02
well then i will have to write a program to put it in standard form

---

### Post by CptPicard on 2008-09-02
> **LaRoza said:**
> 
For quadratic or higher, you'll need to cope with imaginary numbers.

Well, you don't strictly have to, unless you want the (possible) imaginary solutions too :)

> There is no number to find)

:confused:  it's a third degree polynomial with potential roots...

---

### Post by LaRoza on 2008-09-02
> **CptPicard said:**
> Well, you don't strictly have to, unless you want the (possible) imaginary solutions too :)

So you are saying that you don't have to unless you don't want the solutions?

Isn't that a bit like solving a problem without getting the answer?

> it's a third degree polynomial with potential roots...
I misread it.

---

### Post by nvteighen on 2008-09-02
An algebra solver... in C++... are you aware of what are you trying to ask the language to do??

1) Make the language evaluate the expression and distinguish what's data (constants and variables) and what's an operation.
2) Make the language do the operation.
3) Generate the reduced expression.
4) If expression can be further reduced, goto 1 :)

And that to yield a highly inefficient program that doesn't take care for canonical forms to short-cut solutions with formulas...

...using a language that is not able to evaluate data and apply what data means... for C++ "x^2 - 9" is just a string with funny characters...

---

### Post by Ruhe on 2008-09-02
OMG!
You didn't read Herbert Shildt's "C, The complete reference"?
Check out chapter 24.

---

### Post by jimi_hendrix on 2008-09-02
> **nvteighen said:**
> An algebra solver... in C++... are you aware of what are you trying to ask the language to do??


yes...thats why i said at the start i think i am getting ahead of my self

> 
1) Make the language evaluate the expression and distinguish what's data (constants and variables) and what's an operation.
2) Make the language do the operation.
3) Generate the reduced expression.
4) If expression can be further reduced, goto 1 :)

...using a language that is not able to evaluate data and apply what data means... for C++ "x^2 - 9" is just a string with funny characters...

what language would you recommend then (any resources would help too)

---

### Post by Kadrus on 2008-09-02
> An algebra solver... in C++... are you aware of what are you trying to ask the language to do??
Heh,even when functional languages are needed they are not used :-p
**edit**
> what language would you recommend then (any resources would help too)
[Haskell]("http://haskell.org"),[ML]("http://caml.inria.fr"),[Lisp]("http://cliki.net/").
Haskell is widely used in Mathematical applications and domains.

---

### Post by jimi_hendrix on 2008-09-02
how big a job would this be in haskell...and OT Kadrus what is your avatar called because ive seen it as a symbol for both scheme and haskell

---

### Post by Kadrus on 2008-09-02
> **jimi_hendrix said:**
> how big a job would this be in haskell...and OT Kadrus what is your avatar called because ive seen it as a symbol for both scheme and haskell
Well I'd say a lot smaller than C++.Haksell is a purely functional programming language,that has many Mathematical Libraries.
Haskell code is similar to standard mathematical notation in syntax.
[http://hackage.haskell.org/packages/archive/pkg-list.html#cat:Math](http://hackage.haskell.org/packages/archive/pkg-list.html#cat:Math)
Take a look at : [Haskell and Mathematics]("http://www.haskell.org/haskellwiki/Haskell_and_mathematics")
It's [Lambda Calculus ]("http://en.wikipedia.org/wiki/Lambda_calculus")

---

### Post by jimi_hendrix on 2008-09-02
well lisp looks like i will have nightmares and i have never heard of ML so i looked at haskell...the main problem would be parsing the variables/operaters/numbers out of the inputed string problem

---

### Post by CptPicard on 2008-09-02
The biggest problem is the expression rewriting search... the more stuff you want it to be able to handle, the more difficult it becomes. The computer has no way of magically knowing what is a "good" expression or direction to massage the expression into... (unless you really just keep it as a basic polynomial solver or something)

---

### Post by jimi_hendrix on 2008-09-02
i would keep it simple and expand as i needed/learned...i would just want something that can solve basic equations/polynomials first

---

### Post by nvteighen on 2008-09-03
As Kadrus said, this is a job for functional programming and what functional programming is meant to be for (but not exclusively).

There's an example of a polynomial solver in Scheme at [SICP]("http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-18.html#%_sec_2.5"). Read the whole chapter (well, I recommend you to read the whole book :)) to see what it takes to do first a generic calculator and then extend it to symbolical notation. You'll notice that even in Scheme such a thing is not a trivial task and the issue CptPicard mentioned (that you have to teach the program the rules of reduction)... but it surely is much more feasable than in an imperative language like C++.

Here Lisp's "data = code/code = data" principle makes you life really easier. You just could write polynomials as Lisp expressions and, after teaching it how to reduce it (which is the hard part), just reduce them. I don't know if Haskell supports that idea; it would be nice if someone could tell me.

But you want an equation solver, so you have to reduce polynomials to both sides of the equation and then equalize the equation to 0, and reduce the non-zero side... highly inefficient of course, as you better could eliminate things on-the-fly, as you usually would do when solving an equation in paper...

Yes, it's hard, but I don't want you to give up because of that. Maybe, your programming skills aren't enough to deal with this (as mine... I just know how to do this "in theory"), but if you really want to do it, try it as a very-long-term project you build by little steps, learning how to do each step (keeping the final goal in mind)... and value more what you're learning than finishing the project; you may never finish it, but you'll definitely learned something you might use latter.

(Also, it may be a good excuse to learn some Lisp or Haskell, :))

---

### Post by cmay on 2008-09-03
> how i can interpret a string and tell if each character in it is an operator, a variable (any letter), or a number

EDIT: OT noob question:

when you do #include whats the difference between putting <> around a file name and putting "" around the name?
hi. in case you want to know how to create a simple calculator in c++ and how the program can figure out what is operatrs and what is not i found a litle calculator some where . its not mine. but it gives you the idea.
i renember you asked a while ago what the argv argc is used for. here is such example. as said i cant take credit for the example but i cant renember where i snatched it from either . i copied it to rewrite it as a small version in c . which will not be able to do more than just simple math like this. :)
[PHP]// scalc.cpp - simple calculator
#include <iostream>
#include <string>
using namespace std;
int main(int argc,char *argv[])
{
	if (argc!=4) {
		cout << "Usage: scalc number operator number" << endl;
		exit(1);
	}
	double num1 = atof(argv[1]);
	string op = argv[2];
	double num2 = atof(argv[3]);
	double result;
	if (op=="+") result = num1 + num2;
	else if (op=="-") result = num1 - num2;
	else if (op=="*") result = num1 * num2;
	else if (op=="/") {
		if (num2==0) {
			cout << "Error: division by zero" << endl;
			exit(1);
		}
		result = num1 / num2;
	}
	else {
		cout << "Error: unknown operator " << op << endl;
		exit(1);
	}
	cout << argv[1] << " " << argv[2] << " " << argv[3] << " = " << result << endl;
	return(0);
}[/PHP]

---

### Post by jimi_hendrix on 2008-09-03
> **nvteighen said:**
> 
(Also, it may be a good excuse to learn some Lisp or Haskell, :))

i picked haskell because lisp scared me off a while ago with some bad scheme tutorials

---

### Post by cabalas on 2008-09-03
No matter what language you end up deciding to go with it's a great example for teaching yourself how to write a [Recursive Descent Parser]("http://en.wikipedia.org/wiki/Recursive_descent_parser") which you could possibly keep expanding until you have written yourself a parser for a programming language, providing yourself with a neat ongoing project.

---

### Post by Zugzwang on 2008-09-04
> **jimi_hendrix said:**
> i would keep it simple and expand as i needed/learned...i would just want something that can solve basic equations/polynomials first

Even this is quite a tough task. You could do that numerically but I'm afraid that for polynomial degrees >4 there is no way of solving it non-numerically so far (as far as I know).

---

### Post by jimi_hendrix on 2008-09-05
> **cabalas said:**
> No matter what language you end up deciding to go with it's a great example for teaching yourself how to write a [Recursive Descent Parser]("http://en.wikipedia.org/wiki/Recursive_descent_parser") which you could possibly keep expanding until you have written yourself a parser for a programming language, providing yourself with a neat ongoing project.

so i can write my own language after this...?

---

### Post by generalguy on 2008-09-05
There's nothing stopping you from using lex/yacc antlr to make a parser and your on language now.

Note that a generic algebra solver cannot exist. It's not exactly trivial to solve fifth and higher order polynomials, even numerically, and those are the easiest things you can get. Making a parser is fairly simple, although exponentiation is tricky (it's right associative).

---

### Post by jimi_hendrix on 2008-09-06
ok thanks

---

### Post by jimi_hendrix on 2008-09-06
advised language to use to parse to make my own language?

---

### Post by kjohansen on 2008-09-06
> **jimi_hendrix said:**
> advised language to use to parse to make my own language?
[http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

[http://en.wikipedia.org/wiki/Recursive_descent#Implementation_in_functional_languages](http://en.wikipedia.org/wiki/Recursive_descent#Implementation_in_functional_languages)

---

### Post by jimi_hendrix on 2008-09-06
so functional language + recursive parsing = my new language == awsome?

---

### Post by Kadrus on 2008-09-06
> advised language to use to parse to make my own language?
[ML]("http://caml.inria.fr/").
Here's a PDF on language implementation using [CAML LIGHT.]("http://caml.inria.fr/pub/docs/fpcl/fpcl-12.pdf")

---

### Post by jimi_hendrix on 2008-09-06
do u advise caml or caml light (i realize the pdf is for caml light)

---

### Post by Kadrus on 2008-09-06
I advise OCaml..although any ML-derived language would be good as well.

---

