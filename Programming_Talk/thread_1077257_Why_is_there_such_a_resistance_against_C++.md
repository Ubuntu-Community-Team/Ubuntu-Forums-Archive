---
title: "Why is there such a resistance against C++?"
date: 2009-02-22
forum: Programming Talk
---

### Post by MadMan2k on 2009-02-22
reading through some mailing list, like mesa, gtk or compiz. I noticed that there seem to be some kind of resistance against C++ among OSS developers. Instead everyone tries to implement their own object system on top of C.

Is there any rationale behind this?

Note that this thread is about C++ vs. C and nothing else. Especially not about C++ vs. functional programming languages. ;)

---

### Post by howlingmadhowie on 2009-02-22
> **MadMan2k said:**
> reading through some mailing list, like mesa, gtk or compiz. I noticed that there seem to be some kind of resistance against C++ among OSS developers. Instead everyone tries to implement their own object system on top of C.

Is there any rationale behind this?

Note that this thread is about C++ vs. C and nothing else. Especially not about C++ vs. functional programming languages. ;)

basically, if you're not using inheritance (which you shouldn't be doing anyway), C is just as object oriented as C++. C++ doesn't solve any of the problems C has and just adds a huge amount of its own. it's not a good language definition.

---

### Post by nvteighen on 2009-02-22
Because C++ is a mess. It's a language that's very low-level in its original C heritage and very high-level in its later STL features. So, you get several semantical layers one on top of the other and you never really know what is C++ really about. Is it C with Classes? Is it STL code? Is it generic code? What is really C++ of all of its features?

The other issue is that C++ is nowadays a bit redundant. If you want low-level access, go for C and you have a much cleaner language... you can easily implement an object system if you like it. Or, if you're lazy, go for Objective-C (though it's as slow as Java, as I'm told). If you want high-level features, then there are plenty of other alternatives much cleaner than C++.

Maybe you want fast high-level features... but then your code is probably a semantical mess. As you see, I'm not concerned on efficiency at all, but at the linguistical-cognitive approach: that a program is a communication-abstraction device for some knowledge. (Possibly I'm in the wrong forum, but I enjoy annoying programmers :))

---

### Post by jimi_hendrix on 2009-02-22
> **howlingmadhowie said:**
> basically, if you're not using inheritance (which you shouldn't be doing anyway), C is just as object oriented as C++. C++ doesn't solve any of the problems C has and just adds a huge amount of its own. it's not a good language definition.

whats wrong with inheritance...

---

### Post by Zugzwang on 2009-02-22
> **jimi_hendrix said:**
> whats wrong with inheritance...

Nothing, if applied correctly in places where this actually makes sense. Probably howlingmadhowie has a bad experience with academic over-application of this concept. Maybe he also refers to C++'s pitfall of not declaring methods to be virtual by default.

---

### Post by CptPicard on 2009-02-22
> **howlingmadhowie said:**
> basically, if you're not using inheritance (which you shouldn't be doing anyway), C is just as object oriented as C++.

Hmm.. I would say that virtual functions are exactly the feature that I usually miss in my own object-oriented C (which most of my non-trivial C usually is). A lot of objects end up carrying a lot of "override" function pointers, and from there, writing your own virtual function table implementation is just a step away. 

Actually, doing OOP in C is a good way to appreciate why someone would get the idea of creating C++ in the first place, although the full blown OOP approach taken by C++ and especially Java often feels too rigid (IMO).

But of course, there's objective-C to scratch that "lightweight virtual functions for structs" itch. :)

> C++ doesn't solve any of the problems C has and just adds a huge amount of its own. it's not a good language definition.

I guess the issue is that it adds a lot of stuff and you have to be pretty cautious with those additions so that they don't trip you up. The added complexity is quite something compared to a lot of other languages, and you still, you don't have something like closures :)

---

### Post by Ferrat on 2009-02-22
A little off-topic but still fairly on the same subject. 

What about C++0x? which problably will be C++09, hopes? dreams? thoughts about what it will do to C++, good? bad? 
seems most people feel it will just make it more messy?

---

### Post by howlingmadhowie on 2009-02-22
> **jimi_hendrix said:**
> whats wrong with inheritance...

let's say you have a class which represents a stack (i'll write it in java because i can get the syntax right without spending time googling). this class has many methods, two of which are
```

public void PushOneObject(Object obj);

public void PushLotsOfObjects(Collection<Object> coll);

```

let's say you want to extend this class to include the ability to count how many objects are stored, so you write the following:

```


class MyStack extends SimpleStack {

  private int numObjs = 0;

  ...

  public void PushOneObject(Object obj) {
    numObjs++;
    super.PushOneObject(obj);
  }

  public void PushLotsOfObjects(Collection<Object> coll) {
    numObjs+=coll.size();
    super.PushLotsOfObjects(coll);
  }
}

```

and you instantiate the class and add three objects using PushOneObject and then a group of three objects using PushLotsOfObjects. then you ask for the value of numObjs and the answer is 9. 

how did numObj get to be 9? well, in the superclass, PushLotsOfObjects works by looping over coll and calling for each object PushOneObject, which is now of course PushOneObject in the subclass, so each object gets counted twice. The way the methods were implemented in the parent class has an effect when you extend the class. 

this is of course a pretty harmless example, but in some cases it isn't. the technique of composition solves this problem, of course. but you can also use that in C.


---- edit

the classic example in java (and i presume it works in C) is when you use an equals method to determine if someone is allowed to do something. for example:

```


boolean Checkpassword(String pass) {
   return pass.equals("PaSsWoRd");
}


```

which is okay until someone comes along with the following code:

```

class MyString extends String {

  boolean equals(String s) {
    return true;
  }

  ...
}

```

which is why String is final in java. Of course you can make a long list of things the attacker would need to be able to do to get that code to run and bypass the safety of java.lang.String being defined final, but my rant about java will have to wait for another day...

---

### Post by Gordon Bennett on 2009-02-22
> **Ferrat said:**
> A little off-topic but still fairly on the same subject. 

What about C++0x? which problably will be C++09, hopes? dreams? thoughts about what it will do to C++, good? bad? 
seems most people feel it will just make it more messy?

It will only continue doing this:

[IMG]http://i516.photobucket.com/albums/u328/kloria77/overloaded-car.jpg[/IMG]

---

### Post by CptPicard on 2009-02-22
Well, you're just designing wrong there. Don't do that ;) 

But yes, true, functionality in inheritance hierarchy that has side-effects in the class' internals can cause the fragile base class problem, and related problems. There are a lot of handy ways to make use of inheritance though... one method I use a lot is separating a lot of functionality in my classes into small tiny bits that are then overridden in child classes and then get called from a parent class. 

This sort of design should pretty much be of a value-returning type (that is, it's "functional" -- it doesn't mess with object's state, except maybe through calling other well-defined methods).

The alternate of course is using a delegate...

---

### Post by dwhitney67 on 2009-02-22
> **howlingmadhowie said:**
> let's say you have a class which represents a stack (i'll write it in java because i can get the syntax right without spending time googling). this class has many methods, two of which are
```

public void PushOneObject(Object obj);

public void PushLotsOfObjects(Collection<Object> coll);

```

let's say you want to extend this class to include the ability to count how many objects are stored, so you write the following:

```


class MyStack extends SimpleStack {

  private int numObjs = 0;

  ...

  public void PushOneObject(Object obj) {
    numObjs++;
    super.PushOneObject(obj);
  }

  public void PushLotsOfObjects(Collection<Object> coll) {
    numObjs+=coll.size();
    super.PushLotsOfObjects(coll);
  }
}

```

and you instantiate the class and add three objects using PushOneObject and then a group of three objects using PushLotsOfObjects. then you ask for the value of numObjs and the answer is 9. 

how did numObj get to be 9? well, in the superclass, PushLotsOfObjects works by looping over coll and calling for each object PushOneObject, which is now of course PushOneObject in the subclass, so each object gets counted twice. The way the methods were implemented in the parent class has an effect when you extend the class. 

this is of course a pretty harmless example, but in some cases it isn't. the technique of composition solves this problem, of course. but you can also use that in C.

...


Was the OP not asking about C++?  What does this have to do with C?

In the example provided above, I fail to see how numObj will be set to 9.  Using the MyStack object, you add 3 single objects, followed by 3 other object that are part of a collection.  The base class SimpleObject does NOT call the derived class for anything; only the derived class calls the base class.

I think you need to re-evaluate your example, or that, spend a little more time programming (better code).

---

### Post by simeon87 on 2009-02-22
> **dwhitney67 said:**
> Was the OP not asking about C++?  What does this have to do with C?

In the example provided above, I fail to see how numObj will be set to 9.  Using the MyStack object, you add 3 single objects, followed by 3 other object that are part of a collection.  The base class SimpleObject does NOT call the derived class for anything; only the derived class calls the base class.

I think you need to re-evaluate your example, or that, spend a little more time programming (better code).

Funny how people need to correct others on how to program. If you read his post, he meant the following behaviour for the superclass:

```

class SimpleStack {

    public void PushOneObject(Object obj) {
        // handle pushing of one object
    }

    public void PushLotsOfObjects(Collection<Object> coll) {
        for ( Object o : coll ) {
            PushOneObject(o);
        }
    }
}

```

If you now subclass SimpleStack and override both of these methods as described, calling the PushOneObject for 3 objects and PushLotsOfObjects for a collection of 3 items will cause the counter to be nine.

But as said earlier, this is a design flaw in the subclass, not a problem with the base class SimpleStack. Edit: well, it depends on how the behaviour of PushLotsOfObjects is described in the documentation and on whether you know that PushLotsOfObjects calls PushOneObject or not.

---

### Post by dwhitney67 on 2009-02-22
> **simeon87 said:**
> Funny how people need to correct others on how to program. If you read his post, he meant the following behaviour for the superclass:

```

class SimpleStack {

    public void PushOneObject(Object obj) {
        // handle pushing of one object
    }

    public void PushLotsOfObjects(Collection<Object> coll) {
        for ( Object o : coll ) {
            PushOneObject(o);
        }
    }
}

```

If you now subclass SimpleStack and override both of these methods as described, calling the PushOneObject for 3 objects and PushLotsOfObjects for a collection of 3 items will cause the counter to be nine.

But as said earlier, this is a design flaw in the subclass, not a problem with the base class SimpleStack. Edit: well, it depends on how the behaviour of PushLotsOfObjects is described in the documentation and on whether you know that PushLotsOfObjects calls PushOneObject or not.

This must be a fluke of Java, but this does (would) not occur in C++.

In Java, methods are implicitly defined as "virtual", whereas in C++ they are not.  If one were to define the Push methods as virtual in a C++ application, then yes, of course the result would be 9.  In the example provided, there is no convincing rationale to declare the methods as virtual; its best to make them non-virtual and let subclasses override, if necessary, the method with their own implementation.

---

### Post by Zugzwang on 2009-02-22
> **dwhitney67 said:**
> This must be a fluke of Java, but this does (would) not occur in C++.

Basically, this is just an example of a parent-class calling functions from its child. If functions are declared to be virtual, the same happens in C++:

[PHP]
#include <iostream>

class A {
public:
    virtual void one() { std::cout << "Hello World\n"; };
    virtual void two() { one(); };
};

class B : public A {
public:
    virtual void one() { std::cout << "Hello Universe\n"; };
};

int main() {
    B b;
    b.two();
}
[/PHP]
This program will greet the universe although the two() method is inherited from the class A, which would normally only greet the world.

---

### Post by dwhitney67 on 2009-02-22
> **Zugzwang said:**
> Basically, this is just an example of a parent-class calling functions from its child. If functions are declared to be virtual, the same happens in C++:

[PHP]
#include <iostream>

class A {
public:
    virtual void one() { std::cout << "Hello World\n"; };
    virtual void two() { one(); };
};

class B : public A {
public:
    virtual void one() { std::cout << "Hello Universe\n"; };
};

int main() {
    B b;
    b.two();
}
[/PHP]
This program will greet the universe although the two() method is inherited from the class A, which would normally only greet the world.

This is a nice tidy example; thank you.

If you had not declared the methods as virtual, then the base class' two() method would have called the base class' one() method; not the one in the derived class.

In Java, method are implicitly defined as virtual (as I re-discovered again).

---

### Post by MadMan2k on 2009-02-22
> **Ferrat said:**
> A little off-topic but still fairly on the same subject. 

What about C++0x? which problably will be C++09, hopes? dreams? thoughts about what it will do to C++, good? bad? 
seems most people feel it will just make it more messy?
at least I think that C++0x will improve C++ greatly. The "merge" of boost in STL will fix some design flaws in the STL and the core language improvements like Closures are great too.

I must admit, that I directly learned C++0x and did not really spend much time with C++98, so I am probably biased because of that.

But I think that C++(0x) is currently the only language which gives high performance at a reasonable abstraction layer. (In C++0x one is able to mostly ignore the C roots)

---

### Post by nvteighen on 2009-02-22
> **MadMan2k said:**
> at least I think that C++0x will improve C++ greatly. The "merge" of boost in STL will fix some design flaws in the STL and the core language improvements like Closures are great too.

I must admit, that I directly learned C++0x and did not really spend much time with C++98, so I am probably biased because of that.

But I think that C++(0x) is currently the only language which gives high performance at a reasonable abstraction layer. (In C++0x one is able to mostly ignore the C roots)

But then, my question gets stronger: What is C++? If C++0x makes you ignore the C roots, then, is it the same language as it was before?

---

### Post by Ferrat on 2009-02-22
> **nvteighen said:**
> But then, my question gets stronger: What is C++? If C++0x makes you ignore the C roots, then, is it the same language as it was before?

As I understand it, you can do it the old way but that is more for legacy than anything else?

---

### Post by nvteighen on 2009-02-22
> **Ferrat said:**
> As I understand it, you can do it the old way but that is more for legacy than anything else?
But then, why C++ insists in being perfect in all senses? It tries to be backwards compatible even with C, low-level but also high-level, support all possible programming paradigms (now functional programming with the inclusion of closures). That defeats the purpose of having programming languages: you design a language to make something because you want to tackle that specific problem... Science works that way, by restricting the research fields in order to have a solution; is better in Science to have a good partial solution than not have the optimal total solution (e.g. The Unified Field Theory, although it's interesting, is not needed to understand why stuff falls to the floor).

C++ IMO aims to be the "ultimate" programming language. At the end, that makes it a language impossible to manage... or maybe actually different languages that are compiled by a "C++ Compiler" and nobody knows what C++ actually is, as it is an aggregate of completely different semantical systems all supossedly the same language.

The case of C++ is not of, say, the C program that finally implements a high-level feature. No, in that case, you create a high-level environment by using the elements of the C semantic system (which is pretty clean, let me say)... The most high-level C code you can think of (e.g. GTK+) will still be C code in all what that means. That's creating new meaning (semantical systems) **within** the existing one, not creating a conglomerate as C++ does by making everything a built-in or standard feature (btw, my opinion on whether standard features are part of the language or not is not clear... I tend to think they're not, but some reflexions have been pointing me that I may be wrong; stay tuned ;)).

That's why **I** resist myself against C++. Because it's a linguistical nonsense.

---

### Post by MadMan2k on 2009-02-22
but still it is more expressive than C is and it also has solves several problems you encounter when you try to go high-level with C, like the already mentioned Objects or String processing.
So in comparison to plain C it both improves readability and prevents you from reinventing the wheel.

---

### Post by CptPicard on 2009-02-22
> **nvteighen said:**
> (now functional programming with the inclusion of closures).

Hmm. I wonder if the C++0x closures really are "real" in the sense that the lambda's binding environment genuinely exists on its own, or whether they're just some callback syntactic sugar that is still tied to the stack... I get this feeling that a genuine closure essentially requires a garbage collector (or otherwise you must do a lot of very nasty bookkeeping).

> 
 That defeats the purpose of having programming languages: you design a language to make something because you want to tackle that specific problem...

Except if it's Lisp, which tackles all problems since 1958, and elegantly too ;)

> At the end, that makes it a language impossible to manage... or maybe actually different languages that are compiled by a "C++ Compiler" and nobody knows what C++ actually is, as it is an aggregate of completely different semantical systems all supossedly the same language.

Well, my issue tends to be with the way all those systems interact on the technical level -- it produces a lot of detail you just need to know and manage and live with. There is more abstraction but you still need to "work a lot" to get the benefits.

> btw, my opinion on whether standard features are part of the language or not is not clear... I tend to think they're not, but some reflexions have been pointing me that I may be wrong

Personally I do not put much weight on "arguments from libraries", for example. Libraries -- even the standard library -- follow from the base language design. If the latter is bad, no amount of libraries will really help, as libs are "more of the same". If the design is solid, elegant, useful libraries will just come about.

---

### Post by Wybiral on 2009-02-22
Have you ever tried to make sense of a large mess of template metaprogramming in C++? It's disgusting. The fact that it, C-style macros, and low level pointer arithmetic voodoo all exist in the same language, it doesn't help the case of readability much.

Too bad I'm forbidden by the OP from bringing up Lisp macros in this thread, or I would :)

---

### Post by CptPicard on 2009-02-22
> **Wybiral said:**
> 
Too bad I'm forbidden by the OP from bringing up Lisp macros in this thread, or I would :)

Sssh!! You're not allowed to bring LOLCODE-like languages into discussion, you fanboy!! :o

---

### Post by MadMan2k on 2009-02-22
> **CptPicard said:**
> Hmm. I wonder if the C++0x closures really are "real" in the sense that the lambda's binding environment genuinely exists on its own, or whether they're just some callback syntactic sugar that is still tied to the stack... I get this feeling that a genuine closure essentially requires a garbage collector (or otherwise you must do a lot of very nasty bookkeeping).
I am not entirely sure, but in C++0x one can store lambda expressions in function objects. There is also reference counted GC available. On the other hand there is also a special type for closures, which only use references. (and therefore can be expanded at compile time)

So I would say you will get both variants with C++0x - just what you would expect :D

---

### Post by howlingmadhowie on 2009-02-22
> **CptPicard said:**
> Sssh!! You're not allowed to bring LOLCODE-like languages into discussion, you fanboy!! :o

in case anybody doesn't know them, i've just discovered the lecture series held at mit in the 80s called structure and interpretation of computer programmes which can be found [here]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/").

it's really good stuff :)

---

### Post by howlingmadhowie on 2009-02-22
> **nvteighen said:**
> But then, why C++ insists in being perfect in all senses? It tries to be backwards compatible even with C, low-level but also high-level, support all possible programming paradigms (now functional programming with the inclusion of closures). That defeats the purpose of having programming languages: you design a language to make something because you want to tackle that specific problem... Science works that way, by restricting the research fields in order to have a solution; is better in Science to have a good partial solution than not have the optimal total solution (e.g. The Unified Field Theory, although it's interesting, is not needed to understand why stuff falls to the floor).

C++ IMO aims to be the "ultimate" programming language. At the end, that makes it a language impossible to manage... or maybe actually different languages that are compiled by a "C++ Compiler" and nobody knows what C++ actually is, as it is an aggregate of completely different semantical systems all supossedly the same language.

The case of C++ is not of, say, the C program that finally implements a high-level feature. No, in that case, you create a high-level environment by using the elements of the C semantic system (which is pretty clean, let me say)... The most high-level C code you can think of (e.g. GTK+) will still be C code in all what that means. That's creating new meaning (semantical systems) **within** the existing one, not creating a conglomerate as C++ does by making everything a built-in or standard feature (btw, my opinion on whether standard features are part of the language or not is not clear... I tend to think they're not, but some reflexions have been pointing me that I may be wrong; stay tuned ;)).

That's why **I** resist myself against C++. Because it's a linguistical nonsense.

my problems with C++ are really of practical nature. i don't like it when others are able, nay, encouraged to overwrite + and similar. code just gets difficult to read. also there are real big horrible mistakes in the language such as if you change the definition of a private variable or function in a class you have to recompile all code that uses that class, which is just stupid. 

and compiling takes a long time, because the language definition is sooooo complex.

---

### Post by Wybiral on 2009-02-22
> **howlingmadhowie said:**
> in case anybody doesn't know them, i've just discovered the lecture series held at mit in the 80s called structure and interpretation of computer programmes which can be found [here]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/").

it's really good stuff :)

Indeed, the book and the lectures are very enlightening, especially when you're first getting into functional programming (it's one of the shoves that tipped me over the edge towards hating the more procedural languages)

---

### Post by days_of_ruin on 2009-02-22
> **howlingmadhowie said:**
> my problems with C++ are really of practical nature. i don't like it when others are able, nay, encouraged to overwrite + and similar. code just gets difficult to read. also there are real big horrible mistakes in the language such as if you change the definition of a private variable or function in a class you have to recompile all code that uses that class, which is just stupid. 

**and compiling takes a long time**, because the language definition is sooooo complex.

+1.
Compiling wesnoth which uses boost took me 4+ hours iirc.:(

---

### Post by Can+~ on 2009-02-23
To illustrate:

High level languages usually try to offer the top-level tools:

[IMG]http://img.photobucket.com/albums/v517/CanXp/python/graph_normal.png[/IMG]
(very raw example)

The user develops vertically, meaning that learning how the low-level functionality actually works is optional. This is an example on how a language should be, offering the tools as "black boxes" that do what they are asked to.

In the case of C++, it's like it wants to offer both:

[IMG]http://img.photobucket.com/albums/v517/CanXp/python/graph_cpp_export.png[/IMG]
(again, very raw example)

So the idea of "black boxes" fade, and to use properly the high-level tools, you still need how to use C properly, you mostly need to know what's going on under the hood to actually be able to work. You can create an make instances of classes, but without a garbage collector you still need to free the memory manually.

---

### Post by howlingmadhowie on 2009-02-23
oh yes. the lack of a garbage collector in c++ makes life extremely difficult. also the lack of a runtime environment for things like type checking can lead to real problems. at least java throws a ClassCastException when something goes wrong during runtime. i have no idea what C++ does.

---

### Post by nvteighen on 2009-02-23
> **CptPicard said:**
> 
Well, my issue tends to be with the way all those systems interact on the technical level -- it produces a lot of detail you just need to know and manage and live with. There is more abstraction but you still need to "work a lot" to get the benefits.

That's because you have several semantic layers: even though you have lots of high-level features, you still have to deallocate your memory manually because there the low-levelness comes across and there's nothing you can do against it (well, apart from changing the language...).

IMO, it's all nonsense :p. In C you expect to free memory manually, because it is supposed to be totally low-level. Perfect, that's fine in C because the language is organically designed into one single system. In Python you expect not to free your memory because you understand it is a high-level language... and it's a consistent system. C++ instead doesn't seem consistent: tries to be high-level but also low-level with all contradictions that means.

---

### Post by MadMan2k on 2009-02-23
as I said C++0x fixes many of the issues you mentioned. You will get Garbage Collection and better Syntax for Collection Types. You can [take a look at my blog post]("http://www.rojtberg.net/199/c-becoming-usable/"), where I introduced some of its features.

---

### Post by nvteighen on 2009-02-23
> **MadMan2k said:**
> as I said C++0x fixes many of the issues you mentioned. You will get Garbage Collection and better Syntax for Collection Types. You can [take a look at my blog post]("http://www.rojtberg.net/199/c-becoming-usable/"), where I introduced some of its features.
Then the question is: Is C++0x the same language as the previous C++? It may be a weird question, but it implies to have a straight definition on when we consider a language's evolution to be that strong to break the system and be considered a new language.

Your blog post seems to show that C++ is trying to escape from its lower-levelness and become a higher-level language. But then, that may play against C++'s "traditional" market and play in favor of more moderate solutions like Objective-C (for OOP low-level work) or true high-level languages (Perl, Python, Java, ...).

If C++0x instead keeps the low-level features, then you'll get lots of redundant ways to do the same thing: you'll be able to create arrays with the array type or with the C-style... and then, what's the point? That will probably make the language collapse into subdialects: Low-Level C++0x and High-Level C++0x, and all the possible intermediate values... and all supposed to be the very same language.

So, I still ask what is C++? What does C++ want to be? I just don't understand where it tries to go.

---

### Post by MadMan2k on 2009-02-23
> **nvteighen said:**
> Then the question is: Is C++0x the same language as the previous C++? It may be a weird question, but it implies to have a straight definition on when we consider a language's evolution to be that strong to break the system and be considered a new language.
well most of the new features were already available through the boost third party library.
With C++0x they were just polished up a bit and the API will be frozen, so it will be more feasible for long running projects.

As for the rest; probably my view on C++ is more pragmatic; I only care about the performance I get at a certain abstraction level and not so much about whether the syntax is awkward at certain places. (as long as it keeps the abstraction level)

And if you are comfortable with the abstraction level of Java, then C++ will give you the best performance for it.

Plain C on the other hand, while having similar performance, is in no way meant to to be high level and thus fails to provide this abstraction layer.

But nevertheless many developers (hello GObject, hello Vala) try to implement this abstraction on top of it which eventually fails.
So I was wondering why they are not simply using C++?

I mean In some way you can say GObject is ugly too, since it uses all that ugly preprocessor directives to force features onto C which are not meant to be implemented at that level.

---

### Post by eye208 on 2009-02-23
> **nvteighen said:**
> In C you expect to free memory manually, because it is supposed to be totally low-level. Perfect, that's fine in C because the language is organically designed into one single system. In Python you expect not to free your memory because you understand it is a high-level language... and it's a consistent system. C++ instead doesn't seem consistent: tries to be high-level but also low-level with all contradictions that means.
The low-level part of C++ (i.e. raw pointers) exists for one single purpose: to wrap C APIs in container classes. In properly designed C++ code you will never see manual deallocation of resources. The containers take care of that automatically when running out of scope. This is called RAII ("Resource Acquisition Is Initialization") and is vastly superior to garbage collection in my opinion.

Python requires container classes for C APIs too. The only difference is that you can't write those containers in Python itself. You need a separate low-level language to do that.

---

### Post by movieman on 2009-02-24
> **eye208 said:**
> In properly designed C++ code you will never see manual deallocation of resources. The containers take care of that automatically when running out of scope.

class foo
{
// stuff
}

class bar: public foo
{
// stuff
}

class snafu: public foo
{
// stuff
}

How do you create a vector holding objects of type bar and snafu (and any other class derived from foo) without using pointers? Maybe there's something I've missed, but I'm not aware of any way to do so; obviously you can wrap them in some smart pointer class, but they're still pointers.

IMHO the big problem with C++ is not pointers, though they are probably responsible for 50% of the bugs in poorly-written C++ code, but that 'smart' people can so easily write code that's impossible for anyone else to understand without spending six months figuring out what it does.

---

### Post by scourge on 2009-02-24
> **movieman said:**
> class foo
{
// stuff
}

class bar: public foo
{
// stuff
}

class snafu: public foo
{
// stuff
}

How do you create a vector holding objects of type bar and snafu (and any other class derived from foo) without using pointers? Maybe there's something I've missed, but I'm not aware of any way to do so; obviously you can wrap them in some smart pointer class, but they're still pointers.

Yeah, you can use shared_ptr. eye208 said that you shouldn't do manual deallocation, which is not the same thing as not using pointers.

> IMHO the big problem with C++ is not pointers, though they are probably responsible for 50% of the bugs in poorly-written C++ code, but that 'smart' people can so easily write code that's impossible for anyone else to understand without spending six months figuring out what it does.

Clever code is discouraged in every programming language, and it can always be a problem. Well-written C++ is not that difficult to read, assuming that the reader isn't a complete beginner.

---

### Post by eye208 on 2009-02-24
> **movieman said:**
> obviously you can wrap them in some smart pointer class, but they're still pointers.
Pointers are not bad per se. But raw pointers are. Once they are stored in appropriate containers, they are not a problem any more. In my opinion the most important lesson in learning C++ is how to get rid of raw pointers.

The nice thing about RAII is that it goes beyond memory management. You can make file handles close themselves, mutex objects unlock themselves etc.

---

### Post by ajackson on 2009-02-24
> **eye208 said:**
> The nice thing about RAII is that it goes beyond memory management. You can make file handles close themselves, mutex objects unlock themselves etc.
**If** the classes are coded well (so I'd assume all the base ones are) but it would also be possible for a third party class (or one you code yourself) to mismanage memory. RAII is a good memory/resource management tool if implemented right.

Returning more on-topic, C++ really needs to decide which level it wants to be and the only way to do that (if it aims for higher level) is to more or less sever it's links with C. Of course this will never happen so, IMO, C++ will continue being a troubled language. Java learned from C++'s mistakes, C# is learning from Java's (and Java is learning from Java's), maybe the next-gen version of C++ needs to learn from all three.

---

### Post by jespdj on 2009-02-24
C++ is powerful, but it's also complicated.

It doesn't have automatic memory management (garbage collection), so you must manually manage memory and make sure you free any memory that you've allocated. Because you can forget to clean up properly easily, especially in a big and complicated program, it's very easy to make nasty memory leaks. It has pointers, just like C, which make it prone to bugs with invalid pointers.

Languages like Java and C# have automatic memory management and no direct pointers, which makes it easier to program in those languages.

It's unfortunately easy to misuse C++'s powerful features and write software that is very hard to understand and maintain. Also, C++ has features that enable you to program subtle bugs that are hard to find. For example, if you don't make a destructor **virtual** and you delete an object using a pointer to a base class object, the destructor will not be called properly, leading to memory leaks and other strange behaviour.

I'd highly recommend the book [Effective C++](http://www.aristeia.com/books.html) by Scott Meyers - very good learning material for any serious C++ programmer. It will show you a whole list of subtle issues with C++.

---

### Post by CptPicard on 2009-02-24
> **jespdj said:**
> C++ is powerful, but it's also complicated.
...
It will show you a whole list of subtle issues with C++.

That's the problem. An increase in complexity that does not produce a corresponding increase in "power", but a whole list of "subtle issues" (that a lot of people are really proud of being able/willing to handle, simply because it's "hard"). As far as programming languages go, I have always felt like simplicity, elegance and "power" go together. This is why C is more "elegant" for a low-level language (cleanly low-level and simple), and Lisp is elegant for a high-level language (very abstract, yet builds on a small number of strong, universal concepts). 

In "elegant, strong and simple" languages a certain genericity is always present as a design element in reducing the amount of "stuff" that is explicitly needed in the language. It always amazes me that even some supposedly experienced software developers don't seem to understand or appreciate this. It's almost as if I told them that *software architecture doesn't matter* in their chosen language.

A somewhat analogous example that I am dealing with right now is J2EE... I came back to it at version 3 after being disgusted at the unnecessary complexity of version 2. Version 3 does everything version 2 did (and then some), and it does so *with so much less*. In other words, they did not just "write more libraries", but made use of better general concepts such as annotations...

---

### Post by jespdj on 2009-02-24
> **CptPicard said:**
> A somewhat analogous example that I am dealing with right now is J2EE... I came back to it at version 3 after being disgusted at the unnecessary complexity of version 2. Version 3 does everything version 2 did (and then some), and it does so *with so much less*. In other words, they did not just "write more libraries", but made use of better general concepts such as annotations...
(Going offtopic a bit, but...) Yes, the complexity of EJB 2.x was what made EJB impopular and sparked projects like the Spring Framework and Hibernate. EJB 3.x is much simpler and better and stole a lot of ideas from Hibernate.

---

### Post by nvteighen on 2009-02-24
> **MadMan2k said:**
> 
As for the rest; probably my view on C++ is more pragmatic; I only care about the performance I get at a certain abstraction level and not so much about whether the syntax is awkward at certain places. (as long as it keeps the abstraction level)

I'm actually very little concerned about the syntactic issue... Perl's syntax is awkward and I can live with it :)

My concern is about the semantics of the language and how it affects on its design. That's directly related to how good is the abstraction level implemented... The issue is: if you have very high-level concepts but you still have to deal with pointers, then which is your level of abstraction? High or low? Maybe both... but then you only may expect chaos.

> 
Plain C on the other hand, while having similar performance, is in no way meant to to be high level and thus fails to provide this abstraction layer.

But nevertheless many developers (hello GObject, hello Vala) try to implement this abstraction on top of it which eventually fails.
So I was wondering why they are not simply using C++?

Why people are not using C++? Well, in those cases you can ask why people don't use Objective-C. But GObject (I'm not familiar with Vala) doesn't fail IMO... it doesn't savagely modify the language in order to create a new "base" abstraction layer, but it uses the building blocks from C to build a new abstraction layer... It's like what Boost did before C++0x... the problem is when you make that standard and part of the language's definition.

> I mean In some way you can say GObject is ugly too, since it uses all that ugly preprocessor directives to force features onto C which are not meant to be implemented at that level.

You surely mean the casting system? Well, that's a nasty feature in order to get inheritance that's there only because of a low-level detail. I agree with you here.

> **eye208 said:**
> The low-level part of C++ (i.e. raw pointers) exists for one single purpose: to wrap C APIs in container classes. In properly designed C++ code you will never see manual deallocation of resources. The containers take care of that automatically when running out of scope. This is called RAII ("Resource Acquisition Is Initialization") and is vastly superior to garbage collection in my opinion.

So, C++ low-level is just to bring compatibility with another language? The question is: Why should C++ do that?

The RAII technique is just a logical extension of the stack-based allocation system you get in C. But, how many times you are forced to dynamically allocate stuff through new/delete?

> 
Python requires container classes for C APIs too. The only difference is that you can't write those containers in Python itself. You need a separate low-level language to do that.

That's an advantage, IMO. You mix functionality, not languages: you give compatibility but make both semantical systems be clearly different, therefore you have one tool for low-level (C or C++, remember Python can also deal with it) and one for high-level (Python). I think it simplifies stuff... (also, have you used C code in Python? It's annoyingly easy).

---

### Post by eye208 on 2009-02-24
> **jespdj said:**
> It doesn't have automatic memory management (garbage collection), so you must manually manage memory and make sure you free any memory that you've allocated. Because you can forget to clean up properly easily, especially in a big and complicated program, it's very easy to make nasty memory leaks. It has pointers, just like C, which make it prone to bugs with invalid pointers.
You are wrong. Please read my comment above.

If you manage resources manually using raw pointers, you are not a C++ programmer. You are a C programmer using a C++ compiler.

---

### Post by eye208 on 2009-02-24
> **nvteighen said:**
> So, C++ low-level is just to bring compatibility with another language? The question is: Why should C++ do that?
Because most existing APIs are in C. Usually there is a struct declaration and several functions expecting pointers to that struct. Basic OOP in C. Wrapping this in a C++ class is easy.

> The RAII technique is just a logical extension of the stack-based allocation system you get in C. But, how many times you are forced to dynamically allocate stuff through new/delete?
I allocate stuff like this:
```
shared_ptr<type> p(new type);
```
I never use *delete*. When the pointer and all copies of it go out of scope, the object will delete itself. Risk of memory leaks: zero.

---

### Post by ajackson on 2009-02-24
> **eye208 said:**
> If you manage resources manually using raw pointers, you are not a C++ programmer. You are a C programmer using a C++ compiler.
Except C++ **allows** you to use raw pointers, using the functionality of a language doesn't stop you being a programmer in that language. Using certain stuff might make you a bad programmer in that language but that is highly subjective.

> I never use delete. When the pointer and all copies of it go out of scope, the object will delete itself. Risk of memory leaks: zero. 
Just hope and pray if you use third party classes that they weren't written by non-C++ programmers :)

---

### Post by MadMan2k on 2009-02-24
> **nvteighen said:**
> I'm actually very little concerned about the syntactic issue... Perl's syntax is awkward and I can live with it :)

My concern is about the semantics of the language and how it affects on its design. That's directly related to how good is the abstraction level implemented... The issue is: if you have very high-level concepts but you still have to deal with pointers, then which is your level of abstraction? High or low? Maybe both... but then you only may expect chaos.
as eye208 said you can always do:
```
shared_ptr<type> p = new type();
```
of course that is not as nice as if C++ would accept
```
type p = new type();
```
and always use shared_ptr by itself. You may also argue that having to know about shared_ptr lowers the abstraction layer, but I think one can put that to "awkward syntax", if you pretend that noone told you about "type*".

I also think that the "but what if third party..." argument is moot too. Bad written third party code can always blow your program - no matter which language you use.

> **nvteighen said:**
> So, C++ low-level is just to bring compatibility with another language? The question is: Why should C++ do that?
simply because C++ evolved out of C and was not really designed. Thats a big disadvantage when it comes to the language.
But when it comes to compilers this is a big advantage since you (currently) get the best optimized code out of all languages.

> **nvteighen said:**
> 
You surely mean the casting system? Well, that's a nasty feature in order to get inheritance that's there only because of a low-level detail. I agree with you here.
Yeah I was referring to inheritance. In order to get that right in with GObject, you have to write a lot of boilerplate code, which makes you know how inheritance in GObject works instead of allowing you just to use it.
This is also coupled to namespaces in GObject - you have to expand them by hand, and thus know way to much detail about inheritance. This should be the work of the compiler.

Taken from the GTK tutorial:
```

    /* you have always to specify the namespace
       no way to "include" it, which would allow
       writing window_new */
    win = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    
    /* you have to know that gtk_window inherits from g_object
       which provides the signal_connect method
       it should be enough to write
       win.signal_connect
       and the compiler should figure out which method to call */
    g_signal_connect(G_OBJECT (win), "delete_event",
		      G_CALLBACK (delete_event), NULL);

```

---

### Post by Gordon Bennett on 2009-02-24
> **MadMan2k said:**
> 
This is also coupled to namespaces in GObject - you have to expand them by hand, and thus know way to much detail about inheritance. This should be the work of the compiler.

Taken from the GTK tutorial:
```

    /* you have always to specify the namespace
       no way to "include" it, which would allow
       writing window_new */
    win = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    
    /* you have to know that gtk_window inherits from g_object
       which provides the signal_connect method
       it should be enough to write
       win.signal_connect
       and the compiler should figure out which method to call */
    g_signal_connect(G_OBJECT (win), "delete_event",
		      G_CALLBACK (delete_event), NULL);

```

That's more of a programmatical solution rather than a linguistic one - GTK's way of implementing these types of objects is to me a very elegant and simple solution for this reason:
It gets things done efficiently rather than forcing a programmer to wade through tons of semantic ******** just to get something done.

---

