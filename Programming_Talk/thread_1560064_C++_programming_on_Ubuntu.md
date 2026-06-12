---
title: "C++ programming on Ubuntu"
date: 2010-08-24
forum: Programming Talk
---

### Post by Daniel0108 on 2010-08-24
Hi! :D

I have dual boot with Windows 7 and Ubuntu... But I only use Ubuntu :P
Windows 7 only for some programs...
I use Ubuntu for some months now.
I'm a C++ and PHP programmer :)
And I think C++-programming on Ubuntu is PERFECT :D
I'm using g++ and gedit ;)
I learned the basics of bash now.
Now I am learning Makefile-programming.
I made some programs in C++ now.
Now I tested SDL on Ubuntu and it worked perfectly on first try!!!
Ubuntu is perfect!!!
Maybe my school will use Edubuntu soon :)
Can someone give me some tips or tricks for C++ programming on Ubuntu?
And.. What do you think about C++ programming on Ubuntu?
Hope there is no post like mine in the board.. If it is, please say me ;) I'm new to this board :P

Yours,
Daniel

---

### Post by nvteighen on 2010-08-24
First, welcome!

Second, I hate C++ :D

Third, ok, maybe you could in time try learning to use some more advanced editors like vim or emacs... or some IDE... that might be more helpful in any programming task. Not that gedit is bad, I love it and started with it, but it will eventually become too "small".

---

### Post by Random_Dude on 2010-08-24
Hi! Welcome.

Most of the things I've programmed were in gedit (not a big programmer :p), but I've been trying [geany]("http://www.geany.org/") and it looks pretty cool. Very simple and clean IDE.

Cheers :cool:

---

### Post by Lootbox on 2010-08-24
If you're looking for a more integrated IDE (not as lightweight, though), I'd give Code::Blocks a shot. It's nice.

And, at the risk of getting into a pointless programming language war, why do you hate C++ nvteighen? Sure, it's not beginner friendly at all, but that doesn't make it a bad language.

---

### Post by cap10Ibraim on 2010-08-24
> **Lootbox said:**
> 
And, at the risk of getting into a pointless programming language war, why do you hate C++ nvteighen? Sure, it's not beginner friendly at all, but that doesn't make it a bad language.
[IMG]http://www.deimeke.net/dirk/blog/uploads/G7WyP.gif[/IMG]

---

### Post by dtoronto on 2010-08-24
Code::Blocks or Eclipse

---

### Post by Random_Dude on 2010-08-24
Programing language wars? Does such a thing exist?

I've seen sports teams, console and even OS wars, but never programing language wars.:lolflag:

Anyway, Code::Blocks is also cool, I've tried it only on Windows thought.
I'm not sure if it's a good advice, but I think that if you don't write advanced programs, a more simple and lightweight IDE is better.

Cheers :cool:

---

### Post by Daniel0108 on 2010-08-25
I'm now using Code::Blocks :D
It's great!
Thanks for all your posts ;)
Yea.. Gedit is fine but too small :)
For example, I cannot debug with gedit...
PS: I´m a C++ AND C programmer ;)
In C++, I'm programming more C-Style :)
Yours,
Daniel

---

### Post by Lootbox on 2010-08-25
> **Random_Dude said:**
> Programing language wars? Does such a thing exist?

Criticize Python in this forum and you'll see what I mean.

---

### Post by Daniel0108 on 2010-08-25
xD :P
:lolflag:Programming language wars ;)
nvteighen, if you hate C++, which programming language do you prefer?
Yours,
Daniel

---

### Post by X.Cyclop on 2010-08-25
I'd recommend Code::blocks, but recently i was using gedit.:)

> **No programming language is perfect. There's not even a single best language; there're only languages well suited or perhaps poorly suited for particular purposes.** [Herbert Mayer]

---

### Post by nvteighen on 2010-08-25
> **Lootbox said:**
> 
And, at the risk of getting into a pointless programming language war, why do you hate C++ nvteighen? Sure, it's not beginner friendly at all, but that doesn't make it a bad language.

Because it's a schizoid mess: it's a low-level language that aims to be also a high-level language... and target everything at once.

Even if you restrict yourself to STL, to not use pointers and to use references instead, to its highest level features and avoid "C-like C++", in order to understand what's happening you still have to think in low-level terms... Therefore, it's a whole mess.

Small example:
```

#include <iostream>

class MyClass
{
public:
    int& data; // !!

    MyClass(int& mydata) : data(mydata) {}
};

MyClass do_it()
{
    int z = 8;

    MyClass myObj(z);

    return myObj;
}

int main()
{
    MyClass myObj = do_it();
    
    std::cout << myObj.data << std::endl; // !! line 26

    return 0;
}

```

That code is incorrect, regardless that it works under my machine... though valgrind correctly points out that at line 26 an invalid "below the stack" read is performed. But you know that no compiler will detect this error at compile-time (and in my machine, not even the OS will at runtime :P).

Now, to understand why that's wrong, you have to think in terms of call stack... and supposedly references are the higher-level feature C++ puts in in order to replace pointers. But nevertheless we still experience the "dangling pointer" effect (so common in C) with a C++ reference (guess why).

The correct code would have the class not hold a reference, but the integer... or create an integer at the heap!

Meanwhile, the very same code works in Python flawlessly:
```

#!/usr/bin/env python

class MyClass(object):
    def __init__(mydata):
        self.data = mydata

def do_it():
    z = 8 # Keeping things like in the C++ example
    myObj = myClass(z)

    return myObj

def main():
    myObj = do_it()
    print(myObj.data)

# Boilerplate
if __name__ == "__main__": 
    main()

```

Why? Because the language is truly a high-level one and knows that if I pass an integer, then, myObj.data should not be a reference... But if it were some object allocated at heap (strings, for example), then, it would be a reference. As you see, that way you can forget about the call stack at all when writing some code.

Ok, now you say that's because Python has that inmutable vs. mutable data types thing that makes it able to distinguish when to use a reference and when not... Then why does this Perl snippet also work? (where references have to be made explictly with the \ operator):

```

#!/usr/bin/env perl

use strict;
use warnings;

sub make_class 
{
    # Using a hash as a "class"... Very common thing to do in Perl.

    my $mydata = \$_[0]; # Creating reference to first argument.
    my %obj = ('data' => $mydata);
    return %obj;
}

sub do_it
{
    my $z = 8;
    my %myObj = make_class($z);
    
    return %myObj;
}

sub main
{
    my %myObj = do_it;
    print ${$myObj{'data'}}; # Dereferencing
    print "\n";

    return;
}

main;
0;

```

This is just one example that shows the difference between real high-level programming and "low-level programming + high-level features" (C++). In really well-done high-level programming languages, you just don't need to care about what's beneath your abstraction level... That's exactly why you first chose a high-level language, because if you really care about what happens at some lower-level, you need something else. But C++ mixes everything with poor results: its higher-level stuff seems like those libraries that give C some higher-level structures but they still need pointers... The difference is that in the case of C you know that's because of C is intended to be low-level... and well, you can abstract a lot but it's still a low-level language and you cope with that because it was your decision to use that library in C. On the other hand, C++ tries not to be low-level by doing the same those libraries do for C, but it throws them as part of the standard language... and therefore makes the problem part of the language. And then you get these weird cases that do work in real high-level languages while not in C++...

In summary: I hate C++ because it mixes abstraction levels by design. IMO, something like Java is the language C++ should have been. Even though I hate it, it may be possible that C++ is useful for a number of projects... but I guess that's mainly because of the available libraries there are.

> **Daniel0108 said:**
> 
nvteighen, if you hate C++, which programming language do you prefer?


My favorites are Common Lisp, Scheme, Python, C, Objective-C... But I always try to use the best language for the job... I love Scheme but it's pretty useless :P

---

### Post by Lootbox on 2010-08-26
> **nvteighen said:**
> 
Small example:
```
...
```
That code is incorrect, regardless that it works under my machine... though valgrind correctly points out that at line 26 an invalid "below the stack" read is performed. But you know that no compiler will detect this error at compile-time (and in my machine, not even the OS will at runtime :P).

Now, to understand why that's wrong, you have to think in terms of call stack... and supposedly references are the higher-level feature C++ puts in in order to replace pointers. But nevertheless we still experience the "dangling pointer" effect (so common in C) with a C++ reference (guess why).

Imposing absurd restrictions on your code hardly shows anything about the weaknesses of a language. Why would you on one hand forbid yourself from using pointers while simultaneously allowing yourself to use reference variables? That's not an issue with the language - that's just straight-up poor design. 

Yes, you need pointers to have an elegant solution to this. As I said, C++ is not beginner-friendly. The upside of the need to understand pointers is that once you do, you have the ability to explicitly control the behavior of your data (i.e. only allow cloned storage or referenced storage, which is much more likely to be practical in an actual application, not a concocted example).

> This is just one example that shows the difference between real high-level programming and "low-level programming + high-level features" (C++). In really well-done high-level programming languages, you just don't need to care about what's beneath your abstraction level... That's exactly why you first chose a high-level language, because if you really care about what happens at some lower-level, you need something else. But C++ mixes everything with poor results: its higher-level stuff seems like those libraries that give C some higher-level structures but they still need pointers... The difference is that in the case of C you know that's because of C is intended to be low-level... and well, you can abstract a lot but it's still a low-level language and you cope with that because it was your decision to use that library in C. On the other hand, C++ tries not to be low-level by doing the same those libraries do for C, but it throws them as part of the standard language... and therefore makes the problem part of the language. And then you get these weird cases that do work in real high-level languages while not in C++...

In summary: I hate C++ because it mixes abstraction levels by design. IMO, something like Java is the language C++ should have been. Even though I hate it, it may be possible that C++ is useful for a number of projects... but I guess that's mainly because of the available libraries there are.

Of course you're not going to get good results if you indiscriminately mash together different paradigms within a single program, while not understanding what's going on. It's really not hard to keep them separate (i.e. if you don't want to deal with raw C arrays, use the STL vector). I freely admit that you can't jump into C++ programming like you can with Python, but I don't think that warrants a blanket "I hate C++" prejudice.

---

### Post by Daniel0108 on 2010-08-26
:P
Has programming wars started now? xDD :)
btw: you  can write main() instead of int main() too... and you dont have to return 0 or anything else in the main function!! Even if its int main()... Thats C++...
C-style is much better, i think ;) For example, I like printf more than cout :P
Heres a example for a WORKING C++ code:
```

#include <iostream>

main() {
std::cout << "Hi";
}

```
THATS WRONG!!! But it works?! :P
Yours,
Daniel

---

### Post by Paul820 on 2010-08-26
Yes, it's started, it always does. ;)

You should use 'int main()', just because you can do it without int doesn't mean you should. Doing it without int before main produces this output
```
error: ISO C++ forbids declaration of 'main' with no type
```
It doesn't take much more typing to do it right :)

---

### Post by Daniel0108 on 2010-08-26
oh, cool :P
I had an IDE, and it took that main() :P
and my friend uses this main() with g++?!
I always use int main and return 0 :P
PS: it shouldn't be void main, too :P
Yours,
Daniel

---

### Post by nvteighen on 2010-08-26
> **Lootbox said:**
> Imposing absurd restrictions on your code hardly shows anything about the weaknesses of a language. Why would you on one hand forbid yourself from using pointers while simultaneously allowing yourself to use reference variables? That's not an issue with the language - that's just straight-up poor design.

The reason were various: first, pointers are usually considered "C-like" in the C++ community and too "low-level". Yes, I'd also have used pointers if that was production code, but then one would be blatantly conceding that C++ isn't the "higher-level" language people like Soustroup like to say it is. If to make C++ useful you still need to use features that actually are from C, then something is wrong. References are considered to be a "higher-level" construct than pointers because they're supposedly always bound to an object (which is untrue in C++).

Second, because I expect formal-logical languages to be coherent. That's why I took an "absurd restriction" approach (actually, a controlled variable approach): if the language is right, then it should work as expected: you say C++ is "higher-level" than C and that's why it has templates, STL, etc., so why the hell do you still have to think about the stack in order to know what a reference is bound when the idea of references is not to be just memory addresses but a way to "call by reference" vs. "call by value"? Ok, in my example I force a weird situation where call by reference is redundant, but the language should not care about my mistakes, but work in a consistent way. It doesn't because C++ ends up screwing the idea of "call by reference" using a hidden pointer... And pointers are just a way to call by value, where the value just happens to be some memory address (and therefore, it simulates calling by reference to some extent).

> 
Of course you're not going to get good results if you indiscriminately mash together different paradigms within a single program, while not understanding what's going on. It's really not hard to keep them separate (i.e. if you don't want to deal with raw C arrays, use the STL vector). I freely admit that you can't jump into C++ programming like you can with Python, but I don't think that warrants a blanket "I hate C++" prejudice.

No, it's C++ who mashes together different "paradigms" (I think you mean "levels of abstraction") without my consent. I decided to use references because, let's say, I'm happy with them... And all of sudden, I realize they work as syntactic sugar for the awful C pointer syntax... I wanted call by reference and I just get the same issues I get in C... Why? I didn't declare any pointer: I declared a reference. The reason behind all of this is simple: you can't have real references without a garbage collector, per definition, because you'd need to have objects' life-time go beyond the limitations of the C to ASM calling convention.

I placed the examples in Python and, specially, the Perl one to show how coherent languages work. C is 100% coherent by not making any effort in introducing stuff that doesn't match the language's base level of abstraction (well, except the entry keyword...).

Ok, you can tell me I don't know how references work in C++ and that they are designed to work this way... But that behaivor just replicates pointers'. Is that a good designed language? Then why would I use references save for syntactic sugar and avoiding dereferencing pointers? From another point of view, if C++ is higher-level than C, why make the new operator return a pointer instead of a reference? 

Again, this is just one issue that IMO illustrates the major problem I said about C++: its attempt to cover everything. You've got a language that at the same time makes you think about call stack while allowing you, from its standard, to have really abstract stuff like std::vector. And you may say this is a weird example, but what if you want to have a vector of references (or pointers)? The effect will be the same if the object is in the stack... Why do I have to think at both abstraction levels? In C I just think of the call stack and such stuff and I'm fine with it. In Lisp I just think of abstracted objects and I'm fine with it too. In Objective-C they did it right and extended C in a pure low-level fashion, leaving everything else be part of NeXTStep (ok, you may not be able to do anything without that library, but it's not part of the language).

But again, this isn't just me. You surely know the C++ "FQA" and you'll see similar issues popping out everywhere in C++ (of course some stuff is questionable). I don't remember if the author addresses this issue in particular.

Maybe the example should have been a bit less extreme and less concocted. Also, the explanation was badly written. Ok, I can see that, but I guess it still shows the point.

---

### Post by Lootbox on 2010-08-27
> **nvteighen said:**
> The reason were various: first, pointers are usually considered "C-like" in the C++ community and too "low-level". Yes, I'd also have used pointers if that was production code, but then one would be blatantly conceding that C++ isn't the "higher-level" language people like Soustroup like to say it is. If to make C++ useful you still need to use features that actually are from C, then something is wrong. References are considered to be a "higher-level" construct than pointers because they're supposedly always bound to an object (which is untrue in C++).

If that's the case (I don't know the C++ community), then I see it as a misguided interpretation of references. The fact of the matter is that you can't separate pointers from references. I agree - references are nothing more than syntactic sugar, saving you the effort of tedious dereferencing in situations where you would use them. This is why I was surprised at your example; I don't think of references as a high-level abstraction at all. C++ is perfectly consistent in that sense, since you should never be using a reference where the equivalent pointer operation wouldn't make sense.

Even for languages that do operate at a higher level of abstraction, there are still low-level concepts you need to understand in order to program correctly. Take this example in Java (a "sweep-everything-under-the-carpet-and-forget-about-it" style language):

```
public static void main(String[] args) {
    ArrayList<Integer> list = new ArrayList<Integer>();

    foo(list);
    System.out.println(list.get(0));
    // prints "1"

    bar(list);
    System.out.println(list.get(0));
    // prints "1"
}

private static void foo(ArrayList<Integer> list) {
    list.add(1);
}

private static void bar(ArrayList<Integer> list) {
    list = new ArrayList<Integer>();
    list.add(10);
}
```
I'm a TA for an introductory computer science course at a university, taught in Java. -Everyone- struggles to understand the difference between these two examples. You can't explain how parameter passing works for objects in Java without explaining the difference between pass-by-reference and pass-pointer-by-value. And that's fundamentally a low-level concept that requires an understanding of pointers.

Is this a flaw in the Java language? I wouldn't say it is. There are certain concepts that you simply can't use abstraction to ignore.

---

### Post by CptPicard on 2010-08-27
> **Lootbox said:**
> And that's fundamentally a low-level concept that requires an understanding of pointers.

It's mostly a matter of understanding the concept of value types vs. reference types of any kind; not necessarily pointers in the lowest-level memory address value sense. The semantic issue of "values that refer to other values" is a broader, more general one than pointers.

> There are certain concepts that you simply can't use abstraction to ignore.

It seems to me that people who think in terms of low-level languages tend to take the position that abstraction is used to "hide" or "ignore" things. I couldn't disagree more, really... higher-level abstractions just simply are different, and in many cases, more informative about higher-level concepts and ideas than the low-level concepts. Conceptually, the higher-level concepts often include and subsume the low-level ones.

---

### Post by nvteighen on 2010-08-27
> **Lootbox said:**
> If that's the case (I don't know the C++ community), then I see it as a misguided interpretation of references. The fact of the matter is that you can't separate pointers from references. I agree - references are nothing more than syntactic sugar, saving you the effort of tedious dereferencing in situations where you would use them. This is why I was surprised at your example; I don't think of references as a high-level abstraction at all. C++ is perfectly consistent in that sense, since you should never be using a reference where the equivalent pointer operation wouldn't make sense.

I agree. But then, don't call them to be "names for objects" in the C++ 1998/2003 standard (Note in 8.3.2.1) and just declare them to be syntactic sugar for section 8.3.1 (pointers).

OK, I don't know how normative a note in an ISO standard might be, but the idea of "name for object" is the idea behind call by reference. The Perl example accomplishes this perfectly by making the reference actually be a name for an object (therefore making the object persist until all references are unused). 

> 
```
public static void main(String[] args) {
    ArrayList<Integer> list = new ArrayList<Integer>();

    foo(list);
    System.out.println(list.get(0));
    // prints "1"

    bar(list);
    System.out.println(list.get(0));
    // prints "1"
}

private static void foo(ArrayList<Integer> list_par) {
    list_par.add(1);
}

private static void bar(ArrayList<Integer> list_par) {
    list_par = new ArrayList<Integer>();
    list_par.add(10);
}
```


Hm... What you have there is the interaction of two different references in bar's scope. Just for clarity, I've renamed the parameters in bar and foo. Let's see what bar does:

1. Assings parameter list_par to refer to object list at main.
2. Reassigns list_par to a new ArrayList<Integer>. But, in main, you still have list referring to the original ArrayList, so that one is not wiped out by the GC.
3. Adds element 10 to list_par.
4. list_par dies when bar returns to main.
5. You print list.

The key to that behaivor is that you just assigned the name "list_par" to a *new* object. If Java references were just sugar for dereferencing pointers (like in C++), you'd expect 10 in the second line. References are something else than that: they're names for an object and all you did is switching the reference of a name, keeping the other name in main. So, in bar, the name "list_par" is first referring to the same object that the name "list" does in main... but then you change that.

In Common Lisp lingo this is called shadowing:
```

; SLIME 2010-07-21
CL-USER> (defclass dummyClass ()
           ())
#<STANDARD-CLASS DUMMYCLASS>
CL-USER> (defun do-something (myDummyClass)
           (setf myDummyClass 6)) ; "myDummyClass = 6;"
DO-SOMETHING
CL-USER> (defparameter someDummyObj (make-instance 'dummyClass))
SOMEDUMMYOBJ
CL-USER> someDummyObj
#<DUMMYCLASS {B5D2261}>
CL-USER> (do-something someDummyObj)
6
CL-USER> someDummyObj
#<DUMMYCLASS {B5D2261}>
CL-USER> 

```

This is exactly why references can't be reassigned in C++: Because they aren't references, they're pointers but don't want to look like pointers and therefore, they hide their true nature so you can't in theory dangling references... In practice, I created a dangling reference in C++.

---

