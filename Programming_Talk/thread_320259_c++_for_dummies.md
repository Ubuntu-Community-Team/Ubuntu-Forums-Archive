---
title: "c++ for dummies???"
date: 2006-12-17
forum: Programming Talk
---

### Post by nite owl on 2006-12-17
Bought this book a couple weeks ago, without checking round the forums to see whether it was worth the money...Having abit of trouble understanding a few of the concepts explained i.e. pointers and arrays....I'm hoping this is just poorly explained in the book lol. Could anyone answer the usual question for me of suggesting some good books/tutorials....preferably ones you could download.

---

### Post by Mike'sHardLinux on 2006-12-17
Hi!

I  also got hung up on pointers. I haven't had time to get back into C++ since then, but I found several resources for learning C++. One free book that seems to get recommended a LOT is "Thinking in C++." It is a book you can buy or you can also download the PDF for free. [http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html]("http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html")

Like I said, I haven't had enough time to get back into trying to learn C++. At this point, I'll probably have to start all over, since it's been a while. If that book helps you, **please** let me know. It might be enough motivation for me to give it another go.

Oh, almost forgot, there is a thread somewhere in these forums about programming resources online.

Good luck!!

---

### Post by maddog39 on 2006-12-17
Pointers and arrays are difficult topics in general. My primary programming language is PHP and PHP barrows like 90% of its syntax from C. So most of it was familiar but I was also stumped when approaching the topic of pointers, learning them for the first time. My advice would be to either, continue in the book and see how they use pointers in later examples, or practice the examples using pointers from that chapter for a while until you fully understand them.

---

### Post by Wybiral on 2006-12-17
Arrays are pretty simple... if I said I had an array that was 2x2 ( int x[2][2] ) then I basically have 4 variables. Kindof like a grid of space to store info.

x[0][0], x[0][1]
x[1][0], x[1][1]

I can use any of the variables as if it were a normal integer.

Single dimension arrays are even easier, they are like a line segment to store into in...

int x[5];

x[0] = 1
x[1] = 2
x[2] = 3
x[3] = 4
x[4] = 5

So...
x[1] + x[3] = 6

The only part that is slightly confusing is that when you define an array with x elements... Since it starts at 0 instead of one, the last array has the index x-1... Which is why x[4] in that example lined up with the 5 that I put in it... I hope this isn't confusing you any more...

---

### Post by maddog39 on 2006-12-17
I have this C++ program that I made from a tutorial somewhere that is a really nice visual tool for showing you how arrays are layed out. I'll post the source when I find it.

---

### Post by nite owl on 2006-12-17
Hi thanks for your replies... :) hopefully theyll help

---

### Post by John E on 2006-12-17
The easiest way to think of a pointer is to think of it as the address of a variable. Why would you want to know the address of a variable? Well, it's a hangover from the days of 'C'. Consider this function:-

```
void SomeFunc ( int var )
{
     var = 10;
}
```
You might think that if you call it like this, **local_var** will end up as 10

```
int local_var = 9;
     SomeFunc( local_var );
```

However, l**ocal_var** will always be 9. That's because C passes variables to functions by making a copy of them. Therefore, **var** is a _copy_ of **local_var**. The expression v**ar = 10;** affects only the copy - not the original variable.

In C, you can get around this by passing _the address_ of **local_var** like so:-

```
void SomeFunc ( int* var )
{
     *var = 10;
}


/// and call it like this:-
int local_var = 9;
     SomeFunc ( &local_var );
```

**int*** means 'pass me the address of a variable, instead of making a copy of it.'
[B]
&local_var[/B] means 'supply the address of **local_var**'.

***var** means 'assign this number to _what var is pointing at_ - not to var itself.

**var** is a pointer, pointing to the address of **local_var**. Therefore, when you alter  "what var is pointing at" you're actually altering l**ocal_var** (**local_var** is the variable being pointed to). Pointers are one of the most difficult things for newbies to understand. C++ has addressed this by using references, instead of pointers. A reference is very similar to a pointer.

Go here:- [http://www.codeguru.com/forum](http://www.codeguru.com/forum) if you want to ask questions about C and C++. It's a great site.

---

### Post by maxamillion on 2006-12-17
It appears that your questions have been well answered by others pertaining to C++, but about the book....

I purchased that book roughly 8 years ago and now looking back, it is a horribly written book and doesn't explain a large number of things very well. I assume they haven't changed the text in publication and if they have it was incremental updates and editing.

Happy coding :)

---

### Post by studiesrule on 2006-12-17
I too faced problems with pointers, mainly because I didn't get what they were for. However, nce I realised how useful they were I got along fine. Also, after I saw how it was done elsewhere I found it easier to grasp.

I think that the common definition you find is generally a good one, i.e. pointers POINT to memory locations. C(++) is a very strict language, in that it never lets you change the type of data type, define new variables whenever you like (actually C++ does let you do that). Pointers help get around most of these obstacles. Languages like Python too have pointers and all, but you don't require to come face to face with them. Infact in python EVERYTHING is an object and has an pointer code. It automatically references variables to common objects to save memory. For example, if you have 
x = 4
4 will be stored as an object with id 124315
x will only POINT to the location of this object. You can't see this, or ever naturally come to know it but thats what it does. Now if you type:
y =4
then y TOO will point to the object 4. So x and y are simply pointing to object locations.

In C++, its very much the same, but you have to make this pointing association very explict, through pointers. References eliminates this.

---

### Post by pmasiar on 2006-12-17
You did not mention what is your previous programming experience. Different books are suited for different audiences: programmer, who is an expert is another language, needs substantially less handholding when learning new language than beginner does. For me it is hard to judge beginner's books , because reading them is waste of my time :-). That said, C++ is *not* a language I would recommend to someone as first language to learn. (As everyone on this forum knows, it would be python :-) )

I have very good experience with O'Reilly books, so my first look always would be what O'Reilly has about the subject.

---

### Post by Horsman on 2006-12-17
I would say the key difference to understanding pointers is understanding the * and & operators in each of their two contexts.

**As a left hand operator (as used on anything that is a declaration and before the = )**

* means "a pointer to"

IE: int * x = new int(9);  "x is a pointer to an int, which has been assigned the address of a new int of size 9 on the stack".

& means "a reference to" but is better thought of as "an alias of"

IE int & x = y; "x is an alias of the variable y" (which we assume has been previously declared) and we can use it just like we would use any other variable. changing x will change y.

x = 5;
x == y; // returns true;

**As a right hand operator (as used on anything after = or where there is no equals)**

* means "dereference" or "give me the value stored at the address of this pointer"

IE int x = *y; "int x equals the value stored at the address of int * y"

& means "give me the address of this value"

IE int * y = &x; "int * y equals the address of teh variable x"



In a way this seems counter intuitive to the programmer. you use * to make a pointer and dereference a pointer, and & to make a reference (alias) and get the address of a variable. The thing is, pointers store addresses, and references (usually) store values, but on the right hand side * makes a value and & makes a reference.

so just remember:

* is the pointer declarator AND a dereferencer.
& is the reference (alias)  declarator AND a "get address of" operator.

](*,)  can now commence.

---

### Post by Horsman on 2006-12-17
> **pmasiar said:**
> You did not mention what is your previous programming experience. Different books are suited for different audiences: programmer, who is an expert is another language, needs substantially less handholding when learning new language than beginner does. For me it is hard to judge beginner's books , because reading them is waste of my time :-). That said, C++ is *not* a language I would recommend to someone as first language to learn. (As everyone on this forum knows, it would be python :-) )

I have very good experience with O'Reilly books, so my first look always would be what O'Reilly has about the subject.

there are two near ubiquitous C++ books:

"The C++ Programming Language" and "C++ Primer"

Both are more or less expert books.

Java is generally the beginning language of choice in computer science schools. Python seems to be what ubuntu users like but is not really the best option for learning (not statically typed and a scripting language). Both are very useful languages in there own right.

---

### Post by Stormx on 2006-12-17
What should I use for compiling C++ in ubuntu? cc? gcc?

---

### Post by Horsman on 2006-12-17
> **Stormx said:**
> What should I use for compiling C++ in ubuntu? cc? gcc?

g++

---

### Post by pmasiar on 2006-12-17
> **Horsman said:**
> Python seems to be what ubuntu users like but is not really the best option for learning (not statically typed and a scripting language). 

LOL!! Translated: **Python will allow you to solve your problems way too fast** - so you will not appreciate all pain and suffering we users of other, statically typed languages with less flexible memory models prefer to endure all day, every day. :-)

**Python is better as first language exactly *because* it eliminates need to learn static typing and memory management** - student can learn it later, if need arises, or decide not to waste time learning it, solving problems at hand instead, if python solution is fast enough.

I understand you learned C++ and can handle all complex types, and you feel you need to prove yourself it was not wasted time. My definition of **best language for a task**  is: language which allows me to learn it fast and solve problem at hand, while solution is fast enough for user, and still easy to maintain and add new features. What is yours definition?

---

### Post by Horsman on 2006-12-17
> **pmasiar said:**
> LOL!! Translated: **Python will allow you to solve your problems way too fast** - so you will not appreciate all pain and suffering we users of other, statically typed languages with less flexible memory models prefer to endure all day, every day. :-)

**Python is better as first language exactly *because* it eliminates need to learn static typing and memory management** - student can learn it later, if need arises, or decide not to waste time learning it, solving problems at hand instead, if python solution is fast enough.

I understand you learned C++ and can handle all complex types, and you feel you need to prove yourself it was not wasted time. My definition of **best language for a task**  is: language which allows me to learn it fast and solve problem at hand, while solution is fast enough for user, and still easy to maintain and add new features. What is yours definition?

It's very admirable that you like python and I like it to. Some of the points you raised are valid. This person is learning to be a programmer, not just doing a task (programming). You start off and python and you will likely be completely lost if you branch out into any other non scripting language. Python is also one of the slowest languages around. I'm not saying that someone should learn memory management in their first language, but they should start with programming languages and then move on to scripting languages, especially if they want to be a career programmer or are interested in working on anyone else's code. Learning python does not translate very well to other languages, but many other languages translate well to python.

so in summary I feel the difference in opinion varies with the goal of the individual:
-If one wants to produce a working program as fast as possible, and easily maintain and add to it, choose a very high level language like python, perl or ruby.

-If one want to learn to be a programmer, and learn knowledge from the start that will be applied in nearly every other language out there, including those tasks noted above, choose Java, C++, or C# (I would recommend java, its somewhat in between).

Python seems to be ubiquitous in ubuntu, but it is not even a scratch on the surface if you look at the most commonly used languages by software teams worldwide.

---

### Post by pmasiar on 2006-12-17
> **Horsman said:**
> You start off and python and you will likely be completely lost if you branch out into any other non scripting language.  

Why learner would be lost? Expert python programmer is fluent with variable scopes, subroutines, loops, modules, libraries, exceptions, objects, polymorfism,  method decorators etc (all present in python). Java lacks some of the concepts which python allows, like multiple inheritance and operator overloading, although your note would suggest opposite. Also, python's typing is strict: unlike perl, python does not convert string value to number or vice versa. Typing is just dynamic - not resolved at compile time, thats most of the difference.

My argument is: **by learning python programmer can learn *all* important programming concepts, with least amount of unnecessary pain and frustration**. Am I missing some concepts? I learned many languages (started with Algol 60 and 68, PL/1, couple of assemblers, and FORTH).

>  Python is also one of the slowest languages around. 

While I would not argue python is faster in execution than C/C++ or Java, looking at [results of debian language shootout]("http://shootout.alioth.debian.org/") python is often *faster* than other popular scripting dynamically typed languages. So it is just your opinion, or you have some facts to support it? Or maybe it depends what languages are allowed to "be around". :-)

> I'm not saying that someone should learn memory management in their first language, but they should start with programming languages and then move on to scripting languages, especially if they want to be a career programmer or are interested in working on anyone else's code. Learning python does not translate very well to other languages, but many other languages translate well to python.

so in summary I feel the difference in opinion varies with the goal of the individual:
-If one wants to produce a working program as fast as possible, and easily maintain and add to it, choose a very high level language like python, perl or ruby.

-If one want to learn to be a programmer, and learn knowledge from the start that will be applied in nearly every other language out there, including those tasks noted above, choose Java, C++, or C# (I would recommend java, its somewhat in between).

As I mentioned, if programmer learns python she will learn most advanced concept which java has, and some which java lacks: ie. operator overloading, and multiple inheritance. Except static typing and static exception management of course. Are these concepts cornerstone of programming?

> Python seems to be ubiquitous in ubuntu, but it is not even a scratch on the surface if you look at the most commonly used languages by software teams worldwide.

Teams in Google, YouTube, NASA, Industrial Light & Magic etc use python as you can see from these [quotes]("http://www.python.org/about/quotes/") and [success stories]("http://www.python.org/about/success/"). So it looks like is not *most* commonly used language - but is **commonly used by the most succesfull** ones :-P

---

### Post by utab on 2006-12-17
Accelerated C++ and C++ Primer for the 1st time

---

### Post by Wybiral on 2006-12-17
Python and C++ are similar, while being very different... But this post has nothing to do with python! (Although I enjoy both C++ and python a lot)

Another thing about pointers is speed... Since they simply "point to" the actual object by storing it's address, they only contain an integer address, so if you need to pass a large object to a function like a very large class for instance, passing the pointer to the function is A LOT faster because it does not have to copy the entire class object, it just passes the pointer. I hope that makes sense... Then you can still use that class object in the function by using the pointer (which simply tells C++ where the actual object is, C++ handles the rest).

---

