---
title: "C++ bypass &quot;hello world&quot; - rapid dive"
date: 2023-03-11
forum: Programming Talk
---

### Post by aljames2 on 2023-03-11
I am looking for some recommendations to help me speed up the C++ learning.  Programming in general, I am familiar with concepts such as taking inputs, printing outputs, types of variables, conditional segments including equality operators and boolean logic, loops, and arrays.  I guess this would be beginner to intermediate.  I am looking for a dive into the code.  My preferred way to learn would be to see an example of a large code project, with right-side comments throughout explaining the syntax including the objective of each segment or function.  I think I would learn the language and remember the syntax better this way.  Not sure if such experiential problems with embedded training like this even exists.

Back in my high school years I took computer science for 3 years and learned Basic & Pascal.  Both rather useless now, but the theory & concepts of programming are mostly still with me.

My goal is to learn a "lower level language" like C or C++, to better understand Linux under the hood and to be able to contribute, test, and write programs for the fun of it.

---

### Post by TheFu on 2023-03-12
> **aljames2 said:**
> I am looking for some recommendations to help me speed up the C++ learning.  Programming in general, I am familiar with concepts such as taking inputs, printing outputs, types of variables, conditional segments including equality operators and boolean logic, loops, and arrays.  I guess this would be beginner to intermediate.  I am looking for a dive into the code.  My preferred way to learn would be to see an example of a large code project, with right-side comments throughout explaining the syntax including the objective of each segment or function.  I think I would learn the language and remember the syntax better this way.  Not sure if such experiential problems with embedded training like this even exists.
You aren't ready for any large C++ project if you are asking here.  C++ in a project created by more than 1 person looks very, very, very, different from what a single person would create.
Do you know OO already?  I mean, really understand it?  Programming with functions isn't the same as OOP.  For me, I tried over and over and over to learn OO, but until I attended a class in a room, with a teacher, it never "clicked."  Once it did, I could see how my X/Windows programming classes which passes pointers to C structs around to each X-primative was an early attempt at OOP.
When I first started using C++, I was writing C code, but running it through the C++ compiler. That isn't C++ and it isn't OOP.
People usually over-state their true level of understanding.  It is impossible to know what you don't know, until you know it. ;)  

> **aljames2 said:**
> Back in my high school years I took computer science for 3 years and learned Basic & Pascal.  Both rather useless now, but the theory & concepts of programming are mostly still with me.

Not a bad intro for structured programming, but that has little to do with OOD/OOP and how C++ or any OOP is used.

> **aljames2 said:**
> 
My goal is to learn a "lower level language" like C or C++, to better understand Linux under the hood and to be able to contribute, test, and write programs for the fun of it.
Start with C. Pascal, Basic and C are all similar.  When you want to learn OOD/OOP, it is a paradigm change.  At least for me it was.  For large projects, OOP and OOD make things easier.  I don't know if I'd suggest anyone learn C++ today.  Perhaps Rust would be a better language?  Ruby is also OOP from the ground up, though the main use is with webapps, so seeing all the connections isn't nearly so easy.  OO languages aren't really low level. If you want low level, learn C.

BTW, "hello world" in C++ is pretty useless.  OOP for trivial programs is useless and adds way too much bloat to make sense.

I always come back to this ... if you want to become a priest, you have to live and learn at a monastery.  

I think the same applies to OOP and OOD.  Need to get to a monastery to learn the terms and really understand what they mean.  I learned OOD following Booch's method. Over the decades, I think most of the OOD nomenclatures consolidated into UML - Unified Modeling Language. [http://uml.org/](http://uml.org/)  

For any non-trivial program, OOP is a great way to create code that doesn't allow bad data to be introduced.  The data and functions (called "methods") are grouped into a single "class" together.  The methods make ensuring the data is used safely and always have valid values happens.  Outside functions aren't allowed to touch the data.

The real issue with OOP is that people dream up all sorts of methods that aren't necessary to their exact problem.  Using inheritance is one of those things too.  Just because it is possible, that doesn't mean it is a good idea to use.  x100 for people using multiple inheritance.  I can think of only 1 time where using it actually made sense over 10 yrs doing C++.

Python allows OOP, but I haven't seen it used in the real world.  It definitely isn't low-level.  If you aren't manually managing and accessing memory, then you aren't low level.

So, do you want to be low-level or do you want to learn OOD/OOP as a skill for a real job?

One of the best ways to learn a language that I've found, and a great teaching too, is to find "programming standards" from a few different projects, review those to learn "why" they bother setting certain standards at all.  At one company, we spent about a month creating C++ coding standards for our project team.  They started with referencing 2 books by Scott Meyers, Effective C++ and More Effective C++.  Creating maintainable code and using simple techniques to write code that prevents dumb mistakes were the main things.
For example, in C, 
```
if ( something )
    a++;
```
is valid.  But we decided never to allow unbracketed if statements, so
```
if ( something ){
    a++;
}
```
was our standard even though both have exactly the same result. Another standard was whenever the code did comparisons between a static/const value and a variable, the static value would be on the left, since  in many languages, the assignment operator is easy for humans to gloss over, introducing a bug.  This can be a bug:
```
if (  a = 1 ){    // did you mean a == 1?
....
}
```
```
if (  1 = a ){
....
}
```
will cause a compile-time error.  Simple technique to avoid dumb mistakes.
In C++, we decided to make a copy-constructor mandatory for all classes.
>      * All classes will contain a definition for a copy constructor, and equality operator to prevent inadvertent automatic compiler generated methods.
          + By making these methods private and not providing an implementation compiler generated versions will not be utilized without specific developer action. No surprises.
If you don't know what a copy-constructor is and why the compiler generated version is often bad, then it is something to be learned by less knowledgeable programmers.  If a class has pointers and the copy just copies the pointers without de-referencing (doing a deep copy),  we will have a dangerous memory use that can crash a program.  OTOH, doing deep copies can drastically slow performance when it isn't necessary, so maybe the object just needs to know if it is a deep copy instance or a pointer reference instance with a way to know the source object of the copy is still valid?   Or perhaps it can be a shallow copy without bringing the pointers ... that might be fine too.

---

### Post by Tadaen_Sylvermane on 2023-03-12
[https://www.udemy.com/course/c-programming-for-beginners-/](https://www.udemy.com/course/c-programming-for-beginners-/)

I strongly recommend this course + the advanced one by the same person. I got the pair on sale + something involving data structures and algorithms and I'm learning very quickly. I haven't started the advanced one yet as I'm taking a break between to practice little programs and functions. You can work through it as fast as you want. Easy to follow and the instructor doesn't just give you power point stuff. Rather actual explanations about why and how.

---

### Post by aljames2 on 2023-03-13
I think C is where I should start.  Programming is not my profession but I have an interest in it, always have. I have more time to give to it now and I think I will pick up on it rather quickly.

Hard to choose a book, too elementary vs too advanced.  A class at the local college is doable to get things rolling in a structured way.  I am good with self-study, and so the Udemy’s of the world could also be an option.

---

### Post by TheFu on 2023-03-13
I think you can learn C on your own.  It isn't a paradigm shift like all OOP is.
Just know that there are many different C standards, so the the C that I learned isn't the same as the C used today and neither of those are the same as the K&R C language.  New keywords were introduced over all this time.  There are different C compilers too, so each as a slightly different interpretation of the "standard" they claim to follow.  C90, gnu99, C11, C17, are the main standards. If you take a course at the local college, it will probably be taught on Windows, so you'll learn a tool, not the language.  

We see people here start their questions by "I'm using Code::Blocks" or "VSCode" ... and I don't bother trying to help, because the last time I used an IDE on a non-Unix OS was VisualC++ and it was a pain.  On Unix systems, our OS and X/Windows is our IDE. Once you know how to use it, nothing else compares.  gmake, gdb, a web browser, manpages and whatever editor you like with whatever extensions you like for the language used.  I think the kids these days use cmake, not gmake.  Hopefully, they all use indent++ to enforce style guides regardless of the the programmer.  There's a series of blog articles about "UNIX as an IDE" that google finds easily, if that is your interest.  Regardless of the editor, beware of any syntax highlighting. Sometimes all editors get confused and things that appear 100% fine, aren't.

Sometimes paying for learning is a key to ensure you will follow through, but there are free, structured, C programming classes too. Of course, you'll need to decide and follow through yourself then.  Programming knowledge is like Linux knowledge. There's always more to know, so there isn't any end point.
I'm a fan of the Effective C++ books, so I'd expect the [https://nostarch.com/Effective_C](https://nostarch.com/Effective_C) book to be excellent too. It uses C17.
Years ago, I wrote this article: [https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) about how to learn to program.  Back then I recommended C as a second programming language for everyone. I still think that's a good idea.
[https://www.wibit.net/courses](https://www.wibit.net/courses) has free C courses.  MIT, GA Tech and other famous schools sometimes put their course materials online for free too.  If you are going to learn, why not learn from the best teachers?

---

### Post by aljames2 on 2023-03-13
Thank you @TheFu for your blog and the book reference. Read your article & reading the book now, enjoying it and impressed with the author, and the emphasis on quality standards based coding from the beginning, like you were writing about in a previous post here.

Agree on the point about IDEs. Instead I will use an editor, probably vim along with command line compiler.

---

