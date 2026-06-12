---
title: "What to learn next"
date: 2008-05-29
forum: Programming Talk
---

### Post by babacan on 2008-05-29
Greetings
I am currently a 2nd year computer student undergradute student, this summer I want to extend my knowledge especially about the industurial aspect and I guess the ubuntu community is a great place to seek some answers :)

Functional programming(Scheme) was my first language while learning programming at the first year, I got all the basic concepts of programming with it. Second year OOP programming and Java was introduced to me, I got all the concepts of OOP and can currently work well with Java, concurrent programming(threads, locks etc), distributed programming(such as XML-RPC and similars). And indeed data structures and algorithm courses.

Actually I plan to focus on Software Engineering, I will be taking all my electives for next years about it (such as requirement engineering , knowledge engineering etc) and same applies to my future master program but before that, I want to make sure I am good at the core of software development.

This summer I will have nothing to do thus I want to focus on buying some books and extend myself, in order:
1st: Head first SQL , I feel like I really need to learn databases and how exactly they work (I will have a course next year but still cant wait to learn) I want to develop "real" apps, even a simple web app requires database knowledge.

2nd:Head First Servlets and JSP: Well I always wanted to learn real web development(already know XHTML and CSS) , I have checked out Php, Ruby(on rails) and other stuff but came to a conclusion that why should I bother with a new language while I am confortable with java and also it seems like it is used alot by professionals.

3rd: Peopleware - Productive Projects and Teams: This seemed me a good start for software engineering, understanding the people you work with , also seems it has a good rating at amazon.

and finally
4th: Head first Object Oriented Analysis & Design: This also seems a good basic Software Engineering book.

Oh well, I know this topic looks kinda weird but I couldn't help it :p 
Any recommendation will be gladly welcome :)

---

### Post by CptPicard on 2008-05-29
Actually.. I am going to suggest taking a turn off the beaten path and keep on doing Lisp, considering you started with Scheme.

Trust me, code monkey software engineering is mind-numbingly boring in the long run. You really want to get a flexible tool that lets you do "non-bureaucratic programming" although it maybe less "industrial" in some sense...

Functional programming is experiencing somewhat of a renaissance among those people who are in the know of what's "in" in programming. Take something like Common Lisp, or even more interestingly, Clojure... it's a Lisp that runs on the JVM and lets you easily interface with Java libraries.

The reason why functional programming and especially languages like Clojure that try to avoid mutable state are the future is the increasing need for tools for multicore/multithreaded programming. Locks and shared objects are hell compared to doing multithreading with a modern functional language... I just simply *refuse* to go do what you're planning to do for a career, and I'm a professional consultant...

---

### Post by slavik on 2008-05-29
The K&R book, Perl, Python (in that order)

---

### Post by days_of_ruin on 2008-05-29
Perl is butt ugly.If you want to learn a scripting language learn python.

---

### Post by slavik on 2008-05-29
> **days_of_ruin said:**
> Perl is butt ugly.If you want to learn a scripting language learn python.
I'll bite ... what makes you say that Perl is butt ugly?

---

### Post by babacan on 2008-05-29
First of all , thanks for all kind replies

> **CptPicard said:**
> Actually.. I am going to suggest taking a turn off the beaten path and keep on doing Lisp, considering you started with Scheme.

Trust me, code monkey software engineering is mind-numbingly boring in the long run. You really want to get a flexible tool that lets you do "non-bureaucratic programming" although it maybe less "industrial" in some sense...

Functional programming is experiencing somewhat of a renaissance among those people who are in the know of what's "in" in programming. Take something like Common Lisp, or even more interestingly, Clojure... it's a Lisp that runs on the JVM and lets you easily interface with Java libraries.

The reason why functional programming and especially languages like Clojure that try to avoid mutable state are the future is the increasing need for tools for multicore/multithreaded programming. Locks and shared objects are hell compared to doing multithreading with a modern functional language... I just simply *refuse* to go do what you're planning to do for a career, and I'm a professional consultant...

I think your statement seems pretty valid, as far as I know (even the staff of my university keep saying that), functional programming will be rising in the future, even the hated microsoft started the F# language in the close past. I have read at somewhere that Erlang (which I guess a functional language) is getting pretty strong due to being a decent (maybe even the best) concurrent language.

But when I check the IT career sites(that are listing IT related jobs), all I see Java, C#, Oracle and some SAP languages. It feels like in a close run the current trend (which seems like Java for the majority) still rule for some time thus being a functional language focused programmer will limit my chance to get decent job right after my graduation.

Also I would really dislike to being a code monkey in a long run , thats why I thought software engineering would suit me as its perspective is wider.


About the perl, I also think python worths checking more over it. But wouldnt JSP better? I would directly skip the learning curve and directly go for the useage. Maybe I can jump to some new stuff like grails after it?

Btw, please mind that I have zero work experiance outside of the universty so far thus all my statements are from "what I read".

Regards

---

### Post by babacan on 2008-05-29
> **slavik said:**
> The K&R book, Perl, Python (in that order)

Also with the K&R book , do you refer to [this ]("http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628")?

---

### Post by CptPicard on 2008-05-29
> **babacan said:**
> 
I have read at somewhere that Erlang (which I guess a functional language) is getting pretty strong due to being a decent (maybe even the best) concurrent language.

I have no experience with Erlang but IIRC it's based on a so called "Actor" model which is a paradigm of its own... it is suitable in particular for distributed computing -- what it was designed for at Ericsson -- but I probably wouldn't start using it as a general purpose language.


> But when I check the IT career sites(that are listing IT related jobs), all I see Java, C#, Oracle and some SAP languages. It feels like in a close run the current trend (which seems like Java for the majority) still rule for some time thus being a functional language focused programmer will limit my chance to get decent job right after my graduation.

Well, of course you will have to learn a lot of languages in the course of your career. Getting competent in basic Java is not hard -- it's the libraries part and especially the "Enterprise" parts of Java that can get extremely complex. But that's what you learn while at work while you're at it. Java is a good "marketable" language, which is actually what I use currently for my own business, but seriously, it's the other languages -- in particular the functional ones -- that have made me a better problem-solver and have given the real insights...

> 
Also I would really dislike to being a code monkey in a long run , thats why I thought software engineering would suit me as its perspective is wider.

If you just focus on the "business" side of software engineering you just learn to manage a team and draw flowcharts. This means you end up leading a team of code monkeys, after you start at the bottom by being a code monkey yourself. :)

I am personally more of an algorithmics guy who focused in studies on solving problems in the abstract, regardless of language or technology. Then I found myself an interesting niche to apply myself, and what I am doing is not "software engineering" per se... I do not apply any of those "processes" that SE claims to turn into a science. I just take a problem, study its properties, find an algorithmic solution, and implement it in a suitable language -- it is much more fascinating than drawing UML ;)

> 
About the perl, I also think python worths checking more over it. But wouldnt JSP better?

JSP is a web app display technology, so you have a bit of a mismatch there... but if you're into web apps, look at Python and TurboGears. Java's Enterprise platform so (unnecessarily) complex that you really don't want to go there unless you have a masochistic side to you...

---

### Post by bmeyer on 2008-05-29
Babacan, reading your post was like echoing my past experience.  I just recently finished my undergrad and have started my software engineering career and hope to work into the management side of it (requirements, analysis, design, etc.).  We also started with Scheme/Lisp and focused on Java.  I'll be damned if I have to program for the next 40 years ;)

Try looking into the following:
-A good design patterns book.  VERY helpful.
-Code Complete (2nd edition) by Steve McConnell was really good, even though it's published by Microsoft :(
[http://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212082543&sr=8-1](http://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1212082543&sr=8-1)
-A good UML and design book.  One I had in college was:
[http://www.amazon.com/Applying-UML-Patterns-Introduction-Object-Oriented/dp/0131489062/ref=sr_1_1?ie=UTF8&s=books&qid=1212082621&sr=1-1](http://www.amazon.com/Applying-UML-Patterns-Introduction-Object-Oriented/dp/0131489062/ref=sr_1_1?ie=UTF8&s=books&qid=1212082621&sr=1-1)

---

### Post by slavik on 2008-05-29
> **babacan said:**
> Also with the K&R book , do you refer to [this ]("http://www.amazon.com/Programming-Language-Prentice-Hall-Software/dp/0131103628")?
yes

---

### Post by pmasiar on 2008-05-29
IMHO don't waste time on SQL, if you will have classes on it. It is useful, but incredibly boring: select fields from table join another table where... It is not real language - in sense  SQL is not Turing-complete.

Don't waste too much time on JSP. Right way to do any app with GUI is using model-view-controller patters 9see wikipedia). Java has many web app frameworks. Problem with them (and Java in general) is that all are boring because they are set up for huge projects with dozen-hundreds replaceable code monkeys with about-average productivity.

Better learn dynamically typed procedural (not functional) language like Python, Perl or Ruby  (in order of **my** preference). Dynamic typing in "normal" language should open your mind, and is extremely useful to know to quickly hack together solutions for tasks where your priority is your productivity, not CPU efficiency (which are 80% of tasks you do, IMHO).

If you want to challenge your mind, consider learning Forth. very different from anything you encountered.

Another area which you did not mentioned, and is worth real good money now, is AJAX. Learn it if you like it.

---

### Post by CptPicard on 2008-05-29
> **bmeyer said:**
> hope to work into the management side of it (requirements, analysis, design, etc.).  ...I'll be damned if I have to program for the next 40 years ;)

Great attitude for a guy who is supposedly going to analyze and design for those who actually do the coding.

This is exactly why I am working on my own ;)

I am honestly rather suspicious of the value of all the flowcharting and UMLing and supposed top down hierarchical designing, especially if it is done by someone who tries to avoid actual coding... :) most design patterns and such are mostly a *symptom* of a statically typed OOP language anyway, plus trying to just solve a software development problem by cramming in more people (increasing overhead) instead of getting better people plus better tools.

Doing software isn't supposed to be an exercise in bureaucracy, like typical Software Engineering makes it look like. You need to have agile languages that help you express problems naturally instead of having to have all this "process" just to manage all the hacks (design patterns) around the limitations of the language, plus sufficiently competent people who will communicate through the  code they write, plus directly amongst each other, and not through some upstream [Gosplan]("http://en.wikipedia.org/wiki/Gosplan").

But of course that can't be, because the bureucrats at management would end up unemployed.. ;)

> **pmasiar said:**
> 
Problem with them (and Java in general) is that all are boring because they are set up for huge projects with dozen-hundreds replaceable code monkeys with about-average productivity.

Hey, you're forgetting that we're talking about future management here. He's going to be managing those hundreds of code monkeys, not actually using the framework ;)

---

### Post by days_of_ruin on 2008-05-29
> **slavik said:**
> I'll bite ... what makes you say that Perl is butt ugly?

All the non a-z characters.And there are so many different styles of
programming that reading someone else's code is HARD.I was reading
a gimp book and I was reading the scripting section and for the perl
script it had lump characters that looks like cartoon swear words.
Of course the book wasn't even going to attempt to explain them.It just
said "perl magic.copy it".Also have you ever heard of a "Most hard to read
python script" contest?Well there are several for perl.

EDIT:Heres a good example[http://strombergers.com/python/python_perl_slurp_file.html]("http://strombergers.com/python/python_perl_slurp_file.html")

---

### Post by LaRoza on 2008-05-29
> **pmasiar said:**
> IMHO don't waste time on SQL, if you will have classes on it. It is useful, but incredibly boring: select fields from table join another table where... It is not real language - in sense  SQL is not Turing-complete.


I disagree. SQL is very, very simple and I think anyone in the field should know it to a degree. (I see a reference to a class on it, so maybe you are not recommending forgetting about it entirely).

---

### Post by LaRoza on 2008-05-29
> **days_of_ruin said:**
> All the non a-z characters.And there are so many different styles of
programming that reading someone else's code is HARD.I was reading
a gimp book and I was reading the scripting section and for the perl
script it had lump characters that looks like cartoon swear words.
Of course the book wasn't even going to attempt to explain them.It just
said "perl magic.copy it".Also have you ever heard of a "Most hard to read
python script" contest?Well there are several for perl.



There is a "What to Love/Hate Perl" thread for this subject.

(But while you mention it, reading your own Perl code is hard enough if you are not a Perl wizard)

---

### Post by bmeyer on 2008-05-29
> **CptPicard said:**
> Great attitude for a guy who is supposedly going to analyze and design for those who actually do the coding.

Relax, pal.  The reason I said that is not because I have a lack of passion or talent when it comes to development.  That couldn't be farthest from the truth.  I just seem to enjoy the design phases of engineering the most.  It has nothing to do with bureaucracy or any of that jazz.  But thanks for being quick to jump to conclusions.

> I am honestly rather suspicious of the value of all the flowcharting and UMLing and supposed top down hierarchical designing, especially if it is done by someone who tries to avoid actual coding...  most design patterns and such are mostly a symptom of a statically typed OOP language anyway, plus trying to just solve a software development problem by cramming in more people (increasing overhead) instead of getting better people plus better tools.

I agree that increasing the size of a development team, rather than including more productive people and tools (ala Mythical Man Month), is ineffective.  But I disagree that using tools like UML or related ones to iron out the design as much as possible is a bad thing.  Try reading Pentium Chronicles.  Good design and planning helps avoid the snowball effect of changes and unforseen requirements later in the development cycle.

By the way, babacan, both of those books are worth checking out as well.  Mythical Man Month is considered outdated by some, it's main points are certainly relevant.  Also, the Pentium Chronicles is somewhat of a dry read, but it's ideas are worth consideration as well.

---

### Post by bmeyer on 2008-05-29
> **days_of_ruin said:**
> All the non a-z characters.And there are so many different styles of
programming that reading someone else's code is HARD.I was reading
a gimp book and I was reading the scripting section and for the perl
script it had lump characters that looks like cartoon swear words.
Of course the book wasn't even going to attempt to explain them.It just
said "perl magic.copy it".Also have you ever heard of a "Most hard to read
python script" contest?Well there are several for perl.

EDIT:Heres a good example[http://strombergers.com/python/python_perl_slurp_file.html]("http://strombergers.com/python/python_perl_slurp_file.html")

Picking up a pre-existing chunk of Perl to work on can certainly be a task lol.  But, if you can learn it, it's an extremely powerful tool, especially for command-line scripting and cron jobs.

---

### Post by slavik on 2008-05-29
> **days_of_ruin said:**
> All the non a-z characters.And there are so many different styles of
programming that reading someone else's code is HARD.I was reading
a gimp book and I was reading the scripting section and for the perl
script it had lump characters that looks like cartoon swear words.
Of course the book wasn't even going to attempt to explain them.It just
said "perl magic.copy it".Also have you ever heard of a "Most hard to read
python script" contest?Well there are several for perl.

EDIT:Heres a good example[http://strombergers.com/python/python_perl_slurp_file.html]("http://strombergers.com/python/python_perl_slurp_file.html")
read the replies, they are better than the article.

---

### Post by CptPicard on 2008-05-29
> **bmeyer said:**
> But I disagree that using tools like UML or related ones to iron out the design as much as possible is a bad thing.  Try reading Pentium Chronicles.  Good design and planning helps avoid the snowball effect of changes and unforseen requirements later in the development cycle.

Good criticism of UML:

[http://littletutorials.com.nyud.net:8090/2008/05/15/13-reasons-for-umls-descent-into-darkness/](http://littletutorials.com.nyud.net:8090/2008/05/15/13-reasons-for-umls-descent-into-darkness/)

The issue is that you can't avoid changes and unforeseen requirements. One might just as well deal with it. Most of the "software process" is a cure for something that doesn't even need to be a problem, if you're writing your stuff in something flexible enough. 

Sure, a finely, dogmatically crafted object-oriented design in C++ or Java comes crumbling down at first sight of an unforeseen requirement, and unfortunately, it often forces completely breaking apart all the nice patterns you committed to during design phase -- we're talking of a really *unforeseen* requirement here. You probably don't engineer for foreseen requirements you do not *really* expect anyway -- in that case you're voluntarily building a bigger cathedral than you need.

Stuff only snowballs if you're begging for it from the start, using rigid languages and platforms and methodologies where you commit big first and then need to prepare for all the snowballing. It will happen anyway, trust me. :)

I am very much in favour of a quick iterative prototyping process in a small competent team using some sort of an informal, "communication through code" agile process.

In my ideal situation, the "manager", if any, is essentially just the guy in the team that is tasked with talking to the client and maintaining some kind of general co-ordination... nothing more really.

---

### Post by skeeterbug on 2008-05-29
> **slavik said:**
> read the replies, they are better than the article.

So true, lol.

---

### Post by slavik on 2008-05-29
> **skeeterbug said:**
> So true, lol.
not only that, but I also like C which doesn't have any OO at all and I turned out fine.

---

### Post by pmasiar on 2008-05-29
> **bmeyer said:**
> not because I have a lack of passion or talent when it comes to development.  ... I just seem to enjoy the design phases of engineering the most.

PHB likes to tell Dilbert how to do stuff and let him to deal with details. 

OP, look at Agile/Scrum/extreme programming. They don't use analyst to draw UML and to foresee all the problems, they use iteration of fully functional code to research what really requirements are. they are what users expect, not what they said - only way to know is to show them pilot project and ask them what needs to be changed.

Gathering requirements and drawing UML does not work, because users do not understand language of requirements. Or, as saying goes: it is easy to write software  according to requirements, and walk on the water: if both are frozen :-)



> Mythical Man Month is considered outdated by some, it's main points are certainly relevant. 

It was reissued after 25 years, the only 25 years old IT book still relevant as when written, and it exactly says that engineering software by freezing requirements (waterfall) does not work in real life.

---

### Post by robheus on 2008-05-31
> **pmasiar said:**
> IMHO don't waste time on SQL, if you will have classes on it. It is useful, but incredibly boring: select fields from table join another table where... It is not real language - in sense  SQL is not Turing-complete.



SQL is pretty much worth considering - in combination with understanding how an RDBMS works - since it is used pretty much in large-scale projects everywhere.
And most RDBMS'es support some sort of procedural language, so the argument about not being Turing complete is void.

---

### Post by pmasiar on 2008-05-31
> **robheus said:**
> SQL is pretty much worth considering - in combination with understanding how an RDBMS works - since it is used pretty much in large-scale projects everywhere.
And most RDBMS'es support some sort of procedural language, so the argument about not being Turing complete is void.

I never said SQL is not worth knowing - I said it is not worth wasting time on it, if OP will have classes on it later. I do SQL for living, so I know SQL is pretty important :-)

Procedural language for embedded procedures is not SQL. Not that I care much about Turing-completeness, just to mention that SQL is pretty weak and generic tasks. If SQL would be more 'turing-complete', query planner would have much harder time to optimize query, so lack of turingness is good thing for such specialized language. It is not a bug: it is a feature :-)

---

