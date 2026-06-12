---
title: "My first C prog"
date: 2007-10-14
forum: Programming Talk
---

### Post by ashvala on 2007-10-14
Dear Ubuntu Programmers,

I am  an aspiring programmer from India can anyone help me in programming?

---

### Post by Wybiral on 2007-10-14
I advise you pick an easy high level language and get the basics down. Python is a good choice (lots of support, easy, and useful). Grab some good tutorials on the web, and get started.

---

### Post by ashvala on 2007-10-14
ain't there anything else other than Python?

---

### Post by CptPicard on 2007-10-14
No, there isn't, there ist only van vei to do it richtig... ;)

(Seriously, check out Ruby or Java, whichever you feel comfortable with...)

---

### Post by ankursethi on 2007-10-14
I'm also an *aspiring programmer from India* :). Hello there.

I learnt C first. It's small, simple and doesn't do hand holding like Python. Then I moved on to Python. They teach C++ at school, so I've learnt enough to keep those idiots happy. I really don't like that language.

Anyway, get "Let Us C" by Yashwant Kanetkar for a very gentle yet complete introduction to programming. It even goes on to teach you a bit of GTK+/Win32 programming. It's the only book which can be found at any damned bookstore back here. Also try getting "The C Programming Language". It'll be tough to find, since it's not that commonly available. Try one of those stores that sell college books.

You can learn Python online at Python.org.

---

### Post by gnusci on 2007-10-14
Check the Sticky Threads:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Especially:

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)
[http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)

---

### Post by pmasiar on 2007-10-14
wiki in my sig has plenty of links to get you started with Python.

ankursethi is righ, if you want to learn "bottom up", start with C: the hard way, as we oldtimers did :-) Nothing makes you appreciate simple language where beginner can be productive in weeks (as Python is) like trying to understand some cryptic errors (for beginner) when you want just to parse simple text file in C. 

Check [http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/) for example how different languages handle simple task (writing of text of simple song) to get idea how different  languages look  like.

---

### Post by CptPicard on 2007-10-14
Python would be great if only it didn't have some really weird dogmatic choices in it... for example some common [simple]("http://mail.python.org/pipermail/python-list/2003-July/216777.html") [idioms]("http://mail.python.org/pipermail/python-list/1999-October/013778.html") don't work. You might want to look at Ruby so you don't get indoctrinated too much by Guido's Style Guide ;) Knowing several languages is a plus anyway, and eventually, you will...

---

### Post by pmasiar on 2007-10-14
Does Ruby assignment returns a value? 

I think you are too attached to your C in first idiom: in fact, it is not obvious why assigment **should** return a value at all. Why?

Second example is just a matter of taste. Not to have to deal with TIMTOWDI is one of the reason which I like in Python, after struggling with it in Perl.

---

### Post by CptPicard on 2007-10-14
> **pmasiar said:**
> Does Ruby assignment returns a value?

Yes Sir. :)

> 
I think you are too attached to your C in first idiom: in fact, it is not obvious why assigment **should** return a value at all. Why?

Because it is a convenient side effect that comes with no real cost, and that allows for such a convenient idiom.

> Second example is just a matter of taste.

Having to "break" out of stuff or to write contrived conditions at the top with possibly extra state variables is ugly, no matter how you look at it, IMO.

Your pragmatism over purity seems to be slightly relative at times.. ;)

---

### Post by aks44 on 2007-10-14
> **pmasiar said:**
> I think you are too attached to your C in first idiom

In fact, this kind of code is often flagged as a warning by decent compilers (at least C++ ones) because there's too much ambiguity between **while (x = y)** and **while (x == y)**. It could be a typo, and if it's not one it's very easy to overlook when doing maintainance. Just like fallthrough cases, assignments within loop conditions (or if conditions for that matter) are considered a bad programming practice (they should be avoided at all costs, and be extensively commented if used anyway).


> **pmasiar said:**
> Second example is just a matter of taste.

Not only a matter of taste... Having to duplicate some of the loop body to initialize the variables is, just like any code duplication, error-prone. That's why IMHO do-while loops make as much sense as while loops, or even for loops. They just don't serve the same purpose, each one is quite idiomatic.


> **pmasiar said:**
> Not to have to deal with TIMTOWDI is one of the reason which I like in Python

Do you use for...in loops? You should stop using them then, they could be replaced with while loops and it certainly would be less confusing... :twisted: ;)

---

### Post by Wybiral on 2007-10-14
> **CptPicard said:**
> Because it is a convenient side effect that comes with no real cost, and that allows for such a convenient idiom.

Well, it does come at the cost of being error prone for beginners.

When you mean:
```
while x == 1
```

But you accidentally end up with:
```
while x = 1
```

That small difference can be a nightmare for a new programmer to find.

---

### Post by CptPicard on 2007-10-14
People aren't beginners forever, and the 

```

while ((x = get()) != null)

```

idiom is very recognizable for anyone who uses it... in addition, I do *not* think anything else than a boolean should be valid inside a condition, so that makes this substantially more safe...

---

### Post by Wybiral on 2007-10-14
> **CptPicard said:**
> People aren't beginners forever

But this thread is for a beginner. It's also such a minor detail that I personally don't see any reason to "use ruby" instead (because of a couple beginner friendly design choices Guido made). If you want to use ruby, fine, but this is really a trivial reason to do so. I would do much more research into the language.

Personally, as a beginner I would suggest choosing the language with the most support. How many sites offer tutorials? How easy is it to find example code? How many books can you find written on it? Those are more important for a beginner than simple style choices. You can always learn a new language once you understand basic programming concepts. Learning new languages gets easier and easier. But pick one that you can guarantee tons of examples and support to get you started.

---

### Post by CptPicard on 2007-10-14
Actually, I agree with you about Python... and I suggest it to n00bs myself too. However, this one in particular asked if there isn't anything else around, so I just had to answer *that* question -- with my mind on the idea that there is just one way to do it... ;)

And of course, this time for trolling pmasiar out of his coding basement I wanted to try something a bit different from semantic whitespace :D

---

### Post by avik on 2007-10-14
Python and Ruby are both great.  The [Pickaxe book]("http://www.rubycentral.com/pickaxe/") is great for beginners, and it covers Ruby.  It's just another choice.  I myself am partial to Ruby, but either one works.

---

### Post by pmasiar on 2007-10-14
I am thinking if it would be feasible to have one sticky thread "what you love/hate about Python" and redirect therse OT discussions there. Then again, I cannot make it happen... :-/

---

### Post by mjwood0 on 2007-10-15
> **Wybiral said:**
> Personally, as a beginner I would suggest choosing the language with the most support. How many sites offer tutorials? How easy is it to find example code? How many books can you find written on it? Those are more important for a beginner than simple style choices. You can always learn a new language once you understand basic programming concepts. Learning new languages gets easier and easier. But pick one that you can guarantee tons of examples and support to get you started.

I couldn't agree more -- and that said, I'd have to go with C / C++ or Java.  There seem to be many more resources for these than either Ruby or Python.

---

### Post by LaRoza on 2007-10-15
> **mjwood0 said:**
> I couldn't agree more -- and that said, I'd have to go with C / C++ or Java.  There seem to be many more resources for these than either Ruby or Python.

Python has quite a bit: [http://docs.python.org/lib/](http://docs.python.org/lib/), and those are just the standard.

There are many tutorials and books that use Python, finding decent Python tutorials is much easier than a good C tutorial. Many C tutorials are out of date.

Regardless of what language you start with (you'll end up learning many of them), I have attempted to gather good references and tutorials in my wiki for many languages, including C, Java and Python.

---

### Post by pmasiar on 2007-10-15
Sticky in this forum had enough links to keep you busy for years. 

C and C++ are very different languages which share parts of grammar, but you get confused really quickly if you mix them like that. Some experts, like aks44, are probably already upset about that :-)

For java, sun website covers you for another couple years.

Bigger problem is: Google will dig you too many sources, not too few. :-) Befriend Google and wikipedia, and you never need to ask "where to start looking for...".

---

### Post by mjwood0 on 2007-10-15
> **pmasiar said:**
> C and C++ are very different languages which share parts of grammar, but you get confused really quickly if you mix them like that. Some experts, like aks44, are probably already upset about that :-).

I tend to disagree.  C and C++ are very similar languages with different methodologies.  The underlying language is very similar.  In many ways, C is a subset of C++. 

I'm sure the following may offend people, but I personally think it's critical to learn C before an object oriented language such as C++.  Otherwise, what the compiler is doing behind the scenes gets obscured from your mind and you really loose touch with what's happening.  Then again, I also think people should have a basic understanding of assembly and architecture if you want to call yourself a programmer.

But again, that's just me.

---

### Post by pmasiar on 2007-10-15
> **mjwood0 said:**
> people should have a basic understanding of assembly and architecture if you want to call yourself a programmer.

I agree with you. But there should be difference between "programmer" and "computer scientist". I think you should have  used "computer scientist" instead.

90% of users who would profit from ability to write their own programs (in Python they can) don't consider themselves programmers (they don't write programs for living - they just use computers, and need to process own data, by hacking snippets of own code). Wouldn't it be funny  if astronomers have "plain" astronomers, and "real telescopers" with deep understanding how telescopes works? Or biologist had "microscope science"? If we tell that "every biologist needs to understand how electron microscope or mass spectrometer works, before is allowed to use it"?

For most people, programming should be a tool to solve **their own** problems, and not computer science problems. Of course, we are far away from that ideal, and so far other computer users let us (programmers) to impose our own priorities on them. But it is unhealthy situation and needs to change, and not be perpetuated.

Of course there should be people who DO understand how to build and calibrate electron microscope. But they are slight minority of people who will ever use it. Same with use in computers, IMHO. many people will be "programmers" (writing programs for their own use, but in Python or like, and NOT in C), but only very little minority will be computer scientists (who better know C inside and out).

---

### Post by mjwood0 on 2007-10-15
Reading your reply, I can certinally understand that.  And in may regards, I agree.

My main reason for using Linux is to further my understanding of system integration -- getting everything working together.  I've also been studying the kernel development with interest as I'm interested in these types of problems.  On the other hand, writing a gui application seems so cumbersome to me that I have never actually finished one.  

Different strokes for different folks!  But yes, I do see and agree with your point.

---

### Post by CptPicard on 2007-10-15
I would have to pretty strongly disagree on the other hand ... computer scientists are not computer engineers. Computer scientists need, at a minimum, a sharp pencil and lots of paper, but of course having a computer makes things much easier.

I really, really dislike computer science being likened to just programming, even if it is "professional" programming... it is a study of what kind of programs solve which problems how well (if at all) on top of what sort of computing devices (even abstract ones).

Assembly is equivalent to higher-level languages as there is just a transformation between the two. You are essentially just programming inside a slightly different environment, but there isn't even anything fundamentally different in the theory sense.

If you look at things from a classical algorithmics perspective, there is no need to know assembly before you move into your typical OO oriented language. The interesting bits are somewhere entirely different than the CPU's instruction set, and all you really need to know is that "the compiler produces a binary the CPU can understand", and perhaps the basic idea of what it does with that binary. In order to get going with computer science concepts, even that understanding is not neccessary if you're willing to accept there is a "cost" to operations.

Sure, I have written some C in my life and can passably read assembly, but my CS degree's contents were mostly gained by analysing some algorithm on paper, really, and reading books...

Dijkstra was right when he said that "computer science is as much about computers as astronomy is about telescopes"... which is probably what pmasiar had in mind there :)

---

### Post by pmasiar on 2007-10-15
If you can do it without computer, it hardly can be "computer" science, no? Maybe it should be called "algorithm analysis"? Of course all this is mixed together now, and I do mot claim that me definitions are the only one possible, or even optimal.

But we can agree that if medical industry had it as mixed together as computer has right now, people would ask dentist to make bypas or glass prescription, and gynecologist to fix broken bone. After all, it is all health-related? :-)

And yes, I often re-read Dijkstra, and that reference to "telescope science" struck me as relevant.

I am pragmatist. I want real-life problems to solve. I get too bored whan reading  about algorithms per se. I liked to compete in math competitions (solving abstract problems on paper), but it was many olympics ago :-)

---

### Post by CptPicard on 2007-10-15
> **pmasiar said:**
> If you can do it without computer, it hardly can be "computer" science, no?

Yeah, in that sense the term is a bit problematic, but... when you've got an algorithm, you are making an assumption of a computation device... a computer of some kind. An algorithm is not an algorithm if it has some magical step that says "and then we just figure this out" :)

---

### Post by hod139 on 2007-10-15
To quote myself
> **hod139 said:**
> I think a lot of people forget that computer science != computer programming.  Computer science is a **science** and it does not depend, nor should it, on a programming language. It is the systematic study of computation. One topic of the many is programming languages (and even that is theoretical which should start at lambda calculus). More important topics are abstract concepts like algorithms and data structures, grammars, program design, architecture, and theory of computation. Then there are field specific topics like parallel/concurrent/distributed systems, databases, artificial intelligence, graphics, etc.


Mathematicians were studying many parts of what we would call computer science now long before there were any computers.

---

### Post by pmasiar on 2007-10-15
I can understand that a person in India is more interested in language like Java, C or C++, because it is more likely s/he will encounter it at job. 

One reason might be that Java/C/C++ development is slow and expensive, so is outsourced, and to keep your job outside of India, you should look at faster, more agile ways to deliver solutions to your boss, like Python?

> **mjwood0 said:**
> I'd have to go with C / C++ or Java.  There seem to be many more resources for these than either Ruby or Python.

One of the reasons (at least for python and for me) might be that I needed substantially less resources to get started with Python than with Java. Java is just so byzantine complicated. My "Java in a nutshell, 1.3" has 646 pages of standard format, "Python pocket reference" (2.4) has 148 pages, and pages are half the size. You need many more books to get reasonable comprehension of Java than for Python.

I would like to move further discussion to [Why to love/hate Python](http://ubuntuforums.org/showthread.php?t=576690) which I created to avoid polluting other threads.

---

### Post by aks44 on 2007-10-15
> **mjwood0 said:**
> In many ways, C is a subset of C++.

And the fact that C++ is a *superset* of C makes it a *totally* different language... ;)

(yeah, I couldn't help biting the bait LOL)



> **mjwood0 said:**
> I'm sure the following may offend people, but I personally think it's critical to learn C before an object oriented language such as C++.  Otherwise, what the compiler is doing behind the scenes gets obscured from your mind and you really loose touch with what's happening.  Then again, I also think people should have a basic understanding of assembly and architecture if you want to call yourself a programmer.

I'd agree with the general idea, but IMHO C is not critical at all. On the contrary, you'd gain much more (at least as far as C++ goes) learning plain old assembly than learning C. The problem with learning C before C++ is that many (not all, mind you) people tend to use inappropriate C idioms when writing C++ code, which leads to very low-quality (not to say crappy) code.

Basic illustration: what's wrong with this (C++) code?
```
int* i = new int;
*i = 33;
std::cout << *i << std::endl;
delete i;
```

---

### Post by mjwood0 on 2007-10-15
> **CptPicard said:**
> Yeah, in that sense the term is a bit problematic, but... when you've got an algorithm, you are making an assumption of a computation device... a computer of some kind. An algorithm is not an algorithm if it has some magical step that says "and then we just figure this out" :)

In my eyes, this is the study of Computational Science -- much closer to math.

---

### Post by CptPicard on 2007-10-15
> **mjwood0 said:**
> In my eyes, this is the study of Computational Science -- much closer to math.

First time I hear of such a field being discussed. Of course, it's all language games... in Finnish my major is called something like "information processing science". We always translate it as CS.

Also, academically, there is a well established field hod described well that is called "Computer Science"... and IMO it is quite separate from Engineering, although of course they've got strong links...

---

### Post by mjwood0 on 2007-10-15
> **aks44 said:**
> And the fact that C++ is a *superset* of C makes it a *totally* different language... ;)

(yeah, I couldn't help biting the bait LOL)


I figured :lolflag:

> **aks44 said:**
> 
I'd agree with the general idea, but IMHO C is not critical at all. On the contrary, you'd gain much more (at least as far as C++ goes) learning plain old assembly than learning C. The problem with learning C before C++ is that many (not all, mind you) people tend to use inappropriate C idioms when writing C++ code, which leads to very low-quality (not to say crappy) code.

Basic illustration: what's wrong with this (C++) code?
```
int* i = new int;
*i = 33;
std::cout << *i << std::endl;
delete i;
```

Beats the heck out of me!  I'm pretty honest in the fact that my C++ knowledge is marginal at best.  I'm actually a little unclear why you need the "new" at all as you can have a pointer to an int with no malloc in C.  Again -- I live in C so this is a little weird for me.

---

### Post by mjwood0 on 2007-10-15
> **CptPicard said:**
> First time I hear of such a field being discussed. Of course, it's all language games... in Finnish my major is called something like "information processing science". We always translate it as CS.

Also, academically, there is a well established field hod described well that is called "Computer Science"... and IMO it is quite separate from Engineering, although of course they've got strong links...

I've actually heard of people who have gotten degrees in Computational Science.  They basically have a math / algorithms degree with some basic CS in there.

The problem is that if you want to be a software engineer, most companies want a Computer Science degree.

---

### Post by CptPicard on 2007-10-15
> **mjwood0 said:**
> I've actually heard of people who have gotten degrees in Computational Science.  They basically have a math / algorithms degree with some basic CS in there.

The problem is that if you want to be a software engineer, most companies want a Computer Science degree.

Frankly, from my point of view, the stuff in CS that is not math/algorithms or other abstract problem solving and that employers look for in their software engineers is the sort of stuff you learn on the job. Experience counts more than how many times you've read through some software engineering textbook ;)

IT degrees are trying to encroach on CS and even call themselves CS, but I still like to believe that software engineering is nowhere near a proper academic discipline yet (not that I don't respect competent software designers who have years of experience...)

---

### Post by hod139 on 2007-10-15
> **aks44 said:**
> 
Basic illustration: what's wrong with this (C++) code?
```
int* i = new int;
*i = 33;
std::cout << *i << std::endl;
delete i;
```
Well.... How long are you going to leave us in suspense?  As far as I can tell the code looks correct.  You don't have to check the return value of new (unlike C's malloc), and you delete i so there is no leak.  Is what's wrong the lack of exception handling?

---

### Post by aks44 on 2007-10-16
> **mjwood0 said:**
> I'm actually a little unclear why you need the "new" at all as you can have a pointer to an int with no malloc in C. 

The new statement was to demonstrate a point when using C-style memory (or more generally, resource) management mixed with C++ code. Granted I could have used malloc/free instead of new/delete, with the same result.



> **hod139 said:**
> Well.... How long are you going to leave us in suspense?

Sorry for the delay, I was sleeping and now I just came back from work. ;)



> **mjwood0 said:**
> As far as I can tell the code looks correct. [...] Is what's wrong the lack of exception handling?

You pointed it out, the problem is that it is not exception safe.

In C, the equivalent of std::cout is printf, which *may* fail, but most people don't even bother testing the return value.
In C++, when it fails you just can't ignore it since std::cout would then throw an exception. And the pointer would never be deleted.
IOW there is a memory leak in the code (in case of failure to print to the console).


The real point being: C++ code has exceptions (mainly to report errors) and they break the control flow, so **you have to deal with *several* possible execution paths at the same time**. So the syntax similarities between C and C++ are just that: similarities.

Exceptions alone make C++ a totally different language than C, that requires a big paradigm shift especially for those people already knowing C and thinking that they can program in C++ like they used in C. That's why I don't recommend to learn C first *if your goal is to learn C++*, as for most people it is more of a hindrance than anything else. IMO provided you already know the programming basics (variables, tests, loops, functions, ...) better learn ASM to understand the low level concepts that C could learn you, then switch directly to C++, and avoid C altogether.

FWIW the correct way to write the previous code would be to use RAII ([Wikipedia]("http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization"),  [hackcraft.net]("http://www.hackcraft.net/raii/")), eg. using std::auto_ptr:
```

std::auto_ptr<int> i(new int);
*i = 33;
std::cout << *i << std::endl;
// no need to delete, std::auto_ptr takes care of it without *any* overhead
// even if faced with an exception
```

---

### Post by pmasiar on 2007-10-16
> **aks44 said:**
> The real point being: C++ code has exceptions (mainly to report errors) and they break the control flow, so **you have to deal with *several* possible execution paths at the same time**. So the syntax similarities between C and C++ are just that: similarities.

Exceptions alone make C++ a totally different language than C, that requires a big paradigm shift especially for those people already knowing C and thinking that they can program in C++ like they used in C. That's why I don't recommend to learn C first *if your goal is to learn C++*, as for most people it is more of a hindrance than anything else. IMO provided you already know the programming basics (variables, tests, loops, functions, ...) better learn ASM to understand the low level concepts that C could learn you, then switch directly to C++, and avoid C altogether.

Now I finally understand, after all those months. Yes, you are right. 

So C might be good start for Java programmers (so those weenies can avoid ASM :-) ) but hardcore C++ hackers are better off to start with ASM, so they don't have to unlearn bad habits later with C++.

I am happy I left system-level coding years ago and live full time in application world now.

---

### Post by Mickeysofine1972 on 2007-10-16
> **pmasiar said:**
> Now I finally understand, after all those months. Yes, you are right. 

So C might be good start for Java programmers (so those weenies can avoid ASM :-) ) but hardcore C++ hackers are better off to start with ASM, so they don't have to unlearn bad habits later with C++.

I am happy I left system-level coding years ago and live full time in application world now.

Lol I'm really surprised to see you not tell us all to scrap C/C++ and go use Python :lolflag:

I'm just pulling your leg btw :)

Mike

---

### Post by pmasiar on 2007-10-16
> **Mickeysofine1972 said:**
> Lol I'm really surprised to see you not tell us all to scrap C/C++ and go use Python

No, I am really happy you guys (and gals) do that low-level crap - so I don't have to! :-) 

I really do enjoy talking to real users, figuring what they need (which is different from what they tell me they want), and building it.

---

### Post by aks44 on 2007-10-16
> **pmasiar said:**
> No, I am really happy you guys (and gals) do that low-level crap - so I don't have to! :-)

Heh, guess what... I too am really happy there are people like you who make that userland crap, so I don't have to. ;)


> **pmasiar said:**
> I really do enjoy talking to real users, figuring what they need (which is different from what they tell me they want), and building it.

The biggest advantage of doing back-office applications being, IMO, that I don't have to deal with clueless whinners. This way, out of the company I only have to deal with sysadmins, granted they whine too (which customer doesn't? :p) but at least they know their stuff.


See, everyone is happy as it is and "*all is for the best in the best of all possible worlds*". :D

---

### Post by mjwood0 on 2007-10-16
Wow.  I'm loving my job right now.  No system admins (save for the UNIX / VAX admins, but they're really good), no direct customers.  Just me, a JTAG probe, a logic analyzer and hardware... 

Nothing like a good day of debugging PCI Bus Errors :-)

---

### Post by MystaMax on 2007-10-17
Man, this thread got hijacked a long time ago. IMO,  the difference between a scientist and engineer are irrelevant to a novice programmer. Personally, I did find it interesting to read everyones comments.

Let me first say, I'm not well versed in any language, but do enjoy programming and sysadmin tasks. I can read code and understand it better than I can write it and execute it (I probably don't practice writing it enough, coming up w/ trivial tasks is harder than I thought). I'm more of a web guy, so enjoy things like PHP and now [Ruby]("http://www.ruby-lang.org/en/"). I also manage some Ubuntu servers, and have been practicing writing scripts w/ Ruby for sysadmin tasks. 

I'm currently working on one that will backup a MySQL db and copy some files across to a backup server (I know nothing cool, I'm sure someone could whip something up, faster than I could start irb). This allowed me to become familiar w/ Ubuntu and ruby at the same time.

While there are some great all around languages, I think its important (and I could be completely wrong here) to identify what it is you'll be using the language for and find the one that suits your needs. I chose ruby b/c I thought it was easier to read than PHP. Also, PHP is a web scripting language, and is not meant for CLI tasks (but I know it can be used for this as well).

Someone mention that documentation for Ruby (or any modern programming language) is scarce. Someone also stated that Google is your friend. I disagree w/ the statement that docs are not available, and agree w/ [Google]("http://www.google.com/search?q=beginner+ruby+tutorials&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") being your friend. [Del.icio.us]("http://del.icio.us/search/?fr=del_icio_us&p=ruby+tutorial&type=all") is your friend as well. Sitepoint.com has a [free book on Ruby on Rails]("http://www.sitepoint.com/books/rails1/freebook.php"), which has a decent intro to Ruby.

Even though I bought the book, [Beginning Ruby by Peter Cooper]("http://www.rubyinside.com/category/beginning-ruby-book/"), I still find myself struggling w/ certain aspects of programming. Its become a huge wall. Most of what I've learn so far is from books and the internet. No formal learning, which I think would help me a lot. Understanding your learning style is also important. 

Good luck to you.

[B][OFFTOPIC]

[/B]For those that are interested, or care to reply. My difficulties w/ programming involve identify things that should be included in a script/program. I guess you can say its the planning. Identifying what needs to be variables and things like that. I'm not sure if I'm getting my point across, but I hope someone understands me, and could possibly help.

**[/OFFTOPIC]**

---

### Post by j_g on 2007-10-17
> **aks44 said:**
> C++ code has exceptions (mainly to report errors) and they break the control flow, so you have to deal with *several* possible execution paths at the same time.

_You're right on the money there_. Many, many C++ programmers have the mistaken idea that C++ handles a lot more "resource tracking" entirely on its own than C does, and therefore C++ is easier than C. That is so only _if_ the C++ programmer _doesn't_ take error handling into account (especially, as you note, wrt exceptions due to errors). The result is C++ code that leaks resources, or worse, when put into a shared library that some app uses, causes that app to terminate due to an unhandled exception.

I write lots and lots of shared libraries, and the absolute worst thing to do in a shared library is to cause the app to abort. (Incidentally, anyone who puts a call to exit() in a shared lib should be shot dead... with no questions asked).

The majority of C++ code I've seen, particularly open source stuff, does _not_ do proper error handling. Consequently, I have more faith in C projects because error handling tends to be more straightforward, and therefore, more prevalent. I tend to eschew using any shared lib written in C++. There are almost guaranteed to be issues like the example you cited with cout throwing an exception when it fails, whereas printf() doesn't, and the C++ programmer failing to take the former into account.

---

### Post by aks44 on 2007-10-18
> **j_g said:**
> Many, many C++ programmers have the mistaken idea that C++ handles a lot more "resource tracking" entirely on its own than C does, and therefore C++ is easier than C. That is so only _if_ the C++ programmer _doesn't_ take error handling into account (especially, as you note, wrt exceptions due to errors). The result is C++ code that leaks resources, or worse, when put into a shared library that some app uses, causes that app to terminate due to an unhandled exception.

The "easy" solution WRT to resource leaks when facing exceptions is using RAII. This way you just CAN'T have it wrong, and it really cleans up the code.

FWIW last time I checked in our project at work, we only had a few (a dozen or so) **delete**s out of something like 250kloc. std::auto_ptr and boost::*_ptr are probably your best friends in C++. :)

---

