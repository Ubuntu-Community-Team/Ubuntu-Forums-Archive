---
title: "how to solve y=++y + ++x"
date: 2011-01-15
forum: Programming Talk
---

### Post by c2tarun on 2011-01-15
hi friends.
Can anyone please tell me how to solve statements like
```

y=++x + ++y;

```

I want to know the concept how compiler solve such expressions.
please reply
thanks

---

### Post by schauerlich on 2011-01-15
Read the book or ask your professor.

---

### Post by lisati on 2011-01-15
I'm sure this topic has been mentioned in "Programming Talk" before........

If in doubt, use parentheses.

---

### Post by c2tarun on 2011-01-15
> **schauerlich said:**
> Read the book or ask your professor.

Actually in books they just explain postincrement and preincrement operators.
I tried but by the book I always end up in wrong answer.

for example:
```

int x=20;
int y=35;
x=y++ + x++;
y=++y + ++x;

```

my answer was x=56 and y=93.
but on running the programs I am getting y=94.
by the book y should be incremented first and then used. Final value of the RHS of expression in last should be stored as it is in y.
but value of final expression is also incremented by one.

I'll be very thankful if you can please explain me.
otherwise thanks a lot for replying.

---

### Post by c2tarun on 2011-01-15
> **lisati said:**
> I'm sure this topic has been mentioned in "Programming Talk" before........

If in doubt, use parentheses.

I looked into programming talk forums but failed to find the particular thread.
If you can then please give me the link of that thread.
Thank you.

---

### Post by lisati on 2011-01-15
> **c2tarun said:**
> I looked into programming talk forums but failed to find the particular thread.
If you can then please give me the link of that thread.
Thank you.

If memory serves correctly, it was in the middle of another thread. It might take a while to find. 30 years ago I was taught that where there was likely to be any ambiguity, use parentheses to give the compiler a "heads up" on what you mean with an expression.

---

### Post by worksofcraft on 2011-01-16
> **c2tarun said:**
> hi friends.
Can anyone please tell me how to solve statements like
```

y=++x + ++y;

```

I want to know the concept how compiler solve such expressions.
please reply
thanks

Actually this is a very easy one. ++ before the variable means **pre-incremen**t, so it increments each variable before using it:

Thus firstly it increments x, secondly it increments y and then it adds the two together (total being x+y+2)

Finally it assigns the result to y, which overwrites the incremented value that it gained a moment ago.

p.s. if you are not sure of [C++ operator precedence]("http://www.cppreference.com/wiki/language/operator_precedence") you can look it up on that link or even better just put in some brackets and split the expression into smaller steps so there can be no doubt ;)

---

### Post by c2tarun on 2011-01-16
> **worksofcraft said:**
> Actually this is a very easy one. ++ before the variable means **pre-incremen**t, so it increments each variable before using it:

Thus firstly it increments x, secondly it increments y and then it adds the two together (total being x+y+2)

Finally it assigns the result to y, which overwrites the incremented value that it gained a moment ago.

p.s. if you are not sure of [C++ operator precedence]("http://www.cppreference.com/wiki/language/operator_precedence") you can look it up on that link or even better just put in some brackets and split the expression into smaller steps so there can be no doubt ;)


I applied this concept but may be I applied it wrong.
how I applied:
```


x=20
y=35
expression:   x=y++ + x++
valued used:      35        20
now x=55  and y=36
now
expression:y=++y + ++x
values used:   37       56
now x=56   y=56+37=93


but final answer is :(
x=57 and y=94

```

---

### Post by Lootbox on 2011-01-16
The result of the expression:
```

x = y++ + x++;

```
...is undefined behavior. The exact specification of how statements like these behave is somewhat confusing; check out [this thread](http://stackoverflow.com/questions/4176328/undefined-behavior-and-sequence-points[/url) on Stack Overflow for a more detailed explanation. The basic reasoning is, with post-increment, the values of x and y are used in the assignment to x, but it's unclear if the assignment to x should happen before or after the actual increment on x. The standard thus mandates it as undefined behavior, allowing compilers to perform optimizations that would otherwise be impossible.

However, in the example:
```

y = ++y + ++x;

```
... my impression is that since the side-effects on x and y are completely finished by the time assignment to y occurs, it is well-behaved. However, I'm not 100% on this and gcc still gives a warning about that statement.

In short, it shouldn't matter because you should never write code like this anyways.

---

### Post by worksofcraft on 2011-01-16
yes, as Lootbox says... with the ++ AFTER the variable it is known as "post-increment" and that becomes undefined behavior because it isn't clear quite when it gets incremented in relation to other things.

However with pre-increment: 
expression:y=++y + ++x
values used:   37       56

so ++y becomes 38 and ++x becomes 57
add then these two together should give y = 95 IMO :confused:

```


$> g++ -Wall -pedantic preinc.cpp
preinc.cpp: In function &#8216;int main(int, char**, char**)&#8217;:
preinc.cpp:8: warning: operation on &#8216;y&#8217; may be undefined
$> ./a.out
x=57, y=95

```

:)

---

### Post by slavik on 2011-01-16
for the really smart ones, save the simple code in C (C++ adds a lot of unnnecessary code)

then compile with gcc as follows:
gcc -S mycode.c

read the assembly, you will see what gets done. 94 is the correct answer for y.

---

### Post by Arndt on 2011-01-16
The word usually employed here is "evaluate", rather than "solve".

In C, there is the concept of "sequence point". I'm not sure of the rules for where they appear, but the idea is that at a sequence point, all previous evaluations have happened, whereas between sequence points, things can be done in parallel, and thus the value of something like x be undefined when x++ occurs somewhere else in the expression.

A statement end (semicolon) is a sequence point, but I'm not sure whether an assignment is, so the value of y in your example may be undefined in C. 

There are probably useful and correct explanations of this somewhere - I only wanted to mention the concepts to look for.

---

### Post by StephenF on 2011-01-16
Either of these is infinitely preferable.
```

y += 1 + (++x);
y += 2 + x++;

```

---

### Post by i4ba1 on 2011-01-16
> **c2tarun said:**
> hi friends.
Can anyone please tell me how to solve statements like
```

y=++x + ++y;

```I want to know the concept how compiler solve such expressions.
please reply
thanks

maybe your code should like this: 
```

 int x = 56;
  int y = 93;
  y = (++y) + (++x);
  printf("result:%d\n ",y);

```

The ouput is: 151.

---

### Post by trent.josephsen on 2011-01-16
Two modifications of the same object without an intervening sequence point is ALWAYS undefined behavior.  Sequence points are terminated by semicolons or the comma *operator* (not the comma as a separator in a function call).  Parentheses don't help here, because it's not an order of operations issue -- it's an intrinsic ambiguity in the language.

Changing postincrement to preincrement changes nothing; undefined behavior is still undefined behavior, and it's not guaranteed or even likely to do anything meaningful.  93, 94, 95, 4, -1, a segmentation fault, nasal demons, and a suffusion of yellow are all perfectly acceptable results as far as the standard is concerned.

The correct solution is to write code that doesn't invoke undefined behavior.

---

### Post by worksofcraft on 2011-01-16
> **trent.josephsen said:**
> Two modifications of the same object without an intervening sequence point is ALWAYS undefined behavior.  Sequence points are terminated by semicolons or the comma *operator* (not the comma as a separator in a function call).  Parentheses don't help here, because it's not an order of operations issue -- it's an intrinsic ambiguity in the language.

Changing postincrement to preincrement changes nothing; undefined behavior is still undefined behavior, and it's not guaranteed or even likely to do anything meaningful.  93, 94, 95, 4, -1, a segmentation fault, nasal demons, and a suffusion of yellow are all perfectly acceptable results as far as the standard is concerned.

The correct solution is to write code that doesn't invoke undefined behavior.

The compiler warns it **may** be undefined.
It is my understanding that it is only undefined if the final value can be ambiguous. y = ++y + ++x; can OTOH only produce one result which will be the same as:
[php]
   ++y; ++x;
   y = y + x;
[/php]

... but if it helps to avoid confusion (and arguments) then it would indeed be better to write it that way ;)

---

### Post by trent.josephsen on 2011-01-16
> **worksofcraft said:**
> The compiler warns it **may** be undefined.
It is my understanding that it is only undefined if the final value can be ambiguous. y = ++y + ++x; can OTOH only produce one result which will be the same as:
[php]
   ++y; ++x;
   y = y + x;
[/php]

... but if it helps to avoid confusion (and arguments) then it would indeed be better to write it that way ;)
It **is** undefined, regardless of whether the compiler diagnoses it or not (a diagnostic is, I believe, not required here.)

Your belief that the use of ++i on the RHS of the assignment imposes order on the evaluation of the expression is mistaken.  Undefined behavior means anything can happen, including doing what you expect.

A good discussion of sequence points can be found at [http://c-faq.com/expr/seqpoints.html](http://c-faq.com/expr/seqpoints.html).

---

### Post by worksofcraft on 2011-01-16
> **trent.josephsen said:**
> It **is** undefined, regardless of whether the compiler diagnoses it or not (a diagnostic is, I believe, not required here.)

Your belief that the use of ++i on the RHS of the assignment imposes order on the evaluation of the expression is mistaken.  Undefined behavior means anything can happen, including doing what you expect.

A good discussion of sequence points can be found at [http://c-faq.com/expr/seqpoints.html](http://c-faq.com/expr/seqpoints.html).

pre-increment defines that it is incremented *first* and that then the value gets used. Thus IMO it is not undefined and only one thing can happen: There is simply no alternative interpretation in which the other use of variable y (assignment) would not come after that.

Meh whatever, I don't care.

p.s. if you wrote something like:
[php]
   y += ++y;
[/php]
then I would agree as there is both a data-in and a data-out cycle involved in the += operator and it isn't defined where the ++ happens between those.

---

### Post by psusi on 2011-01-16
> **worksofcraft said:**
> pre-increment defines that it is incremented *first* and that then the value gets used. Thus IMO it is not undefined and only one thing can happen: There is simply no alternative interpretation in which the other use of variable y (assignment) would not come after that.

Meh whatever, I don't care.

The incremented value is used in the expression, yes, but when you also assign to the same variable, the order of the assignment and increment are undefined.

The standard only requires that the result of the post increment be stored back to the variable after the next sequence point ( the semicolon ).  That could be before, or after the assignment ( = ).

---

### Post by worksofcraft on 2011-01-16
> **psusi said:**
> The incremented value is used in the expression, yes, but when you also assign to the same variable, the order of the assignment and increment are undefined.

The standard only requires that the result of the post increment be stored back to the variable after the next sequence point ( the semicolon ).  That could be before, or after the assignment ( = ).

I thought I said pre-increment...
Why do you talk about post increment?
:confused:

---

### Post by psusi on 2011-01-16
> **worksofcraft said:**
> I thought I said pre-increment...
Why do you talk about post increment?
:confused:

Typeo; I meant pre.

---

### Post by worksofcraft on 2011-01-16
> **psusi said:**
> Typeo; I meant pre.

Ah... ok
in that case you are are right and I was wrong... the language doesn't guarantee that the result of ++y will be stored back to variable y before the assignment takes place, even if the value of ++y is guaranteed to be calculated before then.

---

### Post by slooksterpsv on 2011-01-16
```

x = 1
y = 1

y = ++y + ++x //this is the equivalent of doing 
//(y +=1, x+= 1, y = y + x)
//y = 4
//x = 2

```

Now let's do the same, but reversed (post-increment instead of pre-increment):
```

x = 1
y = 1

y = y++ + x++ //this is the equivalent of doing 
//(y = y + x then y += 1, and x += 1)
//y = 3
//x = 2

```

What would the following produce =P:
```

x = 1
y = 1
z = 0

z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z
//haha this ones a thinker =P

```

---

### Post by slavik on 2011-01-17
> **slooksterpsv said:**
> ```

x = 1
y = 1

y = ++y + ++x //this is the equivalent of doing 
//(y +=1, x+= 1, y = y + x)
//y = 4
//x = 2

```

Now let's do the same, but reversed (post-increment instead of pre-increment):
```

x = 1
y = 1

y = y++ + x++ //this is the equivalent of doing 
//(y = y + x then y += 1, and x += 1)
//y = 3
//x = 2

```

What would the following produce =P:
```

x = 1
y = 1
z = 0

z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z
//haha this ones a thinker =P

```
Not really ...
z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z

is:
++x - done 3 times, so x = 4
++y - done 3 times, so y = 4
++z - done 2 times, so z = 2

z = 4 + 4 + 2
z = 10

x++ - done 1 time, so x = 5
y++ - done 1 time, so y = 5
z++ - done 1 time, so z = 11

---

### Post by Zugzwang on 2011-01-17
@OP: Did you actually say which programming language you are working with? Someone started to assume C or C++ in this thread, for which, according to the answers, the statement has undefined behaviour.

However, in Java, for example, a language in which your code would also be syntactically valid, the behaviour is, as far as I know, defined.

---

### Post by psusi on 2011-01-17
Still undefined, for the same reason.

If a pre/post increment/decrement is used on a variable on the right hand side, and that same variable is on the left hand side, the results are undefined.

---

### Post by Zugzwang on 2011-01-17
> **psusi said:**
> Still undefined, for the same reason.

If a pre/post increment/decrement is used on a variable on the right hand side, and that same variable is on the left hand side, the results are undefined.

I'm not sure if your answer referred to my post, so I can only assume this. The [Java Language Specification]("http://java.sun.com/docs/books/jls/"), third edition has an example on page 415, where the guaranteed execution order in the Java language is described. The example is that the following code sequence *must* lead to the number 12:
```

int b = 9;
b = b + (b = 3);

```

---

### Post by nema.arpit on 2011-01-17
> **c2tarun said:**
> I applied this concept but may be I applied it wrong.
how I applied:
```


x=20
y=35
expression:   x=y++ + x++
valued used:      35        20
now x=55  and y=36
now
expression:y=++y + ++x
values used:   37       56
now x=56   y=56+37=93


but final answer is :(
x=57 and y=94

```

You forgot the x++ after the first expression it seems..
x=20 y=35
x=y++ + x++
=> x=55 then y++=>y=36 and **x++=> x=56**
then y=++y + x++ => y=37[COLOR=Orange](++y)[/COLOR] + 57 [COLOR=Orange](++x)[/COLOR]=94...

---

### Post by worksofcraft on 2011-01-17
> **Zugzwang said:**
> @OP: Did you actually say which programming language you are working with? Someone started to assume C or C++ in this thread, for which, according to the answers, the statement has undefined behaviour.

However, in Java, for example, a language in which your code would also be syntactically valid, the behaviour is, as far as I know, defined.

Very good point, I think Java does indeed **never** have undefined behavior: It was one of their main design criteria for the language I seem to remember and I suspect the syntax is valid in PhP and Javascript and several other C look-a-like derivatives too.

In etymological terms, apparently the pre/post increment/decrement operators stem from the PDP-11 instruction set, where pointers held in registers could be advanced to the next location concurrent with the execution of an instruction, thus saving memory cycles and instruction fetches when iterating over arrays.

The undefined behavior existed there too in that different generations of the PDP-11 had been microcoded to behave differently e.g:
```

     mov (R0)+, R0 ; source, destination 

```
did not guarantee to auto increment register R0 before overwriting it's value with what it had pointed to. OTOH
```

     mov -(R0), R0

```
was not ambiguous and always predecremented the register before fetching the new value...

---

### Post by psusi on 2011-01-17
> **Zugzwang said:**
> I'm not sure if your answer referred to my post, so I can only assume this. The [Java Language Specification]("http://java.sun.com/docs/books/jls/"), third edition has an example on page 415, where the guaranteed execution order in the Java language is described. The example is that the following code sequence *must* lead to the number 12:
```

int b = 9;
b = b + (b = 3);

```

I thought we were taking about C/C++, so things may be different in Java, but the example you give does not make use of pre/post increment/decrement.

---

### Post by Reiger on 2011-01-17
No but the post-increment can be written as:
```

p= 1 + (p = p); //post-increments assigns to variable, then increments variable by 1 and assigns the result to variable.
```

Pre increment works out as:
```

p = (p + 1); // increments variable by one, then assigns the result to variable.

```

---

### Post by Zugzwang on 2011-01-17
> **psusi said:**
> I thought we were taking about C/C++, so things may be different in Java, but the example you give does not make use of pre/post increment/decrement.

The OP never said in this thread which language he refers to. C++ came only into play when worksofcraft wrote something about it. 

The fact that there is no post/pre-increment in the example doesn't really matter much, as the ambiguity that has been referred to in this thread is introduced by the missing store order in C or C++ when having a RHS (right-hand side) expression with side effects on the variable also used in the LHS, which this examples does have. So the same issue applies in the example, only with different operators.

---

### Post by slooksterpsv on 2011-01-17
> **slavik said:**
> Not really ...
z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z

is:
++x - done 3 times, so x = 4
++y - done 3 times, so y = 4
++z - done 2 times, so z = 2

z = 4 + 4 + 2
z = 10

x++ - done 1 time, so x = 5
y++ - done 1 time, so y = 5
z++ - done 1 time, so z = 11

z doesn't = 11, z = 27, why? 

x = 1
y = 1
z = 0

z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z
z =  2  +  1  +  2  +  3  +  3  +  1  +  1  +  3  +  4  +  4  +   2 + 1
(the plus 1 at the end is for the post increment of 1 in the middle)

=D

---

### Post by slavik on 2011-01-19
> **slooksterpsv said:**
> z doesn't = 11, z = 27, why? 

x = 1
y = 1
z = 0

z = ++x + y++ + ++y + ++y + ++x + ++z + z++ + x++ + ++x + ++y + ++z
z =  2  +  1  +  2  +  3  +  3  +  1  +  1  +  3  +  4  +  4  +   2 + 1
(the plus 1 at the end is for the post increment of 1 in the middle)

=D
completely missed it :(, you're right ^^

---

### Post by lisati on 2011-01-19
My head hurts.

---

### Post by slooksterpsv on 2011-01-19
> **slavik said:**
> completely missed it :(, you're right ^^

Wanna know what's sad, I now understand post and pre-increment, in doing that. Before I loosely understood it, but now that makes complete sense after doing that.

---

### Post by worksofcraft on 2011-01-19
> **lisati said:**
> My head hurts.


lol

my conclusion is to Stay away from Java where all that malarkey is "defined" behavior... :D

---

### Post by Reiger on 2011-01-19
My conclusion would be better to have this general problem well defined, rather than let the compiler introduce off-by-one errors.

That's something Java gets more or less right: the language, and the bytecode is pretty well defined with little leeway for broken compilers touting their bugs as standards compliant behaviour.

---

### Post by Arndt on 2011-01-19
> **Reiger said:**
> My conclusion would be better to have this general problem well defined, rather than let the compiler introduce off-by-one errors.

That's something Java gets more or less right: the language, and the bytecode is pretty well defined with little leeway for broken compilers touting their bugs as standards compliant behaviour.

Does it seem likely that a compiler bug would happen to affect precisely the undefined cases and no others? If it does, it's not a bug. So what does your statement actually mean?

---

### Post by psusi on 2011-01-19
> **Arndt said:**
> Does it seem likely that a compiler bug would happen to affect precisely the undefined cases and no others? If it does, it's not a bug. So what does your statement actually mean?

Indeed.  It is left undefined exactly so that whichever way a compiler goes it is not a bug.  This was done for cross platform compatibility as well as allowing room for optimization.  This is also why integer overflow in C/C++ does not throw an exception like in Java: most CPUs don't support it at the hardware level, so detecting it and raising an exception is very expensive.

---

### Post by psusi on 2011-01-19
> **Arndt said:**
> Does it seem likely that a compiler bug would happen to affect precisely the undefined cases and no others? If it does, it's not a bug. So what does your statement actually mean?

Indeed.  It is left undefined exactly so that whichever way a compiler goes it is not a bug.  This was done for cross platform compatibility as well as allowing room for optimization.  This is also why integer overflow in C/C++ does not throw an exception like in Java: most CPUs don't support it at the hardware level, so detecting it and raising an exception is very expensive.

---

### Post by Rizado on 2011-01-19
> **Reiger said:**
> My conclusion would be better to have this general problem well defined, rather than let the compiler introduce off-by-one errors.

That's something Java gets more or less right: the language, and the bytecode is pretty well defined with little leeway for broken compilers touting their bugs as standards compliant behaviour.There's no one that would actually use something as stupid as this for real so no, having this well defined would only add unnecessary complexity. Which leads to bugs.

---

### Post by trent.josephsen on 2011-01-19
> **Rizado said:**
> There's no one that would actually use something as stupid as this for real so no, having this well defined would only add unnecessary complexity. Which leads to bugs.
I'm with you.  Anybody who writes 'y = ++y' or any variation deserves to have demons fly out of their nose.

---

