---
title: "Absolute noob to linux and programming"
date: 2008-06-17
forum: Programming Talk
---

### Post by screech1973 on 2008-06-17
Hi there, I found an Ubuntu CD on the cover of a magazine about 6 months ago, tried it and kind of liked it, after years of Microsoft "World Domination" I liked the idea of an alternative OS that wasn't bloaty and costing a fortune. The only downside for me is the lack of a player to play DRM and the DirectX monopoly,:( I have to switch back to bloaty old Microsoft for that. But it appears to do everything else so I can't complain.

To feel at home I would like to learn how to do a bit of programming, I work as a Printer and I am hoping to make a program that will record all my works customers details and also store pdf's on a worksheet, it must print a job sheet and be able to cross platforms on to mac. I found Realbasic recently and I am wondering if this is the right program to learn.

I must stress I have absolutely ZERO skills in programming, and I do mean none (well unless you class a dabble in BASIC twenty years ago as programming) what I do have is an unlimited amount of time to do this project.
It must be a simple language for me to understand, as I need to get my head around it, I liked the idea of BASIC because it kind of made sense at the time, *if blah=blah then GOTO etc*. But I understand this is obsolete, so, Realbasic caught my eye, is this a language that has a large following so I can seek out help when I get stuck, or is there another popular language that is easy to pick up with a good following?

So, thats me, a complete novice in UBUNTU, a total newbie to linux and about to dive into programming. Who says Rome wasn't built day. :)

---

### Post by Can+~ on 2008-06-17
Let me make a summary:

-Most of the people will recommend you to look at python.
-Someone will state that C/C++ with Code::Blocks or NetBeans is great.
-Another one will say that Mono with C# is the best way.
-LaRoza will *redirect* you to the [pinned faq](http://ubuntuforums.org/showthread.php?t=796494).
-*Some people* will recommend something that's completely awkward.

Skipping all that usual stuff: Ubuntu comes with the python 2.5.x preinstalled, so you can type "python" on the shell to check it out. Here's the documentation: [http://docs.python.org/](http://docs.python.org/) and here's a good tutorial: [http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/).

And try to avoid any thing resembling BASIC, I mean, really, it's okay to go there, but you should try out new things too, right?

---

### Post by CptPicard on 2008-06-17
> **Can+~ said:**
> 
-A single person will recommend something that's completely awkward.


Actually, you're being an optimist there. These days I see way too many posts advocating some flavor of BASIC or Pascal (for making screensavers)...

---

### Post by LaRoza on 2008-06-17
> **Can+~ said:**
> ...


Actually, I don't post links to stickies, they are easy enough to find.

I would urge you to forget about anything with "basic" in its name or based on it for now. 

The stickies might be useful to you as will my wiki and site (I have some coolish things on there, including a language selector for learning how to program).

Enjoy!

---

### Post by lisati on 2008-06-17
For a simple database-style project, you might want to look at the "Open Office" suite of programs that come pre-installed with Ubuntu. It can save its files in formats that can be used on other platforms, and the "Writer" program has an "Export as PDF". This might help you get started while you find your way aroud.

---

### Post by pmasiar on 2008-06-17
BASIC and it's clones are easy to start with, but it does not scale well for bigger projects - and you will be again locked in the monopoly and it's libraries.

OTOH Python is as easy to learn as BASIC, but open source, cross-platform, and scales well to bigger projects.

You need to realize that (unless you are very dedicated genius) it may take you couple of years to become sufficiently skilled to make application like you use, with GUI and stuff. But you can automate a lot of your boring work with massaging/converting files and creating reports, if you do it in plain old commandline, in substantially less time than with GUI.

---

### Post by LoneWolfJack on 2008-06-17
Before you decide, remember that many of ubuntu's internals are written in Python, so you have a very pro-Python community here. While I would not generally advise against Python, I have to admit that I have a personal distaste against it.

I would suggest that if it has to be a scripting Language, you pay the PHP and Perl communities a visit and see where you feel more comfortable.

Perl/Python do the same things in different ways, PHP has its focus on web development and doesn't force you into OOP.

If you are aiming for serious desktop applications, take a look at Java, which should be a bit easier to learn than straight C or C++.

Good luck.

---

### Post by pmasiar on 2008-06-18
Example of bad advice above: Perl is full of quirks and traps, it's  for a old hand sysadmin and not for a green beginner. Making Python web apps with any of modern web app frameworks are as easy (or more) than in PHP, and Python does not force OOP either (unlike say Java, which requires understanding CompSci and is much less friendly to beginners).

What definitely I would NOT suggest to a beginner to aim for serious desktop application, at least before s/he learned basics of programming.

---

### Post by Mickeysofine1972 on 2008-06-18
Actually I think that BASIC was a bit harder that Python as I remember it, with Python you dont have to do those DIM and REDIM stuff and of course these that GOTO: which we later realised was a bad programming practice.

So if you want command line or GUIs I too would say Python is your man. If you want databse stuff use sqlite if it does'nt needs to be super complicated and if you want to run it across platforms like windows and mac, look at the wxPython libraries which can be installed via the package manager.

Mike

---

### Post by nvteighen on 2008-06-18
Not only that. There's no single BASIC, so what you learned in MS QBASIC or in a ZX-Spectrum machine is not portable to GW-BASIC and sometimes neither to MS QuickBASIC... And VisualBasic is another galaxy... or VBScript...

On the other hand, there's only one Python.

---

### Post by LoneWolfJack on 2008-06-18
I believe that if the OP pays a visit to said communities he will quickly find the same kind of people pushing their favorite language and claiming it to be superior to all others. The usual rah-rah.

As for Perl, it was, in fact, the first real programming language I learned years before PHP took off. Didn't find it that hard to learn.

Just because you have a personal love affair with Python, it is not the holy grail of programming. You will have to live with me dropping by crashing your Python party every once in a while - no matter how much you hate it. ;)

---

### Post by LaRoza on 2008-06-18
> **nvteighen said:**
> Not only that. There's no single BASIC, so what you learned in MS QBASIC or in a ZX-Spectrum machine is not portable to GW-BASIC and sometimes neither to MS QuickBASIC... And VisualBasic is another galaxy... or VBScript...

On the other hand, there's only one Python.

CPython, Jython, IronPython, TinyPython

> **LoneWolfJack said:**
> 
Just because you have a personal love affair with Python, it is not the holy grail of programming. You will have to live with me dropping by crashing your Python party every once in a while - no matter how much you hate it. ;)


This whole discussion has been done before. The stickies are the first stop for questions like this.

---

### Post by nvteighen on 2008-06-18
> **LaRoza said:**
> CPython, Jython, IronPython, TinyPython

Ok, but they are Python + something, not "something else calling itself to be Python not really being like Python"

If I happen to be wrong (very likely), then let 4 = 1 and we're all happy! :)

---

### Post by LaRoza on 2008-06-18
> **nvteighen said:**
> Ok, but they are Python + something, not "something else calling itself to be Python not really being like Python"

If I happen to be wrong (very likely), then let 4 = 1 and we're all happy! :)

They aren't that different, TinyPython lacks features though.

For "Python like" check out Boo and Cobra.

---

### Post by pmasiar on 2008-06-18
> **LoneWolfJack said:**
> You will have to live with me dropping by crashing your Python party every once in a while - no matter how much you hate it. ;)

And you will have to live with me pouncing on you to protect young impressionable minds from the poison like Perl, BASIC  or Java :-)

---

### Post by wootah on 2008-06-18
> **Can+~ said:**
> Let me make a summary:

[B]-Most of the people will recommend you to look at python.
-Someone will state that C/C++ with Code::Blocks or NetBeans is great.
-Another one will say that Mono with C# is the best way.
-LaRoza will *redirect* you to the [pinned faq]("http://ubuntuforums.org/showthread.php?t=796494").
-*Some people* will recommend something that's completely awkward.[/B]

Skipping all that usual stuff: Ubuntu comes with the python 2.5.x preinstalled, so you can type "python" on the shell to check it out. Here's the documentation: [http://docs.python.org/](http://docs.python.org/) and here's a good tutorial: [http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/).

And try to avoid any thing resembling BASIC, I mean, really, it's okay to go there, but you should try out new things too, right?

Rofl :lolflag:

THIS should be a sticky because anytime someone mentions anything related to programming (so long as it is not a direct question about a problem they are having with the language or a bit of code), these exact series of events unfold.

+1 my friend, +1.

[quote=CptPicard]
Actually, you're being an optimist there. These days I see way too many posts advocating some flavor of BASIC or Pascal (for making screensavers)...
[/quote]

lol, I remember that thread! :lolflag:

---

### Post by LaRoza on 2008-06-18
> **pmasiar said:**
> And you will have to live with me pouncing on you to protect young impressionable minds from the poison like Perl, BASIC  or Java :-)

And C++, I was one of those that had to suffer...

> **wootah said:**
> 

THIS should be a sticky because anytime someone mentions anything related to programming (so long as it is not a direct question about a problem they are having with the language or a bit of code), these exact series of events unfold.


No one would read it then...

---

### Post by Mickeysofine1972 on 2008-06-18
I think that Perl and BASIC are just fine, the problem lies in getting to your goal.

ALL programing languages are good and bad in some context, and that may change as someone may decide that they think that language needs extending.

Thats why we have different flavors of C/C++/C--, Python, BASIC etc. Each is a step in the right direction but actually only describes a specific part of software creation that is relevant under the creators context.

The real challenge is knowing how programming really works and being able to apply that to all languages so that you have the choice to switch to a one that fits your needs and not be bound by convention or fear of filling your head up with too much info.

If you look at programming as a gateway to your goals the actual language you use becomes meaningless and the journey actually starts to look the same.

Of course context is always important.

Mike

---

### Post by cmay on 2008-06-18
> 
If you look at programming as a gateway to your goals the actual language you use becomes meaningless and the journey actually starts to look the same.

and may i add as a personal newbie to newbie experience
that its not the goal that is exiting .
it is the journey
no matter what the first language you find exiting to explore first is.

---

### Post by lisati on 2008-06-18
1) If I listed all the programming languages I've had some exposure to it would just get confusing.
2) I think this thread is at risk of being distracted from the OP's questions.......

---

### Post by Mr.Macdonald on 2008-06-18
i started by learning Java, don't try it. many times i wanted to punch the monitor(i didn't). java also makes programming to easy, it has libaries that do everything you could want to do. But they only work if you understand OOP (you don't need to yet).

Python is the second one i learned, and its alot more fun. I makes you think and find ways to solve something. I would suggest this because it can easily make GUI with pyGTK and it take a day for a programmer to learn and probably a week for a beginner.

kind of dive head first too. take the hello world and something slightly complex and try and merge them, that's how i learned. Just don't download some huge projects source and try and read it (I did and failed).

After a while try C++ to make better and faster programs.
Also if you don't understand something, google and wiki it, an then post.

---

### Post by LaRoza on 2008-06-18
> **lisati said:**
> 
2) I think this thread is at risk of being distracted from the OP's questions.......

The OP's question is answered by the stickies. If the OP didn't go check it out when it was first suggested, then it is hopeless :-)

---

### Post by lisati on 2008-06-18
> **LaRoza said:**
> The OP's question is answered by the stickies. If the OP didn't go check it out when it was first suggested, then it is hopeless :-)

:)

---

### Post by rlameiro on 2008-06-18
Well, I am a newbie too. I had the idea of start to learn a PC programming language ( I know some assembly for microcontrollers) an then I came here asking advice about C or C++, and then the savior came ## LaRoza ## and showed to me Python, and now, besides my job (musician) i made 2 little functional programs (1 metronome and one to interface a pc with a microcontroller via SERIAL port) in 2 weeks. Well if this is not enough for the "against" python community why don't you read the Eric Steven Raymond Howto "How to Become a Hacker". [http://catb.org/~esr/faqs/hacker-howto.html](http://catb.org/~esr/faqs/hacker-howto.html)
He recommends Python.

To those who don't know Eric Raymond aka esr , he is one of the most prominent hackers of the programmers community, president of the Open Source Initiative, and one of the responsables about the mozilla project (releasing of the code from netscape to the community).

I want to ear someone more experienced that him, telling him he is wrong now.. :guitar:

---

### Post by LaRoza on 2008-06-18
> **rlameiro said:**
> and then the savior came ## LaRoza ## and showed to me Python, 


A little strong, but I learned it because of pmasiar mostly (his posts often referenced it, and I looked into it because of them.)

---

### Post by pmasiar on 2008-06-19
> **Mickeysofine1972 said:**
> ALL programing languages are good and bad in some context...
The real challenge is knowing how programming really works and being able to apply that to all languages so that you have the choice to switch to a one that fits your needs and not be bound by convention or fear of filling your head up with too much info.

Of course context is always important.

So very true.

There is one step what Mike cannot commit himself into, because of his assumed distaste about Python significant whitespace:

Some languages were designed to be used by non-CompSci specialists, and Python is most widely used one. So context does matter :-)

I liked Perl, I liked learning about concise expressions, but year later it was hard for me to understand my own code. Perl requires dedication to the art, to the shortcuts and quirks. Ancestry of Perl shows: awk, sed, grep - tools what any sysadmin already knows, but beginners has yet to master (or with Python, can avoid mastering :-) ). Python is much more forgiving and easier to start with.

"Python is executable pseudocode. Perl is executable line noise"

Compare for yourself, song "99 bottles of beer" in [Perl](http://99-bottles-of-beer.net/language-perl-539.html) and [Python](http://99-bottles-of-beer.net/language-python-808.html). Instead of Python significant whitespace, Perl has significant special characters, which meaning is far less than obvious.

---

### Post by pmasiar on 2008-06-19
> **mickeysofine1972b said:**
> Eh? When did i say i didn't like Python?

I apologize, I must mix you up with someone else...

---

### Post by nvteighen on 2008-06-19
@OP:

If you are planning to do this a hobby, don't forget that the decision is yours and that you must choose the language(s) you feel more comfortable with, for whatever reason you might have. So, before going for language 'x', check out 'y' and 'z', read comments on them over the web, use the gentle advices of these forums' people for a while and when you have found what's your preference, go for that. (But **don't** jump blindly from language to language... stick to one, master it to a reasonable and competent level and only then go for another)

If you want a job, then learn what's used in the software market and what might be used in the nearest predictable future. Also, some knowledge of what was used in the past and, more important, why has been no longer used might be useful too.

---

### Post by pmasiar on 2008-06-19
> **nvteighen said:**
> If you want a job, then learn what's used in the software market

But OP said in original post he is printer - I assume he does not want to become professional programmer, just use some light hacking to simplify his job duties.

So for OP, it is especially important language be simple to learn and use, with focus on programmer's productivity, not CPU efficiency. Those was **exactly** the reasons why Python fits **much** better than say C++ or Java (or even Perl).

---

### Post by wootah on 2008-06-19
> **pmasiar said:**
> But OP said in original post he is printer - I assume he does not want to become professional programmer, just use some light hacking to simplify his job duties.

So for OP, it is especially important language be simple to learn and use, with focus on programmer's productivity, not CPU efficiency. Those was **exactly** the reasons why Python fits **much** better than say C++ or Java (or even Perl).

Real programmers don't care about a particular language. They care about solving a problem and using whatever tool best suits the situation. If it is a programming language, then sweet. If it happens to be a bash script, awesome.

The best programmers are those that understand the requirements of the problem and can mate a particular language that best solves the given situation with the least amount of time and effort.

EDIT: I think this is what pmasiar said :) To the OP, for this sort of program hacking, try **python **or **bash **scripts.

---

### Post by LaRoza on 2008-06-19
> 
The best programmers are those that understand the requirements of the problem and can mate a particular language that best solves the given situation with the least amount of time and effort.

Python surprisingly is a language like that for many tasks.

> 
EDIT: I think this is what pmasiar said :) To the OP, for this sort of program hacking, try **python **or **bash **scripts.

I wouldn't recommend learning Bash first, as it has features not found in other shells. It would be better to learn the basics of shell scripting before doing shell specific coding.

---

### Post by pmasiar on 2008-06-19
> **wootah said:**
> Real programmers don't care about a particular language. They care about solving a problemand using whatever tool best suits the situation. If it is a programming language, then sweet. If it happens to be a bash script, awesome.

Of course. Even if I am completely baffled why you do not consider bash a programming language. What is it, if not a language?

But then there are also snooty "real programmer wannabes" who do not consider programming needs of people who are experts in other field and just dabble in programming to solve some small problems without bothering programmers.

Those experts do not care about becoming expert programmers, learning whole spectrum of programming languages, and using appropriate for the job: all they want is to learn one almost-universal language which can be used to solve their problems without too much of programming efforts, which they do not forget if used only occasionally.

Python is excellent fit for those experts, more than any other language (it was designed that way).

---

### Post by wootah on 2008-06-19
> **pmasiar said:**
> Of course. Even if I am completely baffled why you do not consider bash a programming language. What is it, if not a language?

Was that directed towards me? If so, I do consider it a 'language'. It instructs the computer what to do :)

> 
But then there are also snooty "real programmer wannabes" who do not consider programming needs of people who are experts in other field and just dabble in programming to solve some small problems without bothering programmers.

Those experts do not care about becoming expert programmers, learning whole spectrum of programming languages, and using appropriate for the job: all they want is to learn one almost-universal language which can be used to solve their problems without too much of programming efforts, which they do not forget if used only occasionally.

Python is excellent fit for those experts, more than any other language (it was designed that way).

Which is very true. Many PhD level profs. at my university use python to accomplish repetitive tasks on a computer that they don't really want to be burdened with.

You said a solid truth: experts in one field don't need to be experts in comp. sci. To them, a computer is often just a tool to accomplish THEIR needs :)

---

### Post by nvteighen on 2008-06-19
> **pmasiar said:**
> But OP said in original post he is printer - I assume he does not want to become professional programmer, just use some light hacking to simplify his job duties.

So for OP, it is especially important language be simple to learn and use, with focus on programmer's productivity, not CPU efficiency. Those was **exactly** the reasons why Python fits **much** better than say C++ or Java (or even Perl).

I see I misread the OP's post. Excuse me.

Yes, he's pretending to use his programming skills for his job, not just for personal enjoyment as I do. So, agree with you totally: something that gives some productivity in the less time as possible (in other words: "the right tool", as always)... Python, with no doubt.

I read that OP wants his program to produce a PDF file at the end... Are there Python modules for interacting with Ghostscript or alternatively with the CUPS server to send stuff to the PDF printer? (I imagine there surely are some).

---

### Post by pmasiar on 2008-06-19
> **wootah said:**
> Was that directed towards me? If so, I do consider it a 'language'. 

No, at wootah, who said what I quoted. I'll fix my quote. Sorry for mix-up.

---

### Post by screech1973 on 2008-06-19
Firstly, thanks to all who have replied, I got to say I am a bit overwhelmed with all the information given. 
I am going to try python, I will give it a good 6 months of a trial to see if I can get to grips with it.
After reading some of the replys on here it makes me feel that perhaps my first project is maybe a bridge too far, but, I will try it and see where it leads me. 

After all, this will be my hobby in the evening for the next few months and the thought of myself ever becoming employed as a programmer has disappeared now, too old to start a career at 35 and far too inexperienced to make up ground. Something I wish I had pursued years ago when I was a little younger and had time and patience on my side.

Thanks again for all your info.

---

### Post by LaRoza on 2008-06-19
> **screech1973 said:**
> 
After all, this will be my hobby in the evening for the next few months and the thought of myself ever becoming employed as a programmer has disappeared now, too old to start a career at 35 and far too inexperienced to make up ground. Something I wish I had pursued years ago when I was a little younger and had time and patience on my side.


Programming as a hobby is much more rewarding than being employeed to do it I think. I would probably turn down a cubicle job programming if I ever got one (and I wasn't desperate for money)

---

### Post by GammaPoint on 2008-06-19
If I were you I'd probably do what worked for me. Just go out and buy (or get from the library) the 'Learning Python' book by Mark Lutz and work through it.  If you like it go pick up 'Programming Python' and then you'll be getting to pretty advanced stuff. 

After that you can simply learn from the web (actually the other stuff can be learnt from the web as well, but I prefer to have a physical, structured book to go through).  If you are still motivated to work on a project, you'll then be in a good position to decide what you might like to do.

---

### Post by pmasiar on 2008-06-19
It's great if OP can vote with your money for Python books - publishers love it, and measure popularity of languages in money spent on books :-) But if you decide not to, Python community released many good books free online - see wiki in my sig. 

Library book is fine, but in my experience selection is skewed towards "marketable" languages like Java/C#, which are so complicated that plenty of books can be sold for profit, and not towards simpler solutions like Python. It is still kinda "secret sauce", only curious people (like forum members :-) ) tend to know about it.

---

### Post by cacycleworks on 2008-06-19
> **screech1973 said:**
> Firstly, thanks to all who have replied, I got to say I am a bit overwhelmed with all the information given. 
I am going to try python, I will give it a good 6 months of a trial to see if I can get to grips with it.
After reading some of the replys on here it makes me feel that perhaps my first project is maybe a bridge too far, but, I will try it and see where it leads me. 

After all, this will be my hobby in the evening for the next few months and the thought of myself ever becoming employed as a programmer has disappeared now, too old to start a career at 35 and far too inexperienced to make up ground. Something I wish I had pursued years ago when I was a little younger and had time and patience on my side.

Thanks again for all your info.

Ah, balderdash. The spirit and your desire to solve a problem are what's needed for programming. :) I was taught C in college and worked for a time as a c/c++ embedded software guy.

Then I moved to e-commerce and it was all html this and that. I tried perl for a while. It was kinda painful, but I was able to piece-meal together a working shopping cart. Next up was when I learned not to go to a windows host and had to write .asp using visual basic (?). Now that was miserable. 

Fast forward 10 years and at age 35 or 36, I started using php to serve active content. I have been writing php for my site and other useful purposes for about a year now. Almost entirely in "spare" time. I love php. php.net + goole = an answer to any question I can think of, usually with working code examples.

I recently stubbed my toe on java ajax and jquery. No thanks, I agree with the others above. That stuff just gives me a headache!

**What I propose for your project:**
Build a web-based application in python or php that uses mysql for the database storage. This is portable, as "simple" php with sql queries should run on any web server: win, mac, linux. 

Some simple advice: Try not to put much work on the prettiness of the GUI (graphical user interface) and work on the foundation of the logic, using lots of functions. This makes your code more portable. And comment everything, even the obvious stuff. I need the easy stuff commented when I'm revisiting the code 1 or 5 years later -- having too many comments helps you think about what you're trying to do and spend less thought trying to figure out what's going on.

I really need to devote some time to python. This thread has put the bug in my ear for this. I really like php and use it for all sorts of things, normally via a webpage script but also on the command line. I've seen people deride cli php efforts, but with its awesome string management, it lends itself well to the command line.

:)

Thanks,
Chris

---

### Post by days_of_ruin on 2008-06-19
> **pmasiar said:**
> It's great if OP can vote with your money for Python books - publishers love it, and measure popularity of languages in money spent on books :-) But if you decide not to, Python community released many good books free online - see wiki in my sig. 

Library book is fine, but in my experience selection is skewed towards "marketable" languages like Java/C#, which are so complicated that plenty of books can be sold for profit, and not towards simpler solutions like Python. It is still kinda "secret sauce", only curious people (like forum members :-) ) tend to know about it.
Learning python really is a great book.Very in depth.Worth every penny.Just buy it on amazon its half the price compared to barnes and noble.

---

### Post by LaRoza on 2008-06-19
> **pmasiar said:**
> It's great if OP can vote with your money for Python books - publishers love it, and measure popularity of languages in money spent on books :-) But if you decide not to, Python community released many good books free online - see wiki in my sig. 


I noticed my personal library has the trend of having fewer books for languages I actually use, and more (and bigger) ones for ones I don't use (Java, C++).

The O'Reilly series are great. The "Programming $LANGUAGE", "Learning $LANGUAGE", "$LANGUAGE Cookbook", the pocket references are all useful. I only buy the pocket references. For learning I use the web, for in depth library references I also use the web.

---

### Post by Can+~ on 2008-06-20
> **LaRoza said:**
> I noticed my personal library has the trend of having fewer books for languages I actually use, and more (and bigger) ones for ones I don't use (Java, C++).

The O'Reilly series are great. The "Programming $LANGUAGE", "Learning $LANGUAGE", "$LANGUAGE Cookbook", the pocket references are all useful. I only buy the pocket references. For learning I use the web, for in depth library references I also use the web.

I bought Python in a Nutshell. It's like both things, half reference with pointers to other projects, half explanation on subjects like classes, error handling, etc. I read all that first section and now I use it as a reference.

---

### Post by pmasiar on 2008-06-20
> **cacycleworks said:**
> Build a web-based application in python or php that uses mysql for the database storage. This is portable, as "simple" php with sql queries should run on any web server: win, mac, linux. 

Nobody called on this, so it's again me, raining on someone's parade: 

Why would anyone suggest to a total beginner to build a MySQL-based website, where simple commandline Python program with simple shelf/pickle (or if SQL is desired, SQLite datastore) is more than enough? Website and DB server means admin/security problems. What is the gain, especially for a beginner? It will add months/years more of learning and development to get to the goal. Simplest solution which works is the best.

I understand that cacycleworks does web-based DB apps for living, but most people don't, and don't have to.

---

### Post by cacycleworks on 2008-06-20
> **pmasiar said:**
> Nobody called on this, so it's again me, raining on someone's parade: 

Why would anyone suggest to a total beginner to build a MySQL-based website, where simple commandline Python program with simple shelf/pickle (or if SQL is desired, SQLite datastore) is more than enough? Website and DB server means admin/security problems. What is the gain, especially for a beginner? It will add months/years more of learning and development to get to the goal. Simplest solution which works is the best.

I understand that cacycleworks does web-based DB apps for living, but most people don't, and don't have to.

I based it on how it took two weeks of after hours diddling around for me to learn as much sql as would be needed for his project. Basically, I built a cheat sheet with 10 commands on it that can accomplish anything most people would ever need.

I didn't see where this was intended to be publicly served. I'm pretty sure security isn't a problem as I've had bone stock LAMP installs work well -- and isn't Apache the single most common web server? You can type this and have a LAMP server up and running: ```
apt-get install apache2 php5 mysql-server mysql-client phpmyadmin
```  With google and question-asking, it only takes an hour or two to have everything configured so serving the pages and accessing the db are ready.

Admittedly, it took another couple hours for me to understand how a db works and what commands mysql required to create a db, add a table, etc etc. My only experience with db's before this was being a user of a MS Access db.

To meet PCI security standards, there are only about a dozen medium level security fixes to implement in a standard LAMP install.

Anyhow, given that all I've seen of python are the initial how-tos referenced above, it would take me a goodly amount of time longer to code this in py than php. duh :) 

Given how web apps are amazingly flexible, some php/sql knowledge would go a looooong way in the future. I don't know about you, but all of my web programming was self taught by implementing some kind of function for the site. Yes, the business is e-commerce, but I'm the owner and my core knowledge and "professional" work is anything but a web dev. I'm mostly just a motorcycle enthusiast who left computers to sell motorbike parts. :-)

So, apologies if I over estimated another's ability based on my own experiences with the same. 

Chris

---

### Post by pmasiar on 2008-06-20
> **cacycleworks said:**
> I based it on how it took two weeks of after hours diddling around for me ...
So, apologies if I over estimated another's ability based on my own experiences with the same. 

But you have college level CompSci education and couple of years of previous programming experience, OP has neither.

---

### Post by cacycleworks on 2008-06-20
> **pmasiar said:**
> But you have college level CompSci education and couple of years of previous programming experience, OP has neither.

Actually, the college level programming I received was only from 4 electives I took as part of an EE degree. When I learned about Computer Science and programming, it was faster to graduate by staying EE than to switch to CS. :) My engineering job was more about understanding and manipulating hardware than high level software design. I have looked at my alma matter about auditing some CS classes but would need to be excused from most of the pre-req's as I wouldn't want to take some of them and don't intend to get a 2nd bachelor's degree. 

OO still is a mystery to me. I fumbled with it a few times and almost got it with my last try in php. My Java OO accomplishments are more coincidence from testing every object.action combination I could try, not from education. I would definitely benefit from formal education in oo and database design.

If I've got an advantage it's that I'm like a pit-bull on a bone when it comes to accomplishing things like this. I believe people can accomplish (nearly) anything if they work hard enough at it.

:) Chris

---

