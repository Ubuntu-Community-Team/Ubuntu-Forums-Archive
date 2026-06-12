---
title: "C++ design concerns; class visibility"
date: 2009-12-02
forum: Programming Talk
---

### Post by jellyfisharepretty on 2009-12-02
So I've embarked upon a rather big computer vision / machine vision project that will use the OpenCV library.  I need a good way of testing out different chains of processing on my images.

At first, I was using only one file, openCV-test.cpp, with the main() method.  As I added functions to test some functionalities of the OpenCV libray on my images, it became rather a burden to keep editing the same file.  Even though I tried to keep things in separate methods and out of the main() method, it seemed whenever I wanted to try some completely different processing, I had to at least re-write the main method, not to mention the length of the file getting larger and larger.

Keeping in mind that I come from a background of Java programming (where practically every file is a class) and that these are my first steps in C++, I came up with this idea for a plan :

**class myCVProcessor :**
- constructor myCVProcessor::myCVProcessor()
- function    myCVProcessor::function1(...)
- function    myCVProcessor::function2(...)
        ...
- function    myCVProcessor::functionN(...)

**openCV-test.cpp :**
- contains main() method.
- instantiates a myCVProcessor object that will be used to apply processing to images.
- methods in this file can then be used for the different chains of filters that I want to apply.

**The question :** what do you think of this design ?  Is this a good idea ?  What would you suggest ?

[Note : I solved my class visibility issue]

Any help much appreciated.  Thanks.

---

### Post by johnl on 2009-12-02
Just thinking out loud here, but I might approach this like so:

```

class Filter {
  public:
    virtual void ApplyFilter(SomeThing& obj) = 0;   
}

class SomeFilter : public Filter {
  public:
    virtual void ApplyFilter(SomeThing& obj) { /* do something */ }
}

class SomeOtherFilter : public Filter {
  public:
    virtual void ApplyFilter(SomeThing& obj) { /* do something else */ }
}


int main(int argc, char* argv[]) 
{
    // the filters we want to apply
    // this could go in some other method.
    std::vector<Filter*> filters;
    filters.push_back(new SomeFilter());
    filters.push_back(new SomeOtherFilter());

    // the thing to apply filters to
    SomeThing obj;

    for(std::vector<Filter*>::iterator i = filters.begin();
        i < filters.end(); ++i) {
        // apply all filters in order to obj. 
        (*i)->ApplyFilter(obj);
    }
    
    // clean up pointers here.
}


```

---

### Post by jellyfisharepretty on 2009-12-02
Neat! Thank you.  Seems very object-oriented, and that is not a bad thing for me.  I am not entirely familiar with virtual classes; they do seem to be equivalent to interfaces in Java from what I can understand.

---

### Post by johnl on 2009-12-02
> **jellyfisharepretty said:**
> Neat! Thank you.  Seems very object-oriented, and that is not a bad thing for me.  I am not entirely familiar with virtual classes; they do seem to be equivalent to interfaces in Java from what I can understand.

A 'virtual' method is a method that can be overridden by an inheriting class.  When you say  ' virtual void ApplyFilter(/*...*/)** = 0; **'

This indicates that the function ApplyFilter **must** be implemented in any inheriting class because there is no implementation of it in the base class.  

Otherwise, an inheriting class may choose not to implement this function and use the base classes implementation. 

A class that contains functions like this is called a 'pure virtual' class because you cannot instantiate it directly since it has no implementation for these methods.  Interfaces in Java or .NET are similar to a pure virtual class, since you are required to implement all their functions when inheriting from them.

---

### Post by MadCow108 on 2009-12-02
virtual means that the function call will be resolved at runtime allowing dynamic polymorphism. It has no equivalent in Java so far I know.

consider this:
```
class base {
   public:
   int method() { cout << " bla " << endl; }
 };
 
 class derived :public base {
   public:
   int method() { cout << " blub" << endl; }
 };
 
 int main(int argc, const char *argv[])
 {
   derived d;
   d.method();
 
   base * d2 = new derived();
   d2->method();
   return 0;
 }
```
output:
blub
bla

d2 called the base class function as it does not know at compile time to which class the pointer points to (although its obvious in this simple case that *d2 is a derived object, generally the compiler can't make any assumptions about the memory a pointer points to).
to resolve this you need to add virtual in the base class method
this then resolves the call at runtime and calls the overloaded function.

---

### Post by nvteighen on 2009-12-02
> **jellyfisharepretty said:**
> 
At first, I was using only one file, openCV-test.cpp, with the main() method.  As I added functions to test some functionalities of the OpenCV libray on my images, it became rather a burden to keep editing the same file.  Even though I tried to keep things in separate methods and out of the main() method, it seemed whenever I wanted to try some completely different processing, I had to at least re-write the main method, not to mention the length of the file getting larger and larger.


The issue of having to constantly rewrite main() is just unimportant. Think about it: if you're manipulating your classes' interfaces, you'll have to modify the caller functions. There's nothing wrong in that.

But the issue of having main() growing larger is a problem. Very probably, your classes aren't abstract enough or need more classes or just mix OOP with procedural programming and create functions... You know: "1 function = 1 task". The main()'s task should be managing the program's most essential starting up and shutting down steps

> 
Keeping in mind that I come from a background of Java programming (where practically every file is a class) and that these are my first steps in C++, I came up with this idea for a plan :


Don't desperate. Java and C++ are very much the same: static typed OOP languages... and C++ influenced Java. The differences you'll encounter will be actually just very minor (pointers are just a technical issue); the concepts are pretty much the same. You're not jumping from Java to Forth (dynamic typed stack-based language with RPN syntax :p).

---

### Post by dwhitney67 on 2009-12-02
> **johnl said:**
> ...
A class that contains functions like this is called a 'pure virtual' class because you cannot instantiate it directly since it has no implementation for these methods.  Interfaces in Java or .NET are similar to a pure virtual class, since you are required to implement all their functions when inheriting from them.

Actually, the term used in C++, as in Java, is 'abstract' class, not 'pure virtual' (or in the case of Java, 'interface').

Read more: [http://www.javaworld.com/javaworld/javaqa/2001-04/03-qa-0420-abstract.html](http://www.javaworld.com/javaworld/javaqa/2001-04/03-qa-0420-abstract.html)

---

### Post by Can+~ on 2009-12-02
You may consider the Decorator Pattern:

[http://en.wikipedia.org/wiki/Decorator_pattern](http://en.wikipedia.org/wiki/Decorator_pattern)

Applying "Filters" as the above example shown, although I'm not sure what you're trying to achieve.

---

### Post by jellyfisharepretty on 2009-12-04
@MadCow108: Thanks for the precision on virtual classes.  It was more subtle than I thought.

> **nvteighen said:**
> The issue of having to constantly rewrite main() is just unimportant. Think about it: if you're manipulating your classes' interfaces, you'll have to modify the caller functions. There's nothing wrong in that.

That's true.  Seems like there is no way around it.

> **nvteighen said:**
> But the issue of having main() growing larger is a problem. Very probably, your classes aren't abstract enough or need more classes or just mix OOP with procedural programming and create functions... You know: "1 function = 1 task". The main()'s task should be managing the program's most essential starting up and shutting down steps

Don't desperate. Java and C++ are very much the same: static typed OOP languages... and C++ influenced Java. The differences you'll encounter will be actually just very minor (pointers are just a technical issue); the concepts are pretty much the same. You're not jumping from Java to Forth (dynamic typed stack-based language with RPN syntax :p).

I do like the idea johnl suggested earlier.  There are a lot more classes in his scheme and I can see that it will allow me to change really easily the order filters are applied in, once I've programmed them.  I just cringe at the number of header files I will have to maintain with so many classes :-?

C++ is not too bad so far, I'm actually getting use to pointers (OpenCV makes heavy use of them).  I understand the concept well , I think, but for me they still are a scary thing in that it is easy to make mistakes using them, while Java seems a bit more "fool-proof" in comparison.  Well, I don't want to start a Java vs C++ debate here, but my first impression is that there are a few more barriers in place in Java to keep me safe, while C++ will allow me to do more, but at greater risk of mistake.

> **Can+~ said:**
> You may consider the Decorator Pattern:
That's an interesting idea, thanks for the input.

---

### Post by nvteighen on 2009-12-04
> **jellyfisharepretty said:**
> 
I just cringe at the number of header files I will have to maintain with so many classes :-?

Don't think about that ;)

> 
C++ is not too bad so far, I'm actually getting use to pointers (OpenCV makes heavy use of them).  I understand the concept well , I think, but for me they still are a scary thing in that it is easy to make mistakes using them, while Java seems a bit more "fool-proof" in comparison.  Well, I don't want to start a Java vs C++ debate here, but my first impression is that there are a few more barriers in place in Java to keep me safe, while C++ will allow me to do more, but at greater risk of mistake.


What I meant was that C++ and Java are pretty much in the same paradigm. But beware: C++ will allow you to do more in lower-level programming, while Java will allow you to do more in higher-level one. Java primitives are meant to be nearer to human concepts and that's usually a good thing for anything that doesn't need to refer to machine-related stuff (e.g. optimization).

Programming refers to conceptual realities in our minds... The computer is "accidental", as you can always execute your code in your mind. Of course there *is* a reason why we use computers :p But, of course, we sometimes need to set our computer up and do computer-related work; there languages as C, C++, Objective-C, Forth, ASM and others come into play.

Of course, sometimes you've got a project that essentially is a high-level programming task but that needs to be really optimized; C++ is usually used for that kind of situation (games are one of these). I personally hate C++, but there are some facts nobody can deny: C++ has a niche and you better use it (like it or not) until there's a better language for it :p

---

### Post by grayrainbow on 2009-12-04
> **nvteighen said:**
> Don't think about that ;)



What I meant was that C++ and Java are pretty much in the same paradigm. But beware: C++ will allow you to do more in lower-level programming, while Java will allow you to do more in higher-level one. Java primitives are meant to be nearer to human concepts and that's usually a good thing for anything that doesn't need to refer to machine-related stuff (e.g. optimization).

Programming refers to conceptual realities in our minds... The computer is "accidental", as you can always execute your code in your mind. Of course there *is* a reason why we use computers :p But, of course, we sometimes need to set our computer up and do computer-related work; there languages as C, C++, Objective-C, Forth, ASM and others come into play.

Of course, sometimes you've got a project that essentially is a high-level programming task but that needs to be really optimized; C++ is usually used for that kind of situation (games are one of these). I personally hate C++, but there are some facts nobody can deny: C++ has a niche and you better use it (like it or not) until there's a better language for it :p
C++ is supposed to support C style programming, plus templates, plus multiple inheiritance(it's quite different than java ;) ), and virtually is the only really multiparadigm language, which comes with its cost, namely complexity.
And strangly...I always thought programming is exactly putting things from outside world into computers world(if your computer run VM that's no different, it's still in computer world), but otherwise one definitely should try "execute" the code in his/her head(some people consider this to be impossible in some situations).

About pointers - they are extreamly easy once you stop afraid of them. You could segment fault - sure you can, people learn from mistakes, and you could be sure: the world won't end from that ;)

I'm curious, does OP follow what basicly every programmer realize at most after 3 projects - "Exam the problem, write your documentation , exam the problem again, fix documentation and write tests which will fail, just after that start coding"?

---

### Post by CptPicard on 2009-12-04
> **grayrainbow said:**
> C++ is supposed to support C style programming, plus templates, plus multiple inheiritance(it's quite different than java ;) )

I hope you are not insinuating that nvteighen's views would come from mere exposure to Java-style single-inheritance and that he wouldn't *understand* what multiple inheritance means. You are completely underestimating him in this case, which is unfortunately of course not uncommon at all with people whose programming experience is limited to C++, and whose attitude comes from elevating what they know.

When it comes to multiple inheritance and object-orientedness, I would suggest you begin by checking out what *multiple dispatch* means, for instance (mind you, I want to bet you right now you have to look that up), and how Lisp multimethods work -- just for starters. It expands the concept quite a bit.

> and virtually is the only really multiparadigm language, which comes with its cost, namely complexity.

Nope. For a genuine multiparadigm language that does things remarkably cleanly, see Lisp. The criticism of C++ tends to come from the way C++ integrates what it seeks to be. The complexity comes from the language's inherent design, not some superiority of managing to encompass things. It's more subtle than most C++-guys are willing to admit.
 
> 
And strangly...I always thought programming is exactly putting things from outside world into computers world(if your computer run VM that's no different, it's still in computer world)

Exactly. That's why programming language conceptuals are so interesting, in particular because the languages are theoretically equivalent (the "old-fashioned" Turing-completeness, according to you...) 

> 
, but otherwise one definitely should try "execute" the code in his/her head(some people consider this to be impossible in some situations).

I can give you a *horrible* Turing tarpit in terms of a single-instruction CPU (subtract-and-jump-if-negative, for example) where you can try to execute the code in your head all you want. It is probably doable but it is not helpful, or even in any way productive of insight. Mathematics on the other hand is very declarative, but most of our understanding of the world is based on it. You can formulate computable functions in terms of pure-functional declarations, and leave the manual, unintellectual parts to the compiler, all the while being mindful that the human input the computer will not ever be able to do will have to be done in the latter just the same... so which one will it be?

> 
About pointers - they are extreamly easy once you stop afraid of them. You could segment fault - sure you can, people learn from mistakes, and you could be sure: the world won't end from that ;)


I wish this random slapping about being "afraid" of pointers stopped. Bragging about them is pointless, and that is exactly why they are considered unimportant especially for the learner by some. A pointer is semantically an indirect reference, which as a concept is present in a lot of other programming languages. A simple array index can serve the exact same purpose, and once you understand those, you understand pointers (a pointer is a typed index to an implicit underlying array, essentially). The whole point of the "pointer discussion" is that it introduces unnecessary issues into the learning curve that are better understood as a part of the picture given by higher-level languages. *There is absolutely nothing magical in the pointer itself, per se*.

Of course, most of the time the whole deal is just totally insignificant even for people who are completely competent in juggling their pointers when need be, such as myself. I am not going to start writing a whole object-management framework from scratch just to prove that I can when I want a closure (a much more interesting programming language construct than a pointer), for example.

---

### Post by Can+~ on 2009-12-04
> **grayrainbow said:**
> C++ is supposed to support C style programming, plus templates, plus multiple inheiritance(it's quite different than java), and virtually is the only really multiparadigm language, which comes with its cost, namely complexity.

The word you're seeking, is "complicated", not "complex".

And I wonder what's your definition for "multi-paradigm".

> **grayrainbow said:**
> About pointers - they are extreamly easy once you stop afraid of them. You could segment fault - sure you can, people learn from mistakes, and you could be sure: the world won't end from that ;)

The only difficult thing about pointers, is the syntax, and C++ adds to the confusion with it's own "&" operator as part of function arguments.

Actually, pointers are so mechanical that I always see the benefit of being abstracted, not having to deal with the little troubles they cause.

---

### Post by grayrainbow on 2009-12-05
> **Can+~ said:**
> The word you're seeking, is "complicated", not "complex".

The only difficult thing about pointers, is the syntax, and C++ adds to the confusion with it's own "&" operator as part of function arguments.

Actually, pointers are so mechanical that I always see the benefit of being abstracted, not having to deal with the little troubles they cause.
No I meant complex ;)
C is quite old language, and most popular in present days, which wouldn't be the case if something so general like pointer wasn't with IMO the best syntax for it's purpose available. And probably you're right about '&' operator(it's overloadable), usually when one uses it in function meaning is quite clear.
Actually, when one does image processing, lot of pointless abstractions is the last thing needed(speaking from game programmer experience).

@CptPicard, I don't get what's the point to write tones of words and say nothing...and completely out of OP subject. May I suggest you: given your love to hight level scripts...write ease for "Thoughts on scripts"...since I sometimes made use of some of them, I may consider not so pointless as your attempt here.

---

### Post by nvteighen on 2009-12-05
> **grayrainbow said:**
> C++ is supposed to support C style programming, plus templates, plus multiple inheiritance(it's quite different than java ;) ), and virtually is the only really multiparadigm language, which comes with its cost, namely complexity.


I was talking about something really different and very related to the OP's post. The OP was a bit afraid to have difficulties of learning C++ because of his past experience with Java. I told him Java and C++ are not that different because the "paradigm" used is quite similar, in contrast to jumping from Java into Forth. Ok, maybe I used "paradigm" in a not totally technical sense, wanting to also mean "mindset" besides "programming paradigm". My fault.

What I've said is just common sense. C++ is a language that, while it supports procedural programming, it is meant to be used with OOP in order to get its best. C-like code in C++ is usually considered bad. There's template metaprogramming too, but this metaprogramming is usually used (although it allows other stuff too) for creating generic OOP. The center of C++ is imperative static-typed OOP.

And Java's center is imperative static-typed OOP too. Ok, there are things you've got in one language and not in the other. Java lacks multiple inheritance... but C++ coders tend to consider multiple inheritance as bad design and so they don't use it (something I can't understand). Coding in Java and in C++ leads to very similar solutions because both were designed to be used for OOP-style programming...

Programming languages lead you to one or another preferred "way of things", even though being Turing-complete and supporting all "ways" in theory. This is not a bad thing; it's the necessary way to do it... Imagine designing a language that supported **all** kinds of programming **perfectly**: You wouldn't ever finish designing it :p

If I code in Perl, all will become a world of strings and regexps. If I code in Python, classes combined with iterable objects. If I code in Lisp, cons-pairs and symbols (i.e. code). If I code in C++, classes combined with containers and pointers... similar to Java. In Forth, I just get a FIFO stack to pile stuff into it :p

> 
About pointers - they are extreamly easy once you stop afraid of them. You could segment fault - sure you can, people learn from mistakes, and you could be sure: the world won't end from that ;)


Of course. The issue is syntax, as Can+~ said. C++ references do this easier a bit.

> 
I'm curious, does OP follow what basicly every programmer realize at most after 3 projects - "Exam the problem, write your documentation , exam the problem again, fix documentation and write tests which will fail, just after that start coding"?

LOL... You've forgot about new specifications when you were just about to solve the problem.

---

### Post by grayrainbow on 2009-12-05
@nvteighen, first lesson on recursion: scroll up a bit, find grayrainbow previous post, and read it, then read it again, then again...

---

### Post by dribeas on 2009-12-05
Well, most people see in C++ only the OO, and that cannot be discussed. But the fact is that metaprograming is a language in itself and allows you to do things that are unachievable in Java (just as functional languages do offer things that are unachievable in C++: you can always write your own interpreter and blah, blah, blah...).

While most people also think that in C++ everything should be OO, that is not the case. In fact, in many cases it is better to extract functionality out of the classes and into free functions (there is no object orientation in STL algorithms, and the Stephanov, the original author, does not even believe in OO).

I have been programming for quite a bit of time in C++, and I can tell you that while being a beginner you do believe in those concepts, but as you grow in experience and knowledge, you move from the pure OO (single-inheritance, utility classes to group similar functions...) and you start doing your share of template programming, prior to understanding metaprogramming...

From Java to C++, the shortest path is doing the same Java-like code in C++ (and at this point the hard parts is resource management and learning to love RAII) and start moving from there on (adding const-correctness is the next step, understanding that references in C++ are not references in Java and that references in Java are in fact pointers in C++ comes right away).

---

