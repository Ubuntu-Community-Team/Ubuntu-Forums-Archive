---
title: "TIOBE: Python is programming language of 2007!"
date: 2008-01-29
forum: Programming Talk
---

### Post by pmasiar on 2008-01-29
**Edit:** I mentioned it in my later comment, but to make it 100% clear, I'll repeat it here:

> Of course all such "popularity index" sites you need to take with a big grain of salt. But they do analyze a lot of data and don't want to be considered fools, so... Such guess is better than random guess based on thin air only.

More interesting than absolute numbers are trends over 5 years: we can assume that with fixed methodology, trends show genuine changes in whatever they measure.

===============

[TIOBE declares Python as programming language of 2007!](http://www.tiobe.com/index.htm?tiobe_index)
"Python has been declared as programming language of 2007. It was a close finish, but in the end Python appeared to have the largest increase in ratings in one year time (2.04%). There is no clear reason why Python made this huge jump in 2007. Last month Python surpassed Perl for the first time in history, which is an indication that Python has become the "de facto" glue language at system level. It is especially beloved by system administrators and build managers. Chances are high that Python's star will rise further in 2008, thanks to the upcoming release of Python 3."

"interesting trends can be derived from the 2007 data. First of all, languages without automated garbage collection are losing ground rapidly. (C/C++)"

"no breakthrough for D"

"What about 2008? C, C++ and Perl will continue to fall. C and C++ because they have no automated garbage collection. C++ will get an extra push down because Microsoft is not actively supporting the language anymore. Perl is just dead. Java and C# will eventually be the 2 most popular languages."

Found via [this blog](http://blog.delaguardia.com.mx/index.php?op=ViewArticle&articleId=99&blogId=1)

"Without all the hype of last years wunderkind, Ruby, Python advanced from 8th to 6th place, overtaking Perl for the first time ever. Ruby lost one place after Delphi (!) climbed from 12th to 9th place and pushed last years fastest growing language into the 11th position, behind Javascript."

Other interesting rapid mover is Lua, and [Factor](http://en.wikipedia.org/wiki/Factor_%28programming_language%29), started in 2003 by Russian hacker raised in NZ and Australia, and not yet in 1.0 version, started at #45!

---

### Post by xlinuks on 2008-01-29
Huh? Is Microsoft planning to abandon C++ for C#? Although on windows C# it's pretty fast, it's still far from the performance of languages like C/C++, or am I missing something?

---

### Post by Sockerdrickan on 2008-01-29
What? C++ going down?

---

### Post by cprofitt on 2008-01-29
I think Microsoft might be writing directly to CLR... but I could be wrong. They may internally write in C++ and C for things that need the speed, but I would imagine the bulk of the coding will be in C#.

---

### Post by xlinuks on 2008-01-29
> **PrivateVoid said:**
> I think Microsoft might be writing directly to CLR... but I could be wrong. They may internally write in C++ and C for things that need the speed, but I would imagine the bulk of the coding will be in C#.

Considering the "speed" of Windows Vista, perhaps it has been their first shot to replace C++ with C# (sarcasm implied)

---

### Post by Balazs_noob on 2008-01-29
> **xlinuks said:**
> Huh? Is Microsoft planning to abandon C++ for C#? Although on windows C# it's pretty fast, it's still far from the performance of languages like C/C++, or am I missing something?

you are missing that hardware is getting cheaper
and cheaper so it can take care of C#

clearly they need to write Operating Systems in C and
C++ for a while though( they have tried to write vista in C# and failed )

i think every programmer should learn C or a language
with memory management at least for educational
purposes....

---

### Post by cprofitt on 2008-01-29
> **xlinuks said:**
> Considering the "speed" of Windows Vista, perhaps it has been their first shot to replace C++ with C# (sarcasm implied)

I don't have any issues with my Windows Vista speed...

and I am only running it on an e6600 with 4gb of ram...

What you talkin' about Willis? :)

---

### Post by SOULRiDER on 2008-01-29
> **Balazs_noob said:**
> 
i think every programmer should learn C or a language
with memory management at least for educational
purposes....

I agree 100% on that.

---

### Post by lnostdal on 2008-01-29
intresting .. mmh .. i kinda wanna regard "java" to mean the same thing as "jvm", and use jython whenever ppl need stuff "written in java" ..  (or maybe clojure or abcl, later when they seem more mature) ..   think i could get away with that? :) .. think of the increase in programmer efficiency and all that

---

### Post by xlinuks on 2008-01-29
C/C++ will be there regardless of whether the hardware gets cheaper. C# and Java are still and will be programming langs for middleware for a long time. Umm.. startup time? waiting until JIT compiles the code into machine code? More memory usage? Increased background CPU usage because of the VM being busy compiling the code? And still roughly 50% of the speed of a C app?  That's what a programmer (like me) has gotta cope and live with (and that's why I decided to learn C++).
I wish Microsoft manages to write it's next OS in C#, we would have more ppl migrating to Linux :)

---

### Post by pmasiar on 2008-01-29
> **xlinuks said:**
> C/C++ will be there regardless of whether the hardware gets cheaper. 

Nobody argues with that. See Cobol at #15 and rising! TIOBE just argues that popularity of C++ is diminishing, being replaced by Java/C#, both languages with GC. of course there still will be areas where programmer will need to speed, and so will suffer the pain of manual memory management, TIOBE just argues that it makes less sense.

But if you look at 5 years trend for top players (C, C++, Java), all trends are down, being replaced by C# and dynamically typed languages.

And looks like Ruby's hype is over, people who left Python for Ruby on Rails are returning for Python with Django and/or TurboGears. If Perl is dead, Python is in the best position to replace it and become universal glue language.

Of course all such "popularity index" sites you need to take with a big grain of salt. But they do analyze a lot of data and don't want to be considered fools, so... Such guess is better than random guess based on thin air only.

---

### Post by pmasiar on 2008-01-29
> **xlinuks said:**
> I wish Microsoft manages to write it's next OS in C#, we would have more ppl migrating to Linux :)

You might be surprised, but MSFT are not total idiots. IronPython is in some benchmarks twice as fast as C-Python. They have lots of money and can hire lots of smart people. 

If IronPython will be fast enough, C# might become Assembly-level language for libraries, with most of high-level development done in high-level languages, with appropriate increase of developer's productivity. And remember, developer's productivity is something which did not increased according to Moore's law, where the biggest returns are. Especially for business customers (who pays us salary).

---

### Post by xlinuks on 2008-01-29
Assembly language for libraries they ain't gonna create, cause its pretty hard to track the OS/architecture in assembly, just cause its very much work to do to say the least. Java uses "assembly" but only for critical parts like System.arraycopy and alike. In rest it's what it is. We still have to have a look at the upcoming "Java Kernel" (if interested search for "Java update N"), see whether it's worth and how well it scales, and whether there will be performance downgrades (which is highly possible taking into consideration that the kernel will have to take care of all apps, not only one as until now).
MSFT is not quite the company who cares much about speed and system resources (should I give an example someone will prolly step in and actually call the black color white, but we all know what I'm talking about).

---

### Post by ThinkBuntu on 2008-01-29
These rankings are determined entirely by search results, so right off the bat they should be taken with a grain of salt. Also, although I think Python is a great language that's on the rise. There's no chance it has outstripped Perl in usage or, more importantly, in demand from employers. Once in a blue moon I stumble across a posting for a Python developer (or with Python as a required skill), on occasion I see Ruby show up for startups with Rails apps, but very often I see postings for Perl developers.

It will be some time before Python apps outnumber Perl ones in the wild.

---

### Post by jingo811 on 2008-01-29
> **pmasiar said:**
> 
........
........

And looks like Ruby's hype is over, people who left Python for Ruby on Rails are returning for Python with Django and/or TurboGears. If Perl is dead, Python is in the best position to replace it and become universal glue language.

Of course all such "popularity index" sites you need to take with a big grain of salt. 
........
........


Thanks for that observation I've been uncertain about which of those (Python or Ruby) to choose and focus on learning.

---

### Post by Lster on 2008-01-29
Python flying high: ;)

[http://www.xkcd.com/353/](http://www.xkcd.com/353/)

and

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=all)

:popcorn:

---

### Post by a9bejo on 2008-01-29
> **jingo811 said:**
> Thanks for that observation I've been uncertain about which of those (Python or Ruby) to choose and focus on learning.

And "Ruby's hype is over" has really helped you with your decision? 

Both languages are wide above "immortality" status, meaning that there are so many projects written in these languages that it is next to impossible that development will stop anytime soon.

And none of them has a significantly better chance of becoming one of the 5 or so mainstream languages that are seriously considered by the majority of the industry.  Both have some backup by big software vendors and both have lots of large projects and great developers that could give the language a lift to the top.  Both have lots of competition from many thousand of other languages that could become "the next Java" in 5 years. 

If you don't know which of these languages you should learn first: Toss a coin, or pick the one that you think has the cooler logo.  It really doesn't matter that much.  Just be sure you pick one that it is fun to code with.

---

### Post by Miriam77 on 2008-01-29
> **a9bejo said:**
> 
If you don't know which of these languages you should learn first: Toss a coin, or pick the one that you think has the cooler logo.  It really doesn't matter that much.  Just be sure you pick one that it is fun to code with.

I read the stickies and found a poll and discussion on what language is best to learn at first. I agree that it really doesn't matter, because you should learn more than one anyway, but I wouldn't toss a coin over the advice of more experienced people.

It seem that you quoted an experience programmer who happens to be a Python advocate. I don't think Ruby is dead either, Python is getting perhaps a bit more attention, but Ruby is growing too: [http://en.wikipedia.org/wiki/IronRuby](http://en.wikipedia.org/wiki/IronRuby). If Microsoft sees a reason to give it attention and contribute to development in open source it probably isn't dying. (Please don't flame Microsoft, they are doing it for Python also)

---

### Post by jingo811 on 2008-01-29
......
......
> If you don't know which of these languages you should learn first: Toss a coin, or pick the one that you think has the cooler logo. It really doesn't matter that much. Just be sure you pick one that it is fun to code with.
Not learn first!  Which language to focus and dedicate my life to.  I'm a slow learner I don't have the skill to switch language like switching clothes.


Never mind I found this.  Educational was what mattered to me the most so Python it is.
[http://en.wikipedia.org/wiki/Comparison_of_programming_languages](http://en.wikipedia.org/wiki/Comparison_of_programming_languages)
> 
[LIST]
**[*]Language**
Python
**[*]Intended use**
Application, Educational, Scripting
**[*]Design goals**
Simplicity, Readability, Expressiveness, Modularity
[/LIST]

[LIST]
**[*]Language**
Ruby
**[*]Intended use**
Application, Scripting, (Good Web Support)
**[*]Design goals**
Expressiveness, Readability
[/LIST]

---

### Post by pmasiar on 2008-01-29
> **Miriam77 said:**
> I read the stickies and found a poll and discussion on what language is best to learn at first. I agree that it really doesn't matter, because you should learn more than one anyway, but I wouldn't toss a coin over the advice of more experienced people.

"first language to learn" and "TIOBE language of the year" are two completely different categories (judged by different metrics), which this year happen to have the same winner.

BTW Python was designed be easy to learn. Ruby was designed to be fully OOP and poweful, as Perl replacement.

> I don't think Ruby is dead either, Python is getting perhaps a bit more attention,

You are first person claiming that "Ruby is dead". I mentioned that: "Perl (might) be dying, according to TIOBE, which poll needs to be taken with a grain of salt." Obviously Perl will be dying for quite a long time - maybe next 10 years. It is still quite productive language (for me), compared to Java :-)

And I think that attention to Python is well deserved, it is the same attention what was directed to Ruby because of the Rails. But there was no hype about the Python - only quiet growth.

I believe (and might be wrong) that efforts of bigger (than Ruby's) Python community is being felt now. Python has BSD-licensed e-shop, Satchmo ( [http://www.satchmoproject.com/](http://www.satchmoproject.com/) ) and less free TinyERP ([http://en.wikipedia.org/wiki/Tiny_ERP](http://en.wikipedia.org/wiki/Tiny_ERP) ). Those are not frameworks but solutions.

---

### Post by a9bejo on 2008-01-29
There are of course differences between both languages (I wrote about some of them [here](http://blog.bookworm.at/2007/01/ruby-python-compared_2902.html)). But none of these are really significant compared to, let's say, the differences between python and Haskell.  If you know that it will be either Ruby or Python, it really doesn't matter which one you choose. Both languages are similar enough that they are suitable for mostly the same problem domain.

Both languages are dynamic, object oriented languages with functional features and a large pool of great libraries.  Both have a active community and are reasonable efficient. Both can talk to C. Both have active Java implementations. Both have .NET implementations.  Both languages are good entry languages to learn programming.  Both are a pleasure to use.


Just pick one.  If yout really cannot decide which you want to learn first, read [The Paradox of Choice](http://www.amazon.com/Paradox-Choice-Why-More-Less/dp/0060005688). Then toss a coin and pick one.

---

### Post by jingo811 on 2008-01-29
Ay ay captain!  This will be a close one like Hilary and Barak :)

---

### Post by pmasiar on 2008-01-29
> **a9bejo said:**
> If you don't know which of these languages you should learn first: Toss a coin, or pick the one that you think has the cooler logo.

This is rather silly advice. Even if both languages are very close in expressive power, there **ARE** substantial differences

In style:
- Python was designed as easy to read and learn: "programs are for communicating between people first, and only after that to computers"
- Ruby was designed as fully OOP Perl replacement, with quite a few of the Perl's warts.

In speed: Python is 2-3 times faster (still slower that C or java, but faster that Ruby)

In community: Python has bigger community, as a result more libraries available, more and better books (also free) etc.

For application programming, I would prefer Ruby over Java, but Python over Ruby or Perl.

Also, big important companies voted for Python as their main scripting language: Google, Canonical. So Python (and not Ruby) is main development language for ubuntu enhancements. Competition was not decided yet, but trend is clear, at least for me :-)

BTW thanks for link to your blog, interesting comparison of features. I still stay with Python :-)

---

### Post by Miriam77 on 2008-01-29
> **pmasiar said:**
> 
You are first person claiming that "Ruby is dead". I mentioned that: "Perl (might) be dying, according to TIOBE, which poll needs to be taken with a grain of salt." Obviously Perl will be dying for quite a long time - maybe next 10 years. It is still quite productive language (for me), compared to Java :-)

And I think that attention to Python is well deserved, it is the same attention what was directed to Ruby because of the Rails. But there was no hype about the Python - only quiet growth.

I believe (and might be wrong) that efforts of bigger (than Ruby's) Python community is being felt now. Python has BSD-licensed e-shop, Satchmo ( [http://www.satchmoproject.com/](http://www.satchmoproject.com/) ) and less free TinyERP ([http://en.wikipedia.org/wiki/Tiny_ERP](http://en.wikipedia.org/wiki/Tiny_ERP) ). Those are not frameworks but solutions.

Sorry, I was distracted. I misinterpreted the hype being over when I typed that.

I am not experiened in Ruby, so I don't know what kind of growth is going on, but it seems from my brief research it will continue to grow.

---

### Post by jingo811 on 2008-01-29
If I choose Python I can keep using LAMP if I use Ruby Microsoft lovers might start calling me a LAMeR that's no good for me :) still undecided though need more insider info from programming teacher.

---

### Post by pmasiar on 2008-01-29
> **jingo811 said:**
> If I choose Python I can keep using LAMP

For learning, your life with Python might be even simpler: use SQLite for database (it is a single-user library, not a full server), and development web server which comes with Django or TurboGears.

Follow tutorials, you will have your first web app up-and-running within an hour, including download! :-)

BTW don't use apt/synaptic to install TG: easy_install/tg-install is as simple, and loads correct packages (correct dependencies).

---

### Post by a9bejo on 2008-01-29
[link](http://blog.bookworm.at/2007/01/ruby-python-compared_2902.html).

> **pmasiar said:**
> 
- Python was designed as easy to read and learn: "programs are for communicating between people first, and only after that to computers"

This is the idea behind about every modern programming lanuage, including Ruby.  The only difference is that each language designer has a different idea what language features help to make code easy to read.

> **pmasiar said:**
> 
- Ruby was designed as fully OOP Perl replacement, with quite a few of the Perl's warts.


No, Ruby shares some syntax from perl, but none of its warts.  It is not a replacement for Perl.  If fact, Ruby is much closer to Smalltalk than it is to any other language.  

> **pmasiar said:**
> 
In speed: Python is 2-3 times faster (still slower that C or java, but faster that Ruby)


Languages cannot be fast. Implementation can be.  The current release of CRuby (1.9) has become even faster than Python. JRuby vs Jython, I don't know.  Not that this would really matter.  The Speed of language implementations increases with time.  Lisp used to be damn slow in the 50ties, and now there are Lisp compilers that optimize lisp code close to c.

> 
In community: Python has bigger community, as a result more libraries available, more and better books (also free) etc.


Python used to have a larger community when I started with Ruby.  Then the rails hype changed all that, and today it really does not make that much of a difference.  

Sun is paying the JRuby developers full time to work on the Ruby Java implementation.  Unlike Jython or Rhino, they do not port just the language, but the whole ruby platform to Java.  

**There are as many libraries for your language as there are libraries for the platform it runs on. **

> 
Python (and not Ruby) is main development language for ubuntu enhancements


That's, of course, a good reason to learn python ;) 


I did not say that there are no differences.  What I did say is that if you choose between these two languages, it does not make much of a difference.  You are not more or less productive in one compared to the other, and are both good for the same type of programs.

---

### Post by jingo811 on 2008-01-29
And SUN Microsystems just recently bought MySQL AB in mid January 2008.  Getting started with Ruby might not be so bad after all in the future.  There might be some job opportunities there.
Is there a big difference between Ruby and Ruby on Rails?  Like the difference between C and C++.

---

### Post by pmasiar on 2008-01-29
All this is nitpicking, getting last 5% of differences, splitting hairs, but there it goes: 
> **a9bejo said:**
> The only difference is that each language designer has a different idea what language features help to make code easy to read.


Guido participated in rather extensive [research project about language ABC](http://www.artima.com/intv/python.html) for intelligent users, so Python is based not only on personal preferences, but on real research (and failed project).


> No, Ruby shares some syntax from perl, but none of its warts.  It is not a replacement for Perl.  If fact, Ruby is much closer to Smalltalk than it is to any other language.  

Might be true. I know Perl, but not Smalltalk, and I love code structure by whitespace, no braces :-)

> Languages cannot be fast. Implementation can be. 

Agree 100%

> Sun is paying the JRuby developers full time to work on the Ruby Java implementation.  Unlike Jython or Rhino, they do not port just the language, but the whole ruby platform to Java.  

Yes, and if Sun supported Jython 10 years ago, main Jython developer would be not working on IronPython for .NET and improving .NET CLI, and Java would have much better competing position against C#. MSFT proved whey do have a clue, Sun lost big time and has to catch up now. And yes, I am pissed off on Sun. :-)

BTW Google is paying Python developers, and Google is richer than Sun :-)

Summary: only time will tell. year 2007 went to Python, next year might go to Ruby. We shall see. I'll keep you posted :-)

---

### Post by a9bejo on 2008-01-29
> **pmasiar said:**
> 
Yes, and if Sun supported Jython 10 years ago, main Jython developer would be not working on IronPython for .NET and improving .NET CLI, and Java would have much better competing position against C#. 


Well, Java already has  a very good stand today against .NET, but I agree with you: Sun or IBM should have invested in jython development years ago.  However, Jython was reborn in 2007 and the project is very active again.  And the Jython, JRuby, Rhino, Groovy and Nice people all seem to be working close together these days.

Btw: My tip for the hype language of 2008 is [Scala](http://www.scala-lang.org/).  Nice is going to get a lot of attention from both the Java people and the functional programming community this year. Pretty much as Erlang got a lot of buzz in 2007.

---

### Post by aks44 on 2008-01-29
Just a few thoughts... (I *had* to chime in ;))

> **pmasiar said:**
> languages without automated garbage collection are losing ground rapidly. (C/C++)
Are you aware that C++ *will* have integrated GC in the upcoming standard (C++0x, which is quite advanced now)? Fortunately the standard allows GC to be disabled. This has two big advantages :
- claims that C++ is not a "modern" language anymore "because it has no GC" will be easily dismissed
- people who need to do serious work (ie. the vast majority of C++ users) will still be able to avoid that nonsense :p


> **pmasiar said:**
> [QUOTE=xlinuks;4229685]I wish Microsoft manages to write it's next OS in C#, we would have more ppl migrating to Linux :)
You might be surprised, but MSFT are not total idiots.[/QUOTE]
That's why their "next OS in C#" (the research project called "Singularity") dismisses the concept of shared libraries in favour of static libraries (AFAIK that thing doesn't even support libraries, only monolithic executables). Talk about an enhancement... </sarcasm>


Just my two cents (I know, I said I'd try to avoid posting opinions but I just couldn't resist ;)).

---

### Post by Geekkit on 2008-01-29
If you go to the link and read carefully what this site is stating, they say:

> The popular search engines Google, MSN, Yahoo!, and YouTube are used to calculate the ratings. Observe that the TIOBE index is not about the best programming language or the language in which most lines of code have been written.

So in reality this rating is absolutely meaningless when it comes to determining whether or not a certain programming language has business utility (i.e., will get you a job in the industry) or whether or not the language is the most commonly used (i.e., more people use this language than any other language currently being used to program computers).

Statistics can be a very powerful tool but can be misinterpreted quite easily and thus used to skew reality - just ask any politician running for (re)election.

EDIT: all this site suggests is that Python gets the most search engine and YouTube hits, nothing more.

---

### Post by pmasiar on 2008-01-29
I really liked how we avoided flamewars, explained our positions, supported them with links, pointed out misunderstandings, and agreed where possible, and agreed to disagree where we have different opinions/preferences. Almost like a grownups! :-)

Maybe we can post our own bets to language which will improve position substantially?

My bets are:
- [Scala](http://en.wikipedia.org/wiki/Scala_%28programming_language%29) , because it unites functional paradigm (important for multicores) and OOP, and runs on JVM
- [Factor](http://en.wikipedia.org/wiki/Factor_%28programming_language%29) because inherits from Forth, which was cool language in '80s which missed it's chance. And Factor has way coolest logo of all languages :-)

And year from now, if someone remembers this thread, we can look how smart or stupid our guesses were.

---

### Post by 1337455 10534 on 2008-01-29
Here is why Python is my favorite;
1. Great support (online docs, Dive into Python, etc.)
2. Flexibility (any newbie can create a functional GUI in a day; wxGlade etc.)
3. Power (hundreds of modules)
4. Speed (as in time of devlopment. its execution speed isnt bad either)
5. Ease of use. No pointer math, and no need to declare a variable before you use it.

Last year, we had a row of Javascript projects at the Science Fair. And now Python is used by approx 60% of high school geeks. Albeit, 50% of that is 'look i made a calculator in IDLE', but its an improvement over 'look i made a javascript alert *[IE randomnly crashes]*'

---

### Post by pmasiar on 2008-01-29
I agree with 50% of the latest comments  of both Geekkit and aks44.

aks44: Optional GC in C++ is interesting for peole who can use it. And I do not think that OS in C# will be very good - but Vista is crap, and people buy it anyway. :-)

As they say, the only MSFT product which does not suck is vacuum :-)

Geekkit: I think it was Churchill who said "I believe only the statistics which I personally cooked"  or something like that :-)

But TIOBE goes beyond YouTube. Maybe not too far, but beyond. :-)

---

### Post by Geekkit on 2008-01-30
> **pmasiar said:**
> Geekkit: I think it was Churchill who said "I believe only the statistics which I personally cooked"  or something like that :-)

Heh, I like that. It reminds me of what my statistics instructor from college told the class one day.

He said, "Did you know that 37.5 percent of all statistics are made up on the spot?"

The marketing students were busy writing that down while us "computer nerds" were chuckling. Also reminds me of that adage about binary:
There are only 10 types of people in the world: those that understand binary and those that don't.  ;)

As far as the whole language thing goes, I like to think of myself as programming language agnostic: I use the language that suits the task at hand.

---

### Post by LaRoza on 2008-01-30
> **Geekkit said:**
> 
There are only 10 types of people in the world: those that understand binary and those that don't.  ;)

As far as the whole language thing goes, I like to think of myself as programming language agnostic: I use the language that suits the task at hand.

"There are 10 types of people in the world, those understand trinary, those that don't and those that confuse it with binary"

"There are three types of lies: lies, damned lies, and statistics" (Mark Twain?)

What editor do you use? Surely you are at least a half normal programmer who has a religious devotion to an editor?

---

### Post by Geekkit on 2008-01-30
> **LaRoza said:**
> "There are 10 types of people in the world, those understand trinary, those that don't and those that confuse it with binary"

"There are three types of lies: lies, damned lies, and statistics" (Mark Twain?)

What editor do you use? Surely you are at least a half normal programmer who has a religious devotion to an editor?

I hadn't heard the trinary adage, that one is funny. :)

As for editors. I'll admit I have an affinity towards Geany in Linux and EditPlus in Windows. I like nice and simple (goes well with my mind). I'll use Netbeans 5.5 if I have to for larger projects especially those requiring UML diagrams although I'm deeply disappointed with NetBeans 6.0 since it's such a horrible bloated pig on memory, crashes, and takes forever and a day just to load up. If I need to do XML Schema stuff (with pretty diagrams), I've decided to use Eclipse. It has a nice plugin to do that. I guess that makes me rather IDE promiscuous but that most likely stems from a bad childhood filled with uncertainty and a lot of moving around.

---

### Post by LaRoza on 2008-01-30
> **Geekkit said:**
> 
As for editors. I'll admit I have an affinity towards Geany in Linux and EditPlus in Windows. I like nice and simple (goes well with my mind). I'll use Netbeans 5.5 if I have to for larger projects especially those requiring UML diagrams although I'm deeply disappointed with NetBeans 6.0 since it's such a horrible bloated pig on memory, crashes, and takes forever and a day just to load up. If I need to do XML Schema stuff (with pretty diagrams), I've decided to use Eclipse. It has a nice plugin to do that. I guess that makes me rather IDE promiscuous but that most likely stems from a bad childhood filled with uncertainty and a lot of moving around.

You can use Geany in Windows too.

You are avoidig the issue, which is it...Vim or Emacs. You can't avoid this. :)

---

### Post by Geekkit on 2008-01-30
> **LaRoza said:**
> You can use Geany in Windows too.

You are avoidig the issue, which is it...Vim or Emacs. You can't avoid this. :)

You really had to bleed that out of me didn't you? ;) Okay, I'll admit, I hate Vi - never liked it. Emacs forever!!!

<insert Dr. Evil-like laugh>

---

### Post by LaRoza on 2008-01-30
> **Geekkit said:**
> You really had to bleed that out of me didn't you? ;) Okay, I'll admit, I hate Vi - never liked it. Emacs forever!!!

<insert Dr. Evil-like laugh>

Good thing I swore to uphold and follow the Ubuntu Code of Conduct...

I'll be watching you :evil:

<footnote>
I am not serious. I am joking here :)
</footnote>

---

### Post by Wybiral on 2008-01-30
> **LaRoza said:**
> You are avoidig the issue, which is it...Vim or Emacs. You can't avoid this. :)

Out of those two... I'd say Gedit :)
(I've warmed-up to eclipse recently as well)

---

### Post by mssever on 2008-01-30
> **jingo811 said:**
> Is there a big difference between Ruby and Ruby on Rails?  Like the difference between C and C++.
Rails is a framework that uses Ruby. It's still Ruby, but Rails adds and shapes Ruby through extensive use of metaprogramming. In effect, Rails implements a domain-specific language based on Ruby. But, it's still Ruby.

---

### Post by Balazs_noob on 2008-01-30
I am the only one surprised to see Delphi at 9 ??
AFAIK Delphi is not a programming language it uses
[object pascal]("http://en.wikipedia.org/wiki/Delphi_%28programming_language%29")

---

### Post by LaRoza on 2008-01-30
> **Balazs_noob said:**
> I am the only one surprised to see Delphi at 9 ??
AFAIK Delphi is not a programming language it uses
[object pascal]("http://en.wikipedia.org/wiki/Delphi_%28programming_language%29")

Read the article again. It says it is called Delphi in certain contexts.

---

### Post by a9bejo on 2008-01-30
> **pmasiar said:**
> My bets are:
- [Scala](http://en.wikipedia.org/wiki/Scala_%28programming_language%29) , because it unites functional paradigm (important for multicores) and OOP, and runs on JVM


+1 for Scala.  When I wrote about the Nice language earlier, I really meant Scala.

---

### Post by a9bejo on 2008-01-30
> **Geekkit said:**
> 
So in reality this rating is absolutely meaningless when it comes to determining whether or not a certain programming language has business utility (i.e., will get you a job in the industry) or whether or not the language is the most commonly used (i.e., more people use this language than any other language currently being used to program computers).


Well, I wouldn't call it excactly 'meaningless'. the TIOBE index alone might not be that interesting, but, together with other stuff, it can give you a pretty good idea which languages are used and which gaining in popularity. 

Statistics about job offers only reflect the current market situation for the first N languages.  They usually ignore most of the activity behind the top 5 languages and software platforms.

Statistics about Booksales/Publications and Web statistics(like TIOBE) are (somewhat weak) indicators, but if you combine all the numbers, you can get an idea of how the big picture looks like.  Statistics from open source hosting services can be quite interesting too.


Of course, the error rates are usually high.  To be language 17 in an index is no guarantee that the language is more popular than the language at position 27.

---

### Post by CptPicard on 2008-01-30
> **pmasiar said:**
> [Scala](http://en.wikipedia.org/wiki/Scala_%28programming_language%29) , because it unites functional paradigm (important for multicores) and OOP, and runs on JVM...

I just spent the evening quickly reading through Scala's tutorial document and considering that I'm mostly a Java guy who has been looking for something "cool to hack in" for the JVM (which plain Java certainly is not), I must admit I'm really drooling now and Scala might even steal me away from Python from now on :) 

First-class functions, closures and even currying(!!) are the sort of features you just can't live without after getting used to thinking in terms of them. And  with the ever-increasing number of cores on CPUs, ease of parallelization by high-level abstraction is going to be more important in high-performance computing than tweaking the number of cycles the single core has to handle.

I must admit that for some reason my eyes glaze over when reading Scala source... it does somehow look a bit "noisy" and non-obvious to parse. And I just hate the separate **var**/**val**/**def** declarations, but I suspect those provide optimization hints as they seem to guide lazy/eager evaluation... I'll get over those. I almost got over Python's whitespace, after all.

---

### Post by Geekkit on 2008-01-30
> **LaRoza said:**
> Good thing I swore to uphold and follow the Ubuntu Code of Conduct...

I'll be watching you :evil:

<footnote>
I am not serious. I am joking here :)
</footnote>

To be honest, I haven't used EMACS in ages. I really have gotten quite comfortable with Geany.

8)

---

### Post by LaRoza on 2008-01-30
> **Geekkit said:**
> To be honest, I haven't used EMACS in ages. I really have gotten quite comfortable with Geany.

8)

Good, you are half way there.

```

sudo aptitude install vim-full

```

---

