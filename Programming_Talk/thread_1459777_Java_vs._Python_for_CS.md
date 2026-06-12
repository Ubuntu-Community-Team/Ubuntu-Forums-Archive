---
title: "Java vs. Python for CS"
date: 2010-04-21
forum: Programming Talk
---

### Post by rabid9797 on 2010-04-21
Hello Programmers!

I'm a college freshman(to be sophomore next semester) and am currently a Computer Science Minor.

This semester I took Computer Science and thoroughly enjoyed the experience(I'm taking a 100 in the class), I found the entire process of programming incredibly stimulating and loved every second of it.

The CS classes at my college all use Java for CS I and partially for CS II(I think they move in to C towards the end), and this all fine and dandy, I've had no problem learning Java...

But, I recently picked up [**Dive Into Python**](http://diveintopython.org/) and was startled by how easy it was to learn. Dynamic Language, non-explicit variables, functions as objects, indentation, whitespaces. It's all so much more natural and (in my opinion) easier to pick up than Java is.

Now I've done some googling and for the most part can't find any relevant websites/postings that make the case for what languages are the best choice for beginning programmers/Computer Science classes, but it seems apparent to me that Java is not the best choice.

TLDR

**So I ask you, fellow programmers, why is Java so popular as a beginning language? Why not Python, C, or some other language?**

---

### Post by delfick on 2010-04-21
Same thing is at my uni.

I could be very much mistaken, but I believe the reasoning that it means the students don't understand what the computer is actually doing otherwise.

As in the fact that the computer doesn't interpret text, it interprets byte code; it has to be told what particular pieces of memory represent, etc.

(though you could probably say the same when comparing assembly to C)

However, atm I'm a student tutor for two different units for first year programming (one is for the engineers (i.e. from all types of engineering), and the other is for cs students) and I find that what happens is they get caught up in the syntax rather than the concepts and it creates quite a bit of unnecessary confusion that they can't get past.

Personally, I think it'd be better to learn the concepts of programming and algorithm design before using a language in the first place at all.

But then again, I'm just a student, and you'd think there's smarter people than me who make these decisions as to what is taught :p

........

:D

---

### Post by Cracauer on 2010-04-21
They want the compile-time type checking.

Also, Python's indentation based syntax isn't good for people who never entered anything in any syntax.

---

### Post by delfick on 2010-04-22
Forced indentation would be a great thing.

No matter how many times I stress to my students to indent they're code, they don't.

Makes it very hard to read.

---

### Post by slavik on 2010-04-22
IMO, style shouldn't be forced.

Other than that, schools want to teach some language which is "used in the field" which at this point in time puts Java at the top. Back in the day, it was C, then for a short time, C++.

One thing I will note from experience is that once you get hang of Java syntax, knowing the language becomes useless. Once you know how to sort of express yourself, you find libraries that do it better, but then you start misusing them and causing all kinds of havoc. For example, you may think that running an update query on a table with 10 columns is no biggie and when you test, your requests get handled within 2-3 seconds (which I would say is acceptable for a web page). What you don't realize is that you will get 1000 requests per minute and since you are using a J2EE server with a JDBC pool, you will max it out!

Or, say you configure hibernate in some weird forsaken way that causes you to pull more data from the DB than you actually need (someone with actual hibernate understanding, please chime in), because you are lazy.

Another one. You allocate random objects without understanding how garbage collection works and cause the JVM to spin on FullGC.

---

### Post by howlingmadhowie on 2010-04-22
> **slavik said:**
> IMO, style shouldn't be forced.

yeah, but with python it's not style but syntax. forcing indentation in java would be forcing style, forcing indentation in python is like forcing use of { or [ or ( in java.

note how horrible C based languages are in this respect.  a huge mish-mash of , { [ ( * & ; :: and others, all of which have to be learned and correctly applied.  pupils have better things to do than learn details of specific broken representations of how-to knowledge.

> 
Other than that, schools want to teach some language which is "used in the field" which at this point in time puts Java at the top. Back in the day, it was C, then for a short time, C++.

no, no, no. schools should teach concepts. specific implementations are to be learned during job experience or at a technical college.

in general i'd say python is a bit better than java. by which i mean that it isn't quite as brain-dead. java is basically short hand for writing register operations, python seems to be a bit more about programming, but still terribly limited---no first-class functions, no continuation passing, no way to explicitly set evaluation order (normal, lazy ...).  in other words, no support for basic programming concepts.

crumbs, i sound quite negative in this post.  it's just certain languages annoy me.  python just annoys me a little less than java.

---

### Post by howlingmadhowie on 2010-04-22
> **delfick said:**
> Same thing is at my uni.

I could be very much mistaken, but I believe the reasoning that it means the students don't understand what the computer is actually doing otherwise.

As in the fact that the computer doesn't interpret text, it interprets byte code; it has to be told what particular pieces of memory represent, etc.

(though you could probably say the same when comparing assembly to C)

However, atm I'm a student tutor for two different units for first year programming (one is for the engineers (i.e. from all types of engineering), and the other is for cs students) and I find that what happens is they get caught up in the syntax rather than the concepts and it creates quite a bit of unnecessary confusion that they can't get past.

Personally, I think it'd be better to learn the concepts of programming and algorithm design before using a language in the first place at all.

But then again, I'm just a student, and you'd think there's smarter people than me who make these decisions as to what is taught :p

........

:D

indeed! my thoughts exactly.  

have a look at scheme, if you don't know it already. it's a language with very little syntax. it just contains brackets instead of the huge mess of strange symbols and stuff found in C based languages.

---

### Post by howlingmadhowie on 2010-04-22
> **Cracauer said:**
> They want the compile-time type checking.

the trouble with explicit typing is that you end up with instance declarations like this:
```

MyLongClassName myLongClassName=new MyLongClassName();

```
and class declarations like this:
```

class MyComplicatedClass extends MyComplicatedAbstractClass implements InDatabaseStoreable, RespondsToRequestA, CanBePassedMessageB, DoesntBreakWhenIDoThis { ... }

```

> 
Also, Python's indentation based syntax isn't good for people who never entered anything in any syntax.

python's indentation based syntax is a godsend compared with curly brackets found in C based languages. It mandates half-way readable code.

---

### Post by Some Penguin on 2010-04-22
> **rabid9797 said:**
> 
The CS classes at my college all use Java for CS I and partially for CS II(I think they move in to C towards the end), and this all fine and dandy, I've had no problem learning Java...

But, I recently picked up [**Dive Into Python**]("http://diveintopython.org/") and was startled by how easy it was to learn. Dynamic Language, non-explicit variables, functions as objects, indentation, whitespaces. It's all so much more natural and (in my opinion) easier to pick up than Java is.

Computer science isn't about white space or other syntactical issues.   There are IDEs that can handle your code formatting needs in ridiculously customizable fashion, these days.

What you should be spending your time is not whether your columns properly line up or whether you're going to accidentally abuse a type system but such things as what's an appropriate algorithm for looking for occurrences of a few hundred thousand strings in a couple of million strings,  identifying similar users by social graphs or purchase histories, developing storage systems that gracefully handle hardware degradation or loss, and so forth -- higher-level problems where the coding is the simplest part of the problem, by far.

---

### Post by ja660k on 2010-04-22
Java is a good foundation because there is alot of potential...
its easier to write then C++

and the API is getting to the point where you think why would anyone need, javax.sound.midi

For the algorithmic side of CS my institution used C, its a faster language and collections have been implemented already in java, trees, maps, lists
so there is no need to reinvent the wheel, 

after learning 5 semesters of java, then C i took for granted the humble
List l = new List();

---

### Post by rabid9797 on 2010-04-22
> **Some Penguin said:**
> Computer science isn't about white space or other syntactical issues.   There are IDEs that can handle your code formatting needs in ridiculously customizable fashion, these days.

What you should be spending your time is not whether your columns properly line up or whether you're going to accidentally abuse a type system but such things as what's an appropriate algorithm for looking for occurrences of a few hundred thousand strings in a couple of million strings,  identifying similar users by social graphs or purchase histories, developing storage systems that gracefully handle hardware degradation or loss, and so forth -- higher-level problems where the coding is the simplest part of the problem, by far.


I agree, that's the point I was trying to make, albeit I didn't actually say concepts over language. I was trying to illustrate that because it was more natural a beginning programmer can focus more on the concepts instead of having to worry about the details. ATM I use Geany(my CS class uses Jgrasp, which is horrible) and have found the auto indenting, color-coding, etc. is a nice deviation from having to worry about it all myself.

[quote="delflick"]However, atm I'm a student tutor for two different units for first year programming (one is for the engineers (i.e. from all types of engineering), and the other is for cs students) and I find that what happens is they get caught up in the syntax rather than the concepts and it creates quite a bit of unnecessary confusion that they can't get past.

Personally, I think it'd be better to learn the concepts of programming and algorithm design before using a language in the first place at all.
[/quote]

[quote="howlingmadhowie"]no, no, no. schools should teach concepts. specific implementations are to be learned during job experience or at a technical college.[/quote]

This is almost the point im trying to make! While I agree concepts should be the main focus when teaching programming, I do think having a language to actually implement the ideas, to flesh them out so you can actually see what you're doing with concrete results rather than abstracts in your head, is essential. I think there's an equilibrium that should be met with the two: concepts coming above all, but using a language that allows the concepts to be implemented in an easy to understand fashion without all the hub-bub of syntax and small details.

---

### Post by CptPicard on 2010-04-22
> **slavik said:**
> 
Or, say you configure hibernate in some weird forsaken way that causes you to pull more data from the DB than you actually need (someone with actual hibernate understanding, please chime in), because you are lazy.

Well, the problem here is that you're lazy and not your association fetching strategy. Put "fetch=lazy" there somewhere in the mapping or something :)

> **ja660k said:**
> 
For the algorithmic side of CS my institution used C, its a faster language and collections have been implemented already in java, trees, maps, lists
so there is no need to reinvent the wheel, 

For the algorithmic side of CS it's also sufficient to use pencil and paper :) Although Java has collections implemented in standard library, I took my own data structures class in Java just fine, because naturally, using the ready-made classes was forbidden...

This is, again, the same discussion as in [http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794) . No need to repeat myself if I just direct you guys to read it.

---

### Post by wmcbrine on 2010-04-22
> **ja660k said:**
> Java is a good foundation because there is alot of potential...
its easier to write then C++Maybe so, but that's not saying much.

> [i]after learning 5 semesters of java, then C i took for granted the humble
List l = new List();[/i]Python:
l = []

---

### Post by simeon87 on 2010-04-22
I started programming with Java and I'm still unlearning the habit that everything is an object. After languages like Haskell, PHP and Python, it's going much better though.

---

### Post by nvteighen on 2010-04-22
Hm... Static typing is somewhat weird in a high-level language like Java. I mean, I know it is because that way the compiler will be able to optimize code in a better way... but compilers and execution time optimizations aren't actually part of Computer Science (study of computable algorithms)... they're part of the implementational side of it (important as well, of course).

If your course is about algorithms and data structures and the like, I guess Python is much more suited for such. If it's about Software Engineering, maybe Java is the best of both...

Anyway, if you're required to use Java, you'll be expected to use it like it or not :P

---

### Post by CptPicard on 2010-04-22
> **simeon87 said:**
> I started programming with Java and I'm still unlearning the habit that everything is an object. After languages like Haskell, PHP and Python, it's going much better though.

Well, in most languages, everything is a kind of object. In Java the static-typedness just makes things much more explicit and in your face.


> **nvteighen said:**
> but compilers and execution time optimizations aren't actually part of Computer Science (study of computable algorithms)... they're part of the implementational side of it (important as well, of course).

Well, constructing and analyzing those things is of course a subset of CS theory, they have their own field of study which can be quite complex. However, at least the vast majority of parsing and static-compilation is already well-established and known.

The source-code transformation is just another algorithm, of course.

---

### Post by trent.josephsen on 2010-04-22
> **ja660k said:**
> after learning 5 semesters of java, then C i took for granted the humble
List l = new List(); 

> **wmcbrine said:**
> Maybe so, but that's not saying much.

Python:
l = []

I hope neither of you ever actually use lowercase L as an identifier. ;)

---

### Post by slavik on 2010-04-22
> **howlingmadhowie said:**
> yeah, but with python it's not style but syntax. forcing indentation in java would be forcing style, forcing indentation in python is like forcing use of { or [ or ( in java.

note how horrible C based languages are in this respect.  a huge mish-mash of , { [ ( * & ; :: and others, all of which have to be learned and correctly applied.  pupils have better things to do than learn details of specific broken representations of how-to knowledge.


no, no, no. schools should teach concepts. specific implementations are to be learned during job experience or at a technical college.

in general i'd say python is a bit better than java. by which i mean that it isn't quite as brain-dead. java is basically short hand for writing register operations, python seems to be a bit more about programming, but still terribly limited---no first-class functions, no continuation passing, no way to explicitly set evaluation order (normal, lazy ...).  in other words, no support for basic programming concepts.

crumbs, i sound quite negative in this post.  it's just certain languages annoy me.  python just annoys me a little less than java.

notice the want vs. should. :) (I agree with the should). However, when a company wants a J2EE developer (or a graphics developer, or anything), they want someone who already has experience.

This is like the situation that you *MUST* have a college degree to get a decent job, whereas 200 years ago, high school was the norm.

When I was interviewing, head hunters refered to their clients wanting someone who can hit the ground running. This is impossible for someone who is an expert at the very same system, but has not worked with the group or the specific setup before.

---

### Post by phrostbyte on 2010-04-22
Python is a better introductory CS language in my opinion.

---

### Post by delfick on 2010-04-22
> **slavik said:**
> notice the want vs. should. :) (I agree with the should). However, when a company wants a J2EE developer (or a graphics developer, or anything), they want someone who already has experience

Doesn't hold true so much when the language is only used to teach basic programming, rather than teaching how to use the language itself. 

I'm in final year of my software engineering degree, and as much as I can use Java, I don't understand how to use it well.

(I also hate Java :p)

Other languages however, that I haven't learnt through uni where I don't have the time constraints and am able to actually use the language for something a lot more complex than stupid examples.... I know much better...........

the morale of the story here being that they should be teaching purely concepts so the students learn how to understand what programming is. And it's up to them to learn the particularities of some language(s) of their choice in their own time.

:D

---

### Post by Cracauer on 2010-04-22
> **nvteighen said:**
> Hm... Static typing is somewhat weird in a high-level language like Java. I mean, I know it is because that way the compiler will be able to optimize code in a better way... but compilers and execution time optimizations aren't actually part of Computer Science (study of computable algorithms)... they're part of the implementational side of it (important as well, of course).


Uh, static typing will shift a lot of runtime errors to compiler time.

---

### Post by slavik on 2010-04-22
phrostbyte, them be fighting words around here ;)

delfick, who said uni know how to teach programming?

like has been already said (here or elsewhere) programming/engineering software solutions is not computer science.

computer science - develops theory and tools for practice
programming - implements theory with tools.

---

### Post by howlingmadhowie on 2010-04-23
> **Cracauer said:**
> Uh, static typing will shift a lot of runtime errors to compiler time.

well, it will shift a very small subset of errors which would very probably have quickly revealed themselves anyway to compile time. 

in other words, in the real world, explicit static typing is usually more trouble than it's worth, and according to all the studies i've seen on the subject (one in total), it results in programmers producing buggier code slower.

---

### Post by howlingmadhowie on 2010-04-23
> **delfick said:**
> Doesn't hold true so much when the language is only used to teach basic programming, rather than teaching how to use the language itself. 

I'm in final year of my software engineering degree, and as much as I can use Java, I don't understand how to use it well.

(I also hate Java :p)

Other languages however, that I haven't learnt through uni where I don't have the time constraints and am able to actually use the language for something a lot more complex than stupid examples.... I know much better...........

the morale of the story here being that they should be teaching purely concepts so the students learn how to understand what programming is. And it's up to them to learn the particularities of some language(s) of their choice in their own time.

:D

that seems fair enough.  

when it comes to java, a friend of mine is a sun certified java programmer and has worked a bit as a java programmer as well.  at some stage he sat down with a book on python and was amazed that he could program more complicated things with more ease in python than in java about an hour after he picked up the book.

programming in java is a huge chore.  just try creating a hash array with elements in it.  you end up writing huge amounts of boilerplate code.

---

### Post by LKjell on 2010-04-23
I believe that a readable style should be enforced or taught. I have seen students which learned python first and then start writing code in java which is so crappy that it is so hard to read.

However, styles are very personal it is like handwriting. It is up to you to make that other can read it. If the code you write is for your eyes only then do not care. Otherwise think of those who are going to read your code and make their life easier.

@delfick. To force a student to use a specific style you can either teach them at the beginning to use a readable style or demands that assignments should be written in them.

Now for java vs python. Why not just learn both?

---

### Post by Some Penguin on 2010-04-23
> **LKjell said:**
> I believe that a readable style should be enforced or taught. I have seen students which learned python first and then start writing code in java which is so crappy that it is so hard to read.

However, styles are very personal it is like handwriting. It is up to you to make that other can read it. If the code you write is for your eyes only then do not care. Otherwise think of those who are going to read your code and make their life easier.

Or even if it's for one's own use -- code written while in a drunken stupor or a state of exhaustion several years prior might be difficult to understand later on, heh.

*shrug*  Seems to me that having (1) collaborative projects (so students feel the pain of not being able to understand each others' code, if it's badly written -- and test them separately on the concepts, to make sure that each groks the entire bit), and (2) having students walk others through their code afterward would help people get in the habit of writing more comprehensible code.

---

### Post by nvteighen on 2010-04-23
> **Cracauer said:**
> Uh, static typing will shift a lot of runtime errors to compiler time.

Yes, but static typing also generates errors that can't ever occur in dynamic languages. e.g. type-casting errors which lead to *runtime* misbehaivor impossible for a compiler to detect.

---

### Post by delfick on 2010-04-23
> **slavik said:**
> delfick, who said uni know how to teach programming?


lol.

fair point :p

> **LKjell said:**
> @delfick. To force a student to use a specific style you can either teach them at the beginning to use a readable style or demands that assignments should be written in them.

essentially it's what we do.

Problem becomes they don't care.

They especially don't care about indentation and don't keep it up as they go along.

Forcing them to because the program won't run otherwise is a great way of getting them to indent code. (indentation is a bit of a pet peeve for me :p)

.........

---

### Post by Cracauer on 2010-04-23
> **nvteighen said:**
> Yes, but static typing also generates errors that can't ever occur in dynamic languages. e.g. type-casting errors which lead to *runtime* misbehaivor impossible for a compiler to detect.

Well, don't cast, in particular not incorrectly :)

In modern C++ there should be few need for plain casting things around and you also have RTTI for things you design that way.

> **howlingmadhowie said:**
> well, it will shift a very small subset of errors which would very probably have quickly revealed themselves anyway to compile time. 

in other words, in the real world, explicit static typing is usually more trouble than it's worth, and according to all the studies i've seen on the subject (one in total), it results in programmers producing buggier code slower.

This is not a universally accepted standpoint.

---

### Post by CptPicard on 2010-04-23
> **Cracauer said:**
> 
This is not a universally accepted standpoint.

May not be, but it just demonstrates that being religious about static typing doesn't really make much sense either. You should, as a Lisper, understand that :p

---

### Post by howlingmadhowie on 2010-04-23
> **Cracauer said:**
> Well, don't cast, in particular not incorrectly :)


isn't this rather like just saying "don't make mistakes, then you won't make any mistakes"?  There are moments where casting makes a lot of sense.  

In general type safety is about commenting your code so a compiler knows what it means. a good thing to do is to just name your variables in a way that makes sense. for example, if you don't call a number "mystring" you have already introduced an explicit type system and will probably automatically catch everything a compiler would catch.

---

### Post by LKjell on 2010-04-23
In the end whatever happens you need to test your code to make sure it is bug-free.

---

### Post by phrostbyte on 2010-04-23
Well I will qualify what I said before.

Python seems to have more functional programming constructs then Java. I think this alone makes it a better teaching language.

Python has some really good scientific computing libraries (numpy/scipy).

Python is simply easier to learn (subjective). You would think this might be a strike against Python, but in my opinion CS is not about learning languages but learning how to develop and analyze algorithms. The closer the language is to just purely describing an algorithm, the better. In some cases I think Python can even make a reasonable substitution for pseudo-code.

---

### Post by Penguin Guy on 2010-04-23
Java is a very common language, it works on most computers. On the other hand Python is more of a Linux thing.

---

### Post by wmcbrine on 2010-04-23
> **Penguin Guy said:**
> Java is a very common language, it works on most computers. On the other hand Python is more of a Linux thing.Completely wrong, and also irrelevant.

---

### Post by bunburya on 2010-04-23
Well I have no prior experience of computer programming and I am not in any kind of computer-related course in uni, but I am trying to learn some computer programming in my spare time. I use Python because my brother (who *is* a CS student/computer nerd) recommended it as a very easy-to-learn yet powerful language. And I think he was right, it's very simple and intuitive and the whitespace syntax is especially good for a noob who will make ten mistakes in every simple program and therefore needs to be able to read what he writes.
 
But I don't know if I'd like to learn Python first before moving onto a load of different languages. Whitespace syntax is one thing, but I hear that Python has a lot of ready-made features that other languages lack, like dictionaries and certain methods of lists. Similarly, Python is known for its large standard library which provides a programmer with tons of handy tools pre-made and ready to be used. If you learned all you know about computer languages in this context, I think you might find it hard to cope when you move onto languages with smaller standard libraries and more of an emphasis on implementing such features yourself. But that's just my guess.
 
FWIW my brother is now learning Java in uni and doesn't like it at all.

---

### Post by CptPicard on 2010-04-23
> **bunburya said:**
> If you learned all you know about computer languages in this context, I think you might find it hard to cope when you move onto languages with smaller standard libraries and more of an emphasis on implementing such features yourself. But that's just my guess.

No, that's a completely misguided take, IMO. What really, actually counts is the core language definition and what that enables. The standard library just follows from there. The languages that make you "cope" with lower-level features are already a subset of the higher-level languages -- that is, Python, although it allows for a higher-level approach that makes you consider ideas you otherwise wouldn't, will also enable you to program on the level of C, if you so choose.

---

### Post by Cracauer on 2010-04-23
Languages with insufficient features for program abstraction tend to have very bad libraries. Just look at any collection class for pre-template C++.

---

### Post by Cracauer on 2010-04-23
> **howlingmadhowie said:**
> isn't this rather like just saying "don't make mistakes, then you won't make any mistakes"?  There are moments where casting makes a lot of sense.  


Where does it? The only thing I can think of is interfacing to C code, namely but not exclusively system calls.

But a dynamically typed language like Python will also interface to the same C libraries, and will have the same opportunity to get the casts wrong.

The point is, in modern C++ you aren't forced to use plain casts in the first place. So you won't have to dance around the possible mistakes. I think it is ludicrous to say that C++ forces you to use plain unconditional casting often enough that you would get a runtime error rate even remotely comparable to runtime type errors in a dynamically typed language.

 > **howlingmadhowie said:**
> 
In general type safety is about commenting your code so a compiler knows what it means. a good thing to do is to just name your variables in a way that makes sense. for example, if you don't call a number "mystring" you have already introduced an explicit type system and will probably automatically catch everything a compiler would catch.

I don't think so.

If you throw in the element of const-correctness (as much const as possible), you get a large amount of pre-runtime diagnosis out of a modern C++ program that is just lacking in Python.  And don't get me started on what huge help constness is for multithreaded code.  Not that Python has threads that use multiple cores/CPUs in the first place.

---

### Post by Cracauer on 2010-04-23
> **CptPicard said:**
> May not be, but it just demonstrates that being religious about static typing doesn't really make much sense either. You should, as a Lisper, understand that :p

The Lisper, of course, can have both :)

```

(defun foo (bar baz)
  (declare (fixnum baz baz))
  (+ bar baz "meh"))

==>
:CL-USER Yes, Master? (compile-file "/home/cracauer/typecheck.lisp")
; compiling file "/mnt/safe/home/cracauer/typecheck.lisp" (written 23 APR 2010 07:55:45 PM):                                                                   ; file: /mnt/safe/home/cracauer/typecheck.lisp                                  
; in: DEFUN FOO                                                                 
;     (+ BAR BAZ "meh")                                                         
; ==>                                                                           
;   (+ (+ BAR BAZ) "meh")                                                       
;                                                                               
; caught WARNING:                                                               
;   Asserted type NUMBER conflicts with derived type                            
;   (VALUES (SIMPLE-ARRAY CHARACTER (3)) &OPTIONAL).                            
;   See also:                                                                   
;     The SBCL Manual, Node "Handling of Types"                                 
                                                                                
; compiling (CONCATENATE (QUOTE STRING) ...);                                   
                                            ; compilation unit finished         
                                            ;   caught 1 WARNING condition      
                                                                                
; /home/cracauer/typecheck.fasl written                                         





```

---

### Post by Reiger on 2010-04-23
Well the argument "types is just annotation code for a compiler to do a modicum of sanity checking" just asks for a compulsory round of Haskell or similar languages.

Here's one thing you may be surprised at: unwanted infinite loops can be detected at compile time in Haskell using only type safety rules. &#8220;Non exhaustive pattern&#8221;. Halting problems too: &#8220;Cannot construct infinite type&#8221;.

---

### Post by howlingmadhowie on 2010-04-24
> **Cracauer said:**
> Where does it? The only thing I can think of is interfacing to C code, namely but not exclusively system calls.

But a dynamically typed language like Python will also interface to the same C libraries, and will have the same opportunity to get the casts wrong.

The point is, in modern C++ you aren't forced to use plain casts in the first place. So you won't have to dance around the possible mistakes. I think it is ludicrous to say that C++ forces you to use plain unconditional casting often enough that you would get a runtime error rate even remotely comparable to runtime type errors in a dynamically typed language.



i'm not saying that explicit static typing is useless, what i am saying is that explicit static typing is to such a large extent mostly useless and requires so much overhead in terms of design and boilerplate code and jumping through hoops and thinking around corners, that in a given amount of time code written in an explicitly statically typed language will in general have more bugs, be less efficient and be less functional than code written in a dynamic language.

as for casting, the only statically typed language i've regularly used is java, and there you seem to spend half your time casting stuff in very complicated ways for no obvious reason.  that and the time spent waiting for compilation result in greatly reduced productivity and cargo-cult programming.

---

### Post by johnb820 on 2010-04-24
I personally feel that either Python or Ruby should be taught in CS, but I won't argue that working backwards into less programmer friendly languages might be an overwhelming leap and getting a head start on them has value.

It's a tough question to answer because even the oldest of languages still have use today but the direction in programming is to make the job of the programmer easier. Do you teach a course in an interpretive language like Python or do you go with a C based language? Not many would suggest CS students start out with C but Java is really just a more abstracted form of C with high use in industry. In one sense you have to learn not only the programming language but how it makes these abstractions.

But really any language is a good idea to start with. I also feel that a generalized programming language course which discusses the differences between them all and the improvements made over time should be taken alongside your first crash course in a specific language.

---

### Post by slavik on 2010-04-24
> **howlingmadhowie said:**
> i'm not saying that explicit static typing is useless, what i am saying is that explicit static typing is to such a large extent mostly useless and requires so much overhead in terms of design and boilerplate code and jumping through hoops and thinking around corners, that in a given amount of time code written in an explicitly statically typed language will in general have more bugs, be less efficient and be less functional than code written in a dynamic language.

as for casting, the only statically typed language i've regularly used is java, and there you seem to spend half your time casting stuff in very complicated ways for no obvious reason.  that and the time spent waiting for compilation result in greatly reduced productivity and cargo-cult programming.
What he said.

For example, in Perl6, you can define a variable to be a type, but it is not madatory. for example:

my int $something = 5;
$something = "Hello, World!";

the above would trigger an error.

my $something = 5;
$something = "Hello, World";

this will work fine.

static typing is useful when you want to give the compiler a hint that something will always be one single type which would allow it to optimize the variable storage (int vs a generic glob).

---

### Post by Cracauer on 2010-04-24
> **howlingmadhowie said:**
> i'm not saying that explicit static typing is useless, what i am saying is that explicit static typing is to such a large extent mostly useless and requires so much overhead in terms of design and boilerplate code and jumping through hoops and thinking around corners, that in a given amount of time code written in an explicitly statically typed language will in general have more bugs, be less efficient and be less functional than code written in a dynamic language.

as for casting, the only statically typed language i've regularly used is java, and there you seem to spend half your time casting stuff in very complicated ways for no obvious reason.  that and the time spent waiting for compilation result in greatly reduced productivity and cargo-cult programming.

Well, Java is a little clunky because of the way that it does types in collections. One of the reasons I ended up not being too enthusiastic about it.

I guess in the end we say the same thing.

---

### Post by LKjell on 2010-04-24
> **Cracauer said:**
> Well, Java is a little clunky because of the way that it does types in collections. One of the reasons I ended up not being too enthusiastic about it.

I guess in the end we say the same thing.

With or without generics?

---

### Post by Cracauer on 2010-04-24
> **LKjell said:**
> With or without generics?

I haven't used Java much since generics went in but I suppose they do better in this respect.

The point here is: all the libraries (and Java is about the libraries, no?) have been designed and implemented before generics came along. Which is why the delay in giving us what we wanted was such a bad thing.

---

### Post by CptPicard on 2010-04-24
> **Reiger said:**
> Well the argument "types is just annotation code for a compiler to do a modicum of sanity checking" just asks for a compulsory round of Haskell or similar languages.

But, being pure, Haskell also removes a lot of the needed annotation because a lot of stuff can be just simply inferred backwards from the instantiation of some piece of data. And where the compiler gets confused, you can tell it what it's supposed to be seeing.

---

### Post by LKjell on 2010-04-24
> **Cracauer said:**
> I haven't used Java much since generics went in but I suppose they do better in this respect.

The point here is: all the libraries (and Java is about the libraries, no?) have been designed and implemented before generics came along. Which is why the delay in giving us what we wanted was such a bad thing.

A lot have changed since then. IO is much simpler and generics makes your life easier though still some problems if you do not use with care.

---

### Post by rabid9797 on 2010-04-24
> **johnb820 said:**
> I personally feel that either Python or Ruby should be taught in CS, but I won't argue that working backwards into less programmer friendly languages might be an overwhelming leap and getting a head start on them has value.

....

But really any language is a good idea to start with. I also feel that a generalized programming language course which discusses the differences between them all and the improvements made over time should be taken alongside your first crash course in a specific language.

To the first point:
I don't see how learning an easier language first and then moving up to a more difficult language would be a harder leap than diving in to the difficult language to begin with. Sure, there is a learning curve with both, but doesn't a smaller jump seem easier?

And as for having generalized programming courses: That seems like an even harder idea to grasp. How would someone who has never programmed and isn't familiar with the terminology or methodology of computer languages is going to be able to grasp the differences between multiple languages and how they work.

---

### Post by CptPicard on 2010-04-24
> **rabid9797 said:**
> 
I don't see how learning an easier language first and then moving up to a more difficult language would be a harder leap than diving in to the difficult language to begin with. Sure, there is a learning curve with both, but doesn't a smaller jump seem easier?

What exactly constitutes the beneficial learning curve in learning programming has probably been the most heatedly discussed topic in the history of this forum :) You should dig up some old threads of "what programming language to start with" -- the high-level vs. low-level camps have historically been quite at odds with each other!

The core issue really is that the two camps do not really seem to agree on what constitutes difficulty or cognitively beneficial features that you want to be exposed to early on, and what sort of "difficulty" in a language is the beneficial kind.

I tend to be of the view that the good learning curve is the one where the language initially does not bog the learner down with language-specific detail that forces essentially a lot of "manual labor" to manage the language itself, and thus prevents the budding programmer from being exposed to the conceptual stuff that goes to programming "in any language". Some people feel that grinding with the low-level details, sometimes even suggesting that people should start with assembly, transfers useful information and ability to the higher-level languages, which they consider "easier" in the sense that they would be less demanding of the programmer in a bad way. Well, I never managed to understand that point... but, I always saw programming more in terms of describing a solution to a problem, instead of messing with hardware.

Which brings me to the next point...

> 
And as for having generalized programming courses: That seems like an even harder idea to grasp. How would someone who has never programmed and isn't familiar with the terminology or methodology of computer languages is going to be able to grasp the differences between multiple languages and how they work.

This is exactly why I am a fan of using a very generalized high-level programming language such as Scheme for teaching beginners. This way, the language itself is very simple to begin with -- there is almost no syntax for example -- and the learner can focus on identifying how to solve problems using a programming language instead of learning the language itself. Also, anything you actually learn from here is transferable to other programming languages after having learned their specifics...

The issue boils down to which languages teach more useful stuff to the user of the other kind of languages... personally I do not believe the ideas and "how you are made to do things" in low-level languages are quite as useful than the other way around; the high-level languages even conceptually completely contain the lower-level languages, while being much more comfortable to use.

---

### Post by johnb820 on 2010-04-24
So take for instance going from Java to C++. Conceptually you want to get a new programmer to understand parameters and how to use them as input but you never explain the difference between pass by value and pass by reference because everything in Java is a reference except for primitives. This is an instance where understanding that there are multiple ways for handling parameter passing might be helpful to the new programmer.

Also with this simple case, the concepts of templates, declaring members before defining them, const (as C++ uses it), or manual garbage collection are completely foreign to the Java programmer. I personally think it's tragic not to be at least familiar with general aspects of programming languages before mastering one and expecting to pick another one up easily.

As I said before, I'd suggest Python alongside a general programming languages course so you understand how Python differs compared to others.

---

### Post by CptPicard on 2010-04-24
> **johnb820 said:**
> This is an instance where understanding that there are multiple ways for handling parameter passing might be helpful to the new programmer.

Is it "helpful" or is it just a language-specific detail that keeps the new programmer from understanding what a function and a parameter is? I mean, in Lisp, all you have are labels that are bound to objects in some environment. A very clean, consistent model. In C++, you can pass values, pointers or references, and value-passing and returning requires in particular a lot of care with the management of the object internals.

I would much rather have the n00b be coding things like sorting algorithms and small data structures by this point, instead of working on the parameter passing details. Which will come in due time,  but anyway.

> 
Also with this simple case, the concepts of templates, declaring members before defining them, const (as C++ uses it), or manual garbage collection are completely foreign to the Java programmer. I personally think it's tragic not to be at least familiar with general aspects of programming languages before mastering one and expecting to pick another one up easily.

I'm not sure those are what I would call "general aspects". The garbage collection issue is the age-old issue too... it's a problem that is a lot of work that esp. the beginner will spend a lot of time and effort on, while being essentially a general resource-management problem that a programmer with a bit more competence will be able to solve more easily.

Then again, I do recognize that things like closures and higher-order functions may not be "general" either in the sense that they don't exist in a lot of languages... but having early exposure to them will "expand the mind" in terms of what can be done with them. Those ideas will influence even the code people write in lower-level languages (I certainly know it influences mine).

---

### Post by Ravenshade on 2010-04-24
Source: My Lecturer

> We use Java because it is an Industry Standard Programming Language. It is also widely considered an easy imperative language to learn unlike Scripting languages such as Ruby. 

Java also has many branch features, such as ANT, Groovy and support for Concurrent Programming. Unlike certain programming languages Java is also specifically designed to be able to support multiple architectures

I put it in a quote but I asked her the question and she gave me a lengthy phd recital so I've condensed. (PHD Thesus: V Bush, University of Gloucestershire, Java...(forgot the rest of the title) it's a good read download it, if you can find it)

In my personal opinion, as I've tried to learn C++ only to find myself on the receiving end of a lot of grief, I found that Java offered similar syntax yet it was more understandable and less things the developer has to decide on before compiling the program. Pointers are not fun. 

C itself is not actually an imperative language unlike Java, I believe it's functional... C# is imperative and so is C++. (I think I have them in the right order). 

I believe Python is a scripting language similar to Ruby or Groovy. (Or so I lead myself to believe. I haven't actually heard of Python being used in a substantial way)

---

### Post by CptPicard on 2010-04-24
> **Ravenshade said:**
> Pointers are not fun.

They are conceptually very similar to an array index -- actually, in the RAM sense, that is exactly what they are, an "index into memory" with associated type information.

If someone understands array indexing, they should understand pointers. The pointer is just a small -- in memory footprint wise -- value (like the integer used to index the array) that is used to refer to another value (the thing actually in the array).

> 
C itself is not actually an imperative language unlike Java, I believe it's functional...

No, no. "Functional" languages are something quite different. C is both imperative and "procedural". Just because C has functions, does not make it "functional".

---

### Post by Some Penguin on 2010-04-24
> **johnb820 said:**
> So take for instance going from Java to C++. Conceptually you want to get a new programmer to understand parameters and how to use them as input but you never explain the difference between pass by value and pass by reference because everything in Java is a reference except for primitives. This is an instance where understanding that there are multiple ways for handling parameter passing might be helpful to the new programmer.

*shrug* Java is purely call by value, but it's not in practice a problem, since it's trivial to create generic containers.

C++'s way of specifying reference parameters is a bit perverse, because it's obscure to somebody reading the calling code which ones are CBR vs CBV.   It's much more clear to use C-style PBV of explicit addressing or to create a generic container anyway -- these scream "watch out, this function call can have side-effects on the parameters".

foo(a);   
foo(&a);  
foo(\$a);

Two of these are pretty explicit about the fact that 'a' might change.  In Perl and C, it's clear that with foo(a), a will not change.  In C++, you have to go find the header for foo() to be sure, because it might be CBR and this little fact is only shown in the declaration/

Must say that I'm pretty impressed with how Perl 6 will handle argument passing.  The flexibility will be useful for such things as numerical methods with a gazillion parameters, many of them optional.  That's orthogonal, however.

> Also with this simple case, the concepts of templates, declaring members before defining them, const (as C++ uses it), or manual garbage collection are completely foreign to the Java programmer. I personally think it's tragic not to be at least familiar with general aspects of programming languages before mastering one and expecting to pick another one up easily.

Generics.  They're there.  You have to be a bit careful of type erasure and its consequences, but they're there.  Interfaces, final, *shrug* if you like, you can create your own global heap and object pools, but it's not really recommended.   You can experience the fun of using weak references if you really want to -- useful for transparent cache layers, for instance -- but most will never need 'em.

Now, getting type variables for primitives for usage with the reflection tools is fairly ugly... but reflection isn't normally heavily used by beginners, anyway.

> As I said before, I'd suggest Python alongside a general programming languages course so you understand how Python differs compared to others.

C and C++ is not that general, if you consider the amount of de facto hardware-based features (sizes for types, byte orderings, non-reproducibility of floating-point computation, et al), and the frequently platform-dependent functionality for what is pretty core in more recent languages (such as thread management,  network communications, and so forth). 

There's a reason why lots of C and C++ code uses explicit configuration scripts and lots of #ifdef and fairly complicated Makefiles.   It can be useful  to have an awareness of this sort of fun because a lot of engineering work can be helped with an understanding of architectural traits, but is not especially conducive to learning the science of the art.  

Novices have enough difficulty grasping basics such as the trade-offs between different hash table designs, determining the space and time requirements of a recursive function, or so forth without getting into really low-level details or worrying about how to write cross-platform code.

---

### Post by Ravenshade on 2010-04-24
by the way... another reason for using Java over Python....readability. Stealing from a previous example. 

```
l = [] 
``` This is an argument for fonts such as Arial to be phased out of programming. (I use a serif font such as New Times Roman in my coding to differentiate between letters)

Java... however

```
list i = ['values'] ; 
```

Python in this context is a useless coding language in my opinion, I at least want to know in plain english that I'm going to create a list and what it is for. While a lot of syntax is used, ' [ ; =, they give me boundaries, unlike in python, but this is personal preference, and I can see the advantage of not having to riddle your code with semi colons. Teachers out there should support this... reading your students code can always be made easier by english. (Pet hate of Haskell and Z-Notation)

----------------------

Back to the reply

Yeah, I get that, but...I thought that was assembly level code. Putting data into specific parts of memory that is. (I programmed Hello World using ARM, took me almost two weeks of just copying the damn code and making sure it was formatted correctly). 

I think my problem with pointers lies not in the concept but more in the syntax. R32 R32, FR2 ... (can't remember the actual code) was far easier to understand than how I came across pointers in C++ >.>

........

I was informed (and I got high marks on that paper, two years ago) that C was much more closely related to functional programming than it was imperative. Might be having a memory lapse. (Functional might not be the word I'm looking for)

---

### Post by CptPicard on 2010-04-24
> **Ravenshade said:**
> Teachers out there should support this... reading your students code can always be made easier by english. (Pet hate of Haskell and Z-Notation)

Not necessarily... programming is quite a specialized language-task, most programming languages that try to be natural-language-like fail.

> 
Yeah, I get that, but...I thought that was assembly level code. Putting data into specific parts of memory that is.

No, not really. On a 64bit machine the pointer is nothing but a 64bit integer that tells the memory location of the pointed-to thing. I find it a bit strange that a lot of learners struggle with pointers...

> 
I was informed (and I got high marks on that paper, two years ago) that C was much more closely related to functional programming than it was imperative.

Well that would be complete nonsense... I sure hope you are remembering it wrong, otherwise whoever graded the paper was not up to the task.

---

### Post by Ravenshade on 2010-04-24
meh, the lecturer who marked those lectures was promptly fired during the recession so who knows. I remember having sources to back it up... (and we're not allowed to use Wikipedia)

---

### Post by phrostbyte on 2010-04-24
> **Ravenshade said:**
> meh, the lecturer who marked those lectures was promptly fired during the recession so who knows. I remember having sources to back it up... (and we're not allowed to use Wikipedia)

When people talk about functional programming they mean functions in the mathematical sense. I am sure you remember in math a function which can output two different values for the same input is not a function at all. C does absolutely nothing to address this behavior. Functional languages tend to treat functions as a special type or pattern.

---

### Post by Cracauer on 2010-04-25
Lacking knowledge about what functional programmng is, actually, if it doesn't enforce pure OO programming, it must be a functional programming language. Now do your homework in Java and not in that Python thing that evil Linux people bound to their copyright-violating toy operating system to lock innocent students out of using Normal Computers(tm).

What disgusts me most about the above quotes about Java in CS is the capitalization of "Industry Standard Programming Language", as if that makes it something god-like.

---

### Post by Gatemaze on 2010-04-25
we had this discussion a few days ago with some colleagues... jave being a much more disciplined and strict language is better for teaching... from there onwards go and do what you want... it's like the way you drive when you learn how to frive and for your driving test and the way you drive for the rest of your life.

---

### Post by CptPicard on 2010-04-25
> **Gatemaze said:**
> we had this discussion a few days ago with some colleagues... jave being a much more disciplined and strict language is better for teaching... from there onwards go and do what you want... 

[Bondage and discipline]("http://c2.com/cgi-bin/wiki?BondageAndDisciplineLanguage"), huh ;)

> it's like the way you drive when you learn how to frive and for your driving test and the way you drive for the rest of your life.

I genuinely hope not. I want to steer clear of programmers who program the way they typically program for Java "for the rest of their lives"; I can't really imagine being boxed in to a certain kind of mental model for things more.

I'm not saying Java is not potentially a good starter language (one of many), but it's hardly particularly special in what kind of stuff it permanently infects you mind with...

---

### Post by LKjell on 2010-04-25
> **Gatemaze said:**
> we had this discussion a few days ago with some colleagues... jave being a much more disciplined and strict language is better for teaching... from there onwards go and do what you want... it's like the way you drive when you learn how to frive and for your driving test and the way you drive for the rest of your life.

I can assure you that how you learn to drive and how you drive for the rest of your life is two different ways of driving :)

And I guess it is the same with programming. You learn one thing but then you find another easy mode of doing stuff. There is two things you can do in programming. The first one is to abstract stuff. It will run slower but you can do fancy stuff with it. The other one is think and understand how the hardware works and use that. It will run faster but you have to write a lot of codes.

---

### Post by CptPicard on 2010-04-25
> **LKjell said:**
> The other one is think and understand how the hardware works and use that. It will run faster but you have to write a lot of codes.

And I would hazard claiming that if one is unable to abstract to begin with, the knowledge of the machine will not be enough when actually trying to make use of it. I mean, what is one going to actually *do* with just a small collection of operations on registers and RAM?

Some people would disagree, of course :p

---

### Post by LKjell on 2010-04-25
> **CptPicard said:**
> And I would hazard claiming that if one is unable to abstract to begin with, the knowledge of the machine will not be enough when actually trying to make use of it. I mean, what is one going to actually *do* with just a small collection of operations on registers and RAM?

Some people would disagree, of course :p

We do need to start somewhere. Either from the beginning or from the end. Actually there is a course at my university which is kind of special. It is split up. One way is that you start from the transistor level and build up to C language. And the other way is to start from C language and go down to transistor level. I might see to get some overview on who of these students get best grades.

---

### Post by CptPicard on 2010-04-25
> **LKjell said:**
> We do need to start somewhere. Either from the beginning or from the end.

IMO there is no beginning or the end. They're just Turing-complete descriptors of computable processes, all of them. They just have different formulations of the exactly same theoretical class of computable functions... but, the *implications* of this issue seems to be philosophically very divisive :)

---

### Post by wmcbrine on 2010-04-25
It would be interesting to do a study -- teach one class Java, and one class Python, and see what the students produced over time. I know how I'd expect it to turn out.

---

### Post by phrostbyte on 2010-04-26
> **wmcbrine said:**
> It would be interesting to do a study -- teach one class Java, and one class Python, and see what the students produced over time. I know how I'd expect it to turn out.

I think that depends more on the students then on the language. :)

---

### Post by wmcbrine on 2010-04-26
> **phrostbyte said:**
> I think that depends more on the students then on the language. :)No, in a proper study, you control for that. Get the two groups as identical as possible.

---

### Post by phrostbyte on 2010-04-26
> **wmcbrine said:**
> No, in a proper study, you control for that. Get the two groups as identical as possible.

It's very difficult to quantify competence. We have GPA, programming interviews, etc. etc. but I am not sure you will be able to truly control the competency of two groups.

And also how would you quantify the results? Some kind of judging panel?

It just doesn't seem very, "scientific", if you know what I mean. :)

---

### Post by howlingmadhowie on 2010-04-26
> **CptPicard said:**
> IMO there is no beginning or the end. They're just Turing-complete descriptors of computable processes, all of them. They just have different formulations of the exactly same theoretical class of computable functions... but, the *implications* of this issue seems to be philosophically very divisive :)

this is an interesting point the good cpt is making here. it is tempting to ask oneself the question "yes, but what is actually going on?" The physicist would answer "well, certain quantum states in transistors are being set to change their resistance to electrical currents". the engineer would probably say "certain bit patterns are being stored and modified in electrical components". the lay person would say "the computer is printing some information on the screen".  the philosopher might well interject, that the computer is actually only displaying a pattern and we are interpreting this pattern as containing information, while the mathematician would say "a mathematical function is being calculated."

five different answers to the same question.  which one you regard as being more correct depends upon your own point of view. 

just as the low-level programmer could say "you're cheating because you're using a language that supports feature X without having to program it yourself", the chip designer could answer "you're cheating because you're using a chip which supports feature X without building this capability yourself".  the low-level programmer fears that someone will use feature X without understanding how it (according to his point of view) "actually works", just as the chip designer could complain about someone using a certain op-code without understanding what this op-code "actually does".

---

### Post by CptPicard on 2010-04-26
> **howlingmadhowie said:**
> 
just as the low-level programmer could say "you're cheating because you're using a language that supports feature X without having to program it yourself"

The funny thing about them is that they probably do not quite understand how the high-level feature works, when and how it is relevant and useful conceptually, and couldn't implement it or may not even know what the relevant "emulation" of that concept on a lower level is.

The typical counter-argument is that  "but you're not managing your memory!" :)

And these are the folks who actually seem to strongly believe that the said memory management helps them in understanding those higher-level ideas...

The "how it actually works" is not as important a point as some people say... I can write a CPU emulator easily in Scheme, and then it "actually works" by running in Scheme. I'm not sure if this information is informative regarding the functioning of the CPU emulator itself.

---

### Post by slavik on 2010-04-26
All I will say about "managing memory" is that there is Java code with memory leaks.

Java code can also be optimized simply by using different data structures and accessing memory differently.

---

### Post by LKjell on 2010-04-26
> **slavik said:**
> All I will say about "managing memory" is that there is Java code with memory leaks.

Java code can also be optimized simply by using different data structures and accessing memory differently.

If you do not need something then let it point to null. In C you would just have to call free then point it to NULL so technically if you can handle C memory then Java way of doing it should not be a problem.

But problems can happen. If you have two classes with a pointer inside that points to each other then you need point one of them to null before losing your working pointer.

---

### Post by rabid9797 on 2010-04-26
> **wmcbrine said:**
> No, in a proper study, you control for that. Get the two groups as identical as possible.

Rather than try to control the group, why not try to control the rate of progress in learning the language?

Do a study where students are given the means to learn the langauge, which is written by the same instructor who tries to make both courses as evenly matched in terms of advancing difficulty, and then see how long it takes the students to learn and understand the material by giving them coding challenges.

If one language is easier/more natural conceptually than the other, the students in that course should progress faster than the students in the other.

---

