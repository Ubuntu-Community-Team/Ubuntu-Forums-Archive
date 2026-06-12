---
title: "C prog. nested loops?"
date: 2007-09-08
forum: Programming Talk
---

### Post by caoinan on 2007-09-08
I didnt really feel like I should post in this section because I'm just learning to program C on my own from C Primer Plus but i'm stuck on one of these exercises in chapter 6 question 2.  ok here is the exercise

> 2. Use nested loops to produce the following pattern:

$
$$
$$$
$$$$
$$$$$

------------------------------------------------
so I am suppose to create this using a for loop I'm pretty sure so if u can explain this to me with out giving me the answer I would really appreciate it and if you could explain it without giving me things that dont come until later chapters i'd appreciate it

---

### Post by dwhitney67 on 2007-09-08
```
#include <stdio.h>

int main()
{
  int i, j;
  for ( i = 0; i < 5; ++i )
  {
    for ( j = 0; j < i+1; ++j )
    {
      printf( "$" );
    }
    printf( "\n" );
  }
}
```


I can't believe you are already "cheating" on what appears to be a first assignment!

Here's the explanation:  The outer loop increments the variable i by 1 each time it loops, for 5 loops, and just at the end of the loop prints a carriage return.  The interior loop is the one responsible for printing the $ character(s).  It prints a number of $ character(s) equal the number of times the outer for-loop has been executed.  I hope this makes sense.

---

### Post by caoinan on 2007-09-08
I am not cheating I didn't want the answer I wanted someone to explain how to do it. He didnt explain well enough(at least to me) what I need to do to make a specific number of rows and have things and a specific part of the row.  I'm not going to look at the answer you posted unless I really really have to. I would rather someone explain how to make a specifc number of columns and rows and place things in a specific spot. and yes that does make sense
ps  I dont cheat I'm trying to learn it  and I didnt ask for the answer

---

### Post by dwhitney67 on 2007-09-08
> **caoinan said:**
> I am not cheating I didn't want the answer I wanted someone to explain how to do it. He didnt explain well enough(at least to me) what I need to do to make a specific number of rows and have things and a specific part of the row.  I'm not going to look at the answer you posted unless I really really have to. I would rather someone explain how to make a specifc number of columns and rows and place things in a specific spot. and yes that does make since
ps  I dont cheat I'm trying to learn it  and I didnt ask for the answer

I edited my post with an explanation of the "algorithm".  Please let me know if you still have any questions.

---

### Post by caoinan on 2007-09-08
thank you I after looking how you did it I realized I was trying to make it harder than what it was. could you explain how do i put things like letters from the alphabet in a specific spot in a column or row. I seem to be having trouble understanding nested loops in that way  so without straight up giving me the answer how would I make a pyramid out of letters. I'm really not trying to just get the answer I just needed a more in depth explanation then the one given in the book which was only like 1 page

---

### Post by lisati on 2007-09-08
> **caoinan said:**
> thank you I after looking how you did it I realized I was trying to make it harder than what it was. could you explain how do i put things like letters from the alphabet in a specific spot in a column or row. I seem to be having trouble understanding nested loops in that way  so without straight up giving me the answer how would I make a pyramid out of letters. I'm really not trying to just get the answer I just needed a more in depth explanation then the one given in the book which was only like 1 page

I haven't seen the book or the explanation it has, but I'll give it a go.
For a pyramid of letters, the outer loop would control the number of lines. I'd probably tackle the details of the lines within the pyramid in two stages - (1) getting to the right place on the line, and (2) getting the data out there. Here's a hint for part 1: the computer able to distinguish between "nothing" and "whitespace" (the blank part before the data). Whitespace is commonly "filled" with a number of "spaces" that you can work out beforehand.

---

### Post by caoinan on 2007-09-08
and could you explain this part a little more
```
for(row = 0; row < i+1; row++)
```
I know how the loops work just an explanation of what makes it stop when it does i guess

---

### Post by lisati on 2007-09-08
> **caoinan said:**
> and could you explain this part a little more
```
for(row = 0; row < i+1; row++)
```
I know how the loops work just an explanation of what makes it stop when it does i guess

Presumably the code is for the inner loop. This loop depends on whatever is in "i" to stop - it works out what "i+1" is each time through and compares "row" with it in order to decide when to stop.

---

### Post by samjh on 2007-09-08
```
for ( i = 0; i < 5; ++i )
```This loop controls the number of rows to be printed.  So it prints from row 0 to row 4:

row 0
row 1
row 2
row 3
row 4

That's five rows, fulfilling the i=0 and i < 5 constraints.

```
for(row = 0; row < i+1; row++)
```This loop controls the number of $ printed for each row.

For every row, it adds 1 to the row number, and prints that value of $s.  So it the loop is in row 0, it wlll print 0 + 1 number of $s, which is just one $.  If the loop is in row 1, it will print 1 + 1, which is $$.  In row 3, it will print $$$, and so on.

To summarise with a diagram:

When i = 0, print 0 + 1 = $
When i = 1, print 1 + 1 = $$
When i = 2, print 2 + 1 = $$$
When i = 3, print 3 + 1 = $$$$
When i = 4, print 4 + 1 = $$$$$

---

### Post by caoinan on 2007-09-08
ok thank for explaining that part for me I finally get it now. if you could explain in pseudocode what to do for this question with a small explanation (use comments to make it easier for me)
> 
4.  Have a program request a user to enter an uppercase letter. Use nested loops to produce a pattern like this:

           A
        ABA
     ABCBA
  ABCDCDA
ABCDEDCBA

The pattern should extend to the character entered. For example, the preceding pattern would result from an input of E...

this is supposed to be a pyramid


I'm really not trying to get the answer but I know thats what it looks like I'm just trying to understand how to use the nested for loops to produce the output I want

---

### Post by slavik on 2007-09-08
it's same as nested loops except you need 2 loops instead of 1 to control the pattern.

on the question of how to produce the letters, look at the ascii table (note the characters and the numbers)

---

### Post by dwhitney67 on 2007-09-08
One way to think of the solution to your last post is use the analogy of a wave coming in and then turning around to go back out.

Thus for each row, count up to the row number + 1 for each character that needs to be printed, and then count back down to zero and continue printing the same characters, but in reverse order.

```
#include <stdio.h>

int main()
{
  int MaxRows = 5;
  int i, j;

  for ( i = 0; i < MaxRows; ++i )
  {
    char lastChar = 'A';

    // tide comes in
    for ( j = 0; j < i + 1; ++j )
    {
      printf( "%c", lastChar++ );   // print lastChar, then increment its value
    }

    --lastChar;  // back off lastChar by one before entering next loop

    // tide goes out
    for ( j = i; j > 0; --j )
    {
      printf( "%c", --lastChar );   // decrement lastChar, then print its value
    }

    printf( "\n" );
  }
}

```

---

### Post by pmasiar on 2007-09-09
> **caoinan said:**
>  I'm just learning to program C on my own

many people will sneer at me for promoting Python again, but my honest opinion is that Python is better (easier and simpler to learn) as a first programming language than C, especially for self-learner. It is easier to grasp basic concepts in python, and then to use then in other languages - in many cases it is just syntax differences.

Of course you are free to learn C if you like it more, I just wanted to inform you about my professional opinion.

---

### Post by dwhitney67 on 2007-09-09
> **pmasiar said:**
> many people will sneer at me for promoting Python again, but my honest opinion is that Python is better (easier and simpler to learn) as a first programming language than C, especially for self-learner. It is easier to grasp basic concepts in python, and then to use then in other languages - in many cases it is just syntax differences.

Of course you are free to learn C if you like it more, I just wanted to inform you about my professional opinion.

And your opinion is valued very much!

Questions.... Can I use Python in an embedded system?  Can it access registers and manipulate bits of data?  Can one develop multi-threaded applications with it?  Can it handle polymorphism like in C++?  Does Python provide a cross-compiler that would allow one to develop applications on one platform (e.g. Intel), yet run it on another (e.g. PPC)? 

Please don't see this as an attack on your post.  I only ask these questions because I have never learned, much less seen any Python code, and since you value yourself as a professional Python developer, perhaps you could enlighten the Ubuntu forum with your wisdom.

---

### Post by andyrobo60 on 2007-09-09
Do we have to go into a big Python Vs C debate? I know this is the Ubuntu forum and that means that most people think Python is great. I like Python as well but this is a topic on C and nested loops, it has nothing to do with python.

---

### Post by dwhitney67 on 2007-09-09
> **andyrobo60 said:**
> Do we have to go into a big Python Vs C debate? I know this is the Ubuntu forum and that means that most people think Python is great. I like Python as well but this is a topic on C and nested loops, it has nothing to do with python.
Yours is probably the Politically Correct post.  My post was merely seeking a "no" answer from the Python supporter.  I guess he/she felt too intimidated to respond.

C (and C++) have its place in this world.  Python maybe has its own as well, as does Perl and other shell scripts, Java, etc.  But not all are usable in every conceivable environment.

This thread begun with a question concerning C programming and hopefully it will end with a discussion of such.

[PHP]# include <stdio.h>

int main( int argc, char** argv )
{
  int i;

  for ( i = 99; i > 0; --i )
  {
    printf( "%d bottles of beer on the wall, "
            "%d bottles of beer! Take one down, pass it around. ", i, i );

    if ( i > 1 )
    {
      printf( "%d bottles of beer on the wall.\n", i-1 );
    }
    else
    {
      printf( "%d bottle of beer on the wall.\n", i-1 );
      printf( "Damn, I thought Ubuntu Beer would get me drunk.\n");
    }
  }
}[/PHP]

---

### Post by CptPicard on 2007-09-09
> **dwhitney67 said:**
> Yours is probably the Politically Correct post.  My post was merely seeking a "no" answer from the Python supporter.  I guess he/she felt too intimidated to respond.

I have grown to respect pmasiar quite a lot as a poster, so I shouldn't steal him his right to very much show you you shouldn't assume he's easily intimidated, but here we go.. ;)

> Questions.... Can I use Python in an embedded system?

I wouldn't be surprised, a lot of embedded machines have VMs these days.

> Can it access registers and manipulate bits of data?

Of course it's got bit operations. On the other hand, I wouldn't worry about accessing registers if I were the OP.

(EDIT: and it's pretty easy to link a module that does, if you really need to, for some reason)

> Can one develop multi-threaded applications with it?

Yes. Pretty much all half-decent platforms these days have threading built in.

> Can it handle polymorphism like in C++?

Yes, but because it's a dynamically typed language, "handling polymorphism like C++" is bit like comparing apples to oranges...

> Does Python provide a cross-compiler that would allow one to develop applications on one platform (e.g. Intel), yet run it on another (e.g. PPC)?

Python is cross-platform in itself, you don't need a cross-compiler.

> C (and C++) have its place in this world.  Python maybe has its own as well, as does Perl and other shell scripts, Java, etc.  But not all are usable in every conceivable environment.

I'd like to remind you that the OP is someone who has trouble grasping *nested loops*, for chrissakes. He's not going to care about down to the hardware low level access any time soon, if ever -- most programmers are more productive in higher-level environments anyway.

I'd say for the OP, the Python suggestion is very much in place...

---

### Post by Lster on 2007-09-09
Python isn't perfect: 

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=python](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=python)

I'm not saying Python sucks (infact I think it is a very elegant language), just that it isn't perfect.

> I'd like to remind you that the OP is someone who has trouble grasping nested loops, for chrissakes.

It took me weeks to understand iteration and recursion. Now, in some of my program I have 10s of levels of iteration and recursion - I think the concept is quite abstract.

---

### Post by CptPicard on 2007-09-09
> **Lster said:**
> Python isn't perfect: 

No language is perfect, and I am not going to even argue from such a strawman position. Pmasiar might try to, I suppose ;)

For a complete n00b, Python is a better start than C. Although I'm willing to admit that changing languages is not going to make the concept of nested loops any less difficult, especially with the criticisms I have had of Python's for loop being expressed in terms of a special iterable structure. But that's just because I like the C-style loop, especially when they are nested :) Python's nested whiles just need more rows of code, but they just *might* be easier for him to understand, I don't know...

> It took me weeks to understand iteration and recursion. Now, in some of my program I have 10s of levels of iteration and recursion - I think the concept is quite abstract.

I hope you do organize your code and don't just dump 10s of levels of iteration in one function though ;)

I never understood why recursion is supposedly so tough. I mean, once you accept the idea of a function call, why not call the same function you're in :)

But anyway, I am by no means suggesting the OP is somehow intellectually inferior because of his question, I fully understand he has met one of the first challenging concepts in programming. And that's why, because of his level of experience, pmasiar is correct suggesting he might benefit more of a more straightforward language to begin with.

Anyway, in order to actually contribute something to the OP's question, I don't think anyone has really pointed out something about the for loop... the general structure:

The for loop contains three major parts: *initialization, condition and step*. Initialization is run before the loop is entered, the loop runs until condition is false, and after each iteration through the loop, "step" is executed. So:

```

for (initialization; condition; step)

becomes for example

for (int i = 0; i < 10; i++)

```

You initialize i to 10, run until i is no longer < 10, and after each iteration increment i by one. The basic structure can be modified to suit your needs. Nested loops really are nothing fancy: the inside loop is simply executed all the way through for each iteration of the outside loop, and the outside loop's variables give the inner loop the state it executes within. So you can for example use the outer loop's index variable inside the condition of the inside loop, like is done in these examples we're looking at.

---

### Post by Lster on 2007-09-09
> For a complete n00b, Python is a better start than C.

I would definitely agree on that. :)

---

### Post by pmasiar on 2007-09-09
> **dwhitney67 said:**
> Can I use Python in an embedded system?  Can it access registers and manipulate bits of data?  Can one develop multi-threaded applications with it?  Can it handle polymorphism like in C++?  Does Python provide a cross-compiler that would allow one to develop applications on one platform (e.g. Intel), yet run it on another (e.g. PPC)?

no, no, no, yes, no :-)

I am not expert on polymorphism in neither C++ or Python, but Python does have multiple inheritance, introspection and stuff. If you need qualified answer, you need to ask **real** Python gurus at Python mailing list. 

There are libraries for threads, I suspect less effective as C one. Someone will work on that after Py3K release :-)

Cross-platform: it depends on your definition of cross-platform. Python relies on libraries, and uses C libraries, so if library is available, it should be doable.

> Please don't see this as an attack on your post

No, your questions are valid. Sorry I did not answered earlier, I was sleeping :-)

My suggestion was to learn walk with Python before you try run with C or C++.

BTW I will be suggesting Python to other struggling beginners, but I will try to be more exact to aviod these flamewars. I like C, I used it before, it is just too low-level for me, and for any beginner, in my honest opinion.

---

### Post by slavik on 2007-09-09
> **pmasiar said:**
> no, no, no, yes, no :-)

I am not expert on polymorphism in neither C++ or Python, but Python does have multiple inheritance, introspection and stuff. If you need qualified answer, you need to ask **real** Python gurus at Python mailing list. 

There are libraries for threads, I suspect less effective as C one. Someone will work on that after Py3K release :-)

Cross-platform: it depends on your definition of cross-platform. Python relies on libraries, and uses C libraries, so if library is available, it should be doable.

> Please don't see this as an attack on your post

No, your questions are valid. Sorry I did not answered earlier, I was sleeping :-)

My suggestion was to learn walk with Python before you try run with C or C++.

BTW I will be suggesting Python to other struggling beginners, but I will try to be more exact to aviod these flamewars. I like C, I used it before, it is just too low-level for me, and for any beginner, in my honest opinion.

I am chiming in to tell you that I disagree with you. (but you probably know that already)

---

### Post by pmasiar on 2007-09-09
> **slavik said:**
> I am chiming in to tell you that I disagree with you. (but you probably know that already)
you quoted whole post - which part you disagree? Or you want me to believe that you prefer Python for embedded systems? :-)

---

### Post by caoinan on 2007-09-09
well I didnt really want to switch to another language before I finished the book but i can see everyone's point. I have a book on perl  so what is your opinion of perl as a starting language?

---

### Post by CptPicard on 2007-09-09
Getting back to the point as the language you're using is irrelevant as far as your immediate question goes... how's the looping going?

Don't get into Perl, it's too... "artistic". You'll find all the Python learning material you'll need online.

---

