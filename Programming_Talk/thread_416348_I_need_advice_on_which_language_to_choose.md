---
title: "I need advice on which language to choose"
date: 2007-04-21
forum: Programming Talk
---

### Post by Laxton14 on 2007-04-21
Okay, I know that this is about the 8382287348th time this question has been asked; Im sorry.. but... i just wanted to get a response that was personalized for me. Ive read many of the other "which language is the best" posts and people arent very specific with what they want to do with programming.  Im not quite sure what i want to do, im just sure that i want to learn to program, If its not really complicated i would like to learn about a programming language that I could use with Ubuntu, Wine & Getting Windows applications to work with Ubuntu, or Device drivers(EX video cards, etc). It sounds really complicated to me.. but i have a lot of free time.. and Im willing to learn... 

PS- I have NO CLUE at all about programming.. I dont even have the slightest idea about how to make a Print "Hello World!" program... but i think that with time and patience i could learn... any advice is appreciated... i would also like a language that I can use in the future.. maybe in college or a career

Thanks

---

### Post by heimo on 2007-04-21
This is hard question, and I think there's no right answer. But then again, you can learn programming in general and when you get good at it, you'll be able to learn new languages much faster. It's not uncommon for a programmer to be able to program in ten different languages. Basic principles are very similar from language to language (yes, there are some exceptions).

My advice is to take a course in programming. Familiarize yourself with programming tools (including IDEs and editors) and concepts. Read about programming in general. Make "hello worlds" in couple different languages. Keep "design patterns" high on your reading list. Read and study other peoples source. It takes time, lots of time. And is incredibly rewarding.

---

### Post by smartbei on 2007-04-21
> **Laxton14 said:**
> Ubuntu, Wine & Getting Windows applications to work with Ubuntu, or Device drivers(EX video cards, etc)

Well, Device drivers and the linux kernel are written in C, (I am pretty sure). I would assume Wine is also. That said, many would recommend that you learn an easier language such as python before learning C, since it will help you establish the basics before plunging into the really advanced stuff.

---

### Post by samjh on 2007-04-21
If you wish to tinker with Ubuntu at system level, ie. make device drivers, work on the Linux kernel (the "brain" part of Linux), etc., then you need to learn C.  But if you just want to make nifty utilities for the desktop, or make add-on features for Ububtu, then Python is the quasi-official language for Ubuntu, so it is a good choice too.

But if you want to get a job later on, then neither language is ideal.  Java or C# will serve better, unless you are extremely skilled at C, or lucky enough to find a Python job (both C and Python jobs are a minority, compared to Java, C#, and even C++).

---

### Post by Tomosaur on 2007-04-21
You want an answer specific to you, and then ask this question in possibly the most vague way yet? If you don't know what you want to do, it is impossible for us to make a reccommendation. The only real advice we can give you is to either re-read the other threads, or decide on a project (not too ambitious, though) and then come back and we can make a reccommendation. We'll only be repeating ourself for the billionth time yet I'm afraid, unless you give us some more specific information.

Device drivers and stuff will be way over your head for the time being. However, C/C++ would be the best languages to use for that kind of thing, so you may want to start learning using those.

---

### Post by barmazal on 2007-04-21
my way of seeing things

php, python and ruby are script languages which are not compiled this means they could be slower than compiled languages like C, C++, .net or Java and few others and less common. 

Next step decide what for you need to program, is your goal to make software, web development of services and applications or just havin a fun with all the stuff mixed. Coz development is quite different for those.

Next step learn programming at all so you will be familiar with stuff like variables, loops and conditions. Most of languages have the same syntax or quite similar one. For example i've never seen Python code but i can read it. This is basic programming. 

After that you will be able to find what lanugage suits you and your needs. As for me i'm not application developer but i would go for C family since it compiles thus works faster and for web i would go for language which has the best tools i need to accomplish what i need to as i'm web developer. I familiar with php and .net, now trying out Ruby (programming language) on Rails ( Ruby's web techology).


So again, decide what for you need the programming and learn basic syntax + read about all languages. Tip, avoid stuff like Ruby developers like to use, this is cool language and really inspiring one. This is total crap to make you into community, nothing more. As the same as following next example, Ruby is easy to learn but hard to moderate which means it has no rules thus it's hard to create stable stuff. Why you need that? I don't know i learn it to see with my bare eyes why it's so easy and why it's hard to moderate as their guys claim which is quite nonsense.

My start was from Javascript, Actionscript (Javascript's clone for Flash), PHP and DOM in general. Web moves towards Advanced Javascript or as it called Asymetric Javascript (AJAX) so i must know all these cool features. Proof Microsoft adpots Ajax, MS guys know winning technology and steal it in time, so bother to learn Javascript and DOM good if you intend to deal with WEB.

I'm not application developer though, ask guys who deal with it.

---

### Post by noerrorsfound on 2007-04-21
> **Laxton14 said:**
> I dont even have the slightest idea about how to make a Print "Hello World!" program.
It's a lot easier than you might think. To print *Hello World* in Python, this is what you must type:
```
print "Hello World"
```
What you wrote would have been correct if Python commands were not case-sensitive.

---

### Post by pmasiar on 2007-04-21
> **Laxton14 said:**
> Okay, I know that this is about the 8382287348th time this question has been asked; Im sorry.. but... i just wanted to get a response that was personalized for me. 

OK no problem, I bumped good thread for you: [ Before you ask: Which programming language? ](http://ubuntuforums.org/showthread.php?t=407187) and also [Ruby, Python - for what are they good for?](http://ubuntuforums.org/showthread.php?t=416082) - my reply in "Ruby vs Python" has plenty of links to further research and compare. Because it is *you* who need to research and compare - we have *no idea* about your interests and preferences, and many people in their answers project their own preferences and interests. So hang around and get feeling what preferences of those people are - and if they match yours.

Especially check link to "The hundred year language" - it shows how languages evolve, and what future improvements in CPU speed could bring to us.

> If its not really complicated i would like to learn about a programming language that I could use with Ubuntu, Wine & Getting Windows applications to work with Ubuntu, or Device drivers(EX video cards, etc).

It is really complicated, because no one language covers it all :-)

> but i have a lot of free time.. and Im willing to learn... 

Great, you will need time, willingness to learn, and focus. You will get there.

> i would also like a language that I can use in the future.. maybe in college or a career

Unless you will learn one obscure language and run it use it all your career (40 years from now being the only human able to use it :-) ) -- you will need to learn many different languages during your career. So relax and don't try to find Holy Grail language - it does not exist.

[Cobol](http://en.wikipedia.org/wiki/Cobol) and [Ada](http://en.wikipedia.org/wiki/Ada_%28programming_language%29) was once the silver bullets you ask for - and because you know their fate, you may guess fate of Java twenty years from now :-)

I would strongly recommend to start with Python. Easier to learn than any other "big" languages (C/C++/C#/Java), does not force you to use objects before you are ready (java does :-) ) and widely used in free software.

After you are familiar with basic programming in Python, data structures, and program design (split program into modules and develop them separately), it will be easier to learn any other programming language: it is basically describing the same concepts using different syntax. Debugging is hard: write and debug program ten times the size is not ten times harder - it is 100 times harder. Read famous essay [The Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) by [Edsger W. Dijkstra](http://en.wikipedia.org/wiki/Dijkstra) - famous programmer/philosopher who "invented" paradigm of [structured programming](http://en.wikipedia.org/wiki/Structured_programming). Trust me, paradigm changes about once a decade or less, this guy knows about programming.

Ubuntu is just distribution, it packs together many (10k+)  free programs created in many languages by many developers, most of those not related to Ubuntu in any way ("upstream" in distro jargon). In every area, there are couple languages best suited for that area - but you do not know where to go yet.

So start with python (see link in my sig), by the time you graduate, chances are, Python will be much more popular in corporate environment  than it is now! :-)

---

### Post by pmasiar on 2007-04-21
I agree with 90% of what you say, let me pinpoint the 10% so we have some interesting discussion and we both can learn something :-)

> **barmazal said:**
> php, python and ruby are script languages which are not compiled this means they could be slower than compiled languages like C, C++, .net or Java and few others and less common. 

You use "script" as some magical enchantment of bad luck :-) FYI Python is compiled into bytecode (like Java is for virtual machine - JVM ), Java's classcode is afterwards compiled farther into object code. Python can be compiled too: [Psyco](http://en.wikipedia.org/wiki/Psyco).

And you did not mention how execution speed is related to speed of learning. In my experience "fast" languages like C/C++ are harder to learn and master. Also, speed of your application might be affected by factors completely outside of your control: if 90% of runtime is spent talking to database and fetching datasets, it is hardly of any importance shaving miliseconds using C. Also you forgot about one very important speed in programming - **speed to the market**. 

"Scripting" - you mean ["duck typing"](http://en.wikipedia.org/wiki/Duck_typing) as kind of [dynamic typing](http://en.wikipedia.org/wiki/Dynamic_typing)? Many people (and my own experience) suggest that using a language with dynamic typing, you can develop, debug and test your code faster, with only minor effect on runtime speed. Of course not everywhere: Like maybe 80% of developers, I do web front-end for database apps, no kernel, no drivers :-)

>  Most of languages have the same syntax or quite similar one. For example i've never seen Python code but i can read it. This is basic programming. 

No - this is very important Python feature - readability! 

Not all languages are made readable: try to guess what [this](http://www.99-bottles-of-beer.net/language-ant-674.html) Ant script does, or [this](http://www.99-bottles-of-beer.net/language-lisp-361.html) Lisp program.

Major concern of Python developers is readability, and some feature implementations were rejected on readability.

>  Tip, avoid stuff like Ruby developers like to use, this is cool language and really inspiring one. This is total crap to make you into community, nothing more. As the same as following next example, Ruby is easy to learn but hard to moderate which means it has no rules thus it's hard to create stable stuff. Why you need that? I don't know i learn it to see with my bare eyes why it's so easy and why it's hard to moderate as their guys claim which is quite nonsense.

Not sure what you mean here. "moderate"? you mean [Software maintenance](http://en.wikipedia.org/wiki/Software_maintenance)? Ruby's focus was not on readability - influence of Perl fells rather strong. And I would argue than to master a language, you should study and learn usage idioms of experts - to become expert.

Looks like you do not have experience of making changes in 40MB (about 1M of lines) of source code, written by couple dozens of programmers over 10 years. When you do, you will understand better. For example, here is my experience in such environment: to fix a bug (reported by customer to your tester) you spend a hour or so learning the interface to see the bug, a day reading the code/understanding it, another day testing it with you and with tester, and about 15 minutes writing it.  Whole change might be 2-10 lines of code, but it takes 2 days to fix/commit it. Just FYI what they are talking about. :-)

> Web moves towards Advanced Javascript or as it called Asymetric Javascript (AJAX) so i must know all these cool features. .

[AJAX](http://en.wikipedia.org/wiki/Ajax_%28programming%29)  = "Asynchronous JavaScript and XML" which is new cool, buzzword-compatible name for rather old technology.

And I agree it is becoming cool on "web 2.0" dynamic websites. 80% of websites are just fine without it, or with just tiny doses tho :-)

---

### Post by LaRoza on 2007-04-21
You should use any language you want.

If you want to be productive quickly try Python, Perl, or ECMAScript.
These are interpreted and and not complicated languages.

If you want to  a steeper learning curve, try C/C++, or JAVA.

If you are using Windows, VBScript and VB.NET are simple languages, but are Microsoft's.

(I started with C++)

---

### Post by Mirrorball on 2007-04-21
> **Laxton14 said:**
> i would like to learn about a programming language that I could use with Ubuntu, Wine & Getting Windows applications to work with Ubuntu, or Device drivers(EX video cards, etc).
If those are your goals, you will have to learn C. It's a simple language, but writing a program in C is not simple. You could start with an easier language, such as Python, and then learn C later, when you know more about programming and computers, because contributing to wine and writing device drivers require advanced skills.

---

### Post by Laxton14 on 2007-04-21
Thanks for all of the suggestions.. it looks like ill start messing around with python then try to move to a more complicated language... C++ or something.. thanks again.

---

