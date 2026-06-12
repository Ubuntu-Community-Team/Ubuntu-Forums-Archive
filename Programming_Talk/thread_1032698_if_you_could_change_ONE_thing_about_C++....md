---
title: "if you could change ONE thing about C++..."
date: 2009-01-06
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-06
what would it be?

---

### Post by dwhitney67 on 2009-01-06
The misconception that it is a difficult language to learn.

---

### Post by efexD on 2009-01-06
Ability to work directly with hardware.

---

### Post by jimi_hendrix on 2009-01-06
i would probably go with more helpful segfault messages/error messages

---

### Post by samjh on 2009-01-06
> **efeXor said:**
> Ability to work directly with hardware.

Do you mean you want to enhance the existing capability, or remove it entirely?

---

### Post by efexD on 2009-01-06
Enhance... of course.

---

### Post by pmasiar on 2009-01-06
> **dwhitney67 said:**
> The misconception that it is a difficult language to learn.

This makes little sense, as "being difficult" is not attribute of the language itself but feeling/thinking by language users about the language. If people's brains do not appreciate C++ greatness, it's problem with the brains not with the language?

And it is funny to see who thanks you for such opinion. Not the multi-language experts I would say :-)

Basically you propose to change brains/thinking processes of the language users to better fit to what **you** consider human brains should work like, regardless of what research and experience says they do work.

C++ was designed as it was for the reason: backward compatibility with C mated with OOP, and result is the ugly offspring :-) C++ serves as example what happens when language designer cannot say 'no' to features which do not fit the idea. Another such language (for different reasons) is Perl. 

And it is interesting that some language (Python) is ready to break with backward compatibility even with old version of itself to achieve simplicity and extendability without being overly complex - to fit human brains as they are, not as they should be according to the uber-smart designer. That means language designer is humble as accepts reality of human brains, and designes with the limits of human thinking in mind.

So thanks but no thanks. I keep my thinking, my brains, you keep C++. :-)

---

### Post by Zugzwang on 2009-01-07
There's one annoying feature: The automatic generation of copy-constructors and assignment operators for classes which contain "naked" pointers - This will fail in 99% of the cases. In this case, it would be ok to give a compiler error. 

The auto-generated assignment operator could also make use of the explicitly defined copy-constructor.

---

### Post by monkeyking on 2009-01-07
array slicing, nested functions and support for closures.

---

### Post by CptPicard on 2009-01-07
+1 for closures support. Functors are too cumbersome. Contrast to Java which is very nice with the way it allows you to create ad hoc anonymous classes on demand so that you can quickly for example create an interface implementation to adapt to some type requirements... if one could have things the Java way plus with it being a genuine closure and not an artificially restricted hack like in Java, that would be good.

Also, templates are a bit of a mess... in particular I dislike the way it makes all of your implementation creep into header files...

---

### Post by jimi_hendrix on 2009-01-07
> **pmasiar said:**
> And it is funny to see who thanks you for such opinion. Not the multi-language experts I would say :-)


uhh...i know parts of more languages then i can remember (due to my want to explore a little) and i dont find C++ very hard...like i said i just wish segfault messages were more helpful

---

### Post by Reiger on 2009-01-07
@pmasiar: I trust you Chinese isn't a difficult language to learn. Count the number of non-native speakers who can master it to the effect they can present themselves credibly as native speakers?

Point is: any language requires you to think in a certain way which is not obvious to someone not accustomed to it. If you want to become any good at functional programming you better drop the concept of destructive update. I suggest you redefine difficult: I trust Python NOT to be a difficult language to learn, I trust it fairly difficult to express such trivialities as:
```

data Tree a = (Tree a,Tree a) | Leaf a

```

---

### Post by Cracauer on 2009-01-07
I want keyword parameters to functions.

Compile-time only is fine with me and would address most of the concerns that people had when objecting to them.

In Lisp I also use compile-time keyword parameters most of the time, runtime is more for interactive utilities (C++ doesn't have interactive function so there).

---

### Post by Cracauer on 2009-01-07
> **CptPicard said:**
> +1 for closures support. Functors are too cumbersome. Contrast to Java which is very nice with the way it allows you to create ad hoc anonymous classes on demand so that you can quickly for example create an interface implementation to adapt to some type requirements... if one could have things the Java way plus with it being a genuine closure and not an artificially restricted hack like in Java, that would be good.


I wasn't happy with Java's inner classes since they don't give you access to everything that is in lexical scope, unlike ... well every other language with closures.

Doesn't Boost have some let, lambda and whatnot now? I didn't fiddle with them yet.

---

### Post by Kilon on 2009-01-07
I am curious Whether "D" programming language is a replacement to "C++" 

[http://www.digitalmars.com/d/2.0/comparison.html](http://www.digitalmars.com/d/2.0/comparison.html)

It seems to me like "your C++ prayers come true"

---

### Post by jimi_hendrix on 2009-01-07
ya and its compatable with C libraries!

---

### Post by cszikszoy on 2009-01-07
> **pmasiar said:**
> And it is funny to see who thanks you for such opinion. Not the multi-language experts I would say

You know nothing about me, yet you judge.  Interesting.

---

### Post by Kilon on 2009-01-07
Well I would not call C++ "difficult" per se. It can be very difficult sometimes but it is not difficult all the times. However I have to accept the fact that it belongs with the most difficult programming languages. Programming languages like python , pascal, basic etc. are many times more easy especially if you write a considerate amount of pages of code. 

But We live in the "AGE OF CHOICE" ,there is literally hundreds of  programming languages to choose from. And of course we cannot forget that we can mix them and combine them any way we want(Python with C++, .NET with C++, Java with Python [jython], python with .NET [ironpython] et. etc.). So everyone can follow a unique approach to programming.  

And when you realize this then you understand that the choice of a computer language is more emotional than practical. So it does not matter which language we choose , there are so many choices to be made after that , so this one is tiny. 

I like C++ as it is and I dont want it to change. It will always be on the first language I took seriously. It may not be my prefered choice anymore but this does not matter. I Love you C++ and I will never forget you. 

:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by CptPicard on 2009-01-07
> **Cracauer said:**
> I wasn't happy with Java's inner classes since they don't give you access to everything that is in lexical scope, unlike ... well every other language with closures.

That's the artificial restriction part... you're not allowed write access to the stack from inside the anon inner class. However... there is a way to get around it... the hack part.. write a parametrized Wrapper<T> type with get and set, and then do this:

```


int foo(final int x) {

   final Wrapper<Integer> ref = new Wrapper<Integer>();

   doSomething() { new SomeClass() {

     void innerMethod() {
       ref.set(x+5);
     }
 
   });

   return ref.get();

}


```

Interestingly, method parameters can also be set "final".

My code is full of this pattern... even to the point of returning these "closures" until I realize that the proper thing to do is to create a class and call the constructor, which I had built ;)

An important way to combine this further is to method calls in the enclosing class, which can be overriden methods in child classes. So you can clean this up a lot by stuffing these sort of things into a base class... this is how I do the neighbour callbacks in the "real Java version" of the analyzer tool we're hacking on in the other thread.

---

### Post by Cracauer on 2009-01-07
Nifty. But of course it's consing up the stuff at runtime and leaks even more memory than a closure does anyway.

---

### Post by pmasiar on 2009-01-07
> **Kilon said:**
> there is literally hundreds of  programming languages to choose from. 

Way more than that: [http://hopl.murdoch.edu.au/](http://hopl.murdoch.edu.au/) lists 8512 languages! [http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity](http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity) counts only 6,912 known living human languages!

> I Love you C++ and I will never forget you. 

LOL it's kinda sad to be devoted with such zeal to such boring language. If you want language worth the devotion (with hacker's appeal), try Forth, Perl or Lisp! :-)

---

### Post by CptPicard on 2009-01-07
> **pmasiar said:**
> 
LOL it's kinda sad to be devoted with such zeal to such boring language.

Now that I think of it, it would indeed feel weird to be religious about Java although I do use it as a tool most of the time.. :)

---

### Post by CptPicard on 2009-01-07
> **Cracauer said:**
> Nifty. But of course it's consing up the stuff at runtime and leaks even more memory than a closure does anyway.

Sure, you can't avoid producing some garbage out of the wrapper, but you really only need them for mutable stuff on stack in the local function scope. Everything else can be touched normally from inside the anonymous class. Also, for things like loop index variables, you can extract the loop body into a function call which turns the index into a "final" formal parameter.

It makes code a bit uglier esp. for the uninitiated, but this stuff still beats C++ functors IMO in ease of use, and has become a major programming style for me... IDEs are very good at hacking up ad hoc implementations of whatever you want at whatever place in code, and they can even refactor your "closure" out for you if it turns out that it starts to get a bit too big...

Performance-wise in a lot of situations, you better be doing something like this instead of, say, returning collections of stuff.. :)

---

### Post by jmartrican on 2009-01-07
Easier way to bind objects to function pointers.  I want thread support already.  A better auto_ptr (I like boost's shared_ptr).  I think the standard should look at some of the stuff that boost is doing and copy some of it.  I hate having to install boost on servers just to use a few key libs.

---

### Post by eye208 on 2009-01-08
> **jmartrican said:**
> I think the standard should look at some of the stuff that boost is doing and copy some of it.
That's already happening. Several parts of Boost will go into the upcoming C++0x standard.

---

### Post by Kilon on 2009-01-08
> **pmasiar said:**
> Way more than that: [http://hopl.murdoch.edu.au/](http://hopl.murdoch.edu.au/) lists 8512 languages! [http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity](http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity) counts only 6,912 known living human languages!



LOL it's kinda sad to be devoted with such zeal to such boring language. If you want language worth the devotion (with hacker's appeal), try Forth, Perl or Lisp! :-)
 
Actually the world we live in is made on the devotion , or should I say obsession. of people with certain things. I wish I was so devoted in my life even if you felt sad about me. But I get bored easiliy.

C++ is boring ? Well it is a matter of taste, I guess.  

Actually I really like C++ , never had anything against it. Actually I have nothing against any language. 

Wait...

Wait.....

ah...

YES!!!!

I hate one programming language!!!!

I mean real burning Hate!!!

I hate LOGO!!!! never liked it and never will. 

[http://en.wikipedia.org/wiki/Logo_(programming_language](http://en.wikipedia.org/wiki/Logo_(programming_language))

Burn in Hell LOGO!!! Hey it says here that LOGO is very similar to Lisp. Hmm...Burn in Hell Lisp then!!!

---

### Post by Magnes on 2009-01-08
I want foreach, but it's planned for the C++ x0 - [http://en.wikipedia.org/wiki/C%2B%2B0x](http://en.wikipedia.org/wiki/C%2B%2B0x) - so I suppose I'll get it one day. :)

---

### Post by emobrad on 2009-01-08
I'd change the haters to lovers.

---

### Post by meson2439 on 2009-01-08
It's about time C++ had interactive mode like python and haskell. Those interactive sessions sure helps during testing and debugging. That ought to reduce the amount of complains people have for C++.

---

### Post by jimi_hendrix on 2009-01-10
> **pmasiar said:**
> LOL it's kinda sad to be devoted with such zeal to such boring language. If you want language worth the devotion (with hacker's appeal), try Forth, Perl or Lisp! :-)

python and perl doesnt make the world go round...

---

### Post by techmarks on 2009-01-10
> **pmasiar said:**
> 


LOL it's kinda sad to be devoted with such zeal to such boring language. 

I'm thinking you meant this in jest, with all due respect, I find that a rather meaningless statement, C++ is very useful if not amusing!

---

### Post by techmarks on 2009-01-10
> **pmasiar said:**
> 


LOL it's kinda sad to be devoted with such zeal to such boring language. 

I'm thinking you meant this in jest, with all due respect, I find that a rather meaningless statement, C++ is very useful if not amusing!

---

### Post by pmasiar on 2009-01-10
> **meson2439 said:**
> It's about time C++ had interactive mode like python and haskell. Those interactive sessions sure helps during testing and debugging. That ought to reduce the amount of complains people have for C++.

yes, shell improves learning - but that is **exactly** why dynamic language like Python (which can, and often does, have a shell) is better for beginner than statically typed language (for which writing a functioning shell is quite complicated - so hard that I am not aware of any).

Thank you for proving my point, which is repeatedly disputed in so many other threads by  "C first" zealots. :-)

---

### Post by pmasiar on 2009-01-10
> **jimi_hendrix said:**
> python and perl doesnt make the world go round...

You are too young to remember (or know) when at end of 90ties, Perl was the ducktape which held the internet together. Way before Java and PHP was usable, Perl was the only alternative to writing CGI app in C. But it is good to know it, Perl earned immense following back then.

And Python manages deployment of hundreds of thousands of Google servers, so in a sense it **does** make the world go around. :-)

---

### Post by jimi_hendrix on 2009-01-10
that was not my point...what is the perl interpreter  written in?  Also find me a major shelfware game that uses just python...or an OS made entirely out of perl...

---

### Post by nvteighen on 2009-01-10
> **pmasiar said:**
> Way more than that: [http://hopl.murdoch.edu.au/](http://hopl.murdoch.edu.au/) lists 8512 languages! [http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity](http://en.wikipedia.org/wiki/Natural_language#Linguistic_diversity) counts only 6,912 known living human languages!


~7000 living languages? Hm... the last time I saw specialists said there were ~5000. And there's the language/dialect definition problem... which also applies to programming languages: is MIT/GNU Scheme a different dialect or language than SCM Scheme? Or what about K&R C and GNU C?? 

> **jimi_hendrix said:**
> that was not my point...what is the perl interpreter  written in?  Also find me a major shelfware game that uses just python...or an OS made entirely out of perl...

perl (with lowercase, i.e. the interpreter's official implementation) is written in C, but nothing prevents you to write a new interpreter in Python ;) An OS written in Perl (with uppercase, i.e. the language) though possible (all you need is someway to transform Perl code into native binary code), would be impractical: the language wasn't designed for that.

---

### Post by Reiger on 2009-01-10
> **pmasiar said:**
> so hard that I am not aware of any

Ehrm, the person you quoted gave an example of a statically typed language for which a shell has been written: Haskell. Which has the GHC, which comes with the GHCi... :)

EDIT: Oh and isn't there a C interpreter? ;)
Quick google: [http://www.softintegration.com/products/chstandard/download/](http://www.softintegration.com/products/chstandard/download/)

---

### Post by jimi_hendrix on 2009-01-10
yes...TCC

---

### Post by Kilon on 2009-01-10
> **jimi_hendrix said:**
> that was not my point...what is the perl interpreter  written in?  Also find me a major shelfware game that uses just python...or an OS made entirely out of perl...

I know there alot of 3d games written in JAVA. Isn't suppose to be JAVA a slow language ? Many people claim so. 

I have read an amazing book, about how fast the world we live in is.The book criticize this situation because "Fast" is something like the holly grail. 

But "Fast" equals to quantity not quality . We should be searching for better. Fast is irrelevant. 

I see today games that try to cramp as much polygons as possible in a computer screen. Is this a computer game ? Hell no !!! 

A game suppose to be fun to play . I still play playstation 2 games which are considered low  spec by today's Pc standard , but they are still a lot of fun. Really I do not know how the world we live in is so hysterical with speed.

---

### Post by CptPicard on 2009-01-10
C is sufficiently simple and straightforward that a "C shell" is thinkable (not that there would be much to play with in the shell, C data being so "raw"), but really, a "C++ shell" would be a huge undertaking and I really am not sure how that is supposed to work... probably it would compile classes in the background and maintain some kind of metadata about them... :)

jimi_hendrix, if you insist on going down the "languages X are written in C", I suggest you look at, say, Prolog -- it's a very high level language that is remarkable for writing parsers and compilers, and even compiles into surprisingly fast code...

---

### Post by pmasiar on 2009-01-10
> **jimi_hendrix said:**
> that was not my point...what is the perl interpreter  written in?  Also find me a major shelfware game that uses just python...or an OS made entirely out of perl...

...yet another speed kiddie...

So what if Perl is written in C? C was designed for writing system utilities and OS - it is portable assembly. Does it mean that it should be used for everything? Eactly the same arguments can be said for ASM - first C compiler was written in ASM. 

Now we have PyPy - Python compiler/runtime written in rPython (subset of Python). Does it mean everyone should rush and rewrite Linux kernel in rPython? Not according to my logic.

BTW [http://en.wikipedia.org/wiki/Eveonline](http://en.wikipedia.org/wiki/Eveonline) is in Python, and quite major game if you ask me, including all the awards. Python is also used to script AI in Wesnoth and other games.

Also, it would be helpfull if you learned to quote when you dispute some claims, so it would be possible to track down your thoughts and respond on exact misunderstanding. And when you learn to quote, please learn also to trim, leaving only the relevant part :-)

---

### Post by jimi_hendrix on 2009-01-10
> **pmasiar said:**
> ...yet another speed kiddie...

im not a speed kiddie...i use C/C++ because i like write in them...you like to write python...each to his own...

---

### Post by dribeas on 2009-01-10
> **CptPicard said:**
> C is sufficiently simple and straightforward that a "C shell" is thinkable (not that there would be much to play with in the shell, C data being so "raw")

More than that, a C shell is part of the past. IIRC there was a C shell back in the late 70s, maybe 80s? Yet I am too young for it. I just read a comment on a forum from someone that had lived those times.

I tried to get to that interpreter by googling, I did not find it, but I found a C/C++ interpreter here:

[http://root.cern.ch/drupal/content/cint]("http://root.cern.ch/drupal/content/cint")

---

### Post by samjh on 2009-01-10
C shell wasn't C in an interpreted shell.  It was just a shell with C-derived syntax.

[http://en.wikipedia.org/wiki/C_shell](http://en.wikipedia.org/wiki/C_shell)

---

### Post by dribeas on 2009-01-10
> **samjh said:**
> C shell wasn't C in an interpreted shell.  It was just a shell with C-derived syntax.

[http://en.wikipedia.org/wiki/C_shell](http://en.wikipedia.org/wiki/C_shell)

I should have been more precise. I meant a shell to execute C statements, as a synonym for interpreter. I did not realize that it would be confusing as there is a single product by that name. My bad.

---

### Post by Emill on 2009-01-10
I want to be able to pass functions in function calls like in Javascript:

```

function function2(a_function){
    a_function();
}

function function1(){
    function2(function(){
        alert('Hello');
    });
}

function1();

```

---

### Post by pmasiar on 2009-01-10
> **jimi_hendrix said:**
> im not a speed kiddie...i use C/C++ because i like write in them...you like to write python...each to his own...

anyyone who claims that C is 'better' than Perl, arguing that it is because Perl is written in C and there is not OS in Perl, is speed kiddie in my book, with little clue **why** different languages are optimized for different tasks.

---

### Post by eye208 on 2009-01-10
> **pmasiar said:**
> yes, shell improves learning - but that is **exactly** why dynamic language like Python (which can, and often does, have a shell) is better for beginner than statically typed language (for which writing a functioning shell is quite complicated - so hard that I am not aware of any).
[http://www.beanshell.org/](http://www.beanshell.org/)

> Thank you for proving my point, which is repeatedly disputed in so many other threads by  "C first" zealots. :-)
Not so fast, Mr Fanboy! The fact that someone else agrees with you "proves" nothing.

It's a common misconception among Python evangelists that the best way to learn programming is to *avoid* programming.

The benefit of strong typing is improved error detection at compile time rather than runtime. Why is this a good thing? Because errors at runtime can result in data loss, security issues etc. The more of these bugs you can catch during compile, the better.

---

### Post by mike_g on 2009-01-10
> **Emill said:**
> I want to be able to pass functions in function calls like in Javascript:
I'm pretty sure that you can do that with a function pointer.

I dumped some C code [here](http://grundez.net/snippet.php?id=51) on my site that uses them. AFAIK the same stuff should work in C++

---

### Post by eye208 on 2009-01-10
> **Emill said:**
> I want to be able to pass functions in function calls like in Javascript:

```

function function2(a_function){
    a_function();
}

function function1(){
    function2(function(){
        alert('Hello');
    });
}

function1();

```
You can't pass the function itself, but you can pass the address of a nested function. Not exactly the same, but pretty close.
```
#include <iostream>
using namespace std;

void function2(void (*a_function)()) {
    a_function();
}

void function1() {
    struct nested {
        static void function() {
            cout << "Hello" << endl;
        }
    };
    function2(nested::function);
}

int main() {
    function1();
    return 0;
}
```

---

### Post by pmasiar on 2009-01-10
> **eye208 said:**
> It's a common misconception among Python evangelists that the best way to learn programming is to *avoid* programming.

If Python allows me to solve more problems in less time by letting language to handle more irrelevant details (like type info), how it is avoiding programming? More problems solved equals more programming in my book. :confused:

> The benefit of strong typing is improved error detection at compile time rather than runtime. Why is this a good thing? Because errors at runtime can result in data loss, security issues etc. The more of these bugs you can catch during compile, the better.

Common misunderstanding discussed many times here, you just missed it. Read up blog post of Bruce Eckel, one of top authorities on C++ and Java: [Strong Typing vs. Strong Testing](http://www.mindview.net/WebLog/log-0025)

Wait, you don't follow the links. :-( OK, this discussion is also useless, can mods please move it to follow it's friend to 'Recurring discussions'?

---

### Post by CptPicard on 2009-01-10
> **Emill said:**
> I want to be able to pass functions in function calls like in Javascript:


> **mike_g said:**
> I'm pretty sure that you can do that with a function pointer.


Having functions as first class objects in a language is the first step to having anonymous functions (lambdas) and their associated closures -- I'm glad that people want them without necessarily knowing the exact terms of what they want ;)

Functional programming is a very strong model indeed...

> 
Not so fast, Mr Fanboy! The fact that someone else agrees with you "proves" nothing.

Maybe not, but if any of the C fanboys actually read and understood what was being written without using name-calling as a substitute for arguments of one's own, it might actually prove something to them.

> 
It's a common misconception among Python evangelists that the best way to learn programming is to *avoid* programming.

A common misconception among those people who know just C and are strangely fiercely proud of that achievement is that you are doing more "real" programming when you move towards the hardware level.

Programming is an act of formulating abstract descriptions of a problem domain/problem solution (depending on the declarativeness/imperativeness of your language). The better abstractors you are able to build in a language, the better, and the more it expands your picture of what kind of components there actually are in the problem domain. Not only that, as the components are semantically stronger and tend to move towards "combining expressions to get new expressions", this kind of an approach can even sometimes reveal structure you didn't think of beforehand... those are the best moments in programming IMO, and I've got most of those Eureka-moments while using Lisp. *Programming is about thinking, not typing!*

Of course, a lot of people who don't use high-level languages don't know what that means, so they react as if the above just means that you're calling into libraries... we had a C-zealot guy here who tried to get me banned for "arrogance" for saying that high-level languages help you abstract better, and then after a year it came obvious that he didn't know what a closure is. We haven't heard of him since ;)


> 
The benefit of strong typing is improved error detection at compile time rather than runtime. Why is this a good thing? Because errors at runtime can result in data loss, security issues etc. The more of these bugs you can catch during compile, the better.

You're confusing static vs. strong typing. Python is not the former but is the latter. Strong typing indeed is a good thing, static typing is not what it is cracked up to be -- I can't really remember a single bug that would not have been completely trivial (immediately obvious in even simple testing) and would have been caused by me passing an object of wrong type into a function, and thus would have been detectable by compiler...

"Duck" typing is excellent because of its genericity... in particular in Java-style languages most of those object-oriented patterns are just voodoo to get some genericity back that you lost in adopting the static type system.

---

### Post by eye208 on 2009-01-11
> **CptPicard said:**
> we had a C-zealot guy here who tried to get me banned for "arrogance" for saying that high-level languages help you abstract better, and then after a year it came obvious that he didn't know what a closure is. We haven't heard of him since ;)
Maybe he was offered a job. ;)

Anyway, I have this feeling that you guys misunderstand me. I consider myself open-minded, so whenever someone comes along and shows me something cool, I say: Hey, this is cool! This is how I learn new things. And believe me, I've learned a lot of new things since I got my first computer.

However, when I look at you Python fanboys, I see some guys switching on their computers, loading operating systems (written in C), clicking through some icons and menus on their desktops (written in C), then loading up a text editor (written in C) to enter some lines in Python, saving them to a file, and then running the Python interpreter (written in C) to execute them. And then the next thing they do is open up their web browsers (written in C++) and posting in this forum, marveling and telling everyone that Python is the best invention since sliced bread.

The question you have to ask yourself is this: Why is hardly any real work done in Python? This is a language that has been around for 18 years! And yet it doesn't play a significant role anywhere. Why is that?

Something smells fishy here.

---

### Post by Kilon on 2009-01-11
> **eye208 said:**
> Maybe he was offered a job. ;)

However, when I look at you Python fanboys, I see some guys switching on their computers, loading operating systems (written in C), clicking through some icons and menus on their desktops (written in C), then loading up a text editor (written in C) to enter some lines in Python, saving them to a file, and then running the Python interpreter (written in C) to execute them. And then the next thing they do is open up their web browsers (written in C++) and posting in this forum, marveling and telling everyone that Python is the best invention since sliced bread.


You avoid answering my question .

If you love so much popular choices , why don't you head back to windows ? Why wasting your time with the pathetic UBUNTU which is used by the mere 1% of the users out there ?

Python has much better statistics than that.

If you love statistics so much then head back to windows and start using Assembly.

---

### Post by CptPicard on 2009-01-11
> **eye208 said:**
> Maybe he was offered a job. ;)

Well, if becoming a code monkey is the only goal in life... ;)

> 
Anyway, I have this feeling that you guys misunderstand me. I consider myself open-minded, so whenever someone comes along and shows me something cool, I say: Hey, this is cool! This is how I learn new things. And believe me, I've learned a lot of new things since I got my first computer.

Well excellent! Now, head off to library and read *Structure and Interpretation of Computer Programs* to learn Scheme, which gives you an excellent POV regarding how much you can actually do with very little syntax if you choose your language elements wisely. A lot of that stuff really is very cool. It is interesting how something like C is essentially a subset of a similarly minimal yet more expressive language (theoretically speaking, the lambda and function application is the only thing you even need for Turing-complete computation -- see lambda calculus). OOP, too, is very insightfully implementable simply in terms of a closure -- you can do inheritance-style stuff trivially as well, and it's nothing but a function plus associated data...

The reason why I get my feathers so ruffled about these "you just call into libraries without understanding how it's done" remarks is that you simply *can't* write a C library that would allow you to "#include <lambda.h>" and run with it, because it requires rather different things from the stack-bound model of C... at the very least, you must write an "engine" in C to get the same expressions to work correctly. The GCC extension nested functions actually get close and I was happy to discover them -- they help me hack C into my desired direction a little bit more -- but of course you can't return them and their associated lexical scope like you can do in a lisp (or Python, by that matter).


> 
However, when I look at you Python fanboys, I see some guys switching on their computers, loading operating systems (written in C), clicking through some icons and menus on their desktops (written in C), then loading up a text editor (written in C) to enter some lines in Python, saving them to a file, and then running the Python interpreter (written in C) to execute them.

The reason for that is both historical and performance-related. There is no reason why all of those (even a lot of OS stuff except perhaps some underlying Python bytecode interpreting microkernel) could not be implemented in Python, given sufficient cycles...

Of course, performance is a metric too, but the strange connection a lot of C guys make that I always fight here is that just because C maps closely to machine code, using C is somehow the same thing then as doing some sort of most intellectually demanding über-programming. C is a "kind of" programming language which is semantically trivially included in lot of higher level languages (meaning that writing a C interpreter is easy to write in something like Lisp)... its machine-friendliness is a practical point that needs to be considered, but does not make it all that "special" when programming in the abstract is considered...

And btw, my preferred editor, Emacs, is for the most part a Lisp machine ;)

> 
 And then the next thing they do is open up their web browsers (written in C++) and posting in this forum, marveling and telling everyone that Python is the best invention since sliced bread.

So? If it works for them and works in cool and impressive ways, what exactly is wrong?

> 
The question you have to ask yourself is this: Why is hardly any real work done in Python? This is a language that has been around for 18 years! And yet it doesn't play a significant role anywhere. Why is that?

18 years is not all that much, it's pretty much the same as Java... and Java got Sun's marketing and the static-typed OOP-obsession behind its back. Python has not only had to come from out of the left field, but also has faced "ideological opposition"...

By the way, I do "real work" in Python. Pretty much all the back-office business-logic, data-mangling and database work in a business I mostly consult for is done in Python. It's remarkably easy to pull stuff out of a DB by query, map that through a few (higher-order!) function operators and then dump results into some kind of email that is mailed to everyone that fits the query, for example...

Doing that in C (or even Java) would be just painful, and my conceptual understanding of what I am doing, is again none the less for using Python...

---

### Post by Kilon on 2009-01-11
> **CptPicard said:**
> 

The reason for that is both historical and performance-related. There is no reason why all of those (even a lot of OS stuff except perhaps some underlying Python bytecode interpreting microkernel) could not be implemented in Python, given sufficient cycles...


Ok let us even accept the fact that python is considerable to very slow compared to C++. Even so , that is not a good enough reason why OSes are written in C++. 

I am going to annoy you here with another Delphi example. Delphi has been benchmarked many times and in some benchmarks has been found even faster than C++!!! Also Delphi has always worked perfectly with Windows APIs. Of course not only OSes were not written in DELPHI but even 3d games were not written even though Delphi has had full support for Direct3d for a very long time. 

It is difficult to defeat popularity. If something has enough buzz to be considered a standard then it is very difficult to change that. 

Java has been in the position to be considered more popular than C++ because SUN aggressive exploited any means to make the JAVA name heard everywhere. Marketing is the Alpha and Omega of popularity, but has little to do with the actual usefulness. 

For example in 3d graphics market , a company called Autdesk made a 3d software that was just a mediocre programm called 3d Studio MAX, but manage with marketing and clever strategic move to buy all its opponents (ALIAS MAYA and SOFTIMAGE XSI) , it kept developing  their opponents  programs  because now it got the ownership of their products, but the updates were pathetic and so now guess what everyone use. OF course 3d Studio MAX.  

That is the way things work, it is sad but true.  

I am not saying that C++ or Java are BAD languages.

LOL I have a car analogy here since you love them. 

"If car is the most popular means of personal transport that does not mean that is also the best way to transport". If you think about it cars, are noisy and poluting our environment. And even it is easy to build a electrical car which will be much quieter, cheaper to keep running and environment friendly , there are only a handful made even if the demand is so huge. 

Even if we assume that Python IS the PERFECT language that alone will be never enough to make it the MOST POPULAR CHOICE!!!

---

### Post by techmarks on 2009-01-11
> **Kilon said:**
> Ok let us even accept the fact that python is considerable to very slow compared to C++. Even so , that is not a good enough reason why OSes are written in C++. 

I am going to annoy you here with another Delphi example. Delphi has been benchmarked many times and in some benchmarks has been found even faster than C++!!! Also Delphi has always worked perfectly with Windows APIs. Of course not only OSes were not written in DELPHI but even 3d games were not written even though Delphi has had full support for Direct3d for a very long time. 



Delphi?

based on Pascal...not good.

Windows only...not good.

Proprietary language without any language standard.

---

### Post by Kilon on 2009-01-11
> **techmarks said:**
> Delphi?

based on Pascal...not good.  

wrong ... it is based on Object pascal 

Object pascal is to pascal what C++ is to C. 


> Windows only...not good.

Wrong again !

Before 2007 ---> Windows = Delphi . Linux = Kylix (you can use Lazarus for even more OSes like MACOS , FreeBSD etc.) 

After 2007 ---> Delphi = .NET = mono = any OS that mono supports 

> Proprietary language without any language standard

Yes it is. 

language standard... you mean something like this?

(2 seconds of google search)

[http://www.cs.ut.ee/~jellen/delphi/cs.html](http://www.cs.ut.ee/~jellen/delphi/cs.html) 

;)

---

### Post by techmarks on 2009-01-11
Are there any good libraries for Delphi?

Basically I see no real benefit in choosing it over Python which has much more momentum behind it, and is not a proprietary language trap.

---

### Post by jimi_hendrix on 2009-01-11
i love inadvertantly starting flamewars

---

### Post by eye208 on 2009-01-11
> **Kilon said:**
> If you love so much popular choices , why don't you head back to windows ? Why wasting your time with the pathetic UBUNTU which is used by the mere 1% of the users out there ?
If you think unpopular is better, why don't you use Slackware? Being an Ubuntu user, you have chosen the most popular distribution of all. And I'm sure you've had your reasons.

Like so many others here, I ditched Windows because I am convinced that GNU/Linux is better in many ways. I don't prefer C/C++/Java because they are "popular" but because I see that real work is being done with these languages, both on the operating system and the application level. Whenever I see something written in Python, it's something of minor importance: a configuration dialog, an embedded automation/scripting interface (like the one in Blender or various games). A while ago this would have been done in Tcl or Perl. Some day we might be using Ruby or Lua or what have you. Scripting languages come and go. But C/C++ is not going anywhere. It's the engine behind all those scripting languages.

> If you love statistics so much then head back to windows and start using Assembly.
I used Assembly long ago, when computers with 64K RAM were popular. By the way, I also used Slackware a few years ago.

My company evaluated Python as an alternative to Java when we had to implement a client application that was to be deployed to Windows terminal servers. Java had a large memory footprint, but at least it was fast once the application was loaded. Python was both large *and* slow. In the end we used C++ with wxWidgets.

---

### Post by CptPicard on 2009-01-11
> **eye208 said:**
> But C/C++ is not going anywhere. It's the engine behind all those scripting languages.

It doesn't have to be. Anything that compiles into standalone native can used, really. In practice it tends to be C or C++, but if you consider the languages themselves as they are defined (syntax and semantics) there is nothing "special" there that makes them particularly suitable for implementing other languages...

---

### Post by samjh on 2009-01-11
> **CptPicard said:**
> It doesn't have to be. Anything that compiles into standalone native can used, really. In practice it tends to be C or C++, but if you consider the languages themselves as they are defined (syntax and semantics) there is nothing "special" there that makes them particularly suitable for implementing other languages...

It's the vicious cycle of popularity.

C and C++ became popular, largely thanks to good luck.  As they became popular, more tools, documentation, and training became available.  Those things produced more and more programmers.  Software developers picked C or C++ for their new projects because of the availability of competent programmers and development tools.  Then C and C++ became more popular still.  And so on...

Neither C or C++ are particularly fantastic languages.  They just appeared at the right time, introduced to the world by the right people, in the right way.

If C and C++ weren't so lucky (or other languages better promoted), then we might have seen Pascal and Object-Pascal (for example) rise to colossal heights.

This is not to say C or C++ are "bad" languages, because they are actually good (helped by improvements driven by their mainstream popularity) for what they intended to be.  However, they certainly shouldn't be idolised.

---

### Post by Kilon on 2009-01-11
> **techmarks said:**
> Are there any good libraries for Delphi?

Basically I see no real benefit in choosing it over Python which has much more momentum behind it, and is not a proprietary language trap.


Maybe I am not that clear .... ok 

here we go again

Forgive me the use of caps locks and large fonts

[SIZE="6"]**DELPHI.NET IS A .NET LANGUAGE**[/SIZE]

which means anything you can access with C# or VB .Net you can access it with Delpi. 

So that means the whole .NET library.... I think this is huge enough don't you think ?

The same exact situation is ironpython . It can also access the whole .NET library.

Oh by the way Delphi .NET has an additional advantage , because is a excellent IDE it gives you the ability to code in VB.NET and C# as well, which means that your DELPHI code can now work together any way you want with both C# and VB.NET in the same IDE.

---

### Post by pmasiar on 2009-01-11
> **eye208 said:**
> Whenever I see something written in Python, it's something of minor importance: a configuration dialog, an embedded automation/scripting interface 

That's because you cannot see the big use of Python, like managing Google servers, YouTube, and more.

Of course I do not dispute that C and C++ are more popular. C had obvious luck of being main implementation language of Unix and then Linux. Is optimized for system programming, does it well, and likely will keep it's popularity in that area.

But because it is so low-level, it is not particularly good for application development, where flexibility and speed of development is more important.

eye208> Scripting languages come and go. 

System programming languages were in the same position before C. Read [url=http://www.paulgraham.com/hundred.html]The Hundred-Year Language
[/url]. 

Wait, you don't follow the links :-( No, I an **not** going to copy-paste that essay for you. If you ignore reading links, you are troll in my book, not interested in discussion but in disagreeing, in flamewars for fun.

---

### Post by KiwiNZ on 2009-01-11
Either discuss with  respect for others and in accordance to the COC or do not discuss at all. Thread closed

---

