---
title: "Is there a recommended order to learn programming languages?"
date: 2008-08-12
forum: Programming Talk
---

### Post by Igniteflow on 2008-08-12
I'm starting out learning to program and was wondering if anyone out there could give me some advice.  I've almost finished the "Learn Java in 24 hours" course, as that is what I thought might be a good start on the road of learning to program.  However, now I'm not sure whether I should continue with Java, or start learning the basics of other languages to get a wider scope on things.  Maybe Perl, C or C++?  Any recommendations for a good next step would be hugely appreciated.  I don't really have a huge project or specific aim, I just want to develop good habits and understanding so that I can contribute to the OpenSource community in the future.

---

### Post by CptPicard on 2008-08-12
We've had endless threads on this subject... but my condensed &#8364;0,02 would be as follows...

1. Python
2. C
3. Some variant of Lisp to make you a better person. One approach is to read "Structure and Interpretation of Computer Programs" and learn Scheme while you're at it.

This gives you a flexible yet easy general purpose language as your first one, the low-level stuff in the second one, and the third one broadens your horizons conceptually...

---

### Post by lordhaworth on 2008-08-12
Yeah Id always recommend learning something like C, thats where I started out and since then I've tried a little ruby, a little java, visual basic and now I've come back to learning Fortran90 (which is a fair bit like C) -which I have to say i'm really enjoying learning!

There are lots of very different languages out there, and it is good to sample them as I have done with ruby and java - however to really learn a programming language will take months/years so eventually you really need to decide on one language to learn properly. Once you have learnt one however well others should come more easily. 

Take home message - look around, try a few different types, decide what you would like to pursue further and then really learn that language properly (try not to jump about too much between languages at first or youll never learn more advanced concepts)

Also check out the beginner programming challenges on this forum, youll find them in programming talk.

Hope this helps

Tom

---

### Post by ghostdog74 on 2008-08-12
> **Igniteflow said:**
> I'm starting out learning to program and was wondering if anyone out there could give me some advice.  I've almost finished the "Learn Java in 24 hours" course, as that is what I thought might be a good start on the road of learning to program.  
the next step is to get in depth. Do some applications using Java.

---

### Post by lordhaworth on 2008-08-12
Ooo also, there is a brief intro to ruby which you can try online - 

[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

---

### Post by tinny on 2008-08-12
> **CptPicard said:**
> We've had endless threads on this subject... but my condensed &#8364;0,02 would be as follows...

1. Python
2. C
3. Some variant of Lisp to make you a better person. One approach is to read "Structure and Interpretation of Computer Programs" and learn Scheme while you're at it.

This gives you a flexible yet easy general purpose language as your first one, the low-level stuff in the second one, and the third one broadens your horizons conceptually...

My NZD0.00938 

What no Java? It would seem a real shame dropping Java after only 24 hours :)

I think it really depends on what the OP wants to get out of it. A job, get involved in open source, hobby, Linux dev etc...?

One thing I definitely think you should do is stick to one language for at least 1 year before branching out.

---

### Post by Reiger on 2008-08-12
I simply don't believe you've learnt much of the quirks & ways of Java after just 24 hours. If it's such a course in which your first ever 'Hello world' program is an applet with full Swing GUI; I'd go so far as to say -- you don't have learned much yet, 100% positively sure about it. (Because even after a year those code examples featuring full Swing layouts just for making a point about event listeners seem terribly over-complicated... How on earth does one see the real patterns from the Swing forest?)

That said I do suggest you try a Swing app, preferably some sort of Paint lite. Trying to implement some sort of magic methods such as "click an object and it disappears", plus a comprehensive do/undo mechanism... Such a project will show you how to build a proper GUI (and you may pick up some fancy tricks along the way too) but also work with a Data structure, interfaces, abstract classes... and Object Oriented design in general.

Then move on to other languages - when you understand some of the so-called design patterns (you'll be able to quickly work them out in different languages also). I'd suggest trying something akin to Haskell for getting to see some of the Functional Programming stuff there is; as well as a dynamically typed language such as Python, PHP or Perl. PHP has a very C-like syntax with some Perl stuff thrown in for added effect.

For something completely different JavaScript may be a very nice touch too: it's a prototypal language!

---

### Post by pmasiar on 2008-08-12
You did not told us in which area of programming you are interested, so it's hard to give good relevant advice.

But either way, you want to master simple, powerful language like Python, which lets you solve quickly big class of file parsing and manipulation tasks (you write it 10 times faster in Python, even if it will run 20% slower than equivalent Java code: if you run it one it does not matter).

One book about Java is nothing - Java has huge library of classes, and it is hard to wrap your head around it if you do not have Java guru around to tell you which 80% you can safely ignore.

"In 24 hours" you just scratched surface of Java. You do not have feeling about which of 60+ file-like classes to use to input/output, which data structure is appropriate (array? List? ArrayList? Map, HashMap? etc). So the little knowledge you have (variables, loops, functions) is directly transferable to Python, but Python will not force OOP on you from very start - you can safely program in Python for quite a long time without defining your own classes. Life is much simpler that way.

You definitely want to learn C. I would recommend C after Python before returning to Java, because C is such a simple language, but there is option to return to java and master it before going on.

By then you will have better idea what kind of application you want to program (and also which languages are used in that area) - you will not program drivers in Python, or web application in C++.

Lisp is good to expand your mind, about different way to approach programing. Other such languages are Prolog and Forth - you should learn about them, to see how different languages make solving some problems hard in one language trivial in another.

See sticky FAQ and wiki in my sig for links.

---

### Post by tinny on 2008-08-12
> You definitely want to learn C. I would recommend C after Python before returning to Java

I wonder if the OP ever wants to sleep?

---

### Post by Kadrus on 2008-08-12
> Learn Java in 24 hours
Everything that's like these books "Learn X in Y hours/days" is really total non-sense.I can't really imagine what motivates authors and publishers to release such books,deceiving a "new comer" to programming that it's possible.
Programming takes times,dedication,practice,and logic.
Reading a book on programming is not like reading any other book.
When you read a book on programming you learn the syntax,practice the code,just like any musician practice a piece until he becomes good at it,you can't make and learn from the mistakes you do in programming during 24 hours to know when and how to avoid doing those mistakes again in the future.And you certainly can't learn enough of the language syntax,as programming is a life-time experience and you keep learning and learning as you go along,no matter how much experience you might have.
Quoting the author from :Pragmatic,Programming Erlang(Author's name:Joe Armstrong)
> If you just read the text without typing in the commands, you
might think that you understand what is happening, but you will not have transferred this knowledge from your brain to your fingertips&#8212;
programming is not a spectator sport.
> However, now I'm not sure whether I should continue with Java, or start learning the basics of other languages 
Stick with Java at the moment since you have started to program with it,its not good to change language quickly,practice and take your time,don't rush into things,then move on to another language of your choice.Python or C is always a good option under Linux,since most of it's applications are written in it.

---

### Post by pmasiar on 2008-08-12
> **Kadrus said:**
> Everything that's like these books "Learn X in Y hours/days" 
Reading a book on programming is not like reading any other book....
Stick with Java at the moment since you have started to program with it,

While I agree with you that "in 24 hours" books are quite useless (or at least making false promises), see [Teach Yourself Programming in Ten Years](http://norvig.com/21-days.html)...

...don't you see that your advice contradict itself? If one book did not taught OP much, why it is a problem to abandon less-optimal language early and switch to more-optimal language for beginners? That little learned is easy to transfer, and rest of learning will be more fun in Python - partially because in Python, learner is not forced to think in objects, creators etc, and write many lines of boilerplate code to accomplish basic things?

Is it because you personally dislike Python?

---

### Post by Kadrus on 2008-08-12
> Is it because you personally dislike Python?
Dislike Python:Not at all.
I just think that jumping from one language to another early on might develop a bad habit on switching consitently languages.While Python is for sure easier than Java,and the results of learning programming with it will be faster.Why give up on a language?I always beleived that when you start with something finish it.
My point of my post is that the books that aim to teach programming in a short notice are quite bad..But I believe that you have much more experience than I do,so your advice should be taken more in consideration.

---

### Post by pmasiar on 2008-08-12
> **Kadrus said:**
> I just think that jumping from one language to another early on might develop a bad habit on switching consitently languages.While Python is for sure easier than Java,and the results of learning programming with it will be faster.Why give up on a language?I always beleived that when you start with something finish it.

finish it, even if you know that is is wrong thing to do? I somehow doubt that. You never abandoned any bad habit? :-)

IMHO better advice would be: "carefully research and consider options, and switch *this one time*, and then stick to it"

---

### Post by Kadrus on 2008-08-12
> finish it, even if you know that is is wrong thing to do?
A wrong thing to learn Java?Not really,a lot of people started with Java.
> You never abandoned any bad habit
I know a couple of guys that started learning programming,and jumped around from one language to another,with struggle,then totally gave up on programming,maybe was trying to help him avoid that.
> IMHO better advice would be
I'm a teenager,I don't know how to give advice:p.I was just expressing my opinion ^^

---

### Post by lukjad on 2008-08-12
I feel that anything that says that you will gain a complete knowledge in a certain amount of time is false. *"Lose 10 pound in 10 minutes!"* **"Become a Pro Athlete in Just Five Minutes a Day!"** _"Learn an Incredibly Complex Language in A Day!"_ and things like that are just scams. They may teach you a little, but they will not teach you all you need to know.

---

### Post by tinny on 2008-08-12
> **Kadrus said:**
> A wrong thing to learn Java?Not really,a lot of people started with Java.

I know a couple of guys that started learning programming,and jumped around from one language to another,with struggle,then totally gave up on programming,maybe was trying to help him avoid that.

I'm a teenager,I don't know how to give advice:p.I was just expressing my opinion ^^

You have a wise head for someone so young. :)

---

### Post by starcannon on 2008-08-12
I'm with Kadrus on the Java issue, even colleges are using it as an introductory "c like" language.

Pick one, stay with it till you are comfortable, then branch out.

---

### Post by Java Geek on 2008-08-12
Personally, I began Trying to learn C++. I actually succeeded for a while. I then tried Java, and both languages tied together and i truly learned programming. However, as i go back now and try simpler, more lightweight languages, I find it harder to understand because of its simplicity.

If you like web development, i suggest python and Java (and DHTML...).

If you want instant, hacker-like results, I suggest python, perl.

Robotics... Ada, C++.

Games... C++, Python, Java.

I hope that helped

---

### Post by neoguy2012 on 2008-08-12
Ignite, the problem is not an order to learn programming languages.  Languages are tools.  A carpenter wouldn't try to master a hammer before he uses a screwdriver.  You should try to pick an area of interest (something you'd like to do).  Then, you can try to evaluate what tools you might need to get the job done.  In some projects, you'll find that multiple languages need to be used.  However, have a goal in mind.

Now the problem is that you don't know the difference between a hammer and a screwdriver if you've never touched the tools before.  For starters, I guess you can learn a bit of Java.  I would recommend learning more about the history and purpose of Java before you delve into it.  Here are some important points about Java:


[LIST=1]
[*]fully Object Oriented (good for modular design if that's what you need)
[*]Garbage Collector (you don't need to focus as much as much effort on memory management)
[*]extensive libraries
[*]not designed to compile into native code (thus, users require java to be installed, requires an intermediate step before it is able to execute code, etc. etc.)
[/LIST]

So the first one can be a blessing or a curse.  For very simple scripts, you're going to have to write quite a bit of code to get some output since all code needs to live inside an object and all functions are parts of objects.  However, object oriented code is very attractive if you are working in a team since it helps manage code (since you can treat each object as a subsystem and, theoretically, develop and test it independently).

The garbage collector also has positives and negatives.  The great thing about garbage collectors is that you can spend more time on your algorithms rather than worrying about what to do with unused memory.  However, for some applications, you may want more control over memory and would not want to waste precious cycles on the automatic garbage collector.

The extensive libraries are only a plus in my book.  I can't see any negatives here.  However, when you are learning, I would advise that you learn the inner workings of some objects such as data structures (linked lists, trees, heaps, etc. etc.) rather than relying solely on the libraries.  One really important part of programming is knowing how data structures work, when to use them, and knowing how to develop your own types for specific applications.

Now the last one is a big-time deal breaker for a lot of people.  With java, you are tied down to the JVM.  Executing any of your code requires the virtual machine to be running.  In addition, you won't be compiling native code, thus you'll be wasting cycles (at some point) converting the intermediate code into machine code.  This isn't necessarily a bad thing and it doesn't necessarily mean your code will be very slow.

Programming is a craft, so it takes practice.  Like any other art or skill, start out small.  Try to make something that seems like it will be within your reach.  Play around with different languages and see what you like about each of them.  Understand the languages you are using.  I hope this helps you in learning how to program.  It's very fun and rewarding.

---

### Post by LaRoza on 2008-08-12
> **neoguy2012 said:**
> 
[LIST=1]
[*]fully Object Oriented (good for modular design if that's what you need)
[*]Garbage Collector (you don't need to focus as much as much effort on memory management)
[*]extensive libraries
[*]not designed to compile into native code (thus, users require java to be installed, requires an intermediate step before it is able to execute code, etc. etc.)
[/LIST]

Ruby and Python are all those also.

The really important points about Java are that it is a distinct platform with several languages to use.

---

### Post by neoguy2012 on 2008-08-12
> **LaRoza said:**
> Ruby and Python are all those also.

The really important points about Java are that it is a distinct platform with several languages to use.

That is very true (except Ruby and Python aren't fully Object Oriented, in that they can also be make great scripting languages).  I was referring to Java as its programming language, but the fact that Java is its own distinct platform and allows for the usage of many other languages within it is also an extremely important point to consider.

Disclaimer: Most of my programming experience is in hardware description languages, low-level assembly, C, and C++ since I do work in signal processing (and matlab too just to get some quick analysis results).  I did some web development work, but nothing too powerful.  I mostly dabble in other languages like python, Java, etc. as a hobby.

---

### Post by slavik on 2008-08-12
consider this to be my obligatory C/Perl post. have a good day. :)

---

### Post by Alasdair on 2008-08-12
> **neoguy2012 said:**
> ... except Ruby and Python aren't fully Object Oriented, in that they can also be make great scripting languages ...
Ruby is certainly fully object orientated, and I'm pretty sure Python is too. A language doesn't have to be stupidly verbose like Java to qualify as being fully OO. While everything in Ruby is an object, I don't think this is true in Java regarding some of the primitive data types (I may be wrong here, I'm not a Java expert). You could therefore say Ruby is more 'fully OO' than Java... whatever that means anyway. :)

---

### Post by neoguy2012 on 2008-08-12
> **Alasdair said:**
> Ruby is certainly fully object orientated, and I'm pretty sure Python is too. A language doesn't have to be stupidly verbose like Java to qualify as being fully OO. While everything in Ruby is an object, I don't think this is true in Java regarding some of the primitive data types (I may be wrong here, I'm not a Java expert). You could therefore say Ruby is more 'fully OO' than Java... whatever that means anyway. :)

Ah, you are absolutely right.  Both python and ruby are both 'fully OO' in the same sense as Java, even more so since even primitives are treated as objects.  I was basing the "fully OO" aspect from the fact that the function where the program enters from must also be an object.  You are right, "fully OO" is a crappy way to refer to an aspect of a language since it can mean anything.

---

### Post by pmasiar on 2008-08-12
> **neoguy2012 said:**
> Languages are tools.  A carpenter wouldn't try to master a hammer before he uses a screwdriver.

But (stretching your alanogy little more) also would not try to master chainsaw before using less powerful manual tools to get feel for the material.

> You should try to pick an area of interest 

If area of interest is to learn programming in general, wouldn't it make sense to start with simple universal language which is easy to learn? because as you said, languages are just tools, and most languages have many features in common?

> Then, you can try to evaluate what tools you might need to get the job done. 

How to do it without any programming experience and understanding what programming is and what kind of problems might be there?

> I guess you can learn a bit of Java.

We had this discussion in stickies "Why I love/hate Java". Would you bother to read it before repeating misleading claims?

> fully Object Oriented (good for modular design if that's what you need)

for a beginner, Java's object obsession is just another obstacle. Python does not force objects on you until you need them and are ready

> Garbage Collector,  libraries

same in Python, only easier to use :-)

> not designed to compile into native code (thus, users require java to be installed, requires an intermediate step before it is able to execute code,

how this is relevant to a beginner? 

> object oriented code is very attractive if you are working in a team 

goal is to learn language as beginner, did you forgot about that?

Of course later OP can learn more languages, but why start with more complicated one?

For beginner, Python shell is the killer feature - allows to learn language one line at a time. Seems like you do not know Python, so you have hard time to compare - but I code in both Java and Python, and also asked many programmers (not teenagers knowing single language only).

---

### Post by pmasiar on 2008-08-12
> **neoguy2012 said:**
> Ruby and Python aren't fully Object Oriented

how Java, language **without** multiple inheritance and operator overloading, is more OO than Python which has both features? You definition of OOP is "whatever Java does"? maybe you really need to re-read "why I love/hate Java" and "why... Python" in stickies?

---

### Post by neoguy2012 on 2008-08-13
> **pmasiar said:**
> But (stretching your alanogy little more) also would not try to master chainsaw before using less powerful manual tools to get feel for the material.

> You should try to pick an area of interest 

If area of interest is to learn programming in general, wouldn't it make sense to start with simple universal language which is easy to learn? because as you said, languages are just tools, and most languages have many features in common?

I wasn't expecting someone to break down what I said in such detail.  I'm honored.  :)  I do agree that learning a simple language is a good idea, but you can't force someone into believing one language is better than another (Whether it's Java or Python).

> **pmasiar said:**
> 
> Then, you can try to evaluate what tools you might need to get the job done. 

How to do it without any programming experience and understanding what programming is and what kind of problems might be there?

I agree.  Thus I mentioned that "Now the problem is that you don't know the difference between a hammer and a screwdriver if you've never touched the tools before."

> **pmasiar said:**
> 
> I guess you can learn a bit of Java.

We had this discussion in stickies "Why I love/hate Java". Would you bother to read it before repeating misleading claims?

Personally, I don't like Java.  The only reason I mentioned java is because the OP mentioned he read a book about learning java in 24 hours.
> **pmasiar said:**
> 
> fully Object Oriented (good for modular design if that's what you need)

for a beginner, Java's object obsession is just another obstacle. Python does not force objects on you until you need them and are ready

This is true.
> **pmasiar said:**
> 
> Garbage Collector,  libraries

same in Python, only easier to use :-)

This, however, is subjective.  Personally, I agree that using libraries in Python is very easy.

> **pmasiar said:**
> 
> not designed to compile into native code (thus, users require java to be installed, requires an intermediate step before it is able to execute code,

how this is relevant to a beginner? 

It depends on what he wants to get out of programming.  I was taught from the ground up.  I started with C/C++ and worked up from there.  I work with on-line (meaning real time) processing algorithms.
> **pmasiar said:**
> 
> object oriented code is very attractive if you are working in a team 

goal is to learn language as beginner, did you forgot about that?

Working in a team is a good skill no matter how skilled you are in a programming language.

> **pmasiar said:**
> 
Of course later OP can learn more languages, but why start with more complicated one?

For beginner, Python shell is the killer feature - allows to learn language one line at a time. Seems like you do not know Python, so you have hard time to compare - but I code in both Java and Python, and also asked many programmers (not teenagers knowing single language only).
I appreciate your pushing Python onto people since it is a very easy to use language.  I am familiar with Python and I have made some interesting programs with it with GUIs using wxGlade.  I'm not saying I'm an expert and I'm sure you are a lot more familiar with programming in python than I am.

> **pmasiar said:**
> how Java, language **without** multiple inheritance and operator overloading, is more OO than Python which has both features? You definition of OOP is "whatever Java does"? maybe you really need to re-read "why I love/hate Java" and "why... Python" in stickies?

Okay... I apologize for my definition of OO as I've mentioned in previous posts...

---

### Post by pmasiar on 2008-08-13
> **neoguy2012 said:**
> you can't force someone into believing one language is better than another (Whether it's Java or Python).

Of course - I am not Inquisitor :-)

But I can, and do, argue - it's up to poster to evaluate arguments and make own opinion. My job is to collect arguments and present them, not to force believing into someone's head. 

After all... [NOBODY expects the Spanish Inquisition!](http://people.csail.mit.edu/paulfitz/spanish/script.html) - thtat's the whole point!

---

### Post by LaRoza on 2008-08-13
> **neoguy2012 said:**
> That is very true (except Ruby and Python aren't fully Object Oriented, in that they can also be make great scripting languages).  I was referring to Java as its programming language, but the fact that Java is its own distinct platform and allows for the usage of many other languages within it is also an extremely important point to consider.


Ruby and Python are fully object oriented from the beginning (I would have included PHP and Perl in my list, but they weren't originally designed that way)

Ruby (JRuby), Python (Jython) and Lisp (Clojure) can be used on the Java platform. The overly verbose statically typed language also called Java isn't all that grand.

---

### Post by LaRoza on 2008-08-13
As for the order of learning, I recommend one learns from the beginning.

---

### Post by Kadrus on 2008-08-13
> **tinny said:**
> You have a wise head for someone so young. :)
Thank you ^_^

---

### Post by Igniteflow on 2008-08-18
Thank you everyone for so much input, it's helped a lot.  Don't worry, I didn't expect to master Java in 24 hours, not even close, but it was a good introduction at least.  I'm starting a course in Computer Science next month, so I'm trying to get as familiar as I can with the concepts before it begins, especially with programming.  Taking from what people have mentioned, I intend to stick mainly with Java now rather than moving on to other languages before I have a better handle on it.  That time could be some way off by the way things are going!  It sounds like the next route would be Python or C/C++.  I've got some books on order because the PDFs are burning my eyes out, but programming certainly looks to be a challenging and fun endeavor.  I took note of the advice to find a project that interests me and could benefit others, if there are any other Java noobs out there who want to work on something feel free to get in touch.

---

### Post by lordhaworth on 2008-08-18
Cool,
One final bit of generic programming advice - when your practicing always look out for things youd LIKE to program, not just the examples from a book. The times you really learn and actually feel rewarded in programming are when you do something from scratch with a few ideas of your own. 
Id also recommend trying a basic game - everyone does it - but naughts and crosses is good. Im actually revisiting my old school naughts and crosses game now to try and program some real learning AI which im really looking forwards to getting working (and then teaching the computer! *cue various remarks about AI*)

Enjoy programming, and when your debugging - drink coffee

Done

---

### Post by unoodles on 2008-08-18
I strongly reccommend starting with a high level, and going lower.
the order I learned was:
Python
C,C++
x86-Assembler

---

