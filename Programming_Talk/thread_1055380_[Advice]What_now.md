---
title: "[Advice]What now?"
date: 2009-01-30
forum: Programming Talk
---

### Post by fiddler616 on 2009-01-30
Hello,
I've started to feel kind of...I dunno...bored? with my current programming. Like it used to be that when I had a spare half hour, I'd open up my bookmarked tutorial, and get to work. Now it's not.

I taught myself Python, and consider myself to be a competent procedural programmer, and a struggling OOPer. I'm learning Java in school, and I guess it's similar to my Python, maybe a bit behind.
So what do you guys think I should do? Should I shove OOP into my face until I understand it? Should I learn a GUI for Python? I'm not really interested in web development, but I feel like JavaScript might be a useful skill--is it? And I feel like I *should* learn C at some point in time--is this true, or should I just it to other people and depend on Java for more speed-critical things?

Thank you very much.

---

### Post by shadylookin on 2009-01-30
> **fiddler616 said:**
> Hello,
I've started to feel kind of...I dunno...bored? with my current programming. Like it used to be that when I had a spare half hour, I'd open up my bookmarked tutorial, and get to work. Now it's not.

I taught myself Python, and consider myself to be a competent procedural programmer, and a struggling OOPer. I'm learning Java in school, and I guess it's similar to my Python, maybe a bit behind.
So what do you guys think I should do? Should I shove OOP into my face until I understand it? Should I learn a GUI for Python? I'm not really interested in web development, but I feel like JavaScript might be a useful skill--is it? And I feel like I *should* learn C at some point in time--is this true, or should I just it to other people and depend on Java for more speed-critical things?

Thank you very much.

well if you're learning java in school and you care about your grade you're going to want a very strong understanding of Object Oriented Programing.

if you're majoring in computer science you're definitely going to need to know C at some point. and if your CS department is anything like mine they're just going to one day expect you to know C without any instruction on how to program in it

if you have no interest in web development then I wouldn't bother with javascript

---

### Post by jimi_hendrix on 2009-01-30
Oop +1

---

### Post by fiddler616 on 2009-01-30
Good call on the OOP. Does anybody have a good tutorial that covers it? (Preferably in Python)
I'll try C too. I already started the GNU C Tutorial (albeit I'm in Chapter 2 or something).

---

### Post by jimi_hendrix on 2009-01-30
i dont know about a tutorial, but once you get going heres a good challenge for you

make a snowball fight game, using inheritance/polymorphism

the player faces an AI (i dont care if you use randoms or what to decide his moves)

you each have 5 health and snowballs must be made (you start with 3)

you can both move forward and back, and hit rate of snowballs depends on range

---

### Post by Ferrat on 2009-01-30
A good start is the 3D buzz c++ game video tutorials, the free ones will get you to the point of them going in for a more graphic look but they explain most elements of OOP pretty good and they are fun to watch and fairly easy to follow, they write the code but don't get stuck on it when explaining IMO but more use it as a tool to present what they mean.

---

### Post by Sorivenul on 2009-01-30
OOP is the way to go, and I suggest you learn it as you learn Java. 

Both universities I've attended teach Java as a first language and introduce objects quite early in order to allow it to permeate student's brains. There is a coworker of mine who recently asked why the school teaches Java first instead of something like Python. I asked what Java has taught him so far. The first answer out of his mouth was "object-oriented programming". Bingo! 

While moving from procedural programming to OOP can be difficult, it is worth the trouble and will make you think in new ways.

Good luck! Cheers!

EDIT: For tutorials (in Java) see:
[http://java.sun.com/docs/books/tutorial/java/concepts/](http://java.sun.com/docs/books/tutorial/java/concepts/)
[http://computing.southern.edu/halterman/OOPJ/index.html](http://computing.southern.edu/halterman/OOPJ/index.html)
[http://www.developer.com/java/article.php/935351](http://www.developer.com/java/article.php/935351)

The entry level courses at the universities I have been at, and now work at, have used:
[http://www.amazon.com/Starting-Out-Java-Early-Objects/dp/0321497686](http://www.amazon.com/Starting-Out-Java-Early-Objects/dp/0321497686)
[http://www.amazon.com/Java-Program-Design-James-Cohoon/dp/0073250309](http://www.amazon.com/Java-Program-Design-James-Cohoon/dp/0073250309)

---

### Post by nvteighen on 2009-01-31
OOP +1 Any decent programmer should know how it works... and know when to use it.

But IMHO, Python will help you better than Java... you won't be learning a new language + OOP, but just OOP. And then you can transfere that knowledge to Java or any other language very easily.

The "Dive into Python" is a good place for this.

Basically put, OOP is about creating new data types ("classes") with their own particular actions and attributes. Then, you make your program work based on the interactions between objects. The difficult part of OOP is actually the practice: understanding what kind of classes you need for some program, how will they work and interact, etc. But that, as you can imagine, is project-specific, so after having learned the theory, I recommend you to write something in OOP style.

---

### Post by CptPicard on 2009-01-31
+1 for nvteighen.

OP needs to learn the OOP parts of Python, in Python. In Python everything really is an object, although the OOP is nicely loose -- Python objects are just hashes with data and functions tacked onto them by their name. For example the much maligned self parameter is there very much for a reason, and clarifies some OOP-things nicely without you realizing you're being educated. :)

Java has the issue of turning OOP into bondage and discipline -- I really feel like I was held back in my programming career by starting "real, bigger programming" with Java. Static typing, everything-OOP forces design patterns on you, and they are really not all that obvious to a beginner. You can't do anything because the language won't let you, until you know how to make the language happy by writing some contrived combination of classes to solve your problem.

Finally, "learning C at some point" is a good idea. Won't be hard to grasp after Python, either. Interestingly, C-style OOP is interestingly close to Python-style OOP too in a sense...

---

### Post by fiddler616 on 2009-01-31
Sweet, I'll post back if I have any problems, but will look into "Dive into Python", etc. (nvteighen-maybe once I thoroughly understand it I'll have a working knowledge of Pyc-Tac-Toe, and will be able to contribute, instead of just saying "Oh, on some abstract level that makes sense, but I never would've been able to think of it")
@CptPicard I was under the impression that C didn't have OOP--and that's why C++ came along. I take it I'm wrong?

---

### Post by CptPicard on 2009-01-31
> **fiddler616 said:**
> Oh, on some abstract level that makes sense, but I never would've been able to think of it"

Interestingly, this is why I advocate higher-level languages so much -- you never would think of a lot of the stuff that is possible if you had to derive everything from first principles...

> 
@CptPicard I was under the impression that C didn't have OOP--and that's why C++ came along. I take it I'm wrong?

It has no explicit support for OOP, but you can use structs to keep your objects' data, then pass those structs to functions, and even keep function pointers in the struct to provide for  per-instance overriding of functions... and you can even write your own virtual table to keep track of which set of virtual functions should be executing for each class of objects... essentially you already have manually implemented a lot of C++'s OOP-support.

I guess it tells quite a lot that instead of C++, I actually prefer hacking up something like that most of the time for my C code :)

---

### Post by Tomosaur on 2009-01-31
Procedural: I will use a bus to go to my friend's house.

OOP: I am the bus.

---

### Post by nvteighen on 2009-01-31
> **fiddler616 said:**
> (nvteighen-maybe once I thoroughly understand it I'll have a working knowledge of Pyc-Tac-Toe, and will be able to contribute, instead of just saying "Oh, on some abstract level that makes sense, but I never would've been able to think of it")


Thanks! :D Any help is always appreciated. But don't hurry up; learn the stuff correctly... And in your place, I'd first try to write something in OOP from scratch; you know, in programming you learn by getting your hands dirty ;)

---

### Post by howlingmadhowie on 2009-01-31
i found when i started programming (java was my first language) i often found no answer to the question 'yes, but what is the computer actually doing?'. without knowing that, i hated OOP, because i didn't have a firm foundation under my feet and it all seemed terribly arbitrary. a couple of months of C and assembly solved that problem. :)

basically i'd suggest spending enough time with C so that structs and malloc are second nature and you really understand what they do. once you have that background you can move to OOP and understand what it's for, how it works and why it's often a good idea.

---

### Post by fiddler616 on 2009-01-31
> **howlingmadhowie said:**
> i found when i started programming (java was my first language) i often found no answer to the question 'yes, but what is the computer actually doing?'. without knowing that, i hated OOP, because i didn't have a firm foundation under my feet and it all seemed terribly arbitrary. a couple of months of C and assembly solved that problem. :)

basically i'd suggest spending enough time with C so that structs and malloc are second nature and you really understand what they do. once you have that background you can move to OOP and understand what it's for, how it works and why it's often a good idea.
Interesting, everyone seems to be advocating high->low, not low->high.

@CptPicard Thanks for clearing that up.

@nvteighen Good call about doing something independently first.

@Tomosaur Maybe my abstract knowledge is flawed. I would've thought OOP busriding would be more like
[PHP]bus255 = bus(home, friend's_house)
bus255.carry(Tomosaur)[/PHP]

---

### Post by CptPicard on 2009-01-31
> **fiddler616 said:**
> Interesting, everyone seems to be advocating high->low, not low->high.

Just keep on reading people's posts (and more importantly essays about programming in general by smarter minds than us here) and make up your mind about that... 

It is my personal impression of a couple of years of hanging out here that high-level advocates usually know both the high and low level and are able to meaningfully see the differences (in particular the fact that high-level languages are conceptually different in interesting ways), while those who push the low level do not quite seem to understand *why* certain things  have been added to their respective languages. This understanding mostly comes from use, and as they refuse to use HLLs, they never understand, and keep on believing that the low level is somehow particularly blessed simply because it runs faster and closer to the hardware. 

A notable (single, as far as I know?) exception to this rule in the world of "smart minds" out there is Knuth. He is both a math geek *and* wrote his Art of Computer Programming in a kind of machine language. His view on asm supporting mathematical analysis of algorithms is certainly interesting...

---

### Post by fiddler616 on 2009-01-31
> **CptPicard said:**
> Just keep on reading people's posts (and more importantly essays about programming in general by smarter minds than us here) and make up your mind about that... 

It is my personal impression of a couple of years of hanging out here that high-level advocates usually know both the high and low level and are able to meaningfully see the differences (in particular the fact that high-level languages are conceptually different in interesting ways), while those who push the low level do not quite seem to understand *why* certain things  have been added to their respective languages. This understanding mostly comes from use, and as they refuse to use HLLs, they never understand, and keep on believing that the low level is somehow particularly blessed simply because it runs faster and closer to the hardware. 

A notable (single, as far as I know?) exception to this rule in the world of "smart minds" out there is Knuth. He is both a math geek *and* wrote his Art of Computer Programming in a kind of machine language. His view on asm supporting mathematical analysis of algorithms is certainly interesting...
I've always kind of imagined a continuum, from low-level to high-level, which goes from speed of execution to ease of development.
I definitely think I'll worry about OO Python before getting involved in C though. While we're here, do GUIs matter?

---

### Post by CptPicard on 2009-01-31
> **fiddler616 said:**
> I've always kind of imagined a continuum, from low-level to high-level, which goes from speed of execution to ease of development.

That is only a half-truth. Ease of development is just a side-effect of a language coming with abstractions that are more about things you're likely to find in "computable functions" than about what you're likely to find "inside the CPU".

It's not all just simply easy, though. For example, some stuff in functional programming is *conceptually hard *for most people who are used to imperative programming, but once they "get it", it clicks for them for the rest of their lives, making solving all problems in terms of this new concept easier. I've experienced this sort of stuff a lot. The "OOP in C" example is one of the more trivial ones :)

I found an [interesting blog post]("http://weblog.raganwald.com/2006/10/are-we-blub-programmers.html") just a moment ago. 

**EDIT**: And another one, this is very good: [http://weblog.raganwald.com/2006/01/finding-signal-to-noise-ratio-in-never.html](http://weblog.raganwald.com/2006/01/finding-signal-to-noise-ratio-in-never.html)

No, GUIs do not matter, IMO they are the most boring part usually. You're just using a library to do some practical stuff...

---

### Post by pp. on 2009-01-31
> **CptPicard said:**
> ...out there is Knuth. He is both a math geek *and* wrote his Art of Computer Programming in a kind of machine language. His view on asm supporting mathematical analysis of algorithms is certainly interesting...

I rather see Knuth in Turing's tradition, in the sense that you can tell all manner of interesting things about an algorithm translated into a computer program when the programming language has very few hidden features.

IMO, you can't get any lower in levels than Turing's FSM. Busy Beavers, anyone?

---

### Post by CptPicard on 2009-01-31
> **pp. said:**
> I rather see Knuth in Turing's tradition, in the sense that you can tell all manner of interesting things about an algorithm translated into a computer program when the programming language has very few hidden features.


Yes, that is his point. Although I on the other hand get the feel that there is something slightly wrong about how one goes about a theoretical proof if it needs some sort of implementation to begin with which to analyze... :)

---

### Post by Tomosaur on 2009-01-31
> **fiddler616 said:**
> 
@Tomosaur Maybe my abstract knowledge is flawed. I would've thought OOP busriding would be more like
[php]bus255 = bus(home, friend's_house)
bus255.carry(Tomosaur)[/php]

I forgot to mention that I inherit from the PublicTransport super-class.

Apologies for the confusion!

---

### Post by shadylookin on 2009-01-31
call me crazy but if you're going to learn OOP and you're already using java I think you should stick to java. 

java adds interfaces and abstract classes(I don't think python has these at least not in a java sense). There's also encapsulation in java that doesn't allow outside code to access your private members. 

In my opinion java just does a much better job of handling object oriented programming

---

### Post by CptPicard on 2009-01-31
Java's and Python's OOP are just somewhat different, really, but they are OOP both. The biggest reason Java's is as it is is the static typing... it requires explicit definition of interfaces (Python's interfaces can be just implicit "protocols" as they are called) and abstract base classes are a similar outcome.

There are differing views on the merits of encapsulation.. I have never quite seen the point of having a language feature that explictly restricts what can be done for such a vague reason -- I can understand the benefits of type restrictions for compilation/verification reasons, but private stuff can be kept private simply by documenting it with "don't touch this kthx" :)

---

### Post by shadylookin on 2009-01-31
> **CptPicard said:**
> Java's and Python's OOP are just somewhat different, really, but they are OOP both. The biggest reason Java's is as it is is the static typing... it requires explicit definition of interfaces (Python's interfaces can be just implicit "protocols" as they are called) and abstract base classes are a similar outcome.

There are differing views on the merits of encapsulation.. I have never quite seen the point of having a language feature that explictly restricts what can be done for such a vague reason -- I can understand the benefits of type restrictions for compilation/verification reasons, but private stuff can be kept private simply by documenting it with "don't touch this kthx" :)

it's all about the implementations. For instance if you have 2 variables that are dependent on each other.

[PHP]public class Circle {

    private double radius;
    private double circumfrence;

    public double getRadius(){
        return radius;
    }

    public void setRadius(double r){
        radius = r;
        circumfrence = Math.PI * 2.0 * radius;
    }

    public double getCircumfrence(){
        return circumfrence;
    }

    public void setCircumfrence(double c){
        circumfrence = c;
        radius = c / (2.0 * Math.PI);
    }

}[/PHP]

if radius and cirumference were accessible outside of the instance of the class then people could change those values independently and get silly useless answers. In the end it's a judgment call, but I prefer encapsulation because I think it helps prevent silly mistakes.

you just shouldn't let strangers touch your privates:lolflag:

another reason he should stay with doing OOP with java is that he has to use it anyway for school. Sure the underlying concepts are the same but when a prof expects you to do an assignment telling them you don't need to do it in their specified language because you understand the concepts doesn't usually fly.

---

### Post by CptPicard on 2009-01-31
Well, that kind of interface definition would be better handled through accessors and documentation IMO... let's say that I find myself having to design around encapsulation way more often than I find myself at risk of messing stuff up because I would inadvertently touch the privates.

The "use what your school tells you to" argument certainly holds.

---

### Post by eye208 on 2009-01-31
> **CptPicard said:**
> private stuff can be kept private simply by documenting it with "don't touch this kthx" :)
Translation:

"Why would you want to use a feature that is missing in Python?"

---

### Post by jimi_hendrix on 2009-01-31
> **CptPicard said:**
>  but private stuff can be kept private simply by documenting it with "don't touch this kthx" :)

i never quite understood why use private...i mean if your coding a module and you just dont use that feature...oh well

---

### Post by fiddler616 on 2009-01-31
> **CptPicard said:**
> 
The "use what your school tells you to" argument certainly holds.
No, stop worrying about school. It's dreadfully easy--we haven't even *thought* about OOP yet. Or even methods (though I've started using them since I knew how and she doesn't take off for them)(and they make much nicer code). And we have great conversations like:
<Task requires looping something three times>
Me: <for loop>
Others: Why the for loop?
Me: Um...to loop?
Others: What's the matter with while?
Me: More lines of code, sloppier.
Others: You're dumb.
...and...
Others: BOOLEAN?!
Me: Um, yes?
Others: Why?
Me: All that variable needs to hold is a yes or no, and it boosts performance and neatness.
Others: Booleans are confusing, why not just use an integer?

So I'm sure that when OOP comes around in school, I'll be able to do it in Java. And all my "free time" programming is in Python.

@eye208 Haha
@CptPicard I still agree though (as much as I can understand it). Java seems overlegislated.

---

### Post by pp. on 2009-02-01
> **CptPicard said:**
> I have never quite seen the point of having a language feature that explictly restricts what can be done (...) private stuff can be kept private simply by documenting it with "don't touch this kthx" :)

That reminds me of my Smalltalk period. 

There was (still is) no mechanism which protects the innards of an object from being misused. Some of the private methods were clearly marked as such, some were not. 

Given that some solutions take an unholy number of different objects, finding the proper sequence of methods and knowing which methods to use at all and which ones to avoid at any cost took an inordinate slice of the learning time and effort. 

To me, Java's attempt to formally declare implementation details as "hidden" seems like a good idea. 

"Step in the right direction", anyway.

---

### Post by ajackson on 2009-02-01
Learning OOP would be very good from a future employment point of view but also understanding procedural will also be beneficial. The more methods you know the greater your employment prospects.

As for a language, once you understand the principles learning the correct syntax will be pretty easy, start with the language you are most familiar with and go on from there.


> **eye208 said:**
> Translation:

"Why would you want to use a feature that is missing in Python?"
Translation:

"I have a lot of problems with people liking Python over my beloved C, I am a troll and I like living under my bridge."

---

### Post by sujoy on 2009-02-01
other than OOP, i would say, also add in functional programming.
lisp, for instance, opened my eyes to a whole new way of coding.

---

### Post by pp. on 2009-02-01
> **ajackson said:**
> Learning OOP would be very good from a future employment point of view but also understanding procedural will also be beneficial.

That's a common misunderstanding. OOP ***is*** procedural.

---

### Post by jimi_hendrix on 2009-02-01
> **sujoy said:**
> lisp, for instance, opened my eyes to a whole new way of coding.

it did for me too when i figured out how i could create OOP in scheme

---

### Post by nvteighen on 2009-02-01
> **eye208 said:**
> Translation:

"Why would you want to use a feature that is missing in Python?"

What's missing in Python? You declare private stuff by using *__name* notation.

```

Python 2.5.2 (r252:60911, Jan  4 2009, 17:40:26) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class MyClass:
...     def __init__(self):
...             self.public = 5
...             self.__private = 13
...     
...     def show_private(self):
...             return self.__private
... 
>>> obj = MyClass()
>>> print obj.show_private()
13
>>> print obj.public
5
>>> print obj.__private
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: MyClass instance has no attribute '__private'
>>> 

```

---

### Post by fiddler616 on 2009-02-01
> **nvteighen said:**
> What's missing in Python? You declare private stuff by using *__name* notation.


While we're talking about naming things, would somebody be so kind as to explain why some methods are written like __this__, and some aren't?

---

### Post by nvteighen on 2009-02-01
The *__name__* notation is for special built-in methods. For example, the constructor method in any Python class is __init__(). But there are many other, for example, if you want to define what a certain class's "length" is so you can then do **len(whatever)** to it is the __len__() method. Or if you want to specify how to transform your object into a string when the str() cast is called upon it, you define the __str__() method, etc.

---

### Post by fiddler616 on 2009-02-01
> **nvteighen said:**
> The *__name__* notation is for special built-in methods. For example, the constructor method in any Python class is __init__(). But there are many other, for example, if you want to define what a certain class's "length" is so you can then do **len(whatever)** to it is the __len__() method. Or if you want to specify how to transform your object into a string when the str() cast is called upon it, you define the __str__() method, etc.
*Thanks*
Jumping back a few posts: I take it I should learn C, and then contemplate a functional language? Or vice versa?

---

### Post by nvteighen on 2009-02-01
> **fiddler616 said:**
> *Thanks*
Jumping back a few posts: I take it I should learn C, and then contemplate a functional language? Or vice versa?
I wouldn't care for the order. You'll get the "culture shock" when entering functional programming no matter how much experience with imperative programming you have. Anyway, I like Python's little support of this paradigm as an introduction for it. Look for map(), reduce(), filter(), lambda and list comprehensions (there's no more than that in Python).

---

### Post by jimi_hendrix on 2009-02-01
> **nvteighen said:**
> You'll get the "culture shock" when entering functional programming no matter how much experience with imperative programming you have. 

actually the more you do imperative, the harder it will be...CptPicard complains about my use of set! when i show him a scheme snippit...

---

### Post by CptPicard on 2009-02-01
> **jimi_hendrix said:**
> actually the more you do imperative, the harder it will be...CptPicard complains about my use of set! when i show him a scheme snippit...

It really is all about "breaking the imperative mindset"... over time, you learn to see how things work in functional terms, and then you are able to transfer that knowledge even over back to imperative languages when applicable. You won't be able to do functional programming in your typical imperative language, but just simply knowing "how you would do this functionally" will help you map that solution to, say, data structures or recursion or a combination thereof.

A very nice feature of a functional solution is that it's declarative... "mathematical". You can analyze and play with it much more easily even with pencil and paper, let alone an editor...

---

### Post by nvteighen on 2009-02-01
> **CptPicard said:**
>  ... You won't be able to do functional programming in your typical imperative language, but just simply knowing "how you would do this functionally" will help you map that solution to, say, data structures or recursion or a combination thereof.

This will surely sound like a silly TV ad... :p 

It's true: after I learned functional programming my data structures improved a lot and I finally understood recursion. Thanks to functional programming, I'm now a better programmer! (Call now to get yours! And if you call in the next 5 minutes, you'll also get this new amazing FORTRAN code for free!! :D)

> A very nice feature of a functional solution is that it's declarative... "mathematical". You can analyze and play with it much more easily even with pencil and paper, let alone an editor...

Yes. And that means there is no "What IDE for Scheme?" threads, e.g. :)

---

### Post by jimi_hendrix on 2009-02-01
> **nvteighen said:**
> Yes. And that means there is no "What IDE for Scheme?" threads, e.g. :)

percent of forum population using scheme?

---

### Post by fiddler616 on 2009-02-01
> **jimi_hendrix said:**
> percent of forum population using scheme?
It can't be big--nvteighen seems to be the only contributor to FreeTruco...
I take it Scheme > Lisp/Haskell/Fortran/etc.?

---

### Post by nvteighen on 2009-02-02
> **jimi_hendrix said:**
> percent of forum population using scheme?

> **fiddler616 said:**
> It can't be big--nvteighen seems to be the only contributor to FreeTruco...
I take it Scheme > Lisp/Haskell/Fortran/etc.?

Ehem... Scheme = Lisp!

The Schemer census seems to be:
1. CptPicard
2. Mr.MacDonald
3. Cracauer (Lisp in general)
4. Wybiral
5. nvteighen
6. jimi_hendrix???

If lnostdal wasn't banned, he would also be counted. :p

---

### Post by eye208 on 2009-02-02
> **nvteighen said:**
> What's missing in Python? You declare private stuff by using *__name* notation.
The "private" keyword is missing. Imagine a private method that has been used dozens of times inside the class. Now you want to make it public. In C++/Java all you need to do is change the declaration. In Python you have to rename the method *and each method call statement*.

This is the same nonsense as program flow control by whitespace or duck typing. It works fine only as long as you are the only person working on the program.

---

### Post by nvteighen on 2009-02-02
> **eye208 said:**
> The "private" keyword is missing. Imagine a private method that has been used dozens of times inside the class. Now you want to make it public. In C++/Java all you need to do is change the declaration. In Python you have to rename the method *and each method call statement*.

This is the same nonsense as program flow control by whitespace or duck typing. It works fine only as long as you are the only person working on the program.
Ok, I see what you mean. I agree with you that the feature could be made a bit easier to use.

But the whitespace and the duck typing "issues" you refer to are absolutely different.

Ok, I also think the significant whitespace is a really bad idea: sometimes it is a nightmere to refactor some Python code by moving something that's in a loop to a new function because the indentation is different and without fixing that, it plainly doesn't run. But you also have a "de facto" rule in C or C++ that you have to indent your code to make it readable... (the great difference is that it will run anyway). Another problem with it is that it adds context-dependency into a formal language, but that's a linguistic issue.

The dynamic typing is a great idea which makes the language a lot more flexible than the static counterparts... It allows a lot more of genericity, exactly as Lisp. For example, you can even create functions that don't need an exact type of object as long as it does the same. In C, C++ or Java you can't do that, as the type is also taken in account... even if two types do the same and are implemented the same way, the fact that they are different types will raise a compiler error... (Ok, in C it will be just a warning... C's weak typing is a good thing too in lots of cases, but it's based on implementation details you shouldn't care about when programming.)

---

### Post by CptPicard on 2009-02-02
> **fiddler616 said:**
> 
I take it Scheme > Lisp/Haskell/Fortran/etc.?

You can't compare like that... the good qualities of Scheme is that it's such a small language syntactically speaking, yet a very high level one, and capable of demonstrating a lot of concepts with that small set of syntax. No wonder it is used in teaching often...

---

### Post by fiddler616 on 2009-02-02
> **eye208 said:**
> It works fine only as long as you are the only person working on the program.
Um, what?
If anything the duck typing makes it *easier* to collaborate, and the indentation just means that you need to reach a consensus before you begin--I normally do a tab, but for the tiny bit of work I did on PycTacToe, I had to use 4 spaces. And if I'd been using my head, I would've just set my tabs to equal 4 spaces--both gedit and vim do this (and I'm sure IDEs do, too).

---

### Post by fiddler616 on 2009-02-02
> **CptPicard said:**
> You can't compare like that... the good qualities of Scheme is that it's such a small language syntactically speaking, yet a very high level one, and capable of demonstrating a lot of concepts with that small set of syntax. No wonder it is used in teaching often...
I guess I was talking in terms of "As a participant in these forums who is interested in the "brains" behind functional languages, Scheme would be the best one to learn"?

---

### Post by CptPicard on 2009-02-02
> **fiddler616 said:**
> I guess I was talking in terms of "As a participant in these forums who is interested in the "brains" behind functional languages, Scheme would be the best one to learn"?

Probably so, because it really is quite educational not only as a functional language but as a lisp. Then there are languages such as Haskell, but it's pure-functionality really makes it somewhat hard when you want to do something like model mutable state.. ;)

By the way, as regards the type system discussion, I really like Common Lisp's approach to this. Type declarations are optional assertions where you can "tighten up" the typing for speed and type-checking and "documentation" when needed. But it does not force you to architecture a type system every time you're writing something.

---

### Post by eye208 on 2009-02-02
> **nvteighen said:**
> The dynamic typing is a great idea which makes the language a lot more flexible than the static counterparts... It allows a lot more of genericity, exactly as Lisp. For example, you can even create functions that don't need an exact type of object as long as it does the same. In C, C++ or Java you can't do that, as the type is also taken in account... even if two types do the same and are implemented the same way, the fact that they are different types will raise a compiler error... (Ok, in C it will be just a warning... C's weak typing is a good thing too in lots of cases, but it's based on implementation details you shouldn't care about when programming.)
The purpose of static typing is to force the programmer to document his intentions at the declaration stage. If you write a function in C++ or Java that expects an object with a particular set of public methods, you are forced to document this in the function declaration. No one can ever pass the wrong type of object to your function because the compiler will not accept it. If you have separate types with similar methods and similar behavior, you can declare a common abstract class or interface for them.

Duck typing means your function will accept any type of object. You can check whether the object matches your requirements only at runtime. And the check itself is inside the function body, i.e. a programmer calling your function must look at your code to see what type of object you want. It gets even worse if you just pass the object to some other function and let the other function do the checks. Even if you document your own code properly for those who call it, a change in the implementation of the functions that you call will invalidate your documentation, and you won't even notice it.

---

### Post by ajackson on 2009-02-02
> **eye208 said:**
> Duck typing means your function will accept any type of object. You can check whether the object matches your requirements only at runtime. And the check itself is inside the function body, i.e. a programmer calling your function must look at your code to see what type of object you want. It gets even worse if you just pass the object to some other function and let the other function do the checks.
OK so how does a programmer know what type of objects are passed to say a Java function? They either look up the source code or check the documentation.

How does a programmer know what type of objects should be passed to a Python function? They do exactly the same, look at the code or look at the documentation.

Edit: In your beloved C, the .h files contain templates showing you what type of object is passed, guess what that is a form of documentation as well.

---

### Post by eye208 on 2009-02-02
> **ajackson said:**
> OK so how does a programmer know what type of objects are passed to say a Java function? They either look up the source code or check the documentation.
No. They look at the function header in the javadoc file which is automatically generated. No handwritten documentation is required. No detail of implementation needs to be known. This is the exact opposite of Python.

> Edit: In your beloved C, the .h files contain templates showing you what type of object is passed, guess what that is a form of documentation as well.
Yes, but you don't have to read it each time there's an update. The compiler does. If you pass the wrong type because the implementation has changed, the compiler will tell you.

---

### Post by nvteighen on 2009-02-02
> **eye208 said:**
> No. They look at the function header in the javadoc file which is automatically generated. No handwritten documentation is required. No detail of implementation needs to be known. This is the exact opposite of Python.

Excuse me. If I have some function in Python, whose interface tells me to pass a tuple, I don't know what happens to that tuple. And be careful, I may pass a list and the whole thing will work at the most of the times... but of course, if it doesn't work, it's my fault not to have respected the function's interface. 

Of course, in Python you don't have a header file and you have to read the docs. I recognize headers are a handy thing in C because the serve as a cheatsheet, but the real reason why there are header files is because the compiler needs to know all functions available to a certain program... and those functions will be in a separate binary. They're actually just a detour to trick the compiler to think there's something there's actually not there (yet). They were not created as documentation...

Otherwise, why people write API docs for C libraries? The most of the time, even knowing what types you have to pass to the function doesn't help.

> Yes, but you don't have to read it each time there's an update. The compiler does. If you pass the wrong type because the implementation has changed, the compiler will tell you.

No. If the type has changed then it's the **interface** which changed: even if the types are exactly the same and the implementation hasn't changed. For example, if I pass a GLib's gpointer to a function asking for a void *, it will raise an error even if both types are exactly the same.

---

### Post by eye208 on 2009-02-03
> **nvteighen said:**
> Excuse me. If I have some function in Python, whose interface tells me to pass a tuple
You don't have any interface. That's the point. You can pass anything to the function, and it may or may not work. You'll find out at runtime.

> I don't know what happens to that tuple. And be careful, I may pass a list and the whole thing will work at the most of the times... but of course, if it doesn't work, it's my fault not to have respected the function's interface.
In order to respect the function's interface, you have to read not only the code of that function but possibly all the other functions that your objects get passed on to. There is no type safety in Python, and that's why Python isn't used on a larger scale. It's OK as long as you maintain each part of the program yourself.

> Of course, in Python you don't have a header file and you have to read the docs.
Reading the docs is not enough. If you write a function that passes its parameters on to other functions, each change in one of the other functions may render your own documentation obsolete.

> I recognize headers are a handy thing in C because the serve as a cheatsheet, but the real reason why there are header files is because the compiler needs to know all functions available to a certain program... and those functions will be in a separate binary. They're actually just a detour to trick the compiler to think there's something there's actually not there (yet). They were not created as documentation...
That's right. They were created to implement type safety. They are machine-readable documentation.

> Otherwise, why people write API docs for C libraries? The most of the time, even knowing what types you have to pass to the function doesn't help.
Most people won't agree with you here. For example, if you have two function headers that look like this...
```
public void setOutputStream(OutputStream out)

public OutputStream getOutputStream()
```
... it's perfectly clear that you can pass the return value of the latter to the former, even if they are part of different classes, written by different people.[list][*]You don't need to look at the code or documentation of either function.[*]You don't need to be familiar with the OutputStream interface.[*]It doesn't matter if the latter function actually returns a FileOutputStream, ZipOutputStream, PrintStream, LogStream or what have you.[/list]
This is why people love static typing. It's essential in collaborative development.

---

### Post by myrtle1908 on 2009-02-03
> **eye208 said:**
> Duck typing means your function will accept any type of object. You can check whether the object matches your requirements only at runtime. And the check itself is inside the function body, i.e. a programmer calling your function must look at your code to see what type of object you want. **It gets even worse if you just pass the object to some other function and let the other function do the checks.** Even if you document your own code properly for those who call it, a change in the implementation of the functions that you call will invalidate your documentation, and you won't even notice it.

This is where duck typing falls down for me completely.  Why bother with a "duck typing" language if you are going to have to check the argument type for cautions sake?  Why not use a strongly typed language and be done with it?  IMO this is why languages like Python cannot be used for large scale multi-developer projects.

---

### Post by CptPicard on 2009-02-03
> **myrtle1908 said:**
> Why bother with a "duck typing" language if you are going to have to check the argument type for cautions sake?

The whole point is that you're not really supposed to. In a duck typed language, you have less types in general -- what is important is that the object just does what it is expected to do. A lot people are too hung up on type-declarations simply because they are used to having them -- for example in eye208's three points, the latter two at least seem meaningless -- you do not need to be familiar with the interface in any case as long as the functions know what to do with it, and the object can very much be whatever as long as it behaves as an outputstream. I don't have to care about the specific type. A simple docstring is needed to say that some parameter X is a stream, and the best part is that the stream, as long it works as it should, can really be positively anything, not just an ObjectStream. Now, really, docs *are* needed, and I would never assume that simple type declarations are sufficient to "document". And of course, getOutputStream and setOutputStream obviously operate on, streams. ;)

> 
  Why not use a strongly typed language and be done with it?

Python is strongly typed. The type of the value exists all right and is enforced. It is just not enforced at "compile-time".

The whole point of the exercise is that static typing forces too much type-architecture for whatever the gain is that you derive from it. It's all about a cost-benefit analysis. For example most of my programming design problems in the past 10 years have been OOP-design issues primarly caused by static-typed OOP languages -- there is no getting around it that just being able to use something where it is going to work anyway is a Good Thing, in particular when you combine this with stuff that really can exploit it -- generic higher order functions and the list comprehension system for example. All of that would require some sort of interface definitions or generics or whatever in a static-typed language... and OOP-design-patterns really are the most non-fruitful programming activity I have ever come across...

---

### Post by myrtle1908 on 2009-02-03
> **CptPicard said:**
> **The whole point is that you're not really supposed to.** In a duck typed language, you have less types in general -- what is important is that the object just does what it is expected to do.


Granted.  However the point I was attempting to make was that this "type checking" ends up inevitable (for safety) on large scale projects where you (as the developer) cannot guarantee the consumers use.  Perhaps I have taken a simplistic view?

> **CptPicard said:**
> Python is strongly typed. The type of the value exists all right and is enforced. It is just not enforced at "compile-time".

Understood.  Poor choice of words on my part.  s/strong/static/ ;)

---

### Post by CptPicard on 2009-02-03
> **myrtle1908 said:**
> Granted.  However the point I was attempting to make was that this "type checking" ends up inevitable (for safety) on large scale projects where you (as the developer) cannot guarantee the consumers use.  Perhaps I have taken a simplistic view?

Let's say that I *understand* what is being said in this argument and where it comes from although I do not believe it is in reality such an awful thing in totality "in most cases", especially if you consider the benefits.

Even Wikipedia says...

> 
Duck typing is aided by habitually not testing for the type of arguments in method and function bodies, relying on documentation, clear code, and testing to ensure correct use. Users of statically typed languages new to dynamically typed languages may want to add such static, (before run-time), type checks which defeats duck typing, constraining the language's dynamism.


But of course one needs to try to set things straight in cases where the opposite side is often armed with lots of bad attitude and a complete denial of the reasons why some languages have chosen a certain typing discipline... ;)

---

### Post by myrtle1908 on 2009-02-03
> **CptPicard said:**
> Let's say that I *understand* what is being said in this argument and where it comes from although I do not believe it is in reality such an awful thing in totality "in most cases", especially if you consider the benefits.

Even Wikipedia says...

But of course one needs to try to set things straight in cases where the opposite side is often armed with lots of bad attitude and a complete denial of the reasons why some languages have chosen a certain typing discipline... ;)

Haha!  Bad attitude?  No Captain.  I appreciate dynamically typed languages and certainly do not underestimate their power.  I have been a Perl user for the last 15 or so years and it has served me very well.  Quick and dirty, just the way I like it.  But I would only ever use these languages for small and remedial tasks (and for these alone).

Perhaps I'm set in my ways and am blinded.  I'm still yet to hear a convincing argument for seriously employing these (and this will hit a nerve) "toys" for anything other than a quick "hack".

I just fail to see why one would really want to embark on a seriously large project with one of these "ducks" ;)

---

### Post by ajackson on 2009-02-03
> **eye208 said:**
> Most people won't agree with you here. For example, if you have two function headers that look like this...
```
public void setOutputStream(OutputStream out)

public OutputStream getOutputStream()
```
... it's perfectly clear that you can pass the return value of the latter to the former, even if they are part of different classes, written by different people.[list][*]**You don't need to look at the code or documentation of either function.**[*]You don't need to be familiar with the OutputStream interface.[*]It doesn't matter if the latter function actually returns a FileOutputStream, ZipOutputStream, PrintStream, LogStream or what have you.[/list]
Funny I always thought that you could describe function headers as both code **and** documentation. How else would a programmer know what objects to pass the function or even that the function exists in the first place?

Also you don't need to be familiar with the OutputStream interface but you have to know that FileOutputStream, etc implement it? How do you do that without documentation? You contradict yourself so much.
> This is why people love static typing. It's essential in collaborative development.
No it isn't, good design and good documentation are essential in collaborative development.

---

### Post by eye208 on 2009-02-03
> **CptPicard said:**
> for example in eye208's three points, the latter two at least seem meaningless -- you do not need to be familiar with the interface in any case as long as the functions know what to do with it, and the object can very much be whatever as long as it behaves as an outputstream.
What does "behaves as an outputstream" mean? What if developer A and B disagree about what an outputstream is? How can I tell that the outputstream returned by class A is compatible with class B? How can I be sure that it's still compatible after one of the classes has been updated?

And most of all: Why should I care about what an outputstream is if all I want to do is make object A read a stream provided by object B?

Static typing is the equivalent of jack and socket standards in e.g. consumer electronics. You can figure out that LAN cables are not meant to be plugged into AC power outlets simply by looking at the connectors.

---

### Post by ajackson on 2009-02-03
> **eye208 said:**
> Static typing is the equivalent of jack and socket standards in e.g. consumer electronics. You can figure out that LAN cables are not meant to be plugged into AC power outlets simply by looking at the connectors.
But you can't figure out that a blu ray DVD isn't compatible with a standard DVD player just by looking at the disk and the tray/slot.

---

### Post by eye208 on 2009-02-03
> **ajackson said:**
> Also you don't need to be familiar with the OutputStream interface but you have to know that FileOutputStream, etc implement it? How do you do that without documentation? You contradict yourself so much.
I don't contradict myself at all. Here's what I wrote:

> It doesn't matter if the latter function actually returns a FileOutputStream, ZipOutputStream, PrintStream, LogStream or what have you.
Which part of "it doesn't matter" didn't you understand?

---

### Post by nvteighen on 2009-02-03
> **eye208 said:**
> You don't have any interface. That's the point. You can pass anything to the function, and it may or may not work. You'll find out at runtime.

You have an interface. What you don't have is compile-time check of that interface. That's all there is in static typing.

I fear you consider the interface just as the data types you have to pass to make a function call work. You're missing the most important part: a function is some abstraction and you have to know what that abstraction is about. What I mean, you have to know what the function's meaning is. Not necessarily how it is implemented, but what it does in which context.

For example, look at this familiar C declaration:
```

void *realloc(void *ptr, size_t size);

```

Ok, what if ptr is NULL? You surely know that in that case, realloc() acts as malloc(size). What if size = 0? Then it is free(ptr). Is there a
way to know that without looking at the docs?

What about this:
```

int scanf(const char *format, ...);

```

What is '...'? What is format supposed to be? Can I just pass an array of chars or has it to be a string (which is not the same... a string is a char array with '\0' terminator)? What is the return value of scanf() about?

The interface is not just the data types. It's the meaning the function has in the semantical system the code is.

> In order to respect the function's interface, you have to read not only the code of that function but possibly all the other functions that your objects get passed on to. There is no type safety in Python, and that's why Python isn't used on a larger scale. It's OK as long as you maintain each part of the program yourself.

What you have to do is to read the functions' (plural) documentation. The code is unimportant... of course, as long as the developers documented their code well.

> Reading the docs is not enough. If you write a function that passes its parameters on to other functions, each change in one of the other functions may render your own documentation obsolete.

Again, if for some reason the interface changes (no matter if the implementation changed), then anything will fail. And the docs can be obsolete even in a C code... What if I modify the header file because I invented a new data type... and the docs are obsolete? The compiler will fail and the user will stare confused at the error. It's true that a look at the header will tell him what type is required, but will them tell him/her how to allocate memory for that type?

> 
Most people won't agree with you here. For example, if you have two function headers that look like this...
```
public void setOutputStream(OutputStream out)

public OutputStream getOutputStream()
```
... it's perfectly clear that you can pass the return value of the latter to the former, even if they are part of different classes, written by different people.[list][*]You don't need to look at the code or documentation of either function.[*]You don't need to be familiar with the OutputStream interface.[*]It doesn't matter if the latter function actually returns a FileOutputStream, ZipOutputStream, PrintStream, LogStream or what have you.[/list]
This is why people love static typing. It's essential in collaborative development.

There's nothing clear there, apart from the arguments and return types. I don't know if the OutputStream has to be empty or not, I don't know what OutputStream is getOutputStream() going to return me and in what cases... The only thing I know is that I can plug them together... like having a cable and a plug and not knowing where ones come from and where the other goes to...

> **myrtle1908 said:**
> I have been a Perl user for the last 15 or so years and it has served me very well.  Quick and dirty, just the way I like it.  But I would only ever use these languages for small and remedial tasks (and for these alone).


Perl is a somewhat special thing... What you have there is rather more "context types" than "data types". What is @a? An array? Not necessarily, you know that if I use @a in a scalar context it will be the array's length...

> **eye208 said:**
> What does "behaves as an outputstream" mean? What if developer A and B disagree about what an outputstream is? How can I tell that the outputstream returned by class A is compatible with class B? How can I be sure that it's still compatible after one of the classes has been updated?

If A and B disagree on what a certain data type is, then a failure is sure... in whatever language you're a coding in.

It "behaives as an outputstream" if it works with that functions that ask for an outputstream. That's it.

---

### Post by ajackson on 2009-02-03
> **eye208 said:**
> Which part of "it doesn't matter" didn't you understand?
Without looking at documentation/code how do you know that FileOutputStream can be used where OutputStream is allowed? What if I made a class called SingingOutputStream, would I be able to use that where OutputStream is allowed? It might or might not implement the OutputStream interface, without looking at the code or documentation you wouldn't know.

So which part of "you need to look at the code or documentation" don't you understand?

---

### Post by eye208 on 2009-02-03
> **nvteighen said:**
> For example, look at this familiar C declaration:
```

void *realloc(void *ptr, size_t size);

```

Ok, what if ptr is NULL? You surely know that in that case, realloc() acts as malloc(size). What if size = 0? Then it is free(ptr). Is there a
way to know that without looking at the docs?

What about this:
```

int scanf(const char *format, ...);

```

What is '...'? What is format supposed to be? Can I just pass an array of chars or has it to be a string (which is not the same... a string is a char array with '\0' terminator)? What is the return value of scanf() about?
You are merely pointing out that C's static typing system is imperfect, not that static typing is the wrong way. That's why C++ and Java are considered improvements over C. They take the static typing approach further by adding OOP features and namespaces. That doesn't mean that all C++ and Java classes are self-documenting. But still you don't need to know the details of an OutputStream in order to pass one from one object to another. The interface is an indicator that the two classes are compatible and capable of passing data to one another directly. There are no such indicators in Python.

> If A and B disagree on what a certain data type is, then a failure is sure... in whatever language you're a coding in.
No. OutputStream is declared in a public namespace. If I declare an incompatible type of OutputStream in my own namespace, the compiler will never confuse the two. If I declare my OutputStream in the public namespace, my program will not compile because of name conflicts. If someone tries to pass my OutputStream to a function expecting the other one, his program won't compile. There's no way the compiler could accidentally produce an executable failing due to an unresolved conflict between programmer A and B. And this is the whole point. If you work in a team on a large project, you want static typing because it forces you to sort these things out.

---

### Post by jimi_hendrix on 2009-02-03
> **fiddler616 said:**
> I take it Scheme > Lisp/Haskell/Fortran/etc.?

fortran has nothing in common with those </geek-OCD-need-to-correct>

---

### Post by eye208 on 2009-02-03
> **ajackson said:**
> Without looking at documentation/code how do you know that FileOutputStream can be used where OutputStream is allowed?
In the case I described above, I don't even need to know that FileOutputStream exists.

> What if I made a class called SingingOutputStream, would I be able to use that where OutputStream is allowed? It might or might not implement the OutputStream interface, without looking at the code or documentation you wouldn't know.
I don't need to look at the implementation. The class header is sufficient:
```
class SingingOutputStream implements OutputStream
```
In C++ the class header can be found in the .h file. In Java I can extract the info using the javadoc tool. Either way I don't need to read your code or depend on your documentation skills.

---

### Post by ajackson on 2009-02-03
> **eye208 said:**
> In the case I described above, I don't even need to know that FileOutputStream exists.
If you are going to pass it as a parameter you should know that it exists and that it implements OutputStream or your program wouldn't even compile, unless you have found a way of getting a compiler to recognise non-existant variable types.

> **eye208 said:**
> I don't need to look at the implementation. The class header is sufficient:
```
class SingingOutputStream implements OutputStream
```
In C++ the class header can be found in the .h file. In Java I can extract the info using the javadoc tool. Either way I don't need to read your code or depend on your documentation skills.
The point you seem unable to grasp is that you claimed that you didn't need to refer to documentation to work out what to pass as parameters.

The header files **are** documentation, the stuff javadoc produces is **documentation**. This is why I said you are contradicting yourself.

While javadoc automates the creation of documentation the developer still has to run it and the developer has to create the .h files that C and C++ use, just as the developer would have to create the documentation for other languages.

Also without documentation (or looking at the source) you haven't got a clue what the function does, even the function name can be misleading.

---

### Post by Kilon on 2009-02-03
> **ajackson said:**
> 
Also without documentation (or looking at the source) you haven't got a clue what the function does, even the function name can be misleading.


This is so painfully true. People so easily ignore the crucial importance of good documentation. 

I tried to learned GWBASIC and was 100x times more difficult to learn than C++ , because the book seriously sucked. While for C++ few years later learned from my mistake found an excellent book with so many practical examples that made the whole learning process a breeze and load of fun. That was console days. 

When I tried to learn Windows GUI, all books I tired did seriously sucked and it was a large factor for total abandonment of C++ in favor of Delphi.

Oh learning Assembly was a breeze as well , again excellent Book.

---

### Post by eye208 on 2009-02-03
> **ajackson said:**
> If you are going to pass it as a parameter you should know that it exists and that it implements OutputStream or your program wouldn't even compile, unless you have found a way of getting a compiler to recognise non-existant variable types.
No. A function declared as
```
public OutputStream getOutputStream()
```
can return an arbitrary implementation of the OutputStream interface. If can be a file, a TCP connection, a simple array of bytes, anything. I need not know, because the other function
```
public void setOutputStream(OutputStream out)
```
need not know either. I can establish a stream connection between the two objects without worrying about implementation details of the OutputStream class being used.

> The point you seem unable to grasp is that you claimed that you didn't need to refer to documentation to work out what to pass as parameters.

The header files **are** documentation, the stuff javadoc produces is **documentation**. This is why I said you are contradicting yourself.
If you are unable to grasp the difference between
[list][*]figuring out how to use a function/class simply by looking at its header, and[*]analyzing someone else's code or reading documentation that may even be written in a language other than English,[/list]
then there's really not much left we can discuss here.

---

### Post by ajackson on 2009-02-03
> **eye208 said:**
> If you are unable to grasp the difference between
[list][*]figuring out how to use a function/class simply by looking at its header, and[*]analyzing someone else's code or reading documentation that may even be written in a language other than English,[/list]

So are you trying to say that without looking at **any** documentation other than the header definition you can tell what a function does? You can see how to call it but that is about all. You still need to either read documentation produced by the **developer** or look at the code to work out what is supposed to do.

Knowing that a function takes two strings and returns a string is pretty useless unless you know what those strings are meant to represent. But hey you can call the function without the compiler complaining.

Edit: an extreme example, say you know that a function takes three numbers and returns one of them, you know how it decides which one to return. The developer alters the function but keeps the interface the same but now it returns a different number. Your program will still compile but behave differently. Just because something compiles after a library it uses changes doesn't mean it still works, that is what testing is for (and checking what the changes to the library you use where).

> then there's really not much left we can discuss here.
ahh the good old "damn my argument is getting shot to bits" exit strategy is being implemented.

---

### Post by Kilon on 2009-02-03
> **ajackson said:**
> So are you trying to say that without looking at **any** documentation other than the header definition you can tell what a function does? 


he is a genius , for a Troll that is :p

The thing is that reading source code or header files is the slowest less efficient way to understand a library. But hey that is what every macho programmer does .... so why blame him ?

But you are all noobs I prefer reading in binary format.:D

Maybe Hex , if I have a difficult day.

---

### Post by nvteighen on 2009-02-03
> **eye208 said:**
> You are merely pointing out that C's static typing system is imperfect, not that static typing is the wrong way. That's why C++ and Java are considered improvements over C. They take the static typing approach further by adding OOP features and namespaces. That doesn't mean that all C++ and Java classes are self-documenting. But still you don't need to know the details of an OutputStream in order to pass one from one object to another. The interface is an indicator that the two classes are compatible and capable of passing data to one another directly. There are no such indicators in Python.

Wait... when did I say you have to know the details of OutputStream? What I say is that from a declaration you can't know what the function means, but just how to call it... because the declaration is just **part** of the interface.

> No. OutputStream is declared in a public namespace. If I declare an incompatible type of OutputStream in my own namespace, the compiler will never confuse the two. If I declare my OutputStream in the public namespace, my program will not compile because of name conflicts. If someone tries to pass my OutputStream to a function expecting the other one, his program won't compile. There's no way the compiler could accidentally produce an executable failing due to an unresolved conflict between programmer A and B. And this is the whole point. If you work in a team on a large project, you want static typing because it forces you to sort these things out.

Ok, true. But dynamic typing does the same... of course, if you passed something wrong, it will fail during runtime, because there's no compile-time checking. And if you work in a team, what you expect is people aware of what interface is being used. Ok, you don't have the headers, but you can look at the docs and you don't need to look at any implementation detail, believe me.

Of course, if the docs are obsolete or nonexistant, then, the project's team is a sloppy one that isn't making its work as it should. But in static typed languages this would be the same... be aware that a header file may also be obsolete with respect to the compiled library and then what you get is a runtime SEGFAULT...

---

### Post by jimi_hendrix on 2009-02-03
i think we've gotten quite a bit off topic and just gotten into a duck-typed vs static typed flame war

---

### Post by ajackson on 2009-02-03
> **jimi_hendrix said:**
> i think we've gotten quite a bit off topic and just gotten into a duck-typed vs static typed flame war
True but our resident troll was making some really silly claims that needed putting right.

---

### Post by eye208 on 2009-02-03
> **ajackson said:**
> So are you trying to say that without looking at **any** documentation other than the header definition you can tell what a function does?
You really don't get it.

Repeat after me:

**If my class implements a public interface, everyone will be able to use it without ever looking at my code or my documentation.**

Please repeat this sentence until it reaches your brain. It may take a while, but it's worth it. Once you start your career as a developer in the real world, joining a team and working on projects with a deadline, you will appreciate what you have learned today. Good luck!

---

### Post by ajackson on 2009-02-03
For someone who said there was nothing more to discuss you seem very vocal.

> **eye208 said:**
> **If my class implements a public interface, everyone will be able to use it without ever looking at my code or my documentation.**
Going for the moving goalposts response, nice one.

How does anyone know what a particular interface is used for without reading the documentation? Your claim is that you can tell what a function does just by looking at the prototype in the header. That quoted part has **nothing** to do with your claim.

Edit: OK lets say your class implements an interface that lets you write to a stream, it is perfectly possible that your function manipulates the data before eventually writing it to the stream. If people didn't know what you function was supposed to do it could well confuse them and cause errors later on in the program. **Which is why they would need to check the documentation** for all they know your implementation could just be a do-nothing function, it meets the requirement of the interface.

> Once you start your career as a developer in the real world, joining a team and working on projects with a deadline, you will appreciate what you have learned today. Good luck!
What a truly pathetic response, I have worked very successfully as a developer in a large team thank you very much.

---

### Post by jimi_hendrix on 2009-02-03
*wonders how long were going to go on about this before mods come in*

---

### Post by slavik on 2009-02-03
Closing thread for review.

---

