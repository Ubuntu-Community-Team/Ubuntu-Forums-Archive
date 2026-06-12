---
title: "[Recommend] Which Next Language Suits My Skill Set?"
date: 2008-08-19
forum: Programming Talk
---

### Post by loganwm on 2008-08-19
A few of the forum regulars may already know that I've been learning C and C++ and I can safely say the I've got the fundamentals down, and I've messed around with some algorithms for the sake of trying them.

Right Now my programming skill set consists of:
Lua [very well]
C++ [fundamental]
C [intermediate]

I'd like to get another language under my belt, and I've been told by many here that it's handy to know {insert debated scripting language name here} but I'd like to get some opinions.

Right now I've got the following in consideration, but I am OPEN MINDED as to what else I could choose to learn:
Python
Perl
Bash [although I'm more considering this in addition to whatever else I choose to learn]

Based on my current experience and exposure levels, which language can you recommend? Please give me support with a recommendation, as I'd really like to have a picture of what I want to learn before I start.

[SIZE="1"]Let the language wars commence :).[/SIZE]

---

### Post by CptPicard on 2008-08-19
Python, no contest ;) It's popular (which actually *is* a proper argument), lots of libs, easy language that has more to it than immediately meets the eye when you get to know it and learn what the duck typing genericity actually means and how generators etc work... easy to learn, easy to write, conceptually strong, scales up and down surprisingly well (you don't feel like you've got training wheels on later on)...

Ruby is another alternative but IMO it's more niche and too OOP.

---

### Post by stevescripts on 2008-08-19
Everyone who programs should spend a least a bit of time with some form of lisp or scheme ... ;)  (regardless of current skillset)

Just another $.02...

Steve

---

### Post by loganwm on 2008-08-19
> **stevescripts said:**
> Everyone who programs should spend a least a bit of time with some form of lisp or scheme ... ;)  (regardless of current skillset)

Just another $.02...

Steve

Much thanks to you and CptPicard for the responses. I don't plan on starting whichever language I pick until I get some more feedback in this thread. (preferably)

Onto python, I understand that it's scripting, so therefore, it's not compiled? or is it?

Ruby I will write off for now for the simple reason that OOP is what steers me towards C rather than C++, I want to take on OOP eventually, but now is not the time for me :)

LISP - I've heard of, but not familiar with.

Scheme - I've honestly heard nothing about.

I don't plan on getting anywhere near tackling Java right now (mainly because it doesn't fit my current plan of picking up a handy workhorse scripting language) But does anyone have any opinions on Java. Just out of curiosity?

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> 
Onto python, I understand that it's scripting, so therefore, it's not compiled? or is it?

It's bytecode compiled on the fly and then the bytecode is executed and cached.

> 
Ruby I will write off for now for the simple reason that OOP is what steers me towards C rather than C++, I want to take on OOP eventually, 

Well, it's not as bad in Ruby as it is in C++... in statically typed languages the OOP design requirements really trip up beginners and keep them from actually achieving anything before they become knowledgeable enough in the design patterns needed to express anything. In my view, OOP is highly overrated anyway.

> 
LISP - I've heard of, but not familiar with.

Scheme - I've honestly heard nothing about.

Both are "kinds of lisp", and stevescripts is correct, although opinions vary whether they are beginner languages or not. They may be; personally they started enlightening me only after I knew a lot of stuff already so I could see exactly why, where and how they really connect to everything I know. Of course, they are the best languages once you get to that part of your development ;)

> 
I don't plan on getting anywhere near tackling Java right now (mainly because it doesn't fit my current plan of picking up a handy workhorse scripting language) But does anyone have any opinions on Java. Just out of curiosity?

I would say you're better off learning Java once you feel like you want it instead of C++. Keep C as your compiled lower-level language. Java is a kind of ... uh... "cleaned-up C++" with garbage collection and other niceties. It's a good corporate workhorse and I use it daily but I still do not consider it awfully "special" if you know what I mean :) -- "it works, it doesn't make me a better person".

---

### Post by jimi_hendrix on 2008-08-19
java opinion: easy to learn and use...and taught in many highschools

---

### Post by ByteJuggler on 2008-08-19
> **loganwm said:**
> M
Onto python, I understand that it's scripting, so therefore, it's not compiled? or is it?


It's bytecode compiled/interpreted, so a bit like Java in that way. There's also several other flavours floating about, including a .Net native bytecode compiled version called Iron Python.  

While Python is a very capable scripting langauge, it would be wrong to think of it as only a scripting language, as you can do a lot more in it than just scripting.  Several parts of Ubuntu's admin tools are in fact written in Python, for example, as is a nice Python IDE, [SPE]("http://pythonide.blogspot.com/").    Another example is the Exaile music player for Ubuntu, which is written in Python.  I'm currently doing the [Python Challenge]("http://www.pythonchallenge.com/"), up to level 17.  If you do this, you'll see just how powerful Python is.  Some of the solutions to these problems are really pains in the neck in other languages, but end up being a couple of succinct lines of code in Python.

---

### Post by danbuter on 2008-08-19
Ruby is a great way to get a handle on OOP. OOP is VERY easy in Ruby. I can't imagine trying to learn OOP in C++.

---

### Post by jimi_hendrix on 2008-08-19
question...what makes lisp/scheme so special that so many people are "enlightened" by it...if its worth looking at then it might be something for me to do in my last 2 weeks of summer (along with blindly asking if it is at all feasible for me to make my own language)

---

### Post by ByteJuggler on 2008-08-19
> **loganwm said:**
> Ruby I will write off for now for the simple reason that OOP is what steers me towards C rather than C++, I want to take on OOP eventually, but now is not the time for me :)

Just an aside here: Both Ruby and Python are IMHO subtantially (might even say "infinitely") better suited to teaching/learning "true" OO, almost automatically, for learning programmers.  You'll probably learn about it without trying using either Ruby or Python, with none of the C++ downsides... :)

---

### Post by jimi_hendrix on 2008-08-19
> **danbuter said:**
> Ruby is a great way to get a handle on OOP. OOP is VERY easy in Ruby. I can't imagine trying to learn OOP in C++.

C# is also great for learning OOP...ive found that it is only good for form programming and interacting with the internet later on though since it feels to structured to dig into the machine (not that i have done this yet...its just a feeling)

---

### Post by stevescripts on 2008-08-19
Having found a couple of more minutes ... re scheme - see [http://mitpress.mit.edu/sicp/]("http://mitpress.mit.edu/sicp/")

Steve
(who also isn't sure that it is exactly for beginners, but doing even parts
of the SICP will make you a better programmer...)

---

### Post by ghostdog74 on 2008-08-19
> **loganwm said:**
> 
Right Now my programming skill set consists of:
Lua [very well]
C++ [fundamental]
C [intermediate]
ask yourself how much do you really know about C/C++. My recommendation: Go into the advance stage.

---

### Post by loganwm on 2008-08-19
> **jimi_hendrix said:**
> java opinion: easy to learn and use...and taught in many highschools

Another reason I'm considering holding off on Java is it's my AP Computers Course next year, so I figure by then, I'll be ready for it.

Python sounds like the most likely next choice for me from what I've heard here, however I'm still open for suggestions of any sort.

Here's my current RoadMap for my longterm programming goals:

[1] Lua
[2] C
[3] Python
[4] Bash
[5/6] Java
[5/6] Lisp
[7] PHP/Web fundamentals

I could factor in other languages depending on how long each takes to reach an understandable level.

Keep the suggestions rolling. I'm reading all of the. And I want to personally thank all of you.

---

### Post by loganwm on 2008-08-19
> **ghostdog74 said:**
> ask yourself how much do you really know about C/C++. My recommendation: Go into the advance stage.

I want a lightweight low maintenance scripting language to help in my further expansion of my C.

C++ is atrocious in my opinion, but I would rather keep from being a "blub" as we've so eloquently begun saying :)

---

### Post by ghostdog74 on 2008-08-19
> **loganwm said:**
> 

Here's my current RoadMap for my longterm programming goals:

[1] Lua
[2] C
[3] Python
[4] Bash
[5/6] Java
[5/6] Lisp
[7] PHP/Web fundamentals
actually, since you have set your goals, learning what next really doesn't matter, unless you have a life and death decision to make.

---

### Post by CptPicard on 2008-08-19
> **jimi_hendrix said:**
> question...what makes lisp/scheme so special that so many people are "enlightened" by it...if its worth looking at then it might be something for me to do in my last 2 weeks of summer (along with blindly asking if it is at all feasible for me to make my own language)

Interestingly, if you want to make your own language, you really need to look at Lisp, because Lisp is a kind of meta-language that makes it easy to describe other languages ... that is, to create your own concepts. This is why Lisp is enlightening... it is very minimal in many ways, especially Scheme, but it is also semantically powerful enough to very easily incorporate pretty much all other languages and paradigms. It really lets you see a lot of stuff differently but as sides of the same coin... it's like zen or something :)

> **loganwm said:**
> 
C++ is atrocious in my opinion, but I would rather keep from being a "blub" as we've so eloquently begun saying :)

It's ok to say C++ is atrocious if you have something to back up the opinion :) I've tried liking C++ but just can't... I'm not blub if I say so because it comes from experience...

---

### Post by loganwm on 2008-08-19
> **ghostdog74 said:**
> actually, since you have set your goals, learning what next really doesn't matter, unless you have a life and death decision to make.

Well they're not set in stone yet. I want to learn in a way where I can continue building in a useful manner.

And I have a limited view on other languages without the views of those who use them.

---

### Post by ghostdog74 on 2008-08-19
> **loganwm said:**
> 
C++ is atrocious in my opinion, but I would rather keep from being a "blub" as we've so eloquently begun saying :)
why do you care what other people say? A blunt sword under the hands of a skillful swordsman can kill too.

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> 
[7] PHP/Web fundamentals


No, web apps... u're doin dem rong. Python extends much more nicely to the web space, no need to learn PHP.

---

### Post by meanburrito920 on 2008-08-19
@jimi_hendrix-- Lots of people find lisp enlightening because it's structure is fundamentally different than most languages. While most languages are oop/procedural, lisp is functional. Wikipedia actually has some nice articles on functional programming. You should check it out.

As for the actual thread topic, I would suggest python. Python doesnt force you into any programming style, so you can put of oo for as long as you want. It also has the best standard library of all scripting languages in its class. As for bash, dont bother going into depth with bash unless you have a specific application that you need to use it for. For the most part, it is easier to use python to accomplish the same task.

Just my $0.02

---

### Post by loganwm on 2008-08-19
> **ghostdog74 said:**
> why do you care what other people say? A blunt sword under the hands of a skillful swordsman can kill too.

It's not what people say that I'm concerned about, its a comparison of my willingness to keep an open mind compared to "blub-iness" of having the narrow view that what you see is the only reasonable insight.

@CptPicard

Regarding PHP, I'm more or less (as a side project) interested in how it works, not too deeply, but the principles behind it.

---

### Post by jimi_hendrix on 2008-08-19
can u guys point me to a good site for lisp learning (and your advised varient of it for me to learn) and a site for making my own language (google hasnt helped with this)

btw burrito that unix war thing was funny

---

### Post by meanburrito920 on 2008-08-19
[http://gigamonkeys.com/book/](http://gigamonkeys.com/book/) is the tutorial I used for Common Lisp.

GIYBF.

---

### Post by ghostdog74 on 2008-08-19
> **meanburrito920 said:**
>  As for bash, dont bother going into depth with bash unless you have a specific application that you need to use it for.

you haven't had an opportunity to be in a situation that needs bash yet. Therefore, i suggest you don't comment on it.
> 
 For the most part, it is easier to use python to accomplish the same task.

Just my $0.02

really? show me an easy way to do a process listing in Python. No, don't use system call to ps.

---

### Post by loganwm on 2008-08-19
> **jimi_hendrix said:**
> can u guys point me to a good site for lisp learning (and your advised varient of it for me to learn) and a site for making my own language (google hasnt helped with this)

btw burrito that unix war thing was funny

I suppose in theory you would need to design your language based on a low level language and either A) interpret it or B) build a compiler

Look into how the Java VM works. It's actually pretty spectacularly genius. Ableit a bit less efficient than some other languages.

---

### Post by mike_g on 2008-08-19
> C++ is atrocious in my opinion, but I would rather keep from being a "blub" as we've so eloquently begun saying
And why do you find it attrocious? there seems to be this catchy C++ bashing thing on this board, which while minorly entertaining, IMO is not really justified. Sure stl make things complicated and not everyone likes the obligatory verbose code that comes with OOP. Still, if thats the case theres nothing stopping you procedural code, using some of C++'s basic, but useful features. Such as: new/delete, function overloading, defalt parameters and predefined boolean stuff.
 
While it would definely be worth learning a high level language such as python, if you want to become proficient with C it takes time so stick with it as well. Its been around 2years since I started with the language and I'm still learning new stuff all the time. IMO your better off being good with one or two languages, then have a go at many, but not be able to do much with them.

Edit: wow all these posts in such little time.

---

### Post by CptPicard on 2008-08-19
> **meanburrito920 said:**
> Lots of people find lisp enlightening because it's structure is fundamentally different than most languages. While most languages are oop/procedural, lisp is functional.

Actually I need to point out that this confuses two features of lisp by seemingly making them into one. There are functional programming languages that do not have the metaprogramming facilities Lisp has (Haskell), which stem from its homoiconic structure where code is data and data can be eval'ed as code.

Lisp code is structured as nested lists which actually is already an AST representation. These lists can be manipulated at will *in any way* by other Lisp functions. You can even build code at runtime and trivially eval it, or compile it, or whatever. Lisp really can be turned into anything at will, and offers essentially a semantic superset of anything in other languages, so all other languages' features can be covered at ease (broadly speaking). It's true that you can write an interpreter for any Turing-complete language in any other Turing-complete language, but Lisp conquers the other languages from the top down, where the other languages it has to be done from bottom up, at great cost in construction of missing abstraction.

Functional programming is a nice way of modelling a lot of interesting stuff... and in my view both a more abstract and natural and theory-friendly way of modelling, too, 

Functional and OOP programming also are not mutually exclusive, actually OOP is an interesting subset of functional programming. CLOS is a really nice OOP system for Common Lisp, and in Scheme you trivially get objects by returning lambdas which grab environment for object state.


> **loganwm said:**
> 
Regarding PHP, I'm more or less (as a side project) interested in how it works, not too deeply, but the principles behind it.

PHP may have been nice in the 90s, but these days we no longer embed code in HTML :p

---

### Post by loganwm on 2008-08-19
> **mike_g said:**
> And why do you find it attrocious? 
.. 
While it would definely be worth learning a high level language such as python, if you want to become proficient with C it takes time so stick with it as well. Its been around 2years since I started with the language and I'm still learning new stuff all the time. IMO your better off being good with one or two languages, then have a go at many, but not be able to do much with them.

Edit: wow all these posts in such little time.

My opinion of C++ is essentially that I enjoy the implementation of C a bit more, so when I attempt to write in C++, I prefer to fall back on C style and standards because they seem to make more sense to me.  I just don't like it because, if I wanted to write code that looks and functions like C, I would honestly rather work with C. But I am not entirely against using C++, I just see it as something that I'll use when I need or when it suits the situation. But it's definately not my preferred language.

C (and its variants) are going to be the "Focus" of my longterm studies, however, secondary languages can't hurt?

And It is amazing how fast the replies are coming in.

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> 
C (and its variants) are going to be the "Focus" of my longterm studies, however, secondary languages can't hurt?


To be honest, there is not so much to "study in the long term" in "C and its variants" purely in the language sense (ignoring libs and language-independent learning). C-style language structure is frankly *not hard*, so I would recommend branching out into completely different directions (Python?) as soon as you feel comfortable in C...

---

### Post by loganwm on 2008-08-19
> **CptPicard said:**
> To be honest, there is not so much to "study in the long term" in "C and its variants" purely in the language sense (ignoring libs and language-independent learning). C-style language structure is frankly *not hard*, so I would recommend branching out into completely different directions (Python?) as soon as you feel comfortable in C...

I feel competent in C. And I've heard I can be a bit more productive with a scripting language, so it's appealing to be able to write simple/quasi-complex programs in a scripted, higher level language.

and my "long-term" C goals are essentially, the other libraries that can add a whole new perspective on things.

I'd like to move to a scripted language mainly because, I don't feel like tackling libusb, sdl, gtk, kde without learning a bit more about programming, in a wider perspective.

---

### Post by meanburrito920 on 2008-08-19
@ghostdog-- I have used bash quite often, and I understand your point completely. However I did say it is better to use bash 'if you have a specific application for  it'. The ps example obviously being one of them. If you believe that bash is better than python, then we must respectfully agree to disagree.

@CptPicard-- Thanks for the clarification :-)

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> I feel competent in C. And I've heard I can be a bit more productive with a scripting language, so it's appealing to be able to write simple/quasi-complex programs in a scripted, higher level language.

Why do I get a sense you are being a little bit dismissive of "scripting languages" in the sense that a lot of C-obsessed speed kiddies are? ;)

You'll be able to write a lot of very interesting, complex programs in a much more intellectually pleasing fashion in higher-level languages.

> 
and my "long-term" C goals are essentially, the other libraries that can add a whole new perspective on things.

The whole point is that they don't "add a new perspective", they are just more stuff in the same language. The new perspective comes from fundamental differences in languages.

---

### Post by loganwm on 2008-08-19
> **CptPicard said:**
> 
The whole point is that they don't "add a new perspective", they are just more stuff in the same language. The new perspective comes from fundamental differences in languages.

I'm not totally dismissing them, I really want to prove my bias wrong. Lua was a nightmare to me. I hated it. It encouraged horrible habits. So I take it out on scripting as a whole.

But I want to give Python an honest chance. And see how things work, see how things go, see what makes it so interesting :)

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> It encouraged horrible habits.

Such as?

Do you know yet what horrible habits are? :)

There's a lot of enforced bondage and discipline in the culture of statically typed languages that is actually somewhat pointless in higher-level languages and therefore missing for a good reason.

(Disclaimer: never done any Lua)

---

### Post by loganwm on 2008-08-19
> **CptPicard said:**
> Such as?

Do you know yet what horrible habits are? :)

Using VisualBasic :) haha

I'm kidding.


Lua, in the incarnation I used at least, didn't have any memory management whatsoever, variables initialization is almost automatic, executables relied on another program to interpret them which added a bit of overhead, OOP was horrid, 

I don't want to go into any more detail, as it might have just been my dread of my programming beginner days, but in hindsight, I didn't like it.

"(Disclaimer: never done any Lua)"

Never do, not worth it.

---

### Post by pmasiar on 2008-08-19
CptPicard already mentioned it, but I'll repeat so even people who skipped it first time will notice:

Power of Lisp is in the fact that there is no difference between code and data. Even common scripting languages like Perl/Python, which have eval(), cannot match easily. 

You rightfully ask: What can be more powerful than ability to put together string  containing any code (say function body definition), eval it, and assign  that executable to any function name? Lisp has more than simple strings: whole power of data manipulation of Lisp is focused on data structures (list) which are exactly the syntax structure of Lisp. So adapting underlying code to match the task is routinely done by expert Lisp hackers. 

Of course that's real brain surgery: imagine debugging code which was changed since written. But imagine pain of Lisp hackers when they cannot do it in C++, and they have to fight layers of typecasting.

Of course Lisp beginners don't start with those macros changing code: plain list processing is enough.

--------------------

Other languages to consider:
- Forth: language extremely close to the metal (includes assembly), but extremely easily extendable in any direction. It has absolute trust to programmer, provides no protection, and allows you  to do really strange things: patch (in binary) code of the compiled functions. Define intepreter/shell of new language and change to it. Most likely you will not be able to master it (only maybe top 5% or 10% hackers can) but you be totally awed when you will read complete Forth OS, including compiler, editor and shell, in just couple dozens pages of commented code. 

If you can handle it, Forth will blow your mind. It's like Lisp (without the lists), but close to the metal when you need to.

- Prolog: Language where you describe known facts and rules, then ask questions and system will figure out answer. 

Languages to ignore:

PHP: 10 years ago, any kid could mix HTML tags and snippets of PHP to get dynamic pages. These days, we understand that mixing business and presentation logic makes for hard to maintain mess and creates more problem than solves. Way to do web apps is "Model-View-Contoller" design pattern (see wikipedia), and there are plenty frameworks to do that. Rails (Ruby on Rails) was first framework of new generation, using "convention instead of configuration" approach (to avoid byzantine XML config files of Struts and Spring for Java), but today, Python has two Rails-like frameworks: Django ('pronounced' as best for beginners) and Turbogears (when you need more flexibility and trickery).

- Ruby: is 99% like Python, but less libraries).
- Perl: is old and it's age shows. However, widely used for old projects, but past prime. Possibly Perl6 will revive interest in Perl again, but chances are slim. 

Of course, learn any language needed for any project you are interested in, even PHP, Ruby or Perl.

Then of course you may want to learn some bland 'enteprisey' language to get you job, like Java, C++ or C#. Or maybe you will get involved in a startup, where agile languages is the only way to 'beat averages' :-)

---

### Post by angelina03 on 2008-08-19
python is a dynamic object-oriented programming language that can be used for many of software development.It comes with extensive standard libraries,and can be learned in a few days

prel borrows features from other programming languages including c,shell scripting(sh)which can be easy for u in understanig.

----------------------------------------------------------------------------------------------------------------------------------
angelina0305
[Missouri Drug Treatment]("http://www.drugtreatments.com/missouri")

---

### Post by pmasiar on 2008-08-19
> **meanburrito920 said:**
> @ghostdog-- If you believe that bash is better than python, then we must respectfully agree to disagree.

Not only that: we had heated discussion that there is no difference to use as first language for beginner Python, Java, awk or C++. In case you missed it -- it was long, more than 100 comments. Just to save you from wasting your effort to persuade ghostdog about errors in his ways :-)

@OP: It was thread somewhat related to your question: [ New to Programming with Java](http://ubuntuforums.org/showthread.php?t=892101), asking to what do next.

---

### Post by meanburrito920 on 2008-08-19
I think you have a misunderstanding of scripting languages, or at least I get that feeling from your posts. Like lua, all scripting languages run on a virtual machine (by definition). I'm pretty sure they all include automatic memory management (at least most of them do). All of them have weakly typed variables (as far as I know), and I dont know exactly what you mean by oop being horrid in Lua (I've never used Lua), but in general scripting languages don't vary too much as far in syntax (except for specialized ones like Awk,or Perl). I probably will get corrected by CptPicard in some of my statements :-) but for the most part, Lua doesnt stray to far from the flock as far as scripting languages go. (although perl may be the exeption to every rule).

EDIT: it is features like these that make scripting languages so compelling-- they take care of all the menial work for you. Its just more convenient.

---

### Post by pmasiar on 2008-08-19
> **jimi_hendrix said:**
> asking if it is at all feasible for me to make my own language)

yes - when you will have strong grasp what features language may have, how to implement them, and why. Very few people are capable to master multiple languages (to give them the perspective), and theory required. Some smart grad students can, but mostly it requires more than decade of learning to get there.

And then, how your language would be so special that anyone (including you) would bother to learn and use it?

---

### Post by CptPicard on 2008-08-19
> **meanburrito920 said:**
> All of them have weakly typed variables 

Weak, strict and dynamic typing are different things. Look them up on Wikipedia, I am too lazy to add links to post :)

> but in general scripting languages don't vary too much as far in syntax (except for specialized ones like Awk,or Perl)

No, there is not some general "scripting language syntax" -- all the fun diversity is actually mostly achievable in languages that don't need static compilation.

---

### Post by loganwm on 2008-08-19
> **CptPicard said:**
> 
No, there is not some general "scripting language syntax" -- all the fun diversity is actually mostly achievable to languages that don't need static compilation.

That's pretty much what I mean about Lua, to me, it doesn't make a whole lot of sense in a lot of its implementation.

My view of scripting is a bit jaded, but it's justified in some cases where efficiency is cast aside in favor of something much much less important.

Question about python and C interaction:

I understand the a system() call in C can run a python script, any other methods to have them inter-op?

Same question but in reverse, how about Python calling an executable?

---

### Post by meanburrito920 on 2008-08-19
Python can call an executable through the os library:

```

import os
os.system('EXECUTABLE_NAME')

```

---

### Post by ghostdog74 on 2008-08-19
> **meanburrito920 said:**
> @ghostdog-- I have used bash quite often, and I understand your point completely. However I did say it is better to use bash 'if you have a specific application for  it'. The ps example obviously being one of them. If you believe that bash is better than python, then we must respectfully agree to disagree.

Of course if you are talking about just pure bash itself, it has some limits as well. But coupled with its "modules" stored in /usr/bin,/usr/lib, it can do just as much as what other scripting languages can do, except for specific ones like doing a GUI. You have to import modules as well in Python, don't you? Whether bash is better or Python is better is not the issue. The issue is whether you really understand your tools and where your tools can be used in different situations.

---

### Post by CptPicard on 2008-08-19
> **loganwm said:**
> 
My view of scripting is a bit jaded, but it's justified in some cases where efficiency is cast aside in favor of something much much less important.

Which are rare. I really don't see what this is that you consider "less important" in semantically richer and expressive languages that let you actually express algorithmic concepts better and model your problem in a more logical, clearer manner. Shaving off constant factors by bit-pushing should really be a last resort, spending too much time on it really is not fitting of a creature of intelligence.

> 
I understand the a system() call in C can run a python script, any other methods to have them inter-op?

Not sure about this direction, but I sure hope you don't do it like that :)

> 
Same question but in reverse, how about Python calling an executable?

You don't call executables, you write modules in C and call those modules from Python.

---

### Post by ghostdog74 on 2008-08-19
> **meanburrito920 said:**
> Python can call an executable through the os library:

```

import os
os.system('EXECUTABLE_NAME')

```

Use bash. That's what you said in post #22. :)

---

### Post by ghostdog74 on 2008-08-19
> **pmasiar said:**
> about errors in his ways :-)

it happens both ways right? :)

---

### Post by pmasiar on 2008-08-19
> **ghostdog74 said:**
> it happens both ways right? :)

No, it only happens to people who disagree with me. meanburrito agrees with me, so he is obviously right :-)

---

### Post by mssever on 2008-08-20
First, a comment about Ruby. I didn't grasp OOP until I learned Ruby. C++ and Java taught me little about it (though I haven't touched either language since I was a newbie, so my opinion might not count for much). IMHO, Ruby is nicer than Python for OOP, though you can easily use Ruby in a non-OO way if you want.

Also, some people consider Ruby to be mainly a web language. But it's really great for system administration and text processing--better for those tasks than Python IMO. Ruby by itself isn't all that great of a web language. Rails isn't really Ruby; it's more of a domain-specific language based on Ruby.
> **ghostdog74 said:**
> you haven't had an opportunity to be in a situation that needs bash yet. Therefore, i suggest you don't comment on it.I have. But I've seen a lot of people around here struggling to make bash do things that would be so much easier in Ruby--or even Python.
> really? show me an easy way to do a process listing in Python. No, don't use system call to ps.Show me an easy way to do that in bash, without using a system call to ps. ps is an external program, so there really isn't much difference between calling ps from bash, or doing [FONT=Courier New]`ps`.chomp[/FONT] in Ruby or [FONT=Courier New]os.system('ps')[/FONT] in Python. Bash has its uses, but why fight bash's oddities when you don't need to? bash's syntax is quite clunky (all the various kinds of expansion are great for interactive use, but make scripting complicated). You can only return an integer >= 0 and < 256 (I think). If your functions need to return something else, you have to resort to a kludge. Variables are, by default, global, which can cause problems with recursion if you aren't careful. Plus, you have to use other languages (canonically sed and/or awk) to accomplish many tasks.

Leave bash to the command line and the few scripts that need it (or the simple wrappers where anything else is overkill), and use a Real Programming Language for the rest. My productivity has gone up quite a bit since I started following this advice.

> **pmasiar said:**
> And then, how your language would be so special that anyone (including you) would bother to learn and use it?
Designing your own language is difficult, I'm sure. But there are many cases where domain-specific languages come into play. I understand that many Lisp programs consist largely of what are essentially DSLs (I don't yet know Lisp, so I risk exposing my ignorance here). Ruby is also a good language on which to build a DSL. (Rails is one such example.) I wrote a trivial DSL on Ruby once as a proof of concept. I must admit, though, that I haven't had any practical use for a DSL that I'd be capable of writing.

---

### Post by ghostdog74 on 2008-08-20
> **mssever said:**
> 
I have. But I've seen a lot of people around here struggling to make bash do things that would be so much easier in Ruby--or even Python.

Correction: Bash+standard Unix tools. You might want to quote an example that is so difficult to do. 

> **mssever said:**
> 
bash's syntax is quite clunky (all the various kinds of expansion are great for interactive use, but make scripting complicated). You can only return an integer >= 0 and < 256 (I think). If your functions need to return something else, you have to resort to a kludge. 

such things are said when one does not fully understand how to use his programming tools well enough. You can not only return an integer in a function, you can return a string.
```

foo()
{
 #do something
 echo "Returned string"
}
v=`foo`
echo $v

```

> 
Variables are, by default, global, which can cause problems with recursion if you aren't careful. 

you can set local variables using local.
eg
```

func ()
{
  local var=100
}  


```

> 
Plus, you have to use other languages (canonically sed and/or awk) to accomplish many tasks.

they are what i call bash's libraries or "battery included" like what you say in Python. I don't see any difference. Do you?

---

### Post by ByteJuggler on 2008-08-20
I thought I'd another dime in the hat... :) Read [this article]("http://www.python.org/about/success/esr/") by Eric S. Raymond, well known open source [hacker]("http://www.catb.org/~esr/faqs/hacker-howto.html") (used in the "genius programmer" sense) about how he came to Python and what his opinion on it is.   (If you don't know who Eric S. Raymond is, then I suggest you read/educate yourself about him a bit.  The man's opinion counts, IMHO.)  Edit: For that matter, the section on "Learn how to program" in the [hacker document]("http://www.catb.org/~esr/faqs/hacker-howto.html") I linked to above is probably quite relevant to this whole discussion as well.

---

### Post by Kadrus on 2008-08-20
Although Lisp is much more popular,**I** would prefer ML,more specifically Objective Caml,which is statically typed checked(unlike Lisp) and improves efficiency,and Lisp is slower than Objective Caml.
And I think Lisp was a good choice for AI 20 years ago,before modern alternatives were built.Lisp was at first designed for Artificial Intelligences because they benefit from recursion.Although Common Lisp failed to standardize tail recursion which is an absolutely essential element for any functional language,and bundles only the most rudimentary techniques for destructuring data (e.g. **CAR, CDR**) 
Language implementation is probably the single most compelling showcase for
the productivity of pattern matching over algebraic datatypes (a key
ingredient of all MLs) because the hardest part of writing a compiler  is term rewriting (tree substitution).

---

### Post by Alasdair on 2008-08-20
Have you considered Haskell? Or failing that how about ML or OCaml? As Kadrus rightly points out, Common Lisp isn't really that much of a functional language. It's a great multi-paradigm language, but don't fall into the trap of thinking that learning it will make you a great functional programmer - just look at the horrors of the loop macro if you need proof.:)

Some benefits of Haskell:
[LIST]
[*]It's purely functional.
[*]It's lazy.
[*]It has an active user base, which is growing by the day.
[*]It has a real static type system, don't let the dynamic language advocates and the horrors of C and Java fool you - static type systems can be great!
[*]You can do all that metaprogramming jazz you've heard about in Haskell too, just have a look at this [paper (PDF)]("http://web.engr.oregonstate.edu/~erwig/papers/Monadify_SCP04.pdf").
[/LIST]
Hopefully I've at least made you consider Haskell as a language that's worth learning, even if it's not any time soon.

---

### Post by CptPicard on 2008-08-20
Not that I have anything against OCaml or would "argue against it", all HLLs are kosher, but..

> **Kadrus said:**
> which is statically typed checked(unlike Lisp) and improves efficiency

Well, personally I very much prefer dynamic typing and consider *that* a feature.. ;) interestingly, you can provide type hints in CL that let SBCL for example compile a lot of stuff to be very fast, often close to C speed.

In my experience the worst offending parts speed-wise in SBCL-generated code are in consing intermediate lists if you use map/reduce a lot. I wish CL had better support for lazy evaluation...

> ,and Lisp is slower than Objective Caml.

Ok, *if* speed is such an issue...

> 
And I think Lisp was a good choice for AI 20 years ago,before modern alternatives were built.

Lisp is very much a general purpose language. The "AI winter" was bad for Lisp because it was so associated with AI that even Lisp fell out of favour. Talk about baby and bathwater.

You can build a "modern alternative" with Lisp, into Lisp, if you want to :-)

> Although Common Lisp failed to standardize tail recursion

It's not mandated in the standard, but practically exists...

> and bundles only the most rudimentary techniques for destructuring data (e.g. **CAR, CDR**

Well, the Lisp list data structure is enormously powerful in the macro system and that's the reason why the language looks like the way it does :)

---

### Post by Kadrus on 2008-08-20
Haskell is a language worth learning indeed,and has a great community behind it as well.

---

### Post by Kadrus on 2008-08-20
> **CptPicard said:**
> Not that I have anything against OCaml or would "argue against it", all HLLs are kosher, but..

I've learned(still learning) both,maybe the Original Poster should do the same,as it will benefit him even more.

---

### Post by CptPicard on 2008-08-20
Oh, a slight redaction of position regarding type systems -- most of the nastiness of static typing really is seen in OOP languages where you do (forced, ideological) encapsulation and polymorphism, requiring lots of "design" :) It's probably better in a functional language.

---

### Post by ramocc on 2008-08-20
I'd recommend assembly (using nasm/yasm, not that nasty gas syntax). IMHO, it's worth having some idea of how the processor does things internally.

Also, although relatively unknown, I really recommend learning Modula-3. It really encourages you to write clean maintainable code (good interface/implementation separation, explicitly marked unsafe code, etc), and shows you how simple a language can be and still accomplish a lot.

Finally, if only to see how different languages affect your thinking, I'd suggest Icon (or the somewhat newer Unicon). AFAIK Python's negative string subscripting came from Icon, and Icon brings generators to a whole new level.

Of all the languages I've used, Modula-3 and Icon have had the most influence on the way I program.

---

### Post by mssever on 2008-08-20
> **ramocc said:**
> <snip>
Wow. You joined the forums back in 2006, yet this is your first post. You have a lot more restraint than I do! (And that's a good thing; I tend to waste too much time here :).)
> **ghostdog74 said:**
> Correction: Bash+standard Unix tools. You might want to quote an example that is so difficult to do.There are many, but the first that comes to mind is text processing. I know that you can use awk and sed quite effectively, but sed is awkward, and awk is a programming language in its own right. I could run an awk script from within Ruby just as easily as from bash. But in Ruby, I don't have to. The point is, the standard UNIX tools are available from within Ruby, just like they are from bash, so using them to argue in support of bash doesn't make sense. (You could also argue that csh uses standard UNIX tools.)


> such things are said when one does not fully understand how to use his programming tools well enough. You can not only return an integer in a function, you can return a string.As I said, you can't return a string without resorting to kludges. Using echo and backticks is a kludge. But what about returning (or even passing around--or even creating) complex data types? Can't be done in bash.
> you can set local variables using local.Of course. Which is why I said, "Variables are, **by default**, global." That's not really a sensible default. I'll go one further and point out that because bash functions use positional parameters, you lose several valuable things. First, it's valuable to specify how you intend to call a function, so that you'll get an error if you give the wrong number of arguments (given bash's seriously outdated expansion rules that require excessibe quoting, this is quite relevant). Also, it makes code more readable if you can see at a glance what input a function expects. I do something like this to come as close to readability as I can: ```
function foo {
  local bar="$1"
  local baz="$2"
  
  # function body here
}
```
But it would be so much better if I could write: ```
function foo(bar, baz) {
  # function body here
}
```
> they are what i call bash's libraries or "battery included" like what you say in Python. I don't see any difference. Do you?
Yes, I do. Because Python's (or Ruby's) libraries are written in the language, they interoperate with the language more cleanly. In bash, the only input you can give to bash's "libraries" is one or more strings, and it's up to the "library" to parse the string into usable data. In Python or Ruby, you can use any object that makes sense. Much more flexible. And, remember, 100% of bash's so-called library is available just as simply from within Ruby, thanks to Kernel#` (Python sometimes makes it harder to access).

Another thing: Suppose you need to extend the library, because it doesn't do quite what you need. In bash, you have to either dig out the sources of the command you want to modify (in which cases, the changes are global across the entire system), or script around the deficiency. In Ruby, you just directly modify the library as needed from within your program (in which case the change only affects that program unless you make the changes themselves into a library and use that in multiple places).

---

### Post by mikjp on 2008-08-20
What about French or German?

:lolflag:

mikko

---

### Post by jimi_hendrix on 2008-08-20
> **pmasiar said:**
> And then, how your language would be so special that anyone (including you) would bother to learn and use it?

my idea (if it ever gets completed it will be a miracle and if it actually becomes popular that will take divine intervention) is to make a near english language that would be extremely easy for a beginner to pick up and might make programming a little more popular (covetously this would mean it is probably high level and OO)

---

### Post by jimi_hendrix on 2008-08-20
> **CptPicard said:**
> 
Well, personally I very much prefer dynamic typing and consider *that* a feature.. ;) interestingly, you can provide type hints in CL that let SBCL for example compile a lot of stuff to be very fast, often close to C speed.

whats the difference between dynamic and static typing? wikipedia gives me a headache on this subject also what type of lisp would you recommended

---

### Post by LaRoza on 2008-08-20
> **jimi_hendrix said:**
> whats the difference between dynamic and static typing? wikipedia gives me a headache on this subject also what type of lisp would you recommended

```

#!/usr/bin/python

name = "LaRoza"
age = 20
#variables are declared without the programming needing to declare types
# and the interpreter dynamically determines the datatype (dynamic typing).
# This data type is enforced (strongly typed).

```

```

int main(void)
{
    string name = "LaRoza";
    unsigned short int age = 20;
    //the variables types are declared (statical typing), 
    //but are not enforced (weak typing)
}

```

---

### Post by jimi_hendrix on 2008-08-20
thanks

---

### Post by loganwm on 2008-08-20
> **jimi_hendrix said:**
> my idea (if it ever gets completed it will be a miracle and if it actually becomes popular that will take divine intervention) is to make a near english language that would be extremely easy for a beginner to pick up and might make programming a little more popular (covetously this would mean it is probably high level and OO)

That's actually a pretty solid idea, I'm interested in seeing how it pans out, I might actually be interested in it for something I'm working on, just as a prelim kind of thing since it hypothetically suits my needs and it'd be a great prototype for you have.

PM me about it and I'll show you what I'm working with.

---

### Post by jimi_hendrix on 2008-08-20
ok ill pm you later...thanks for the encouragement

---

### Post by Kadrus on 2008-08-20
> my idea (if it ever gets completed it will be a miracle and if it actually becomes popular that will take divine intervention) is to make a near english language that would be extremely easy for a beginner to pick up and might make programming a little more popular (covetously this would mean it is probably high level and OO)
Ever heard of [Revoltion Programming Language]("http://en.wikipedia.org/wiki/Revolution_(programming_language)")
It's practically English

---

### Post by Alasdair on 2008-08-20
> **LaRoza said:**
> ```

#!/usr/bin/python

name = "LaRoza"
age = 20
#variables are declared without the programming needing to declare types
# and the interpreter dynamically determines the datatype (dynamic typing).
# This data type is enforced (strongly typed).

```
There is more to static/dynamic typing than that because the following is valid Haskell...
```

name = "LaRoza"
age = 20

```
Statically typed languages can be explicitly typed, where the programmer has to declare all the types manually. This is what most people complain about when they complain about static typing - what they are really complaining about is *explicit* static typing. A language with implicit static typing will infer the types of the variables without them needing to be declared as such (although it is often considered good style to do so), and ensure they are used correctly at compile type. This process is known as type inference.

Being statically typed just means that the compiler performs type checking at compile time, rather than when your program is running. Obviously having type errors show up at compile time rather than runtime is a big win. The advantage of a Dynamic language is that it offers more flexibility (but not as much as some dynamic language advocates try to make out, you can implement a type-safe eval in a static language, [for example]("http://www.cse.unsw.edu.au/~dons/hs-plugins/html/System-Eval-Haskell.html")).

---

### Post by pmasiar on 2008-08-20
> **ByteJuggler said:**
> Eric S. Raymond, well known open source [hacker]("http://www.catb.org/~esr/faqs/hacker-howto.html") (used in the "genius programmer" sense) 

excuse me, but any other sense is just due by ignorant journalists who hijacked perfectly good word for misleading book. For that bad meaning, proper term is "cracker". Don't let clueless journos to steal our (hacker's) language.

---

### Post by pmasiar on 2008-08-20
> **mssever said:**
> Designing your own language is difficult, I'm sure. But there are many cases where domain-specific languages come into play. 

Yes, but I don't think OP is on the level to understand what DSL is, and meant to design one.

BTW best language to develop DSLs is IMHO Forth: it gives you power, and total lack of syntax in Forth gives you flexibility - even more than Lisp, possibly.

---

### Post by loganwm on 2008-08-20
> **pmasiar said:**
> Yes, but I don't think OP is on the level to understand what DSL is, and meant to design one.

BTW best language to develop DSLs is IMHO Forth: it gives you power, and total lack of syntax in Forth gives you flexibility - even more than Lisp, possibly.

I AM aware of DSLs, I just am not on a level to use them at their full potential.

---

### Post by ByteJuggler on 2008-08-20
> **pmasiar said:**
> excuse me, but any other sense is just due by ignorant journalists who hijacked perfectly good word for misleading book. For that bad meaning, proper term is "cracker". Don't let clueless journos to steal our (hacker's) language.

Exactly.  Unfortunately the incorrect meaning is easily the assumed one, which is why I clarified and provided links for elucidation.  :)

---

### Post by pmasiar on 2008-08-20
> **loganwm said:**
> That's actually a pretty solid idea [programming in a 'natural English']

Hint: Smartest minds on the planet were not be able to do it for 40 years now (and not for lack of trying), so maybe it's not as easy?

Read [http://en.wikipedia.org/wiki/Chomsky_hierarchy](http://en.wikipedia.org/wiki/Chomsky_hierarchy) about types of language grammars. Natural language and programming language (which obviously has to be deterministic to be of any practical use) are different classes of grammars. Think about it.

---

### Post by loganwm on 2008-08-20
> **pmasiar said:**
> Hint: Smartest minds on the planet were not be able to do it for 40 years now (and not for lack of trying), so maybe it's not as easy?

Read [http://en.wikipedia.org/wiki/Chomsky_hierarchy](http://en.wikipedia.org/wiki/Chomsky_hierarchy) about types of language grammars. Natural language and programming language (which obviously has to be deterministic to be of any practical use) are different classes of grammars. Think about it.

In it's simplest form, It's useful for something I'm working on. I understand the language barrier per se between English and Machine Language, but jimi_hendrix's language could be used for a part of one of my programs.

---

### Post by meanburrito920 on 2008-08-20
> **pmasiar said:**
> Hint: Smartest minds on the planet were not be able to do it for 40 years now (and not for lack of trying), so maybe it's not as easy?


I don't think it was necessarily that they couldn't do it, I think it was more affected by the fact that a natural English language will be needlessly verbose and inefficient. There would be dozens of ways to execute any command, and all phraseology would have to be accepted to allow it to be truly natural English. It just doesnt make sense. This is  where python has the right idea- There should only be one way to do something. 

I looked at that article on the Revolution programming language, and while I must say it makes certain things simpler (like the example about grabbing from ftp or url), It also manages to waste a bunch of typing. If you can do it with less in any other programming language, why would you give that up to use a less efficient language?

---

### Post by Alasdair on 2008-08-20
Isn't applescript proof enough that an english like syntax is actually a bad thing? :p

---

### Post by pmasiar on 2008-08-20
> **meanburrito920 said:**
> I don't think it was necessarily that they couldn't do it, I think it was more affected by the fact that a natural English language will be needlessly verbose and inefficient. 

You did not read link about Chomski grammars above, did you? Can you see that English is non-deterministic and context-sensitive, while programming languages are for obvious reasons deterministic and context-free? And would be are trying to fit square peg in round hole?

---

### Post by darsha on 2008-08-20
> **jimi_hendrix said:**
> can u guys point me to a good site for lisp learning (and your advised varient of it for me to learn) and a site for making my own language (google hasnt helped with this)

[www.htdp.com](www.htdp.com) its for scheme and i would recomend using the program drscheme

---

### Post by Kadrus on 2008-08-20
> can u guys point me to a good site for lisp learning (and your advised varient of it for me to learn) and a site for making my own language (google hasnt helped with this)
Practical Common Lisp is a good book,I suggest reading it...and it's free(yes,legal).
[http://gigamonkeys.com/book/](http://gigamonkeys.com/book/)
And Check the [Common Lisp wiki,]("http://www.cliki.net")it has many links and resources.
[Google did help]("http://www.google.com/search?q=Common+Lisp+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")
And [ANSI Common Lisp]("http://www.paulgraham.com/acl.html"):Absolutely worth reading.

---

### Post by jimi_hendrix on 2008-08-20
> **pmasiar said:**
> Yes, but I don't think OP is on the level to understand what DSL is, and meant to design one.

BTW best language to develop DSLs is IMHO Forth: it gives you power, and total lack of syntax in Forth gives you flexibility - even more than Lisp, possibly.

DSL?

and what language would you recommend for making an OOP language

---

### Post by meanburrito920 on 2008-08-20
> **pmasiar said:**
> You did not read link about Chomski grammars above, did you? Can you see that English is non-deterministic and context-sensitive, while programming languages are for obvious reasons deterministic and context-free? And would be are trying to fit square peg in round hole?

Point taken.

---

### Post by pmasiar on 2008-08-20
> **jimi_hendrix said:**
> DSL?


See post #50: [Domain specific language](http://en.wikipedia.org/wiki/Domain_specific_language)

> and what language would you recommend for making an OOP language

Is your goal to learn how languages are implemented? Or just create a hobby simple language of your own?

Start maybe with understanding couple of them? Hacking on the core? Only after you understand how it is implemented, and want to do it differently, makes sense to create new language. Why before, and what you would implement?

DSL does not **have* to be OOP: it is just useful for some (small) problem domain, it's not a generic language. SQL is domain-specific, and not aspires to be Turing-complete.

---

### Post by jimi_hendrix on 2008-08-20
> **pmasiar said:**
> 
Start maybe with understanding couple of them? Hacking on the core? Only after you understand how it is implemented, and want to do it differently, makes sense to create new language. Why before, and what you would implement?

i was planning on doing it as a learning experience and a hobby.  i wasnt really aiming at being totally radical...just making a clear language that is more user friendly for the simple computer user...also i was planning on adding as i learned so at first it would be simple but later more complex

---

### Post by CptPicard on 2008-08-20
> **jimi_hendrix said:**
> also i was planning on adding as i learned so at first it would be simple but later more complex

Write a basic Scheme interpreter first, it's actually remarkably easy...

---

### Post by jimi_hendrix on 2008-08-20
would you recommend scheme over common lisp?

---

### Post by CptPicard on 2008-08-20
Yes, especially for a learner. CL is bigger and more "practical" but has its issues. Scheme is more elegant and minimal but more "academic".

My own pet lisp at the moment is Clojure... runs on top of JVM and is pretty much the perfect lisp IMO.

---

### Post by jimi_hendrix on 2008-08-20
any scheme tutorials...i cant find many in google

---

### Post by Tim Sharitt on 2008-08-20
> **jimi_hendrix said:**
> any scheme tutorials...i cant find many in google

You might try [Teach Yourself Scheme in Fixnum Days]("http://www.ccs.neu.edu/home/dorai/t-y-scheme/t-y-scheme-Z-H-1.html").

---

### Post by CptPicard on 2008-08-20
[http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)

---

### Post by jimi_hendrix on 2008-08-20
thank you

mit = big words and headaches but ill try it out

---

### Post by slavik on 2008-08-20
> **stevescripts said:**
> Everyone who programs should spend a least a bit of time with some form of lisp or scheme ... ;)  (regardless of current skillset)

Just another $.02...

Steve
Python is similar to Lua ...

before learning Python, you should try Scheme/Lisp, maybe even a completely functional language (Haskell) and looking into Prolog would also help you widen your programming thinking.

---

### Post by mssever on 2008-08-20
> **jimi_hendrix said:**
> whats the difference between dynamic and static typing? wikipedia gives me a headache on this subject also what type of lisp would you recommendedBefore you can design a decent language, you need a lot more experience. In enough languages so that you understand these types of things--and much more.

> **Alasdair said:**
> Isn't applescript proof enough that an english like syntax is actually a bad thing? :p
+1

Syntax isn't the hard part of programming.

---

### Post by pmasiar on 2008-08-20
> **slavik said:**
> before learning Python, you should try Scheme/Lisp, maybe even a completely functional language (Haskell) and looking into Prolog would also help you widen your programming thinking.

100% misleading advice, IMHO. So you stopped to promote Perl as first language and started this?

You should try any/all of those languages, of course, but only **after** understanding basic of programming, by learning Python (you may skip OOP). Trying to understand programming by learning haskel/scheme would confuse you much more than trying Python first.

If someone else posted this, I would assume troll/flamewar. But forum mod posting this? :confused:

---

### Post by mssever on 2008-08-20
> **pmasiar said:**
> If someone else posted this, I would assume troll/flamewar. But forum mod posting this? :confused:
There are several conversations in this thread. slavik was replying to the OP 
(loganwm), who appears to have a bit more experience than some later posters. It's not apparent to me that you noticed this.

---

### Post by pmasiar on 2008-08-20
> **mssever said:**
> There are several conversations in this thread. slavik was replying to the OP 
(loganwm), who appears to have a bit more experience than some later posters. It's not apparent to me that you noticed this.

OK, I just don't want any green beginner reading this to think that learning haskel as first language is good idea, supported by forum mod.

---

### Post by loganwm on 2008-08-20
> **pmasiar said:**
> OK, I just don't want any green beginner reading this to think that learning haskel as first language is good idea, supported by forum mod.

I'm definitely past the First language status. :)

I've gotten an extremely large torrent of information so far, but at this point, I've pretty much decided, I'm sticking with C for the majority of my work. Learning Python or Lisp (or a variant) will be an ongoing project that I'll mess around with on occasion.  In addition to the VisualBasic I've been taking courses in at school. (The only choices before Java in our course guide) 

I don't really see a need for too much convincing at this point on what language to choose, as I've obtained some great information, but I'm sure this thread will continue to grow a bit just from the multitude of different conversations taking place.

Either way, I appreciate all the help and insight from everyone.

---

### Post by jimi_hendrix on 2008-08-20
> **loganwm said:**
> In addition to the VisualBasic 

is VB as bad as ive heard?

---

### Post by loganwm on 2008-08-20
> **jimi_hendrix said:**
> is VB as bad as ive heard?

It's the second language that I'd learned and although I'm still a beginner in it, it does follow a pretty logical implimention.

-With the Microsoft IDE making graphical or console programs is relatively quick and simple
-The standard functions aren't intensely difficult to use
-You have a great amount of control over a variety of Windows graphical gui aspects for your program

I haven't done anything too complex in it, but it is a neat language for making Windows programs, but I'm sure there's better.

If you want see see some of the syntax, I might be able to dig up a few of my oldies if I can find that damned flash drive..

---

### Post by LaRoza on 2008-08-20
> **jimi_hendrix said:**
> is VB as bad as ive heard?

If you heard it was a satan spawned language based on a language intended for use for non programmers, then yes, it is true. 

VB is a Windows only language. The only good thing about it is its IDE (at least, that is the one reason why people use it. I never heard of anyone using VB without using VS)

---

### Post by loganwm on 2008-08-20
> **LaRoza said:**
> If you heard it was a satan spawned language based on a language intended for use for non programmers, then yes, it is true. 

VB is a Windows only language. The only good thing about it is its IDE (at least, that is the one reason why people use it. I never heard of anyone using VB without using VS)

It's not horribly bad if you're using it for "what Microsoft intended it for"

---

### Post by nvteighen on 2008-08-20
I support multi-threading reply :)

@jimi_hendix:
1) I'm learning Scheme and definitely recommend you for getting some meta-programming ideas. But expect your brain breaking because of the radical difference there is between functional (e.g. Lisps, Haskell) and imperative programming (C, C++, C#, etc.). But it's really worth and interesting... and you may finally hate all languages you've learned before and join **us** and rule the world! :)

2) VB is strange. I mean, MS had a good idea behind it... but they kinda did wrong by choosing BASIC as their base and it encourages program-for-the-interface instead of the more recommended interface-for-the-program approach.

@loganwm:
In your position, 
1) I'd keep improving the C and C++ skills by learning how to use the most popular libraries. I mean, the syntax and structure of those languages is that simple that you probably master it; now you have to know what tools have people created for you to use.

2) Data structures. Learn to see the world in terms of data!

3) Python. Coming from the C-world, you'll learn it in two days. The hard part will be to write "native Pythonic" code instead of "C (C++) code in Python syntax".

4) Learn the very basics of functional programming in Python.

"Joke" 5) Jump into Lisp and, together with jimi_hendrix, join us to rule the world!!! :)

"Serious" 5) Learn something different outside the structured-imperative paradigm. Whatever, but something that makes you see things from another point of view. Lisp (functional), XML/HTML (declarative), Assembly... Maybe not "useful" stuff, but that will enrich your programming knowledge with a broader perspective.

---

### Post by nvteighen on 2008-08-20
> **LaRoza said:**
> 
I never heard of anyone using VB without using VS

I did! I used VB 4, which existed before Visual Studio (VB 5+)...

---

### Post by pmasiar on 2008-08-20
Today it's hardly any reason to recommend learning VB to anyone. 

If you want to be locked in MSFT-based sweatshop, learn C#.

---

### Post by Kadrus on 2008-08-20
> **pmasiar said:**
> 
If you want to be locked in MSFT-based sweatshop, learn C#.
..Or F# which seems to be Microsoft next-generation language,a dialect of Ocaml,which runs on .Net,mostly influenced by Ocaml +  C#.

---

### Post by jimi_hendrix on 2008-08-20
> **Kadrus said:**
> ..Or F# which seems to be Microsoft next-generation language,a dialect of Ocaml,which runs on .Net,mostly influenced by Ocaml +  C#.

never heard of F#...is it any good?

> **pmasiar said:**
> If you want to be locked in MSFT-based sweatshop, learn C#.

I DID! i think its great for new programmers to learn it for the structure i think and basic form programming...after that i dont like it for digging into the machine (game programming which i do in C++)

---

### Post by pmasiar on 2008-08-20
> **jimi_hendrix said:**
> (learn C#)
I DID! i think its great for new programmers to learn it for the structure i think and basic form programming...

Let me disagree on C# for a bit.

If you want to live in MSFTland, learn IronPython.

---

### Post by LaRoza on 2008-08-20
> **jimi_hendrix said:**
> 


I DID! i think its great for new programmers to learn it for the structure i think and basic form programming...after that i dont like it for digging into the machine (game programming which i do in C++)

I started to look into C# a while ago, and found it to be nothing special. It was a version of Java and I think it is bad for new programmers. For basic programming, I would recommend a language like Python, which doesn't require doing things that aren't obvious (like why do you in C#/Java have to declare an object and a method to do a simple output to the terminal? In Python/Perl/Ruby, you just do it)

---

### Post by jimi_hendrix on 2008-08-20
what object? if you mean the class program thing that starts off all programs ive never really noticed/cared about it because my IDE did it for me...subject closed no room for a programming war in here

---

### Post by LaRoza on 2008-08-20
> **jimi_hendrix said:**
> what object? if you mean the class program thing that starts off all programs ive never really noticed/cared about it because my IDE did it for me...subject closed no room for a programming war in here

That is even worse ;) You didn't notice/care and more importantly, you probably didn't **know** what it was or why it was needed.

---

### Post by Kadrus on 2008-08-20
> **jimi_hendrix said:**
> never heard of F#...is it any good?
F# lets you write Windows applications in a decent language,which is great for business because Windows users have extremely low expectations of software and like to burn money.
I would recommend F# to a functional programmer who is keen to earn a living but I would not recommend it to someone who wants to better
themselves as a programmer. 
OCaml is a much better educational language than F# but it is still very practically-oriented.I am aspiring both though...maybe you should too.

---

### Post by skeeterbug on 2008-08-20
> **LaRoza said:**
> I started to look into C# a while ago, and found it to be nothing special. It was a version of Java and I think it is bad for new programmers. For basic programming, I would recommend a language like Python, which doesn't require doing things that aren't obvious (like why do you in C#/Java have to declare an object and a method to do a simple output to the terminal? In Python/Perl/Ruby, you just do it)

I like Python, but provide a more clear example of why C# is bad for new programmers?

C#:
```

System.Console.WriteLine("Hi, I just wrote to the terminal without declaring an object or a method.");
```

Python:
```

print "Whatever"

```

C# has more advanced features that Java doesn't have such as lambda, delegates, unsafe code, partial classes, namespaces not bound to a specific location (aka java packages), properties, generics (java uses them internally now I guess), operator overloading, user defined casts, and conditional compilation. I am sure I am missing some others as well. I am not trying to start a flame war with any Java developers out there, but anyone who says "C# is just a version of java" clearly lacks any experience in either of the two technologies.

If you are going to advocate Python, please use a more compelling argument.

---

### Post by LaRoza on 2008-08-20
> **skeeterbug said:**
> I like Python, but provide a more clear example of why C# is bad for new programmers?

C#:
```

System.Console.WriteLine("Hi, I just wrote to the terminal without declaring an object or a method.");
```

Python:
```

print "Whatever"

```

If you are going to advocate Python, please use a more compelling argument.

Here is my compelling argument:

Newb>"Hi. I am interested in learning to program, can I have an example?"

Me>Sure, it is simple. Here is the simplest action you can do:

```

class p 
{
    static void Main() 
    {
        System.Console.WriteLine("Hello World!");
    }
} 

```

VS:

```

print "Hello world"

```

---

### Post by Kadrus on 2008-08-20
> If you are going to advocate Python, please use a more compelling argument.
I think it's pretty clear without an argument,the code says it all in my mind.

---

### Post by pmasiar on 2008-08-20
> **skeeterbug said:**
> C#:
```

System.Console.WriteLine("Hi, I just wrote to the terminal without declaring an object or a method.");
```


Q: What is "System.Console." part of the name? 

A: Shut up and do as you are told! You do not have esoteric knowledge I do so if I explained to you your braaane will burrrrst!

:-)

---

### Post by LaRoza on 2008-08-20
> **pmasiar said:**
> Q: What is "System.Console." part of the name? 
:-)

It is a namespace, obviously. (Not to mention the code omitted is even less intuitive)

---

### Post by skeeterbug on 2008-08-20
> **LaRoza said:**
> Here is my compelling argument:

Newb>"Hi. I am interested in learning to program, can I have an example?"

Me>Sure, it is simple. Here is the simplest action you can do:

```

class p 
{
    static void Main() 
    {
        System.Console.WriteLine("Hello World!");
    }
} 

```

VS:

```

print "Hello world"

```

So since Python has built-in print statement that requires less code than C#, it is clearly the winner for a first language? You could say that the C# code gives you the opportunity to explain objects, static functions, namespaces, and string types for their first tutorial, or at least give a brief explanation that can be explained later. These topics would be covered later anyways.

---

### Post by LaRoza on 2008-08-20
> **skeeterbug said:**
> So since Python has built-in print statement that requires less code than C#, it is clearly the winner for a first language? 

No, it is a clear winner over C#. For a first language, its syntax, availability and standard library are needed to justify my recommendation over some other languages.

> 
You could say that the C# code gives you the opportunity to explain objects, static functions, namespaces, and string types for their first tutorial, or at least give a brief explanation that can be explained late.

You could. But I would doubt any person with background in psychology or learning would say that is an effective way to learn/teach.

---

### Post by loganwm on 2008-08-20
> **skeeterbug said:**
> So since Python has built-in print statement that requires less code than C#, it is clearly the winner for a first language? You could say that the C# code gives you the opportunity to explain objects, static functions, namespaces, and string types for their first tutorial, or at least give a brief explanation that can be explained later. These topics would be covered later anyways.

Or it'll scare the pants off of beginners who honestly don't need all that confusion while trying to grasp the fundamentals.

It's like having a kid learn to swim in a rushing river, and expecting the child to find out how to swim faster :)

---

### Post by jimi_hendrix on 2008-08-20
> **LaRoza said:**
> That is even worse ;) You didn't notice/care and more importantly, you probably didn't **know** what it was or why it was needed.

yup...gotta love uninformative books/over helpful IDE's

---

### Post by skeeterbug on 2008-08-20
> **LaRoza said:**
> No, it is a clear winner over C#. For a first language, its syntax, availability and standard library are needed to justify my recommendation over some other languages.

Is this because you have professional experience using both platforms and have experienced Python's superiority first hand? Why would you want to learn C# over Python as a first language? Probably because getting a job in .NET is more likely. I have a family to feed and my sweat shop C#/.NET job pays those bills.

Believe it or not, I actually enjoy coding in Python more. I use it for all sorts of internal applications and side projects at home. Your argument is based on a simple print statement (which Python has built-in, and .NET has available in a static class). Not a very fair or realistic comparison. Go search monster or craiglist for Python jobs, and then do the same search for .NET jobs. I feel pretty secure knowing how many jobs I have available to me.

If you don't factor in the amount of lines of code a programmer does in his productivity, why would you factor in the size of code for a print statement and come to the conclusion the language is superior? The entire argument is silly because VS.NET has incredible intelli-sense/code completion. PyDev has nice code completion for Python, but it isn't anywhere near as good.

> 
You could. But I would doubt any person with background in psychology or learning would say that is an effective way to learn/teach.

So giving them a stupid print statement is an effective way to learn the language? /boggle

---

### Post by skeeterbug on 2008-08-20
> **loganwm said:**
> Or it'll scare the pants off of beginners who honestly don't need all that confusion while trying to grasp the fundamentals.

It's like having a kid learn to swim in a rushing river, and expecting the child to find out how to swim faster :)

So what exactly would be the point of the tutorial? You can easily highlight only the print statement and explain that if needed. I've read countless books that give a very brief or no explanation of a piece of code, stating that it will be covered later on.

---

### Post by jimi_hendrix on 2008-08-20
> **skeeterbug said:**
> I am not trying to start a flame war with any Java developers out there, but anyone who says "C# is just a version of java" clearly lacks any experience in either of the two technologies.

If you are going to advocate Python, please use a more compelling argument.

you started one ;)

i think that C# is a tad cleaner then python though (maybe because i learned C# first) but each to his own...as long as its not C++ i think you could teach it to someone willing to learn

---

### Post by jimi_hendrix on 2008-08-20
> **skeeterbug said:**
> So what exactly would be the point of the tutorial? You can easily highlight only the print statement and explain that if needed. I've read countless books that give a very brief or no explanation of a piece of code, stating that it will be covered later on.

very true

---

### Post by loganwm on 2008-08-20
> **skeeterbug said:**
> So what exactly would be the point of the tutorial? You can easily highlight only the print statement and explain that if needed. I've read countless books that give a very brief or no explanation of a piece of code, stating that it will be covered later on.

Its actually moreso a comparison than a tutorial. :)

And both tasks accomplish the same feat, but one has a bit More overhead and jargon that isn't necessary in 99% of situations where you would use it.

---

### Post by LaRoza on 2008-08-20
> **skeeterbug said:**
> Is this because you have professional experience using both platforms and have experienced Python's superiority first hand? Why would you want to learn C# over Python as a first language? Probably because getting a job in .NET is more likely. I have a family to feed and my sweat shop C#/.NET job pays those bills.

What does getting a job have to do with programming? Who mentioned .NET. This is a Linux forum, and I am a hobbiest with career aspirations elsewhere. This is about learning, not about getting a job. 

> 
So giving them a stupid print statement is an effective way to learn the language? /boggle
That was an example. This thread wasn't intended to be a full blown discussion on what is the best (if any) language to start with. For that, I refer you to the sticky.

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> What does getting a job have to do with programming? Who mentioned .NET. This is a Linux forum, and I am a hobbiest with career aspirations elsewhere. This is about learning, not about getting a job.

There are a lot of developers on this forum that code professionally for a living, the OP never specified which path he/she wishes to take. The Mono project has some nice backing, making .NET completely relevant for a professional or hobbiest.

> 
That was an example. This thread wasn't intended to be a full blown discussion on what is the best (if any) language to start with. For that, I refer you to the sticky.

Your sticky loses credibility when you are talking negative about a language you know nothing about. I simply asked you to give a clear example of why C# is bad for new programmers because you felt so strongly against it. Hint: If you know little to nothing about a subject, don't bash it.

> It was a version of Java and I think it is bad for new programmers.

---

### Post by loganwm on 2008-08-21
@skeeterbug

I'll give you credit, you do have a point, you're making it in a semi-hostile fashion, but you make sense.

BUT:

Those who are responsible for the sticky compilation are numerous and the sources span various sites located all over the internet. You can't expect LaRoza to be able to know every detail about every language and make an expert opinion in all case. (although LaRoza is quite knowledgeable)

The sticky is not the work of one poster, it's a compilation of a legion of posters on the forum. Despite your criticism of LaRoza's opinion sharing, the sticky *does* stand in this forum as a credible resource regardless of whom is referencing it.

---

### Post by skeeterbug on 2008-08-21
> **loganwm said:**
> @skeeterbug

I'll give you credit, you do have a point, you're making it in a semi-hostile fashion, but you make sense.

BUT:

Those who are responsible for the sticky compilation are numerous and the sources span various sites located all over the internet. You can't expect LaRoza to be able to know every detail about every language and make an expert opinion in all case. (although LaRoza is quite knowledgeable)

The sticky is not the work of one poster, it's a compilation of a legion of posters on the forum. Despite your criticism of LaRoza's opinion sharing, the sticky *does* stand in this forum as a credible resource regardless of whom is referencing it.

Fair enough. I just get angry because personally I don't talk negatively about something I know little about. I wouldn't tell someone to eat at restaurant A because B sucks, even though I've never ate at B. I would tell them I've never ate at B, but A was extremely good.

---

### Post by loganwm on 2008-08-21
> **skeeterbug said:**
> Fair enough. I just get angry because personally I don't talk negatively about something I know little about. I wouldn't tell someone to eat at restaurant A because B sucks, even though I've never ate at B. I would tell them I've never ate at B, but A was extremely good.

Which is perfectly reasonable, and I agree that criticism (at least: valuable criticism) is based on pure experience.

It should be acceptable to admit that in a comparison between language A and language B that if you've only had experience with Language A, then your opinion is much more valuable ***without*** making assumptions about Language B to "help" your argument.

Your argument is more credible when not based on any preconceptions, rather on pure unfiltered experience.

---

### Post by LaRoza on 2008-08-21
> **skeeterbug said:**
> There are a lot of developers on this forum that code professionally for a living, the OP never specified which path he/she wishes to take. The Mono project has some nice backing, making .NET completely relevant for a professional or hobbiest.

Ok, so learning it will be good for a job, but all the programming jobs I have seen require degrees of a sort. Learning how to program C# first will not get anyone closer to any job....

> 
Your sticky loses credibility when you are talking negative about a language you know nothing about. I simply asked you to give a clear example of why C# is bad for new programmers because you felt so strongly against it. Hint: If you know little to nothing about a subject, don't bash it.

I know things about it, I have programmed in C# before. It is obviously inspired by Java, and as first languages, Java and C# are in the same boat.

C# and Java are not good as first languages because of:

[list]
[*] Static typing
[*] C like syntax
[*] Less intuitive standard libs (System.Console.In isn't all that clear, Python and C win here)
[*] Java Virtual Machine/Common Language Infrastructure
[/list]

---

### Post by ByteJuggler on 2008-08-21
This is fast going off topic and turning into a language flamewar.  I think this thread should probably now be marked as solved and/or locked.

---

### Post by pmasiar on 2008-08-21
It's up to OP to decide, but it always help to have discussion in the context. If someone finds a year from now something interesting to said, wouldn't it be shame if thread was closed?

If someone feels like thread exhausted itself, easy: don't post to it and it will be soon forgotten. If there are people interested in continuing discuss little leftover bits, ignore it. Why it bothers you  if anyone else has discussion about what you don't care? Why to silence it?

A thread is closed usually only if it  devolves into flamewars insulting people. I don't see this happening here now, so I don't see your point.

BTW meta-analysis of lessons learned from this and other flamewars are discussed in [Lessons about biases learned from language flamewars](http://ubuntuforums.org/showthread.php?t=896087), just for future reference.

---

### Post by LaRoza on 2008-08-21
> **pmasiar said:**
> 
A thread is closed usually only if it  devolves into flamewars insulting people. I don't see this happening here now, so I don't see your point.


Or if the OP requests it, but she hasn't.

---

### Post by loganwm on 2008-08-21
> **laroza said:**
> or if the op requests it, but she hasn't.

"he"

---

### Post by mssever on 2008-08-21
> **LaRoza said:**
> Or if the OP requests it, but she hasn't.
Of course, regular members have the ability to close their own threads...

---

### Post by jimi_hendrix on 2008-08-21
never knew that

---

### Post by loganwm on 2008-08-21
> **mssever said:**
> Of course, regular members have the ability to close their own threads...

It would have to reach an aggressive level before I would consider closing it, I see no harm in allowing these discussions to continue.

---

### Post by LaRoza on 2008-08-21
> **loganwm said:**
> "he"

OMG! A male on the internet! Can't be true. pix pls.

> **mssever said:**
> Of course, regular members have the ability to close their own threads...

No they don't, at least, not that I know of, but mods will close threads if the OP requests it most of the time.

---

### Post by mssever on 2008-08-21
> **LaRoza said:**
> No they don't, at least, not that I know of, but mods will close threads if the OP requests it most of the time.
[Here's a test]("http://ubuntuforums.org/showthread.php?p=5636562"). Note, however, that I don't have the ability to re-open a thread. EDIT: Or post in an already-closed thread.

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> Ok, so learning it will be good for a job, but all the programming jobs I have seen require degrees of a sort. Learning how to program C# first will not get anyone closer to any job....

If that's what your professors told you, OK.

> 
I know things about it, I have programmed in C# before. It is obviously inspired by Java, and as first languages, Java and C# are in the same boat.

C# and Java are not good as first languages because of:

[list]
[*] Static typing
[*] C like syntax
[*] Less intuitive standard libs (System.Console.In isn't all that clear, Python and C win here)
[*] Java Virtual Machine/Common Language Infrastructure
[/list]

That is your opinion, however I could say:
[LIST]
 [*] Static typing is an advantage when you are new to the language. The compiler will catch a lot of common mistakes.
 [*] Python requires indents vs brackets, pure semantics.
 [*] Again, you are comparing simple statement which Python happens to have built in. The .NET framework has a very intuitive namespace design. The MSDN library is very easy to search and the documentation provides clear examples.
 [*] I fail to see how a virtual machine with garbage collection is a disadvantage when compared to an interpreter.
[/LIST]

---

### Post by LaRoza on 2008-08-21
> **skeeterbug said:**
> If that's what your professors told you, OK.

No, I am a complete hobbyist with no formal education. I learned programming on my own for my own reasons. My knowledge of programming doesn't bring me close to getting a job, so my statement about learning C# is along the same lines. If someone is going to teach themself a language, it doesn't matter job wise what it is, no matter how hirable that language is in the professional world. 

> 
That is your opinion, however I could say:
[LIST]
 [*] Static typing is an advantage when you are new to the language. The compiler will catch a lot of common mistakes.
 [*] Python requires indents vs brackets, pure semantics.
 [*] Again, you are comparing simple statement which Python happens to have built in. The .NET framework has a very intuitive namespace design. The MSDN library is very easy to search and the documentation provides clear examples.

The interpreter will catch mistakes also (in Python) by throwing exceptions, just like a compiler.

The syntax (braces or indents) is important I think, but that is another topic for another thread.

The .NET framework intuitive? That is great. Unfortunately, this is a Linux forum remember, and .NET is for Windows based systems.

> 
I fail to see how a virtual machine with garbage collection is a disadvantage when compared to an interpreter.


I mean the compile/excecute stage is more complicated. Python is swifter to execute, and has an interactive shell. The interactive shell is an invaluable tool when learning.

---

### Post by mssever on 2008-08-21
> **skeeterbug said:**
> The .NET framework has a very intuitive namespace design.I don't know C# or .NET, so I may be guilty of speaking out of ignorance, but I fail to see how namespaces could be any more intuitive than they are in Python.

<off-topic>I've seen the word *hobbyist* misspelled frequently in this thread.</off-topic>

---

### Post by ByteJuggler on 2008-08-21
> **skeeterbug said:**
> 
 [*] I fail to see how a virtual machine with garbage collection is a disadvantage when compared to an interpreter.
[/LIST]

Just to be clear, "Python" is not interpreted in the classical sense which is what you seem to be implying above.  In fact, there's many implementations of Python, the main ones arguably being as follows:

CPython - the current reference implementation of Python - uses byte-code compilation + VM.  

Jython also uses byte-code compilation + VM, but obviously uses Java byte-code and VM. 

IronPython targets MS .NET CLR and compiles to .Net IL.  

So, don't think C# has some sort of edge purely because its reference implenetation compiles to IL bytecode.  Python has that as well (compiling to .Net IL bytecode) as well as (at least) 2 other mainstream VM alternatives, and all 3 of these uses VM's with some sort of garbage collection.  If you don't like the way the reference Python does that, then feel free to use another VM.  :)

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> 
The interpreter will catch mistakes also (in Python) by throwing exceptions, just like a compiler.
At run time, and if you happen to execute that piece of code. The compiler would catch them *all* at compile time.

> 
The syntax (braces or indents) is important I think, but that is another topic for another thread.
Well you mentioned it, so go ahead and start up a new thread about it.

> 
The .NET framework intuitive? That is great. Unfortunately, this is a Linux forum remember, and .NET is for Windows based systems.
Mono implements the .NET framework API, remember? Completely relevant. 

Look under "API completion status pages"
[http://www.mono-project.com/Resources](http://www.mono-project.com/Resources)

> 
I mean the compile/excecute stage is more complicated. Python is swifter to execute, and has an interactive shell. The interactive shell is an invaluable tool when learning.

Monodevelop, Sharpdevelop, and Visual Studio all include projects and you simply click "Run", or build->compile. Hell, even doing it from command line is pretty basic. [http://www.mono-project.com/Mono_Basics](http://www.mono-project.com/Mono_Basics)
If a user couldn't figure that out, they probably shouldn't be programming.

---

### Post by jimi_hendrix on 2008-08-21
my standing as a beginner:

its not the language its the teacher that makes a good begining language

---

### Post by pmasiar on 2008-08-21
> **skeeterbug said:**
>  [*] Static typing is an advantage when you are new to the language. The compiler will catch a lot of common mistakes.

this is opinion, or you can prove it?

In my experience, dynamically strictly typed language like python does not distract learner with irrelevant type info, but if used wrong, runtime error will let her know. Simpler to learn and use: no time investment upfront and errors reported only if they exist.

You may be confused with dynamic but weakly typed languages like Perl: yes, that **is** a confusing problem there.

> [*] Python requires indents vs brackets, pure semantics.

So is at least no worse, and in fact better: coding standards for every language suggest indent like Python has. So what in other languages is additional weakly enforced suggestion (and subject of constant flamewars), is simple part of Python syntax, with side effect of all code having similar style

> [*] Again, you are comparing simple statement which Python happens to have built in. The .NET framework has a very intuitive namespace 

intuitive for whom? total green beginner? Would you bother to solve the two tasks in C# so OP can compare and make own mind?

---

### Post by skeeterbug on 2008-08-21
> **ByteJuggler said:**
> Just to be clear, "Python" is not interpreted in the classical sense which is what you seem to be implying above.  In fact, there's many implementations of Python, the main ones arguably being as follows:

CPython - the current reference implementation of Python - uses byte-code compilation + VM.  

Jython also uses byte-code compilation + VM, but obviously uses Java byte-code and VM. 

IronPython targets MS .NET CLR and compiles to .Net IL.  

So, don't think C# has some sort of edge purely because its reference implenetation compiles to IL bytecode.  Python has that as well (compiling to .Net IL bytecode) as well as (at least) 2 other mainstream VM alternatives, and all 3 of these uses VM's with some sort of garbage collection.  If you don't like the way the reference Python does that, then feel free to use another VM.  :)

Yeah I have IronPython installed. LaRoza stated a virtual machine was bad for new programmers. I think it is irrelevant.

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> this is opinion, or you can prove it?

I have proved it through experience using two dynamic languages (Python/Ruby) in production systems, and one static (C#). Most often it comes from a misspelling, some light re-factoring, or a typo in the language syntax. The compiler will catch these types of mistakes every time. It isn't a huge issue, but it can save some time.

> 
In my experience, dynamically strictly typed language like python does not distract learner with irrelevant type info, but if used wrong, runtime error will let her know. Simpler to learn and use: no time investment upfront and errors reported only if they exist.

You may be confused with dynamic but weakly typed languages like Perl: yes, that **is** a confusing problem there.
And only if they happened to execute that chunk of code. See my original response.

> 
> [*] Python requires indents vs brackets, pure semantics.

So is at least no worse, and in fact better: coding standards for every language suggest indent like Python has. So what in other languages is additional weakly enforced suggestion (and subject of constant flamewars), is simple part of Python syntax, with side effect of all code having similar style
OK, so if my C# editor provides good indentation when I enter a bracket, what is the advantage? You could probably agree a good Python editor would do the same thing.

> 
> [*] Again, you are comparing simple statement which Python happens to have built in. The .NET framework has a very intuitive namespace 

intuitive for whom? total green beginner? Would you bother to solve the two tasks in C# so OP can compare and make own mind?
Intuitive to beginner and seasoned expert. System.Diagnostics has your tracing, debugging, etc. System.IO has stream and file IO operations, etc. I hired someone with no C# experience (he had done C++ and Java in college). We gave him a fairly decent sized winforms application to do as his first task. I pointed him to the documentation he needed, and he was good to go. He picked it up very quick and completed the application in under three months. The product is almost two years old now, and is still very maintainable and has undergone several updates. You could argue he wasn't a complete beginner, but neither is the OP.

---

### Post by LaRoza on 2008-08-21
> **skeeterbug said:**
> Yeah I have IronPython installed. LaRoza stated a virtual machine was bad for new programmers. I think it is irrelevant.

I didn't say that! Python has a VM...

> **skeeterbug said:**
> At run time, and if you happen to execute that piece of code. The compiler would catch them *all* at compile time.

Not really. Run some C code and you'll see it is weakly typed. Just because they were declared, doesn't mean it is enforced (I am not sure how C# or Java do things).

The worst errors are logic errors, not syntax errors.

> 
Mono implements the .NET framework API, remember? Completely relevant. 

No. Mono implements Ecma-334 and Ecma-335, and .NET is not part of the standard. Although mono is trying to port more than the standard, the legallity of that is questionable (but no legal actions have taken place yet).

> 
If a user couldn't figure that out, they probably shouldn't be programming.
So the ability to use IDE's is directly related to the worthiness to program?

---

### Post by pmasiar on 2008-08-21
> **skeeterbug said:**
> I have proved it through experience using two dynamic languages (Python/Ruby) in production systems, and one static (C#). 

OK so just opinion. Works just fine too.

I "proven" my opinion like you did: by using Perl, Python and Java to develop web apps, **and also** by learning from the problems encountered during teaching programming to my son and advising some non-programmer colleagues to learn programming.

We can put cards on the table, disclose our schools of thought (I am intuitionist) and be done with it: we stated our arguments, let OP makes own mind.

Or continue discussion as you see fit.

You may consider starting "Why I love/hate C#" thread which will be promptly linked from FAQ by mods if you prefer C# and care to have one place to argue about it, as we have about Python and other languages. You may want to read it if you did not yet, and comment about failures of Python, if you have something new to say. But warning: most of the arguments were repeated many times and they are quite stale.

---

### Post by wdaniels on 2008-08-21
> **LaRoza said:**
> Ok, so learning it will be good for a job, but all the programming jobs I have seen require degrees of a sort. Learning how to program C# first will not get anyone closer to any job....

Programming is one field where it's not strictly necessary to have a degree, because it's well-known that many of the better programmers are self-taught. Most job advertisements will say that they require a degree, but in reality I've found that's rarely the case, so long as you're prepared to take a lower salary (initially). An employer with any real business acumen will always consider an opportunity to employ somebody who can do the job for less money, especially given that it's relatively easy to determine whether somebody knows what they're doing or not in this profession. And once you get started, experience is key.

But having the particular language skill set somebody is looking for is always helpful, and in that case C# will always be a bigger advantage in general than Python. As for C# being synonymous with .NET and Microsoft, this is not the case. I've found Mono to be a perfectly good and viable platform for Linux development. They key there is not to view Mono as a compatibility layer for the .NET framework (that way only leads to frustration) but rather as a platform in its own right.

Otherwise, I always recommend Python over C#/Mono for less experienced programmers. You will get more done, faster. And that makes it more enjoyable, and helps you to learn the relevant APIs for all the 3rd party stuff (e.g. Gtk) that is ultimately more useful as an immediate concern IMHO. Your own language preferences will develop naturally over time so long as you keep an open mind with it all, for which fussing too much over which order to learn things in does not help. Too many people base their language preferences on whichever one they have "chosen" at some point and developed a particular mastery of. I find it's better to keep some familiarity will all of them to get a feel for which is the right tool for each job, and which ones suit your ways of working.

My final piece of advice is not to use any IDEs unless/until you come across a very good reason to do so.

---

### Post by jimi_hendrix on 2008-08-21
> **pmasiar said:**
> 

You may consider starting "Why I love/hate C#" 

sure i will

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> I didn't say that! Python has a VM...

Yes you did - "Java Virtual Machine/Common Language Infrastructure" was put in the reasons why one shouldn't choose java/C# as a first language.

No worries, we can move past that.

> 
Not really. Run some C code and you'll see it is weakly typed. Just because they were declared, doesn't mean it is enforced (I am not sure how C# or Java do things).

The worst errors are logic errors, not syntax errors.

Either are bad. If the compiler can do a lot of the work for me, so be it.

> 
No. Mono implements Ecma-334 and Ecma-335, and .NET is not part of the standard. Although mono is trying to port more than the standard, the legallity of that is questionable (but no legal actions have taken place yet).
Microsoft did not release WinForms and ADO.NET. Mono has alternatives to those anyways if there was legal action. Which is unlikely at this point.

> 
So the ability to use IDE's is directly related to the worthiness to program?
I also linked a command line example which was extremely easy to grasp. Did you even follow the link?

---

### Post by LaRoza on 2008-08-21
> **skeeterbug said:**
> Yes you did - "Java Virtual Machine/Common Language Infrastructure" was put in the reasons why one shouldn't choose java/C# as a first language.
I put it there because the learner is exposed to those details earlier, because they have to compile and run it on the VM.

> 
Microsoft did not release WinForms and ADO.NET. Mono has alternatives to those anyways if there was legal action. Which is unlikely at this point.

Microsoft doesn't always act immediately, and they can change their position for any reason (new directors, new CEO, CEO feels like it, etc)

> 
I also linked a command line example which was extremely easy to grasp. Did you even follow the link?
No, I didn't. Why? Because you still have to compile it no matter how you do it.

---

### Post by LaRoza on 2008-08-21
> **wdaniels said:**
> Programming is one field where it's not strictly necessary to have a degree, because it's well-known that many of the better programmers are self-taught. Most job advertisements will say that they require a degree, but in reality I've found that's rarely the case, so long as you're prepared to take a lower salary (initially).

I don't trust or expect anomalies.

> 
But having the particular language skill set somebody is looking for is always helpful, and in that case C# will always be a bigger advantage in general than Python. As for C# being synonymous with .NET and Microsoft, this is not the case. I've found Mono to be a perfectly good and viable platform for Linux development. They key there is not to view Mono as a compatibility layer for the .NET framework (that way only leads to frustration) but rather as a platform in its own right.
There are many job oppurtunies for people with no degree, using C# on Linux?

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> 
No, I didn't. Why? Because you still have to compile it no matter how you do it.

> gmcs hello.cs

> mono hello.exe

Whew, that was rough.

---

### Post by skeeterbug on 2008-08-21
> **LaRoza said:**
> I don't trust or expect anomalies.
If you are good at what you do and have passion for it, does it matter? Chances are you would have related experience in personal or open source projects if you love programming. That can easily get your foot in the door to start building professional experience. It isn't really an anomaly.

> 
There are many job oppurtunies for people with no degree, using C# on Linux?
Learning it on either system would be a two way street. So yes.

---

### Post by wdaniels on 2008-08-21
> **LaRoza said:**
> I don't trust or expect anomalies.

What is the anomaly you're referring to?

> **LaRoza said:**
> There are many job oppurtunies for people with no degree, using C# on Linux?

Not on Linux probably, but there are plenty for somebody without a degree but having a good familiarity with C#. I can only speak from my own experience of course (as somebody without a degree who has never had any trouble getting any kind of programming job) and I do know that in the US people put a lot more stock in the formal academic system, but it can't be all *that* different than the UK.

---

### Post by pmasiar on 2008-08-21
> **wdaniels said:**
> Programming is one field where it's not strictly necessary to have a degree, because it's well-known that many of the better programmers are self-taught. Most job advertisements will say that they require a degree, 

... or comparable experience.

But to get to interview, there is one important step: you need to get past HR. HR clerk has pile of dozens or hundreds of resumes applying for a position, and has to evaluate them quickly to select a dozen for phone screening interview. She does it by checking for red flags, and not having education is huge red flag. I worked as IT recruited for couple months, so I know how I did it. Even resume formatted in a way it will be too much work to make it presentable to hiring manager is a red flag, if there is another equally good candidate with decent resume.

---

### Post by LaRoza on 2008-08-21
> **pmasiar said:**
> ... or comparable experience.

But to get to interview, there is one important step: you need to get past HR. HR clerk has pile of dozens or hundreds of resumes applying for a position, and has to evaluate them quickly to select a dozen for phone screening interview. She does it by checking for red flags, and not having education is huge red flag. I worked as IT recruited for couple months, so I know how I did it. Even resume formatted in a way it will be too much work to make it presentable to hiring manager is a red flag, if there is another equally good candidate with decent resume.

Yeah, to get a good job without a degree, I would have to present some rather admirable accomplishments.

---

### Post by wdaniels on 2008-08-21
> **pmasiar said:**
> But to get to interview, there is one important step: you need to get past HR.

One of the biggest problems that happens here is that HR asks the engineering team for a list of skills they are looking for, which tends to come out as a very specific set of "technologies" (for example, experience with "VB6" plus "ActiveX" plus "Active Directory Services" plus "ADO" plus "SQL Server") and HR doesn't always understand the relative importance and relationships between these things. Somebody having things like "Visual Studio" and "COM" and "T-SQL Programming" listed instead does not appear to be a very close match to the requirements. So I agree that HR can often be a problem, but this can be equally true for any candidate - it's always hit and miss if there are a lot of candidates. Most recruitment agencies I've worked with though have only tended to send 3/4 CVs to HR each day to try to ensure that each one gets enough attention.

> **pmasiar said:**
> HR clerk has pile of dozens or hundreds of resumes applying for a position, and has to evaluate them quickly to select a dozen for phone screening interview. She does it by checking for red flags, and not having education is huge red flag.

Which is why a person looking for their first job would be better advised to apply to smaller, specifically software-oriented companies, preferably start-ups looking for a decent junior programmer as cheap as they come. These kinds of companies are usually much better for gaining the raw "problem solving" kind of experience you need initially anyway. Once you get a foot in the door it's easy enough to progress on merit. Then for more senior positions, there are fewer candidates who receive more attention from the right people. I've never found that for senior positions a lack of formal education is a red flag at all, but like I say, I can only speak from my own experience as both an employee and more recently an employer...I might have just had some extraordinary luck, but I've encountered plenty of other programmers without degrees and even in cases where I fully expected it to count against me (such as huge financial institutions in London) I was pleasantly surprised to find that it didn't seem to be an issue given my existing experience - after 2 days I had to turn my mobile off because I simply couldn't cope with any more calls. So I always try to encourage people not to view a lack of formal education as any kind of barrier in this industry - a lot of the time people just assume that they wouldn't be able to get a programming job without a degree, but it's not the case!

I don't mean to imply that it's just as easy to get a programming job without a degree, but it's a very long way from "rare" or "impossible" (certainly in the UK it's not even difficult). I'm only trying to make the point that without a degree, being able to list "C#" (regardless of platform) will help to match most job requirements better than "Python", and that could easily make all the difference given the number of HR people that might disregard a candidate based on other factors like education.

> **LaRoza said:**
> Yeah, to get a good job without a degree, I would have to present some rather admirable accomplishments.

I would employ you based on what I read from you here on the forums and the links in your signature, in preference to a new Computer Science graduate. Obviously, the average prospective employer is not going to do that much research on you, but if they are looking for somebody more than a 'generic' programmer resource to plug into slots in project plans, they might if you point them in the right direction. You either have an unrealistic idea about the level of competence and general usefulness of the average graduate student, or an unjustified pessimism about the ability of good tech companies to find and employ useful people. If this is indeed something you want personally, perhaps you only need to learn to sell yourself better? Not every employer is looking first at your qualifications - many are looking for a general aptitude, passion, energy and a certain kind of attitude. IT is one place where you will find such "modern" recruitment practices more readily.

---

### Post by LaRoza on 2008-08-21
> **wdaniels said:**
> I would employ you based on what I read from you here on the forums and the links in your signature, in preference to a new Computer Science graduate.
Honestly, so would I. I found the students and instructors at my school inferior in skill and drive to me when it came to computers. I had the entire IT department looking up to me, and the most classic moment was when the program director for the IT department asked me for help for computer related issues!

> If this is indeed something you want personally, perhaps you only need to learn to sell yourself better?

Actually, I am not trying to get such a job, and don't won't one. My major is Criminal Justice, nothing to do with IT (after I get my bachelors, I may go into IT related fields, but I don't have definite plans on what happens after)

---

### Post by wdaniels on 2008-08-21
> **LaRoza said:**
> My major is Criminal Justice, nothing to do with IT (after I get my bachelors, I may go into IT related fields, but I don't have definite plans on what happens after)

Definitely a better choice for qualification than anything computer-related I think - no avoiding the academic system when it comes to law (AFAIK!?).

I find that programming is not much fun professionally unless you're lucky enough to find a really good small start-up to work for. Having to justify everything commercially (and then try to explain the justification to people who can't see past the commission on their next sales contract)... having to spend more time trying to build capability as processes rather than building it in people... I personally don't find it very rewarding.

Better to keep programming as a hobby; it's something that you can apply usefully to all kinds of other endeavours, and maybe you could make a business out of it if a particular opportunity crops up? I've always thought there must be plenty of potential uses from applying the emerging semantic technologies (RDF/OWL) markup to various legal texts.

---

### Post by LaRoza on 2008-08-21
> **wdaniels said:**
> 
Better to keep programming as a hobby; it's something that you can apply usefully to all kinds of other endeavours, and maybe you could make a business out of it if a particular opportunity crops up?

I have said I enjoy programming to much to get hired for it :-)

If I do get a "perfect oppurtunity", I would take it of course, but I don't want to end up like pmasiar (joking pmasiar, almost)

---

### Post by pmasiar on 2008-08-21
> **wdaniels said:**
> I find that programming is not much fun professionally unless you're lucky enough to find a really good small start-up to work for. 

Did you read 'Beating the averages'? Startups are forced to use agile languages, not C#. What you were saying a while ago? :-)

> Having to justify everything commercially .. having to spend more time trying to build capability as processes rather than building it in people... 

Better to keep programming as a hobby; 

Or in academia. It is fine and more interesting that industry, but sometimes there are dry stretches... And we use free technologies quite often...

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> Did you read 'Beating the averages'? Startups are forced to use agile languages, not C#. What you were saying a while ago? :-)

Which is why the start-up I work for using C# is doing so terrible and growing!
/sarcasm

You take his article way out of context. It was written about his development the mid/late 90's when C/C++ were being used outside of their domain. He discovered LISP was a better fit in the web domain than C. So a low level system language couldn't build web applications rapidly? Hardly a surprise. You beat keep beating that dead horse.

Maybe this would be a good read for you:
[http://www.pchristensen.com/blog/articles/hey-language-snobs-dont-pinch-pennies/](http://www.pchristensen.com/blog/articles/hey-language-snobs-dont-pinch-pennies/)

---

### Post by pmasiar on 2008-08-21
> **skeeterbug said:**
> Which is why the start-up I work for using C# is doing so terrible and growing!


So you might be lucky. Good for you! Hope that MSFT will buy you soon!

I am always so upset that that Sun, instead of investing 100K/y for single developer working on Jython (ten years ago, when they were puking money) decided to let this smart guy slip to MSFT and start IronPython and dynamic language revolution.

MSFT are ruthless but they are not idiots - they understand making software and when everything else fails, they are capable to do decent job. 

It's still hard to switch tho...

---

### Post by skeeterbug on 2008-08-21
> **pmasiar said:**
> So you might be lucky. Good for you! Hope that MSFT will buy you soon!


Hopefully they do. It would put my company shares to good use.

---

### Post by slavik on 2008-08-21
> **pmasiar said:**
> OK, I just don't want any green beginner reading this to think that learning haskel as first language is good idea, supported by forum mod.
what's wrong with a functional language being the first one?

---

### Post by LaRoza on 2008-08-21
> **slavik said:**
> what's wrong with a functional language being the first one?

Nothing, but functional programming (especially in haskell) isn't quite the best basis for learning "programming". Variables aren't variable, strict static typing, monads...

---

### Post by loganwm on 2008-08-21
> **LaRoza said:**
> Nothing, but functional programming (especially in haskell) isn't quite the best basis for learning "programming". Variables aren't variable, strict static typing, monads...

And you've also gotta deal with pesky lemmings that eat your code when your not looking :)

And LaRoza, remember that Hurricane I was talking about? Fay?

It's still sitting right over head and apparently it's here to stay for the indefinite future.

---

### Post by LaRoza on 2008-08-22
> **loganwm said:**
> 
And LaRoza, remember that Hurricane I was talking about? Fay?

It's still sitting right over head and apparently it's here to stay for the indefinite future.
You are lucky. My internet goes out if any sort of storm is nearby...

---

### Post by pmasiar on 2008-08-22
> **slavik said:**
> what's wrong with a functional language being the first one?

So your position is agnostic?

And what is right with it?

I (as intuitioninst) thought it would be you who should argue for your favorite language, if the selection is a rational choice, and not just something in spite of other opinions.

---

### Post by LaRoza on 2008-08-22
> **pmasiar said:**
> 
I (as intuitioninst) thought it would be you who should argue for your favorite language, if the selection is a rational choice, and not just something in spite of other opinions.

He is an anti-pmasiar, as noted earlier.

---

### Post by slavik on 2008-08-22
I am not agnostic because BASIC is crap ...

IMO, I am an intui... whatever it is. Scheme is easy (and most use in intro classes with Scheme, it is used in a completely functional manner). the syntax of Scheme can be learned in under 5 minutes and if it takes longer than that, you're in the wrong field.

---

### Post by pmasiar on 2008-08-22
> **slavik said:**
> IMO, I am an intui... whatever it is. Scheme is easy (and most use in intro classes with Scheme, it is used in a completely functional manner). the syntax of Scheme can be learned in under 5 minutes and if it takes longer than that, you're in the wrong field.

If you believe that some language is more intuitive for beginners and should be used, you are intuitioninst. (according to my quite arbitrary terminology :-) but we don't have any better, so let's use it)

In fact, Scheme is not that bad choice. And it was used as intro language IIRC in MIT until recently. So with scheme you are in good company :-)

But why you do not suggested Perl over Scheme? I thought Perl was your favorite (after STAR of course :-) )

Either way, this is not right place to discuss Scheme over other options, maybe you want to start "Why I love/hate Scheme" thread so I can learn something?

---

### Post by mssever on 2008-08-22
> **LaRoza said:**
> You are lucky. My internet goes out if any sort of storm is nearby...
You must have satellite Internet like I do. (I hate it, but the phone company isn't smart enough to either give me DSL or provide a rational explanation for why they can't--and maintain it in their records so they don't keep trying to sell me a service they can't provide. And cable isn't available here.)

---

### Post by LaRoza on 2008-08-22
> **mssever said:**
> You must have satellite Internet like I do. (I hate it, but the phone company isn't smart enough to either give me DSL or provide a rational explanation for why they can't--and maintain it in their records so they don't keep trying to sell me a service they can't provide. And cable isn't available here.)

No, DSL.

---

### Post by Kadrus on 2008-08-22
> In fact, Scheme is not that bad choice. And it was used as intro language IIRC in **_MIT_** until recently.
They assume previous programming experience,no?

---

### Post by CptPicard on 2008-08-22
> **Kadrus said:**
> They assume previous programming experience,no?

Actually no they don't, and Scheme really doesn't either. It can be used as a from-first-principles teaching tool, and it was created to be one.

---

### Post by Reiger on 2008-08-22
Don't know any Lua, still...

From looking at the OP's list of "wiki"; I do think taking a step into the functional world would be a good thing.

I mean: 3 lines of (trivial) code to calculate a list of arbitrary positive relative-primes* values given an input list...?
```

primes (x:xs) = x : ( primes (filter (`isRelativePrimeTo` x) xs) )
primes x	  = x

isRelativePrimeTo x y = x `mod` y /= 0
```

Such things simply ain't possible in an imperative language in an equal amount of code. (It's Haskell, btw).

* Values that are relatively prime to all other values in the output list, I mean.

---

### Post by pmasiar on 2008-08-22
> **Kadrus said:**
> They assume previous programming experience,no?

Even if many MIT freshmen quite possibly did some programming in high school, IIRC Scheme was "intro to programming" type of class, no experience necessary. But second language was C++, and now they switched to Python as intro language, I assume it is easier to switch to C++ from Python than from Scheme :-)

---

