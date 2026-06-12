---
title: "C vs. C++"
date: 2007-09-05
forum: Programming Talk
---

### Post by bks on 2007-09-05
Okay, this may be a serious noob question, but what is the difference between C and C++? I am just starting a course on C++ and it got me wondering.

---

### Post by Mirrorball on 2007-09-05
The main difference is that C++ has lots of features for object oriented programming (classes with private, protected, and public members, inheritance, constructors and destructors etc), but it is not the only difference.

---

### Post by Wybiral on 2007-09-05
Basically C++ adds: classes, overloading (function and operator), templates, and also new and delete (instead of malloc and free).

Of course these new features generally come with the price of overhead and name mangling (making it hard to use for dynamic linking and low-level integration).

But, these new features radically alter the languages use... So learning C++ is not learning C, they have completely different idioms.

EDIT:

I almost forgot passing by reference... C++ allows function parameters to be defined as references that automatically create a variable that is linked to the variable used to pass. C requires you to do this by dereferencing a variable passed as a pointer.

---

### Post by nrs on 2007-09-05
With C, you have a reasonable chance of learning all there is to know, plus good style, in a single lifetime.

---

### Post by Lux Perpetua on 2007-09-05
The inventor of C++ basically took C and improved it in a few areas. Most of those improvements have been mentioned. Another big improvement is the Standard Template Library, which is a bigger & better standard library. The C standard library is still available, but the STL replaces much of its functionality, and C++ programs should generally not resort to the C standard library for those features.

---

### Post by rharriso on 2007-09-05
C++ is the first Object Oriented Programming.

If your at a school like mine, you'll never hear the end of how awesome it is.

Also C++ is literally 3x harder to debug.
No lie, three times.

---

### Post by Lux Perpetua on 2007-09-05
C++ isn't the first object-oriented language by a long stretch. (See Simula and Smalltalk.)

---

### Post by Mirrorball on 2007-09-05
> **rharriso said:**
> C++ is the first Object Oriented Programming.
Not at all.
> **rharriso said:**
>  Also C++ is literally 3x harder to debug.
Harder to debug than what?

---

### Post by nrs on 2007-09-05
> **Lux Perpetua said:**
> The inventor of C++ 

[http://www.chunder.com/text/ididit.html](http://www.chunder.com/text/ididit.html) :)

---

### Post by bks on 2007-09-05
Thank you to everyone for your detailed response.

---

### Post by rplantz on 2007-09-06
I suggest that you read "The Design and Evolution of C++" by Bjarne Stroustrup. He talks about many issues and why he made the choices he did when designing C++. Not only will you learn a lot about C versus C++, but you will also learn a lot about programming.

---

### Post by pmasiar on 2007-09-06
"Thinking in C++" by Bruce Eckel also explains WHY, not only HOW.

---

### Post by LaRoza on 2007-09-06
> **bks said:**
> Okay, this may be a serious noob question, but what is the difference between C and C++? I am just starting a course on C++ and it got me wondering.

As the difference were already layed out, I won't go into that. You should study C also, especially if you already of some programming experience and are mostly learning syntax.

For free books and tutorials, you can look at my wiki, [http://laroza.pbwiki.com/ProgrammingLibrary](http://laroza.pbwiki.com/ProgrammingLibrary), there is a section for C and C++ and one for both.

---

### Post by emperon on 2007-09-06
Well the difference is, C++ sucks and C sucks too :)

---

### Post by Wybiral on 2007-09-06
> **emperon said:**
> Well the difference is, C++ sucks and C sucks too :)

lol, and what exactly do you propose as a superior language? Or does programming, in general, suck to you?

---

### Post by emperon on 2007-09-06
> **Wybiral said:**
> lol, and what exactly do you propose as a superior language? Or does programming, in general, suck to you?

Python , Ruby, C# , Java, Boo, D are nice languages to me

---

### Post by happysmileman on 2007-09-06
> **emperon said:**
> Python , Ruby, C# , Java, Boo, D are nice languages to me

Well done, a binch of interpreted and/or slow languages...

If you waneted a fast program what would you do? For every project using one of the above languages there are about 10 using C/C++.

OMG C sucks, that's why pretty much all operating systems are written in it

---

### Post by pmasiar on 2007-09-06
> **happysmileman said:**
> Well done, a binch of interpreted and/or slow languages...


My boss is 100% sure that the most important speed in application programming is **speed to the market**. From that POV (especially for web-based database apps),  python beats C, hands down. Do you have different experience? What exactly **is** your experience based upon?

---

### Post by happysmileman on 2007-09-06
> **pmasiar said:**
> My boss is 100% sure that the most important speed in application programming is **speed to the market**. From that POV (especially for web-based database apps),  python beats C, hands down. Do you have different experience? What exactly **is** your experience based upon?

Based upon the fact that Python is AFAIK implemented in C/C++, same with PHP, probably Ruby etc...

You can argue that in your situation they're better languages... But C/C++ is what most programs are written in, and without them you wouldn't be able to use any interpreted languages or anything,in fact if you think C/C++ are pointless you might as well just format your drive and write a Python OS (yes that's a joke).

C/C++ may not be best for you, but saying they're worse than Python etc... Is just ignoring the fact that without them Python wo0uldn't exist... that's like saying they need to completely do away with ASM because C is better, or get rid of C because now there's C++

---

### Post by aks44 on 2007-09-06
> **happysmileman said:**
> if you think C/C++ are pointless you might as well just format your drive and write a Python OS (yes that's a joke).

As a side note... it's not such a joke... those guys at Microsoft wrote a full OS in C# !! (can't remember the project name right now)

EDIT: found it... it's called [Singularity]("http://en.wikipedia.org/wiki/Singularity_%28operating_system%29")

---

### Post by Wybiral on 2007-09-06
> **emperon said:**
> Python , Ruby, C# , Java, Boo, D are nice languages to me

That's fine. But why does that mean C sucks? I use Python too, but I also program in C and C++ and I don't think they suck at all... In fact, as a Python programmer, it's a good thing to have a decent knowledge of C so that you can write your own modules when things get critical. Then again, it mostly depends what you're doing...

---

### Post by pmasiar on 2007-09-06
> **happysmileman said:**
> Based upon the fact that Python is AFAIK implemented in C/C++, 
....
C/C++ may not be best for you, but saying they're worse than Python etc... Is just ignoring the fact that without them Python wo0uldn't exist...

I don't see how this is relevant. C is excellent for implementing low-level task, where raw performance is crucial and flexibility is not as important, like compilers, databases, libraries, etc., so called "systems programming".  C is excellent complement for Python in area of "application programming", where I **use** C libraries, databases etc and write application programs which needs to be flexible and performance is not as crucial (in part because big part of running time will be spent in C libraries anyway).

I don't argue that without C, Python would not exist - it is true. It is like arguing that without stone tools, civilization would not exist, so we need to stick to proven stone tools. Not so: using basic tools we build better tools, and use those.

>You can argue that in your situation they're better languages... But C/C++ is what most programs are written in, and without them you wouldn't be able to use any interpreted languages or anything,

Some experts think that most of the executed code was written in COBOL :-)

And yes, I **do** argue that Python is more productive for application programming than C or C++. 

>  write a Python OS (yes that's a joke).

It is not: OLPC wrote desktop GUI (Sugar) in Python instead of C. Joke is on you :-)

> that's like saying they need to completely do away with ASM because C is better, or get rid of C because now there's C++

No, I never said that. ASM is good for deep-down optimization of C. And as **most of us agreed in this thread**, comparing C and C++ like you do does not make sense, so why you try to sneak this argument again, and even pretend I said that?

All my argument is, that you are mistakenly obsessed by raw performance of the language, committing common noobish mistake of not taking into account time it takes to finish the application.

(and letting emperon off the hook with his unsupported claims) :-)

---

### Post by emperon on 2007-09-06
> **happysmileman said:**
> Well done, a binch of interpreted and/or slow languages...

If you waneted a fast program what would you do? For every project using one of the above languages there are about 10 using C/C++.

OMG C sucks, that's why pretty much all operating systems are written in it

Java and C# has comparable speed to C / C++ (around 80 - 90 percent). Thanks to JIT. D is as fast as C/C++ with a much much neater syntax  So calling them slow would be wrong.

---

### Post by aks44 on 2007-09-06
> **pmasiar said:**
> All my argument is, that you are mistakenly obsessed by raw performance of the language, committing common noobish mistake of not taking into account time it takes to finish the application.

Although I can't disagree with that, it all depends on what you're writing in the end.

Front-office stuff (where the computer wastes its time waiting for the user) doesn't quite have the same requirements as back-office servers that get thousands hits per second (or that perform very expensive calculations). But I know you already know that. ;)

---

### Post by pmasiar on 2007-09-06
> **happysmileman said:**
> For every project using one of the above languages there are about 10 using C/C++.

You misleadingly use "project" which mixes together userland application and system-level programming. They are very different, and different tools are optimal in each case.

Even if this (10 for each) is true (and I am too lazy to check or disprove it), it does not mean that many of projects using C or C++ would not be much better off using more agile language, like Python. There **are** areas where raw speed is important: but they are not as widespread as you would like to suggest. Using [Sturgeon law](http://en.wikipedia.org/wiki/Sturgeon_law) I guess that 90% of programmers are coding application code where raw speed is not important, and 90% of them are using suboptimal C/C++ for those applications.

Even in cases where speed is important, you cannot guess in advance where the bottleneck would be: instead, better (and faster, cheaper, more maintanable) solution is to create whole application in Python, find the bottleneck, and recode **that part only** as C library (using already stabilized API).

---

### Post by nrs on 2007-09-06
> **pmasiar said:**
> My boss is 100% sure that the most important speed in application programming is **speed to the market**. From that POV (especially for web-based database apps),  python beats C, hands down. Do you have different experience? What exactly **is** your experience based upon?

Speed to market is in the best interest of business, not necessarily the users.

---

### Post by pmasiar on 2007-09-06
> **nrs said:**
> Speed to market is in the best interest of business, not necessarily the users.

Not sure what you mean. **Your users** prefer to have application year from now, and are happy to wait? **My users** want it yesterday! :-)

---

### Post by aks44 on 2007-09-06
> **pmasiar said:**
> Not sure what you mean. **Your users** prefer to have application year from now, and are happy to wait? **My users** want it yesterday! :-)

It happens that tuesday we just made a demo of our new release to our biggest customer. We got roughly that response: "we'll wait and see, we may switch in 6 months, this app is too critical for us to gamble anything".

But again, it all depends on your target audience, both POVs are equally valid IMHO.

---

### Post by nrs on 2007-09-06
> **pmasiar said:**
> Not sure what you mean. **Your users** prefer to have application year from now, and are happy to wait? **My users** want it yesterday! :-)

Note: Everyone wants their project to get to the market quickly, so I'm talking about the gimmick "Speed to Market: :D!!1:D" 

I don't think the differences in development time would be that large if the programmers were properly qualified. And while I shall never have the privilege(sic) of developing or using commercial proprietary software, I'm sure most of the those users would rather wait and have it done right.  

Speed to market is of obvious benefit to the company; low development costs, quick return, customers are usually dependent. Speed to market is an obvious non-benefit to users because of how it was achieved; poor testing, wildly inappropriate use of interpreted languages resulting in poor performance, etc.

---

### Post by pmasiar on 2007-09-06
> **aks44 said:**
> It happens that tuesday we just made a demo of our new release to our biggest customer. We got roughly that response: "we'll wait and see, we may switch in 6 months, this app is too critical for us to gamble anything".

OK. Now imagine instead of presenting working demo, you would show GUI screen design, and tell them that **you hope** you will have it year from now. What the response would be? :twisted:

But to understand your position, I need facts: what kind of app? What language do you use?

---

### Post by frenchcr on 2007-09-06
I am a post grad student, had to learn programming in C and C++ very quickly. Needed simple easy (entertaining if possible) books that would learn quickly from as i had too much other hard work to do, so these books had to be less academic more easy going but still get me to where i needed to be...i went to our university library and gave dozens of books a chance...i ended up with the following purchases for my private collection:

An absolute beginners guide to C by ??
Starting out with C++: Early Objects by Gaddis
The C programming language by Kerrnighan and Ritchie.

If you want to learn both, and id advise you to do both, start with C then go to C++ and doing these books in the order i list them is a great way to start. Good Luck.

---

### Post by pmasiar on 2007-09-06
> **nrs said:**
> I don't think the differences in development time would be that large if the programmers were properly qualified. 

In what languages you completed some non-trivial projects? What kind of experience are we talking about?

> I'm sure most of the those users would rather wait and have it done right.  

No. Users want it **right and yesterday** :-)

> Speed to market is an obvious non-benefit to users because of how it was achieved; poor testing, wildly inappropriate use of interpreted languages resulting in poor performance, etc.

"wildly inappropriate use of interpreted languages resulting in poor performance"? Seems to me that you are committing the same noobish error like I warned happysmileman bofore. What kind of application are you talking about? If you program is web-based front-end for a database, 90% of response time is out of your control (database query, web server response), so even doing it in InstantAssembler(tm) which uses no execution time at all, will make it only 10% faster.

I have feeling that we are talking about different things. What is your use case?

---

### Post by aks44 on 2007-09-06
> **pmasiar said:**
> OK. Now imagine instead of presenting working demo, you would show GUI screen design, and tell them that **you hope** you will have it year from now. What the response would be? :twisted:

That's why we maintain 2 concurrent versions (the legacy one, and the latest one) alongside with the devel branch. And we don't present prototypes. ;)

> **pmasiar said:**
> But to understand your position, I need facts: what kind of app? What language do you use?

It's a data analysis tool, in the geotechnics field. We gather tons of raw data about soil resistance (drilling parameters, pressure essays, ...) and do calculations & correlations on it to help engeeners determine how the soil will react to building.

I personnaly work on the server, which in some cases has something like 1000 concurrent clients (keep in mind some of the computations are really heavy).
To add to this, the client is pretty dumb, apart from graphical rendering it does almost nothing and all computations are done server-side since otherwise too much data would have to be transfered over the network. Not to mention the "housekeeping" work: all user input is verified both client and server side (for safety we decided just not to trust our own client), plus managing the data tree (including real time broadcasts of the tree updates to the concerned clients).

The server is written in C++ with a mix of ASM for the bottlenecks (a few calculation routines), the GUI is written in C++ (graphical rendering) and Delphi (UI).

---

### Post by aks44 on 2007-09-06
> **frenchcr said:**
> If you want to learn both, and id advise you to do both, start with C then go to C++

I couldn't stress enough that learning C first is the best way to get very bad habits when it comes to C++. IMO doing it the other way around allows to better grasp the differences between the two languages, and get the most out of them both.

---

### Post by pmasiar on 2007-09-06
I am glad that someone is using all that math, all I am using are integers!

> **aks44 said:**
> That's why we maintain 2 concurrent versions (the legacy one, and the latest one) alongside with the devel branch. And we don't present prototypes. ;).

But this is not the situation which will reveal "speed to market". Here is scenario:

Your good customer comes to you, and says: 

> I was happy customer for N years, but now your competition program has this cool feature, and it would save us X monthly, and we really, really want it. So when your program will have it, and how much will cost the upgrade?

Now what? C++ to the rescue? Or some agile language like Python?

Read article about how to beat competition: [Beating the averages](http://www.paulgraham.com/avg.html) by dot-com millionaire [Paul Graham](http://en.wikipedia.org/wiki/Paul_Graham) and his friend Robert Morris, yes, [that Morris](http://en.wikipedia.org/wiki/Robert_Tappan_Morris) :-)

---

### Post by Wybiral on 2007-09-06
> **aks44 said:**
> I couldn't stress enough that learning C first is the best way to get very bad habits when it comes to C++. IMO doing it the other way around allows to better grasp the differences between the two languages, and get the most out of them both.

Opinion, not fact.

---

### Post by pmasiar on 2007-09-06
> **aks44 said:**
> I couldn't stress enough that learning C first is the best way to get very bad habits when it comes to C++. IMO doing it the other way around allows to better grasp the differences between the two languages, and get the most out of them both.

Bruce Eckel, well-known expert, requires C as prerequisite to his C++ courses. Do you just trust me, or do you want me to dig out a link for you? :-) 

If I find the link, will it change your mind? :twisted:

---

### Post by nrs on 2007-09-06
> **pmasiar said:**
> In what languages you completed some non-trivial projects? What kind of experience are we talking about?

> I'm sure most of the those users would rather wait and have it done right.  

No. Users want it **right and yesterday** :-)

> Speed to market is an obvious non-benefit to users because of how it was achieved; poor testing, wildly inappropriate use of interpreted languages resulting in poor performance, etc.

"wildly inappropriate use of interpreted languages resulting in poor performance"? Seems to me that you are committing the same noobish error like I warned happysmileman bofore. What kind of application are you talking about? If you program is web-based front-end for a database, 90% of response time is out of your control (database query, web server response), so even doing it in InstantAssembler(tm) which uses no execution time at all, will make it only 10% faster.

I have feeling that we are talking about different things. What is your use case?

Generally, I think it is inappropriate for any large project where acceptable levels of performance are desired. Web applications, and mere frontends excluded.

---

### Post by nrs on 2007-09-06
> **pmasiar said:**
> Bruce Eckel, well-known expert, requires C as prerequisite to his C++ courses. Do you just trust me, or do you want me to dig out a link for you? :-) 

If I find the link, will it change your mind? :twisted:

Depends on his arguments. The fact that you can bring bad C habits to C++ but not the other way around is seems pretty compelling to me. 

I made the mistake, I regretted it, even though more often than not my projects are plain C.

---

### Post by pmasiar on 2007-09-06
> **nrs said:**
> Generally, I think it is inappropriate for any large project where acceptable levels of performance are desired. Web applications, and mere frontends excluded.

because you quoted my whole comment without trimming, it is hard to me to comprehend to which part of my comment you replied.

But I am still missing how using dynamically typed  "slow" interpreted language will inevitable result ie in poor testing, as you claim. I even know about shop programming in C++ but using Ruby for testing. 

What languages you dislike this way? Are we both talking about Python?

---

### Post by nrs on 2007-09-07
> **pmasiar said:**
> because you quoted my whole comment without trimming, it is hard to me to comprehend to which part of my comment you replied.

> 
"wildly inappropriate use of interpreted languages resulting in poor performance"? Seems to me that you are committing the same noobish error like I warned happysmileman bofore. What kind of application are you talking about? If you program is web-based front-end for a database, 90% of response time is out of your control (database query, web server response), so even doing it in InstantAssembler(tm) which uses no execution time at all, will make it only 10% faster.

> **pmasiar said:**
> 
But I am still missing how using dynamically typed  "slow" interpreted language will inevitable result ie in poor testing, as you claim. I even know about shop programming in C++ but using Ruby for testing. 
 

I didn't claim using interpreted languages will result in poor testing, I claimed that such emphasis on speed to market will result in poor testing. 

> **pmasiar said:**
> 
What languages you dislike this way? Are we both talking about Python?

I don't dislike Python (or any language) so much as I dislike how/when/where it's used.

---

### Post by emperon on 2007-09-07
[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

---

### Post by Wybiral on 2007-09-07
> **emperon said:**
> [http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

Well, he's saying that C is better.

---

### Post by pmasiar on 2007-09-07
> **nrs said:**
> I didn't claim using interpreted languages will result in poor testing, I claimed that such emphasis on speed to market will result in poor testing.

Your argument does not make any sense. If my users are waiting for a feature, and I can choose two languages to implement it: Python will take 2 months, Java 6 months. How choosing Python results in poor testing? I think I will have **more** time for testing, not less.

> I don't dislike Python (or any language) so much as I dislike how/when/where it's used.

Again I am missing something. So you like Python only if it is **not** used? How it is different from hating it? 

And you still did not answered to my question what language experience you have, although you suggested you don't have professional (programming for pay) experience, so I guess you are just a student/hobbyist. In my experience, 95% of people who tried Python for about a week, like it. :-)

---

### Post by Shoot3r101 on 2007-09-07
C++ manages to provide horse power and has more implementation features than other programming languages. The downs of C++ is that it argues too much.

---

### Post by LaRoza on 2007-09-07
> **aks44 said:**
> I couldn't stress enough that learning C first is the best way to get very bad habits when it comes to C++. IMO doing it the other way around allows to better grasp the differences between the two languages, and get the most out of them both.

Others believe the opposite, however, I think the main problem is due to the difference in programming with OO. A procedural programmer would need to learn a lot about OO programming, whereas it *might* be easier to go from OO to procedural, but since I won't be able to back that up with facts (I can't unlearn, then try it again :D.), most speculation in this area is just that.

I used to think it would be better to do C++ first, but now I am not sure, and don't think it really matters, as long as one learns.

---

### Post by aks44 on 2007-09-07
<OT post>

> **pmasiar said:**
> Here is scenario:

Your good customer comes to you, and says: 

> I was happy customer for N years, but now your competition program has this cool feature, and it would save us X monthly, and we really, really want it. So when your program will have it, and how much will cost the upgrade?

Now what? C++ to the rescue? Or some agile language like Python?

Don't get me wrong, I totally see your point. But again, this is all a matter of context.

In *my* *current* context, I'd answer: "*OK, figure out how to migrate your database from our produt to our competitor's, we'll have this feature ready way before*". (granted, I wouldn't say it *exactly* that way but you get the idea... ;))

BTW we face exactly the same problem: even though our product is currently more advanced than our competitors' (but it's only a matter of time for them to catch up on the features), we're having really hard time making their customers switch, because they're pretty locked in. The only real advantage we have in being more advanced is regarding new customers that have to make a choice.

As far as I'm concerned, I'm trying to push interoperability, but neither my company nor our competitors want to hear about it. :( Since most of the important data is stored in blobs, only some serious reverse engeenering (either side) can make this status quo evolve.


But again, you have a point (I won't even discuss its validity, you're *also* right, period). My whole rant is just that it's not *always* the case... ;)

</OT>

---

### Post by aks44 on 2007-09-07
Now, back on topic, ie. C vs C++...

> **Wybiral said:**
> Opinion, not fact.

As a matter of fact, I've seen too many very competent C programmers write unsafe C++ because they are "*used to do it that way in C, and C++ can do all that C does*". Which is only half-true as you know it.
The fact that most people incrementally switch from C to C++ IS the problem IMHO, since most C++ instructions can (and will) throw, and it is simply not possible to write exception-safe code that mixes "plain old" C concepts.

As a basic example, this kind of code is *not* safe, but I've seen it way too often to my taste:
```
Foo* foo = new Foo();
std::cout << foo->bar(); // you can even assume that Foo::bar() doesn't throw...
delete foo;
```

I guess that's this kind of facts which I've witnessed that made me have this opinion... ;)


> **pmasiar said:**
> Bruce Eckel, well-known expert, requires C as prerequisite to his C++ courses. Do you just trust me, or do you want me to dig out a link for you? :-)

I trust you that Bruce Eckel believes that ;). But I don't believe he's right, although I can see his point: "*learn the low level stuff beforehand, because anyway you will need it to fully understand C++*" (which I couldn't agree more, I just don't agree with the path he recommends).

If one's goal is to learn C++, I'd rather recommend to learn first a very high level language (like Python for instance), then very low level stuff (ASM anyone? Here C isn't a good choice IMHO *because of the syntactic similarities* which may confuse the learner later when he comes to C++), then only the mid-level C++. By the time he will know how to write correct C++, he'll also be able to write decent C code.

My whole point being: if you learn C before C++, you WILL have to (temporarily) unlearn C before getting into C++. And IMHO unlearning is one of the hardest things to do. Doing it the other way around doesn't have the potential for problems, so better take the safe path.

---

### Post by pmasiar on 2007-09-07
> **aks44 said:**
> OK, figure out how to migrate your database ... we'll have this feature ready way before


You can even pull this couple times, then customer gets tired of that and switches (switching from windows anyone :-) )

Yes, you are of course right, in your case. Your heavy reliance of CPU-intensive calculation makes C++ better choice. You are in that 20% where Python is **not** the better option. :-)

I will trust more your opinion about C++ from now on. You know your special case, and you know it well.

Were you aware how special and non-standard are your apps? :-)

---

### Post by aks44 on 2007-09-07
<OT>

> **pmasiar said:**
> You can even pull this couple times, then customer gets tired of that and switches (switching from windows anyone :-) )

Our customers (as well as our competitors' customers) just don't dare to switch because they'd loose too much (ie. all their legacy data). As a side note, we also store GPS data so we can also do correlations on those essays that were made a few kilometers away. No sane manager would be willing to loose such a knowledge base... ;)

Switching away from Windows is way less burdensome, just because there are far more resources out there that made interoperability (almost) seamless (most of the time through reverse engeenering BTW ;)).


Vendor lock-in FTW????? (yeah, this is meant as a sarcastic comment, I don't believe in that but unfortunately the reality is there...)


> **pmasiar said:**
> Were you aware how special and non-standard are your apps? :-)

Do you really think I'm unaware of that? ;)

</OT>

EDIT: instead of hijacking threads, maybe we should discuss it on PMs or IRC? ;)

---

### Post by Wybiral on 2007-09-07
> **aks44 said:**
> My whole point being: if you learn C before C++, you WILL have to (temporarily) unlearn C before getting into C++. And IMHO unlearning is one of the hardest things to do. Doing it the other way around doesn't have the potential for problems, so better take the safe path.

Absolutely not true at all. There is no unlearning, you just have to realize the differences and know what C code is OK to use in C++ and what is not.

It's a matter of opinion, and you are trying to argue it as a fact.

Some people will learn C faster and then be able to adopt C++ idioms afterwards, some people may be better off starting with C++, then learning C.

But it is a matter of opinion and personal preference.

---

### Post by pmasiar on 2007-09-07
> **aks44 said:**
> Vendor lock-in

it works profitable for you if **you** are the vendor and **you** have the keys from the golden cage. :-)

> instead of hijacking threads, maybe we should discuss it on PMs or IRC? ;)

nah, it just grew OT step by little step ... and I think it was educational :-)

---

### Post by aks44 on 2007-09-07
> **Wybiral said:**
> There is no unlearning, you just have to realize the differences and know what C code is OK to use in C++ and what is not.

To me, "realizing the differences" is the same as "unlearning" (YMMV). And as far as I can think of, not a single "plain old" C concept is OK in a C++ context... if you know some code **_that mixes *both* C & C++ concepts_** (including C++ exceptions, since all decent C++ code uses exceptions ; tough enough?) that would contradict my statement please show it as I'd be more than happy to expand my knowledge. Or maybe I'm too much biased?

EDIT: Just in case... I've never been saying that you *can't* learn C++ after C, just that it's definitely *easier* to do it the other way around...



> **pmasiar said:**
> it works profitable for you if **you** are the vendor and **you** have the keys from the golden cage. :-)

Both my company and our competitors are sharing the keys to that "golden cage"... They (yeah, "they" since I'm quite a newcomer in that business, only been there for 2 years) managed to lock both the customer in, and the competitors out. Who talked about open standards? (j/k again ;))

---

### Post by CptPicard on 2007-09-07
Oh, how I love the power of vendor lock-in when I am the vendor. :)

I'm currently almost full-time consulting for a friend of mine who has a fairly hard to understand business, but that manages to produce good money for himself and investors. He needs someone to be intimately knowledgeable of what he is doing, to quickly test some analysis ideas and implement the actual tools he uses and to maybe contribute one's own ideas as to how to advance his business.

I've been involved for a few years, and written his toolkit and website. I would be extremely hard to replace, as I have made sure that, uh, not everything is quite obvious in my code, and in addition I know just way too much of what he's doing... training someone else would take a year.

I'm on call 24/7 when it comes to maintaining the website (not a big chore really), work pretty much when I like as long as I get stuff done on the analysis tools side, and am in a strong bargaining position when we get together every few months over beer to discuss what next... and the business has a projected 5 million euro turnover and 10% profit margin for 2007. With two guys. ;)

---

### Post by aks44 on 2007-09-07
> **CptPicard said:**
> I would be extremely hard to replace, as I have made sure that, uh, not everything is quite obvious in my code

... what... are... comments... for? ;) [*I'm beating the hell out of my programmers, but I tend to have the same attitude, so no hard feelings... ;)*]

---

### Post by CptPicard on 2007-09-07
> **aks44 said:**
> ... what... are... comments... for? ;) [*I'm beating the hell out of my programmers, but I tend to have the same attitude, so no hard feelings... ;)*]

Not only that, but my implementation strategies tend to be slightly experimental for the learning experience, and I do not shy away from producing code that makes use of language features to the fullest. I also throw in algorithms that are maybe slightly overkill, but ensure that he would need to really get in a pro to replace me, which would be unlikely as most people my level prefer to have a real job, or then he would have to take some kid on board who would have to recode it all (and wouldn't be as useful and might even go blindly down dead-end alleys, as most of his problems tend to be hard number-crunching with underlying NP-hardness at times). :)

---

### Post by Wybiral on 2007-09-07
> **aks44 said:**
> To me, "realizing the differences" is the same as "unlearning" (YMMV). And as far as I can think of, not a single "plain old" C concept is OK in a C++ context... if you know some code **_that mixes *both* C & C++ concepts_** (including C++ exceptions, since all decent C++ code uses exceptions ; tough enough?) that would contradict my statement please show it as I'd be more than happy to expand my knowledge. Or maybe I'm too much biased?

EDIT: Just in case... I've never been saying that you *can't* learn C++ after C, just that it's definitely *easier* to do it the other way around...


And I didn't say "concept" I said "C code". It's the concepts that you need to adjust when jumping between C and C++, much of the code will remain with the exception of the stuff that C++ adds on.

So it's safe to say that C++ is extending C and as a result you need to learn new idioms to deal with the new tools at your disposal. It makes more sense to me to learn the non-extended version before learning the extended.

I don't have a problem with you saying that you personally think it's harder to learn C++ after C, my problem is that you explain it as a fact. It's not, some people will do better one way, some the other. Just because something may have worked for you doesn't make it a proven fact that it will work for everyone. Agree?

---

### Post by nrs on 2007-09-07
> **pmasiar said:**
> Your argument does not make any sense. If my users are waiting for a feature, and I can choose two languages to implement it: Python will take 2 months, Java 6 months. How choosing Python results in poor testing? I think I will have **more** time for testing, not less.


Note: We're talking about market rushing, unloading the software as soon as it's "complete". Of which, I said the inappropriate use of interpreted languages are a symptom not the problem. You'd have a point, if say the project wouldn't ship in a year but was done in 2 months; leaving 10 for testing vs 6 for Java. Otherwise they'd have the same abysmal testing. I still don't know where you're getting your 2 vs 6 months from.


> **pmasiar said:**
> 
Again I am missing something. So you like Python only if it is **not** used? How it is different from hating it? 


You are indeed missing something. I don't dislike any language just where / when / how they're used. I don't know how to be any clearer. I don't dislike sports cars. I dislike them when they're being used to fetch groceries. 

> **pmasiar said:**
> 
And you still did not answered to my question what language experience you have, although you suggested you don't have professional (programming for pay) experience, so I guess you are just a student/hobbyist. In my experience, 95% of people who tried Python for about a week, like it. :-)

Everything under the sun. If I were to rank them; 1.) C 2.) C++ 3.) Perl 4.) Python. after that I really can't rank them.

---

### Post by pmasiar on 2007-09-08
> **nrs said:**
> inappropriate use of interpreted languages are a symptom not the problem.....I don't dislike sports cars. I dislike them when they're being used to fetch groceries. 

So what is in your opinion "appropriate" use of a scripting language like Python? Is web-based front-end for a database "appropriate"? If not, what language is?

>  We're talking about market rushing, unloading the software as soon as it's "complete". 
....
I still don't know where you're getting your 2 vs 6 months from.

Well, I agree with you that rushing is wrong. But why is wrong using RAD language with higher productivity wrong? 

It is well-known fact that developing a program in dynamically typed language like Python takes less time that developing same program in strictly typed language like Java or C or C++. Do you dispute **that**?

---

### Post by nrs on 2007-09-08
> **pmasiar said:**
> So what is in your opinion "appropriate" use of a scripting language like Python? Is web-based front-end for a database "appropriate"? If not, what language is?


I'm sure you could find plenty of appropriate uses for it, it's just knowing when it's inappropriate. I myself use it for testing concepts which may find themselves in my game project (C), general utilities for my game which just don't make sense doing in C. And other stuff. I wouldn't consider a web front-end an inappropriate use because of the reasons you cited earlier. 


> **pmasiar said:**
> 
Well, I agree with you that rushing is wrong. But why is wrong using RAD language with higher productivity wrong? 


It isn't wrong, never argued it was wrong. What I argued was wrong was choosing them purely because you wanted a high speed to market without other considerations. 

> **pmasiar said:**
> 
It is well-known fact that developing a program in dynamically typed language like Python takes less time that developing same program in strictly typed language like Java or C or C++. Do you dispute **that**?

Nope, just the large differences. Especially in regards to Java.

---

### Post by aks44 on 2007-09-09
> **Wybiral said:**
> And I didn't say "concept" I said "C code". It's the concepts that you need to adjust when jumping between C and C++,

I get your point. I guess we misunderstood because of our choice & interpretation of words. To me what you call "code" (if I understood correctly) is rather "syntax", in my understanding the "code" itself is the result of applying concepts to a problem and expressing that through a particular syntax. IOW the *resulting* code is always intimately bound to both the concepts and the syntax of the language you're using, in the context of a problem.

You may say that I'm just playing on words, and you wouldn't be totally wrong. :) But that's not *just* playing on words.
For natural languages as well as computer languages, words & grammar are meant to express concepts, and adequate communication can only take place if the involved parties already share (or agree on) the same references, ie. if a word or sentence triggers exactly the same concepts both sides.
I just didn't realize earlier that we were putting slightly different meanings on the same words.

Now call me picky, I know I am. ;)


> **Wybiral said:**
> much of the code will remain with the exception of the stuff that C++ adds on.

So it's safe to say that C++ is extending C and as a result you need to learn new idioms

As far as syntax is concerned, yes. But again, the shift in paradigms will result in very different code (still in *my* definition of the word "code", which I hope is clear by now).


> **Wybiral said:**
> Just because something may have worked for you doesn't make it a proven fact that it will work for everyone. Agree?

Again, I agree. I also hope that in the light of this explanation you'll better understand my previous rants... ;)

---

