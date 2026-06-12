---
title: "Why are programs being developed in C# more and more?"
date: 2008-04-11
forum: Programming Talk
---

### Post by thenetduck on 2008-04-11
Hey 

This isn't a flame question, 

I am wondering, I just have noticed that more and more gnome apps are being made in Mono C# vs something like C++. Is there some reason? I mean for instance, F-Spot, Beagle, Tomboy all apps that  use almost every day yet they are c# instead of c++, Does anyone know why this is? Is C# going to be around forever? Or I mean is the language going to be activly developed as much as c++. I am a little confused. Maybe it's easier to create a gui in c# is that why? 

Thanks for and explanation. 

The Net Duck

---

### Post by Caduceus on 2008-04-11
I don't know much on the subject, but C++ and C# are two different languages with two different purposes. It could be that C++ carries a lot of uneccesary 'weight', and C# is more suited for the job, or it could be a matter of personal preference. Just my initial thought.

---

### Post by LaRoza on 2008-04-11
> **thenetduck said:**
> Hey 

This isn't a flame question, 

I am wondering, I just have noticed that more and more gnome apps are being made in Mono C# vs something like C++. Is there some reason? I mean for instance, F-Spot, Beagle, Tomboy all apps that  use almost every day yet they are c# instead of c++, Does anyone know why this is? Is C# going to be around forever? Or I mean is the language going to be activly developed as much as c++. I am a little confused. Maybe it's easier to create a gui in c# is that why? 

Thanks for and explanation. 

The Net Duck

Three apps is hardly a trend. Do you have some better statistics?

---

### Post by sq377 on 2008-04-11
C and C++ are fairly difficult to program in.  C# is simpler, and many of the programmer converts from windows know C# already.  I'm a C person, and I don't like sharp objects near my code :P.

---

### Post by thenetduck on 2008-04-11
> **LaRoza said:**
> Three apps is hardly a trend. Do you have some better statistics?

Well it seems like every project that I am interested in developing on because I think it's a cool proeject is useing C# (which I know very basic) The three I mentioned are examples. Obviously c/c++ are bigger than c# . 

I guess there isn't as many as I thought (just seemed that way) but you have to admit, it's gaining some popularity for some reason.

The Net Duck

---

### Post by LaRoza on 2008-04-11
> **thenetduck said:**
> 
I guess there isn't as many as I thought (just seemed that way) but you have to admit, it's gaining some popularity for some reason.


The open source implemenation of C# has improved to the point it is a language that is usable.

I personally wouldn't use it (unless I got paid) but is is free and available for Linux.

---

### Post by pmasiar on 2008-04-11
C# is easy to start with for many (majority?) of .NET developers who want to goof aroud Linux but don't dive into too deep waters. Novel thinks that it knows how to play with fire safely, time will tell if they were right, or they end up like so many other companies collaborating with MSFT. 

It is also possible that times changed and MSFT is not as all-powerful as it was 10-15 years ago. With GPLed Java for open-source enterprise applications, and Google App Engine for web apps, application landscape looks very differently than in 1995 when Windows was the only game in the town. As a result, MSFT might decide not to squash competitors this time, but join them to fight against Google and IBM+Sun/Java. And compiled C# for CLR libraries with dynamic scripting languages on DLR for front-end, MSFT has very intriguing platform.

---

### Post by slavik on 2008-04-11
for gobject development there is a new language called Vala which looks like C# but is especially made for gobject development and gets translated into C.
more info: [http://live.gnome.org/Vala](http://live.gnome.org/Vala)

---

### Post by lnostdal on 2008-04-12
slavik strikes a point at the very core of gnome/gtk here .. gobject is really where all focus _should_ be

..gobject is the real "language" of, and for gnome/gtk..

what language you use on top of that is or should ideally be irrelevant! .. gnome/gtk is meant to be a platform for cooperation and compatibility regardless of programming language .. that is the idea anyway(#1), and it seems like the gnome/gtk+ developers are finally beginning to realize this as focus seems to be switching to these inner-most parts of the platform recently .. good news =)

but what c#, mono and novell/ms might effectively be doing is to embrace, extend and extinguish these things ( [http://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish](http://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish) ) or this idea....

..because if they do not extend the _core libraries_ of gtk/gnome (the gobject stuff and things close to it) but instead extend only their outer "branch" - they really are on the MS path of e-e-e ..... history repeating itself yet again (edit: exactly as with microsofts implementation of java ......)

..i'm keeping a safe distance.. i'm not stupid enough to fall in a MS trap -- especially not one placed in my own house (the Linux platform and environment) .. if it is a trap, it's placed strategically _exactly_ where it should be ..

 .. if it isn't - why should i care? c# is _not_ a very nice language and environment anyway .. there are _way better_ alternatives out there


#1: i have tried implementing language bindings the Right Way using only the gobject path instead of generating code based on c header files (this is the traditional way of doing FFI, but it is the Wrong Way) .. i still have this project on hold, as i am awaiting improvements to gobject and the core libraries in gtk/gnome before i continue it ..

if focus from fixing the core problems in gtk/gobject/gnome where to be "stolen" by mono/novel/c#/ms .. they would effectively have extended, and extinguished everything else around them -- and the very point of gtk/gnome/gobject is gone; no _real_ collaboration and cooperation would be possible .. (or it would only be at the premises of the CLR .. i'm not interested in (only) that)

edit: i'm quite close to going off on a frantic rant containing multiple F words here actually .. just stay away, imho ..

edit2: note that i'm aware of the history behind gtk+/gnome .. miguel etc. .. he's smart and all .. but that doesn't mean people can't **** him over

---

### Post by ricegf on 2008-04-12
[TIOBE]("http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html") is one reasonably well-thought-of index of the "popularity" of programming languages, based on the number of skilled engineers world-wide, courses and third party vendors. It ranks C# at #8 currently, well below Java (#1), C (#2), and C++ (#5).  TIOBE actually selected Python "language of the year" in January as the fastest growing language on its index; it is currently #7.

Fascinating stuff (well, to me :-) ), but the real driver should be the language that enables you to get _your_ work done most efficiently and with which _you_ feel most comfortable.  I'm personally not comfortable with C#'s lineage, and worry about "patent traps". Thus I prefer more "open" languages such as C and Python. But as always, your mileage may vary.

---

### Post by apoth on 2008-04-12
Speed of development is drastically reduced with C# and the knowledge entry barrier is much lower.

Yes, there may be a bloat / performance cost. But more and more C/C++ is left for the niche cases where that performance and small footprint is a necessity. I think Linux has been probably been hit by this less than other OSes, to its benefit.

---

### Post by samjh on 2008-04-12
> **thenetduck said:**
> Hey 

This isn't a flame question, 

I am wondering, I just have noticed that more and more gnome apps are being made in Mono C# vs something like C++. Is there some reason? I mean for instance, F-Spot, Beagle, Tomboy all apps that  use almost every day yet they are c# instead of c++, Does anyone know why this is? Is C# going to be around forever? Or I mean is the language going to be activly developed as much as c++. I am a little confused. Maybe it's easier to create a gui in c# is that why? 

Thanks for and explanation. 

The Net Duck

C# is the most prominent language in Microsoft's .NET Framework.  And the .NET Framework is the most popular application development framework for Windows-based systems in business.

Novell's Mono project provides a FOSS implementation of the ECMA standardised portion of the .NET Framework and the C# language compiler, along with its own versions of Microsoft's proprietary .NET libraries.

The Mono project is the brain-child of Miguel de Icaza, who was one of the founders of GNOME.  The Mono project developed a C# language binding for GTK+ and GNOME.  One's imagination doesn't have to stretch far to think that Mono's support for GNOME and GNOME's connection with de Icaza has had considerable influence it the adoption of C# and Mono to develop GNOME applications.

C# and Mono provide a solid framework to develop "managed" applications.  These have automatic memory management and the ability to run in a "sandbox" environment similar to Java.  Software developed using those technologies tend to have fewer programmer errors, memory problems, and security vulnerabilities, than equivalent software developed using C or C++.  Of course, Python and other languages offer similar features, but they are much slower than C# and Mono, and to achieve equivalent speed often requires juggling between two languages (eg. Python and C) and the attendant increases in tools.  By contrasts the Mono project, like its .NET parent, includes a tightly-integrated development tool called Monodevelop, which includes a great depth of development tools such as a WYSIWYG graphical user interface designer, debugger, documentation viewer, project manager, etc., all without having to touch any other language or external development tool.

There are questions about the legalities of the Mono project, but all such arguments are purely speculative.  There is no doubt that Microsoft has patent rights to the non-ECMA portions of Mono's .NET implementation.  Whether those patents are legally enforceable and whether patent breaches will have a negative effect on the Mono project and any projects using Mono, is very much open to question.

Technically, C# and Mono/.NET are good technologies.  I prefer Java over Mono, but nevertheless, credit is given where it is due.

---

### Post by Shin_Gouki2501 on 2008-04-12
this is representing an crucial fact of linux desktop apps. C# uses garbage collection via its runtime. Also the design concepts are , compared to C++( and GUI apps), quite high level.
Programming languages enable you to do almost everything. So you can develop GUI Applications in C# or C++ or C. The results will differ in diffrent aspects like:
1. how long did it take to develop the application
2. how good is the application maintainable
3. how much resources does the application use
4. how responsive is the application
5. how much feature does the application offer
Here is my vauge rating regarding C# and C++ (more better, 5 max):
1.
C#:****
C++:**
2.
C#:****
C++:***
3.
C#:**
C++:****
4.
C#:**
C++:****
5.
C#:****
C++:***
Since it takes longer to develop in C++ less features can be implemented in the same application.

Gargbage Collection and High Level concepts enable faster application develeopment with C#. You can do the same with C++ but it takes WAY more time.

wbr Shin Gouki

---

### Post by YetAnotherNoob on 2008-04-12
Reasons for using it include:
Powerfull language with modern features that some older languages lack.
Fantastic framework, loads of well designed classes.
The CLR is a brilliant concept. The more I learn the more I respect its design.
Loads of documentation/reference material.

All of the above help reduce the complexity, boiler plate code, and time required to implement a product.

---

### Post by LaRoza on 2008-04-12
> **Shin_Gouki2501 said:**
> this is representing an crucial fact of linux desktop apps. C# uses garbage collection via its runtime. Also the design concepts are , compared to C++( and GUI apps), quite high level.
Programming languages enable you to do almost everything. So you can develop GUI Applications in C# or C++ or C. The results will differ in diffrent aspects like:

Since it takes longer to develop in C++ less features can be implemented in the same application.

Gargbage Collection and High Level concepts enable faster application develeopment with C#. You can do the same with C++ but it takes WAY more time.

wbr Shin Gouki

Why not D then?

---

### Post by LaRoza on 2008-04-12
> **YetAnotherNoob said:**
> 
The CLR is a brilliant concept. The more I learn the more I respect its design.


You mean **CLI**. CLR is an Windows only implementation of the CLI standard.

The concept is nothing new. Java, Python, Perl, Ruby, and other do similar things.

[http://en.wikipedia.org/wiki/Common_Language_Infrastructure](http://en.wikipedia.org/wiki/Common_Language_Infrastructure)

---

### Post by Oxnigarth on 2008-04-12
It is probably because it is similar to C/C++ but it has a more friendly way of usinig it and still you have the OOP tools. As it has been previously said I haven't really seen that many applications done in C# but I know it is used for web developing too.

---

### Post by LaRoza on 2008-04-12
> **Oxnigarth said:**
> It is probably because it is similar to C/C++ but it has a more friendly way of usinig it and still you have the OOP tools. As it has been previously said I haven't really seen that many applications done in C# but I know it is used for web developing too.

I would say it is similar to Java. It is nothing like C, and pretty far from C++. It has a C style syntax, but that is just syntax.

---

### Post by xlinuks on 2008-04-12
Using C#  (and almost same applies to Java) you have to cope with:
- A pretty slow startup
- always a second-class system citizenship (which is sometimes critical)
- slower code execution
- more memory and CPU consumption
- automatic memory management = in fact slow and (sometimes) buggy/bloated runtime
- vulnerability to FUD and questionable legal issues
-  the bugs that always exist in the C# (and Java) runtimes
- write once, test everywhere (applies to C# as well)
- other stuff..

---

### Post by Zugzwang on 2008-04-12
> **xlinuks said:**
> Using C#  (and almost same applies to Java) you have to cope with:
- A pretty slow startup
- [...]
- write once, test everywhere (applies to C# as well)
- other stuff..

So these are the reasons why more and more programs are being developed in C#? Interesting. So either all of the developers of these programs are all idiots *or* your list is a little bit biased. ;-)

---

### Post by Shin_Gouki2501 on 2008-04-12
well i think he simply ignores the fact that in "real" enterprise business implementation is choosen by diffrent factores ( see above).
In most cases or scenarios C# will do just fine.
As i said you *could*  probably implement every C# Application in C++ "faster" its *simply* too ineffective, as it costs a programemr more time ( or even a better programemr ;) ). 
C++ surely has its place as C# does,it dependds on the domain.

Ah and LaRoza  D is nice and fine but you cannot compare .NET Platform for Windows ruinnig C# with D. 
Its way a dimension ahead ;)
Besides all the nice Technology aspects of Programming languages, in real business its quite more often a polotical choice what platform you use.

---

### Post by LaRoza on 2008-04-12
> **Shin_Gouki2501 said:**
> 
Ah and LaRoza  D is nice and fine but you cannot compare .NET Platform for Windows ruinnig C# with D. 
Its way a dimension ahead ;)


I didn't try to. I was merely pointing out the enumarated advantages of C# over C++ are all in D, not that D has every feature of C#.

---

### Post by Shin_Gouki2501 on 2008-04-12
which is also an advantage and so its mising ;)

---

### Post by YetAnotherNoob on 2008-04-13
> **LaRoza said:**
> You mean **CLI**. CLR is an Windows only implementation of the CLI standard.

[http://en.wikipedia.org/wiki/Common_Language_Infrastructure](http://en.wikipedia.org/wiki/Common_Language_Infrastructure)

My experience with C# is limited to the CLR.  I haven't worked with mono. Not sure about the implementation differences.

---

### Post by TenPlus1 on 2008-04-13
Viva la BASIC!

:)

---

### Post by atsukoarai86 on 2008-04-14
I think it's because C# is simpler than C++, and it's included in the .NET platform. More and more, the market is moving over to the .NET platform, and this is where a lot of jobs and money are going to be. A friend of mine just took a job in Maryland making twice the money he's making now, working with C#.NET.

I'm looking forward to learning it! Gotta take a class in it myself after I finish the C++ sequence or classes. All hail computer science!

---

### Post by LaRoza on 2008-04-14
> **atsukoarai86 said:**
> I think it's because C# is simpler than C++, and it's included in the .NET platform. More and more, the market is moving over to the .NET platform, and this is where a lot of jobs and money are going to be. A friend of mine just took a job in Maryland making twice the money he's making now, working with C#.NET.

I'm looking forward to learning it! Gotta take a class in it myself after I finish the C++ sequence or classes. All hail computer science!

C# is more complicated than C++.

More and more the market seems to be moving open source. .NET is popular in the job market, but Java, C and Python are big as well and are growing.

---

### Post by pmasiar on 2008-04-14
With C# you are betting your career on Microsoft technologies, against Open Source. It might make sense for some people, but it is not a silver bullet best for all situations. Even MSFT itself is opening, shifting to using C# for libraries and implementing for CLI/DLR more agile dynamically typed languages like Python (MSFT: IronPython) and Ruby (MSFT: RubyOnSteel). So pick carefully, and be prepared to change direction. Ie Google's App Engine is destined to dramatically change web application area, and C# implementation is unlikely, IMHO.

---

### Post by themusicwave on 2008-04-14
> **atsukoarai86 said:**
> I think it's because C# is simpler than C++, and it's included in the .NET platform. More and more, the market is moving over to the .NET platform, and this is where a lot of jobs and money are going to be. A friend of mine just took a job in Maryland making twice the money he's making now, working with C#.NET.

I'm looking forward to learning it! Gotta take a class in it myself after I finish the C++ sequence or classes. All hail computer science!

The one thing you have to look at with claims of making "twice what he is making now" is the cost of living.

I live in Pittsburgh, PA which was ranked the most affordable city in the USA recently.  I make about half what a programmer would make in many other places.  However, I also pay half as much as them for rent, food, etc.

Many of my friends make more than double what I make in California and are having trouble getting by with the insane prices out there.

Don't fall into the trap of forgetting about cost of living, salaries in different parts of the world/country can't be compared so easily.

I make less than people in other parts of the country, but I am living quite comfortably.

---

### Post by pmasiar on 2008-04-14
That might be all tue for mortgage/rent, but IMHO west-PA price of car, or foreign vacation is closer to national average :-)

But yes, I also decided not to try surviving in Silicon Valley - rent is ridiculous, home prices are in outer space, and commute is insane! :-)

---

### Post by bruce89 on 2008-04-15
> **thenetduck said:**
> I am wondering, I just have noticed that more and more gnome apps are being made in Mono C# vs something like C++.

<pedant>
Most GNOME programs are C actually. To be precise, they use C with the GObject object system, which was invented to make bindings easy. This is why so many programs are written in Python these days.
</pedant>

---

### Post by schmendrick on 2008-04-16
why is C# used more and more for linux applications? 
first it is of course easier&faster to create GUI apps with high level languages that use garbage collection like C# and Java in comparison to C/C++.
many have said so before and its a valid point. but i think there is another point:
there is a growing mass of .NET programmers out there getting curious about linux. 
the "obstacles" windows users/programmers have to overcome to get familiar with linux become less and less. 
now those people (me being partly one of those myself) look over the microsoft-rim, try out linux and then of course also want to make some programs for that new platform.

but when you are used to .NET you are possibly very enthusiastic about C#: its just a great, comfortable language in the opinion of many people [coding on windows] out there.
(a former working colleage of mine is even willing to stay with my old company for the sake of coding C# instead of switching to another company offering him some more money for coding a java app. i also took the language into consideration when i was offered a job as a java developer instead of doing C#, but then took the chance anyway.)
when you are used to .NET you are used to have ONE tool (visual studio) with which you can do everything: code, compile, make GUIs, have documentation included. .NET developers are used to LOADS of documentation with examples being there in the instant of a mouseclick. 
and monodevelop is now providing that same thing for linux. switch to ubuntu, install monodevelop, and you more or less feel at home.
when i first looked how to develop a GUI application for windows&linux in C++ i was shocked: no WYSIWYG editor for the gui, needing to think of the differences in linux&windows, then needing to install wxWidgets (of course could have taken another framework) seperately, getting it to compile/run...

some of those .NET people are unwilling to learn a new language or a framework "just" for being able to create linux apps. they are happy with making programs that run on 90% of the home computers. if the other 10% running linux can be included without much effort they will do so. if not, they will leave it.
they want to have C#. (i am pretty sure most of them will also want to use Visual Studio when creating the App.)
with mono & monodevelop they now have a tool with which they are familiar with and can start coding right away. like LaRoza said, 

> The open source implemenation of C# has improved to the point it is a language that is usable.

Windows programmers who are willing to contribute to the linux community but dont want to learn another language for whatever reasons are now able to do so. Then they start, make the first 2 small programs, and then they are already in the linux scene and start contributing to bigger projects for GNOME.

And that is IMHO a very important aspect why there are many new C# programs sprouting for linux right now.

lnostdal said
> what language you use on top of that is or should ideally be irrelevant! 

could be, but i think there are many coders out there who don't see it that way and want *their* language. 
why waste their potential contribution-energy to linux and ignore them? 

i also agree with samjh, i dont see the threat of C# for linux. his explanation i think is also a very important aspect why mono/GNOME are close together.

i also don't understand why so many people have to say, "use python", "use Vala" or whatever instead of C#. why get people to use a different language? 
yes they are also other high level languages out there, offering garbage collection and
they also get the job done, but why not use C# if you are already familiar with that?
Just don't use it because it was originally created by MS and everything coming from Microsoft is automatically bad and evil? but i understand if you think mono is bad for linux (cause of EEE) then it is a red flag for you. i on the other hand think its a great opportunity to get many more apps for linux which will effectively draw more windows users to use linux. 

last point, xlinuks said

> Using C# (and almost same applies to Java) you have to cope with:
- A pretty slow startup
- always a second-class system citizenship (which is sometimes critical)
- slower code execution
- more memory and CPU consumption
- automatic memory management = in fact slow and (sometimes) buggy/bloated runtime
- vulnerability to FUD and questionable legal issues
- the bugs that always exist in the C# (and Java) runtimes
- write once, test everywhere (applies to C# as well)
- other stuff..

Zugzwang already countered that, additionally I dont think that C# is that much slower if implemented correctly.
of course languages like C# will always be slower than when doing things in C++! 
But i'd like to point out that even the gaming industry now begins to use C# for games (which are of course time-critical applications)
[http://de.wikipedia.org/wiki/XNA_(Microsoft](http://de.wikipedia.org/wiki/XNA_(Microsoft))
Plus: bugs also exist for other languages. STL for C++ was famous for its bugs in former times, wasn't it? (i guess thats the reason why it is still not completely accepted by many programmers?)

of course i could be wrong ;)

whew thats it, that took my lunch time. sorry if something is not spelled right or something, i needed to hurry a bit to get this done

---

### Post by jespdj on 2008-04-16
The reason why C# and Mono are popular with GNOME programmers is because [Miguel de Icaza](http://en.wikipedia.org/wiki/Miguel_de_Icaza) is involved in both GNOME and Mono.

I wonder why he and others wanted to implement Microsoft's proprietary .NET stuff on Linux, and why they are using it in some of the standard GNOME applications - which binds GNOME to Mono (i.e. when you install GNOME and its standard apps you must also have Mono installed).

Microsoft .NET works exactly the same as Java, with its virtual machine to run bytecode in a managed environment. In fact, Microsoft started with .NET when Java was becoming popular. It's just another instance of Microsoft stealing a good idea and trying to make the whole world use their version.

Sun is clearly much more open-source friendly than Microsoft (Sun's implementation of Java will be GPL'ed in the next version), and Sun's Java VM is a very mature and very high quality environment to run bytecode.

Why didn't GNOME use Java instead of implementing their own version of a Microsoft technology? Java would have been a much more logical choice for an open-source system.

---

### Post by pmasiar on 2008-04-16
I agree that C# is convenient way for Windows programmers to contribute to linux, and I have no problem with that, i appreciate any free program which enhances usability of Free software. But when you say
> **schmendrick said:**
> 
i also don't understand why so many people have to say, "use python", "use Vala" or whatever instead of C#. why get people to use a different language? 
yes they are also other high level languages out there, offering garbage collection and
they also get the job done, but why not use C# if you are already familiar with that? 
Just don't use it because it was originally created by MS and everything coming from Microsoft is automatically bad and evil?  

It is not about language from Microsoft. Garbage collection is not the only language Python has. No offense, but you obviously are not familiar with any dynamically typed language, and you fit into Blub paradox (read [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) yes you need to read it to understand, don't be offended). As GC improves 3 times C# programmer productivity compared to C++, dynamic typing improves Python programmer productivity 3 times compared to C# or Java.

Suggesting to learn more HLL than C# people are doing you a favor: there are features in languages you do not miss (yet) because neither Java or C# have them.

Of course you are free to stay with C# or Java all your life, but you will never know what you are missing, and what we are talking about, and you will be forever offended when someone talks about other languages, exactly like Blub programmer in above linked article. Up to you! :-)

I myself would never consider developing Free software in something like Java or C# in my free time because it is not fun, it is hard boring work.

Good link from another thread (thanks to  stevescripts): [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

---

### Post by Can+~ on 2008-04-16
> **schmendrick said:**
>  also don't understand why so many people have to say, "use python", "use Vala" or whatever instead of C#. why get people to use a different language?

You're not constrained to a single language, we usually say Python since it's easier to start through there:
-It will teach you how to use indentation properly (trust me, some of my friends on C give me horribly indented code, completely unreadable)
-Syntax is quite short, you don't need to mySomething.anotherThing.YetMoreThingies.method(); to do a single task.
-It's preloaded on ubuntu.
-It has a interactive mode for learning.

Even if we suggest python, we don't force people to use it.

And I tried C#, I didn't like it a single bit (even before I started with py).

---

### Post by skeeterbug on 2008-04-16
> **pmasiar said:**
> ..
read [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) 
..

I remember reading that several months back. If you currently work for a startup or plan on it at some point, make sure to read it. Hell, read it anyways. Even if you don't use LISP, a lot of it applies to where Ruby and Python are today.

---

### Post by pmasiar on 2008-04-16
Paul Graham has hobby horse - promoting Lisp. Most people ignores that and read his essays in language independent way :-) : they apply exactly about Lisp or many other dynamic languages, for any programmer who considers C# (or Java, or C++) be the end and final solution of human civilization (so, by definition, a Blub programmer). :-)

---

### Post by mssever on 2008-04-16
> **pmasiar said:**
> Paul Graham has hobby horse
And so does pmasiar, regarding Python... :)

---

### Post by slavik on 2008-04-17
> **pmasiar said:**
> I myself would never consider developing Free software in something like Java or C# in my free time because it is not fun, it is hard boring work.

yet, there is Tomboy and Beagle. ;)

---

### Post by LaRoza on 2008-04-17
> **slavik said:**
> yet, there is Tomboy and Beagle. ;)

I don't think pmasiar works on those in his free time.

---

### Post by slavik on 2008-04-17
> **LaRoza said:**
> I don't think pmasiar works on those in his free time.
you forgot to put the ';)' smiley in your reply, :P

I have actually programmed with Mono-C# (using Monodevelop) and to me it seems like (in comparison with Java) wherever Java is red, C# is blue.

Same as US and USSR during the cold war (or even US and Russia now).

Same **** (I put the asterisks there) different name. :)

---

### Post by pmasiar on 2008-04-17
> **slavik said:**
> yet, there is Tomboy and Beagle. ;)

I am not sure what your comment mean. :confused:

I am NOT claiming that programming in C# in free time is not possible: I agree with others comments here that C# might be simple way for Windows programmers to  contribute to Free Software.  

I am just claiming that **I** would not do it, and I gave **my** reasons. Do **you** hack on C# in free time? Do you consider C# good language for Free software? (surely not better than Perl, is it :twisted: ) Am I allowed to have different opinion than Windows-only programmers? 

Existence of Beagle is anecdote which shows that Free hacking in C# is possible, but does not prove OP thesis that C# hacking increases, IMHO. And your comment was orthogonal to either.

---

### Post by slavik on 2008-04-17
Perl and C# are completely different languages.
Unfortunately I can't afford to hack in my free time (that requires having free time in the first place).

C# is as good for OSS as Java is. The language is not the problem, the patented libraries are.

as for C# use in OSS increasing, I haven't seen any recent studies about any language usage in OSS projects.

EDIT:
There is also Gtk# (AFAIK, there are not Gtk bindings for Java). This is another reason why GNOME apps might be increasingly written in C#, although there is also Vala which is intented to be a language for GObject (GTK) development.

---

### Post by jespdj on 2008-04-17
> **slavik said:**
> There is also Gtk# (AFAIK, there are not Gtk bindings for Java). This is another reason why GNOME apps might be increasingly written in C#, ...
Ofcourse there is a [GNOME / GTK+ binding for Java]("http://java-gnome.sourceforge.net/"), there has been for a long time, so that's not an argument.

.NET / Mono is exactly the same as the Java runtime environment with regard to how it works.

It's strange that people chose to implement their own version of Microsoft-proprietary stuff instead of using the much more open-source friendly Sun Java VM and runtime environment.

---

### Post by LaRoza on 2008-04-17
> **jespdj said:**
> 
It's strange that people chose to implement their own version of Microsoft-proprietary stuff instead of using the much more open-source friendly Sun Java VM and runtime environment.

No, they are implementing the ECMA standard, not "their own version".

---

### Post by Zugzwang on 2008-04-17
> **jespdj said:**
> It's strange that people chose to implement their own version of Microsoft-proprietary stuff instead of using the much more open-source friendly Sun Java VM and runtime environment.
One of the reasons is that C# has a lot a language features which Java doesn't have. Two example that come to my mind are "properties" which is effectively (almost) just syntactic sugar but avoids the necessity for calling putters and getters manually. Far more important are the functional extensions that MS added recently which simplify *some* tasks *extremely much*. Note that also generics were introduced in .NET earlier than Java.

Also, .NET is not just C#, but take for example the pretty new F# language I've tried recently which has some very nice features.

---

### Post by Shin_Gouki2501 on 2008-04-17
> **Zugzwang said:**
> Also, .NET is not just C#, but take for example the pretty new F# language I've tried recently which has some very nice features.

Java Platform has Scala for that :P

---

### Post by peterdk on 2008-05-30
I am used to Ruby scripting, and C/C++ was just to low-level for me. I really dislike the ugly syntax and it is just way beyond me.
C# on the other hand is beautiful, has a very nice crossplatform .net library now, has garbage collection like Ruby, and a lot more high-level language stuff. 

For me it is a very attractive step from a scripting language to a more "real" programming language, while not making it unnecessary difficult. It is probably a bit slower and uses more resources than C/C++, but that's the price for programmer productivity. At least programmers like me.

---

### Post by LaRoza on 2008-05-30
> **peterdk said:**
> I am used to Ruby scripting, and C/C++ was just to low-level for me. I really dislike the ugly syntax and it is just way beyond me.
C# on the other hand is beautiful, has a very nice crossplatform .net library now, has garbage collection like Ruby, and a lot more high-level language stuff. 

For me it is a very attractive step from a scripting language to a more "real" programming language, while not making it unnecessary difficult. It is probably a bit slower and uses more resources than C/C++, but that's the price for programmer productivity. At least programmers like me.

I am not sure what to think. C, C++, and C# have the same syntax. C and C++ are more cross platform by design. 

Also, it is a common mistake to think Ruby and such are not "real" programming languages. Your statements are pointing to the reason why Ruby and friends are used over other languages; they increase productivity. For "real programmers" read: [http://www.pbm.com/~lindahl/real.programmers.html](http://www.pbm.com/~lindahl/real.programmers.html)

---

### Post by pmasiar on 2008-05-30
> **peterdk said:**
> For me it is a very attractive step from a scripting language to a more "real" programming language,

looks like your "real" programming language is C++ with garbage collection. So you probably missing more advanced features of Ruby (and other "scripting" languages like Python and Perl) related to functional-like programming, with advanced list processing and stuff. Be careful not to become blub programmer. It is hard to judge correctly languages which are more advanced that your current skill level.

---

### Post by Lau_of_DK on 2008-05-30
In regards to the question that spawned it all: Why are people using C# in increasing measure? 

I think, unless you're a blub programmer (ie. one who embraces only  1 language for every challenge), your programming-languages are your tool-kit. You might love Haskell with all your heart, but I doubt you'll write a little utility script that snatches input from a few websites in it? Of course not, you'd go with something high-level that could get the job done in < 2 hours right?

C# targets fast and easy development, whether it be desktop apps or webservices, C# has tools to speed up development from start to finish, by sporting powerfull libraries and an easy syntax and a very forgiving editors. Sounds alot like Python? Would Python have had the rennaisance it has now, if C# had been ported 2-3 years ago?

If you're insistant upon not being a blub-programmer, C# will be the intelligent choice for a lot of your programming needs. Not everything, but a lot. 

Some might argue "Oh Lisp is mega flexible, I can bend it totally to my will and even design new languages within days" and thats great, if thats what you need. But does that help you if you get a call from Mark saying "I want to include a nice looking, easy to use, stable and fast FTP client to include in the next Ubuntu release - please have it ready by tomorrow." Then no. It probably doesn't :)

One last note: When you sit down with C# the first time, you're probably filled with skepsis as you're cautiously moving a little bit away from Visual C++ or something and you dislike the high-level feel. After an hour or so, you've already applied strong encryption, network algorithms and blazing GUIs all the while maintaining control even on socket level - All thanks to this powerful IDE, which discovers the language for you by the press of a "."  (intellisense)

/Lau

ps: Before you all kill me, I'm sitting in emacs hacking away at Lisp right now. But if I needed to built a good looking (read presentable) program that has an easily maintainable code, where converts from Windows wouldn't cringe and say "man thats ugly, now I know why they call it "free" software. I would use C# or something similar :)

---

### Post by slavik on 2008-05-30
> **Lau_of_DK said:**
> In regards to the question that spawned it all: Why are people using C# in increasing measure? 

I think, unless you're a blub programmer (ie. one who embraces only  1 language for every challenge), your programming-languages are your tool-kit. You might love Haskell with all your heart, but I doubt you'll write a little utility script that snatches input from a few websites in it? Of course not, you'd go with something high-level that could get the job done in < 2 hours right?

Obviously, you've never heard of Perl ...

> 
C# targets fast and easy development, whether it be desktop apps or webservices, C# has tools to speed up development from start to finish, by sporting powerfull libraries and an easy syntax and a very forgiving editors. Sounds alot like Python? Would Python have had the rennaisance it has now, if C# had been ported 2-3 years ago?

Umm, C has an even simpler syntax than C#. Python has nothing to do with C#. Microsoft positioned C# to compete with Java, not Python.

> 
If you're insistant upon not being a blub-programmer, C# will be the intelligent choice for a lot of your programming needs. Not everything, but a lot. 

Some might argue "Oh Lisp is mega flexible, I can bend it totally to my will and even design new languages within days" and thats great, if thats what you need. But does that help you if you get a call from Mark saying "I want to include a nice looking, easy to use, stable and fast FTP client to include in the next Ubuntu release - please have it ready by tomorrow." Then no. It probably doesn't :)

First off, Mark is not stupid. You cannot have ANY app ready in 1 day and say that it is good and won't break. But since you went there, Perl has modules that you can use to write your own FTP client as well as a server with TLS support.

Do you really want to argue about GTK/QT?

> 
One last note: When you sit down with C# the first time, you're probably filled with skepsis as you're cautiously moving a little bit away from Visual C++ or something and you dislike the high-level feel. After an hour or so, you've already applied strong encryption, network algorithms and blazing GUIs all the while maintaining control even on socket level - All thanks to this powerful IDE, which discovers the language for you by the press of a "."  (intellisense)

IDE has nothing to do with the language. I needed to write VBScripts (within Active Directory), even finding the BEST IDE for writing such scripts, VBScript was still unbearable.

> 
/Lau

ps: Before you all kill me, I'm sitting in emacs hacking away at Lisp right now. But if I needed to built a good looking (read presentable) program that has an easily maintainable code, where converts from Windows wouldn't cringe and say "man thats ugly, now I know why they call it "free" software. I would use C# or something similar :)

You hacking away at Lisp in emacs does not somehow give you any 'brownie points'

---

### Post by Lau_of_DK on 2008-05-30
> **slavik said:**
> 
You hacking away at Lisp in emacs does not somehow give you any 'brownie points'

I wasn't saying that C# was the only option, there are also moments in time where Python or Perl would be the language of choice.

I was merely trying to outline a few of the reason I myself switched to C#, way back when.

/Lau

---

### Post by xlinuks on 2008-05-30
This is also a _political_ issue. How do you think would novel (aca Miguel) feel since they developed Mono with the help from Microsoft and in the end there's no serious app created with mono? They would look dumb to say the least, thus they were the first ones (Novel) to push mono. For that purpose they bundled mono into gnome (Microsoft's way to do business and win) and there you go, sooner or later many fish will be caught.
People come from windows and since there .net has been pushed they are looking to .net on linux. Simple and powerful cause and the consequences will be as big, unless Sun finally manages to realease a high quality OpenJDK (with fast/bug-free graphics like in Sun's JDK) and a bug-free JavaFX which they promised to release free with professional tools, time will tell.

---

### Post by Wybiral on 2008-05-30
> **Lau_of_DK said:**
> Python? Would Python have had the rennaisance it has now, if C# had been ported 2-3 years ago?

Yes, because unlike C#, Python doesn't look like you just threw-up after eating a big nasty bowl of Java and C++.

Come to think of it, everything you said about C# could be said about Java, and Java is more portable ATM than C#, so by your argument... Why don't you use Java?

The truth is, for me, that syntax is very important when writing readable and reusable code, and C# just doesn't have it like Python does. It also lacks several of the amazing dynamic features present in languages like Python... So yes, imo, Python would have still existed even if C# had been ported.

---

### Post by Lau_of_DK on 2008-05-30
> **Wybiral said:**
> 
The truth is, for me, that syntax is very important when writing readable and reusable code, and C# just doesn't have it like Python does. It also lacks several of the amazing dynamic features present in languages like Python... So yes, imo, Python would have still existed even if C# had been ported.

You're right of course, and I don't doubt it for a second - I still choose Python over C# when on Linux for almost everything. Like I mentioned to Slavik I was just pointing out some of the things that make C# comfortable to work with, and even the right choice in certain situations.

I just re-read Slaviks reply, and I think on the point of the IDE, many Linux old-schoolers really need to have their eyes opened a bit. Consider your programming language like the cock-pit of a plane. Would any pilot say "I dont care about the cock-pit, I changes nothing, I just need the throttle and the rudder" ? Of course not. IDEs can contain Intellisense, Diagrams, helpful ways to present debugging information and on and on. A bad IDE is like a cock-pit missing the fuel-guage, altitude and wind-speed gauges - You can still fly without them of course, but having them making certain things a breeze. This is also one of the most common argument when we're dicussing high-level languages, compared to low-level languages. 

I think a smart move for everybody who doubts this, would be to install Visual Studio in a Virtual Box and give a whirl for a few weeks - You'll notice how quickly you pick up things if you commit to it.

Anyway, Im not expecting everybody to agree - My first post was merely to let you guys know, what things I was looking at when I made the jump from Visual C++ -> C# on Windows. 

/Lau

---

### Post by pmasiar on 2008-05-30
> **Lau_of_DK said:**
> Would Python have had the rennaisance it has now, if C# had been ported 2-3 years ago?

Absolutely. Python is 15 years old now, it makes it about 10 years older than C# :-) Python was popular way before C# was around, and will remain popular - even MSFT itself now suggests to use C# for libraries (for speed) but most of logic in dynamically typed languages like IronPython, RubyOnSteel, and other improvements they are making for .NET be more friendly for dynamically typed languages.

[www.paulgraham.com/hundred.html](www.paulgraham.com/hundred.html) suggests that Python-like language will be here 100 years from now, when both C# and Java will be as obsolete as Cobol is now (and why).

---

### Post by LaRoza on 2008-05-30
> **Lau_of_DK said:**
> Y

I just re-read Slaviks reply, and I think on the point of the IDE, many Linux old-schoolers really need to have their eyes opened a bit. Consider your programming language like the cock-pit of a plane. Would any pilot say "I dont care about the cock-pit, I changes nothing, I just need the throttle and the rudder" ? Of course not. IDEs can contain Intellisense, Diagrams, helpful ways to present debugging information and on and on. A bad IDE is like a cock-pit missing the fuel-guage, altitude and wind-speed gauges - You can still fly without them of course, but having them making certain things a breeze. This is also one of the most common argument when we're dicussing high-level languages, compared to low-level languages. 


The reason a cockpit on large planes is complicated, is because the plane is typicall too large and complex for a human to use alone. A language that is large and complex will need tool like VS.

---

### Post by Lau_of_DK on 2008-05-30
> **LaRoza said:**
> The reason a cockpit on large planes is complicated, is because the plane is typicall too large and complex for a human to use alone. A language that is large and complex will need tool like VS.

Yes it will, and even smaller languages will benefit from having a good well-rounded IDE. 

I think this will mark my exit-point from the discussion, because I've really said what I believe were C# strong-points. And if someone were to disagree, its either because they have not spent enough time in VS, or because we simple have a difference of opinion - Whatever the case may be, it's completely fine and we're no worse friends for that reason. Its a discussion about tools, not something worth wrecking "friendships" over :)

/Lau

---

### Post by Wybiral on 2008-05-30
> **Lau_of_DK said:**
>  ... 

Look, you preach about intellisense a lot... Is it seriously THAT big of a deal? Does it really improve your ability to code that much? Doesn't eclipse come close enough?

---

### Post by LaRoza on 2008-05-30
> **Lau_of_DK said:**
> Yes it will, and even smaller languages will benefit from having a good well-rounded IDE. 

I think this will mark my exit-point from the discussion, because I've really said what I believe were C# strong-points. And if someone were to disagree, its either because they have not spent enough time in VS, or because we simple have a difference of opinion - Whatever the case may be, it's completely fine and we're no worse friends for that reason. Its a discussion about tools, not something worth wrecking "friendships" over :)

/Lau
The point was that the hand holding and features of large IDE's is only really useful in large complex languages. The "well rounded IDE" for a language like Python or Perl will need less features.

---

### Post by Wybiral on 2008-05-30
> **LaRoza said:**
> The point was that the hand holding and features of large IDE's is only really useful in large complex languages. The "well rounded IDE" for a language like Python or Perl will need less features.

Exactly. In fact, it's not even possible with languages like Python and Lisp. Pythons objects can change anywhere they are passed to... Attributes added, altered, removed... They aren't the "set in stone, draw it out in UML first, encapsulate everything" objects from C++ and Java. And with things like macros in Lisp, code being conditionally created at runtime... How would a fancy IDE be of any possible use?

---

### Post by slavik on 2008-05-30
> **Wybiral said:**
> Exactly. In fact, it's not even possible with languages like Python and Lisp. Pythons objects can change anywhere they are passed to... Attributes added, altered, removed... They aren't the "set in stone, draw it out in UML first, encapsulate everything" objects from C++ and Java. And with things like macros in Lisp, code being conditionally created at runtime... How would a fancy IDE be of any possible use?

to add a point: the best IDE is your own brain. :)

---

### Post by pmasiar on 2008-05-30
Lau_of_DK, comparing IDE to a plane's cockpit cuts both ways. In [http://en.wikipedia.org/wiki/Paragliding](http://en.wikipedia.org/wiki/Paragliding) or [http://en.wikipedia.org/wiki/Hang_gliding](http://en.wikipedia.org/wiki/Hang_gliding) you can fly without it, and many people say it is more fun that way. 

In my experience, it takes many many months to become comfortable and productive with an IDE. Just try for fun become Eclipse expert. You love VS because you know it well and it makes you productive.  Vim/Emacs feels same for people who invested time to learn it.

---

### Post by nvteighen on 2008-05-30
> **pmasiar said:**
> Absolutely. Python is 15 years old now, it makes it about 10 years older than C# :-) Python was popular way before C# was around, and will remain popular - even MSFT itself now suggests to use C# for libraries (for speed) but most of logic in dynamically typed languages like IronPython, RubyOnSteel, and other improvements they are making for .NET be more friendly for dynamically typed languages.

[www.paulgraham.com/hundred.html](www.paulgraham.com/hundred.html) suggests that Python-like language will be here 100 years from now, when both C# and Java will be as obsolete as Cobol is now (and why).

Your argument speaks absolutely in favor of C, which is more than 30 years old! So Python is still just a child! ;) (kidding)

Seriously, there are fashion languages and languages that are the strong enough to stay for a long time. C# will dissappear when MS decides it's no longer a good business and replace it for something else, as they did with the old pre-.NET Visual Studio (which wasn't obsolete at all) and always do with all their products (e.g. remember MS Schedule in Office 97? MS Works Suite?)

I really don't like the idea of languages whose reason to exist is almost merely commercial and not properly scientific. If you create a language it should be for something there wasn't available before... Python has a scientific purpose to give people a new technology, but C# was created only to compete against Java and that's its aim.

---

### Post by pmasiar on 2008-05-30
> **nvteighen said:**
> Your argument speaks absolutely in favor of C, which is more than 30 years old! So Python is still just a child!

My argument was not that older language wins. Lau argued that if C# was released earlier (before 2001), Python would be less popular. But Python is much older than 2001, and also significantly different: C# has static typing, python has dynamic typing. It is not about age but features. Even adding smile does not help if you miss the real argumentation.

>  there are fashion languages and languages that are the strong enough to stay for a long time. ...C# was created only to compete against Java and that's its aim.

Yup, and this is exactly discussed in much deeper and more informed fashion in link I provided and you quoted. Did you read it? :-) It argues why 100 years from now, we will all program in Python.

---

### Post by nvteighen on 2008-05-30
> **pmasiar said:**
> My argument was not that older language wins. Lau argued that if C# was released earlier (before 2001), Python would be less popular. But Python is much older than 2001, and also significantly different: C# has static typing, python has dynamic typing. It is not about age but features. Even adding smile does not help if you miss the real argumentation.

I did understand what you said (as I think the second part of my post shows); maybe I didn't make the joke the right way as English is not my mother language. If so, excuse me.

But in "some" way, age does count. Not that older=better, but we surely agree you can't compare a 5 years old language like C# with a 17 years old like Python. Simply put: Python is more mature and more has been achieved in it than C#. I don't care for cuantity (number of programs developed on x language), but on how good technology has been developed with it. This is achieved after some time has passed and more people have used the language, I believe.

This is very similar to what happens to natural languages; no new-born language is able to produce quality litterature (either oral or written), but look how Romance languages took over Latin at the end. On the other hand, lots of languages end up dying without leaving any trace.

> Yup, and this is exactly discussed in much deeper and more informed fashion in link I provided and you quoted. Did you read it? :-) It argues why 100 years from now, we will all program in Python.

Of course I read it, but some time ago. A very interesting article which may help me if I decide to do some linguistic research on programming languages in the future. (It's something that attracts me a lot... and one of the reasons why I like to program: it makes me think on human language in general!)

---

### Post by pmasiar on 2008-05-30
OK maybe joke is on me :-)
> **nvteighen said:**
> but we surely agree you can't compare a 5 years old language like C# with a 17 years old like Python. Simply put: Python is more mature and more has been achieved in it than C#.

This is also not obvious. MSFT can marshal more resources, more developers for IDE, and more writers of documentation than free project (especially emerging project) and accomplish more in less time. It does not guarantee quality, but it does help.


> I don't care for cuantity (number of programs developed on x language)

I seriously tried to look up "cuantity" - it would be cool if such word (with your definition) existed, but alas - all I found is plain quantity :-)

> and one of the reasons why I like to program: it makes me think on human language in general!)

I was also fascinated by Larry Wall's comparison of natural and programming languages, but after experiencing Perl first-hand, I am more detached now: being trained anthropologist, even extremely smart, does not guarantee superior language design skills. Now I prefer language designed by Guido, who is **programmer** by education :-)

---

### Post by nvteighen on 2008-05-30
> **pmasiar said:**
> 
I seriously tried to look up "cuantity" - it would be cool if such word (with your definition) existed, but alas - all I found is plain quantity :-)

Thanks!

> 
I was also fascinated by Larry Wall's comparison of natural and programming languages, but after experiencing Perl first-hand, I am more detached now: being trained anthropologist, even extremely smart, does not guarantee superior language design skills. Now I prefer language designed by Guido, who is **programmer** by education :-)

Oh, you too? (Great!)

For example: All those "best programming practices in x language" threads in these (and other) forums are just plain pragmatical discussions! People asking that want to know what's the community standard... The same as when a foreigner learns your language and asks you how something is actually said by people (not just what the grammar book says).

Other thing I'm interested on (but far more technical) has to do with where does meaning rely in programming languages. Is it in the letters that form the word "while"? In the word "while" itself? In the statement "while(1)"?

I'm glad to see I'm not alone on these topics around here!

---

### Post by kragen on 2008-05-30
Well, on windows C# is being used more and more because its a really great language.

[LIST]
[*]Its far quicker to develop in C# than it is in C++.
[*]Because its managed a lot of common C++ issues are eliminated or even reduced.(its not a "programming skill" thing, no-one is perfect and mistakes are always made. Especially on a larger project with lots of contributers).
[*]Although C++ is quicker, in practice C# isn't much slower because of all the optimizations made by the .Net runtime. Of course if you want a really fast app, you need to use C++, but if development effort is a limited resource you really have to consider if putting the extra effort into optimizations in your C# could would give better performance gains.
[*]Like java and c++ its cross platform - windows developers can transfer their skills to mono and visa versa.
[/LIST]

In my opinion its the best managed language available at the moment, and when it comes to managed vs unmanaged, for GUI and front end development managed will usually come out on top.

The above is all based on windows development btw - the situation might be different with mono.
My guess is that even if the mono interpreter isnt up to the same standard as the .Net one at the moment, it will improve.

---

### Post by pmasiar on 2008-05-30
> **kragen said:**
> Although C++ is quicker, in practice C# isn't much slower because of all the optimizations made by the .Net runtime. Of course if you want a really fast app, you need to use C++, but if development effort is a limited resource you really have to consider if putting the extra effort into optimizations in your C# could would give better performance gains.


correct. And you can get even bigger gain if you make another step in that direction: do not waste efforts with statically typed language for GUI - dynamically typed language does it just fine, with 5-10 times increase of development speed. 

And if you need real speed, OOP overhead is too much price to pay and you need C or Fortran. C# is decent intermediate language for libraries where speed is important but not paramount. About 90% of productivity improvement (compared to C++) comes from memory management. But it's waste of time to code 90% of the code where speed is not important in C#, IMHO, if you can have almost identical results with 20% of the effort.

> In my opinion [C#] is the best managed language available at the moment, 

maybe between statically typed languages. But dynamic languages is where action is these days. Are you familiar with any? Take look at IronPython :-)

---

### Post by pmasiar on 2008-05-30
> **nvteighen said:**
> where does meaning rely in programming languages. Is it in the letters that form the word "while"? In the word "while" itself? In the statement "while(1)"?

That might be interesting discussion to have in a separate thread. Do you care to start it?

Because this is the main problem in transforming requirements into correct code: meaning of 'while' is in your mind only, and it is extremely hard to communicate exact meaning  (required by computer) to other humans, who are genetically "programmed" to guess, handle silent assumption, and make decisions based on fuzzy and inadequate information about the problem. 

The only computer capable of generate valid outcomes from inadequate information was Mike HOLMES, year 2076, and only in the book "Moon is the harsh mistress" :-) I finally read it recently, and it deserves the fame.

---

### Post by id1337x on 2008-06-01
I have experience with Visual Basic and C# but I avoid them now because they are MicroSoft and there isn't as much open source stuff for them. I like Perl because it is open source and practically all of its applications are too besides this it is 150% as popular as C#.

I don't think I'll ever be using C# a lot at least until I see lots of *gnome applications* with it.

---

### Post by scourge on 2008-06-01
> **pmasiar said:**
> correct. And you can get even bigger gain if you make another step in that direction: do not waste efforts with statically typed language for GUI - dynamically typed language does it just fine, with 5-10 times increase of development speed.

That's an exaggeration. The GUI toolkit has a lot more to do with GUI development speed than static or dynamic typing. To me Qt4 (C++) has been a lot simpler and faster to use than eg. wxPython ever was. It's because of Qt:s signals and slots mechanism, dynamic properties system, documentation, gui designer, etc.


> And if you need real speed, OOP overhead is too much price to pay and you need C or Fortran.

In C++ you can have an OOP design and still get "real speed". Just try to avoid dynamic allocation of objects, and don't go crazy with runtime polymorphism, and you're fine. Maybe it won't be exactly as fast as C, but it should be close enough.

---

### Post by pmasiar on 2008-06-01
> **scourge said:**
> That's an exaggeration. The GUI toolkit has a lot more to do with GUI development speed than static or dynamic typing.

I was talking about programming, not GUI development. GUI is complicated, IDE helps, and IDE has better chance to help with statically typed language. 

But why use static typing for rest of the programming, unless you have to, in a library, for speed?

---

### Post by slavik on 2008-06-01
> **pmasiar said:**
> I was talking about programming, not GUI development. GUI is complicated, IDE helps, and IDE has better chance to help with statically typed language. 

But why use static typing for rest of the programming, unless you have to, in a library, for speed?

I agree with the point of using dynamic languages, but the way you say it sounds like ALL apps can be written with a dynamically typed language. One thing you have to keep in mind is that the dynamic typing comes at the cost of checking assignment statements to ensure proper conversion which can be slow.

If you are writing a GUI front end to something like wget or for editing a file interactively (xorg.conf, smb.conf) then scripting languages are great since it is easy to interface them with a shell (Perl uses backticks, Python does os.popen(), etc.). It is also easy to process text using these languages (loading the said config files and etc). Believe me, I would not want to process text using C.

here is an example in Perl using regex and a loop to read a config file that looks like the following (there is a module for config files, but if you must have your own code ...):

```

#sample config file
Setting1 = "blah"
TIMEOUT=5

```

The code
```

# this is a crude example, so we die on error
open CONFIG_FILE, "/etc/myprog/config" or die$!;
%config = map { split /\s*=\s*/ }, <CONFIG_FILE>;
close CONFIG_FILE;

```

---

### Post by kragen on 2008-06-01
Hmm, well probably my biggest argument against dynamic typing is not the speed but the maintainability. If you look at a C# program you know exactly what an object can and cant do, whereas the same cant be said for dynamically typed languages like python. If you wrote the code or understand it well, your fine, but if your looking at a program for the first time that someone else wrote, these sorts of things have more of an effect.

In honesty I've not done much python development so I don't know if that would actually become an issue or not.

---

### Post by LaRoza on 2008-06-01
> **kragen said:**
> Hmm, well probably my biggest argument against dynamic typing is not the speed but the maintainability. If you look at a C# program you know exactly what an object can and cant do, whereas the same cant be said for dynamically typed languages like python. If you wrote the code or understand it well, your fine, but if your looking at a program for the first time that someone else wrote, these sorts of things have more of an effect.


It depends on what you are doing. In my experience, the strict typing leads to slow downs when wrapping your head around the types being used.

---

### Post by pmasiar on 2008-06-01
> **kragen said:**
> my biggest argument against dynamic typing is not the speed but the maintainability. If you look at a C# program you know exactly what an object can and cant do

In Python, we do not care about what type object belongs to, but what methods it understands. Duck typing: If it walks like a duck and quakes like a duck, for all we care it is a duck :-)

Having substantially less lines of code to maintain helps too. Most of my code (in Java) I spend wrestling with types: I have ListArray but only List can do sublist. Array has length but ListArrays has size (or other way?). 60+ types of file-like objects. I understand that this complexity helps compiler to wrestle little more performance  out of CPU, but who cares about me? It causes me immeasurable pain. :-)

And BTW if you have some unit tests, they should make sure that values you pass can do what they are asked to do. Instead of compile-time, you do it test-time. But you have the flexibility of dynamic typing development-time, where it counts.

---

### Post by slavik on 2008-06-01
the good thing about duck typing is that it is done for you, so you don't have to worry about converting things.

---

### Post by LaRoza on 2008-06-01
> **slavik said:**
> the good thing about duck typing is that it is done for you, so you don't have to worry about converting things.

Well, to a degree. You don't want things converted in weird ways.

---

### Post by days_of_ruin on 2008-06-01
> **LaRoza said:**
> Well, to a degree. You don't want things converted in weird ways.

Yeah like lua.IIRC you can add a number to a string if the string is a string of number like "22".

---

### Post by slavik on 2008-06-01
> **days_of_ruin said:**
> Yeah like lua.IIRC you can add a number to a string if the string is a string of number like "22".
Perl does the same ...

it is because the concatenation operator is not '+'

---

### Post by LaRoza on 2008-06-01
> **slavik said:**
> Perl does the same ...

it is because the concatenation operator is not '+'

ECMAScript does it also. It can cause some interesting bugs.

---

### Post by Wybiral on 2008-06-02
> **LaRoza said:**
> ECMAScript does it also. It can cause some interesting bugs.

Both of which are classic examples of a weakly typed system, which is just plain evil.

---

### Post by LaRoza on 2008-06-02
> **Wybiral said:**
> Both of which are classic examples of a weakly typed system, which is just plain evil.

C does it also, but if one is using C, one should accept the power to do things even if it wasn't the intent.

---

### Post by kragen on 2008-06-02
> **pmasiar said:**
> In Python, we do not care about what type object belongs to, but what methods it understands. Duck typing: If it walks like a duck and quakes like a duck, for all we care it is a duck :-)

But can you tell if something walks like a duck and quacks like a duck quickly and easily just by looking at the code?

The thing about dynamic typing is that any thing could be any object at any time. In smaller applications where things are easier to keep track of, and this definitely works in your favor (from a productivity standpoint)

In larger projects however, where its could be nearly impossible for one person to understand the whole code-base, I can see situations where an object supports some methods and properties some of the time, and other properties and methods the rest of the time.

In fact I did some JavaScript debugging recently and had massive problems because an object didn't support a method that it was supposed to (but the object wasn't null). I spent ages and ages trying to work out when and where this object was supposed to gain this method, (It actually turned out to be a simple 404 error that was hidden because of some weird quirks...)

My point is that in strongly typed languages you know that an object is either null, or supports all of the methods and properties defined on its interface as well as exactly what format the arguments are in. If there is an unexpected exception, its unarguably because the code isn't properly implemented, not because the inputs are in a slightly different format.

I suppose really I do see strongly typing as a restriction, but its a good thing in lots of situations - it reduces the need to spend time documenting things, and prevents certain mistakes and bugs.

IMO the future is in the middle ground - Python is brilliant for smaller projects where its easier to keep track of everything and you wont run into these sorts of problems. 
If documentation was effortless and easily accessible (and developers actually did it!), then a fair few of these problems would go away.

---

### Post by Wybiral on 2008-06-02
> **kragen said:**
> Python is brilliant for smaller projects where its easier to keep track of everything and you wont run into these sorts of problems.

Yes, small projects only... Like NASA projects, YouTube, Viacom websites, Reddit, and... You know... Small stuff.

You don't need compile-time safety when you have test-time safety. Not only that, but unit tests catch WAY more than a simple type check being run by a compiler, they discover bugs in logic and common use cases. Compilers aren't going to find those kinds of errors, which are way more common than type-related errors. So no, this issue isn't nearly as big as you're imagining it to be.

---

### Post by Wybiral on 2008-06-02
> **kragen said:**
> My point is that in strongly typed languages you know that an object is either null, or supports all of the methods and properties defined on its interface as well as exactly what format the arguments are in.

btw, Python IS strongly typed. It's just not statically typed :)

C/C++ are both capable of being weakly typed since you can do dirty things with pointer casts and stuff. There is no type casting in Python, when you say int(obj) you're really saying obj.__int__() and returning a new object as defined by the __int__ method.

---

### Post by kragen on 2008-06-02
> **Wybiral said:**
> Yes, small projects only... Like NASA projects, YouTube, Viacom websites, Reddit, and... You know... Small stuff.

Just because they use it doesn't mean they never run into any issues with it :)

> You don't need compile-time safety when you have test-time safety. Not only that, but unit tests catch WAY more than a simple type check being run by a compiler, they discover bugs in logic and common use cases.

True, but this doesn't address the documentation issues (although example code does help), plus unit testing can be even more time consuming than writing the code in the first place.
Besides, unit tests can have errors too!

Sorry, but I'm sticking to my guns on this one. In an ideal world yes, everyone would write comprehensive unit tests and documentation, code would be well commented and people wouldn't make dirty cheap hacks to fix bugs, but in the real world all of those things happen, and they make maintaining code a nightmare.
C# is designed with maintenance and robustness in mind. Although at times static typing can feel like a bit of a chore, in the long run it really does pay off.

---

### Post by pmasiar on 2008-06-02
> **kragen said:**
> Sorry, but I'm sticking to my guns on this one. 

Of course nobody will force you to change your habits and opinions. But for the education of the reader, let me link to one rather smart and well-known programmer [Bruce Eckel](http://en.wikipedia.org/wiki/Bruce_Eckel), author of Thinking in Java (which has 4 editions - not many computer books get that many, so he is at least above average). Bruce compares [Strong Typing vs. Strong Testing](http://www.mindview.net/WebLog/log-0025)

"(A more accurate title would be "Static Checking vs. Strong Testing"). "
"To claim that the strong, static type checking constraints in C++, Java, or C# will prevent you from writing broken programs is clearly an illusion"

Again, nobody wants to change your habits. It is entirely to better serve readers - by providing info by real, proven experts. Heed or ignore any advice at your will.

---

### Post by LaRoza on 2008-06-02
> **kragen said:**
> Just because they use it doesn't mean they never run into any issues with it :)

C# is designed with maintenance and robustness in mind. Although at times static typing can feel like a bit of a chore, in the long run it really does pay off.

True. Although their use of Lisp and Python (among others) has led to great advancements and flexibility. Also, Ada, the ultimate in strict static typing has lead to the destruction of rather expensive equipment.

There is no compile time program checker ;)

C# is designed to compete with Java after MS failed at Java.

---

### Post by Wybiral on 2008-06-03
> **kragen said:**
> Just because they use it doesn't mean they never run into any issues with it :)

The biggest problems YouTube ran into were with scalability. Their userbase was growing too big, too fast. The only way to keep up with being on the edge of a scalability nightmare was to develop really quickly... This kind of rapid development really is only capable with a dynamic language like Python. Here, watch [this]("www.youtube.com/watch?v=ZW5_eEKEC28") and read [this]("http://www.paulgraham.com/avg.html"). This "strict type safety" nonsense is an illusion.

To keep up with your competition and your growing userbase, you're going to have to be able to develop FAST. The statically typed, object oriented bureaucracy and overbearing inheritance schemes for getting around the lack of dynamicness that you're probably used to isn't going to help you at all, it's going to hold you back and get big, unmaintainable, and slow to develop.

Maybe you should start writing software for the elderly, so your users will be the right age when you finally get to release it :)

> **kragen said:**
> 
True, but this doesn't address the documentation issues (although example code does help), plus unit testing can be even more time consuming than writing the code in the first place.

See, you're thinking about this from the perspective of someone who's never really experienced a good dynamic language. What extra documentation do you get from having types? The ability to know what types a function/method takes/gives, right? That's absolutely useless information in a dynamic language, and in fact would hinder your generic flexibility.

If I say "a + b", I'm not confused by the lack of types... All I need to know is that those objects are addable with each-other, that's it. That's all the documentation you need wrt types.

You're not exempt from unit testing just because you use static types, lol. And even if your tests take a while to develop, it's worth it, and it's probably still faster than developing in statically typed languages, AND you have added logic/use-case checking to help verify that your program isn't going to segfault the second a user does something (of which simple type-checking alone will not do).

> **kragen said:**
> Although at times static typing can feel like a bit of a chore, in the long run it really does pay off.

No, it doesn't.

---

### Post by nvteighen on 2008-06-03
> **pmasiar said:**
> 
"(A more accurate title would be "Static Checking vs. Strong Testing"). "
"To claim that the strong, static type checking constraints in C++, Java, or C# will prevent you from writing broken programs is clearly an illusion"

Agree:

The only thing that will prevent you from writing broken programs is trying to do your own best effort.

I'm much more used to static typing; I just feel much comfortable with it... But my programs are still crap with or without static typing!  (hey, it's true... no matter how much I've improved! :p).

---

### Post by pmasiar on 2008-06-03
> **kragen said:**
> plus unit testing can be even more time consuming than writing the code in the first place.

1) With rapid/agile development using dynamically typed language, you save enough time to write the tests

2) You have to write your tests anyway, and writing tests in statically typed language will take that much more time

3) Without tests, you cannot refactor, and how you will know that your program works, after any minor change? Running tests is the only reasonable option - the option which really saves you time in the long run, as you claimed to care.

Read [http://en.wikipedia.org/wiki/Test_driven_development](http://en.wikipedia.org/wiki/Test_driven_development) and be enlightened :-)

---

### Post by slavik on 2008-06-03
> **pmasiar said:**
> 1) With rapid/agile development using dynamically typed language, you save enough time to write the tests

2) You have to write your tests anyway, and writing tests in statically typed language will take that much more time

3) Without tests, you cannot refactor, and how you will know that your program works, after any minor change? Running tests is the only reasonable option - the option which really saves you time in the long run, as you claimed to care.

Read [http://en.wikipedia.org/wiki/Test_driven_development](http://en.wikipedia.org/wiki/Test_driven_development) and be enlightened :-)
static typing allows you to cut down on many errors.

Ada is a strictly typed (static) language. The Ada compiler can catch many errors at compile time that C programs would reveal during run-time.

All air traffic control software as well as airplane control software is written in Ada.

---

### Post by Wybiral on 2008-06-03
> **slavik said:**
> static typing allows you to cut down on many errors.

Ada is a strictly typed (static) language. The Ada compiler can catch many errors at compile time that C programs would reveal during run-time.

All air traffic control software as well as airplane control software is written in Ada.

Everything that the compilers can do, a well-written automated test system could do as well... Except that the test phase can simulate real-world uses for things and give deeper insight into the trouble stops and help find more than just type safety issues (which aren't nearly as common as logic problems).

---

### Post by Peyton on 2008-06-03
> **pmasiar said:**
> Of course nobody will force you to change your habits and opinions. But for the education of the reader, let me link to one rather smart and well-known programmer [Bruce Eckel](http://en.wikipedia.org/wiki/Bruce_Eckel), author of Thinking in Java (which has 4 editions - not many computer books get that many, so he is at least above average). Bruce compares [Strong Typing vs. Strong Testing](http://www.mindview.net/WebLog/log-0025).

Just don't make the mistake of thinking that your Eckel is "against" static typing:
> In general, my attitude is that static typing is desirable as long as it doesn't cost you too much.

But, no, of course static typing isn't going to guard against every error.

---

### Post by pmasiar on 2008-06-03
> **Peyton said:**
>  your Eckel 

is as mine as yours. I think his books are excellent, that's all. I use his authority to support my arguments against other random forum posters who cannot even be bothered to support own arguments by anything but own bias, that's all.

---

### Post by LaRoza on 2008-06-03
> **pmasiar said:**
> is as mine as yours. I think his books are excellent, that's all. I use his authority to support my arguments against other random forum posters who cannot even be bothered to support own arguments by anything but own bias, that's all.

Professor Thomas D. Fahey agrees that static typing is extremely essential to developing bug free programs. Dr. Judd Biasiotto also feels that duck typing is inefficient and error prone, and should be avoided. Research by Professor Verkhoshansky and Dr. Siff also confirms the superiority of strong static typing over any other scheme.

My references can beat your references up!

(Thread is already long and boring, so I'd thought I'd spice it up with some fake flamebait, maybe some will start citing these guys for other arguments)

---

### Post by Wybiral on 2008-06-03
> **LaRoza said:**
> (Thread is already long and boring, so I'd thought I'd spice it up with some fake flamebait, maybe some will start citing these guys for other arguments)

lmao

---

### Post by kragen on 2008-06-03
> **Wybiral said:**
> Everything that the compilers can do, a well-written automated test system could do as well... Except that the test phase can simulate real-world uses for things and give deeper insight into the trouble stops and help find more than just type safety issues (which aren't nearly as common as logic problems).

Anything which dynamically typed test system can do, a statically typed system can do as well. In fact I challenge you to prove otherwise :)

Besides - There is nothing stopping you writing your code base in a statically typed language and your unit tests in a dynamically typed language. In fact thats probably a really good idea - because unit tests are by nature small isolated chunks of functionality, the code is easily manageable.

Because of the very nature of dynamically typed languages its impossible to test every possible test case. No matter what you test, someone using your code will be able to send it an object which you haven't tried. Let me give you an example...

Suppose you have a method Norm(a, b):

```

def Norm(a, b):
    return (a + b) * (a + b)

```

Now suppose someone has an object where a + b != b + a, if you change your code to read

```

def Norm(b, a):
    return (a + b) * (a + b)

```

Unless your test case included objects where a + b != b + a, the definition of your norm has now changed without you realising it.

My point is that a lot of errors are not at all obvious, and by not imposing any restrictions at all on what objects you will and wont accept your opening your self up to a whole host of un-obvious errors which could be missed even in unit testing. This is a relatively simple example, imagine the sheer number of test cases you would have to do to test a more complex system. (More test cases == more work, remember that unit testing is way more time consuming then the actual coding in the first place)

On the flip side, with static typing you have the ability to test close enough to every single test case. If you only need a method which works out the norm of a vector or a matrix, why goto the effort of doing test cases for more complex objects? By restricting what the consumers of your library can and cant do, you mitigate the risk of them successfully managing to do things for which it wasn't designed while reducing the number of tests you need to do at the same time.

I'll give you another example... Suppose you change your norm method to use a slightly different calculation:

```

def Norm(a, b):
    return (a + b) ** 2

```
[SIZE="1"]EDIT: Fixed the code so it used the python symbol for power - I just learnt what it was! :)[/SIZE]

The methods that the object (a + b) must support have now completely changed, and although to you it might be obvious that anything implementing * must implement ^ (int), but someone else might not have bothered and now once again your code is broken without warning.

I completely agree - a lot of the time dynamic typing increases productivity no end, but for you application to be truly robust at some point you need to be able to define a contract between you and your users. Testing lots of use cases simply isn't good enough - you need to test all of them.

IMO C# and python are opposite ends of the spectrum - C# is too strong with its typing, and python doesn't allow you to be strong enough. In an ideal world I'd have python with the ability to statically type my interfaces when and where I want.

---

### Post by LaRoza on 2008-06-03
> **kragen said:**
> Anything which dynamically typed test system can do, a statically typed system can do as well. In fact I challenge you to prove otherwise :)

Besides - There is nothing stopping you writing your code base in a statically typed language and your unit tests in a dynamically typed language. In fact thats probably a really good idea - because unit tests are by nature small isolated chunks of functionality, the code is easily manageable.

Well, yeah. No one is saying it isn't possible.

Exactly, Python (as commonly used) is written in C, and the ctypes are available for use, and it is easy to write modules in C for it. 

Python has all the hard things done behind the scenes (like Perl, Ruby, etc)

It would be nice if you could point out some studies to support your views.

Like this: [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

---

### Post by Wybiral on 2008-06-03
> **kragen said:**
>  ... 

Unit tests don't have to check every combination of argument types for sanity, they only have to make sure that the proper usage works. If you're that paranoid, do you do lots of checks everywhere for value errors? You don't want your users sending bad values to a function and blowing it up.

Doesn't C# have pointers? Can you not cast something to a 'void*' and accidentally cast to to something else? Your compiler might warn you a bit, but it's still going to allow that code. The only way to be sure in situations where you're doing that is to do unit tests.

This idea that "I'm writing this library, that means I should babysit for my users and lock everything up" is nonsense. You're willing to waste your time developing some massive, non-reusable, overly restricted, unreadable piece of crap just because your users might do something stupid? Your users will ALWAYS find something stupid to do. How about you spend that time and write some good documentation instead! That way you have a flexible, well documented system (which is a wiser use of your wasted time).

And when you use a language that's closer to pseudocode, you get to spend even less time on documentation because your code makes more sense, you aren't building this unnecessary framework just to solve problems imposed by using an overly restrictive language.

BTW, unit testing is fast and easy with an interactive language. Python and Lisp have a REPL, you can interactively feed tests to it and figure out where they went right and wrong as you go along by introspectively poking around in the code. You don't have this AT ALL with compiled languages, the best you usually have are some primitive debugging tools that give you some friendly addresses and assembly code to look at.

---

### Post by kragen on 2008-06-03
Yeah, the more I learn about python the more impressed I am with how its put together - if you need something to be faster, simply find the bottleneck and put some of it into a faster language. I was reading an article on improving python performance:

[http://wiki.python.org/moin/PythonSpeed/PerformanceTips](http://wiki.python.org/moin/PythonSpeed/PerformanceTips)

Unless you really need to make something fast I cant really see why anyone would have an issue with pythons speed.

I have a couple of questions...

1) How easy is it to call python code from other languages? (say c++)
2) Also, I've heard that python isn't great for multi-threading... is this a fundamental thing, or is it just that the modules for threading aren't as feature rich as other languages?

---

### Post by LaRoza on 2008-06-03
> **kragen said:**
> 
1) How easy is it to call python code from other languages? (say c++)
2) Also, I've heard that python isn't great for multi-threading... is this a fundamental thing, or is it just that the modules for threading aren't as feature rich as other languages?

0. It is usually done the other way around
1. CPython uses a GIL which prevents many problems but also restricts some threading uses.

---

### Post by Wybiral on 2008-06-03
> **kragen said:**
> 1) How easy is it to call python code from other languages? (say c++)
2) Also, I've heard that python isn't great for multi-threading... is this a fundamental thing, or is it just that the modules for threading aren't as feature rich as other languages?

Using the C/Python API it's pretty easy (there's practically an "exec" function that you can send Python code to). But it makes more sense to call C from Python.

Python is stuck in a GIL. So true multithreading isn't possible (multi processing is an option though). This, however, is only a problem with the CPython implementation, Jython has true multithreading support. CPython has threads, but they wont make use of multiple processors, they're just good when you want to interleave code.

---

### Post by kragen on 2008-06-03
> Doesn't C# have pointers? Can you not cast something to a 'void*' and accidentally cast to to something else?

I think it does technically have pointers, but no-one ever uses them (and I mean ever...)

Yes users can send bad values to your functions, but generally speaking you know exactly what they are and you can test for them (usually things like nulls).

> This idea that "I'm writing this library, that means I should babysit for my users and lock everything up" is nonsense.

If re-use is important to you then dynamic languages are great, if reliability is important to you then they're not - sure you can make your code reliable by creating loads of use cases, but with statically typed languages you have the ability to say "only give me vectors of ints", and you save yourself all the hassle.

Besides... what if reliability isn't the issue... what if security is? When people are willing to goto great lengths to find those specific cases where your code doesn't behave as expected, its a massive time-saver to know that the object your looking at absolutely has to be the one you expect.

---

### Post by Wybiral on 2008-06-03
> **kragen said:**
> but with statically typed languages you have the ability to say "only give me vectors of ints", and you save yourself all the hassle.

Don't be fooled into thinking you don't have this power in dynamic languages too. In Python, you have a few tools to help you such as isinstance and hasattr that allow you to check types and attributes when needed. You can argue "yeah, but it doesn't happen at compile time" but neither do your value checks and they seem to work out, right?

---

### Post by pmasiar on 2008-06-03
> **LaRoza said:**
> Professor Thomas D. Fahey ...Verkhoshansky 

but they don't have wikipedia pages and **blogs**. Blog lets reader to do additional research, find any relevance to own situation, and form own opinion. Personal bias of random posted has no context, so I cannot form informed opinion - I can either trust or not. I would not trust posting from anonymous forum dweller - I even suspect your experts exists only on your hard disk, and I e-know you for more than a year :-)

So I still prefer bias of a known **existing** expert over nonexisting one :-)

---

### Post by LaRoza on 2008-06-03
> **pmasiar said:**
> but they don't have wikipedia pages and **blogs**. Blog lets reader to do additional research, find any relevance to own situation, and form own opinion. Personal bias of random posted has no context, so I cannot form informed opinion - I can either trust or not. I would not trust posting from anonymous forum dweller - I even suspect your experts exists only on your hard disk, and I e-know you for more than a year :-)

So I still prefer bias of a known **existing** expert over nonexisting one :-)

They are all real people and real experts. This thread is really long (and off topic, but that is nothing new) and I thought I'd fool around for a while.

In case anyone is wondering, they are all doctors and trainers and are experts in physical strength development. Nothing to do with computers.

---

### Post by Peyton on 2008-06-04
> **Wybiral said:**
> Doesn't C# have pointers? Can you not cast something to a 'void*' and accidentally cast to to something else? Your compiler might warn you a bit, but it's still going to allow that code.
It supports pointers, but you have to mark the surrounding type, method or block of code as "unsafe" and compile the assembly with the /unsafe option.

Pointers aren't an integral part of your average program. The need for them comes when you need to interact with outside code.

---

### Post by pmasiar on 2008-06-04
> **LaRoza said:**
> They are all real people and real experts.

This disclosed again that you are just a bot. :-)

Humans would be able to infer from the context that relevant experts for the question being discussed are computer/programming experts, and not just random experts.

You may want to report this incident to the borg collective that launched you, and ask to improve your AI inferencing algorithms. You need better semantic analyzers to improve your skill for pretending you are young human, or mistakes like this will break your cover again :-)

---

### Post by Can+~ on 2008-06-04
There to kinds of experts:

The real ones. And the ones that fox news put on tv.

---

### Post by LaRoza on 2008-06-04
> **pmasiar said:**
> This disclosed again that you are just a bot. :-)

Humans would be able to infer from the context that relevant experts for the question being discussed are computer/programming experts, and not just random experts.

You may want to report this incident to the borg collective that launched you, and ask to improve your AI inferencing algorithms. You need better semantic analyzers to improve your skill for pretending you are young human, or mistakes like this will break your cover again :-)

Resistance in futile.

Humans infer all sorts of things, and it leads to miscommunication. If you want to have computer science experts why didn't you say so? (Don't answer that...)

I am the collective. There is no cover, resistance is futile, you will be assimilated (except for Java programmers, I don't want them)

I originally clicked on this thread now for saying "This thread has had more views and two of the stickies together".

---

### Post by nvteighen on 2008-06-04
> **LaRoza said:**
> 
I am the collective. There is no cover, ressistance is futile, you will be assimilated (except for Java programmers, I don't want them).

And except also for a crappy C newb like me. You may run into undefined behaivor.

But maybe I'll protect myself getting a cup of Java... coffee!

(Excuse me: I'm stupid today)

---

### Post by pmasiar on 2008-06-04
> **LaRoza said:**
> except for Java programmers, I don't want them

Java programmers are already assimilated in the J2EE collective :-)

---

