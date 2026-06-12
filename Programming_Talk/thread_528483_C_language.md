---
title: "C language"
date: 2007-08-17
forum: Programming Talk
---

### Post by bribaetz on 2007-08-17
my question is why is such a powerful language so much less organized and beautiful than python. (this is just a opinion)
i know that C has far far more capabilities but i think i may just learn assembly. any suggestions on what i should?, do im still continuing to learn CPP pascal and python. so really does C++ have the same abilities as C as fas as an os.

---

### Post by Wybiral on 2007-08-17
> my question is why is such a powerful language so much less organized and beautiful than python. (this is just a opinion)

I don't think it's less organized or beautiful, I think it just takes more consideration when designing things in it (it doesn't have all the jazz that Python has).

> i know that C has far far more capabilities but i think i may just learn assembly. any suggestions on what i should?

Assembly is good, but impractical for modern software development. Great for a learning experience though. But you will still want to learn some C before diving into assembly.

> im still continuing to learn CPP pascal and python.

You should really only learn one language at a time... Just don't stop after that one language. But don't overwhelm yourself learning 3-4 languages... Just learn one. (but much easier to develop and maintain)

> so really does C++ have the same abilities as C as fas as an os.[/QUOTE]

Yes and no... It's possible, but the machine code won't be as small and standard C++ practices aren't as low level as C often resulting in more overhead. Not to mention issues involving integrating the STL in your OS.

If you're going to write an OS, don't reinvent the wheel, use C and assembly. But also... Don't reinvent the wheel... Use standard OS. Maybe develop off of one of the smaller Linux distributions.

---

### Post by pmasiar on 2007-08-17
> **bribaetz said:**
> my question is why is such a powerful language so much less organized and beautiful than python. .

Thats easy: because Python has garbage collection :-)

Ah I forgot you are not done reading yet :-) - it went hight above your head

---

### Post by bribaetz on 2007-08-17
> **pmasiar said:**
> Thats easy: because Python has garbage collection :-)

Ah I forgot you are not done reading yet :-) - it went hight above your head

pmasiar im done listening to you your fallowing all of my threads making fun of me hey mind explaining what you wanted to tell me.

---

### Post by slavik on 2007-08-18
1. C was written in the 70s (if not 60s)

2. Python was written/invented only fairly recently

3. Some things that are a nobrainer in Python (OO, garbage collection, etc.) were either non-existant in 70s or were too slow (Smalltalk)

4. C was designed to write Unix for the PDP-7 minicomputer which had very little memory, even for computers back in the day.

---

### Post by samjh on 2007-08-18
Bribaetz, you really should just settle down and learn a language.  You've posted quite a few threads asking about this language and that, and not really getting anywhere.  I thought you picked Pascal (a good language, mind you), so why not sit down and learn that?

---

### Post by xtacocorex on 2007-08-18
Instead of learning a language, learn about programming methodology and logic; that will help in understanding what any language syntax is doing. 

No language will look as beautiful as FORTRAN in all caps.

---

### Post by pmasiar on 2007-08-18
> **bribaetz said:**
> pmasiar im done listening to you your fallowing all of my threads making fun of me 

[fallowing ](http://dictionary.reference.com/search?q=fallowing&x=0&y=0): 
# Plowed but left unseeded during a growing season: fallow farmland.
# Characterized by inactivity: a fallow gold market

See, you can find all kinds of useful information on internet, even if English is not my first language. So I learned new word today. :-)

> hey mind explaining what you wanted to tell me.

You don't understand answers people spend valuable time writing, so you are wasting their time.

I still believe you can change (otherwise I would not write this and just ignored you - it is **much** faster), but asking questions does not do you any good if you don't understand answers.

Learn a language, any language. Look up words you don't know in wikipedia. 

Trust me, attitude is **not** a valid substitute for competence. :-)

---

### Post by CptPicard on 2007-08-18
You fall into the classic n00b trap of imagining that there is such a thing as a generally "more powerful" language than some other language. We see these sorts of opinions here every now and then.

Here's an important point: there is an equivalence between Turing-complete programming languages (all "full" programming languages are Turing-complete). As soon as you reach a certain point of expressiveness, all languages are "equally good enough" as far as theory of computation goes -- this means that you can solve the same set of problems with them. In that sense, BASIC, Pascal, C/C++, Java, Python... are all equally powerful.

Now, depending on what you're doing, you might prefer one language over another, due to differences between languages. There is no such thing as objectively "better" or "more powerful" language.

C is actually a very simple language as far as the language syntax goes, and in that sense it is elegant. It is also "powerful" if you want to code low-level, as it exposes you to the hardware most -- most importantly, memory management -- and doesn't add layers of convenience. If you're writing an OS, that is Good. If you're writing something else, it might be Bad, because you'll just have to pay so much more attention to little low-level details you don't actually need to bother with when you're coding, say, command-line text-manipulation tools.

C++ on the other hand is syntactically complex and fairly low-level. With OO extensions to C, it's quite suitable for large-scale applications programming. Again, it's a "right tool for the job" question. In particular, C++ still forces you to manage your memory manually; garbage-collected languages are far more convenient for the programmer, so from a productivity standpoint they are "more powerful" when you do not explicitly need the ability to operate outside of a virtual machine (which is, roughly put, the difference between langauges you can code an OS in and not... look it up and understand..)

I don't understand your interest in which language is best for "OS programming". You're obviously such a beginner that you really don't want that to be a criterion for your learning, in particularly if it leads you to consider asm "because it's more powerful". Stick to Python, learn the basics, and you'll be better prepared to move onwards...

---

### Post by slavik on 2007-08-18
learn brainfuck ... it has only 8 statements and is turing complete. :)

---

### Post by CptPicard on 2007-08-18
Hmm... or if bribaetz is actually considering assembler because of its power, perhaps he should go all the way in general-purpose computing and start giving his programs in Turing machines or lambda calculus expressions? Now this would be hardcore fundamental :-k

---

### Post by slavik on 2007-08-19
I vote for hardwired circuits :P

---

### Post by loell on 2007-08-19
reading the thread, i felt the high egos of those who know programming or so those people that pretends to know.

---

### Post by bribaetz on 2007-08-19
i wasn't trying to be egotistic but then again i have not been saying i know how to program all that well and i really cant. but you people don't have to beat me down about it, that does not help me that just makes me resistant to help.

---

### Post by loell on 2007-08-19
> **bribaetz said:**
> i wasn't trying to be egotistic but then again i have not been saying i know how to program all that well and i really cant. but you people don't have to beat me down about it, that does not help me that just makes me resistant to help.

hey pal, i'm on you side here ;) ,i'm refferring them/him or what ever, if you could just read my post more carefully , 

cause if i'm reffering to you, i would address you as the **OP.**

---

### Post by daveshields on 2007-08-19
There is no single "best" programing language, and even comparing two given languages is not an exact science.

C and Python are at opposite ends of the spectrum. C is said to be "low level" meaning that it can be efficiently executed almost as well as assembly language; indeed, C has become in effect the portable assembly language of open-source. But it also lacks a number of features found in more modern, higher-level programming languages.

If you do want to get the flavor of C then I suggest you learn PHP. It is based on C and I expect that, since PHP is so widely used to support dynamic web sites,  you'll find the knowledge you gain from studying PHP more valuable than learning C itself, unless you want to be a Linux kernel  hacker, in which case C is the only game in town.

Python works at what is said to be a "higher" leve. You get language features such as automatic storage management, portability, and support for more flexible data structures. To get a flavor for Python, take a look at the source for some of the runtime libraries that are widely available, or look for an http server written in Python. Comparing that with Apache.org's http server,  which is written in C,  will also give you a feel for what is meant by language "level."

---

### Post by CptPicard on 2007-08-19
> **loell said:**
> reading the thread, i felt the high egos of those who know programming or so those people that pretends to know.

Please do tell in which category you feel I fall into ;)

Something I didn't quite touch in my response was brib's feeling that C is somehow "unelegant" despite being "powerful". There is a very simple reason to this -- C is both very general-purpose and minimal as a language. Pretty much everything outside of pointer and value manipulation, function calls and basic program logic is handled by outside libraries (standard library included), which means that sometimes, things are not always very consistent.

Python and other virtual machine (interpreter)-based languages are designed as a whole, standard library included. Of course this means you get a much more consistent system to work with.

At extremes, if you go to languages that are not genuinely general-purpose, but are aimed at specific problem domains, you get really powerful tools for specific purposes. It doesn't mean that they're neccessarily even Turing-complete, though (like HTML)...

---

### Post by pmasiar on 2007-08-19
> **loell said:**
> reading the thread, i felt the high egos of those who know programming or so those people that pretends to know.

I do have opposite problem. I see high egos of people who know but little, and don't realize that.

It is well know fact that this is beginners, and not experts, who tend to overestimate own knowledge. As they say, 10 years of experience means nothing only to someone lacking it.

I am willing to help, and understand that all beginners are green, but it is quite frustrating to compete for attention with people who have maybe college level experience in maybe 1-2 languages, or less, and still feel they are qualified to give expert advice. I don't want to brag with my experience, and big part of it is in obsolete languages, but still...

---

### Post by loell on 2007-08-19
> **pmasiar said:**
> I do have opposite problem. I see high egos of people who know but little, and don't realize that.

perhaps you've mistakenly identify an ego  from an enthusiastic classic noob , who want to take on programming swiftly and quickly, i believe we've all gone to this stage at some point in programming.


> I am willing to help, and understand that all beginners are green, but it is quite frustrating to compete for attention with people who have maybe college level experience in maybe 1-2 languages, or less, and still feel they are qualified to give expert advice. I don't want to brag with my experience, and big part of it is in obsolete languages, but still...

yes it is frustrating , but then its always hard to compete for attention on advices given in the programming section, you can only be on the spotlight when you code meticulously for a project.  then one can see a developers experience on how beautifully they wrote it.

---

### Post by CptPicard on 2007-08-19
Enthusiastic noobs are great, helping them is fun. However, if someone is enthusiastic enough, they will get to work, educate themselves as much as they can, and when they have a genuine question, they will make sure they get the most of the help they will get by asking something they genuinely don't understand on their own, give grounds why they aren't enlightened yet so we can go straight to the source of the problem, and then when they get a response, they will chew through it for all it's worth, and if it turns out they are not prepared for the answer, they will follow the pointers given, educate themselves some more, and then come back with a hopefully refined question.

I'm not seeing that much here, unfortunately. Learning is a work-intensive process, and if someone is not willing to put in the effort, it's all futile.

---

### Post by beckham on 2007-08-20
I agree with cptPicard.

---

### Post by loell on 2007-08-20
> **CptPicard said:**
> Enthusiastic noobs are great, helping them is fun. 

> However, if someone is enthusiastic enough, they will get to work, educate themselves as much as they can, and when they have a genuine question, they will make sure they get the most of the help they will get by asking something they genuinely don't understand on their own, give grounds why they aren't enlightened yet so we can go straight to the source of the problem, and then when they get a response, they will chew through it for all it's worth, and if it turns out they are not prepared for the answer, they will follow the pointers given, educate themselves some more, and then come back with a hopefully refined question.

I'm not seeing that much here, unfortunately. Learning is a work-intensive process, and if someone is not willing to put in the effort, it's all futile.

how can you say this isn't a genuine question? surely the OP had some misconceptions about languages, but that does not mean its not been asked genuinely. 

even if the OP had related threads regarding this matter.  Either you continuosly help him or just ignore him. that's how it works.

but please spare the beginner with your sarcasm

---

### Post by LaRoza on 2007-08-20
To the OP, all the languages were written for a certain purpose and time, C was written with different goals in mind than Python. You'll find that syntax will vary wildly among languages and there is little point trying to find a "right" syntax.

If you want to learn a language, my wiki has links and information on many langauges, including C, Assembly and Python.

When starting, find a language, and work with it, *then* start learing other languages.

---

### Post by pmasiar on 2007-08-20
> **loell said:**
> how can you say this isn't a genuine question? 

Because he post 2 new questions before digesting answers from previous one. 

There is in "emperor shortcut" to learn programming, or chess, or any other intellectual activity. CptPicard expressed it the best.

> surely the OP had some misconceptions about languages, but that does not mean its not been asked genuinely. 

IMHO OP is asking genuinely but obsessively :-) 
But not all is lost, if OP is genuinely interested, and willing to do his homework, he will learn and be fine. Everyone was young and green once... For some it is in more distant past, that's all. maybe we were more patient when learning in times before Internet... 

> even if the OP had related threads regarding this matter.  Either you continuosly help him or just ignore him. that's how it works.

No, I like to help - thats why I am here. But if I waste my own time to write answer, with pointers for OP to what to do next, wouldn't it be nice for OP to follow the pointers, do some googling and wikipedia reading, before asking for more attention? 

> but please spare the beginner with your sarcasm

I used sarcasm as last defense from onslaught of hare-brained questions on forum. I value this forum, and want to protect it from noise.

Read this famous post, [A Group Is Its Own Worst Enemy](http://www.shirky.com/writings/group_enemy.html) about that can happen on forums if discussion is not regulated.

---

### Post by bribaetz on 2007-08-20
pm im not going to liste to you i make a thread based on where i am at the moment and when i ask a question i dont expect you to fallow me around in th treads and put me down. heres one of my own.
the wise are humbled even when to the foolish while the foolish are eregent to the wise.

---

### Post by Wybiral on 2007-08-20
bb im not going to liste to you i take th time to help you you dont bothe listeing to anyone when thy try to help thats why peple arnt able to help you you dont liste we are not eregent to the wise we only try to help no one is fallowing you

---

### Post by pmasiar on 2007-08-20
> **bribaetz said:**
> pm im not going to liste to you i make a thread based on where i am at the moment and when i ask a question i dont expect you to fallow me around in th treads and put me down. heres one of my own.
the wise are humbled even when to the foolish while the foolish are eregent to the wise.

Sorry, but English is not my first language, and when parsing this snippet I got "Spelling error overflow" - I can catch the spirit, but have **no** idea what you are trying to tell. :-(

---

### Post by skeeterbug on 2007-08-20
> **pmasiar said:**
> Sorry, but English is not my first language, and when parsing this snippet I got "Spelling error overflow" - I can catch the spirit, but have **no** idea what you are trying to tell. :-(

lol

---

### Post by LaRoza on 2007-08-21
...
-EDIT I was aware that you know many languages, and first studied Assembly (from another thread), sorry if my comment was not appropriate.

---

### Post by Nekiruhs on 2007-08-21
> **bribaetz said:**
> pm im not going to liste to you i make a thread based on where i am at the moment and when i ask a question i dont expect you to fallow me around in th treads and put me down. heres one of my own.
the wise are humbled even when to the foolish while the foolish are eregent to the wise.
Ok, English is my first language and that still didn't make any sense, logically or syntacticly. Maybe the post should have been as follows:
> 
[COLOR="Red"]Pmasiar[/COLOR], [COLOR="DarkOrange"]I'm[/COLOR] not going to [COLOR="Red"]listen[/COLOR] to you. I have made a thread based on where I am at the moment, and when I try to ask a question I [COLOR="DarkOrange"]don't[/COLOR] expect you to [COLOR="Red"]follow[/COLOR] me around in the thread and put me down. Here is a saying of my own:
Have you even heard of a spell check? You know those red underlines underneath words? Try right clicking and selecting the right word.

---

### Post by cb951303 on 2007-08-21
that's easy. python is a high-level language and C is a low-level language. You just can't compare them the way you do....

---

### Post by Lster on 2007-08-21
Isn't python written in C?

---

### Post by LaRoza on 2007-08-21
> **Lster said:**
> Isn't python written in C?

Yes.

---

### Post by pmasiar on 2007-08-21
FYI, my first "programming" language was ASM for IBM/360, then Algol60.

---

### Post by pmasiar on 2007-08-21
> **Lster said:**
> Isn't python written in C?

It depends.

There are 4 implementations of Python:
- original which you most likely use, in C, called also CPython in context of comparing implementations
- JPython, or Jython, implementing Python in Java/JVM
- IronPython, in C#, for .NET on top of CLI.NET
- PyPy, Python in Python, implemented in (subset of) Python.

---

### Post by LaRoza on 2007-08-21
--edit--

---

### Post by Wybiral on 2007-08-21
> original which you most likely use, in C, called also CPython in context of comparing implementations

Have any of you ever looked at the source to Python? It's crazy! That's some hardcore C code. I was going to try to get familiar with it and maybe help with development if I ever got the chance, but it's going to take a long time before I'm comfortable enough with that source to even think about improving it (if it's possible).

I used to be a low-level snob who's motto was "if it's not as efficient as it can be, it's not efficient enough" but recently I've begun to realize just how valuable high level languages are.

Case in point: some of the code behind Python is almost certainly more optimized then any code I would have produced, and I can take advantage of that without having to worry about it. For me to assume that I could write better code then ALL of the developers who have pitched in on Python, and to do it for every project I work on... That would just be arrogant.

Sure, languages like Python have inherent soft spots for efficiency (such as tight loops) but that's only a portion of the battle. Algorithmic solutions tend to have a MUCH greater impact then "simple operation" optimization.

(I'm done hijacking this thread now, lol)

---

### Post by pmasiar on 2007-08-21
> **LaRoza said:**
> I am not very please with your insinuation that I am in any way close minded to other cultures or languages, and that I am from the USA.

Well, then it is even harder to understand your joke. Maybe this is a joke specific to your culture which was funny for you but I cannot comprehend.

---

### Post by LaRoza on 2007-08-21
> **pmasiar said:**
> Well, then it is even harder to understand your joke. Maybe this is a joke specific to your culture which was funny for you but I cannot comprehend.

Nothing was supposed to be the butt of the joke, it was just a light hearted comment on the use of the word "language". I edited it, so it is gone now, except in your quote.

I am inclined to view things in terms of computers, so to me, finding references to computers in everyday conversation is amusing.

---

### Post by pmasiar on 2007-08-21
> **Wybiral said:**
> Algorithmic solutions tend to have a MUCH greater impact then "simple operation" optimization.

This is exactly the point of PyPy. If compiler/runtime is written in Python, it is easier to refactor and to try different variants of implementation.

---

### Post by beckham on 2007-09-07
Thanks for all the replies.

---

### Post by Fingolfin on 2007-10-01
> **CptPicard said:**
> Here's an important point: there is an equivalence between Turing-complete programming languages (all "full" programming languages are Turing-complete). As soon as you reach a certain point of expressiveness, all languages are "equally good enough" as far as theory of computation goes -- this means that you can solve the same set of problems with them. In that sense, BASIC, Pascal, C/C++, Java, Python... are all equally powerful.

Great summary Captain.
The underlying differences are in the compiler implementations which lead to different times required for programs compiled with different tools to execute and perform particular task.

---

### Post by pmasiar on 2007-10-01
What about different times needed to write (code)  the same task in different languages? Would you argue that parsing a text file is easier done in C than in ie Python? I know that C code would run faster, but what if CPU speed is not my bottleneck and I don't care?

---

### Post by Fingolfin on 2007-10-02
Complex subject is that "language organisation" whenever C needs to be analysed. It is reasonable to assume that faster executable is the ultimate programming goal. I think that's what propelled C to the top of the game. 
Pascal was there a year before, with its strong and secure typing, the clearest syntax + unmatched speed of parsing who would think it could have ever been replaced with something else. 
Then, if C compilers were not producing faster executables (due to intimate relation with the underlying operating systems UNIX/BSD and later MS Windows), how could it have ever ousted Pascal from the throne?

---

### Post by CptPicard on 2007-10-02
> **Fingolfin said:**
> Complex subject is that "language organisation" whenever C needs to be analysed. It is reasonable to assume that faster executable is the ultimate programming goal.

Ricer ;)

Especially nowadays when computers are faster all the time, squeezing every single millisecond out of your code is not the point at all. Let the computer do the grinding, that's why it is there, and focus your human resources on expressing your ideas in a higher-level language. You should also be aware that switching to a better algorithm beats any fine-tuning, always, by a long shot.

For me the ultimate programming goal is to express my ideas elegantly and preferably quickly, and in a way that is clean enough for me, or someone else, to get back to it in a few years' time.

> Pascal was there a year before, with its strong and secure typing, the clearest syntax + unmatched speed of parsing who would think it could have ever been replaced with something else.

Pascal is more verbose and sort of unwieldy at points, C is really compact as a language and gained momentum because it ended up being the UNIX systems programming language of choice. And who cares about the speed of Pascal's parsing? It's a compiled language, no? I would think that it being syntactically more complex than C, it would actually parse slower...

> Then, if C compilers were not producing faster executables (due to intimate relation with the underlying operating systems UNIX/BSD and later MS Windows)

It has nothing to do with compiler being somehow intimately tied to OS and producing faster code. The point is that C just ended up being the language for UNIX development, so everyone who interfaced with the OS had to write apps in C...

---

### Post by pmasiar on 2007-10-02
> **Fingolfin said:**
> It is reasonable to assume that faster executable is the ultimate programming goal. 

No. My ultimate goal is to get it done, fast, yesterday if possible at all :-) 

If CPU will be used for 20% instead of 5%, I don't care. Language which allows me to code my task the fastest, and then year later to change it (no Perl please) is what I prefer.

---

### Post by Coyote21 on 2007-10-02
> **bribaetz said:**
> my question is why is such a powerful language so much less organized and beautiful than python. (this is just a opinion)
i know that C has far far more capabilities but i think i may just learn assembly. any suggestions on what i should?, do im still continuing to learn CPP pascal and python. so really does C++ have the same abilities as C as fas as an os.

And again, the thread is hijacked, and their start to discuss about the diferences of one and another language, and about old programming days... So once, again I will answer directly to the question...

Why is C less beautiful than python?

Thre's three (even more) reasons for this, first one, python is an interpreted language, and C is an compiled language (That's why in python you don't have "variable types", the interpreter does it on the fly), second one, C is much more old than python, and some of the things that existed in python time, didn't existed in C time. 

Third, C was created, because the Unix creator, needed to port Unix from an PDP-7 to an PDP-11, and for that Ken Thompson, needed an language higher than assembler, so C was invented (see [http://pt.wikipedia.org/wiki/Unix](http://pt.wikipedia.org/wiki/Unix), if you want to know more, but basically since the first versions of Unix were free, everyone copied them, and make Unix clones, so the BSD branch was born, and many other Unices, including Linux (in 1991). And no other operating system using other concept ever made it to destroy the Unix, or it's clones... God is still waiting to give someone the deed :rolleyes:), forth, python shares more concepts with functional languages (like Lisp), than C, which is an procedural language.

Does C++ has the same abilities for doing an OS, that C?

Certainly, the only differences it that you can't use new nor delete (at least until the memory manager/page manager is on), the C++ standard library is off the game, and you can't use exceptions either (or  pure virtual classes, and global objects), see [http://www.osdev.org/wiki/C_PlusPlus](http://www.osdev.org/wiki/C_PlusPlus), if you want to know more... (Even  pascal can do an os).

---

### Post by slavik on 2007-10-02
Python is also about 30 years younger than C

---

### Post by CptPicard on 2007-10-02
> **Coyote21 said:**
> And again, the thread is hijacked, and their start to discuss about the diferences of one and another language, and about old programming days... So once, again I will answer directly to the question...


Nothing wrong with hijacking the thread, as the OP seems to be long gone, and frankly, no amount of explaining to him would have amounted to much more than wasted characters :p Besides, if he really was interested in an answer, he will find enlightenment in the discussion...

---

### Post by Wybiral on 2007-10-02
> **slavik said:**
> Python is also about 30 years younger than C

And C is about 20 years younger than assembly

---

### Post by slavik on 2007-10-02
> **Wybiral said:**
> And C is about 20 years younger than assembly
yes, and that's why you don't see "libraries" in assembly like in C.

also, when people used assembly/machine code/pascal they didn't even have a concept of a "stored program" today, the only computer you see without permanent storage (hard drive or even a floppy) is probably a non-working system :)

---

### Post by Fingolfin on 2007-10-02
> **CptPicard said:**
> It has nothing to do with compiler being somehow intimately tied to OS and producing faster code. The point is that C just ended up being the language for UNIX development, so everyone who interfaced with the OS had to write apps in C...

I was never able to find the satisfactory answer to the question why exactly the same numerical algorithms compiled with  gcc  or  intel c compiler always beat the equivalent from FPC with the execution times reduced by 10-20% on average. And ignorantly decided that it must be down to UNIX being written in C and not in Pascal :-)

I can't help but bring the GNU Pascal into the story here, not because it is a Pascal but because of the rumours I heard some time ago that its parser will be back-ended by gcc.
I wonder if it is going to be possible in that case for a compiler to generate identical machine code for the same algorithms written in two different 3GL languages. Or maybe that's already a reality? I recall that C and Pascal compilers on Sun Solaris used to cross-compile and link with the chunks of code written in the other language (assembler included I guess).

Something on the speed of parsing can be found here:
[http://en.wikipedia.org/wiki/Comparison_of_Pascal_and_C](http://en.wikipedia.org/wiki/Comparison_of_Pascal_and_C)

---

### Post by Wybiral on 2007-10-02
> **slavik said:**
> yes, and that's why you don't see "libraries" in assembly like in C.

also, when people used assembly/machine code/pascal they didn't even have a concept of a "stored program" today, the only computer you see without permanent storage (hard drive or even a floppy) is probably a non-working system :)

Why does the fact that assembly is 20 years older then C have anything to do with their use for programming libraries?

I don't see where you're going with the second statement.

My point was that age has NOTHING to do with quality in a language, in fact... Inversely because languages evolve and get better.

C caught on because it was a portable abstraction over assembly. Languages like Python are catching on because they are an even more portable abstraction over C.

---

### Post by CptPicard on 2007-10-02
> **Fingolfin said:**
> I was never able to find the satisfactory answer to the question why exactly the same numerical algorithms compiled with  gcc  or  intel c compiler always beat the equivalent from FPC with the execution times reduced by 10-20% on average.

Well, it is just a compiler quality issue of course. Some compilers optimize better than others. :) Has little to do with the OS the compiler runs on or compiles for...

> I wonder if it is going to be possible in that case for a compiler to generate identical machine code for the same algorithms written in two different 3GL languages. Or maybe that's already a reality?

It's well possible, and in a lot of cases even probable. After all, the corollary of what I said about programming language equivalence a while ago (that you commented on) is that indeed, you can translate any algorithm from one language to the other. GCC first parses with the front-end, then has this internal representation for your code that it manipulates to optimize, and then the back-end dumps the structure into assembly. Especially for simpler pieces of code, I can well imagine everything after the front-end can be near identical, if not completely so.

---

### Post by slavik on 2007-10-02
how is Python any more portable then say Perl or Smalltalk?

---

### Post by samjh on 2007-10-02
> **Fingolfin said:**
> I can't help but bring the GNU Pascal into the story here, not because it is a Pascal but because of the rumours I heard some time ago that its parser will be back-ended by gcc.
I wonder if it is going to be possible in that case for a compiler to generate identical machine code for the same algorithms written in two different 3GL languages.

On a related note, here is a simple test with four languages all compiled to assembly code using GCC or a GCC back-end compiler.

I used Ada, C, C++, and Pascal.  Compilers used were gnat, gcc, g++, and gpc, respectively.  No optimisation flags.  Only compiled using the -S switch to generate assembly.

Here are the results, with source code first, and then the resultant assembly code:

**Ada test:**
```
with Ada.Text_IO;

procedure adatest is
begin
    Ada.Text_IO.Put_Line("Hello world.");
end adatest;
```
```
	.file	"adatest.adb"
	.section	.rodata
	.align 4
	.type	C.0.390, @object
	.size	C.0.390, 8
C.0.390:
	.long	1
	.long	12
.LC0:
	.ascii	"Hello world."
	.text
.globl _ada_adatest
	.type	_ada_adatest, @function
_ada_adatest:
.LFB3:
	pushl	%ebp
.LCFI0:
	movl	%esp, %ebp
.LCFI1:
	subl	$24, %esp
.LCFI2:
	movl	$.LC0, %eax
	movl	%eax, -8(%ebp)
	movl	$C.0.390, -4(%ebp)
	movl	-8(%ebp), %eax
	movl	-4(%ebp), %edx
	movl	%eax, (%esp)
	movl	%edx, 4(%esp)
	call	ada__text_io__put_line__2
	leave
	ret
.LFE3:
	.size	_ada_adatest, .-_ada_adatest
.globl __gnat_eh_personality
	.section	.eh_frame,"a",@progbits
.Lframe1:
	.long	.LECIE1-.LSCIE1
.LSCIE1:
	.long	0x0
	.byte	0x1
	.string	"zP"
	.uleb128 0x1
	.sleb128 -4
	.byte	0x8
	.uleb128 0x5
	.byte	0x0
	.long	__gnat_eh_personality
	.byte	0xc
	.uleb128 0x4
	.uleb128 0x4
	.byte	0x88
	.uleb128 0x1
	.align 4
.LECIE1:
.LSFDE1:
	.long	.LEFDE1-.LASFDE1
.LASFDE1:
	.long	.LASFDE1-.Lframe1
	.long	.LFB3
	.long	.LFE3-.LFB3
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI0-.LFB3
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI1-.LCFI0
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE1:
	.ident	"GCC: (GNU) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)"
	.section	.note.GNU-stack,"",@progbits
```

**C test:**

```
#include <stdio.h>

int main(void)
{
    printf("Hello World.\n");
    return 0;
}
```
```
	.file	"ctest.c"
	.section	.rodata
.LC0:
	.string	"Hello World."
	.text
.globl main
	.type	main, @function
main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	subl	$4, %esp
	movl	$.LC0, (%esp)
	call	puts
	movl	$0, %eax
	addl	$4, %esp
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
	.size	main, .-main
	.ident	"GCC: (GNU) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)"
	.section	.note.GNU-stack,"",@progbits
```

**C++ test:**

```
#include <iostream>

int main()
{
    std::cout << "Hello World." << std::endl;
    return 0;
}
```
```
	.file	"cpptest.cpp"
	.section	.ctors,"aw",@progbits
	.align 4
	.long	_GLOBAL__I_main
	.text
	.align 2
	.type	_Z41__static_initialization_and_destruction_0ii, @function
_Z41__static_initialization_and_destruction_0ii:
.LFB1409:
	pushl	%ebp
.LCFI0:
	movl	%esp, %ebp
.LCFI1:
	subl	$24, %esp
.LCFI2:
	movl	%eax, -4(%ebp)
	movl	%edx, -8(%ebp)
	cmpl	$1, -4(%ebp)
	jne	.L5
	cmpl	$65535, -8(%ebp)
	jne	.L5
	movl	$_ZSt8__ioinit, (%esp)
	call	_ZNSt8ios_base4InitC1Ev
	movl	$__dso_handle, 8(%esp)
	movl	$0, 4(%esp)
	movl	$__tcf_0, (%esp)
	call	__cxa_atexit
.L5:
	leave
	ret
.LFE1409:
	.size	_Z41__static_initialization_and_destruction_0ii, .-_Z41__static_initialization_and_destruction_0ii
.globl __gxx_personality_v0
	.align 2
	.type	_GLOBAL__I_main, @function
_GLOBAL__I_main:
.LFB1411:
	pushl	%ebp
.LCFI3:
	movl	%esp, %ebp
.LCFI4:
	subl	$8, %esp
.LCFI5:
	movl	$65535, %edx
	movl	$1, %eax
	call	_Z41__static_initialization_and_destruction_0ii
	leave
	ret
.LFE1411:
	.size	_GLOBAL__I_main, .-_GLOBAL__I_main
	.align 2
	.type	__tcf_0, @function
__tcf_0:
.LFB1410:
	pushl	%ebp
.LCFI6:
	movl	%esp, %ebp
.LCFI7:
	subl	$8, %esp
.LCFI8:
	movl	$_ZSt8__ioinit, (%esp)
	call	_ZNSt8ios_base4InitD1Ev
	leave
	ret
.LFE1410:
	.size	__tcf_0, .-__tcf_0
	.section	.rodata
.LC0:
	.string	"Hello World."
	.text
	.align 2
.globl main
	.type	main, @function
main:
.LFB1401:
	leal	4(%esp), %ecx
.LCFI9:
	andl	$-16, %esp
	pushl	-4(%ecx)
.LCFI10:
	pushl	%ebp
.LCFI11:
	movl	%esp, %ebp
.LCFI12:
	pushl	%ecx
.LCFI13:
	subl	$20, %esp
.LCFI14:
	movl	$.LC0, 4(%esp)
	movl	$_ZSt4cout, (%esp)
	call	_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movl	$_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_, 4(%esp)
	movl	%eax, (%esp)
	call	_ZNSolsEPFRSoS_E
	movl	$0, %eax
	addl	$20, %esp
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
.LFE1401:
	.size	main, .-main
	.local	_ZSt8__ioinit
	.comm	_ZSt8__ioinit,1,1
	.weakref	_Z20__gthrw_pthread_oncePiPFvvE,pthread_once
	.weakref	_Z27__gthrw_pthread_getspecificj,pthread_getspecific
	.weakref	_Z27__gthrw_pthread_setspecificjPKv,pthread_setspecific
	.weakref	_Z22__gthrw_pthread_createPmPK14pthread_attr_tPFPvS3_ES3_,pthread_create
	.weakref	_Z22__gthrw_pthread_cancelm,pthread_cancel
	.weakref	_Z26__gthrw_pthread_mutex_lockP15pthread_mutex_t,pthread_mutex_lock
	.weakref	_Z29__gthrw_pthread_mutex_trylockP15pthread_mutex_t,pthread_mutex_trylock
	.weakref	_Z28__gthrw_pthread_mutex_unlockP15pthread_mutex_t,pthread_mutex_unlock
	.weakref	_Z26__gthrw_pthread_mutex_initP15pthread_mutex_tPK19pthread_mutexattr_t,pthread_mutex_init
	.weakref	_Z26__gthrw_pthread_key_createPjPFvPvE,pthread_key_create
	.weakref	_Z26__gthrw_pthread_key_deletej,pthread_key_delete
	.weakref	_Z30__gthrw_pthread_mutexattr_initP19pthread_mutexattr_t,pthread_mutexattr_init
	.weakref	_Z33__gthrw_pthread_mutexattr_settypeP19pthread_mutexattr_ti,pthread_mutexattr_settype
	.weakref	_Z33__gthrw_pthread_mutexattr_destroyP19pthread_mutexattr_t,pthread_mutexattr_destroy
	.section	.eh_frame,"a",@progbits
.Lframe1:
	.long	.LECIE1-.LSCIE1
.LSCIE1:
	.long	0x0
	.byte	0x1
	.string	"zP"
	.uleb128 0x1
	.sleb128 -4
	.byte	0x8
	.uleb128 0x5
	.byte	0x0
	.long	__gxx_personality_v0
	.byte	0xc
	.uleb128 0x4
	.uleb128 0x4
	.byte	0x88
	.uleb128 0x1
	.align 4
.LECIE1:
.LSFDE1:
	.long	.LEFDE1-.LASFDE1
.LASFDE1:
	.long	.LASFDE1-.Lframe1
	.long	.LFB1409
	.long	.LFE1409-.LFB1409
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI0-.LFB1409
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI1-.LCFI0
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE1:
.LSFDE3:
	.long	.LEFDE3-.LASFDE3
.LASFDE3:
	.long	.LASFDE3-.Lframe1
	.long	.LFB1411
	.long	.LFE1411-.LFB1411
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI3-.LFB1411
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI4-.LCFI3
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE3:
.LSFDE5:
	.long	.LEFDE5-.LASFDE5
.LASFDE5:
	.long	.LASFDE5-.Lframe1
	.long	.LFB1410
	.long	.LFE1410-.LFB1410
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI6-.LFB1410
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI7-.LCFI6
	.byte	0xd
	.uleb128 0x5
	.align 4
.LEFDE5:
.LSFDE7:
	.long	.LEFDE7-.LASFDE7
.LASFDE7:
	.long	.LASFDE7-.Lframe1
	.long	.LFB1401
	.long	.LFE1401-.LFB1401
	.uleb128 0x0
	.byte	0x4
	.long	.LCFI9-.LFB1401
	.byte	0xc
	.uleb128 0x1
	.uleb128 0x0
	.byte	0x9
	.uleb128 0x4
	.uleb128 0x1
	.byte	0x4
	.long	.LCFI10-.LCFI9
	.byte	0xc
	.uleb128 0x4
	.uleb128 0x4
	.byte	0x4
	.long	.LCFI11-.LCFI10
	.byte	0xe
	.uleb128 0x8
	.byte	0x85
	.uleb128 0x2
	.byte	0x4
	.long	.LCFI12-.LCFI11
	.byte	0xd
	.uleb128 0x5
	.byte	0x4
	.long	.LCFI13-.LCFI12
	.byte	0x84
	.uleb128 0x3
	.align 4
.LEFDE7:
	.ident	"GCC: (GNU) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)"
	.section	.note.GNU-stack,"",@progbits
```

**Pascal test:**

```
program pascaltest;
begin
    writeln('Hello world.')
end.
```
```
	.file	"pascaltest.pas"
	.section	.rodata
.LC0:
	.string	"Hello world.\n"
	.text
.globl _p__M0_main_program
	.type	_p__M0_main_program, @function
_p__M0_main_program:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$24, %esp
	movl	$1568, 4(%esp)
	movl	_p_Output, %eax
	movl	%eax, (%esp)
	call	_p_Write_Init
	movl	$-2147483648, 12(%esp)
	movl	$13, 8(%esp)
	movl	$.LC0, 4(%esp)
	movl	_p_Output, %eax
	movl	%eax, (%esp)
	call	_p_Write_String
	movl	_p_Output, %eax
	movl	%eax, (%esp)
	call	_p_Write_Flush
	cmpl	$0, _p_InOutRes
	je	.L1
	call	_p_CheckInOutRes
.L1:
	leave
	ret
	.size	_p__M0_main_program, .-_p__M0_main_program
	.local	static_ctor_run_condition_0_1
	.comm	static_ctor_run_condition_0_1,1,1
.globl _p__M0_init
	.type	_p__M0_init, @function
_p__M0_init:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$8, %esp
	cmpb	$0, static_ctor_run_condition_0_1
	jne	.L4
	movb	$1, static_ctor_run_condition_0_1
	call	_p_DoInitProc
.L4:
	leave
	ret
	.size	_p__M0_init, .-_p__M0_init
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$24, %esp
	andl	$-16, %esp
	movl	$0, %eax
	addl	$15, %eax
	addl	$15, %eax
	shrl	$4, %eax
	sall	$4, %eax
	subl	%eax, %esp
	movl	_p_GPC_RTS_VERSION_20060325, %eax
	movl	$0, 12(%esp)
	movl	16(%ebp), %eax
	movl	%eax, 8(%esp)
	movl	12(%ebp), %eax
	movl	%eax, 4(%esp)
	movl	8(%ebp), %eax
	movl	%eax, (%esp)
	call	_p_initialize
	call	_p__M0_init
	call	_p__M0_main_program
	call	_p_finalize
	movl	$0, %eax
	leave
	ret
	.size	main, .-main
	.section	.note.GNU-stack,"",@progbits
	.ident	"GCC: (GNU) 3.4.6 (Ubuntu 3.4.6-5ubuntu1)"
```

Perhaps someone with good assembly knowledge could whittle down the assembly code to their essentials.  Predictable, the assembly code from C is the smallest.  Strangely, the assembly from C++ is the largest.  I'd have thought Ada's assembly would be largest.  Also strange is all the .weakref lines in C++'s assembly.  I wonder what that's all about.

---

### Post by CptPicard on 2007-10-02
IMO your test is not really representative of the compiler because what you're doing is just having the boilerplate for making a single syscall for printing :)

C++'s objects always get substantially bigger at the point at which you bring iostream in, it's a fairly complex library although it just prints to screen in Hello World.

What I would be interested in seeing would be some simple arithmetic, looping, branching and maybe a few calls and some recursion, without any library use. Then just strip all the header and footer fluff and see what the actual algorithmic bit looks like. It should be quite identical. :)

---

### Post by Wybiral on 2007-10-02
> **slavik said:**
> how is Python any more portable then say Perl or Smalltalk?

Stop being so defensive... I never said it was. I said "languages LIKE python" (meaning higher level languages).

---

### Post by slavik on 2007-10-02
my point is also that Perl is much older than Python and more widespread. any *nix system comes with perl, but not every *nix system comes with python.

---

### Post by Wybiral on 2007-10-03
> **slavik said:**
> my point is also that Perl is much older than Python and more widespread. any *nix system comes with perl, but not every *nix system comes with python.

And my point was that age doesn't merit superiority.

Almost all modern *nix distributions come with Python too... And the two-three that don't can easily install it. If you disagree, show me some examples (I can probably find some that lack Perl too). I'm not sure what your point is. You first attack Python by making a comparison with C, then you try to use Perl (which nullifies your C comparison). Sounds like you're just militantly anti-Python to me, with no real point.

---

### Post by loell on 2007-10-03
if the lines of words  of this thread would have been converted to lines of codes, most probably we would finish a nice project by now, sigh :lolflag:

---

### Post by eph1973 on 2007-10-03
Huh, I did a google search for flame war and came across this thread....

---

### Post by loell on 2007-10-03
flamewar? no flamewar here, just an intense discussion.

some coders would even dare say "a poinltess one" :popcorn:

---

### Post by pmasiar on 2007-10-03
It IS pointless, but less pointless than other threads started by this same OP - we know him well, what do you expect?

Of course any discussion about "why you prefer this or that language" is pointless by definition. But it requires superb self-control not to join :-)

---

### Post by Fingolfin on 2007-10-03
So, yet another C language thread bites the dust.

---

### Post by bribaetz on 2007-10-28
> **pmasiar said:**
> Thats easy: because Python has garbage collection :-)

Ah I forgot you are not done reading yet :-) - it went hight above your head

i think i get what your saying
more or less i guess i didn't want to get what you were saying because i was  feeling picked on  so i guess i apologize

---

### Post by ThinkBuntu on 2007-10-28
Ha ha...this is a very funny flamewar when inebriated...I mean, why does it matter? Use what you like. You know which feels more comfortable to you, and you know which ones are fast (C, Perl, C++) and slow (Python, Ruby, maybe PHP, Java), and you know which ones your environment requires. So it shouldn't be so tough. I know that I feel most comfortable in JavaScript because I learned that first, but I would always use PHP for a site's backend, and Python for a simple desktop application. With the opportunity, I'd love to try out a Rails app too.

---

