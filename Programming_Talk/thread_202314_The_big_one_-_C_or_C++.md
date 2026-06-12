---
title: "The big one - C or C++?"
date: 2006-06-23
forum: Programming Talk
---

### Post by bb2120 on 2006-06-23
I'm sure this one has been asked hundreds of times, but I'm yet to find a decent, unbiased comparison that uses standard english.
I have good skills in PHP, XHTML and CSS, but want to try something different.

Which of the two best encourages good coding practices?
Do both support OOP?
Which has the most logical syntax?

Is there anything else that I should think about?
I'm not too bothered about speed of execution, but which one is the fastest?

---

### Post by cronholio on 2006-06-23
> Which of the two best encourages good coding practices?

C++

> Do both support OOP?

Only C++ does.

> Which has the most logical syntax?

Hard to say. Depends on personal preferences. For instance, I can see the logic in C++ class syntax but the "<<" and ">>" thing seems out of place.

> I'm not too bothered about speed of execution, but which one is the fastest?

Depends on compiler and compiler settings. Should be fairly equal. Both are pretty fast.

I suggest you install Anjuta and try out both. Lots of things are pretty similar between them. For everyday stuff (I mean for what is everyday stuff for me) I prefer C, and I use C++ when the task to be done literally cries for OOP.

---

### Post by bb2120 on 2006-06-23
> Hard to say. Depends on personal preferences. For instance, I can see the logic in C++ class syntax but the "<<" and ">>" thing seems out of place.

It's just that I heard that some C operator preferences were 'wrong'.
I totally agree with you on the << and >> - What do they actually do? I realise that they are bitwise shift operators but  what the hell are those?

---

### Post by thumper on 2006-06-23
operator << and >> in C++ are considered the streaming operators.

Yes, between integers (and some other numeric types) it is also the bitwise shift operator.

You do get used to the syntax really quickly, and to me the streaming operators are much more natural than printf or scanf.

---

### Post by bieber on 2006-06-23
I'd say start with C, then learn C++, which is a superset of C--it adds object orientedness and some other features.

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=cronholio]Hard to say. Depends on personal preferences.[/quote]No, it doesn't.  Both have equally terrible and horrendous syntax.  On a technical level, C wins here because it's LR(1) parsable, while C++ needs a LR(infinity) parser.

 For instance, I can see the logic in C++ class syntax but the "<<" and ">>" thing seems out of place.

> Depends on compiler and compiler settings. Should be fairly equal. Both are pretty fast.It depends on exactly what you're doing.  

[quote=bieber]I'd say start with C, then learn C++, which is a superset of C[/quote]It's almost a superset.  It's not actually.

More importantly, the best C code is really bad C++, and the best C++ is impossible to write in C.  As such, pick one and learn one.  THen forget that language and learn the other.

I'd recommend learning C++ first because the books for it are far, far better than any C book.

---

### Post by wmcbrine on 2006-06-23
Broadly speaking, C and C++ are appropriate for different problem spaces. Learn both, and you'll see what I mean.

---

### Post by mdurham on 2006-06-23
Aparantly it's easier to learn C after learning C++.  C to C++ is more dificult.
This isn't just my opinion, a lecturer teaching C++ said the sudents that already knew C struggled more than those that didn't.

---

### Post by skymt on 2006-06-24
I'd say C, for the following reasons.

* It has a much simpler syntax with fewer concepts and keywords.

* It's much more widely used than C++ in the open-source community, so if you release the source, more people will be able to contribute.

* Glib (mostly used in GTK applications) [adds object-orientation](http://le-hacker.org/papers/gobject/index.html) (of a sort) to C, without the extra complications of C++.

---

### Post by LordHunter317 on 2006-06-24
[QUOTE=skymt]
* It has a much simpler syntax with fewer concepts and keywords.[/quote]It's syntax isn't much simpler than C++'s at all, until you consider templates.  Even then, if you ignore some of the more esoteric template features: specialization, and two-phase type-lookup, the situation is not drastically worse.

> * It's much more widely used than C++ in the open-source community, so if you release the source, more people will be able to contribute.Not especially.

> * Glib (mostly used in GTK applications) [adds object-orientation](http://le-hacker.org/papers/gobject/index.html) (of a sort) to C, without the extra complications of C++.The stuff added by Glib is just C++ in sheep's clothing.  If you're using it, it means you really should be using C++.

---

### Post by Stromham on 2006-06-25
Which of the two best encourages good coding practices?
use proper cases
add lots of little comments with /* */

Do both support OOP?
no only c++

Which has the most logical syntax?
they both are farily simalir but c++ is newer and more refined

Is there anything else that I should think about?
yes c# and java they are very easy to get into and dont overwelm you.

I'm not too bothered about speed of execution, but which one is the fastest?
well c++ is faster than c but 1 being the fastest and the slowest.

1. c#
2. java
3. C++
4. c

i would not suggest going straight into c/c++ qith your current programming experience, i would suggest c# or java as they are farily easy to learn and you dont have to worry about heap/stack data and registery, etc. the jrm and .net framework do it all for you, while having speed benifets like garbage collection.

---

### Post by LordHunter317 on 2006-06-25
[QUOTE=Stromham]well c++ is faster than c but 1 being the fastest and the slowest.

1. c#
2. java
3. C++
4. c[/quote]You have this list backwards.  C# is unquestionably slower than anything else on the list.   C and C++ are honsetly of equal speeds these days in almost all situations.  The differences come down to compiler optimizations most of the time.  There's a few cases where the added overhead gets C++, but they're not often.  They can usually be coded around too.

i > i would suggest c# or java as they are farily easy to learn and you dont have to worry about heap/stack data and registery, etc.You have to worry about heap and stack in both.  I don't see what "registry" has to to do with anything.

---

### Post by bb2120 on 2006-06-25
Thanks guys, this (slightly argumentative) discussion is really helpful.

I understand that C++ is a massive step up in complexity from interpreted languages such as PHP and Python, but I think I'm ready :)

I want to learn to learn good practices and from what I've heard, C++ will help me with this more than C, though I understand that C# and Java are also strog in this field.

---

### Post by bb2120 on 2006-06-25
Sorry - double post

---

### Post by bieber on 2006-06-25
Also, this might be a little out there, but someday, when you're comfortable with programming in high level languages, learn Assembly language for your platform of choice.  It's not going to have many practical applications, but it's a great way to really learn how a computer works.

---

### Post by LordHunter317 on 2006-06-25
[QUOTE=bb2120]I understand that C++ is a massive step up in complexity from interpreted languages[/quote]It is, but it isn't, when compared to python.  Python has lots of features that C++ doesn't have: generators, formalized lambda expressions, list comprehensions, automatically reference counting for objects  (though some, like certain generators and some lambda expressions, can be done differently).  

C++ has a ton of features Python doesn't have, most related to static typing.  

C++ is a more complicate language, in part due to the type system.  But the type system is quite powerful and when properly leveraged, grant you all sorts of nifty tricks (boost::variant still be one of my favorites) and compile-time type saftey.

> I want to learn to learn good practices and from what I've heard,Best practices are highly language and somtimes even API dependent.

---

### Post by IYY on 2006-06-25
> I want to learn to learn good practices and from what I've heard, C++ will help me with this more than C, though I understand that C# and Java are also strog in this field.

Not exactly. Java and C# hide a lot from you, and so you might be doing incredibly inefficient and silly things without understanding. However, with C# and Java it is easier to focus on the "big picture", so from a software engineering point of view you are right.

I think you should start with C, but eventually learn Java, C++ and C#. They are all very similar when it comes to syntax, so it's not difficult to learn them all.

---

### Post by LordHunter317 on 2006-06-25
[QUOTE=IYY]Not exactly. Java and C# hide a lot from you,[/quote]Not especially.  The biggest issue they hide from you that's part of the language proper is the garbage collection rules.  That is what people run up against most often, at least in terms of obscured details.

The rest of it is API (standard perhaps, but API nonetheless) details.  But the whole point of encapsulation is that you don't have to worry about those implementation details.

And C++ hides all sorts of details from you as well.  Like the fact most implementations have copy-on-write std::basic_string<>.  Or the fact that std::sort() swithc algorithms based on the size of what is being sorted.

> However, with C# and Java it is easier to focus on the "big picture", so from a software engineering point of view you are right.There's little about C# and Java beyond their huge class library (which isn't an ispo facto positive thing) that make it eaiser to focus on the "big picture" than C++.

The only reason it may be eaiser is the existance of more evolved tools for them over say, C++.  C++ IDEs usually aren't as featureful as C# and/or Java IDEs, because C++ is a much more difficult language to parse and analyze.

Then again, the standard library is IMNSHO far-more powerful (for what it does, anyway), which frees me to care about big picture issues more.  I don't have to worry about things like basic resource managment, how to cope with a broken collections API, or wrong data type decisions in C++.

> They are all very similar when it comes to syntax, so it's not difficult to learn them all.I say this in every thread, but similar syntax isn't a compelling reason to learn a language.  If anything, it adds to confusion.

---

### Post by Stromham on 2006-06-25
[QUOTE=LordHunter317]You have this list backwards.  C# is unquestionably slower than anything else on the list.   C and C++ are honsetly of equal speeds these days in almost all situations.  The differences come down to compiler optimizations most of the time.  There's a few cases where the added overhead gets C++, but they're not often.  They can usually be coded around too.[/qoute]

so garbage collection does nothing? it guess it mostly depends on the programmer and how well he handles his memeroy in any language.

[qoute]i You have to worry about heap and stack in both.  I don't see what "registry" has to to do with anything.[/QUOTE]

i was talking in regards to windows registery.

---

### Post by bieber on 2006-06-25
...that didn't make any sense at all...

---

### Post by LordHunter317 on 2006-06-25
[QUOTE=Stromham]i was talking in regards to windows registery.[/QUOTE]And?  My point is that the registry is totally irrelevant, I don't see why you brought that up.

---

