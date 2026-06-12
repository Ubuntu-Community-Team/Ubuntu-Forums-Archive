---
title: "starting out with C - for a dumb guy"
date: 2005-07-13
forum: Programming Talk
---

### Post by byen on 2005-07-13
Ok. I know this type of question was asked many times but I could not get a definitive answer. Please bear with me as I am really charged up and need some patient listening/answers.
Ok. After going through various threads Ive decided that the best way to get into programming would be by starting of with 'C'.  It covers all the basics and would help me get to JAVA (which is my current final destination point!) I have some books on C but i have no Idea about which compliers to use(/download) on ubuntu and how to run the program that i have typed for errors and output. So can anyone walk me through this.
thank you for your help and support.

---

### Post by byen on 2005-07-13
well..did a little digging and found anjuta and installed gcc as well.
So can some one tell me this. Anjuta is used as a text editor which also tells me if there is any error in the syntax while typing and gcc is used to check the output right? or is there anyway where i can check the program output in anjuta itself?
thank you.

---

### Post by zeroK on 2005-07-14
I have never really worked with Anjuta but if you just want to compile a small programm you've written, simply run gcc -Wall -o test test.c

It will produce the executable "test" from the source file "test.c". -Wall gives you more warnings :)

For complexer programs you should also start writing Makefiles. There are quite a few tutorials about how to write Makefiles :-) For example this one:
[http://www.eng.hawaii.edu/Tutor/Make/](http://www.eng.hawaii.edu/Tutor/Make/)

---

### Post by thumper on 2005-07-14
[QUOTE=byen]Ok. After going through various threads Ive decided that the best way to get into programming would be by starting of with 'C'.  [/QUOTE]
Not the easiest way to get into programming in my opinion, but each to their own.  I started with Pascal (but that was almost 20 years ago [oh my god is it that long...]), but these days I would suggest Python or Ruby (you may have got that from some of the other posts).
[QUOTE=byen]It covers all the basics and would help me get to JAVA (which is my current final destination point!)[/QUOTE]
Sorry but I really have to disagree with this.  C does not cover object orientation.  And really, if Java is your final destination point, why not learn that?  C won't really help that much with Java.  The only thing that they really have in common is using braces ({}) to mark code blocks, and similar operators.

[QUOTE=byen]I have some books on C but i have no Idea about which compliers to use(/download) on ubuntu and how to run the program that i have typed for errors and output. So can anyone walk me through this.
thank you for your help and support.[/QUOTE]
If you still really want to learn C then use something like Kate (KDE advanced editor) which has syntax hilighting and command line compilation.  When you are comfortable with that, then move on to hand crafted makefiles (you do want to do it the hard way first).

zeroK already gave you the command line for compiling a single C file.  gcc is the package that you want to look for, and gmake (gnu make) once you are ready to move onto makefiles.

Good luck with C  :wink:

---

### Post by zeroK on 2005-07-14
Stupid question, but why don't you want to start with C# or Java and _then_ work your way down to low-level languages C?

---

### Post by m87 on 2005-07-14
I absolutely DON'T agree with going to low level from high level.

C is a good point from where to start, because it's a very powerful language indeed and  it helps you understand lots of stuff because not being garbage-collected you have to malloc() and free() everything, and there are neither classes nor objects.

THEN you go a bit higher and understand what C lacks and why it's going to be replaced (it won't happen though, unless the Linux kernel or an important platform loke GNOME keeps on supporting C). In fact I am currently programming in C# (although I have never quit C).

I think that IDE's are cool. But they may be some sort of bad habit, unless you get addicted to the syntax/functions and you are actually learning something :)

Anyway
[QUOTE=byen]It covers all the basics and would help me get to JAVA (which is my current final destination point!)[/QUOTE
I agree with thumper. I started with C because I wanted to learn C. You shouldn't start learning a language that you won't use. If you want to use java you may learn java, I just suggest C because, OOP or not, it's still the most used, and when using Linux, if you want to debug something, it's undoubtly the best choice, IMHO.

btw, C# is good as well :)

---

### Post by thumper on 2005-07-14
[QUOTE=m87]I absolutely DON'T agree with going to low level from high level.[/QUOTE]
You sure you got this the right way around?

[QUOTE=m87]C is a good point from where to start, because it's a very powerful language indeed and  it helps you understand lots of stuff because not being garbage-collected you have to malloc() and free() everything, and there are neither classes nor objects.[/QUOTE]
I agree that it is often good to get an understanding of memory management in the same way that it is good to get an understanding of basic data structures.

But, when just starting out programming you often want to see results quickly, and you have to write a large amount of C to do reasonably simple things.  For example how much code do you have to do to to create a set of numbers from a file that contains an integer on each line?

```
x = set([int(x[:-1]) for x in open('file.txt').readlines()])
```
A completely convoluted example in python, but how much C do you need?

Don't get me wrong, I think that new programmers should get an understanding of what things are being done under the covers, but should they learn it first?  I dunno.

---

### Post by m87 on 2005-07-14
I didnt say that it was the right way for everyone... I did like that and I did indeed learn C at first, and I believe that was the right way for me :)

By the way maybe you're right, python has a good approach to programming, and C would surely be on the way to oblivion if it wasn't used so much.

The real problem is that we will need C until computers will embed some VM and we'll have kernels built on top of JAVA or Mono or whatever, for our desktop systems. Until then, learning C will be somehow useful.

Anyway, if anybody's unsure from where to start, Python and C# are good choices, they're going fine these days.

---

### Post by LordHunter317 on 2005-07-14
Learning C as a pathway to learning other languages is simply stupid.

Actually, I have harsher words, but they'd probably get me in trouble.

If you want to learn Java, just learn Java.  The only transfer you'll get from learning C first is syntax.  Really.  This is something you where you need to trust those more experienced than you in this.  

Don't learn C to learn any other language.  You'll just get yourself in trouble.

---

### Post by m87 on 2005-07-14
[QUOTE=LordHunter317]Don't learn C to learn any other language.  You'll just get yourself in trouble.[/QUOTE]

There is no language to be learned to be able to learn others.
This sounds more like a flame against C programmers...

---

### Post by nonphasis on 2005-07-14
[QUOTE=m87]The real problem is that we will need C until computers will embed some VM and we'll have kernels built on top of JAVA or Mono or whatever, for our desktop systems. Until then, learning C will be somehow useful.[/quote]
Yes, for those who plan to do kernel or embedded development. The chances of that actually happening are very slim for programmers starting to learn programming today. C++ is more widely used, but for that learning C helps very little.

---

### Post by LordHunter317 on 2005-07-14
[QUOTE=m87]There is no language to be learned to be able to learn others.[/quote]That's not strictly true.  Learning some of the odd-off functional languages is much harder if you don't have a strong functional background, which is eaiser to accomplish in a more "mainstream" functional language like Scheme first.

> This sounds more like a flame against C programmers...No, seeing as I am one, and have been one professional in the past.

It's a notion against the two ideas that: "C is a good language to start learning programming in."  That's not really true, for a multitude of reasons.  I could go on about this, but I won't.  Suffice to say, the fact it's not commonly taught as a first language anymore should be reasonable and sufficent evidence.

The other is the idea. "You should learn C first before learning C++ or C#, or Java".  That's just not true.  The only similarity between them is syntax.   Best practices in one language are poor practices in the other.  And syntax is probably the eaisest thing to learn and teach, so why learn a different language than what you want to know if that's all you're going to gain?  It just doesn't make sense.  The concepts and correct ways of doing thigns in C won't carry over at all, so it makes even less sense.

Learning C first doesn't make you a better programmer if you want to be a Java programmer.  It's silly to think it does.

---

### Post by thumper on 2005-07-14
Let me play devil's advocate a little.  Firstly I think I have made my position quite clear above.

Implementing data structures and algorithms in C does give you a better appreciation for what other higher level languages give it for free.  I wouldn't want to write anything in C these days if given the choice.

My preferences are for C++ and python.  

But I'll reiterate again, and what LordHunter317 and I have said, if you want to program in Java, learn Java not C.

---

### Post by LordHunter317 on 2005-07-14
[QUOTE=thumper]Implementing data structures and algorithms in C does give you a better appreciation for what other higher level languages give it for free.[/quote]What C++ does perhaps.  Given the other two C children (Java and C#), I don't generally want their data structures.

That's an aside though.

---

### Post by byen on 2005-07-14
ok. First of all thank you for all the replies , I got gcc running and complied my first program ;-). As to why I rounded off on C? here is what i understand:
First of all...I am really inclined towards programming and want to eventually get into it as deep as possible and after looking around( which i did..a lot) it seemed to me that C is the most  basic/powerful language that seemed to cover most of the programming bases and I figured I better learn the ABC's of programming (with C) before I  leap into this sea called JAVA and probably other programming languages too. I know many people would disagree with me and say that If java is what I want then JAva is what i should learn..and yes, i do know that C hardly covers all the bases for java ..esp.(OOP) but I guess my belief that " it is better to learn to ride a bicycle before I ride a bike" has got me to this point...  any takers?

---

### Post by thumper on 2005-07-14
[QUOTE=LordHunter317]What C++ does perhaps.  Given the other two C children (Java and C#), I don't generally want their data structures.

That's an aside though.[/QUOTE]
Can't talk for C# as I have never done any, but Java, are you trying to tell me that you don't use the containers in java.util?  No Vector, HashMap, TreeSet et al?

---

### Post by thumper on 2005-07-14
[QUOTE=byen]I guess my belief that " it is better to learn to ride a bicycle before I ride a bike" has got me to this point...  any takers?[/QUOTE]
But is it better to learn to ride a bike before learning to drive an 18 wheeler truck (which some might argue that Java is)?

---

### Post by byen on 2005-07-14
[QUOTE=thumper]But is it better to learn to ride a bike before learning to drive an 18 wheeler truck (which some might argue that Java is)?[/QUOTE]
 so.. you mean..someone can get proficient in JAVA without actually knowing the nuts and bolts of programming? 
PS- please understand that I am in noway negating you or disagreeing with you... I asked so many people including the professor of the Univ and this is pretty much what came out and the JAVA- name factor got me thinking that I need to cover some bases be4 i take the leap.

---

### Post by LordHunter317 on 2005-07-14
[QUOTE=byen] it seemed to me that C is the most  basic/powerful language that seemed to cover most of the programming bases[/quote]No, and no.  

> and I figured I better learn the ABC's of programming (with C) before I  leap into this sea called JAVA and probably other programming languages too.And we're telling you that you're wrong.

If you really want to learn about programming, I recommend you start with the book *Structure and Interpretation of Computer Programs*.  Google for it, and you can get the complete text online.

After that, you need decide whether you want to go more of a CS-oriented route (the thereotical side) or a software-engineering route (the practical side).

> but I guess my belief that " it is better to learn to ride a bicycle before I ride a bike" has got me to this point...  any takers?Yes, but would you learn to ride a bike before driving a car?  That's a much closer approximation to what you're doing.

>  so.. you mean..someone can get proficient in JAVA without actually knowing the nuts and bolts of programming?Yes, there are hundreds of books about Java for people who have never programmed before.  This isn't a recommendation, but you can get *Thinking in Java* online for free.

[quote=thumper]Can't talk for C# as I have never done any, but Java, are you trying to tell me that you don't use the containers in java.util? No Vector, HashMap, TreeSet et al?[/quote]Oh I use them, but what I'm saying is that the Collections API java provides is crap compared to C++'s STL.  C#'s is no better, as it's a copy from Java.

---

### Post by byen on 2005-07-14
[QUOTE=Everyone]Not the easiest way to get into programming in my opinion

Sorry but I really have to disagree with this. C does not cover object orientation. 

You shouldn't start learning a language that you won't use. If you want to use java you may learn java

C does give you a better appreciation for what other higher level languages give it for free. I wouldn't want to write anything in C these days if given the choice.
And we're telling you that you're wrong.


Learning C as a pathway to learning other languages is simply stupid.

AND FINALLY!!!
[COLOR=Blue]Actually, I have harsher words, but they'd probably get me in trouble[/COLOR].[/QUOTE]

well... so many people cant be wrong! and getting it from someone who has been a professional (U) I dont see any reason to think otherwise. I will try and see if anyone has asked questions about java compilers and Qs abt running java and try to get started.  I really appretiate the time taken...imagine spending hours and hours learning C and finding this out after....  thank you.

---

### Post by thumper on 2005-07-14
[QUOTE=byen]I asked so many people including the professor of the Univ[/QUOTE]
Not sure if you university is anything like mine was, but many of the professors were pure academics.  Great with all the theory, but not too good with real world practice.

Unfortunately I learnt Java after C and C++ so I can't really recommend any books to learn from.  Go with LordHunter317's suggestion.

[QUOTE=LordHunter317]Oh I use them, but what I'm saying is that the Collections API java provides is crap compared to C++'s STL.  C#'s is no better, as it's a copy from Java.[/QUOTE]
I do have to agree with this.  Mostly though I think that the usability of the C++ standard library containers is better due to the operator overloading which gives a more consistant feel with the built in types.  Java has to provide methods which makes the code verbose.

---

### Post by LordHunter317 on 2005-07-14
Well, operator overloading is one thing ,but it's not the biggest thing.

The collections API is simply designed wrong.  Consider this.  ArrayList is the intended analouge to a C++ std::vector.  It's meant to simulate a dynamically growing array.

Yet, it's implementation of the interface List, and of AbstractList.  AbstractList contains methods to implement like [add(int, Object)](http://java.sun.com/j2se/1.4.2/docs/api/java/util/AbstractList.html#add(int,%20java.lang.Object)) which adds an item at a specific index and shifts everything down.  Such an operation doesn't make any sense, **especially on an unordered array**.  If my array is unordered, then I can just insert at the end, which is O(1) instead of O(N).  If my data is ordered and I need to be able to insert/remove in the middle, then a vector or an ArrayList is a poor choice anyway.

Even better is the fact that it's an optional operation, and could throw MethodNotSupportedException at you.  The whole Collections API violates OOP in a pretty fundamentally terrible way.

So it's not just pure usuablity.  The API is simply designed wrong.

---

### Post by thumper on 2005-07-14
[QUOTE=LordHunter317]Well, operator overloading is one thing ,but it's not the biggest thing.

The collections API is simply designed wrong.  Consider this.  ArrayList is the intended analouge to a C++ std::vector.  It's meant to simulate a dynamically growing array.

Yet, it's implementation of the interface List, and of AbstractList.  AbstractList contains methods to implement like [add(int, Object)](http://java.sun.com/j2se/1.4.2/docs/api/java/util/AbstractList.html#add(int,%20java.lang.Object)) which adds an item at a specific index and shifts everything down.  Such an operation doesn't make any sense, **especially on an unordered list**.  If my list is unordered, then I can just insert at the end, which is O(1) instead of O(N).  If my list is ordered, then a vector or an ArrayList is a poor choice anyway.

Even better is the fact that it's an optional operation, and could throw MethodNotSupportedException at you.  The whole Collections API violates OOP in a pretty fundamentally terrible way.

So it's not just pure usuablity.  The API is simply designed wrong.[/QUOTE]
Having a method to insert into the middle of a vector is not "wrong", just not O(1).  The std::vector allows you to do this as well.

Unfortunately just having good containers such as the ones in the standard library doesn't mean that people write good code.  This comes back to having the understanding about data structures and algorithms and knowing which one to choose in which circumstances.  Unfortunately much of this knowledge comes from experience and not from classroom style learning.

I also agree with you about the Java collections trying to use inheritance where generics are much more aligned to the design process.

For those of you who don't necessarily know the difference, generics imply some form of usage so you might have several classes that could be used interchangably by having the same interface without necessarily deriving from a common base class.  If you are really interested you should check out the "concepts" for the new C++ standard (C++0X).

---

### Post by GeirG on 2005-07-14
I have only been doing a little dabbeling in C, Perl and Tcl, so I'm hardly qualified to argue with people with 20 years of professional history. However, one arument/question I would say is missing from this discussion is the What/Why?

What field of sw development are you heading for?
Why are you aiming for Java?

The questions are really to two different takes on the same issue.
One can probably argue to the end of time about what language is "best". My little experience and what I've got from general discussions/books/articles tells me most languages has their benefits... and drawbacks.

The one thing I guess all languages give you, is an general understanding of programming concepts (variables, datastructures, algorithms, etc.). 
Then the different choices might give you advantages depending on what kind of applications you are going to create, or what environment you are working in.

As an example; I work in a company making equipment for telecom operators (optical transport, SDH(the european version of Sonet), Ethernet bridging, etc).
I'm sure some of the guys know C++, but I don't think anybody uses it.
The embedded sw is written in C. The management applications are Java based (come to think of it I don't really know what is used for the server side, might as well be C++ in there), and I use some Tcl and Perl for automating tests and parsing debug output.
My point (in case it was a bit unclear) is; the different parts of the total product solution are pretty much using different languages due to their nature.

My advice would be to get an idea about what would be a cool project, and then find out what tools would be best used to carry it out.
Of course, as you had your sight set for Java, you might already have done that.

Besides, you can only learn so much from reading a book (unless you read a very large amount of books, that is). To really learn how to code, you need to code, code, code. So get yourself a pet project, decide on a suitable language for the job, and learn as you go (you probably need to read a few chapters first though).

On closing, I don't think C is a bad choice given its power and possibilities, and that it gives you a lot of insight on memory stuff and such, but again it depends on what you are going to make. 
And as I mentioned in the beginning of the post; compared to most programmers I'm kind of a newbie, so what do I know?

Good luck, and happy coding!

---

### Post by thumper on 2005-07-14
[QUOTE=GeirG]I have only been doing a little dabbeling in C, Perl and Tcl, so I'm hardly qualified to argue with people with 20 years of professional history. [/QUOTE]
Only 10 years of professional history, 20 years of programming history  :) 

I do agree with you that each language has its pro's and con's, was really just saying that in this day and age learning C first is not a prerequisite to being a good programmer.

---

### Post by jerome bettis on 2005-07-14
[QUOTE=byen]so.. you mean..someone can get proficient in JAVA without actually knowing the nuts and bolts of programming? [/QUOTE]

yes absolutely.  java is pretty easy to pick up on.  you'll have to learn the nuts and bolts of programming in java, instead of learing them in C, which will be much easier.  IMO c is a terrible language in general anymore.  

learning a language like C just to learn how to program is dumb because a) you're not going to use it for your project,  b) a lot of things you'll need to know in java don't exist in C, c) a lot of things you'll learn in C don't exist in java  d) C is a huge pain in the ass to program in all around,  however m\aking the switch from c to java will be like removing a 10000 lb weight off your back.  why carry the weight at all in the first place if you don't have to?  just start with java, it's well documented, you'll enjoy using the standard library instead of writing that stuff yourself (in a way this is counter productive if you don't know how things work, stacks queues etc) 

about 5 weeks ago i fell back in love with c++ for about 2 weeks.  then i discovered python and i'll never ever use c or c++ unless i absolutely have to.  programming is difficult, try to make it as easy as possible on yourself.  learning java will be pretty straightforward, then learning C will be much simpler versus starting with C (very difficult) then making java very easy.

but the bottom line is if you can program well in any language, you can program just as well in all the rest with some practice.

---

### Post by m87 on 2005-07-14
[QUOTE=LordHunter317]Oh I use them, but what I'm saying is that the Collections API java provides is crap compared to C++'s STL.  C#'s is no better, as it's a copy from Java.[/QUOTE]

They're quite comfortable to use... I don't actually know how they are built because I rarely look at Mono sources (this is somehow good when looking at interpreted languages :) ), but they're more friendly than C++'s STL, as the whole C# thingy is made to be 'easier'. They are a great invention... should have been part of a "new" C standard, as the actual C implementation of lists and trees is the void :)

Anyway, there's no critical utility for Mono by now.. I would like to see it in action as an environment like J2ME is for java. It will be fun.

---

### Post by the_it on 2005-07-15
Not to play devil's advocate or anything like that, but I started with C on the right foot and it wasn't as hellish as some people seem to be suggesting.  It certainly gives me a greater appreciation for the more high level programming languages in use today.

Don't take me as a hardcore C person though.  Poorly done, C code looks like a mess and noone wants to read a mess.  But without my C background I simply would be lost in C++.  Without understanding the simple concept of linear memory space, heaps and stacks, bounds checking, and how everything is all interconnected in memory, I would be a poorer programmer, and my training in C helped my realize that.

C isn't the only way to do it.  You could learn it from assembly, you could learn it from C++, you could learn it from just theory.  But C is the closest, most natural approach that comes to mind when learning it in practice (no way ordinary folk would do assembly).  In Java and Lisp, and other VM based (or VM extensive) languages, a lot of this stuff is isolated from you by the system.  Well Pascal comes to mind, but C is more contemporary.  I'd at least guess that there's a bit of truth when the professor suggested C, coz he'd get two birds in one stone.

But you guys are also right.  Learning C is not essential to learning other languages.  However, I think it might be an oversight to think that learning C does not help you to learn other languages, or even to be a better programmer, in the same way that learning Java does not help you to learn OOP, or to write for readability.

I'd just like to stress that a C background may be helpful, if you've got the time, and at least be able to cover abstract data structures and streams.  But it is not essential.

---

### Post by LordHunter317 on 2005-07-15
[QUOTE=m87]They're quite comfortable to use...[/quote]Not really, if you care about your performance from your data structures, and care about having well-defined semantics for them.

Java and C# both make ensuring those semantics rather difficult, all the time.

> but they're more friendly than C++'s STL, as the whole C# thingy is made to be 'easier'.Yes, but friendly isn't the only consideration at hand here.

Sure, a lot of people don't care, but a lot of programmers need data structures that have defined behavior in all cases.  C# and Java's collections API make providing that far more difficult than necessary.

> I would like to see it in action as an environment like J2ME is for java. It will be fun.J2ME isn't used on PCs, so I don't follow.

[quote=the_it] But without my C background I simply would be lost in C++. [/quote]Absolute nonsense.  A proper C++ book would teach you the language without having to learn anything about C.  And it means you won't have bad habits in C++ because of things that are necessary evils in C.

> Without understanding the simple concept of linear memory space, heaps and stacks, bounds checking, and how everything is all interconnected in memory, I would be a poorer programmer, and my training in C helped my realize that.But if you're using a language where you don't have that kind of control over memory management, you really haven't gained anything.  You just think you have.

> But C is the closest, most natural approach that comes to mind when learning it in practice (no way ordinary folk would do assembly).I'm sure colleges worlds over would love to hear that.  Very few schools teach C as an introductory language anymore, if they teach it at all.  Really.  It's not a teaching language, it was never meant to be.

> However, I think it might be an oversight to think that learning C does not help you to learn other languages,But it doesn't.  The right way to do anything is C is almost always the wrong way to do it in every other language.  The carryover is pretty low.

And the things that aren't that way are pretty much universal to every language, like data structures.  Meaning you can learn them in any language.

---

### Post by m87 on 2005-07-15
[QUOTE=LordHunter317]J2ME isn't used on PCs, so I don't follow.[/QUOTE]
I didn't talk about PC's. I just considered the idea of having a Mono interpreter for embedded devices.

---

### Post by LordHunter317 on 2005-07-15
Well, MS provides the .NET Compact framework if you really want to do mobile/portable device .NET programming.

It's unlikely that a Mono implementation of the same framework would see extremely widespread use as there's not that many devices worth running it on.

---

### Post by poster_nutbag on 2005-07-15
Going back to the original question:

C is *not* a good choice to start learning programming with. Python would be better, IMHO.

C *is* a good language if you want to learn how computers work. Machine code would be even better for this but impractical for day to day use.

---

### Post by magomago on 2005-07-21
[QUOTE=poster_nutbag]Going back to the original question:

C is *not* a good choice to start learning programming with. Python would be better, IMHO.

C *is* a good language if you want to learn how computers work. Machine code would be even better for this but impractical for day to day use.[/QUOTE]
 
Just looking through these thread and I'll say bingo!

I tired to learn C on my own a few years ago and I couldn't hack it, but then agian perhaps it was because the book I was using tied me down to Visual Studio and I didn't have that
So I just messed with Qbasic a lot, and SOME visual basic

But I took a quarter of Python in college and I got acquainted with a lot of things

now i'm going back to learn C, and the hardest part honestly seems to be picking up on syntax.  looking back, python is VERY easy and straight foreward.   I remember before taking the class my ICS friend told me ,"Don't worry~ Python is like reading English Essays"

If you are learning your first language, DEFINTELY go python.  Especially considering how it is useful for Linux as well and has a large following ;)  After that you will find whatever you program in to be considerably easier, as the first language is always the hardest.

Now my only problem is people are telling me to skip C and save myself the headache and just do C++ ;)

---

