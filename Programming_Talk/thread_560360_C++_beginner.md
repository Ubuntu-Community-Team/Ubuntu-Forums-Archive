---
title: "C++ beginner"
date: 2007-09-26
forum: Programming Talk
---

### Post by yyz on 2007-09-26
Hello. I'm 17 years of age, and I'm very keen to learn how to program.
I currently am taking a BTEC introductory IT course(Level 1) at college.

I have no experience in computer programming. I borrowed a foundation C++ programming book from the college library, but there are so many programming languages out there, I'm not exactly sure if this will be a good one to start with.

I have a target to work in the computer security field in my future career. I want to program in Linux.
Which language will give me a good start-off?

(Note: I was advised by one of the IT teachers(programmer) at college to begin with Visual Basic, but another teacher(programmer too) said C++ is fine to start with; I'm in between, and a bit confused.

I hope I've made it all clear. Feel free to ask me, if you need extra information/more details, to give me a better guidance-advice.

Thank you

yyz

---

### Post by LaRoza on 2007-09-26
The stickies, or my wiki:

the links are in my sig.

For the language: Python.

Python is:

* crossplatform
* Easy to learn, but very powerful
* Mature
* Clean, and makes for good programming habits

---

### Post by thetejon on 2007-09-26
C++ is kind of a pain in the ***, and not where I'd recommend that you start.  Honestly, if you're going to be a programmer, you're going to end up using a bunch of languages.  

I would start with PHP.  There are tons of tutorials on getting started with LAMP (Linux Apache MySql PHP).  It's easy to get up and running, PHP is used all over the place, and it can be really simple or really complicated, depending on your skill level.

For example, as a beginner, you can write more or less an HTML page and throw in a few PHP commands to do something more interesting.  As you learn more, you can create classes and objects and do all kinds of things.

Pyhton is probably a good place to start, too, but I have never used it so I can't really say.

---

### Post by LaRoza on 2007-09-26
> **thetejon said:**
> 
Pyhton is probably a good place to start, too, but I have never used it so I can't really say.

If you have web experience, PHP might be best to start with.

To write your first program in Python, open a terminal, type "python" type:

```

print "Hello world"

```

Press enter.

---

### Post by hod139 on 2007-09-26
I usually try not to hijack threads, but this statement perked my curiosity

> **LaRoza said:**
> 

Python is:

* Clean, and** makes for good programming habits**
(emphasis added)

From my experience, good programming habits are not learned from languages (neither writing nor reading).  I'm interested in why you said this and curious as to how you can back this up.

---

### Post by LaRoza on 2007-09-26
> **hod139 said:**
> 
From my experience, good programming habits are not learned from languages (neither writing nor reading).  I'm interested in why you said this and curious as to how you can back this up.

Maybe I should have said: "It enforces good style"

---

### Post by thetejon on 2007-09-26
> **LaRoza said:**
> *Python hello world*
That's too hard.  Isn't there a program where I can point and click to make hello world?

---

### Post by anandanbu on 2007-09-26
Python is a wonderful language to start with if you are new to programming . But if you are supposed to learn C++ check this out which i referred from one of the post in this forum ;)

[How to start programming C++]("http://anandanbu.wordpress.com/2007/08/31/how-to-start-programming-c-2/")

---

### Post by LaRoza on 2007-09-26
very funny...

---

### Post by LaRoza on 2007-09-26
> **anandanbu said:**
> Python is a wonderful language to start with if you are new to programming . But if you are supposed to learn C++ check this out which i referred from one of the post in this forum ;)

[How to start programming C++]("http://anandanbu.wordpress.com/2007/08/31/how-to-start-programming-c-2/")

Some of your information looks familiar, you copied some wikipedia without citing or quoting.

---

### Post by hod139 on 2007-09-26
> **LaRoza said:**
> Maybe I should have said: "It enforces good style"
How does python enforce good style?  First you need to define what you mean by good style (good luck, people argue about this all the time), and then show me how a language enforces this good style.  This is going to be a very difficult argument to support.

---

### Post by anandanbu on 2007-09-26
Thanks for the fine review, LaRoza :)

---

### Post by LaRoza on 2007-09-26
> **hod139 said:**
> How does python enforce good style?  First you need to define what you mean by good style (good luck, people argue about this all the time), and then show me how a language enforces this good style.  This is going to be a very difficult argument to support.

It enforces readable code.

By good style, I would say generally "consistant style". For more than one programmer involved, this means a consistant style among the team. In OSS, this means a generally universal style, although there are differences.

Would you ever think to write code like:

[php]
if
(
    name != "LaRoza";
)
{printf("%s %i","Welcome LaRoza today is the ",day);if 
(
day < 23
){printf("%s","Your Credit card bill is not yet here");}
[/php]

---

### Post by hod139 on 2007-09-26
> **LaRoza said:**
> It enforces readable code.

Readable code is only one (and arguable minor since automatic code formatters exist for non-white spaced delimited languages) part of "style".  And even python has its limitations.  Some programmers may want to use tabs, whereas others want 2 spaces.  Python makes no distinction, and one person can argue that tabs are more readable and another argue that 2 spaces are more readable.  Again, this is subjective.

> 
By good style, I would say generally "consistant style". For more than one programmer involved, this means a consistant style among the team. In OSS, this means a generally universal style, although there are differences.

There are many difference styles, each consistent in its own right.  Which one is better?  Again, there is no answer.

> 
Would you ever think to write code like:

[php]
if
(
    name != "LaRoza";
)
{printf("%s %i","Welcome LaRoza today is the ",day);if 
(
day < 23
){printf("%s","Your Credit card bill is not yet here");}
[/php]
Of course not.  But that doesn't show me how python enforces better style.


I'm not trying to be an argumentative jerk.  I'm just trying to point out that if you want to make claims about a language, do not use subjective terms such as "programming habits" or "good style".  If all you are trying to say is that Python was designed to be highly readable by humans, then fine I won't argue that.  But saying than it "enforces" something subjective is vacuous and serves no one.

---

### Post by LaRoza on 2007-09-26
> **hod139 said:**
> 
I'm not trying to be an argumentative jerk.  I'm just trying to point out that if you want to make claims about a language, do not use subjective terms such as "programming habits" or "good style".  If all you are trying to say is that Python was designed to be highly readable by humans, then fine I won't argue that.  But saying than it "enforces" something subjective is vacuous and serves no one.

Do you know Python at all? If you don't, I am sorry.

Python makes constant indentation mandatory, although the indent doesn't matter:

```

while x < 10:
    print x
    x -=1

```
[php]
while (x <10)
{
    printf("%i",x);
    x--;
}
[/php]

These do the same thing, assuming x is defined and initialized. The first is python, the way it is written is valid, and anything other than changing the indent size or spacing will result in a syntax error.

The C code after it, is written in a readable style, similar to Python's, except it doesn't have to be written that way, although most of the time it is.

If you are going to indent anyway, what is the point of braces? Also, notice the lack of semicolons as a statement terminator, a newline does that in python, although you can make statements span multiple lines if you need to.

The inherent readability of Python, is good for beginners, no "funny characters", and its style is used in most other languages.

Does that make sense? I am sorry for assuming you knew Python.

---

### Post by LaRoza on 2007-09-26
> **hod139 said:**
>  If all you are trying to say is that Python was designed to be highly readable by humans, then fine I won't argue that.  But saying than it "enforces" something subjective is vacuous and serves no one.

It does enforce it, if you don't follow it, you get a syntax error. How is "enfores" not describe that?

It doesn't send a raptor to you (like with goto's) but a fatal syntax error is what I consider enforcement.

-EDIT For the goto enforcement: [http://xkcd.com/292/](http://xkcd.com/292/)

---

### Post by pmasiar on 2007-09-26
> **hod139 said:**
> Readable code is only one (and arguable minor since automatic code formatters exist for non-white spaced delimited languages) part of "style".  

yes, but if two programmers have different preferences for formatting, they have hard time reading each other's code, even if properly formatted in the other "foreign" standard. 

>  And even python has its limitations.  Some programmers may want to use tabs, whereas others want 2 spaces.  ... and one person can argue that tabs are more readable and another argue that 2 spaces are more readable.  Again, this is subjective. 

Python makes no distinction,

No, they cannot argue, and Python does make distinction: BDFL pronounced in PEP8 tab to be 4 spaces, case closed, stop arguing and start coding. Really.

> There are many difference styles, each consistent in its own right.  Which one is better?  Again, there is no answer.

This is why Python has dictator for :-)

> But that doesn't show me how python enforces better style.

I'm not trying to be an argumentative jerk.  I'm just trying to point out that if you want to make claims about a language, do not use subjective terms such as "programming habits" or "good style".  If all you are trying to say is that Python was designed to be highly readable by humans, then fine I won't argue that.  But saying than it "enforces" something subjective is vacuous and serves no one.

It is not syntax enforcement, but **social** enforcement. Arguing about coding standards is non-issue in Python land. And beginners learn style by reading example source, written in proper style by gurus. maybe it is not "enforcing" but "gentle nudging". :-)

Another hint programmers get is that Python strives to have "one obvious solution which looks right". Ie don't use convoluted syntax for simple concepts, use "for i in range(1,5)" instead of "for(i=0; i<5; i++)"

Of course we can argue about what is "enforcing" and what is good style, but fact remains that 95% people who knows Python recommend it for beginners, and most people who do not recommend Python don't know it themselves (yet :-) ).

---

### Post by aks44 on 2007-09-26
I'll pop in for a small rant... ;)


> **LaRoza said:**
> Python makes constant indentation mandatory, [...]

[php]
while (x <10)
{
    printf("%i",x);
    x--;
}
[/php]

The first is python, the way it is written is valid, and anything other than changing the indent size or spacing will result in a syntax error.

The C code after it, is written in a readable style, similar to Python's, except it doesn't have to be written that way, although most of the time it is.

Sorry, but what if I WANT to write a one-liner? (or whatever other formatting choice, for instance)

```
while (x<10) { printf("%i",x); --x; };
```
BTW, postincrementation is bad (at least in C++), use preincrementation unless you have no choice. :p


> **LaRoza said:**
> If you are going to indent anyway, what is the point of braces? Also, notice the lack of semicolons as a statement terminator,

For either indentation or semicolons, the point is the same: flexibility. IOW, choice... I'd hate a language that would forbid me to format code the way *I* want. ;)

---

### Post by LaRoza on 2007-09-26
> **aks44 said:**
> 
For either indentation or semicolons, the point is the same: flexibility. IOW, choice... I'd hate a language that would forbid me to format code the way *I* want. ;)

Use Perl, TIMTOWTDI

---

### Post by pmasiar on 2007-09-26
> **aks44 said:**
> I'd hate a language that would forbid me to format code the way *I* want. ;)

I found it funny that people who are ready for fight to death for silly freedom to format code in any random peculiar way (idiosyncratic, unreadable to others), are ready to submit their thinking to bondage and discipline of statically typed languages.

Myself I don't need freedom to mis-indent my code to make it harder to read (to me and others), and I am grateful for freedom of dynamic typing, which allows me to **write my code the way I think** and not like my compiler wants me to.

Edit: BTW Python allows multiple statements:

[php]
for i in range(5): print i
[/php]

it is valid, but ugly and scorned upon.

---

### Post by CptPicard on 2007-09-26
> **hod139 said:**
> 
I'm not trying to be an argumentative jerk.  I'm just trying to point out that if you want to make claims about a language, do not use subjective terms such as "programming habits" or "good style".... But saying than it "enforces" something subjective is vacuous and serves no one.

Sorry, but you are being an argumentative jerk, stirring up a storm in a logical teacup for the heck of it ;)

It is completely irrelevant whether you can "argue" about what consitutes good coding practice and good style. These arguments have been going on for all eternity, but there is a very good general agreement that the Obfuscated Perl Contest does not produce code that is according to good standards and style, no matter how much I wanted to subjectively argue I really love the kind of code it produces.

My subjective preferences simply do not make it good, because for us to in order even to have the concept of good style we need to have some common objective ground as to what constitutes code that us as human beings on average like reading. So therefore, good coding standards and practices generally mean you should produce logical, understandable, cleanly-laid out code. This should be generally understood without further need to address this, no?

Also, while there is no generally agreed upon definition of the Coding Style to Rule Them All, it is also agreed that it is better to have "a" style than no style at all. Python enforces a style, which is good (some people claim, YMMV). Whether you like the particular style is immaterial; the point is there *is* a consistent style.

Thus, to state that "Python enforces good coding practices" makes only a partially subjective claim. There clearly is a broadly agreed-upon standard, or the majority of the people would whine loudly. These are "best practices" because they are accepted by many, and because they work for those many, there has to be something objective behind it all, otherwise there would not be an agreement...

---

### Post by yyz on 2007-09-26
Hello to everyone who is in discussion in this thread. Thanks to everyone who participated with their comments, (although they were not specifically with the reference to my question), I appreciated it.
Thanks for the support LaRoza

My attempt in opening this thread wasn't to provocate the programmers in this community to start debating about the standards or ethics.
Since I'm a beginner in the field, I 'only' asked for advice, but its turned out into a total wreck, and hijacking of the thread.

I'm sure there are free areas to discuss the irrelevant topics.

Anybody else suggesting alternative or similar languages as a start-off?
Thanks Ubuntu Community.

---

### Post by pmasiar on 2007-09-26
Don't worry, every discussion goes off-topic, it is normal :-)

Python is good intro to programming, much easier to learn and use than C++. Even if you will code C++ for living, you will find Python useful for small tasks supporting your mega-project, which would be too hard to do in C++ and speed is not important - all the scaffolding which holds projects together.

See wiki in my sig for training tasks for beginners - especially good is PythonChallenge website.

And you always can learn C++ or any other as **second** language - most programmers use more than one language anyway.

Good luck!

---

### Post by CptPicard on 2007-09-26
> **pmasiar said:**
> 
Python is good intro to programming, much easier to learn and use than C++. Even if you will code C++ for living, you will find Python useful for small tasks supporting your mega-project,

Python's strong point is for me that it actually works both as a quick scripting language *and* quite a scalable programming language. It's not as unwieldy as statically typed languages like C++ or Java, but it also seems to have enough rigour and explicit form to it that you don't constantly feel like a script kiddie out of his depth when trying to write a "proper app".

That support bit is important... I would like to point out that one of the most interesting alternative build tools, Scons, is in Python and uses Python files as build scripts. This was actually the first time I met Python :)

As an interesting personal testimonial, I recently ditched Java web app development in favour of Python and Turbogears. There has to be something wrong when in order to create a fairly simple application you've got to have a gig's worth of RAM full of tools in use in order to keep it all under control, dozens of XML files in your project, a few thousand pages of reference books on hand, you spend a week trying to integrate three frameworks to produce essentially "Hello World!"... and this is after I've been following Java's web side developments from the early servlet and jsp days. That's when it was still manageable, but now I've just had it :p

---

### Post by hod139 on 2007-09-26
> **yyz said:**
>  
My attempt in opening this thread wasn't to provocate the programmers in this community to start debating about the standards or ethics.
Since I'm a beginner in the field, I 'only' asked for advice, but its turned out into a total wreck, and hijacking of the thread.

Sorry about that.  I didn't mean to stir up the hornets nest.

> 
Anybody else suggesting alternative or similar languages as a start-off?
If you are interested in computer science, don't worry too much about languages; you will use the one you are told to use.  More important in understand data structures and algorithms.


Now, to continue the debate...

First, I have nothing against python; I think it is a fine language to use for beginners and experts alike.  If you noticed, I never said not to learn python, nor offered an alternative language.  My problem was only in the wording LaRoza used when giving the merits of the language.  If you look back to my original post, I stated that I did not like the one sentence:
> **LaRoza said:**
> 

Python is:

* Clean, and** makes for good programming habits**
(emphasis added)

If LaRoza had said that Python was designed to have syntax to ease readability or anything along those lines then I wouldn't even had said anything.  Good programming habits does not equal readability. Readability is a subset of this, and a minor one as I tried to point out.

After stating this, LaRoza changed his statement to
> **LaRoza said:**
> Maybe I should have said: "It enforces good style"
and again I pointed out that this is ambiguous and not an objective merit.

Finally after this LaRoza stated > **LaRoza said:**
> It enforces readable code.
which was my original point!  

I never wanted to argue about good coding styles since I know that is pointless, which is why I asked LaRoza to remove his claim that python enforces good style!

(/me wonders if anybody even read what I was writing?) 

@pmasiar
I only brought up the tab versus spaces argument to highlight that programmers argue over the smallest things.  I didn't realize that the python BDFL had made a decree about the number of spaces.

---

### Post by yyz on 2007-09-26
Pmasiar, 
thank you for your support. The more I read from programmers, the more it gets me motivated. I'm quite pleased with that :)

My monitor is a little strangely eye-straining though, and it does in fact hurt my eyes very often. In this case would you suggest some books for Python, it'll give me the opportunity to do most of the work by reading. (Looking less often at my monitor).

I do have glasses (unfortunately because of the same monitor), but it isn't enough on its own to protect my eyes. I'm planning to purchase an anti-glare device soon for the solution of this particular issue.

Thanks for your time.

---

### Post by bunker on 2007-09-26
To answer OP's original question, see this site: [http://www.parashift.com/c++-faq-lite/index.html](http://www.parashift.com/c++-faq-lite/index.html).  Read a few bits of it and it'll give you a good flavour for C++ (and of the hassles you will undoubtedly come across).  This page gives as much advice as is necessary: [http://www.parashift.com/c++-faq-lite/how-to-learn-cpp.html](http://www.parashift.com/c++-faq-lite/how-to-learn-cpp.html)

I should add my own advice: don't learn solely from the Internets.  Get a book (or three, as the guy on that site suggests).  There are however some free books you can download "Thinking in C++" by Bruce Eckel is a good one - comes recommended by the KDE people.  There are two volumes of it.

As for leaning in general, I think pmasiar hit the proverbial nail on the head a while back - it all depends on how good the teaching material is.  You can write good code in any language, provided you learn how to first.  The thing with python is a lot of people learn it to be *A Programmer*, rather to write a program so the advice you get and the tutorials you see tend to be geared towards this.  A language like (say) PHP is very much centred on completing a task - in this case making a website - which is why most of the PHP code around is atrocious.  In fact, I find even the off-line material for PHP is generally fairly bad.

As to whether I think C++ is a good language to start with, well that depends on your patience.  It's not a 'friendly' language - you can do Very Bad Things, and you may or may not ever notice you've done them unless you read some material that says so.  Personally, I think C++ is great!  It's ugly and frustrating for many reasons (sometimes) but that just makes me feel better when I solve whatever problem I'm working on, especially when I can use the full flexibility of the language to implement something really elegant.  To each his own, though.

This got a little long winded... the last thing I'll say is learn more than one language.  From my own experience I can say that looking at things from another angle will give you a great boost.

For reference, my language progression: Java, PHP, C, Haskell, Python, C++, Ruby (learning now - damn it's a weird one!)

---

### Post by Blue Sky on 2007-09-26
The best book I've found for learning C++ from scratch is "C++ How to Program" by Deitel, it's excellent. I found it much easier to read than "Thinking in C++" by Bruce Ekcel. [http://www.amazon.com/Program-Harvey-Paul-Deitel-Associates/dp/0136152503/ref=pd_bbs_sr_2/002-8785456-7857604?ie=UTF8&s=books&qid=1190843459&sr=8-2](http://www.amazon.com/Program-Harvey-Paul-Deitel-Associates/dp/0136152503/ref=pd_bbs_sr_2/002-8785456-7857604?ie=UTF8&s=books&qid=1190843459&sr=8-2)

---

### Post by slavik on 2007-09-26
start with scheme, no python addict will dare say that scheme is simpler than python ;) (if they do, they are on drugs or smoking good stuff).

learn to program, not to babble in another language. (think of how foreign languages are tough, computer languages are simple).

---

### Post by pmasiar on 2007-09-27
> **yyz said:**
> Pmasiar, 
thank you for your support. The more I read from programmers, the more it gets me motivated. I'm quite pleased with that :)

Yup, programming is really fun. 

But be careful: [Programming Can Ruin Your Life](http://devizen.com/blog/2007/09/11/ruin/) :-) if you are not aware differences between cyberspace (where you have everything under control) and meatspace, where you don't. "The same traits that make you a great programmer can make you an awkward, misunderstood and miserable human being. ..."

Sometimes people in forum/email tell you stuff they would never tell you in person, and sometimes programmers have abrasive personalities trained in FPS games :-) but it is still fun overall.

> would you suggest some books for Python, 

O'Reilly books are constantly very good, "Learning Python" is one of good ones. "Python for dummies" is also decent, even if it is not deep enough is some places. And most online free books mentioned in my wiki do have paper counterparts. And if they don't, Lulu will print you any digital book for $0.10 per page and $5 to bind it :-)

Python will introduce you into programming, later you can learn other languages: java, C++, VB.NET or whatever you need for the job. But all those other languages are mostly just different (more clumsy) syntax, different libraries, and often more complicated ways to create data structures.

---

### Post by LaRoza on 2007-09-27
> **slavik said:**
> start with scheme, no python addict will dare say that scheme is simpler than python ;) (if they do, they are on drugs or smoking good stuff).


Or Common Lisp...

For the books mentioned above, you can download some of them, the links for them are in my wiki.

---

### Post by LaRoza on 2007-09-27
> **hod139 said:**
>  My problem was only in the wording LaRoza used when giving the merits of the language. 

After stating this, LaRoza changed **his** statement to


<snip>

If you see a technical error, like I once used the term "system call" incorrectly, correct me, I'd appreciate it. If I make a claim that one language is inherantly superior to another, feel free to jump in and counter it, if I have a small insignificant comment directed to another, that you take exception to, ignore it, or PM me.

---

### Post by hod139 on 2007-09-27
> **LaRoza said:**
> On this forum:

* Don't assume the poster is a native english speaker, therefore, don't pick pick apart wordings

I don't assume the poster is a native English speaker, and while I sympathize for the non native English speakers, it is an English language forum.  IMO, I was not "picking apart wordings", but maybe that got lost when things got heated.
> 
* Don't assume gender
I usually don't (if you look at me previous posts I tend to use "his or her" instead of his), but I did this time and I apologize.  No offense was meant.  You do hang out here a lot, so I will do my best in the future with any posts related to yours to refer to you as she.

> 
* Don't nitpick posts! My post was not making any outlandish claims, just a little tidbit for a beginner 
Here I disagree.  I did not feel I was nitpicking, and that you were making outlandish claims.  To me, and maybe I'm in the minority, making claims that one language is better because "it makes for good programming habits", and telling this to an impressionable novice is outlandish.  This is why I commented on it.

> 
Am I to assume from your posts that you are a pendantic, obsession compulsive, elitist, sexist? I think you mean pedantic :) .  Seriously though,  I should not have singled you out like I did.  For that I apologize.  Many other people chimed into the discussion and I got defensive.  Not a good excuse, but that's what happened.  

That said, I made no personal remarks about you, and take offense especially at the last two implications you made about me.

---

### Post by LaRoza on 2007-09-27
> **hod139 said:**
> 
Seriously though,  I should not have singled you out like I did.  For that I apologize.  Many other people chimed into the discussion and I got defensive.  Not a good excuse, but that's what happened.  

That said, I made no personal remarks about you, and take offense especially at the last two implications you made about me.

It is easy to get OT isn't it? Maybe we should give the thread back to the OP... :D

The things I said were meant to be just points, not actual implications. I was demonstrating taking things out of posts, then expounding on them. (I don't think you are what I was saying, just that I feel you were extrapolating the same from my posts.)

---

### Post by pmasiar on 2007-09-27
> **slavik said:**
> start with scheme, no python addict will dare say that scheme is simpler than python ;) (if they do, they are on drugs or smoking good stuff).


I would dare, and I am also curious what **you** are smoking: that should be illegal in most countries :-)

Just standard test, notch above trivial "hello world": printing "99 bottles of beer" song.

In Scheme: [original](http://99-bottles-of-beer.net/language-scheme-582.html),  [shorter, efficient](http://99-bottles-of-beer.net/language-scheme-852.html) and finally [idiomatic using macros](http://99-bottles-of-beer.net/language-scheme-832.html). If you don't know Scheme, you have no idea what is happening.

In Python: [simple](http://99-bottles-of-beer.net/language-python-808.html) and [OOP using iterator class](http://99-bottles-of-beer.net/language-python-1028.html). Simple version is obvious even for person not knowing Python.

OOP looks more like [Java solution](http://99-bottles-of-beer.net/language-java-3.html), object-obsessed instead of object-oriented, simple is the way of Python. 

BTW even [simple Java](http://99-bottles-of-beer.net/language-java-950.html) is way more complicated than simple Python.

---

### Post by LaRoza on 2007-09-27
My original, unaltered post:
> **LaRoza said:**
> 
Python is:

* crossplatform
* Easy to learn, but very powerful
* Mature
* Clean, and makes for good programming habits

The last statement is what caused all this. Read it again.

I said "makes for", in the sense that it helps a new programmer get a constant style. When people start coding, they often think on how they should write the code, Python elimates this concern, by making it clear. Indent, and indent constantly or the program won't work.

One can write messy Python code, but it takes an effort.

I, like most other programmers, use a constant style in any language, unless that language requires a deviation, like Fortran 77.

Python is a good place to develop this style because it can be transfered to other languages.

I personally started with a C style language, and my original code was messy because I was unsure of how to write.

---

### Post by aks44 on 2007-09-27
> **pmasiar said:**
> I found it funny that people who are ready for fight to death for silly freedom to format code in any random peculiar way (idiosyncratic, unreadable to others), are ready to submit their thinking to bondage and discipline of statically typed languages.

Funnily enough, I don't really see the point of dynamic languages. But again don't get me wrong, I've been writing back-office stuff since forever, so I guess I'm a bit biased. ;)

---

### Post by LaRoza on 2007-09-27
> **aks44 said:**
> Funnily enough, I don't really see the point of dynamic languages.

For many things, dynamic languages make life easier, and the code usable, for some programms, dynamic languages are dangerous:

[quote="Wikipedia"]
Because Ada is a strongly typed language, it has been used outside the military in commercial aviation projects, where a software bug can mean fatalities. The fly-by-wire system in the Boeing 777 runs software written in Ada. The Canadian Automated Air Traffic System (completed in year 2000 by Raytheon Canada) was written in 1 million lines of Ada (SLOC count). It featured advanced (for the time) distributed processing; a distributed Ada database; and object-oriented design.
[/quote]

Most people don't need that, and dynamic languages are the tools of choice. Python does have data types, and they are enforced, however.

---

### Post by pmasiar on 2007-09-27
> **hod139 said:**
>  I was not "picking apart wordings"

It is splitting hairs, and I am torn between hod139 and LaRoza, but I am sligthly leaning towards hod here. Python can win on merits, does not need objectionable claims and hype. Good style cannot be "enforced" by any language, we all know that determined programmer can write FORTRAN in any language :-), and enforcing proper indentation is just part of good style, so hod is right.

But  LaRosa is also right: beginners can read code of gurus and learn from it, much easier than learning from say Perl gurus. So the "enforcing" part is done not by compiler, but the community, using code review.

> I should not have singled you out like I did.  For that I apologize.  Many other people chimed into the discussion and I got defensive.  

yes, I plead with hod, please forgive :-)

And I am really glad we have smart ladies around (and not only as ubuntu code enforcers, forum police, but plain forum inhabitants), it will be warmer place I hope.

And we need be more careful about using genders pronouns now :-)

---

### Post by pmasiar on 2007-09-27
> **aks44 said:**
> Funnily enough, I don't really see the point of dynamic languages. But again don't get me wrong, I've been writing back-office stuff since forever, so I guess I'm a bit biased. ;)

dynamic as dynamically typed, or late-binding languages, are great for developer productivity. There was research years ago that programmers can write about 30 lines on debugged, maintainable code a day, regardless of language, what was givan as argument for [http://en.wikipedia.org/wiki/4GL](http://en.wikipedia.org/wiki/4GL) Dynamically typed languages is an effort to make that productivity gain be accessible to mainstream tasks, when compiler will figure type information from the code.

And dynamically-typed code can be as safe as statically (strongly) typed (or even more): it just needs be strongly tested. If time saved by using dynamically typed languages is used to write strong tests, you may win overall.

---

### Post by CptPicard on 2007-09-27
I wonder how the static vs. dynamic language issue plays out in the long term when your application needs to be maintained and extended. I have this fleeting suspicion that dynamic languages allow one to create a codebase that is a mess, and that has quick fixes applied to it time after time. Then, when you have no type information at hand, you better have used at least descriptive variable names in order to at least understand your code.

Then again, I have started becoming more and more sceptical of the merits of enforced OO design by statically typed languages like Java. When you use them, changes tend to break things all over the place because of typing issues creeping everywhere, esp. if you have inheritance structures (which is why inheriting functionality is not all it's hyped up to be anyway). You just can't design everything presciently in one go and then write it all up... when you fail in that, it's no good to say "nah nah your design was wrong" -- it's still wasted work -- and then you find yourself fighting your type structures all the way to Object. Java's Generics, btw, have made these issues just worse, and when you're doing refactoring, you really *need* tools to make your life easier. Then again, typing information of course helps in doing this automagically.. it would be harder (impossible?) in a dynamically typed language. I generified the analysis toolkit that is my main breadwinner with lots of pain and sweat in a week's time or so, and Eclipse was *very* useful.. but I honestly don't know if the gain of having cool generified collections was worth it.

I suspect the dynamically-typed side wins at least in quicker, smaller, small-developer-count projects simply because once you've got your wonderful OO design finally correct after revising it N times during development, *it no longer matters as the software is already done*. At most, OO design helps at the extension points of your project.

Now, if you do have a huge project, it's probably different, as the OO way of designing things helps communication of what is being done, and all the encapsulation and contracts might actually be worthwhile. Code reuse doesn't really exist... my analysis tools use similar algorithms for a lot of tasks, but they are different enough to usually just make me copy and paste and adapt to taste. I've tried writing cool OO designs, but when my friend wants some new feature, it usually just tends to need something I  *just* designed behind some encapsulation barrier... and making use of my framework forces me to break it all, introducing bugs everywhere else :)

By the way, I find it just slightly contradictory that Python devotees believe in the bondage and discipline of the One Right Way To Do Something when it comes to language syntax, and even want each line to carry global indentation information as multiples of invisible characters, yet sing the praises of not doing a static design, which would be just one more straightjacket that enforces good style ;)

---

### Post by aks44 on 2007-09-27
> **pmasiar said:**
> There was research years ago that programmers can write about 30 lines on debugged, maintainable code a day, regardless of language, what was givan as argument for [http://en.wikipedia.org/wiki/4GL](http://en.wikipedia.org/wiki/4GL)

30 locs per man/day of maintainable, production-quality code? :shock: You're kidding, right?

Make it 300 locs per man/day, and that's still not even average productivity IMO...

---

### Post by pmasiar on 2007-09-27
> **CptPicard said:**
> By the way, I find it just slightly contradictory that Python devotees believe in the bondage and discipline of the One Right Way To Do Something when it comes to language syntax, and even want each line to carry global indentation information as multiples of invisible characters, yet sing the praises of not doing a static design, which would be just one more straightjacket that enforces good style ;)

"One obvious way to do it right" you mean? It is mostly response to Perl's [http://en.wikipedia.org/wiki/TIMTOWTDI](http://en.wikipedia.org/wiki/TIMTOWTDI) principle, which sounds nice in theory, but in practice leads to code which is hard to share and understand. Of course  you have a lot of wiggle room in Python, you can use plain loops or list comprehension, full-bodied objects, or just pass around dictionaries and use procedural code... It is **more** flexibility that ie java, not less. Less is only when compared with Perl, which is good thing :-).

> global indentation information as multiples of invisible characters,

how it is worse than global indentation information based on count of preceding { and }, which are not even on the line in question? In C or java, if your code is according to the coding standards, it's structure is exactly the same. i really don't see the point.

>  static design, which would be just one more straightjacket that enforces good style

straightjacket can enforce many things, but not sure how it can enforce good style.

Big application should be **strongly tested, not strongly typed**. Type information is the only test compilar can perform, but only very small part of things which need to be tested (and BTW type test are simple to write), and for all other test you need to use (clumsy) strongly typed language, which slows you again. A language with introspection can check for presence of functions with names matching certain patterns, and run them. Very flexible way to write test, so it is easy, so people are easier persuaded to do it.

---

### Post by CptPicard on 2007-09-27
> **pmasiar said:**
> 
how it is worse than global indentation information based on count of preceding { and }, which are not even on the line in question? 


That's the whole point. Before hod jumps out of the woodwork, I should of course clarify that I meant semantic information, not indentation information, but you know the argument.. ;)

While you're inside a clearly delimited block -- one that it is delimited at both of its ends and that's it -- you are working within that context and don't need to constantly babysit the indentation on *every* line, ******* up which will cause actual bugs that actually have a reach of the area where you should have been delimiting your blocks. It's mostly an editing convenience of course, but most work on code is done while applying all sorts of transforms to it to make it look the way you want it to. I spend very little time admiring code I already got done :)

> Big application should be **strongly tested, not strongly typed**.

Are you sure you're able to write comprehensive integration tests for massive projects? OOP is a communication and consistency enforcement paradigm as much as anything else...

---

### Post by RamsesII on 2007-09-27
> **yyz said:**
> Hello. I'm 17 years of age, and I'm very keen to learn how to program.
I currently am taking a BTEC introductory IT course(Level 1) at college.
 
I have no experience in computer programming. I borrowed a foundation C++ programming book from the college library, but there are so many programming languages out there, I'm not exactly sure if this will be a good one to start with.

I have a target to work in the computer security field in my future career. I want to program in Linux.
Which language will give me a good start-off?

(Note: I was advised by one of the IT teachers(programmer) at college to begin with Visual Basic, but another teacher(programmer too) said C++ is fine to start with; I'm in between, and a bit confused.

I hope I've made it all clear. Feel free to ask me, if you need extra information/more details, to give me a better guidance-advice.

Thank you

yyz

Hello yyz,

    There's no a best language to start as you have learned through
 launching this thread. Everyone has his own idea of what is a best
language to learn how to program. It depends of the person and
 which kind of learner you are. 
      Some people will tell you C is the best because they have learned 
in C and have many years of programming and have tried other 
languages learned them pretty fast and will argue it's because of the 
good bases they got from C. Other will tell you java, other Eiffel, other php,
 html. You can get the most peculiar answer (peculiar here is also completely subjective) 
. What you need to know to make your choice is why do you 
want to learn a language of programming. In your case it seems clear
 you'd lile to work in computer security later. You need to know that 
learning only one language will never be enough to become an IT security 
guy (but you may already know that).
 Security ? networks security ? system security ? web apps security ? 
We're talking about different kind of security, which involved different 
tech so different languages. Python ? maybe it's good to start with, I 
am not a specialist in Python. For me what a beginner in programming should 
learn before attacking any programming language is some basics 
about numbers handling by a computer. How a short, a long, a real, a
 string are handled in computer ... What do we mean memory leaks,
 stack overflow, compiler, precompiler, syntax, semantic ? Don't start 
with a language which could be 
powerful but hide these points by treating them too automatically;
which allows to get to a result quickly but we'll leave 
you with some bad programming habits when you'll start to learn
another language. And also you need to know 
there are different kind of languages (object oriented language, 
procedural languages, scripts ...) That's not the same. If you learn 
with the kind of language I've spoken above you're going to 
complicate your task the day you will try to learn an Object 
Oriented Languages for instance. What you will have to do sooner or 
later to become a computer security professional.

Learning programming could be very frustrating sometimes but 
persevere and keep your dream to become a computer security
professional one day in mind to motivate you. It's a good thing to
have a stimulator.  ;-)
Hope this will help,

---

### Post by slavik on 2007-09-27
basic functional rundown ...

func x (int n) {
 if n < 0 return;
 "n bottles on the wall, etc."
 x(n-1)
}

that scheme version is messed up (the short one that you lsited).

---

