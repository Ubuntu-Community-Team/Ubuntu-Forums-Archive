---
title: "Langauge advice and  bindings? (warning: here there be novices)"
date: 2007-07-17
forum: Programming Talk
---

### Post by keifer on 2007-07-17
I'm high-school student who has been spending the summer learning my first programming language (ruby). But the more I learn Ruby, the more I question how wise it is to use it. ( i.e., being able to override built-in classes - what happens if I use a library that overwrites a basic class without my realizing it.)

So I'm shopping for another language, and I'm looking between Python and C++. I'm leaning towards going with C++ because it seems the most interesting, and it lends it's self well to my ambition of contributing to KDE in the far future. From what I understand of language bindings, they are like a 'bridge' between two languages. If I learn python, would the experience of using the kdepy bindings translate well to C++ later on, or would I have to relearn the API?  I'm wondering if it makes sense to learn the native language of the project I'm most interested in from the beginning, or should I even worry about things like this until I actually have a language under my belt first? 

If I do go with C++, I'm not *that* worried about being overwhelmed:  I'm a fairly fast learner, and I already have an understanding of many concepts from my short stint with Ruby.

A rather rambling post, but I blame youth and lack of sleep. :P  Comments/advice on anything you think  good for me to know will be most welcome :)

---

### Post by Steven_B on 2007-07-17
C/C++ and Python each have their own place, and they're different.  I would suggest C++ first, but that's just me...  C and C++ will give you a lower level, compiled view of programming, while Python allows you to quickly tie things together.
 I'm actually spending the summer trying to learn C++ and Qt.  I've also dabbled in a little Python, and hope to get into it more the next few months.

---

### Post by cwaldbieser on 2007-07-18
> **keifer said:**
> I'm high-school student who has been spending the summer learning my first programming language (ruby). But the more I learn Ruby, the more I question how wise it is to use it. ( i.e., being able to override built-in classes - what happens if I use a library that overwrites a basic class without my realizing it.)

So I'm shopping for another language, and I'm looking between Python and C++. I'm leaning towards going with C++ because it seems the most interesting, and it lends it's self well to my ambition of contributing to KDE in the far future. From what I understand of language bindings, they are like a 'bridge' between two languages. If I learn python, would the experience of using the kdepy bindings translate well to C++ later on, or would I have to relearn the API?  I'm wondering if it makes sense to learn the native language of the project I'm most interested in from the beginning, or should I even worry about things like this until I actually have a language under my belt first? 

If I do go with C++, I'm not *that* worried about being overwhelmed:  I'm a fairly fast learner, and I already have an understanding of many concepts from my short stint with Ruby.

A rather rambling post, but I blame youth and lack of sleep. :P  Comments/advice on anything you think  good for me to know will be most welcome :)

If you have a good grasp of an API with bindings to multiple languages, it should not be hard for you to make the transition.  It becomes largely a matter of syntax and knowing what idioms are most appropriate for a giving language.

Name conflicts can happen with many different languages, including C++ and Python.  The use of namespaces in both those languages is designed to help with that particular problem.

It is good to experiment with different types of languages and find out what types of tools you find most useful for given tasks.  Having multiple tools at your disposal can make performing many tasks a lot easier.

---

### Post by Wybiral on 2007-07-18
> **Steven_B said:**
> C/C++ and Python each have their own place, and they're different.  I would suggest C++ first, but that's just me...  C and C++ will give you a lower level, compiled view of programming, while Python allows you to quickly tie things together.
 I'm actually spending the summer trying to learn C++ and Qt.  I've also dabbled in a little Python, and hope to get into it more the next few months.

I'm a fan of the "ground up" approach too. I think it's best to learn the low-level side of things first so that you have a solid understanding of the foundations that higher level languages are built from. Then move on to high-level if you need the decrease in development time.

I think it's important that everyone spend some time learning about the low-level aspect of programming, but if you start at a high-level it makes little sense to move down as this would seem like a decrease in productivity. However, if you never investigate the inner workings, then you never learn why certain things are more efficient and how things really work... A valuable _bit_ of knowledge for a programmer _byte_. :)

So yeah... I suggest you start low, learn how things work, then learn about productivity and why to avoid low-level programming (because programs aren't efficient works of art these days, it's all about "speed to market" and profit, not efficiency and functionality).

---

### Post by pmasiar on 2007-07-18
> **Wybiral said:**
> I suggest you start low, learn how things work, then learn about productivity and why to avoid low-level programming (because programs aren't efficient works of art these days, it's all about "speed to market" and profit, not efficiency and functionality).

Yes, I am a big proponent of Python and "speed to market" :-) If your boss needs something quickly, most efficient IMHO is the program you can write and debug the fastest :-). 

But I agree with Wyb, it is important to know programming on low level. I would suggest first to become reasonably experienced in high-level language like Python or Ruby (it is faster to get results - and more fun), then invest some time to learn programming "down and dirty" in C. Not even C++, so won't have OO machinery helping you, plain C. To get the feeling how bits are moved in and out of CPU. It will be harder and much more work to get things done, but previous knowledge of high-level language will help you to see what is happening, and why.

---

