---
title: "learning to program in C"
date: 2009-10-06
forum: Programming Talk
---

### Post by Otiosedodge on 2009-10-06
Hi Folks,

I'd really like to get into programming with C, really starting from 0. Do any of you know of what the best way to do this is? Ideally I'd like to end up developing software for Linux. 

Thanks

---

### Post by Bachstelze on 2009-10-06
You mean you have zero experience of programming? You might want to start with something simpler, like Python.

---

### Post by ApEkV2 on 2009-10-06
I started out with Bash scripting. It's a good starting point, and probably easier than Python

---

### Post by NoaHall on 2009-10-06
bash -> perl -> gtk -> php(if you want some experience with similar syntax) -> python/java -> C

Try that. It's probably a easier route to take.

---

### Post by Otiosedodge on 2009-10-06
Yes, I have zero experience. It might also be worth mentioning that I'm starting a bachelor's degree in computing this year which is quite Java-intensive, so that may make a difference. And it might also make a difference that I have very good logical abilities. Would you still recommend starting out with Python, and in any case, could you tell me a good starting point? Thanks again

---

### Post by forrestcupp on 2009-10-06
Well, you can go ahead and start with C, and just realize that it's not easy if you don't have any experience.  If you stick with it, it's not impossible, though.  The reason people suggest to start with something easier is because you see results more quickly, and there's a little less chance you'll give up.

[Here's a decent online C tutorial.](http://www.cprogramming.com/tutorial.html#ctutorial)

---

### Post by nvteighen on 2009-10-06
I'd recommend you Python -> C -> (anything else). Python has very clean syntax and semantics and also very good resources to teach beginners. That's a combination worth to take account of.

But, more important than that, is that Python is also a language that scales up very well to bigger projects, being much more than just a "toy language". So, you'll not be learning a reduced language, but a real programming language.

An alternative (which was used by MIT before Python) is Scheme... but it's a highly impractical language due to several factors I won't detail here. You'd benefit from a more pure language than Python and much more easier to get, but losing libraries, speed and... well... support.

Perl, IMO, needs knowledge from C to be understood well. Bash is a shell scripting language and as such is optimized for text processing and system programming... which is something you might need in the future, but at this stage you need something along the lines of general more abstracted programming where you could develop a programming "mindset".

C is a must, of course. Only learning Python is useless; as C works on the fundamentals of the computer... Programming is not about computers, but about abstract models... but we use them in computers and sometimes C is needed :p Also, knowing C will open the doors to a huge amount of languages similar to it (either by direct inheritance or by just influence).

---

### Post by Otiosedodge on 2009-10-06
OK, I'll digest all your answers and then get to work. Thanks a lot for all your responses!

---

### Post by nvteighen on 2009-10-06
> **Otiosedodge said:**
> OK, I'll digest all your answers and then get to work. Thanks a lot for all your responses!
Answers taste better in a sandwich :p

Good luck!

---

### Post by michaeld003 on 2009-10-06
I noticed this the other day and it seems like it may help you.

[http://www.reddit.com/r/carlhprogramming/]("http://www.reddit.com/r/carlhprogramming/")

---

### Post by SouthOfHell on 2009-10-06
> **michaeld003 said:**
> I noticed this the other day and it seems like it may help you.

[http://www.reddit.com/r/carlhprogramming/](http://www.reddit.com/r/carlhprogramming/)

^ Yep that really is pretty bloody well done, the guy explains things crystal clear.

---

### Post by NoaHall on 2009-10-06
Reddit is a horrible site to read from.

---

### Post by falconindy on 2009-10-06
> **NoaHall said:**
> **bash -> perl -> gtk -> php**(if you want some experience with similar syntax) -> python/java -> C

Try that. It's probably a easier route to take.
Given that GTK isn't really a language, is the implication here that you should be using the gtk2perl bindings? Wouldn't it be simpler just to toss out perl and learn python instead? Perl seems like something you pick up along the way for purposes of regex and file parsing -- you wouldn't necessarily need/want to learn the language in depth. php is also fairly low key compared to something like ruby which could serve the same purpose (then again, pylon is a quick extension of python and almost as powerful).

---

### Post by TheBuzzSaw on 2009-10-07
Egads, starting directly with C is not as horrible as you people make it out to be. In fact, I recommend it. I'd kill myself if I went through a dozen languages before finally reaching C/C++. The only one I learned before C was BASIC, and that was because I was 8 years old.

Get a good book, and follow through each chapter/example carefully. Don't give in to all this FUD concerning learning C/C++.

---

### Post by -grubby on 2009-10-07
Well... [http://ubuntuforums.org/showthread.php?t=667422](http://ubuntuforums.org/showthread.php?t=667422)

---

### Post by nvteighen on 2009-10-07
> **TheBuzzSaw said:**
> Egads, starting directly with C is not as horrible as you people make it out to be. In fact, I recommend it. I'd kill myself if I went through a dozen languages before finally reaching C/C++. The only one I learned before C was BASIC, and that was because I was 8 years old.

Get a good book, and follow through each chapter/example carefully. Don't give in to all this FUD concerning learning C/C++.

Well, starting out with C is not that bad for sure. The issue is that C is more about controlling the computer and that's just an accidental part of programming. Programming is about modelling realities in order to simulate them... You can of course do that in C, but you'll have to be constantly checking for the simulator's state meanwhile you're also checking for your simulation's too.

Then, you can get into the trap of believing low-level programming is "true programming"... which is as false as saying Python is "true programming", but for some reason people that only know C and C++ tend to imply that idea more than those just knowing Python (it's an empirical fact from my experience at these forums).

But it's true that C isn't that a bad choice either. A really bad choice would be C++, as its a completely messed up language where several abstraction layers are constantly interleaved (well, this also occurs in C... not at language level, but at code level); that leads to a weird mix you can't decide what's in what level of abstraction in your code. Avoid C++ for now.

---

### Post by CptPicard on 2009-10-07
It's all about the shape of the learning curve, BuzzSaw. C is a triviality *once* you have got yourself started in programming, but for a total beginner it is just rather unhelpful and harder to use than it needs be exactly because it is rudimentary.

Python is not only "easy to use" but much richer in ideas, and does that in still a rather economical, good language design... it exposes the new programmer quickly to a lot of important concepts and ideas, and in C you would just have to essentially hack it all up from scratch (or more likely not use those approaches at all), and unless you're incredibly good, that won't happen.

Once you learn how to think about programs, the machine-level details will follow in due time. Those are after all not the intellectually interesting parts.

---

### Post by TheStatsMan on 2009-10-07
I also agree python is an excellent choice as it allows you to attack the problem straightaway.

> **nvteighen said:**
> 
But it's true that C isn't that a bad choice either. A really bad choice would be C++, as its a completely messed up language where several abstraction layers are constantly interleaved (well, this also occurs in C... not at language level, but at code level); that leads to a weird mix you can't decide what's in what level of abstraction in your code. Avoid C++ for now.

Whilst, I agree C++ isn't the best choice, I think your rationale is slightly exaggerated. With C++ you construct objects on a lower level and then you use them on a higher level. For numerical computing this is extremely useful. You can for instance attack a problem on a similar level to MATLAB. If you are willing to work on a level of abstraction slightly further away from the problem (say for instance between the level of python's numpy and MATLAB) you can obtain the efficiency of C. Check out the eigen library for instance. There is good reason that C++ is so popular with engineers and people that work with large scale problems in science. 

Like all languages you can write good an bad code in C++, but perhaps it is a language that is very easy to write bad code. C++ has its flaws and it certainly is a language that is easy to write bad code, I just not sure about your rationale (even though it does seem to be a popular one around here).
.

---

### Post by myromance123 on 2009-10-07
Mmm I learnt C as my first language.
 It's not that hard if you have the right resources. Choose books that help you understand terms, keywords and the overall idea/concept of the language and its main function alongside how to use it. Don't go for technical/doodad books just yet that implement the language in , say, technical situations (or books with silly "I use big words on you but won't tell you what they mean" kind of books) :D
 Those will turn you off it easily.

 C is good because its a braces language much like Java, which if I'm not wrong is based off C. ;)
 Good Luck mate, toodles hehe
A strong foundation is everything.

---

### Post by forrestcupp on 2009-10-07
> **nvteighen said:**
> A really bad choice would be C++, as its a completely messed up language where several abstraction layers are constantly interleaved (well, this also occurs in C... not at language level, but at code level); that leads to a weird mix you can't decide what's in what level of abstraction in your code. Avoid C++ for now.

I completely disagree.  I think it's *better* to start with C++.  Object Oriented programming is very useful, especially with a powerful, lower level language like C++.  

A lot of frameworks and API's are made for C++ and not just straight C.  And if you learn C++ syntax and standard libraries, you can pretty much just leave out the object oriented stuff, and you already know C.  If you learn the object oriented stuff up front, you won't have any problem at all programming in plain C.

---

### Post by MasterOfTheHat on 2009-10-07
Well, first off, you can't really compare C to Java. You're talking about two totally different types of programming models: structured vs. object-oriented. Both are good languages to learn, but they can't be compared side-by-side.

I learned how to program in college, and the language we used was Java. It was good to learn on because it allowed us to learn an extensive OOP language while also learning data structures, good practices, etc, etc. Fortunately, we also had a class in C/C++, so I actually had an old penquin guiding me through some of the mud and muck of those languages. 

Personally, I don't think C is a good place to start programming because of all the caveats and how much it allows you to get away with bad practice. On the other hand, once you've learned the fundamentals and gotten into some good practices, there isn't a more powerful language out there! Of course, you can write bad code in any language...

Unfortunately, I don't know of a structured language to start with. The only other structured language I've dealt with is COBOL, and you definitely don't want to start there! lol! 

As for the comments about programming being about creating abstract models, etc, that is only partially true. There are definitely different types of programming and one of those is indeed modeling objects and interacting with them, but another side is the low-level programming that makes your abstract models possible! We need the drivers, OS, firmwares, low-level utilities, etc so that we have a working machine on which to create and use our models. So your definition of "true programming" is a little skewed...

---

### Post by CptPicard on 2009-10-07
It is a matter that has been discussed to death here but it seems like it needs to be reworked with newcomers every now and then so here goes... ;)

First of all before some C-guy jumps up again and accuses me of being lazy or "afraid of C" (something I've always found rather amusing), let me be perfectly clear that there's nothing wrong with my understanding of the low level for what it's worth, nor am I dissing it really... my actual initial learning path was BASIC->Pascal->C, but it's just that it has never impressed on me new ideas as much as a lot of other languages have. And the more I code, the more I think in terms of "how this problem of mine maps to concepts that are known to be computable" (and after that I've done the human input part and after that it's just proven-correct machine work), and the less I find it interesting to do work for the sake of it as life is so short... 

Really, I do wish I had started with something like Python or Scheme... but alas I had a similar mindset as a teenager that I sometimes see here... :)

> **MasterOfTheHat said:**
>  On the other hand, once you've learned the fundamentals and gotten into some good practices, there isn't a more powerful language out there!

Well... theoretically you can write anything in any language... but it seems to me that mostly C's "power" is related to execution speed, which is a valid technical goal. But I do miss my universal macros enabled my homoiconic syntax, closures, higher-order functions (the last two are theoretically important, see lambda calculus and how the relate to OOP), algebraic data types, programming by predicate-safisfaction, optimizations and parallelism enabled by pure-functionality... just to mention a few things. 

Even the much maligned garbage collection is essentially just an algorithm to solve a fairly basic resource-management problem, which then enables a lot of this stuff (closures' binding frames' lifecycle management, for example, which would be very hard to do manually).


> There are definitely different types of programming and one of those is indeed modeling objects and interacting with them

Which is a very broad way to look at the "other" types of programming... how much exposure have you had to, say, functional programming or declarative logic programming? :) An "object" is a kind of natural entity in a lot of programming languages (it does not have to be exactly the kind of object as we understand it in Java/C++) -- they are types, probably with some compatibility, plus operations on the types, and a way to resolve an operation on a piece of data based on the type information. Java/C++ implement a certain model for OOP, Lisp's CLOS another... (in my view, a superior one..)

> 
, but another side is the low-level programming that makes your abstract models possible!

And yet another side of this is that hacking up a CPU emulator with some basic opcodes, registers and RAM in something like Haskell is trivial. It's certainly hard to program in, but it's Turing-complete... :)

It all boils down to what kind of conceptuals one finds valuable...

---

### Post by TheBuzzSaw on 2009-10-07
The thread is about learning to program **in C**. If the OP indicated that he wanted to learn how to "program" certain things, we could recommend other things. However, when the request is explicitly about learning C, it pains me to see everyone come running in to say, "OMG learn languages X Y Z P Q R before learning C".

Using C does not automatically imply that someone wants low-level control. C can be very high level as well.

---

### Post by Renée Jade on 2009-10-07
Hmm. I'm learning C at the moment and I can't give you any great wisdom or overall plan. But I can share that the best thing you can do is to find nice little assignments to work on - things that help to drive home one, or a few, points at a time. Check out the website for the university you're going to attend and see if they have any lab exercises and lecture notes up for their beginner C programming course. 

Get at least one good book. But I would say get one reference-style book and one text-style book. Text books are great for teaching yourself but you need to able to look stuff up too.

Practice, practice. And don't try to force feed your brain. Enjoy the discovery process.

I've found these resources useful:
[http://www.eskimo.com/~scs/cclass/notes/top.html]("http://www.eskimo.com/%7Escs/cclass/notes/top.html")
[http://www.eskimo.com/~scs/cclass/int/top.html]("http://www.eskimo.com/%7Escs/cclass/int/top.html")
[http://www.acm.uiuc.edu/webmonkeys/book/c_guide/](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/)

I was going to say "make sure you're working on *nix", but since you're on an Ubuntu forum I guess you've gotten that far already :P

If you're on Ubuntu (well, I can only speaky for Jaunty, really) you'll want to install the 'manpages-dev' package
```
sudo apt-get install manpages-dev
```So that you can use the "man <someLibraryFunction>" command to get manual pages for functions in the standard C library.

And also, don't listen to all these people who are trying to tell you to learn scripting languages. If you want to learn a proper, compiled, general purpose language then go for it. It'll be more work but you sound keen.

I hope that helps a bit. It's just what I'm doing and it seems to be working :)

---

### Post by Renée Jade on 2009-10-07
And also, a practical tip. It may seem silly to point this out, but I gave up teaching myself C because I couldn't figure out how to compile it. So to compile your C code you should save it as a .c file and then, in the directory where the file is, use the command

```
gcc -std=c99 -Wall -Werror -pedantic -o nameForExecutable nameOf.cFile
```And to run it you use

```
 ./nameOfExecuatable argument1 argument2 ...
```Make "gcc -std=c99 -Wall -Werror -pedantic -o"  an alias.

I'm really sorry if that is a dumb thing to tell you but I was like you - totally keen to get started. And I could not work out how to compile, having only used IDEs in the past.

So just go for it: Write C, little bits at first,  and have fun.

---

### Post by nvteighen on 2009-10-07
> **TheStatsMan said:**
> I also agree python is an excellent choice as it allows you to attack the problem straightaway.



Whilst, I agree C++ isn't the best choice, I think your rationale is slightly exaggerated. With C++ you construct objects on a lower level and then you use them on a higher level. For numerical computing this is extremely useful. You can for instance attack a problem on a similar level to MATLAB. If you are willing to work on a level of abstraction slightly further away from the problem (say for instance between the level of python's numpy and MATLAB) you can obtain the efficiency of C. Check out the eigen library for instance. There is good reason that C++ is so popular with engineers and people that work with large scale problems in science. 

Like all languages you can write good an bad code in C++, but perhaps it is a language that is very easy to write bad code. C++ has its flaws and it certainly is a language that is easy to write bad code, I just not sure about your rationale (even though it does seem to be a popular one around here).
.

Hm... What bothers me in C++ is that while you can be "talking" about very abstracted classes, you still have to simultaneously be aware whether you're allocating them in stack or in heap and, if the second option, start using pointers while you are also using a very nice concept... Ok, this also happens in C when you reach a certain abstraction level height e.g. using class-like structs, but the difference seems to be that in C++ this behaivor is even present in the language while in C this is a product of your own code and the language's limitations...

Even though an experienced programmer will know how to deal with this, a beginner won't ever be able to do that.

> **forrestcupp said:**
> I completely disagree.  I think it's *better* to start with C++.  Object Oriented programming is very useful, especially with a powerful, lower level language like C++.

Well, I don't see the relationship between OOP and low-levelness. Python is also OOP... OOP can be used in C... There you have Objective-C, which implements OOP in a *very much saner* way than C++. And I've stated my view on why low-levelness is not the best way to start to program.

> A lot of frameworks and API's are made for C++ and not just straight C.  And if you learn C++ syntax and standard libraries, you can pretty much just leave out the object oriented stuff, and you already know C.  If you learn the object oriented stuff up front, you won't have any problem at all programming in plain C.

And a lot of frameworks are made for a lot of other languages too... I haven't ever said you shouldn't learn C++, but that to learn it you need some degree of maturity in order to get it well and understand it. Someone without C experience won't ever understand why std::vector isn't a generic container or why introspection is done through a pointer (this), for example.

---

### Post by forrestcupp on 2009-10-07
> **nvteighen said:**
> I haven't ever said you shouldn't learn C++, but that to learn it you need some degree of maturity in order to get it well and understand it. Someone without C experience won't ever understand why std::vector isn't a generic container or why introspection is done through a pointer (this), for example.

Well, that's the age-old argument.  Should I learn C++ and thereby learn C along with the other stuff, or should I learn C first and add object oriented ideas to that after I get a grasp on it.

I guess it really depends on the individual and how he learns.  I, personally, did better starting with C++ because it suited my needs better.  Then when I needed straight C for things like win32 programming, I already knew the syntax.

You don't really see Objective C anywhere but on the Mac.

---

### Post by jessiebrownjr on 2009-10-07
> **TheBuzzSaw said:**
> Egads, starting directly with C is not as horrible as you people make it out to be. In fact, I recommend it. I'd kill myself if I went through a dozen languages before finally reaching C/C++. The only one I learned before C was BASIC, and that was because I was 8 years old.

Get a good book, and follow through each chapter/example carefully. Don't give in to all this FUD concerning learning C/C++.

AMEN... Im doing this right now too... Heck, l I tought myself basic when I was 12 too lol.

If the guy CAN hang, then let him :-) I too often see bad advice where somebody asks a question, and instead of being told how to do it, he is only warned away from it.. I mean I can see a post where the reply has both.. a warning and a howto... but strictly a warning is deviating from the post, and not what the OP wanted :-).

Im currently on chapter 5 of C for dummies.. and its terrible but its workin slowly..

---

### Post by ApEkV2 on 2009-10-07
C is for cookie and it's good enough for me

---

### Post by TheStatsMan on 2009-10-08
^^^I think you guys are missing the point. The reason people are recommending python is not because c is too difficult, it is because it will allow you to concentrate on programming interesting things and learning how to program rather that worrying about the language. Then once you already know how to program, then you will be able to learn C more quickly, so you can use it when you need to.

---

### Post by Renée Jade on 2009-10-08
> **TheStatsMan said:**
> ^^^I think you guys are missing the point. The reason people are recommending python is not because c is too difficult, it is because it will allow you to concentrate on programming interesting things and learning how to program rather that worrying about the language. Then once you already know how to program, then you will be able to learn C more quickly, so you can use it when you need to.

I agree dude. I learned Java first and now I looking back I understood so little about programming when Java was all I knew, but it helped me to **start** understanding. It was a great place to start and I recommend it (I only started programming this year and have come a long way fast, so it's all fresh in my mind).  But the OP says he wants to learn C. And he sounds keen and confident. I reckon he'll be ok :)... But mate - as someone who was in your shoes less than a year ago, I would say that Python or Java are probably a good choice to get you started. But stick to multi-purpose sorts of things. Don't worry about Bash or other typically "scripting" languages. (Ok, I know that Python is a scripting language but it's a big one. And a lot of people say that Python is the bomb if you're coding for fun - I wanna learn it myself). 

But if you wanna learn C then learn C. You can do it! :)

---

### Post by rkwill98356 on 2009-10-08
In college, I learned several languages; however, Not C.
I learned the C statements in a 3 day seminar at the Hartford Adult Ed Center in Hartford, CT.
In general, C has 7 statements, that makes it very easy to learn.
It also has an extensive standard library.  Many of the entries in the standard library are used extensively.  
C has no intrinsic I/O, all I/O and most other common actions are in the standard library; therefore, it pays to learn the standard library functions also.

With practice, the gritty details of those 7 statements are easily mastered.

The concepts of program design are (generally) the same, irregardless of the language used.  
Some languages make it easy to manipulate the hardware (I.E. C).  
Some languages make it easy to manipulate data (I.E. Lisp, Prolog).  
Which language to use for any one application depends mostly on what function the application must accomplish and  how fast it has to accomplish that function.

*I* would be more concerned withlearning how to think in abstract/programming  concepts, then learn how to implement those concepts in the selected language.

---

### Post by VertexPusher on 2009-10-08
> **Otiosedodge said:**
> I'd really like to get into programming with C, really starting from 0. Do any of you know of what the best way to do this is? Ideally I'd like to end up developing software for Linux.
Get a book on C programming for beginners, e.g. "Teach Yourself C" by Herbert Schildt, and read the GNU Coding Standards ([http://www.gnu.org/prep/standards/](http://www.gnu.org/prep/standards/)). That's all you need to get started.

Probably the most important thing to learn is how to use 3rd party libraries. C is a very simple language with a small standard library for basic I/O, memory management, string manipulation and math functions. Its simplicity makes it easy to learn, but if you want to do anything useful with it (GUI, networking, database access, multimedia etc.) you'll need to link 3rd party libraries with your programs.

---

### Post by grayrainbow on 2009-10-08
[http://www.amazon.com/C-Dummies-One-Two-Bundle/dp/1568849397](http://www.amazon.com/C-Dummies-One-Two-Bundle/dp/1568849397)
 
Basicly there's lot written about C, but in general C got just 32 keywords and pretty much that makes it easyest language of them all. One just have to pay attention to importand stuff:
1) memory managment(which is the most importand part of programming), when reading about pointers - read slowly.
2) user defined "types" - it can take less than a minet to understand hight leve data structure if you were pay attention while learning 1)
Once you understand 1) and 2) you can create what ever you can imagine(sometimes people imagine programming languages and usually implement them whit C, python is an example)
3) Calling third party libraryes(it's platform specific, so it can have nothing to do with beginners stuff, choose one platform and stay with it at least a year)
 
Last, but not least - don't forget that all come from the hardware and how one use it.

---

### Post by nvteighen on 2009-10-08
> **grayrainbow said:**
> [http://www.amazon.com/C-Dummies-One-Two-Bundle/dp/1568849397](http://www.amazon.com/C-Dummies-One-Two-Bundle/dp/1568849397)
 
Basicly there's lot written about C, but in general C got just 32 keywords and pretty much that makes it easyest language of them all. One just have to pay attention to importand stuff:
1) memory managment(which is the most importand part of programming), when reading about pointers - read slowly.
2) user defined "types" - it can take less than a minet to understand hight leve data structure if you were pay attention while learning 1)
Once you understand 1) and 2) you can create what ever you can imagine(sometimes people imagine programming languages and usually implement them whit C, python is an example)
3) Calling third party libraryes(it's platform specific, so it can have nothing to do with beginners stuff, choose one platform and stay with it at least a year)
 
Last, but not least - don't forget that all come from the hardware and how one use it.
It's got only 32 keywords and almost none concept... Its easiness to learn its syntax and constructs lies on the former; its hardness to use relies on the latter.

If you take a deep look on C, you'll see there aren't even types in it... "types" are defined by space in memory and that's why you get that weak typing discipline in C. There is no "integer" concept nor a "character" one. You got just different predefined basic segmentations of memory... which you can use no matter what you put inside as long as the content fits that segmentation. 

The concept of int = integer, char = character (which actually are used through their ASCII values) is actually in C programmers' mind but that idea holds no real mapping in the C language. What consequences does this have? Well, look at all the hassle strings give to a beginner... When you realize that, while using char * to **denote** a certain string, actually char * **means** a pointer to a char, you start seeing how the machine details are who build the meaning system in C and not actually anything more abstracted like in other languages.

Of course, that kind of stuff is probably confusing for the most of the people as far from my experience here. Humans need a consistent semantical system or we get easily confused... Python is extremely coherent on its semantics, maybe not perfect, but starts with a set of principles that it follows very well... Of course I know that under a Python int you have a C struct and that all boils down to Assembly, but in well-designed higher-level languages you observe a "cut" in which you start seeing that the language itself is retroactively defining itself making unnecessary any reference to the lower abstraction level (of course that means also a disadvantage).

That's my point. I know it's not the regular argument of a programmer, but a Linguistic student's... :P

---

### Post by TheBuzzSaw on 2009-10-08
> **rkwill98356 said:**
> ...irregardless...

I lost focus once I hit this word. XD

---

### Post by __p1n__ on 2009-10-08
I'd skip python, c, and, c++ for the moment if you're interested in becoming an open systems application developer.  Commerical open system application development has moved pretty heavily to J2EE.

For system/networking apps and anything high-speed it's C/C++ of course.  If you're serious about becoming effective with these languages and actually understanding what you're doing then instead of trial and error I suggest that you read the following in sequence:

'The C Programming Language' - Kernighan & Ritchie
'The Standard C Library' - Plauger
ISO C99 Specification

'C++ Primer' - Lippman
'Effective C++' - Meyers
'The Draft Standard C++ Library' - Plauger
'The C++ Standard Template Library' - Plauger
'Inside the C++ Object Model' - Lippman
'The Annotated C++ Reference Manual' - Stroustrup (i'm serious, read this last)
ISO C++98 Specification

Good luck!

---

### Post by Can+~ on 2009-10-08
> **__p1n__ said:**
> I'd skip python, c, and, c++ for the moment if you're interested in becoming an open systems application developer.  Commerical open system application development has moved pretty heavily to J2EE.

So what? What's "popular" in the business doesn't imply that is the best learning route.

And most people here will say "this is the path that I took, and I recommend it, because ...". And it's fairly valid, programming languages aren't all that different from each other. But only people that who have learned beyond the practical aspect of a language can give the "hollistic" viewpoint. Analyze your own path an realize, maybe your choices weren't all that good.

In my case, I started with Actionscript (that thing from Flash), something like a Java dialect, moved to C, C++, Python, Scheme, Java and little perl (currently learning: R). And you know what? I wouldn't recommend neither Actionscript nor C to a newbie. And I can relate to myself on those years, as I remember not knowing what the heck I was doing.

From my experience, I conclude that Python is pretty much the safest entrance. Strict indentation rules enforces good coding, not need to know about typing, casting, pointers, or memory management (looking at C), not having to deal with Classes without even knowing the OO paradigm (looking at Java), not having to deal with strange design choices on the syntax (looking at C++).

And contrary to most people believe in this forum, C is still my favorite language.

---

### Post by shadylookin on 2009-10-08
Well if you have to learn java for school then I would consider just picking up java now. Python is nice and all but if you have to learn java it's not terribly hard for a beginner to learn. 

If you have your heart set on C I use [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/) for references on how to use the standard library functions. I would avoid purchasing the teach yourself c in 21 days series(I bought the 6th edition and it was pretty bad)

oh and get the build essentials sudo apt-get install build-essential

---

### Post by jessiebrownjr on 2009-10-08
> **Otiosedodge said:**
> Hi Folks,

I'd really like to get into programming with C, really starting from 0. Do any of you know of what the best way to do this is? Ideally I'd like to end up developing software for Linux. 

Thanks

I just wanted to repost his statement incase the thread was derailing.  A lot of you guys are referring him to other languages assuming C will be too hard or that he should take baby steps via another language.

  __p1n__ had a good post.. Said why he shouldn't, but here is how to do it if you want to anyway. Some people learn easier then others and in different ways. You shouldn't always try to scare somebody off of something.  I, for instance, type/talk like I have an 8th grade education but have an engineering degree... I get lost driving in new towns easier then normal hehe... But, I am learning C fairly easy, without knowing anything else but Qbasic when I was 12, and I hardly would say I mastered it then! 

I guess what I'm saying yet again is, when ya post, think about what the original poster was asking, and see if you can answer his question :-)

---

### Post by ApEkV2 on 2009-10-08
> **jessiebrownjr said:**
> 
I guess what I'm saying yet again is, when ya post, think about what the original poster was asking, and see if you can answer his question :-)
Amen

---

### Post by VertexPusher on 2009-10-09
> **jessiebrownjr said:**
> I just wanted to repost his statement incase the thread was derailing.  A lot of you guys are referring him to other languages assuming C will be too hard or that he should take baby steps via another language.
Thank you for this. I was wondering why many people here chose to discourage the OP instead of answering his question. C is still quite an important language, maybe the most important one on Linux, so we should welcome anyone who's not afraid to learn and use it.

---

### Post by nvteighen on 2009-10-09
> **VertexPusher said:**
> Thank you for this. I was wondering why many people here chose to discourage the OP instead of answering his question. C is still quite an important language, maybe the most important one on Linux, so we should welcome anyone who's not afraid to learn and use it.
Because although we can be mistaken or right, we believe that the OP is choosing a wrong method and we express our opinion hoping it will benefit the OP. That's it.

---

### Post by TheStatsMan on 2009-10-09
> **jessiebrownjr said:**
> I just wanted to repost his statement incase the thread was derailing.  A lot of you guys are referring him to other languages assuming C will be too hard or that he should take baby steps via another language.


I think people are suggesting that the OP should take big steps via another language rather than baby steps via C. 

Also the OP's second post, which suggests the OP is open to suggestion and possibly interested in peoples opinion on the matter.
 
> 
Yes, I have zero experience. It might also be worth mentioning that I'm starting a bachelor's degree in computing this year which is quite Java-intensive, so that may make a difference. And it might also make a difference that I have very good logical abilities. Would you still recommend starting out with Python, and in any case, could you tell me a good starting point? Thanks again


---

### Post by descendency on 2009-10-09
> **Otiosedodge said:**
> Yes, I have zero experience. It might also be worth mentioning that I'm starting a bachelor's degree in computing this year which is quite Java-intensive, so that may make a difference. And it might also make a difference that I have very good logical abilities. Would you still recommend starting out with Python, and in any case, could you tell me a good starting point? Thanks again

Given this, I'd start with Java. You'll take a C class sometime before you graduate.

---

### Post by napsy on 2009-10-09
Otiosedodge: since C is very low level if you compare it to other "modern" languages like Python, Java or C#, I would sudgest you get a good C book like K&R. 

The problem with C is that if you're not experienced enough and trying to build a medium/large program, you'll have troubles as the code gets bigger and bigger. For some problems it's better to use other languages than C.

About Java... the SDK gives you great features if your'e building enterprise software but for regular development many of those features are bloat. The language itself is more complex then e.g. C. You immediately have to understand classes, polymorphism, generics.

---

### Post by Chronon on 2009-10-09
I think checking out an open source project written in your language of choice can be quite illuminating.

---

### Post by VertexPusher on 2009-10-09
> **Otiosedodge said:**
> Yes, I have zero experience.
If you go to a public forum and ask what's the best way to learn Linux, some people will tell you: Get a Mac! It's easier for beginners!

That's exactly what is happening here. Since you stated that you have zero experience, everyone takes the opportunity to plug his favorite language. "Get them while they're young!" is the motto.

There's nothing wrong with learning C as a first programming language. Likewise, there is nothing wrong with learning some other language as a first programming language. However, you won't learn Chinese faster by learning Spanish first, no matter what people tell you about big steps vs. baby steps etc.

---

### Post by TheStatsMan on 2009-10-09
> **VertexPusher said:**
> If you go to a public forum and ask what's the best way to learn Linux, some people will tell you: Get a Mac! It's easier for beginners!

That's exactly what is happening here. Since you stated that you have zero experience, everyone takes the opportunity to plug his favorite language. "Get them while they're young!" is the motto.


Well in my case I don't have a favorite language, although there are some languages I don't like. Most of the time I code in C++. Yet as useful as C++ is to me I would not recommend it to someone with zero programming experience. Not cause it is hard, simply because a lot of syntax needs to be learned before the language becomes useful. Templates are the perfect example, they are extremely useful, particularly to a guy like me that does a lot of numerical coding. They provide an extremely nice approach to polymorphism, then there is template meta-programming and fantastic things like expression templates, making it a weapon for numerical problems. The catch with templates is that while they are very useful there is a lot of strict syntactic rules, which must be followed, if you don't want the compiler too spit out 100 error messages. Now should someone who hasn't programmed before be getting bogged down in syntax or should they be learning to program.  

> 
There's nothing wrong with learning C as a first programming language. Likewise, there is nothing wrong with learning some other language as a first programming language. However, you won't learn Chinese faster by learning Spanish first, no matter what people tell you about big steps vs. baby steps etc.
 
This analogy does not clearly reflect the point people are trying to make. They are saying learn how to program first, worry about syntax and other issues (associated with lower level programming) latter.

---

### Post by Grey Melon on 2009-10-09
> **Otiosedodge said:**
> Hi Folks,

I'd really like to get into programming with C, really starting from 0. Do any of you know of what the best way to do this is? Ideally I'd like to end up developing software for Linux. 

Thanks

C is a great choice to start with. You'll be fine and will look back on this one day and wonder why you didn't do it sooner. 

I don't know if anyone has mentioned this already but C has only become more useful over the years as a result of the growth of the electronics market. The lines are already blurred in regard to "computer or embedded". Nearly every electronic device you buy has at least one microprocessor in it that was programmed either with C or something similar.

I recommend this book: "C Primer Plus, fifth edition" by Stephen Prata. The ISBN# is 0-672-32696-5.

This book will cement your intent to start with C. Also if you need more validation on C's usefulness head on over to [COLOR=Red][http://www.avrfreaks.net/](http://www.avrfreaks.net/)[/COLOR] 

You'll love C. Good luck and remember that while constructive criticism is great you should take it with a grain of salt and follow your instincts after you've gathered as much information as you can absorb. Sometimes it's better to quiet the mind and listen to your guts. Mmmm I'm hungry.

---

### Post by kayosiii on 2009-10-09
here's my take:
C is a nice sensible small language that is good for writing, system libraries, situations where you need to manipulate a lot of data quickly (eg video conversion filter) it is also quite handy for working on small embeded systems. I use it for micro controllers. Its best for small applications. (C++ scales up further but takes more maintenence than true high level languages). If these are things you want to do then.

There is plenty of good sample code lying around (apt-get source) should be your friend here - Get your self a nice IDE or at least editor (I am really enjoying kdevelop at the moment) purhaps look into getting a good book on C (don't have any specific reccomendations) and finally Internet search engines are your friends.

---

### Post by jessiebrownjr on 2009-10-09
> **Grey Melon said:**
> C is a great choice to start with. You'll be fine and will look back on this one day and wonder why you didn't do it sooner. 

I don't know if anyone has mentioned this already but C has only become more useful over the years as a result of the growth of the electronics market. The lines are already blurred in regard to "computer or embedded". Nearly every electronic device you buy has at least one microprocessor in it that was programmed either with C or something similar.

I recommend this book: "C Primer Plus, fifth edition" by Stephen Prata. The ISBN# is 0-672-32696-5.

This book will cement your intent to start with C. Also if you need more validation on C's usefulness head on over to [COLOR=Red][http://www.avrfreaks.net/](http://www.avrfreaks.net/)[/COLOR] 

You'll love C. Good luck and remember that while constructive criticism is great you should take it with a grain of salt and follow your instincts after you've gathered as much information as you can absorb. Sometimes it's better to quiet the mind and listen to your guts. Mmmm I'm hungry.

I like your style! :-)  I'm personally dead set on C because im going into robotics and Linux is hawt too... yeah..

---

### Post by aiworld on 2009-10-14
Wonder if anyone mentioned The C Programming Language, second edition, by Brian **Kernighan** and Dennis **Ritchie.**
That's the must. The rest is OS particulars.

---

### Post by matmatmat on 2009-10-14
> **aiworld said:**
> Wonder if anyone mentioned The C Programming Language, second edition, by Brian **Kernighan** and Dennis **Ritchie.**
That's the must. The rest is OS particulars.

+1, bit on the thin side though.
I suppose C isn't that big though...

---

### Post by raydeen on 2009-10-14
Ansi C Made Easy - Herbert Shildt is the book I've been using. It's old, but easy to read, especially the code. It's not printed in any shaded blocks or funky fonts. Very easy on the old eyes. :)

[http://www.amazon.com/ANSI-Made-Easy-Herb-Schildt/dp/0078815002/ref=sr_1_1?ie=UTF8&s=books&qid=1255559010&sr=8-1](http://www.amazon.com/ANSI-Made-Easy-Herb-Schildt/dp/0078815002/ref=sr_1_1?ie=UTF8&s=books&qid=1255559010&sr=8-1)

---

### Post by 65daysofstatic on 2009-10-14
> **aiworld said:**
> Wonder if anyone mentioned The C Programming Language, second edition, by Brian **Kernighan** and Dennis **Ritchie.**
That's the must. The rest is OS particulars.

+1 

a must have for a C programmer :)

---

### Post by SouthOfHell on 2009-10-14
> **aiworld said:**
> Wonder if anyone mentioned The C Programming Language, second edition, by Brian **Kernighan** and Dennis **Ritchie.**
That's the must. The rest is OS particulars.


I'll probably get flammed for this but here's my two cents anyhow, I found K&R one of **the** most boring and terse books out there, honestly, if anything put me off C for sometime, that would've been it.

[carlhprogramming]("http://www.reddit.com/r/carlhprogramming/?count=100&after=t3_9olf8") > K&R.   Anyday.

---

### Post by Grey Melon on 2009-10-15
I actually agree with you *SouthOfHell*. K&R put me off in the way it read and did not contain the most recent updates to the standard.

I also picked up Herbert Schildt's "[C: The Complete Reference, 4th Ed.]("http://www.amazon.com/gp/product/0072121246/ref=pd_lpo_k2_dp_sr_1?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=0078824761&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=06N4RQDWT5R7K22Z33AQ")" as I usually learn more efficiently from reference style text. This book did not jive with me either. Overuse of needlessly large words. Not practical or efficient for me.

After picking up "[C Primer Plus]("http://www.amazon.com/Primer-Plus-5th-Stephen-Prata/dp/0672326965/ref=sr_1_1?ie=UTF8&s=books&qid=1255616433&sr=1-1")" everything changed for the better. It has been said here before, and should be repeated, that different people learn in different ways so you might have different results. */* 3 "different's" in one sentence. That's a personal best*/*

Having said that, I have noticed an upsetting pattern of behavior regarding the learning of any proficiency. There are many people out there who, once they understand something, will tend to protect that knowledge. Seems as if they feel that they've earned it and why should they make it any easier for those that follow. I'm sure everyone here has seen this on many different forums and I've experienced it in the physical classroom as well.

Now in regard to learning C I still get very frustrated when I'm trying to understand a concept better. I have never seen the high level of resistance to sharing, with other languages or proficiencies, as I have with C. I don't know why but there is a sea of attitude out there sprinkled with wonderful human beings that "get it". You really have to dig and it's aggrivating but it inspires me to freely share as I continue to learn.

This really is one of the rare and great forums though. It's also a great place to help each other out. I've lurked here many times to save my *** and thanks to all for that.

---

### Post by makkirot on 2009-10-15
Buddy ,What ever u learn ..try to execute it. I prefer u read the complete reference book for C.

---

### Post by SouthOfHell on 2009-10-16
> **Grey Melon said:**
> 

Having said that, I have noticed an upsetting pattern of behavior regarding the learning of any proficiency. There are many people out there who, once they understand something, will tend to protect that knowledge. Seems as if they feel that they've earned it and why should they make it any easier for those that follow. I'm sure everyone here has seen this on many different forums and I've experienced it in the physical classroom as well.

Now in regard to learning C I still get very frustrated when I'm trying to understand a concept better. I have never seen the high level of resistance to sharing, with other languages or proficiencies, as I have with C. I don't know why but there is a sea of attitude out there sprinkled with wonderful human beings that "get it". You really have to dig and it's aggrivating but it inspires me to freely share as I continue to learn.



I know exactly what you mean actually, try asking for help in freenode #C for instance, all you get is a wall of flame, it's pretty disgusting to be honest.

---

### Post by CptPicard on 2009-10-16
> **rkwill98356 said:**
> 
The concepts of program design are (generally) the same, irregardless of the language used.

Oh, I have to take issue here. In particular functional and declarative logic programming languages design programs in ways that are very very interesting compared to your typical imperative way of doing things. It is only the imperative, usually C-derived way of programming that tends to be very similar across the same family of languages.

> 
Some languages make it easy to manipulate data (I.E. Lisp, Prolog).

Interestingly, it pretty much always boils down the relationship between computation and data, and the computability of data... and the reproduciability of data by computation...

> 
*I* would be more concerned withlearning how to think in abstract/programming  concepts, then learn how to implement those concepts in the selected language.

Okay, generally agreed, +1.


> **Can+~ said:**
> 
And contrary to most people believe in this forum, C is still my favorite language.

Contrary to what most people believe in this forum, I am willing to respect this view coming from you as I know that you're one of those people who does not speak from willful ignorance. :)


> **VertexPusher said:**
> 
That's exactly what is happening here. Since you stated that you have zero experience, everyone takes the opportunity to plug his favorite language. "Get them while they're young!" is the motto.

Yes, while they're young, I'd rather prod them into productive directions.

> However, you won't learn Chinese faster by learning Spanish first, no matter what people tell you about big steps vs. baby steps etc.

Untrue. Programming languages actually occupy a very fruitfully common niche here. There is a certain logical rhyme and reason to Turing-computable symbolic systems, which does not exist (and cannot exist) in natural languages. Learn to apply your mind while the computer does the computer-computable stuff, and you've got it all.

---

