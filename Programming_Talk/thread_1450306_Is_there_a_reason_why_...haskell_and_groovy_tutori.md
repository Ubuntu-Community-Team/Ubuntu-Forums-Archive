---
title: "Is there a reason why ...haskell and groovy tutorials are unclear?"
date: 2010-04-08
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-08
When I look at Java or C++ (Granted, OOP languages) they have a distinct pattern, not only that but the source code is obvious. Effectively you can copy and play around with source code and have a valid working program. (Perhaps not so much valid). Take a look at Java for example. 

Sun has produced an extensive tutorial system, taking you right through the helloWorld section straight through classes and to your first fully fledged app. C++ has a similar layout. Most tutorials for them show source code, explain what the code is doing, why its doing it then moves on. 

Groovy/Haskell don't seem to want newbies to pick the language up. Looking for simple "HelloWorld" scripts for either of these languages left me scratching my head for hours. (Have manged to do it in the end). Defining sets/lists/arrays what ever you want to call them however were almost impossible. After hours of reading every tutorial on YAHT (Yet another Haskell Tutorial) and Haskell WikiBooks I found nothing that tells me how to define a set, except through the ghci and that's not permanent. Therefore useless. I thought this was just me missing something, I decided to look up any code (Haskell). I found in every tutorial, 50 lines of source code that actually looked like it could be usable. 

Why is this? Why are such languages which have been in the public domain and could be revolutionary to the programming world so poorly documented. (Excluding books, I haven't read that many to make that kind of judgement). Anyone feel free to jump in!


.........................

And if anyone feels particularly helpful... any good tutorials that do show how to write haskell files (.hs files that is). Thanks to anyone who can help.

---

### Post by OgreProgrammer on 2010-04-09
Haskell files are just text files. 

While C style languages are imperative (do as I say NOW), Haskell and others are less so. Surely you have heard that Haskell is a lazy language. 

Because of this it takes a different sort of thinking, and thats useful in itself to develop. For instance, haskells infinite lists...

```
let inf = [1..]
```Haskell doesnt care that you do that until you actually ask it to do something with the list, at which point you had better put some limits on it. 

```
take 5 inf
```so you are trusting haskell to do what you mean rather than directly what you say. 

So generally when someone is interested in haskell, they already have a good deal of experience in programming. It doesnt mean that haskell is hard(its not), but that the audience the tutorials are written for dont need the tiny steps typically found in tutorials. 

Have you seen this tutorial? it helped me a lot. 

[http://learnyouahaskell.com/chapters](http://learnyouahaskell.com/chapters)

and this one?

[http://www.lisperati.com/haskell/](http://www.lisperati.com/haskell/)

Also, if you learn python, haskell will make more sense. You can learn list comprehensions there. For example, in python

```
answer = [x*x for x in numlist if x > 6]
```is the same as

```
answer = [x*x | x <- numlist, x > 6]
```in haskell.

---

### Post by Ravenshade on 2010-04-09
I'll take a look at those tutorials thanks for the information. 

Unfortunately I am a relative newbie to programming. (Yet a task I have been set is to write a certain code in Java, Groovy and Haskell), by your reasoning Haskell is going to be very hard for me to unlock..

---

### Post by Reiger on 2010-04-09
Haskell is a pure functional language. The sooner you wrap your head around the fact you can only define `what' you are computing but not `how' you are doing that; the easier Haskell will be. Also in Haskell the `hello world' example is typically the factorial function or Fibonacci sequence (naive algorithm), since it is easier to understand those in terms of functions.

EDIT: For a comparison; the difference between learning Java and Haskell could be the difference between English written in iambs, and French written in dactylic hexameter. The sooner you learn to appreciate the difference in rhythm, the easier it becomes to read and write in that style.

---

### Post by CptPicard on 2010-04-09
The reason why Haskell tutorials may seem "unclear" is simply because pure-functional programming takes a mindset change in how you accomplish things. That is hard to teach by hand-holding, it must come from actually working with the language, seeing solutions to problems ... so on.

However, I fully agree with you that Groovy is badly documented. Tutorials just show you how to achieve some specific thing; it's almost as if the whole language is not documented properly anywhere. I have a Groovy book that I like but I forgot the name and I haven't been at home all winter so I can't take a look...

---

### Post by OgreProgrammer on 2010-04-09
> **Ravenshade said:**
>  by your reasoning Haskell is going to be very hard for me to unlock..

Dont get that into your head. Its just different, not particularly hard.

Ask questions here of course.

---

### Post by Ravenshade on 2010-04-09
All I need to know regarding haskell, groovy can be compiled into a single list. 

How to write the code in a script and not through an interpreter like ghci
How to write a simple hello world program. 
How to write if statements, loops and finally arrays. 
How to compile the code 
How to execute the code. 


Yet (and thanks for those resources but I have read them both previously and they're not quite that clear) the resources I have found, either insist on using an interpreter or not actually deliver code that can be put into a script that actually works, making learning very difficult.

---

### Post by Bachstelze on 2010-04-09
I have made Haskell entries for some of the recent Programming Challenges, you can have a look at them and see if that makes things a bit clearer.

[http://ubuntuforums.org/showthread.php?t=1424102#8](http://ubuntuforums.org/showthread.php?t=1424102#8)
[http://ubuntuforums.org/showthread.php?t=1407897&page=2#12](http://ubuntuforums.org/showthread.php?t=1407897&page=2#12)
[http://ubuntuforums.org/showthread.php?t=1410818&page=3#22](http://ubuntuforums.org/showthread.php?t=1410818&page=3#22)

As you can see, especially with the third one, Haskell is usually very concise and elegant (some would even say beautiful), but this comes at the cost of performance: you don't have a lot of ways to control exactly how your program works, so you can't really optimize it for performance.

There are no if statements or loops in Haskell*, those things belong in imperative languages. Of course, you can emulate them, but if you're going to do Haskell like it's C, you might as well not bother and do C in the first place.

Compiling the code is done with ghc, which has mostly the same syntax as gcc:

```
ghc -o foo foo.hs
./foo
```

* Well, there are if/then/else statements, but they don't work quite the same as in C. For example, here's how you could code the absolute value function in Haskell (on integers for the sake of suimplicity):

```
absoluteValue :: Int -> Int
absoluteValue n = if n < 0
                      then -n
                      else n
```

The if clause is followed by a condition, but the then and else clause (the else clause being required!) do not define a block of instructions to run, but a value to return.

---

### Post by Søren on 2010-04-10
Haskel is functional, groovy is attached to grails - frameworks are always frustrating.

---

### Post by CptPicard on 2010-04-10
> **Søren said:**
> groovy is attached to grails

Not really, it's an independent language, but certainly most examples of Groovy are Grails-specific, a bit like a lot of the Ruby stuff you see is RoR-specific...

---

