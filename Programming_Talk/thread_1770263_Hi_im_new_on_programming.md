---
title: "Hi im new on programming"
date: 2011-05-29
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-05-29
Ok so i fell in love with programming stuff.

Im using NetBeans IDE wich is very cool but i have some doubts.

I was willing to learn C++, but...
I hear its too hard and also its very bad designed and may i ask:

Is there a lenguage as powerfull as C++ and at the same time multiplatform and already installed in most systems and of course Easy to learn. 

I hear Python was one but it have to be installed on windows so not so usefull to test on moms pc or ma friends pc,s to show them my advance...

we enjoy this subjects but they dont use linux thouhg i love it..

So is there an alternative.....

And if there isnt one i wanna ask if an executable for windows/linux  file could be created even if it just outputs a msg.

---

### Post by Smart Viking on 2011-05-29
I would recommend Python as a starting language. It is not too hard to install Python in windows.

The syntax of Python is very clear and feels very natural when you get into it.

Here is a great book for beginner programmers:
[http://greenteapress.com/thinkpython/thinkpython.html](http://greenteapress.com/thinkpython/thinkpython.html)

EDIT: I would recommend to not use an IDE that does code _for_ you if you are a beginner, preferably, just use a normal text editor like Gedit, Vim, Emacs or Nano.

---

### Post by ThatCoolGuy220 on 2011-05-29
Thx Bro i will read...

OFF:
nice signature..

---

### Post by lavinog on 2011-05-29
If you want to avoid having to install python on windows, you can use a tool such as py2exe [http://www.py2exe.org/](http://www.py2exe.org/)

---

### Post by ThatCoolGuy220 on 2011-05-29
Ok im using python but IDK wich IDE would be good.

I used eclipse but it tells me to get psyco debug... i installed it but idk how to integrate it

---

### Post by ziekfiguur on 2011-05-29
Like Smart Viking said, if you are a beginner it's probably best not to use any IDE but just a text editor like gedit and a terminal.
If you insist on using an IDE anyway Geany is a good choice.

---

### Post by cgroza on 2011-05-29
> **ziekfiguur said:**
> Like Smart Viking said, if you are a beginner it's probably best not to use any IDE but just a text editor like gedit and a terminal.
If you insist on using an IDE anyway Geany is a good choice.
Geany is not really an IDE. It is just a little more advanced text editor as it does not provide great integration with compilers, debuggers, etc...
I started programming using it and have no regrets.

---

### Post by ThatCoolGuy220 on 2011-05-29
allrite

---

### Post by ThatCoolGuy220 on 2011-05-29
Yep Geany is good it makes an executable fiel withouth hastle only think is IDK how to run it.

Its the tipaically "Hello World" aplication 

i Double click it and it doesnt open LOL well unless its there

---

### Post by Petrolea on 2011-06-01
> **ThatCoolGuy220 said:**
> Yep Geany is good it makes an executable fiel withouth hastle only think is IDK how to run it.

Its the tipaically "Hello World" aplication 

i Double click it and it doesnt open LOL well unless its there

You have 'Run' option in Geany also. It won't run by itself that way, you need terminal emulator or simply run it in terminal with ./your_app.

---

### Post by zobayer1 on 2011-06-01
But, after a while, when you become a coder junkie... u will understand, nothing beats VIM

---

### Post by juancarlospaco on 2011-06-01
> **ThatCoolGuy220 said:**
> Ok im using python but IDK wich IDE would be good.


**[http://ninja-ide.org/](http://ninja-ide.org/)**

---

### Post by lavinog on 2011-06-02
> **juancarlospaco said:**
> **[http://ninja-ide.org/](http://ninja-ide.org/)**

Looks nice, trying out right now.

also, vim or any text based editor is nice to for coding over ssh.

---

### Post by ThatCoolGuy220 on 2011-06-02
very interesting though now i decided to go c++ then python, step by step

---

### Post by zobayer1 on 2011-06-02
> **ThatCoolGuy220 said:**
> very interesting though now i decided to go c++ then python, step by step

I think this is the best way, i.e. first to learn C/C++ then any other language.

---

### Post by Petrolea on 2011-06-02
> **zobayer1 said:**
> I think this is the best way, i.e. first to learn C/C++ then any other language.

Must agree, it will give you a better understanding of variables and functions. Doing it in a reverse way would be harder.

---

### Post by CptPicard on 2011-06-02
> **Petrolea said:**
> Must agree, it will give you a better understanding of variables and functions. Doing it in a reverse way would be harder.

How do C and C++ give a better understanding of *functions and variables* than, say, Python? On those counts, the two work very much the same...

---

### Post by Petrolea on 2011-06-02
> **CptPicard said:**
> How do C and C++ give a better understanding of *functions and variables* than, say, Python? On those counts, the two work very much the same...

I didn't compare it directly to Python, but some programming languages use same declaration for all data types. In C you can't compare char '5' to int 5 and get TRUE as return. In some toher languages you can. 

In ruby you can even multiply strings by numbers, for example "Ubuntu" * 5, which would print Ubuntu 5 times. In C something like that won't work - that's why you get better understanding of variables - you see WHY it won't work, what's the difference between String and Integer and char and array of ints and chars. 

Also functions in programming language like PHP don't need to be declared as int to return int. You just use function something() for any type of function. That's where C comes and tells you it isn't the same thing when declaring a void or int function and that int must return something of type int.

After you understand these things it is way easier to get used to "easier" declarations. The other way around is harder.

---

### Post by simeon87 on 2011-06-02
> **Petrolea said:**
> I didn't compare it directly to Python, but some programming languages use same declaration for all data types. In C you can't compare char '5' to int 5 and get TRUE as return. In some toher languages you can. 

In ruby you can even multiply strings by numbers, for example "Ubuntu" * 5, which would print Ubuntu 5 times. In C something like that won't work - that's why you get better understanding of variables - you see WHY it won't work, what's the difference between String and Integer and char and array of ints and chars. 

Also functions in programming language like PHP don't need to be declared as int to return int. You just use function something() for any type of function. That's where C comes and tells you it isn't the same thing when declaring a void or int function and that int must return something of type int.

After you understand these things it is way easier to get used to "easier" declarations. The other way around is harder.

The same can also be argued in the opposite direction. The general concept is that a function computes something and it can, optionally, return a value. When you understand that

```
def f(args):
    a = 3
    return a
```

returns the number 3, why would it be harder to learn that in C, you have to explicitly write int a = 3; and add int to the function header?

It's indeed true that you can do some funky stuff in Python due to dynamic typing but I'm not necessarily convinced that moving to a language such as C would be harder as a result of that. For example, multiplying a string with a variable ("Ubuntu" * 5) won't work in C but that's mainly because C focuses on variables being pieces of memory and operators perform work on that. This is a language decision but not necessarily a better one for teaching / learning the principles of programming. The laborious work of allocating, declaring and moving memory around in C is then relatively easy to learn afterwards.

---

### Post by Petrolea on 2011-06-02
> **simeon87 said:**
> The same can also be argued in the opposite direction. The general concept is that a function computes something and it can, optionally, return a value. When you understand that

```
def f(args):
    a = 3
    return a
```

returns the number 3, why would it be harder to learn that in C, you have to explicitly write int a = 3; and add int to the function header?

It's indeed true that you can do some funky stuff in Python due to dynamic typing but I'm not necessarily convinced that moving to a language such as C would be harder as a result of that. For example, multiplying a string with a variable ("Ubuntu" * 5) won't work in C but that's mainly because C focuses on variables being pieces of memory and operators perform work on that. This is a language decision but not necessarily a better one for teaching / learning the principles of programming. The laborious work of allocating, declaring and moving memory around in C is then relatively easy to learn afterwards.

Well, nevermind, I didn't want to make a big discussion here. But I think you get the point. C gives you way more options and is harder, some other languages are easier and give less options. Now choose whatever fits you more.

---

### Post by ThatCoolGuy220 on 2011-06-02
LOL i did it

---

### Post by zobayer1 on 2011-06-02
> **CptPicard said:**
> How do C and C++ give a better understanding of *functions and variables* than, say, Python? On those counts, the two work very much the same...

In a python program, you dont really need to know the internal structures, say u can multiply two 100 digits number with a simple *, which is not directly done by computer (infact, core of python is built with c). In C program, you have to be careful about many things which depends on your machine, and also, you will know better how things works... 

python type language gives you waaaaay tooooo much abstraction (I mean to a beginner). say, you can say, it is a limitation of c that it gives wrong result if you do 2147483647 + 1, but I would say no, it is your machine how it handles calculations. so, for beginners, python is good, but a language with such a great level of abstraction can never be real programmers choice :p (dont get mad on me if you dont agree with me)

---

### Post by simeon87 on 2011-06-02
> **zobayer1 said:**
> In a python program, you dont really need to know the internal structures, say u can multiply two 100 digits number with a simple *, which is not directly done by computer (infact, core of python is built with c). In C program, you have to be careful about many things which depends on your machine, and also, you will know better how things works... 

python type language gives you waaaaay tooooo much abstraction (I mean to a beginner). say, you can say, it is a limitation of c that it gives wrong result if you do 2147483647 + 1, but I would say no, it is your machine how it handles calculations. so, for beginners, python is good, but a language with such a great level of abstraction can never be real programmers choice :p (dont get mad on me if you dont agree with me)

The idea that Python is not for "real programmers" is similar to the idea that lives among novice programmers who think that they must learn C++ to be considered a programmer.

> **Petrolea said:**
> Well, nevermind, I didn't want to make a big discussion here. But I think you get the point. C gives you way more options and is harder, some other languages are easier and give less options. Now choose whatever fits you more.

C actually has less features to learn than a language such as Python. I don't intend to make it a big discussion either; the languages are useful in their own right, for different projects.

---

### Post by zobayer1 on 2011-06-02
It makes me sad that people here seem like, C is so hard to start with, and you might break your keyboard to write codes in C/C++, I started with C/C++ and never found it hard so far, like thousands and thousands of other people. And just take a look to the algorithmic problem solving world, you will find out how poor is python in terms of popularity, may be it is good for "boring" software development, but never an exciting language. A simple array initialization in python beats the heck out of the programmer, try to solve a flow network problem in python, or try to find some dynamic programming problem's solution...

Obviously the point is, algorithms and problems are independent from languages, and you just need to choose the language that suits you best. But, I believe, beginning must not be with abstraction. (not that directly machine level either) thats why, a mid level language like C is always my choice. It has flexibility of both high level and mid level, so you can switch to any side easily... thats my point of favoring C++

---

### Post by zobayer1 on 2011-06-02
> **simeon87 said:**
> The idea that Python is not for "real programmers" is similar to the idea that lives among novice programmers who think that they must learn C++ to be considered a programmer.



C actually has less features to learn than a language such as Python. I don't intend to make it a big discussion either; the languages are useful in their own right, for different projects.

Well they are rather wrong, why would someone need to learn a specific language to be considered as a programmer? that's a mis-concept...

---

### Post by Petrolea on 2011-06-02
> **zobayer1 said:**
> It makes me sad that people here seem like, C is so hard to start with, and you might break your keyboard to write codes in C/C++, I started with C/C++ and never found it hard so far, like thousands and thousands of other people. And just take a look to the algorithmic problem solving world, you will find out how poor is python in terms of popularity, may be it is good for "boring" software development, but never an exciting language. A simple array initialization in python beats the heck out of the programmer, try to solve a flow network problem in python, or try to find some dynamic programming problem's solution...

Obviously the point is, algorithms and problems are independent from languages, and you just need to choose the language that suits you best. But, I believe, beginning must not be with abstraction. (not that directly machine level either) thats why, a mid level language like C is always my choice. It has flexibility of both high level and mid level, so you can switch to any side easily... thats my point of favoring C++

Discussions like that don't have an end, so lets just answer OP. 

If you want to learn it then learn it. It isn't too hard. Too hard would be if you'd start with pointers and structures right away. C++ is good, so are other programming languages mentioned here. Every programming language is good in its own way. You'll soon discover which one fits you the most.

---

### Post by simeon87 on 2011-06-02
> **zobayer1 said:**
> It makes me sad that people here seem like, C is so hard to start with, and you might break your keyboard to write codes in C/C++, I started with C/C++ and never found it hard so far, like thousands and thousands of other people. And just take a look to the algorithmic problem solving world, you will find out how poor is python in terms of popularity, may be it is good for "boring" software development, but never an exciting language. A simple array initialization in python beats the heck out of the programmer, try to solve a flow network problem in python, or try to find some dynamic programming problem's solution...

I didn't say C was hard, I would just recommend Python as a language to learn the principles of programming. Furthermore, a beginner isn't going to implement those examples, they're more likely to create a basic application, website or game that they can play with. If you're ready for more complex programming tasks, you're also ready to choose a different language if that suits your problem better.

You may not agree but the whole reason we still need the level of abstraction of C is because computers aren't fast enough to do everything in Python. We like programming but if our computers are fast enough, I can just solve many problems by iterating over possible objects and do whatever we want:

```
for p in planets:
     do_complex_mathematical_calculations(p)
```

Indeed, for many desktop applications and websites the higher level of abstraction of Python is good enough. Why would I have to deal with all those memory issues if I want a Tetris game in 2011?

More and more problems will cross the boundary of "needs C for speed" to "can be done in Python nowadays". Currently, we need all the computing power we can get for complex simulations so C is still very valuable to make the most of our machines. But that's far beyond what a beginning programmer needs to deal with.

---

### Post by zobayer1 on 2011-06-02
> **Petrolea said:**
> Discussions like that don't have an end, so lets just answer OP. 

If you want to learn it then learn it. It isn't too hard. Too hard would be if you'd start with pointers and structures right away. C++ is good, so are other programming languages mentioned here. Every programming language is good in its own way. You'll soon discover which one fits you the most.

Those are a bit hard to get for the first time, I must admit.. but anyone will agree with me about the flexibility they offer... well, python and java doesn;t offer those may be because of security risks... If I am not wrong.

I learnt C++ 3 years ago, then I've learnt Java and Python. I use python every now and then for quick calculations, small programs and such... But I miss pointers in both python and java :( I dont like java much because of its too much oop mumbo jumbo...

---

### Post by ThatCoolGuy220 on 2011-06-02
Lol though is marked as solved posts like this never end and I go for C++ cause I like it not cause I think its better..

---

### Post by CptPicard on 2011-06-02
> **Petrolea said:**
> In C you can't compare char '5' to int 5 and get TRUE as return. In some toher languages you can. 

Yes, for example in Javascript. Weak typing is generally considered a Bad Thing, and I am in agreement on that count. Most dynamic-typed languages are still strongly typed in the sense that at runtime, things do have a type, although you're not being explicit about it when writing your code.

> 
In ruby you can even multiply strings by numbers, for example "Ubuntu" * 5, which would print Ubuntu 5 times. In C something like that won't work - that's why you get better understanding of variables - you see WHY it won't work, what's the difference between String and Integer and char and array of ints and chars. 

In Ruby you still get a runtime error for genuine type mismatches even though you are not spelling the types out for the compiler to check beforehand. For the 5 * "Ubuntu" case... well, that just teaches you that the * operator is a function that can be defined for N-times repetition.

> 
Also functions in programming language like PHP don't need to be declared as int to return int. You just use function something() for any type of function. That's where C comes and tells you it isn't the same thing when declaring a void or int function and that int must return something of type int.

Why is this somehow inherently better? It's just a feature of statically-typed languages. The static vs. dynamic typing debate is a whole can of worms on its own of course :)

> 
After you understand these things it is way easier to get used to "easier" declarations. The other way around is harder.

Well, I'd simply suggest the learning curve is easier the other way around. For example Java is a good example of a language where static-typed OOP is mandated so strongly that a beginner has a hard time achieving anything before reading through some OOP-patterns book...

Dynamic typing allows for much more flexible "implicit" interfaces to objects ("if it knows how to respond to this, it will") and so on, making it much faster to experiment, and that's one of my favourite ways to learn...

> **Petrolea said:**
> C gives you way more options and is harder, some other languages are easier and give less options.

I think this is pretty much at the core of the disagreement between the high-level vs. low-level language crowds' ideas about languages. In my own view, C is not really "hard", it's just too rudimentary and requires too much grunt work to achieve things, plus it introduces some marginal issues that consume way too much of the programmer's attention (think manual memory management) especially at the start.

I guess the "gives you more options" idea comes from the idea that "you can implement Python in C". Well, I can implement Python in Python and even C in Python, and the only difference is execution speed. So the thinking goes that "if you know what you're doing, you can put the C building blocks together to achieve more than you can by using Python". But one still needs to know what one is doing, and that assumes a lot of the programmer, and my personal feelings about this is that you can get a lot -- most -- of the ideas needed from higher-level languages, and get them faster. I find even my C is informed by stuff I've taken from HLLs.

Higher-level languages give you other kinds of possibilities by having more abstractions built into the language, while being "easier" on many of the the issues of programming that can easily be offloaded to the computer. Those things that can be automated away are pretty much by definition things that are not worthy of a human's attention anyway. HLLs are also not necessarily intellectually "easier" -- I suggest you familiarize yourself with something like continuations, continuation-passing style, trampolining in functional programming, the Y combinator, Haskell's monads...

---

### Post by Petrolea on 2011-06-02
> **CptPicard said:**
> Yes, for example in Javascript. Weak typing is generally considered a Bad Thing, and I am in agreement on that count. Most dynamic-typed languages are still strongly typed in the sense that at runtime, things do have a type, although you're not being explicit about it when writing your code.



In Ruby you still get a runtime error for genuine type mismatches even though you are not spelling the types out for the compiler to check beforehand. For the 5 * "Ubuntu" case... well, that just teaches you that the * operator is a function that can be defined for N-times repetition.



Why is this somehow inherently better? It's just a feature of statically-typed languages. The static vs. dynamic typing debate is a whole can of worms on its own of course :)



Well, I'd simply suggest the learning curve is easier the other way around. For example Java is a good example of a language where static-typed OOP is mandated so strongly that a beginner has a hard time achieving anything before reading through some OOP-patterns book...

Dynamic typing allows for much more flexible "implicit" interfaces to objects ("if it knows how to respond to this, it will") and so on, making it much faster to experiment, and that's one of my favourite ways to learn...



I think this is pretty much at the core of the disagreement between the high-level vs. low-level language crowds' ideas about languages. In my own view, C is not really "hard", it's just too rudimentary and requires too much grunt work to achieve things, plus it introduces some marginal issues that consume way too much of the programmer's attention (think manual memory management) especially at the start.

I guess the "gives you more options" idea comes from the idea that "you can implement Python in C". Well, I can implement Python in Python and even C in Python, and the only difference is execution speed. So the thinking goes that "if you know what you're doing, you can put the C building blocks together to achieve more than you can by using Python". But one still needs to know what one is doing, and that assumes a lot of the programmer, and my personal feelings about this is that you can get a lot -- most -- of the ideas needed from higher-level languages, and get them faster. I find even my C is informed by stuff I've taken from HLLs.

Higher-level languages give you other kinds of possibilities by having more abstractions built into the language, while being "easier" on many of the the issues of programming that can easily be offloaded to the computer. Those things that can be automated away are pretty much by definition things that are not worthy of a human's attention anyway. HLLs are also not necessarily intellectually "easier" -- I suggest you familiarize yourself with something like continuations, continuation-passing style, trampolining in functional programming, the Y combinator, Haskell's monads...

Oh god, responding to this post will take some time. I guess that's where I'd use C :P

Well, my point in it having more options was meant in general. You can't write OS in Python for example (I'm not saying I can do it in C lol). Lets leave this part out, I want to sleep today.

For the Ruby part: Ruby is Ruby. It has simple syntax with which you can achieve things quickly and with nice code (even though it doesn't have native 2D+ array support which really confused me at first) and uses kind-of human logic (put 'Ubuntu' 5 times - it doesn't mean "sum all ASCII values of 'Ubuntu' and multiply by 5" but just prints it 5 times). That's why I like Ruby :) But enough of ruby, it was just there to compare with data types of other languages.

Im not saying that that type of function is bad. I actually like it so I don't have to worry about whether it returns something or not, or whether it returns array of ints or a string. There is no usage in C-kind of functions for a programmer that wants to create Tic-tac-toe game.

You mentioned Java also. Java is totally different from C and other non-OO languages. When I started learning OOP it really was a pain because I came from C++ background with no one even telling me about classes. But I was talking about variables, in Java you don't have to worry about pointers when passing some variables to functions, and in C it is a painful experience. But when you understand C (which can take some time) you will understand variable system in Java also (excluding the OOP part).

So, don't think I'm a C fan because I'm quite the opposite. I was just comparing objectively.

Hope this debate ends soon, there's no need to bump a solved thread.

---

### Post by ThatCoolGuy220 on 2011-06-02
yes but some insight is very interesting

---

### Post by CptPicard on 2011-06-03
> **Petrolea said:**
> 
Well, my point in it having more options was meant in general. You can't write OS in Python for example (I'm not saying I can do it in C lol).

Yes, that is a very common point that is being advanced from the low-level language side. I'd suggest "writing an OS" is just as much as special niche activity as, say, writing J2EE applications is; it is not particularly interesting when talking about language features in general. When you have a very specific technical need for something, you're always going to be using the language that for some reason is suited for the purpose.

> 
For the Ruby part: Ruby is Ruby. It has simple syntax with which you can achieve things quickly and with nice code (even though it doesn't have native 2D+ array support which really confused me at first) and uses kind-of human logic (put 'Ubuntu' 5 times - it doesn't mean "sum all ASCII values of 'Ubuntu' and multiply by 5" but just prints it 5 times). That's why I like Ruby :)

Now, please don't take this as an offense, it's not meant to be as such. I know I'm mostly aligned with you mostly because you in the end say that the human-logic is why you like Ruby. But still, I wonder if you have fully considered why Ruby is designed the way it is. It goes much deeper than what I assume you appreciate. It's not just syntax... it's the design and the concepts, the semantics of what you have in the language.

> 
Im not saying that that type of function is bad. I actually like it so I don't have to worry about whether it returns something or not, or whether it returns array of ints or a string.

Which results in an ability to write implicit interfaces. It's a very fast, surprisingly efficient way of writing code -- in particular, surprisingly efficient when compared to the expectations to static-typing coders.

> 
 There is no usage in C-kind of functions for a programmer that wants to create Tic-tac-toe game.

This one here sounds like a classic slight one hears in this discussion. The point is not that high-level languages are just for authors of *simple programs* as this seems to suggest. The point is that high-level languages introduce more important kind of thinking more easily than do lower-level languages, where one does not get this kind of exposure, and is instead made to deal with things that are far more irrelevant to the intellectual goal at hand.

> You mentioned Java also. Java is totally different from C and other non-OO languages.

When we're talking about type system's relevance, it's a good example. It's a good example of a static-typed system taken to a kind of extreme within the OOP context. 

> 
 When I started learning OOP it really was a pain because I came from C++ background with no one even telling me about classes.

If you had never heard of classes, why do you even consider you came from a C++ background?

> 
 But I was talking about variables, in Java you don't have to worry about pointers when passing some variables to functions, and in C it is a painful experience.

Why is having a painful experience a good thing?

Actually, Java here is a bit of a bad example because you have both  reference-values and primitive types on stack. Anyway, I'm a big fan of languages that just bind to values to begin with (such as Python/Ruby/Lisp); in that case you don't have the primitive/reference distinction anywhere. Variables are just labels bound to values in a context, period. With a bit more Lisp this gets interesting.

> 
 But when you understand C (which can take some time) you will understand variable system in Java also (excluding the OOP part).

I guess you mean the idea of pass-by-reference-value. When using a non-C language, you'll understand that part trivially enough; pass-by-value is a simple addition.

> 
So, don't think I'm a C fan because I'm quite the opposite. I was just comparing objectively.

Well, my objectivity seems to be different :)

> 
Hope this debate ends soon, there's no need to bump a solved thread.

Let's hope not! This is one of the longest-running intellectual conversations here, and the only reason why I even bother to frequent anymore. I genuinely believe there is some value to be extracted from the endless grind :)

---

### Post by Petrolea on 2011-06-03
> **CptPicard said:**
> Yes, that is a very common point that is being advanced from the low-level language side. I'd suggest "writing an OS" is just as much as special niche activity as, say, writing J2EE applications is; it is not particularly interesting when talking about language features in general. When you have a very specific technical need for something, you're always going to be using the language that for some reason is suited for the purpose.



Now, please don't take this as an offense, it's not meant to be as such. I know I'm mostly aligned with you mostly because you in the end say that the human-logic is why you like Ruby. But still, I wonder if you have fully considered why Ruby is designed the way it is. It goes much deeper than what I assume you appreciate. It's not just syntax... it's the design and the concepts, the semantics of what you have in the language.



Which results in an ability to write implicit interfaces. It's a very fast, surprisingly efficient way of writing code -- in particular, surprisingly efficient when compared to the expectations to static-typing coders.



This one here sounds like a classic slight one hears in this discussion. The point is not that high-level languages are just for authors of *simple programs* as this seems to suggest. The point is that high-level languages introduce more important kind of thinking more easily than do lower-level languages, where one does not get this kind of exposure, and is instead made to deal with things that are far more irrelevant to the intellectual goal at hand.



When we're talking about type system's relevance, it's a good example. It's a good example of a static-typed system taken to a kind of extreme within the OOP context. 



If you had never heard of classes, why do you even consider you came from a C++ background?



Why is having a painful experience a good thing?

Actually, Java here is a bit of a bad example because you have both  reference-values and primitive types on stack. Anyway, I'm a big fan of languages that just bind to values to begin with (such as Python/Ruby/Lisp); in that case you don't have the primitive/reference distinction anywhere. Variables are just labels bound to values in a context, period. With a bit more Lisp this gets interesting.



I guess you mean the idea of pass-by-reference-value. When using a non-C language, you'll understand that part trivially enough; pass-by-value is a simple addition.



Well, my objectivity seems to be different :)



Let's hope not! This is one of the longest-running intellectual conversations here, and the only reason why I even bother to frequent anymore. I genuinely believe there is some value to be extracted from the endless grind :)

I'm going to respond in the same order as your post goes because it's late and I don't fell like quoting :P.

Well of course you use the language that fits the task. Some of the languages kind of suit all tasks (for example C - it can do pretty much everything, but for some tasks it takes a huge amount of complex code to solve problems that would usually take a line or two in some other languages; scripting languages are a good example because they have lots of functions already built in).

Ah Ruby again. I never programmed a lot in Ruby. I like the syntax but I can't remember the last time I used it. It was only for some simple problems that I solved in some other languages before. I know Ruby can be powerful in some cases, but as I said, I can't tell much about it since I never went deep into it.

Don't know what to write as a reply. There's nothing more to discuss about functions.

My first reply replied this (part about using different languages for different tasks).

Nothing to add about Java here.

In school we were learning C++. But we were only learning basics - arrays, loops, functions. We didn't learn anything about classes. Actually it was kind of a C/C++ mixture that they called C++. That's why I said I come from C++ background. It was my first language. I don't even know how I got into Java. I never really liked OOP but something attracted me. It was a good learning experience. 

I never said it's good. My point was that passing variables around is way more complicated in some languages than in others.
When I began in C I wanted to kick my computer's a*s because of all the seg faults when messing with pointers. But it gets better over time. Funny thing you mentioned Lisp, I wanted to try it for a long time and I think I will now. Next on the list is Haskell :). 

Hope OP finds something useful in these posts :) I will just add that you should really try lots of different languages, I switched many of them, came back to them, tried new ones and so on and still didn't find a language that I would get deep into. And I can assure this to you: the language you are learning atm won't be your last.

---

### Post by ThatCoolGuy220 on 2011-06-13
LOL segmentation fault happen to me often

---

### Post by ThatCoolGuy220 on 2011-06-13
In fact this post is very usefful as well the others they give very good insigh on the lenguage

---

### Post by Petrolea on 2011-06-13
> **ThatCoolGuy220 said:**
> LOL segmentation fault happen to me often

Need help? If you do, post the code and tell us the problem.

---

### Post by JupiterV2 on 2011-06-13
C. I like C. Why? I have no better reason than: "It's the first language I became somewhat proficient in." When I start learning a new language, the first thing I do is compare it to C. Would I argue that C is better? Heck no! It's good for certain tasks but not others. It has features I like and features I don't. Same as every other language I've tried.

To argue that you should learn C because you can do anything in C is absolute garbage. Yes, most low-level system processing is done in C? Why? Speed. That's it. You could write an OS in Python but it would be cumbersome without an extremely powerful computer. But, writing an OS doesn't really teach you anything. No more than reading the source for Python teaches you about Python. And how many people enter the programming field to write operating systems? My money would be on few and far between. Applications and games are the reason that I would argue the majority of students see as the reason to learn a language. In that case, there are a lot of other languages which are better suited to this task than C.

Pointers and memory management are not a mark of strength. Outside of C or C++, it doesn't help you much. In learning Java and Go, many things I learned in C had to be either unlearned, or discarded, because they have no use outside of the C language.

Dynamic vs. Static typing. I can only answer this question when I include Weak vs. Strong typing. I really enjoy a dynamically typed language when the typing system is strict. Flip-flopping between types on the fly, while can be handy, is problematic to me. Static+Strong typing takes away ambiguity at the cost of flexibility and usability. It is incredibly nice to type: 
(Go)
```
somevar := 8
othervar := "string"
```

Simple and clear. Once the type is set, make it static. I don't see any real advantage to allowing me to use a variable in any way. I think its sloppy. Why? Because I like C. Clear and, though not necessarily, concise.

Compiled vs. Non-compiled. 

I look no further than writing an application with a GUI. Have you ever tried building a GUI application in GTK+ without Glade? Been there, done that. Don't ever plan on doing it again. Not when you compare what you can do with Java Swing, Qt or wxWidgets. Or Tcl/Tk. It was an exercise and an excellent learning experience. The most important thing I learned? There are ways to not only create the application faster but also more cleanly/clearly.

A language doesn't make the coder anyways. Abstract thinking and efficient methods/algorithms make the programmer. Premature optimization (I fall victim to this constantly) is a sign of a poor programmer. Using bubble-sort to solve every sorting problem is a sign of a bad programmer.

A language which teaches the fundamental aspects of programming without bogging the learner down with language specific idiosyncrasies and libraries, would be a good choice. A materialistic language would likely be best. Build a good foundation on which to build from. Yes, maybe you won't be able to write applications right out of the gate but it would, hopefully, make you a better programmer in the end. C, then, would not be a good choice. Being "lower-level" does not teach you how to be a good programmer, as I myself once thought. Nor does using a "higher-level" language like Java. There are things in Java you won't see anywhere else. Perhaps a minimalist language like Lisp or Scheme would be more appropriate. I've never programmed in either of them, yet, but from what I've read they might be good choices. I don't know. Yet.

---

