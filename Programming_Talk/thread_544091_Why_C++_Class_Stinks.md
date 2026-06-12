---
title: "Why C++ Class Stinks"
date: 2007-09-05
forum: Programming Talk
---

### Post by TreeFinger on 2007-09-05
I am taking an introduction course to C++ at college this year. I am excited about it but some things about it make me mad.

In class all developing happens on Visual Studio 2005. I hate this program. Windows just sucks for developing in my opinion. The whole reason it sucks is because of Notepad. I love the text editor in Ubuntu. It is so nice for anything you are developing. In class I wrote a few programs using notepad and compiling with the command line compiler included with VS 2005. Why don't they make notepad nice like the Text Editor in Ubuntu?? During class I am pretty much forced into using VS 2005 since you can't install any program you want for developing. 

Oh, well. While I am at home I enjoy programming much more because I can do it on Ubuntu :)

Some talk on open source came up in a few of my classes. The response I heard from some of my classmates made me wonder if they are not all Bill Gates Drones. They scoff at the fact that programs are free. For some reason they believe this makes them insecure. Is this true? I am all about open source ever since installing Ubuntu. Hopefully, one day, I can contribute to the wonderful community.

---

### Post by the_darkside_986 on 2007-09-05
Well, free and **open** software is secure because more eyes are seeing the code and spotting errors, whereas closed-source software, even if it is freeware, may contain unseen security holes that are only found by the developers or by ethical hackers through hacking means.

I took C++ when I got to college as well, but I learned C++ on my own using Dev-Cpp. If you have a jump drive, then perhaps you could install Dev-Cpp on the jump drive and run it at school. Dev-Cpp is a nice IDE that contains gcc, or I should say, the Windows port of gcc, the GNU C/C++ compiler. 

I agree that gedit is an awesome IDE as well as general purpose text editor. Another good IDE for Ubuntu is Anjuta.  Some people say bad things about it but I like it a lot. You can get it from the repos using Add/Remove programs in the Applications menu, and it is in the programming category.

---

### Post by TreeFinger on 2007-09-05
In my one class Open Source software came up because the teacher was talking about how France and another country in Europe banned Microsoft products from being used in government offices, etc. She says now they are having all these security problems because their software is open source and they are regretting doing it.

Is there any truth to what she told us?

---

### Post by RavenndudE on 2007-09-05
> **the_darkside_986 said:**
> 

I took C++ when I got to college as well, but I learned C++ on my own using Dev-Cpp. If you have a jump drive, then perhaps you could install Dev-Cpp on the jump drive and run it at school. Dev-Cpp is a nice IDE that contains gcc, or I should say, the Windows port of gcc, the GNU C/C++ compiler. 


That's what I did in my freshman year of college, now (a senior) I just ssh into one of the computer science department's linux machines and use vim.

---

### Post by pmasiar on 2007-09-05
For editing, use SciTE: same small little smart editor on Windows and Linux.

Unsecure free software is nonsense: many people read the code and many fixes go in **before** any exploits are found. With MSFT, fix goes in **after** exploit. 

Also, there was comparison of bugs in RedHat vs. Windows for IIRC year 2005. **All RH packages** had about twice number of errors than Windows OS, and clueless journos made big deal out of it. But MSFT included Windows OS bugs only, while RH included complete distribution: Linux kernel, and couple of web servers, databases, dozens of compilers, 2 or 3 office suites, dozen email clients, and **thousands** of applications. So rate of error per program was **substantially** less than Windows - and bugs were fixed faster.

And it is obvious why it is so: MSFT employs some 30-50 K people, maybe half are developers. Free software has many times more than that amount of developers. And more is joining every day. Especially in developing countries, where recent "improvements" of "genuine advantage" made free software so more interesting.

Only in USA paying $400 for software can save you money on training. If your people make $3 a day, sending $400 hard-earned money to USA makes very little sense: better is to fund local Linux user group and support **local** companies.

---

### Post by ryno519 on 2007-09-05
Why are you writing your code in notepad? You have VS2005! It blows away any IDE you'll currently find on GNU/Linux. Of course, if they're making you write this code in notepad then... ouch.

You could always download Code::Blocks or another Windows C++ IDE. It should let you choose which compiler to use, mingw or Visual Studio 2005.

As for which is more secure, closed or open source code... experience tells me it makes little difference. The developers make it secure, not the distribution method.

---

### Post by pmasiar on 2007-09-05
> **ryno519 said:**
> As for which is more secure, closed or open source code... experience tells me it makes little difference. The developers make it secure, not the distribution method.

Open source/free software is **development** method, distribution is completely accidental.

And of course fixing bug in code without source is... hard, but fixing it when source is available is fun! Read Halloween Documents, even MSFT developer was excited how easy was to look at sources, fix the bug he found, and post the patch upstream!

---

### Post by ryno519 on 2007-09-06
> **pmasiar said:**
> Open source/free software is **development** method, distribution is completely accidental.

And of course fixing bug in code without source is... hard, but fixing it when source is available is fun! Read Halloween Documents, even MSFT developer was excited how easy was to look at sources, fix the bug he found, and post the patch upstream!

It's both a development and distribution method, but that's not the point, really. Although the distribution method isn't accidental in many cases, but mandated (see GPL).

Now, I'm not really one to call fixing bugs very fun. Designing the structure of a program, coding and optimizing it and finally, using it for the first time are pretty fun. Maintenance is by far the part I hate most, so I'll have to take your word for it that some people think it's fun. :P

And as I said before, distribution/development method is not the main factor in the security of an application. I'd say (useless guestimate statistic warning!) 70% is the developers expertise, 20% is the development process (rushed release dates, lack of management, too much micro-management, etc) and the final 10% is the development model itself, with both open source and closed source having their pros and cons.

---

### Post by andyrobo60 on 2007-09-06
> **TreeFinger said:**
> Some talk on open source came up in a few of my classes. The response I heard from some of my classmates made me wonder if they are not all Bill Gates Drones. They scoff at the fact that programs are free. For some reason they believe this makes them insecure. Is this true? I am all about open source ever since installing Ubuntu. Hopefully, one day, I can contribute to the wonderful community.

I think this is because in the windows world everyone is out to make money. So when people who use windows all the time and don't know much or anything about open source see a program thats free they think it is crap or full of adware/spyware. 

I must admit that when I see something free for windows that is not open source the first thing I think is "why don't they make it open source, what are they hiding."

---

### Post by cwaldbieser on 2007-09-06
> **ryno519 said:**
> Why are you writing your code in notepad? You have VS2005! It blows away any IDE you'll currently find on GNU/Linux. Of course, if they're making you write this code in notepad then... ouch.

Not to knock VS2005, but sometimes if you are making small changes to a program, waiting for Visual Studio to open is painful on some less powerful machines.  Editors like SciTE and Notepad++ that have useful editor features but don't require as many system resources are much more useful in this regard.

---

### Post by ryno519 on 2007-09-06
> **cwaldbieser said:**
> Not to knock VS2005, but sometimes if you are making small changes to a program, waiting for Visual Studio to open is painful on some less powerful machines.  Editors like SciTE and Notepad++ that have useful editor features but don't require as many system resources are much more useful in this regard.

Well then you have to compile your changes anyway, so I think the time saved might be negligible.

---

### Post by slavik on 2007-09-06
another thing: open source code is peer reviewed and if one developer will try to stick in a backdoor somewhere and someone spots it, that person will never be seen in OSS again. where as in proprietary ... dunno, wrist slap maybe?

---

### Post by samjh on 2007-09-06
Depends on the severity of the backdoor, Slavik.

If it is criminal, jail-terms are possible (employee or contractor used backdoor for industrial espionage, fraud, or worse).  Often it is either a formal written warning (for jokes), immediate dismissal (if it is not seriously damaging but was a significant hindrance to development or repeated negligence), or in some non-criminal but very serious cases, civil action (ie. company sues employee or contractor if the backdoor caused loss of sales, loss of reputation, etc.)

---

### Post by xtacocorex on 2007-09-06
> **TreeFinger said:**
> I am taking an introduction course to C++ at college this year. I am excited about it but some things about it make me mad.
Here's the thing that pisses me off about people who are in your position, they don't understand anything: programming is programming no matter what platform it's on.  Complaining about using Visual Studio and trying to use other methods for development for the class won't make you a good programmer.  Who cares if Visual Studio sucks?  You're paying for the class, you might as well get the most out of it you can, am I wrong?

Focus on what the methodology behind the syntax and learn why things are done certain ways.  Learn and understand the logic; once this is done, you'll probably have gotten more out of the class then originally intended **and** you'll arm yourself with the background knowledge to learn any programming language because at this point, you'll only need to understand syntax and maybe some special quirks the language has to offer.

---

### Post by LaRoza on 2007-09-06
For the OP, you can use many good editors, even if you can't install on the school computers.

Use portable apps, even Dev-C++ has a portable version.

* [http://portableapps.com/](http://portableapps.com/)

* [https://sourceforge.net/project/showfiles.php?group_id=190331](https://sourceforge.net/project/showfiles.php?group_id=190331)

---

### Post by slavik on 2007-09-06
> **xtacocorex said:**
> Here's the thing that pisses me off about people who are in your position, they don't understand anything: programming is programming no matter what platform it's on.  Complaining about using Visual Studio and trying to use other methods for development for the class won't make you a good programmer.  Who cares if Visual Studio sucks?  You're paying for the class, you might as well get the most out of it you can, am I wrong?

Focus on what the methodology behind the syntax and learn why things are done certain ways.  Learn and understand the logic; once this is done, you'll probably have gotten more out of the class then originally intended **and** you'll arm yourself with the background knowledge to learn any programming language because at this point, you'll only need to understand syntax and maybe some special quirks the language has to offer.

how can he focus on fundamentals when he is not in an environment that makes him happy?

---

### Post by Lord Illidan on 2007-09-06
Use notepad++, it is a very good editor, matches and surpasses Gedit in my opinion.

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> And as I said before, distribution/development method is not the main factor in the security of an application. 

Proprietary closed-source code can hide any backdoors or unsecure code and you will never know it untill some cracker owns your computer. Open source is peer-reviewed, and it is extremely hard to sneak something in. So I cannot see how I can trust closed-source code as much as open source.

And it is not only me. Ie China government does not trust Windows enough to rely on it: they correctly assume that if CIA asked nicely MSFT "just to add this little custom backdoor", MSFT would have hard time not to comply.

It already happened, CIA blown some Russian gas fields operations.

---

### Post by ryno519 on 2007-09-06
> **slavik said:**
> how can he focus on fundamentals when he is not in an environment that makes him happy?

Because code is code regardless of the platform and if he wants to be a programmer, he'll have to learn how to code in platforms he may not prefer using because chances are he'll spend 100% of his career coding in Windows.

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> because chances are he'll spend 100% of his career coding in Windows.

I agree with you that you have to use the platfom boss told you -- but 100% career on windows? Is OP a slave who cannot change jobs to get to work for some smart company instead? Are we all doomed to switch to Vista, and Linux development was abandoned? I certainly did not get the memo, and most of our servers run Linux. :-)

---

### Post by ryno519 on 2007-09-06
> **pmasiar said:**
> I agree with you that you have to use the platfom boss told you -- but 100% career on windows? Is OP a slave who cannot change jobs to get to work for some smart company instead? Are we all doomed to switch to Vista, and Linux development was abandoned? I certainly did not get the memo, and most of our servers run Linux. :-)

Most of the jobs in the field are for Windows development and most developers do spend all or most of their career developing applications for the Windows platform. Not sure why he would want to change jobs though, .net developers are raking it in right now. ;)

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> Most of the jobs in the field are for Windows development 

unsupported claims again. There is Java, and there is Linux. YouTube is **not** a .NET company. Unless you say that 51% is "most". Windows is strong but not as overwhelming as it was 10 years ago. And it's position is becoming weaker every year.

And .NET is not where fun is!

BTW: Why we have this OT battle about astroturfing for windows here? When OP positions is so obviously **against** windows? Who you want to convert?

---

### Post by Tomosaur on 2007-09-06
I just install Notepad++ to my usb flash drive and take it around with me - an awesome text editor that I can open wherever I like!

[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

---

### Post by codesplice on 2007-09-06
Regardless of what any personal preference may be, Windows IS the industry-standard OS, and VisualStudio IS the industry standard development environment.  If you refuse to work with one or both of those, employment options may be limited for you in the future.

---

### Post by pmasiar on 2007-09-06
I use Python and Turbogears, and I am happily employed.

I do not **refuse** to use Vista/VS: I **prefer** not to, and I was lucky enough to find a job where I can be more productive (and have more fun) using better tools.

---

### Post by ryno519 on 2007-09-06
> **pmasiar said:**
> unsupported claims again. There is Java, and there is Linux. YouTube is **not** a .NET company. Unless you say that 51% is "most". Windows is strong but not as overwhelming as it was 10 years ago. And it's position is becoming weaker every year.

And .NET is not where fun is!

BTW: Why we have this OT battle about astroturfing for windows here? When OP positions is so obviously **against** windows? Who you want to convert?

You challenge the claim that the majority of the programming jobs available are for Windows development? You're free to prove otherwise, but I don't feel like searching google for statistics to prove what is common knowledge, you are free to try and prove otherwise. 

Also wasn't aware that youtube made up 49% of the programming community. ;)

.NET programming is as good as anything else, really. I definitely prefer it to java and prefer C# to just about any other high level language.

A little paranoid? Correct me if I'm wrong, but the OP was talking about Windows development, correct? He said that developing in Windows sucks, I disagree, so given the OP I'd say that no discussion about Windows as a development environment is off topic. I don't think I ever said that he shouldn't code on GNU/Linux, I simply said that in industry there's a very very very very good chance he's going to be working mostly in Windows using Visual Studio.

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> I simply said that in industry there's a very very very very good chance he's going to be working mostly in Windows using Visual Studio.

No, you try to weasel out: you said: 
> because chances are he'll spend 100% of his career coding in Windows

If he hates Windows, chances are he can easily find Linux (or even Java) job. And this chance will be only increasing. Windows is not the only game in the town.

Edit: BTW I never said Windows is off-topic. **Pretending that Windows is the only platform with any future** is.... silly astroturfing. Especially in this forum :-)

---

### Post by dempl_dempl on 2007-09-06
> **ryno519 said:**
> You challenge the claim that the majority of the programming jobs available are for Windows development? You're free to prove otherwise, but I don't feel like searching google for statistics to prove what is common knowledge, you are free to try and prove otherwise. 

Also wasn't aware that youtube made up 49% of the programming community. ;)

.NET programming is as good as anything else, really. I definitely prefer it to java and prefer C# to just about any other high level language.

A little paranoid? Correct me if I'm wrong, but the OP was talking about Windows development, correct? He said that developing in Windows sucks, I disagree, so given the OP I'd say that no discussion about Windows as a development environment is off topic. I don't think I ever said that he shouldn't code on GNU/Linux, I simply said that in industry there's a very very very very good chance he's going to be working mostly in Windows using Visual Studio.


The thing is,  Linux looks very good from the distance, but when it becomes something you work with, you start to like it's charm , but you also start being pissed off. People who say they like programming on Linux more than programming on Windows , have never tried to make something usefull on both of them. I have, and both of those platforms piss me off in different kind of ways.

But I'm moving to Linux permanently, because it slowly starts to be a lot comfortable for work, espacially our distro.

But spitting MS **programs** is not Ok ( spitting a M$ **company** is  ok, offcourse , like on any other evil company :)  like Coca-Cola and Lochead-Martin etc.)
Those folks have finished colleges like the rest of us, and make programs for 20 or more years.

Journalists like spitting on MS most, but leave them without Windoze for three days, and they will die :-D .

BTW,
If you think C# is better than C++ , you don't know those two languages enough, if you like C# more than C++ , well .....  ok :) .

---

### Post by ryno519 on 2007-09-06
> **pmasiar said:**
> No, you try to weasel out: you said: 


If he hates Windows, chances are he can easily find Linux (or even Java) job. And this chance will be only increasing. Windows is not the only game in the town.

Edit: BTW I never said Windows is off-topic. **Pretending that Windows is the only platform with any future** is.... silly astroturfing. Especially in this forum :-)

Alright, do you deal with everybody who doesn't agree with you by accusing them of being paid operatives spreading FUD? Thought we were having an good conversation until that idiocy came into play. Lucky for me, if you decide to continue acting like a child instead of an grown adult, I can simply add you to my ignore list and not have to deal with that ****.

Chances are a programmer will spend all of their time coding in Windows. Most of the programmers I know code in nothing but Windows. We can't all work for Red Hat, you know. The vast majority of commercial of business applications are written on Windows. Sure, he can find a job programming nothing but GNU/Linux apps, but they're not as easy to come by.

Mind pointing out where I pretend Windows is the only platform with any future? All popular platforms have a future, I'm pointing out that Windows has the easiest to use development environment NOW.

---

### Post by ryno519 on 2007-09-06
> **dempl_dempl said:**
> The thing is,  Linux looks very good from the distance, but when it becomes something you work with, you start to like it's charm , but you also start being pissed off. People who say they like programming on Linux more than programming on Windows , have never tried to make something usefull on both of them. I have, and both of those platforms piss me off in different kind of ways.

But I'm moving to Linux permanently, because it slowly starts to be a lot comfortable for work, espacially our distro.

But spitting MS **programs** is not Ok ( spitting a M$ **company** is  ok, offcourse , like on any other evil company :)  like Coca-Cola and Lochead-Martin etc.)
Those folks have finished colleges like the rest of us, and make programs for 20 or more years.

Journalists like spitting on MS most, but leave them without Windoze for three days, and they will die :-D .

BTW,
If you think C# is better than C++ , you don't know those two languages enough, if you like C# more than C++ , well .....  ok :) .

Yeah, I've moved entirely to GNU/Linux a while ago and code all of my personal projects on it.

I don't really consider C++ a high-level language. In many regards, it can be considered as such, but it also has a lot of low-level access as well. I put it somewhere in between. C++ is my preferred language, by the way. :)

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> Chances are a programmer will spend all of their time coding in Windows. 

Chances are, if you want to, you can get job where at least part of your work will be running Linux web server, or database server, or something. Linux is becoming ubiquitous IMHO. maybe it depend on which country you live? 

And you can always start your own company and do it right :-) 

> We can't all work for Red Hat, you know. 

I don't work for RH, but I do run Linux web server, MySQL, Python, TurboGears, TRAC, perl, Twiki, etc.

> The vast majority of commercial of business applications are written on Windows. 

Big part are coded in Java, so even if developed on windows, they are deployed on Linux. Linux is just better server in my experience.

> Mind pointing out where I pretend Windows is the only platform with any future? 

when you said 100% of future career?

> All popular platforms have a future, I'm pointing out that Windows has the easiest to use development environment NOW.

Until now you claimed "windows are most used". Now it is "easiest to use". Is it a change? Or am I missing something?

Not sure about which superior windows environments are you talking about. But I admit I actively try to avoid welding myself to .NET. :-) One of our smartest programmer has big project in.NET, and he is unhappy about it, but it looked like a good decision years ago, and too late to change now. So yes, I am sorry it would be interesting to work with him, but I still try to avoid .NET.

I have to develop on windows at work, so I try hard to use only cross-platform tools (no difference to use), but even then, installing them on ubuntu is so much simpler. And I like to be in the control: if I really want to, I can learn how it works and customize it. This is important for me.

Looks like we agree that we disagree. maybe you want to run a poll to ask people here which development platform they prefer? Or is easiest to use?

---

### Post by pmasiar on 2007-09-06
> **ryno519 said:**
> .NET programming is as good as anything else, really. I definitely prefer it to java and prefer C# to just about any other high level language.

> **ryno519 said:**
> C++ is my preferred language, by the way. :)

so which one is it? Or some other confusion again?

---

### Post by xtacocorex on 2007-09-06
I only said learn the fundamantals no matter what, because that is the starting place for learning anything.  Sometimes you have to buck up and deal with stuff you have no control over.  If a class requires you to do something a certain way, anything against that will garner bad grades and reputation.  

The more you know, the more marketable you become.  Either way, I provided my opinion to the OP, he can take it as he wants.

---

### Post by rharriso on 2007-09-07
A neat editor for Windows is Notepad++ its free check it out

---

### Post by EXCiD3 on 2007-09-07
> **rharriso said:**
> A neat editor for Windows is Notepad++ its free check it out

PSPad is my favorite Windows programing IDE. It support just about every programming language ever!

---

