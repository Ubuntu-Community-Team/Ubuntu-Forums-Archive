---
title: "beginning programing"
date: 2007-10-26
forum: Programming Talk
---

### Post by DestroyMicroshaft on 2007-10-26
Hello everyone, Ive been doing some poking around about programing, and have decided its a path Id like to take, so I'm kind of looking for some direction here. Id like to be able to make applications, like a dvd burning program, or a file converter, you standard useful applications, Ive pretty much narrowed down the languages Id like to learn, and Ive come down to pretty much c/c++ or python, now it seems everywhere I go people are screaming python, but I'm totally oblivious in this area of computers, I don't know where to start basically. One thing Id like to able to do write stuff for Linux, but eventually windows, as I'm thinking about making this a career move, which is why I was kind of leaning towards c/c++, I don't know, and direction would be greatly appreciated.

---

### Post by lhtown on 2007-10-26
How to think like a computer scientist (the python version) is a good place to start for the self-taught. Make sure you get the more recent version. The original one is a bit dated. You can google it. It is a free download.

---

### Post by aks44 on 2007-10-26
> **DestroyMicroshaft said:**
> Id like to be able to make applications, like a dvd burning program, or a file converter, you standard useful applications

Forget about that for the moment, you'll spend much time just learning and not doing anything eally useful.


> **DestroyMicroshaft said:**
> Ive pretty much narrowed down the languages Id like to learn, and Ive come down to pretty much c/c++ or python, now it seems everywhere I go people are screaming python

For a beginner, I believe Python is indeed a ****very**** good start. It will allow you to easily learn the basics of programming.


> **DestroyMicroshaft said:**
> One thing Id like to able to do write stuff for Linux, but eventually windows, as I'm thinking about making this a career move

Funny, considering your user name / avatar. ;)


> **DestroyMicroshaft said:**
> I'm thinking about making this a career move, which is why I was kind of leaning towards c/c++

If you are serious enough about *industry* programming, you'll eventually have to learn C++. But it requires many knowledge of what happens under the hood, so better start easy with Python.


My best bet for a wannabe C++ programmer is:
- learn an easy language, and programming basics (Python - probably several years)
- learn hardcore "close-to-the-metal" stuff (ASM - one year may be enough)
- combine both, and learn new tricks (C++ - a lifetime)


If you're not going to do low-level system programming, better avoid C altogether. It may give you bad habits when it comes to C++.


Note: I'm a C++ architect/programmer. So please take these advices for what they're worth: a bit biased. ;)

---

### Post by Can+~ on 2007-10-26
Everyone say python is a good start, I personally started directly with C, but anyway, here are some tips for any language:
[LIST]
[*]Set some goals, but reachable. A dvd-burning-app may be very complex right now. So start with something easier. Like:[LIST]
[*]Creating a Factorial calculator (5! = 1x2x3x4x5)
[*]Arrays: Create a matrix and "transpose" it (Mixj -> Mjxi).
[*]Etc..
[/LIST]
[*]Having an IDE usually makes everything easier, compiling and editing.
[*]Is good to look at examples, but beware: those example must be on your same or a little superior "level", since something complex may confuse you.
[*]STORE EVERYTHING! You may be dealing with same old problems a lot, sometimes the best solution, is the one you coded years ago.
[*]When starting with functions, create small functions, a single task for each one. Later you can move on making things more hard.
[/LIST]

---

### Post by DestroyMicroshaft on 2007-10-26
> **aks44 said:**
> 

Funny, considering your user name / avatar. ;)



LOL, yeah well I just thought that to get a paying job in programming you have to be writing windows/mac software, If theres a way to earn a living only programming for Linux Id love to know about it, so I can set my goals towards that.

Thanks for everyones help, I guess Ill start with python then, anyone recommend a book? Ive grabbed a few from torrents i.e. Python in a nutshell & Python programming.

---

### Post by Wybiral on 2007-10-26
I'm also going to suggest Python. It's easy to learn and will teach you in a way that promotes good design. Unlike aks44, I don't think C is the devil :) but I do agree that if C++ is your goal, it takes some mental acrobatics to go from C idioms to C++. So, I too would suggest Python, then C++ (if you even find that you need it).

> **aks44 said:**
> Funny, considering your user name / avatar. ;)

lol

---

### Post by aks44 on 2007-10-26
> **DestroyMicroshaft said:**
> If theres a way to earn a living only programming for Linux Id love to know about it

Don't even look at me, I've been doing almost exclusively Microsoft (DOS/Windows) software since forever, and only got serious about Linux like 6 months ago... ;)


> **Wybiral said:**
> Unlike aks44, I don't think C is the devil :) but I do agree that if C++ is your goal, it takes some mental acrobatics to go from C idioms to C++.

Don't get me wrong... C is a perfectly fine language. I just happen to be pretty voicy about the fact that (IMHO) it is a bad start **_if_** you plan to learn C++ in the end, because of the very "mental acrobatics" you mentionned... ;)

---

### Post by pmasiar on 2007-10-26
wiki in my sig has plenty links to get you started with Python: good online books, and (text-only) tasks to solve before you are ready for major league GUI.

Yes, you **can** get good job in Python, as YouTube guys found. In fact, web apps are next hot area, and doing them in C++ is just waste of resources.

---

### Post by aks44 on 2007-10-26
> **pmasiar said:**
> In fact, web apps are next hot area, and doing them in C++ is just waste of resources.

+1


However, don't forget that for every front-end (even web-based ones) you need to have a performant, hardcore backend. Which is where C or C++ kick in.

Now it's all a matter of what you prefer to do, but both kinds of programming have their place under the sun... :)

---

### Post by pmasiar on 2007-10-26
> **aks44 said:**
> but both kinds of programming have their place under the sun... :)

Python for apps; C or C++ for libraries, database engines, web servers, OS and other stuff deep down, close to the metal. So yes, if you see yourself as next MySQL, C++ is better fit. But you should to start with Python anyway: even deep down, there are task which are not time critical (build scripts, generating test data, etc) where Python will be perfect fit.

---

### Post by jespdj on 2007-10-26
> **DestroyMicroshaft said:**
> LOL, yeah well I just thought that to get a paying job in programming you have to be writing windows/mac software, If theres a way to earn a living only programming for Linux Id love to know about it, so I can set my goals towards that.
That's not necessarily true. I'm a professional software developer and  I have not written any apps for Windows since 2000. I am programming mainly in Java, which is used by many big companies for many different business applications. Most of the software I write runs on big Unix servers (running AIX, HP-UX, Solaris, Linux...). Sometimes I make web applications, but most of the software that I write doesn't even have a GUI.

> Thanks for everyones help, I guess Ill start with python then, anyone recommend a book? Ive grabbed a few from torrents i.e. Python in a nutshell & Python programming.
Start with this excellent [Python tutorial](http://docs.python.org/tut/) from the Python home website. You do realize that those books you grabbed from torrents are illegal copies, don't you?

---

### Post by Fbot1 on 2007-10-26
I honestly think you're better of with C.

---

### Post by LaRoza on 2007-10-26
> **Fbot1 said:**
> I honestly think you're better of with C.

How to start: Top->Down, Bottom->Top is an interesting topic. But for speed, learning with Python, then C is most likely faster than C to Python.

---

### Post by dewey on 2007-10-26
Ideally, I believe one should start as close to the system as possible, meaning assembler first and progressing from there.

Once you know exactly how the computer works, you can think like a computer much better, hopefully leading to better coding and or better practices.  Not to mention it would simplify solving complex design problems.

Once you learn a low level language, you won't be spoiled by modern conveniences.

Although there is a huge flaw in my belief, very few people who wish to learn to program, will have the motivation to learn something as complex as assembly.  

So, the top->down perspective will proabably work out better, because if it's easier to get into programming in the first place, they will be more motivated to move on to better languages, and or improve themselves.

Cliff Notes:
Try python

---

### Post by LaRoza on 2007-10-26
> **dewey said:**
> 
Although there is a huge flaw in my belief, very few people who wish to learn to program, will have the motivation to learn something as complex as assembly.  


I am self taught. I started with C++, went up, then learned assembly. I also learned Fortran 77, and am working on Lisp.

Those with a drive to learn will succeed given the resources, and has nothing to do with what you start with.

---

### Post by Fbot1 on 2007-10-26
> **dewey said:**
> Although there is a huge flaw in my belief, very few people who wish to learn to program, will have the motivation to learn something as complex as assembly.

I think it's a lot less complex. The only downfalls are that it is unportable and the source is larger. IMHO python is crap. This is simply how I feel, the op obviously may not feel the same.

---

### Post by Fbot1 on 2007-10-26
> **LaRoza said:**
> Those with a drive to learn will succeed given the resources, and has nothing to do with what you start with.

I disagree, I've seen a lot of people screwed over because they don't feel comfortable using anything other than VB or python.

---

### Post by LaRoza on 2007-10-26
> **Fbot1 said:**
> I disagree, I've seen a lot of people screwed over because they don't feel comfortable using anything other than VB or python.

"drive to learn" means more than accepting what is understood in five minutes.

---

### Post by Fbot1 on 2007-10-26
> **LaRoza said:**
> "drive to learn" means more than accepting what is understood in five minutes.

Yes, I am aware...

---

### Post by LaRoza on 2007-10-27
> **Fbot1 said:**
> Yes, I am aware...

Then how do you disagree? Anyone unwilling to move forward because they are "not comfortable" with anything other than VB or Python is an indication of a lack of drive. 

If someone wants to learn something, and has access to the resources, they will be able to learn it. Those who don't put forth the effort will not get past their comfort zone.

---

### Post by Fbot1 on 2007-10-27
> **LaRoza said:**
> Then how do you disagree? Anyone unwilling to move forward because they are "not comfortable" with anything other than VB or Python is an indication of a lack of drive. 

If someone wants to learn something, and has access to the resources, they will be able to learn it. Those who don't put forth the effort will not get past their comfort zone.

They want to but just like most people they quit after a while.

---

### Post by LaRoza on 2007-10-27
> **Fbot1 said:**
> They want to but just like most people they quit after a while.

Most people don't have the drive. If it were easy, everyone would do.

---

### Post by Fbot1 on 2007-10-27
> **LaRoza said:**
> Most people don't have the drive. If it were easy, everyone would do.

It's not that it's hard. People are just lazy little bastards.

---

### Post by nickoli on 2007-10-27
I'm currently enrolled in college for computer programming the first programming class that I'm taking at the moment is unix scripting I haven't decided wether to go with c++ or java, I haven't given .net or visual any thought. Where does unix scripting fit in, also what do you think would be a wiser choice between java and c++?

---

### Post by slavik on 2007-10-27
everyone knows the language I am going to recommend, so I will not even mention it. :)

---

### Post by Fbot1 on 2007-10-27
> **nickoli said:**
> I'm currently enrolled in college for computer programming the first programming class that I'm taking at the moment is unix scripting I haven't decided whether to go with c++ or java, I haven't given .net or visual any thought. Where does unix scripting fit in, also what do you think would be a wiser choice between java and c++?

If you're looking for a job then Java.

---

### Post by LaRoza on 2007-10-27
> **Fbot1 said:**
> It's not that it's hard. People are just lazy little bastards.

True :), but tell them that to their faces. They can be sensitive.

---

### Post by LaRoza on 2007-10-27
> **nickoli said:**
> I'm currently enrolled in college for computer programming the first programming class that I'm taking at the moment is unix scripting I haven't decided wether to go with c++ or java, I haven't given .net or visual any thought. Where does unix scripting fit in, also what do you think would be a wiser choice between java and c++?

In the beginning, OS's were written in assembly. This had several problems, and C was invented to solve them. C was almost just as fast, and cross platform, as long as a compiler existed. C was low level and not good for basic tasks, the the shell was made. So Unix users had two tool, C, for system programming, and the shell for everything else.

The shell is still used, however, languages like Perl, Python and Tcl have more uses, and can do the same things. 

As for the Java v C++, I recommend learning both. Neither are hard. You should learn a language like Perl or Python. You also should not limit yourself to what the University teaches you. I know more languages and am a better programmer than the head of the IT department at my school, and I never took a class in that field. Learning C++ first might prepare you more for both Java and C. So I would say C++ first, but that is not hard coded (written in stone).

Don't do .net or visual until you have learned more portable languages, or we'll all make fun of your programming abilities. (j/k)

---

### Post by LaRoza on 2007-10-27
> **slavik said:**
> everyone knows the language I am going to recommend, so I will not even mention it. :)

You should put it in your sig.

[Learn Perl]("http://www.perl.com/pub/a/2000/10/begperl1.html") | [Get Perl]("http://www.activestate.com/Products/activeperl/")

---

### Post by slavik on 2007-10-27
no, sorry, no such thing as "get per", it's already there on any decent platform ;)

as for learn perl - [www.perl.org](www.perl.org) or [www.perlmonks.org](www.perlmonks.org)

---

### Post by LaRoza on 2007-10-27
> **slavik said:**
> no, sorry, no such thing as "get per", it's already there on any decent platform ;)

as for learn perl - [www.perl.org](www.perl.org) or [www.perlmonks.org](www.perlmonks.org)

The "Get Perl" link was for ActivePerl, for the not-so-good-but-widely-used OS.

---

### Post by slavik on 2007-10-27
read the whole sentence ;)

---

### Post by LaRoza on 2007-10-27
> **slavik said:**
> read the whole sentence ;)

I know, but you would be able to spread Perl by having it in your sig. It was just a suggestion.

---

### Post by pmasiar on 2007-10-27
> **Fbot1 said:**
> I think it's a lot less complex. The only downfalls are that it is unportable and the source is larger. IMHO python is crap. This is simply how I feel, the op obviously may not feel the same.

I think your advice (start via ASM) is crap. This is simply how I feel, but I do hope the op will feel the same.

---

### Post by LaRoza on 2007-10-27
> **pmasiar said:**
> I think your advice (start via ASM) is crap. This is simply how I feel, but I do hope the op will feel the same.

Sounds like that is how you started...

---

### Post by pmasiar on 2007-10-29
> **LaRoza said:**
> Sounds like that is how you started...

Yes, and we started on punchcards too. Does it mean that ppl should start  with punchcards now? 

And to remind you, we went to school all year in waist deep  snow, uphill both ways :-)

I remember first talk about Unix file system, for me, exposed to IBM JCL untill then, it was like a revelation. Imagine, tree of files and directories with flexible line lenght, instead of flat JCL namespace and fixed 80 char lines! 

There is no reason to start with ASM now, unless you really enjoy the pain.

---

### Post by DestroyMicroshaft on 2007-10-31
Thank you for all your help and sorry about the lengthy response time (limited internet access). I have settled on trying to learn Python 1st, as it seems just about anyewhere I go, most everyone says Python. Ive got a few ebooks, like beginning Python, Python in a nutshell, and programing in Pyhthon, to start off with. If anyone has any books to recomend, feel free to.

---

### Post by Nequeo on 2007-10-31
If you are interested in a career in programming, I think that rather than concentrating on one language to begin with - you should aim to put yourself in a position where you can learn any language quickly and easily. 

IMHO, I heartily agree that Python is the best place to start. It's a very easy language to pick up, and if you don't enjoy Python you probably won't enjoy programming at all. Even better - Python code reads like 'pseudocode', so once you're proficient in Python basics, you'll know how to think like a programmer. This *really* helps, and it's something I believe you can pick up faster learning Python than any other language.

But... Can I suggest that - despite what others have said - after you've learned the Python basics and you're comfortable writing basic scripts, then switch to C for a while.

Not for long, because you do pick up bad habits, but you should definitely master and pointers and dynamic memory allocation ('malloc' and 'free'). As soon you can write your own linked list, and *really understand* what you're doing, that's probably a good place to stop. 

The reason I suggest this is because it will give you a good, basic understanding of how other programming languages work 'under the hood'. When you come up against terms like 'pass by reference/pass by value', stack, heap, garbage collection, object references, delegates, etc. etc. you won't feel lost. 

After some basic C, if you're still interested in application programming as a career, I suggest your next step is Java. As an application developer for any platform, you're going to need to be strong on OO principles and design patterns. I think that Java is the best language for learning OO design. I'd put a bit of time in here, actually write a working program with a GUI. Go beyond just the basics and get a good feel for how the language works. As an added bonus, learning Java will teach you about 95% of C#, so if you ever have to do any .NET programming you're already there. 

By now you'll have good programming habits, have a basic understanding of how higher-level programming languages actually work, and an understanding of Object Oriented design. At this point you'll be in a position to pick up any 'teach yourself...' book, and teach yourself the basics of any other language in a day or so. This is also when you should probably choose a favorite language that you'd like to work with and get to know its APIs and idioms. 

I would also strongly recommend steering clear of C++ and PHP before this point. C++ is a punishing way to learn OO programming compared to Java, and PHP will teach you bad design principles. (Not saying it's a bad language - just that I've never seen a beginners guide to PHP that taught good design at the same time). 

I'd like to qualify this post by saying that this order of languages is not the way I learnt, but it's the way I'd want to learn if I had to do it all again.

---

### Post by LaRoza on 2007-10-31
> **pmasiar said:**
> Yes, and we started on punchcards too. Does it mean that ppl should start  with punchcards now? 

And to remind you, we went to school all year in waist deep  snow, uphill both ways :-)


I agreed with you, but was commenting on the possible pain in your "voice" about starting with ASM.

I think that ASM should be learned, for the knowledge, but not as an introduction. To learn it, you have to start with hardware and math before actually coding anything.

I believe it, if you grew up in Poland or nations near by.

The best hyperbole I heard was:

[quote="Old Timer"]
When I was your age, we didn't have shoes. When it snowed, we wrapped barbed wire around our feet for traction.
[/quote]

Also, my [a younger relative] was amazed that I didn't have a video game system when I was the same age. This relative has a Nintendo DS, a Game Cube, computer games, a Playstation 2, and maybe others. I still don't own a game system.

---

### Post by ThinkBuntu on 2007-11-01
> **LaRoza said:**
> I still don't own a game system.
I have one system: Sega Genesis baby! If I can't play your game without a memory card, I don't want to because that means you expect me to spend more than a couple hours to beat the game. Which means your game is all about quantity, not quality.

Exceptions: Zelda, and a couple others.

---

### Post by pmasiar on 2007-11-01
> **Nequeo said:**
> If you are interested in a career in programming....[start with Python, then C, Java, PHP

All valid advice, except one thing: Now, many people are learning programming who have no intentions to be "career programmers". A biologist parsing DNA sequences, engineer automating some simulation, lawyer writing a custom search for her data: with current affordability of hardware and software, more people can harness data processing for their own use without hiring a programmer to do it.

For them, getting "stuck" in Python phase will work just fine. Yes, they will not have exact knowledge how C implements low-level memory allocation. They may newer write OOP code, define own class (just use OOP libraries). But they will be solving problems which "career programmer" cannot solve, because has no understanding of the problem domain.

Python has uncanny ability to get stuck in your brain and be intuitive even if you haven't used it for couple months. Most other languages have quirks, and are unforgiving: after couple months pause, you need to re-learn language idioms again (best, or worst, example of this phenomenon being Perl).

Python can be your first language, and also language to learn OOP, and also your bash, and also web apps language. Of course, as professional career programmer, you will have to learn many languages during your career, but not everyone has to be career programmer to have use of little programming here and there.

---

### Post by slavik on 2007-11-01
> **pmasiar said:**
> But they will be solving problems which "career programmer" cannot solve, because has no understanding of the problem domain.

Either you were thinking much faster than you were typing or are you saying that someone who knows some python can solve a problem that a professional C programmer can't?

---

### Post by pmasiar on 2007-11-01
Yes. Because biologist *understands* what data are telling, and can see errors where programmer (ie. me) cannot see them - results looks OK but they don't make *biological* sense, bug is hiding somewhere.

Of course C programmer *can* solve this problem, but only after lots and lots of training and explaining, which might not be worth if biologist can hack together less effective solution in Python faster than teaching C coder to do it "properly" in C (or even in Python).

It is a language barrier too. Biologist use many of same words programmers use, but with completely different meaning, sometimes making funny misunderstandings. Ie for biologist, "buffer" is solution (water), "emty buffer" is pour it out to the sink. "Vector" is ie virus (hah! virus!) which spreads the disease, or a plasmoid if you want to infect a bacteria to modify it. Etc etc.

---

### Post by slavik on 2007-11-01
words might be the same, but context is completely different.

Also, most professional programmers either have biology as a minor or studied it at length if they want to become programmers in the biological field.

If you are a physicist getting people to mars, you can use FORTRAN to solve the task (better than a C programmer who doesn't know physics). But if you are a physicist who has no idea of parallelism (whereas a C programmer with physics training should) then forget about coding your problem, just give the formulas to the coder.

Biologists understand biology, not data structures or parallel algorithms (unless they are really interested in computer science).

---

### Post by CptPicard on 2007-11-01
I need to second pmasiar's argument here. My main project at the moment is doing sports betting analysis software for my friend's business, and while we make a great team, we constantly have trouble communicating both ways as he is not a programmer and I am not a sports betting guru.

Figuring out what exactly it is he needs done can sometimes be a challenge, as I have no domain knowledge and he is a fast explainer ;). But he's bright enough to "just give me the math" and maybe some very high-level pseudocode of what he thinks *should* happen, and we go from there -- the optimization of implementation is my problem.

---

### Post by slavik on 2007-11-01
> **CptPicard said:**
> I need to second pmasiar's argument here. My main project at the moment is doing sports betting analysis software for my friend's business, and while we make a great team, we constantly have trouble communicating both ways as he is not a programmer and I am not a sports betting guru.

Figuring out what exactly it is he needs done can sometimes be a challenge, as I have no domain knowledge and he is a fast explainer ;). But he's bright enough to "just give me the math" and maybe some very high-level pseudocode of what he thinks *should* happen, and we go from there -- the optimization of implementation is my problem.
exactly, if your friend knew a little bit of python, he still would not be able to solve the problem.

you need to learn less than your friend to be able to solve the problem :)

---

### Post by CptPicard on 2007-11-01
Actually, it is really helpful that Python is readable even by non-programmers as soon as I get rid of my love for extensive use of list comprehensions and economy of temporary variables... it means that I can isolate some piece of logic into a function and ask him if he thinks it looks correct... just a double-check. I am almost certain that when it comes to our simpler data mangler scripts, he actually could write them, but there of course really is no point when he can pay me to.

He used to do this stuff on Excel on which he is quite a wizard, but of course this stuff moved beyond Excel's capabilities a few years ago already. It just *is* great to have a user who is not a complete n00b but who can actually be told to pipe stuff from one program to another instead of me coding some extra switch for the purpose...

Our more intense number-crunchers are in Java and C though, so the Python argument is limited in scope...

---

### Post by wolfbone on 2007-11-01
[QUOTE="slavik"]Biologists understand biology, not data structures or parallel algorithms (unless they are really interested in computer science).[/QUOTE]

Many are!

[http://bioinformatics.org/](http://bioinformatics.org/)

[QUOTE="slavik"]you need to learn less than your friend to be able to solve the problem [/QUOTE]

That may be true in sports betting but it's generally a lot easier for scientists to acquire a sufficient grasp of programming and comp. sci. for their purposes than it is for programmers to acquire a sufficient understanding of research topics in the sciences. And scientists frequently do of course: cmbfast was written by physicists, kenzo by a mathematician, atlas by a mathematician, geant by physicists (and computer scientists) etc.

---

### Post by CptPicard on 2007-11-01
Actually it is my impression that most bioinformaticists are computer scientists applying themselves to biology, as you really need a solid background in algorithms in order to get efficient implementations...

For other scientists, what's better than having for example a scripting interface to some toolkit written by a programmer? It's the job for the non-programmer scientist to learn new stuff about his own field so he has to be able to pose novel "questions" to his data, but the general data processing bit can certainly be implemented by someone who knows that part better...

---

### Post by slavik on 2007-11-01
That is also the reason why there are languages like FORTRAN and Haskel. If a Physicist needs to calculate complex equations, Python will be one of the last languages that he is going to even think about (along with Perl, C, and other languages some universities teach first).

---

### Post by wolfbone on 2007-11-01
FORTRAN?!!! Good grief! Is this a vintage programming forum? ;-)

[http://www-teaching.physics.ox.ac.uk/computing/ProgrammingResources/programming.html](http://www-teaching.physics.ox.ac.uk/computing/ProgrammingResources/programming.html)
[http://ph-sft.web.cern.ch/ph-sft/](http://ph-sft.web.cern.ch/ph-sft/)
[http://geant4.web.cern.ch/geant4/support/download.shtml](http://geant4.web.cern.ch/geant4/support/download.shtml)

---

### Post by LaRoza on 2007-11-01
> **wolfbone said:**
> FORTRAN?!!! Good grief! Is this a vintage programming forum? ;-)


Fortran was made in the 50's, but has changed since then. I use Fortran 77, although it is old, it is powerful. The new editions Fortran 90/95 are much different, and there is Fortran 2003 and Fortran 2008 is in the works.

The newer versions are very modern, I hear. I use Fortran 77, even though I know of the newer editions.

Also, age doesn't really mean anything. C is from the 70's, and is still a widespread language.

---

### Post by Paul820 on 2007-11-01
Wow LaRoza, how many languages do you use? I only use one at the moment but i am thinking of giving python a go. I will hopefully write some scripts for blender or something like that.

---

### Post by LaRoza on 2007-11-01
> **Paul820 said:**
> Wow LaRoza, how many languages do you use? I only use one at the moment but i am thinking of giving python a go. I will hopefully write some scripts for blender or something like that.

Look in my wiki, I am not equally skilled with all of them, and some I have just barely studied.

I use PHP, ECMAScript, and Python most often, but actively use C, Fortran 77, Assembly, C++ and Java. I play with Ada, Ruby, Perl and a few others. I am working (somewhat) at Lisp now. I am not studying programming as part of any course, just something I enjoy.

-EDIT I am not that old, still a teenager in fact.

---

### Post by CptPicard on 2007-11-01
> **LaRoza said:**
> 
-EDIT I am not that old, still a teenager in fact.

Whoah.. props. I thought you're about my age (about you +10 years) :D

---

### Post by Paul820 on 2007-11-01
I've bookmarked your wiki for when i start with python. That's a big list of languages you are using :)

---

### Post by LaRoza on 2007-11-01
> **Paul820 said:**
> I've bookmarked your wiki for when i start with python. That's a big list of languages you are using :)

"Using" should be used loosely. As much as I enjoy working with Assembly, I don't really use it for anything. The only languages I really use for a purpose are PHP, Python, ECMASCript, and C.

I use the others for fun.

---

### Post by wolfbone on 2007-11-01
[QUOTE=LaRoza]Also, age doesn't really mean anything..[/QUOTE]

It certainly doesn't - which is why smart people hate Fortran but love Lisp ;-) (which doesn't really belong in the interpreted language section of your wiki btw) :)

---

### Post by LaRoza on 2007-11-02
> **wolfbone said:**
> It certainly doesn't - which is why smart people hate Fortran but love Lisp ;-) (which doesn't really belong in the interpreted language section of your wiki btw) :)

Smart people don't hate anything. I am working with Lisp also.

Java doesn't belong in the compiled section either, but the separations are used loosely.

---

### Post by wolfbone on 2007-11-02
Smart people don't make casual generalisations :) and there are - at least - two ways of saying you hate something:

[QUOTE="Albert Einstein"]Heroism on command, senseless violence, and all the loathsome nonsense that goes by the name of patriotism - how passionately I hate them! [/QUOTE]

[QUOTE="Richard Feynman"]I love only nature, and I hate mathematicians.[/QUOTE]

One of the above sentences reads as though it had a following ";-)". Like mine.

Why does Java not belong in the compiled section?

---

### Post by pmasiar on 2007-11-02
> **CptPicard said:**
> Actually it is my impression that most bioinformaticists are computer scientists applying themselves to biology, as you really need a solid background in algorithms in order to get efficient implementations...

In my experience, opposite is true. I have hard time to learn "Fundamentals of cellular, molecular and developmental biology" (but enjoyed it tremendously), which is Bio120 level. In my experience, many (not all) biologists/medics are able to learn enough CompSci by themselves to be able to make you first draft database design and understand enough so you can explain them constraints, shortcuts, and consequences of design decisions. Smartest of them are hardcode hackers enough to write C libraries we use.

> **slavik said:**
> If a Physicist needs to calculate complex equations, Python will be one of the last languages that he is going to even think about (along with Perl, C, and other languages some universities teach first).

... but Python might be her good choice if she is aware of numpy, which is C library. RPy for statistics in R is big in gene research. Etc.

I don't know any physicists personally, but some biologists/medics I interact daily are experienced enough programmers to hack Java/Perl web apps. best .NET expert I know is a MD. Even Perl CGI module was writtem by [Lincoln Stein, MD](http://www.cshl.edu/public/SCIENCE/stein.html). Where would be Perl without CGI module?

So I would recommend any budding CompSci major to minor in some science, and if possible, reconsider: major in the science, and minor in CompSci.

---

### Post by slavik on 2007-11-02
numpy might be nice, but Haskel is inherently more powerful for a scientist, because they can think in terms of functions. Most comp sci majors learn to think in serial code (one instruction after another), sometimes this is a huge hinderance (based on the problem).

---

### Post by LaRoza on 2007-11-02
> **slavik said:**
> numpy might be nice, but Haskel is inherently more powerful for a scientist, because they can think in terms of functions. Most comp sci majors learn to think in serial code (one instruction after another), sometimes this is a huge hinderance (based on the problem).

Perhaps learning Lisp should be mandatory for all CS majors.

---

### Post by CptPicard on 2007-11-02
> **LaRoza said:**
> Perhaps learning Lisp should be mandatory for all CS majors.

I agree with this wholeheartedly, it made me a better programmer. My favoured dialect for this character-building would be Scheme to be exact, Common Lisp is a bit of a monster in its complexity...

---

### Post by LaRoza on 2007-11-02
> **CptPicard said:**
> I agree with this wholeheartedly, it made me a better programmer. My favoured dialect for this character-building would be Scheme to be exact, Common Lisp is a bit of a monster in its complexity...

Isn't Scheme meant to be for learning? I am working on Common Lisp now, and just started reading up on Haskell. In fact, I just downloaded Hugs and installed it to my flash drive, and played around with it. Looks very useful for math.

(I am at school, on break, and using their computers)

---

### Post by CptPicard on 2007-11-02
> **LaRoza said:**
> Isn't Scheme meant to be for learning?

Yep, it is. And it's not just for learning, I feel that Scheme's intentional simplicity is a blessing really. You can implement your own little library of functions you use often, and then you already have a pretty powerful platform. It's fascinating how you get all sorts of programming paradigms out of Scheme's minimalist underpinnings; for example message-passing OOP is a simple matter of creating a closure you can pass around and that can be called with a message symbol and parameter...

May I suggest you continue your language explorations with Prolog? ;) Now that's the one nasty language I never managed to get anything done in, I just can't think of things in terms of the matching system although it's supposedly "obvious"... took me a long time to figure out how to for example manipulate lists declaratively, and I still don't quite feel comfortable with it...

---

### Post by slavik on 2007-11-02
One of the most powerful things Prolog can do is constraint programming ... ie: give me a list of 9 numbers so that such and such is in such place and none are the same ... easiest way to write a sudoku solver ;)

it would be faster to write the code and the code would be faster than what you could come up with in most (if not all) other languages.

---

### Post by LaRoza on 2007-11-02
> **CptPicard said:**
> Yep, it is. And it's not just for learning, I feel that Scheme's intentional simplicity is a blessing really.

I wasn't demeaning it, just asking. "Simple is better than complex" -- Python

I will look into it.

---

### Post by CptPicard on 2007-11-02
> **slavik said:**
> One of the most powerful things Prolog can do is constraint programming ... ie: give me a list of 9 numbers so that such and such is in such place and none are the same ... easiest way to write a sudoku solver ;)


It is fundamentally a controlled depth-first search among the predicates, with the matching rule. Why I would want to express all of my problems in those terms, is beyond me... it's way too easy to just make everything explode in your face if you don't provide all the neccessary constraints, and debugging that is just nasty.

But then again, it was invented by the French, so what do you expect.. :p

---

### Post by slavik on 2007-11-02
> **CptPicard said:**
> It is fundamentally a controlled depth-first search among the predicates, with the matching rule. Why I would want to express all of my problems in those terms, is beyond me... it's way too easy to just make everything explode in your face if you don't provide all the neccessary constraints, and debugging that is just nasty.

But then again, it was invented by the French, so what do you expect.. :p

There's a problem with your statement ... care to guess what? It's the 'all' word. Not all problems can be solved with constraints, but those that can, it is much easier to use Prolog for them than most other languages.

Don't forget, Sudoku is NP Complete, so you have to build a tree and traverse it depth first. You just have to be smart about which paths to go down and Prolog has that "smartness" built in.

---

### Post by tyoc on 2007-11-02
Side note, I personally think that being or not being to compiler or interpreted is about the implementation of a language, the language is only a lang, not an implementation that is restricted to how machines work.

---

### Post by LaRoza on 2007-11-02
> **tyoc said:**
> Side note, I personally think that being or not being to compiler or interpreted is about the implementation of a language, the language is only a lang, not an implementation that is restricted to how machines work.

?

Even if that made sense, it would be way OT.

---

### Post by CptPicard on 2007-11-02
> **slavik said:**
> Not all problems can be solved with constraints, but those that can, it is much easier to use Prolog for them than most other languages.

And the Prolog-applicable set is so limited that I really don't want to start building my computational model on top of the scaffolding provided by Prolog :)

> 
Don't forget, Sudoku is NP Complete, so you have to build a tree and traverse it depth first. You just have to be smart about which paths to go down and Prolog has that "smartness" built in.

Yeah, but an imperative forward-checking recursion is even more clear a solution IMO. Prolog does not quite fulfill its promise of being the general purpose next generation AI language where you just tell the computer "what to do".. you still need to understand you're guiding a depth-first search with all the red cuts and whatnot. So it's not even all that smart in worst case, and this is even less obvious than it would be in the imperative case.

---

### Post by Fbot1 on 2007-11-02
> **LaRoza said:**
> Perhaps learning Lisp should be mandatory for all CS majors.

That seems pretty pointless to me.

---

### Post by LaRoza on 2007-11-02
> **Fbot1 said:**
> That seems pretty pointless to me.

"Perhaps" means that it isn't a belief I hold dear. Teaching someone 4 imperative languages is pointless. Anyone can learn syntax, then look up the standard library. Learning a new paradigm will help the programmer in all aspects of programming. I could have state Haskell, which I am using right now, instead of Lisp. Lisp, actually, it's dialects, would be good for a new student to study. Learning 4 ways to write the same code is not as useful as learning 2 ways to view a problem.

---

### Post by CptPicard on 2007-11-02
> **Fbot1 said:**
> That seems pretty pointless to me.

Why so? Why do you feel that the insights gained from Lisp or its dialects are not profoundly educational?

Do you know any Lisp yourself?

---

### Post by pmasiar on 2007-11-02
> **LaRoza said:**
> Perhaps learning Lisp should be mandatory for all CS majors.

In fact, until recently Scheme was standard **intro** language in MIT (recently replaced by Python). Joel Spolsky (I am too lazy to find the link :-) ) argues that this is for worse: Lisp weeded out people who cannot handle abstraction.

---

### Post by LaRoza on 2007-11-02
> **pmasiar said:**
> In fact, until recently Scheme was standard **intro** language in MIT (recently replaced by Python). Joel Spolsky (I am too lazy to find the link :-) ) argues that this is for worse: Lisp weeded out people who cannot handle abstraction.

I can't find the link either, but similar points are made in this article: [http://www.cs.virginia.edu/~weimer/2007-615/reading/ThePerilsofJavaSchools.html](http://www.cs.virginia.edu/~weimer/2007-615/reading/ThePerilsofJavaSchools.html)

---

### Post by Fbot1 on 2007-11-02
> **CptPicard said:**
> Why so? Why do you feel that the insights gained from Lisp or its dialects are not profoundly educational?

Do you know any Lisp yourself?

I know Common Lisp and Scheme. I really don't feel that Lisp is all that special and definitely not worth being required, there's already a lot of BS classes.

---

### Post by LaRoza on 2007-11-02
> **Fbot1 said:**
> I know Common Lisp and Scheme. I really don't feel that Lisp is all that special and definitely not worth being required, there's already a lot of BS classes.

You don't see the value of learning more than one paradigm? All the experts do. Even me, a lowly beginner understands the importance.

How about Haskell then? It is truly functional, unlike Lisp.

I am starting to think there is trolling amiss.

---

### Post by Fbot1 on 2007-11-02
> **LaRoza said:**
> You don't see the value of learning more than one paradigm? All the experts do. Even me, a lowly beginner understands the importance.

How about Haskell then? It is truly functional, unlike Lisp.

I am starting to think there is trolling amiss.

Maybe if they were really different but as far as I can tell they're not. You're much better off taking a math class.

---

### Post by LaRoza on 2007-11-02
> **Fbot1 said:**
> Maybe if they were really different but as far as I can tell they're not. You're much better off taking a math class.

That explains it. You don't know Lisp or Haskell well enough to really discuss it. Functional programming is very different from imperative programming. Knowing the general syntax of Lisp is missing the point.

---

### Post by Fbot1 on 2007-11-02
> **LaRoza said:**
> That explains it. You don't know Lisp or Haskell well enough to really discuss it.

what ever

> **LaRoza said:**
> Functional programming is very different from imperative programming.

not really

---

### Post by pmasiar on 2007-11-03
> **Fbot1 said:**
> not really

You just proved beyond reasonable belief you lack not only self-awareness, but also a clue.

But as you said, whatever. Good luck learning more, you have a long way ahead.

---

### Post by handzmonkey on 2007-11-03
Well what OS do you want to program for.  Cause if its Windows based your best bet is C++.

---

### Post by LaRoza on 2007-11-03
> **handzmonkey said:**
> Well what OS do you want to program for.  Cause if its Windows based your best bet is C++.

No, Python, VB, Perl, Ruby, C, and almost all other languages work very well on Windows. Python in particular has its very own MS implementation, so you have a very powerful language there.

---

### Post by pmasiar on 2007-11-03
> **handzmonkey said:**
> Cause if its Windows based your best bet is C++.

And of course on Windows, language with most features, MSFT's own, is not C++ but C#.

It just tells you how much (or how little) you can trust advice of random strangers. You always need to double-check.

---

### Post by LaRoza on 2007-11-03
> **wolfbone said:**
> 
Why does Java not belong in the compiled section?

Because it is not compiled like C and others. It is compiled to byte code, which is then interpreted by the JVM. It is just actually an interpreted language.

I am catorgorizing the languages by the steps needed to run it, Java requires a "compile" stage.

---

### Post by CptPicard on 2007-11-03
> **LaRoza said:**
> It is compiled to byte code, which is then interpreted by the JVM. It is just actually an interpreted language.


Actually, it's compiled to byte code, and then the bytecode is JIT-compiled to native code, which is then executed. :)

---

### Post by Fbot1 on 2007-11-03
> **LaRoza said:**
> No, Python, VB, Perl, Ruby, C, and almost all other languages work very well on Windows. Python in particular has its very own MS implementation, so you have a very powerful language there.

I don't think handzmonkey ever said that they didn't work. 

> **pmasiar said:**
> And of course on Windows, language with most features, MSFT's own, is not C++ but C#.

It just tells you how much (or how little) you can trust advice of random strangers. You always need to double-check.

You don't know the reason so you really shouldn't attack their credibility, it makes you look stupid.

> **CptPicard said:**
> Actually, it's compiled to byte code, and then the bytecode is JIT-compiled to native code, which is then executed. :)

I've seen either done.

---

### Post by CptPicard on 2007-11-03
> **Fbot1 said:**
> 
I've seen either done.

Sure, it can be done both ways and in the old days it was, but JIT-compilation is the modern, common way to do it...

---

### Post by LaRoza on 2007-11-03
> **Fbot1 said:**
> I don't think handzmonkey ever said that they didn't work. 



You don't know the reason so you really shouldn't attack their credibility, it makes you look stupid.



I've seen either done.

0. True, but that wasn't what I responding to. I was responding to the statement that C++ was the way to go. There are better Windows languages out there.

1. That poster has decades of experience, he knows what he is talking about

2. JIT is the way to go, I omitted that mainly because I forgot :) and it isn't a step explicitly done by the programmer

---

### Post by pmasiar on 2007-11-03
> **Fbot1 said:**
> You don't know the reason so you really shouldn't attack their credibility, it makes you look stupid.

Sadly I cannot say about that you are stupid, it would cost me permanent ban.

So yes, you are much smarter than me, and know it all. Enjoy, forum admins won!

---

### Post by CptPicard on 2007-11-03
Some people simply have more credibility than others, and some people are better at making themselves look stupid than others. It's pretty obvious for anyone with half a clue to tell which is which, so don't sweat it pmasiar, although I sympathize with you fully and understand the annoyance -- just consider it to be *so* below you :)

---

### Post by TheHustle on 2009-07-24
[LEFT]I agree, go with something easy at first.  I was thrown into C++ when I started work and had to modify someones (Not Commented) code and it was hell.  It took a few months before I could do anything of intirest.  Go from the bottom up and focus on making small applications that will build up your knowledge of the language whatever you choose.
[/LEFT]

---

### Post by Mirge on 2009-07-24
Thread necromancer......

CptPicard you've been here a long time :).

---

### Post by CptPicard on 2009-07-24
> **Mirge said:**
> 
CptPicard you've been here a long time :).

Too long a time. This place is actually much quieter these days compared to the time of the Language Wars... epic they were... (read back on this thread for example)

---

### Post by Can+~ on 2009-07-24
> **CptPicard said:**
> Too long a time. This place is actually much quieter these days compared to the time of the Language Wars... epic they were... (read back on this thread for example)

Or go for the Why I Love/Hate _________ on the recurring discussions, that was a super merge of old topics.

I can't believe I posted to this 2 years ago.

---

### Post by JordyD on 2009-07-24
> **Mirge said:**
> Thread necromancer......

Anyone else notice an increase in these, or am I just crazy?

---

### Post by CptPicard on 2009-07-24
> **JordyD said:**
> Anyone else notice an increase in these, or am I just crazy?

Well, it is a FAQ (that is covered in the stickies, but people never read them) so it gets searched and people answer before looking at the timestamp (they never do that either)

---

### Post by JordyD on 2009-07-24
> **CptPicard said:**
> Well, it is a FAQ (that is covered in the stickies, but people never read them) so it gets searched and people answer before looking at the timestamp (they never do that either)

Well, yes, but has it *increased* lately? Or have I just been reading the forums more?

---

### Post by Can+~ on 2009-07-24
I also noticed an increase of old post resurrection. It's like some kind of [Eternal September]("http://en.wikipedia.org/wiki/Eternal_September")?

---

### Post by Mirge on 2009-07-24
> **Can+~ said:**
> I also noticed an increase of old post resurrection. It's like some kind of [Eternal September]("http://en.wikipedia.org/wiki/Eternal_September")?

lol I remember just reading that link... CptPicard posted it 2 years ago I think? Regardless, it was pretty funny.

---

### Post by slavik on 2009-07-24
This thread has outlived its usefulness.

---

