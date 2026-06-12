---
title: "To OO or not to OO"
date: 2009-07-18
forum: Programming Talk
---

### Post by Wisey on 2009-07-18
Hello! I am completely new to programming, learning C++ as my first language. The textbook I use for self-study focuses a lot on object-oriented programming. 

When I was utterly jobless a couple of afternoons back, I searched for object-oriented programming on google, and came upon a bit of criticism. Searching specifically for more of these led me to a whole lot more of such criticism.

Basically, since I am learning programming with OO right from the start, I just want to make sure I am learning something that works, not something that is just hyped up with nothing to back it up. So is it okay if I proceed with that textbook and the way I am learning right now? Did I only encounter so much criticism because I specifically searched for it? Basically I don't want to learn something, just to unlearn it later on.

---

### Post by hessiess on 2009-07-18
There is nothing wrong with OO, though it can be somewhat complicated in C++ due to the manual memory management.

Also a lot of people here would not recommend C++ as a first language, it was my first and I had no problems learning it (unlike higher level languages).

---

### Post by zolookas on 2009-07-18
As you may have noticed, there are many opinions about OO.

I like OO and generic programming features in C++, because it makes easy to write generic code (compared to C), but I do think you should also read about procedural programming.

Take a look at different programming paradigms: [http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm)

---

### Post by CptPicard on 2009-07-18
As a matter of fact, most programming is object-oriented in some way. The point is that the concept of "object" must be understood somewhat more generally and loosely than what you see in your typical static-typed OO languages such as Java or C++. In those languages it is easy to end up with a kind of type explosion and extremely complex and contrived object models where you have to invent all kinds of classes just to make your architecture work.

The "hype"-style object-orientedness you see sometimes is not a solution to everything as was suggested in the 90s, but on the other hand, it's almost impossible to avoid the idea of an object in most code.

---

### Post by jero3n on 2009-07-18
As you get more experience in programming, you'll notice that there are many problems that fit well to OO model. In such cases you'll see that OO model helps you write more maintainable and clear code, especially in large projects.

There are also problems that do *not* fit to OO model. It's good to know this or will lead you to troubles.

I suggest you to study OO well. You 'll probably not need all the features, but it is always good to understand a new programming philosophy. I use many of OO ideas even when I program with C.

---

### Post by CptPicard on 2009-07-18
It is also worthwhile noticing that although you may not be explicitly defining classes with rigid interfaces and whatnot, most high-level languages see pretty much everything in the language as some kind of object anyway (think about python, or lisp). On the other hand, in the more "explicit" OOP languages, you rather soon find yourself having to resort to all kinds of "design patterns" and whatnot to create what you need... and IMO those patterns are often just workarounds to fundamental problems in the model itself...

---

### Post by Leslie Viljoen on 2009-07-18
Although there is some criticism, I haven't seen any alternatives that will give you OOP's benefits. In fact, you can get away with using only some of OOP's features and still gain a lot. I have seen cases where hundreds of lines were removed as we factored out similar code into objects. This can be done without objects (you can write "object oriented" C), but it's relatively cumbersome.

You'll very likely have to learn it eventually anyway if you are going to work with other programmers and it will definitely not be a waste.

---

### Post by Wisey on 2009-07-19
Thank you for the replies, they were really helpful. 

@hessiess
I was stuck with C++ as my first language as my college asked me to get familiar with it, it doesn't seem all too bad for a beginner as most people make it out to be, although I have to admit I haven't done all that much yet, just approaching pointers now.

---

### Post by gtr32 on 2009-07-19
> **Wisey said:**
> although I have to admit I haven't done all that much yet, just approaching pointers now.

That's where the fun begins, at pointers. Learn them and their scope well, and you're off to a very good start. Even if you move from C++ to a language that has garbage collection, you have not certainly wasted time by learning how memory management works.

C++ might not be the easiest language to get started but a combination of C and C++ might still be the best place to start for someone who is thinking of making a career out of it. That's just my opinion, and to tell the truth I do most of my work in C# nowadays because it's faster and easier.

About the topic of OO, it's definitely something you want to learn, sooner or later. Sooner would be preferred. Good luck and have fun!

---

### Post by nvteighen on 2009-07-19
OOP is a design pattern really intuitive for human beings... we usually think in terms of object, so coding with objects is a really natural thing to do. So, no problem in learning it...

What you should learn, of course, is when to choose OOP and, then, which is the correct classes design for your project. In my experience, you learn that only by coding... And another thing you have to learn (but this is probably only possible when having learned more than one language), is to distinguish between OOP and your chosen language's ways to OOP... Actually, OOP is just about having the ability to refer to data and code with respect to some given object.

---

### Post by wil on 2009-07-19
I know both methods.

I like to do a hybrid of both methods. My ultimate goal is to create simple solutions for complex problems, and I use whatever achieves that. 

Cut and paste is one of the most powerful ways to reuse "objects", it is also very flexible as you can fine tune it without worries about breaking something.

Huge object hierarchies can become huge nightmares, so no matter what method you use the wheels can come off.

Divide and conquer is a great method to use, make sure that which you divide is divided/contained/autonomous/a class/module, create a test program that tests that bit of code, once tested it is conquered and you are ready for the next piece.

Good Luck.

---

### Post by Can+~ on 2009-07-19
OO is fine, as long as you don't get stuck on it and thinking that's the only way of doing things.

I guess that the big criticism against OO that you've seen, is mostly related on C++'s implementation.

---

### Post by ratcheer on 2009-07-19
I would definitely recommend OO. **Smalltalk** and **Ruby** are good places to start, because they are pure OO languages.

---

### Post by nvteighen on 2009-07-20
> **ratcheer said:**
> I would definitely recommend OO. **Smalltalk** and **Ruby** are good places to start, because they are pure OO languages.
Smalltalk... a fine language. Sadly, almost nobody cares about it.

---

### Post by karlmp on 2009-07-20
**python!** [http://www.catb.org/~esr/faqs/hacker-howto.html#skills1](http://www.catb.org/~esr/faqs/hacker-howto.html#skills1)

---

