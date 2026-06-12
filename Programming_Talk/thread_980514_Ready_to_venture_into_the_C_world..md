---
title: "Ready to venture into the C world."
date: 2008-11-12
forum: Programming Talk
---

### Post by OutOfReach on 2008-11-12
I've learned Python in June/July(?) and been practicing ever since, writing small, somtimes useless, mini-programs (both CLI and GUI). And I consider myself intermediate. I have explored many of the standard modules, anyway:

I've just ordered a couple of C books from Amazon with the money I've been saving up and will be expecting them between the next 5-9 days. 
But I would like some feedback on C. Is it easy (compared with Python)?
Any specific (good) habits that I should get used to? Any bad habits that I should avoid? Any advice in general?

EDIT: Ooo, yes I almost forgot: Can you use Qt with C?

Thanks. :)

---

### Post by snova on 2008-11-12
Qt is a C++ library, so no, it cannot be used from C.

C is much more low-level than Python. You have to think more like a computer as a result, because there is much less to separate you from it.

---

### Post by Phenax on 2008-11-12
> **snova said:**
> Qt is a C++ library, so no, it cannot be used from C.

However, if I'm not mistaken, there are QT bindings for C.

---

### Post by jimi_hendrix on 2008-11-12
C is harder than python...and you need to program defensively and remember to free your pointers...however my programming path has gone:

C# -> Python-> C++ -> C

it wasnt that hard and i have yet to segfault my computer... (watch me blow the monitor tomorrow)

---

### Post by snova on 2008-11-12
No. There aren't.

Perhaps you're thinking of GTK+?

---

### Post by OutOfReach on 2008-11-12
Hmm, I see. No Qt bindings for C. Bummer. I'll stick with writing CLI with C for now and maybe learn GTK later (as I understand it's written in C).

So C is pretty hard? Well, I have about 3 C books I bought and this great community to turn to if I need any help. :)

More experiences/advice welcome. :)

---

### Post by jimi_hendrix on 2008-11-12
C is not really that hard for the concepts...but like any language it will take a long time to master

---

### Post by snova on 2008-11-12
> **jimi_hendrix said:**
> it wasnt that hard and i have yet to segfault my computer... (watch me blow the monitor tomorrow)

You must be incredibly lucky... I have done it countless times. But then, I like experimenting with weird things and ghastly compiler features... Although there's no way that accounts for all, or even most, of them.

---

### Post by psusi on 2008-11-12
Learning the language in theory is not hard.  The hard part is actually trying to use it.  C will let you shoot yourself in the foot in all kinds of interesting ways that you can't in higher level scripting type languages.

---

### Post by jimi_hendrix on 2008-11-12
> **psusi said:**
>   C will let you shoot yourself in the foo

that reminds me of a funny geek webpage i found...it had a bunch of computer related stuff (windows, linux, python, c, etc) and how you would shoot yourself in the foot with it...

and for the gui thing...you could always write the guts of the app in C and just call the functions from a python script gui

---

### Post by michaeljohn225 on 2008-11-12
I've learned Python in June/July(?) and been practicing ever since, writing small, somtimes useless, mini-programs (both CLI and GUI). And I consider myself intermediate. I have explored many of the standard modules, anyway:

[Packers And Movers]("http://www.packersandmover.com/packers-and-movers.html")
[Packers Movers]("http://www.packersandmover.com/packers-movers.html")

---

### Post by OutOfReach on 2008-11-12
> **jimi_hendrix said:**
> 
and for the gui thing...you could always write the guts of the app in C and just call the functions from a python script gui

Excellent idea! As I've heard, Python and C act nicely together.

Well, I have a feeling that I'll be shooting myself in the foot with C at times, but you learn from your mistakes, no?

---

### Post by jimi_hendrix on 2008-11-12
dont know...havnt shot myself yet...but i have killed my projects before...

---

### Post by tom66 on 2008-11-13
Well, C and C++ are quite similar. You can learn C, then C++ is very easy, only a few new concepts to learn.

---

### Post by ad_267 on 2008-11-13
[http://burks.bton.ac.uk/burks/language/shoot.htm](http://burks.bton.ac.uk/burks/language/shoot.htm)

I should probably add something constructive too. I'd say C is a lot simpler than C++, the two are quite different. C is very low level compared to Python and you have to understand pointers and what happens when a variable is passed to a function if it is passed by value or by reference. There isn't really a lot of stuff to learn in C though. I also find it hard to believe jimi_hendrix has never segfaulted!

---

### Post by CptPicard on 2008-11-13
The relative hardness of C vs some high level languages is an interesting question that has been discussed a lot here.

It really is a different kind of hardness. C is as a language really simple, just a limited set of basic control constructs plus functions (which aren't higher-order functions in the real sense) plus values plus pointers which also are values. The set of what you've got is not hard to grasp, but it can be hard to write stuff in terms of it because you really need to write so much from bottom up.

Plus, C lacks some of the really powerful language primitives such as lambdas that make higher-level languages possible. I know a lot of people here have even denied their validity as somehow clearly more expressive than just mere syntactic sugar, but, uh, they are wrong :)

Actually I wish I had not started my programming with languages like Pascal and C because after those it really requires a mindset shift to just get rid of the idea of pointers and call stack and what not. Those are technical issues.

Languages like Scheme on the other and minimize "in the other direction" -- not closer to the hardware but closer to a minimal set of abstractions you need in order to write programs. Just the other day I was writing some Scheme where I not only got rid of loops and variables but even the implicit "return place" of typical functions -- continuation passing style allows you to explicitly always state where the computation is to proceed next. Kind of like a functional-programming GOTO.. ;) But it is remarkable how close you can come to just simple function evaluation like you do in mathematics. All the rest are technical details. And when you get rid of as many technical requirements as possible, the minimum set of theoretical requirements can be enlightening about the very problem you are solving.

In addition I am in complete disagreement with the idea that learning C++ is just learning C and then adding a few concepts on top of it. Actually proper C++ code has lots of stuff in it that you do not do in C. This is perhaps one of the flaws of the language as I see it... it is surprisingly hard to "use it right" and if you try to use it just by adding classes to C, you are setting yourself up to all kinds of interesting issues.

---

### Post by pmasiar on 2008-11-13
> **CptPicard said:**
> C is as a language really simple,...

Plus, C lacks some of the really powerful language primitives 

Simplicity of C is based on lack of features. C is very simple to learn if you understand ASM and CPU architecture - C is "just" fancy macroprocessor for ASM is a sense. It lacks such basic (for Python programmer) concepts as string (you have 0-terminated arrays of chars). No self-expanding arrays: you need to allocate memory yourself, and make sure it fits. Dictionaries are major hassle, no syntax sugar to make it painless.

And of course every variable has a type and you need to track it all the time.

> Actually I wish I had not started my programming with languages like Pascal and C because after those it really requires a mindset shift to just get rid of the idea of pointers and call stack and what not. Those are technical issues.

Yes, but I attend course in data structures in Java, and I am often amused how hard is for kids with only Java experience to understand what is going on, because they do not grok pointers. They do not grok how computer memory works, all objects are some opaque magic entities, instead of convenient shortcuts to improve programmer's productivity. I believe that you can ignore low level architecture if you grok it. If you don't, you lack base to understand "cost" of high-level constructs, and is harder to write effective code.

Of course often you don't care about the "price" and Python or Scheme is fine. But if you do, Java  does not guide you as well as C does. It is like a dull knife: it is easier to cut yourself ;-)

Just my ramblings about my experience with students who learned Java as the only language... ;-)

---

### Post by nvteighen on 2008-11-13
It will be a good experience for you, having Python in your pocket. It will surely enlighten you on why there are so much discussions on high-level vs. low-level languages and also help you to have a well-formed opinion on the topic.

What I recommend you is to also learn the history behind C and its relation with UNIX development. It will help you understanding why the language is like it is. Also, don't care on GUI toolkits until you have mastered the Std. Library (hint: install manpages-dev package... it installs man pages for the C Std. Lib. functions!). Not that it is difficult, but in C, as you have almost nothing to build from, it's much more difficult to implement stuff, so you have to heavily rely on libraries and of course, the Standard. Otherwise, you'll have a hard time reinventing the wheel almost without tools and finally get easily frustrated.

Good luck! And ask us if you have any question.

---

### Post by OutOfReach on 2008-11-13
> **nvteighen said:**
> It will be a good experience for you, having Python in your pocket. It will surely enlighten you on why there are so much discussions on high-level vs. low-level languages and also help you to have a well-formed opinion on the topic.

What I recommend you is to also learn the history behind C and its relation with UNIX development. It will help you understanding why the language is like it is. Also, don't care on GUI toolkits until you have mastered the Std. Library (hint: install manpages-dev package... it installs man pages for the C Std. Lib. functions!). Not that it is difficult, but in C, as you have almost nothing to build from, it's much more difficult to implement stuff, so you have to heavily rely on libraries and of course, the Standard. Otherwise, you'll have a hard time reinventing the wheel almost without tools and finally get easily frustrated.

Good luck! And ask us if you have any question.

Yes I was planning on being all CLI while learning C.

I have always been intruiged with UNIX developemnt, I have no idea why, but since I am not going to be getting my books for a couple of days, maybe a week, I will research that and get familiar with that subject. :)

Finally, Thanks. :)

---

### Post by Kilon on 2008-11-14
I have studied C\C++ and Assembly which is a much more low level. Actually Assembly is as much low level as it can be. And surprise surprise I enjoyed the language quite a bit. When I was saying to people that I did not find assembly so difficult they looked at me like I was crazy. 

I think they issue here is to understand that the more low level you go  , the more things you will need to understand and learn. So it is not so much about complexity or difficulty as it is about quantity of information. I think things seem difficult when you do not yet understand what the hell your are doing. When you go low level you must be patient and study the smallest detail. If you cannot be patient then stick to a higher level language that makes you feel  comfortable. 

Of course you have to ask yourself whether you really need all these quantity of information . I have studied assembly for fun and for expanding my knowledge of things, never intended to use it cause I realized that a much higher  language called Delphi would fit my needs just perfect. You will draw your own conclusion by trying C++ by yourself. 


I can promise you that you will not waste anytime. C++ is not that hard but it may not fit your needs, yet it may expose you to knowledge that will seem very helpful later even if you decide to abandon the language

---

### Post by CptPicard on 2008-11-14
> **Kilon said:**
> When I was saying to people that I did not find assembly so difficult they looked at me like I was crazy.

You're actually correct. Assembly is not hard, it's just "technical". The instruction set is small and after that it's just manipulating register contents and shuffing stuff between them and the RAM.

> 
I think they issue here is to understand that the more low level you go  , the more things you will need to understand and learn.

The lower level you go, the more you're dealing with the computer, not the problem. My issue with asm especially if used as a learning tool is that you are very specifically learning to "run the computer" instead of approaching programming from the perspective of actually expressing an algorithm to solve some problem.

> 
 So it is not so much about complexity or difficulty as it is about quantity of information.

It's about the quality of information, which in asm is strongly bound to the inner workings of the hardware. You still need to relate that somehow to what you're actually doing.

As an aside, C++ is a whole different kind of beast here of course, that language is genuinely complex to use *as a language*...

> If you cannot be patient then stick to a higher level language that makes you feel  comfortable. 

Fighting words... HLL guys do not do what they do because they lack patience or whatever. It's not a cop-out, trust me, although in particular beginners seem to be so totally enamored by their newly found understanding of what lies under the hood. Unfortunately, in the long run the interesting stuff is not down there in the engine room IMO :)

---

### Post by samjh on 2008-11-14
> **CptPicard said:**
> ...beginners seem to be so totally enamored by their newly found understanding of what lies under the hood. Unfortunately, in the long run the interesting stuff is not down there in the engine room IMO :)That depends on goals and perspectives.

There are plenty of students who are NOT at the least bit interested in what happens under the hood, and vice versa.  I don't remember many classmates who were too excited about learning opcodes or trawling through MCU spec sheets.  Nor were there many classmates who displayed much enthusiasm over Z notation and formal specification of software either. ;)

---

### Post by CptPicard on 2008-11-14
> **samjh said:**
> 
There are plenty of students who are NOT at the least bit interested in what happens under the hood, and vice versa.

Well, to be fully "civilized" in the field you certainly need to know. It's just that after all it is not all that difficult really, and not awfully informative when it comes to computation in general. It is just a way of implementing things close to the hardware.

> Nor were there many classmates who displayed much enthusiasm over Z notation and formal specification of software either. ;)

Wow, reminds me of how much formally deriving algorithms with predicate logic sucked, regardless of my like of theory. That was a pretty hard class... :)

---

### Post by Kilon on 2008-11-14
> **CptPicard said:**
> You're actually correct. Assembly is not hard, it's just "technical". The instruction set is small and after that it's just manipulating register contents and shuffing stuff between them and the RAM.



The lower level you go, the more you're dealing with the computer, not the problem. My issue with asm especially if used as a learning tool is that you are very specifically learning to "run the computer" instead of approaching programming from the perspective of actually expressing an algorithm to solve some problem.



It's about the quality of information, which in asm is strongly bound to the inner workings of the hardware. You still need to relate that somehow to what you're actually doing.

As an aside, C++ is a whole different kind of beast here of course, that language is genuinely complex to use *as a language*...



Fighting words... HLL guys do not do what they do because they lack patience or whatever. It's not a cop-out, trust me, although in particular beginners seem to be so totally enamored by their newly found understanding of what lies under the hood. Unfortunately, in the long run the interesting stuff is not down there in the engine room IMO :)


As you can see from my post I did not dare to talk about quality of info, because quality is something subjective and depends on the needs of the programmer. Quantity on the other hand is something objective and easy to measure.

I think you tried to look under my statements and not my actually my statement. My post is what you is what you get. I never approached Assembly as a holy grail, I approached it from the side that there is no such thing as too much knowledge. I personally feel that people are easily impressed by low level stuff and speed and benchmarks and somehow ignore their real needs. 

But even if you spend time learning Assembly it will expose you to knowledge which at some point will be proven useful even if you never actually use the language. The same applies with C++ even though of course there is no comparison between Assembly and C++. 

Other than that there are no mandatory choices, a computer language does not define a programmer skill, their way he approaches it and the time he spent with it , defines his skill.   

Maybe that is why I was never a fan of any computer language.

---

### Post by CptPicard on 2008-11-14
> **Kilon said:**
> As you can see from my post I did not dare to talk about quality of info, because quality is something subjective and depends on the needs of the programmer. Quantity on the other hand is something objective and easy to measure.

I am not quite sure of that... mind you, I mean "quality" in terms of "qualitative differences" -- "different kinds of information", which I characterized quite well in my post I believe. These differences are very clear.

The "amount" is the harder thing to measure in my view... how do you do that? In bits of documentation? How much information someone gets from some new evidence in light of prior knowledge is, even information-theoretically, subjective on that prior knowledge -- and on whether you choose to measure stuff as informative in the first place, depending on whether your that learning serves your purpose. 

> I never approached Assembly as a holy grail, I approached it from the side that there is no such thing as too much knowledge.

I am not quite sure I claimed you did... but then again, when one is discussing preferences for learning and what one learns from where and why, "learning anything is good because it's knowledge" waters down the argument a bit too much for my taste :)

> I personally feel that people are easily impressed by low level stuff and speed and benchmarks and somehow ignore their real needs.

True. There is a certain willingness to just withdraw into being a "specialist" who is technically very competent in some perhaps technically difficult language, but I am not always sure that I am seeing big-picture appreciation of issues there...

> 
Other than that there are no mandatory choices, a computer language does not define a programmer skill, their way he approaches it and the time he spent with it , defines his skill.

Yes, a determined Real Programmer can write FORTRAN in any language :)

---

### Post by pmasiar on 2008-11-14
> **Kilon said:**
> Assembly which is a much more low level. Actually Assembly is as much low level as it can be. 

It is now, but years ago (when CPU was not single microprocessor but one or more PCBs: I mean **long** time ago ;-) ), CPU was programmable by [http://en.wikipedia.org/wiki/Microcode](http://en.wikipedia.org/wiki/Microcode) : so you can implement new instructions for CPU, and people did.

Arguments why microcode was abandoned in 80ties in that wikipedia article should be required reading for speed kiddies 8-)

---

### Post by Kilon on 2008-11-14
> I am not quite sure of that... mind you, I mean "quality" in terms of "qualitative differences" -- "different kinds of information", which I characterized quite well in my post I believe. These differences are very clear.

Quality as different kinds of information? Yes that makes sense, but As I said it depends on what you need from the language. For example some people do value OO highly some other find it a problem . The example of VB developers comes in mind where the OO was forced on them with the introduction of VB .NET , it made alot of people unhappy, some said that it destroyed the nature of the language. So Quality here can have two or more different meanings.  

> The "amount" is the harder thing to measure in my view... how do you do that? In bits of documentation? How much information someone gets from some new evidence in light of prior knowledge is, even information-theoretically, subjective on that prior knowledge -- and on whether you choose to measure stuff as informative in the first place, depending on whether your that learning serves your purpose. 

Amount is should we say the amount of commands a language has , or should we say the amount of documentation needed to describe how the language works and behaves , excluding techniques of course which something personal. I do not understand why you find it hard to measure quantity.

   
> I am not quite sure I claimed you did... 

Then I must apologize , I misunderstood you. 

> but then again, when one is discussing preferences for learning and what one learns from where and why, "learning anything is good because it's knowledge" waters down the argument a bit too much for my taste :)


Yes sure we should be selective about what we learn . We cannot spend the rest of our lives reading books for things that do not matter for us. Of course we cannot always know that something we learn will be helpful or not , now or in the future. When I learned Assembly and did some basic programming , I only did it for fun, I never expected to help me anywhere. But It did help to understand programming better. So in the end we cannot be certain . 


> True. There is a certain willingness to just withdraw into being a "specialist" who is technically very competent in some perhaps technically difficult language, but I am not always sure that I am seeing big-picture appreciation of issues there...
 
Agreed.


> Yes, a determined Real Programmer can write FORTRAN in any language :)


I do not know FOTRAN so I cannot comment this.

---

### Post by meson2439 on 2008-11-15
Fortran is fun and is no more harder than C, simpler I might say. However the use is limited to Math. I still miss the goto function. The new fortran standard has too much similarity with C in style.

---

