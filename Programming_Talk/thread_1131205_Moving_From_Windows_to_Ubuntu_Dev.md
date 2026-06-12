---
title: "Moving From Windows to Ubuntu Dev"
date: 2009-04-20
forum: Programming Talk
---

### Post by ubuwatson on 2009-04-20
I have been programming in Microsoft Windows environments for over 20 years.  I have been looking around at various programming options for Linux and in general I have been disappointed (or should I state 'confused'). 

I think in general what turns off windows programmers like myself in linux is that information is scattered all over the place and there are too many variables making the whole process rather confusing, plus some of the information that is out there is often dated or incomplete.

I would love to contribute to the community, but Ubuntu users in general need to stop snobbing newbies like myself, I often read post after post where a user is attempting to move from excellent IDEs like that of .NET only to find the typical answer such as IDEs are for beginners and you should learn to use a text editor - these blanket statements are rather uneducated, show a childish bias against Microsoft and don't encourage people like myself to contribute.  In general, if you want to 'grow' linux you need to accept and embrace users like myself so that we can make the development transition and in turn provide the kind of applications that attract users who are thinking of switching from Windows....

Please do us Windows transplants a favor, make this thread one that 'fills in the blanks': give me the information from scratch, post step-by-step screen shots if at all possible.

Just to give things a start, Python looks to be good language to work with and I think i can live in a text editor and learn to program using this language.  I found a good tutorial, but wanted to make sure the concepts applied here are fairly current and that tutorial works with my distro: [http://www.pygtk.org/dist/pygtk2-tut.pdf](http://www.pygtk.org/dist/pygtk2-tut.pdf) as the information is dated from 2005.  

My problem with Python development (and Linux development in general) can be found here: [http://www.pygtk.org/articles.html](http://www.pygtk.org/articles.html).  There are articles about Python development using Cairo, using Glade, using Gnome, using GTK, Widgets, etc.  See my confusion, I just want to know how to develop a GUI using Python in Ubuntu, but the information is all over the place and don't know where to start. Keep in mind I am not asking how to program in linux (I'll figure that part out for myself), what I am trying to learn is how to start programming in linux.

Thanks,
Daniel

---

### Post by ddrichardson on 2009-04-20
Widgets are a nause. The default Ubuntu desktop uses Gnome, so you want GTK, or rather pygtk for python: [http://www.pygtk.org/pygtk2reference/](http://www.pygtk.org/pygtk2reference/). Glade is basically a screen painter for GTK, that produces XML defining interfaces.

KDE (Kubuntu) is normally Nokia/Trolltech's QT libraries.

---

### Post by lvleph on 2009-04-20
I don't program in Python, but [this](http://wiki.python.org/moin/GuiProgramming) was what I found using the google. It looks to me as though this site would be a good place to start.

---

### Post by gtr32 on 2009-04-20
If you're coming from Visual Studio, I would suggest trying out MonoDevelop: [http://monodevelop.com/](http://monodevelop.com/)

There should be a plugin for Python as well.

---

### Post by simeon87 on 2009-04-20
Programming for Linux comes down to: grab the tools you need and get to work. Which tools you ask? That depends on the task at hand. Coming from Windows you'll have to familiarize yourself with a lot of new terms but that's life. Also, "dated" information is not necessarily wrong.

To be honest though: you're critizing the attitude towards the use of an IDE but your post also proves that point by asking for step-by-step screenshots or saying "I think I can live in a text editor", which, to me, indicates a dependence on IDE-centered development. It's important for people without programming experience to know the difference between the language and the IDE. Although you have programming experience, you do appear to defend your IDE: "these ... statements ... show a childish bias towards Microsoft"? Eh no, it's genuine advice to learn programming in a text editor.

---

### Post by ubuwatson on 2009-04-20
> **simeon87 said:**
> Programming for Linux comes down to: grab the tools you need and get to work. Which tools you ask? That depends on the task at hand. Coming from Windows you'll have to familiarize yourself with a lot of new terms but that's life. Also, "dated" information is not necessarily wrong.

To be honest though: you're critizing the attitude towards the use of an IDE but your post also proves that point by asking for step-by-step screenshots or saying "I think I can live in a text editor", which, to me, indicates a dependence on IDE-centered development. It's important for people without programming experience to know the difference between the language and the IDE. Although you have programming experience, you do appear to defend your IDE: "these ... statements ... show a childish bias towards Microsoft"? Eh no, it's genuine advice to learn programming in a text editor.

I don't get the IDE dependence reference.  We are living in a modern age of programming where IDEs are part of the development process, use of the text editor for development is fine, but it also archaic as we have come a long way in the development process and now have 'tools' available to us to make some of the common/redundant tasks such as form design less taxing so we can spend more time on the heart of an application.  I get paid to develop sophisticated client/server systems under .NET, and I don't have time to draw each button by hand (I have done that in the past mind you) - my time is better spent on the code behind the scenes and not on the GUI itself and that is where an IDE makes perfect sense. I am not defending the IDE by talking about 'Microsoft Bias', but if you mention .NET around here and it almost seems like you are an outcast.  I just want to help, want to contribute....

I don't think forcing someone to develop in a text editor vs. an IDE necessarily makes them a better programmer, sometimes it's all about getting started and sometimes that requires the path of least resistance.  

A friend of mine is facing the same challenge, I consider him one of the best in this field and yet he is exactly where I am at, where to start.

I thought Ubuntu stood for Linux For Human Beings, I just want this terminology to hold true when we talk about software development.

I am sorry if my post seemed 'angry' or 'frustrated' - i was more or less hoping to solve problems here that other people face as I have talked to other programmers with the same questions/problems, etc.  I really just want to figure this out and contribute as my way of paying back for what I consider a fantastic product.

---

### Post by ubuwatson on 2009-04-20
> **ddrichardson said:**
> Widgets are a nause. The default Ubuntu desktop uses Gnome, so you want GTK, or rather pygtk for python: [http://www.pygtk.org/pygtk2reference/](http://www.pygtk.org/pygtk2reference/). Glade is basically a screen painter for GTK, that produces XML defining interfaces.

KDE (Kubuntu) is normally Nokia/Trolltech's QT libraries.

Thank you, that is the kind of information I was looking for.  Yes I do have some terminology to learn.

---

### Post by Yacoby on 2009-04-20
> **ubuwatson said:**
> I often read post after post where a user is attempting to move from excellent IDEs like that of .NET only to find the typical answer such as IDEs are for beginners and you should learn to use a text editor - these blanket statements are rather uneducated, show a childish bias against Microsoft and don't encourage people like myself to contribute.

What I think people means is that you shouldn't just know how to compile a program in IDE xyz, but you should understand how the underlying tools work. Although when someone makes this statment, there are usally a lot of other posts saying "Use IDE pqr"


I learnt C++ in a text editor, which may be why I can't see the point in it. Horrible thing, writing complex code in a text editor, imo start running. ;)
OK, I can see a bit of a point in understanding how things like gcc work, but it isn't required.

> **ubuwatson said:**
> I don't get the IDE dependence reference.  We are living in a modern age of programming where IDEs are part of the development process, use of the text editor for development is fine, but it also archaic as we have come a long way in the development process and now have 'tools' available to us to make some of the common/redundant tasks such as form design less taxing so we can spend more time on the heart of an application.  Understanding how things work is a good idea. It may not directly help your productivity, but it may help with your understanding.
A bit like a C++ developer leaning assembly.

> I get paid to develop sophisticated client/server systems under .NET, and I don't have time to draw each button by hand (I have done that in the past mind you) - my time is better spent on the code behind the scenes and not on the GUI itself and that is where an IDE makes perfect sense. An IDE doesn't necessarily include a GUI designer.

---

### Post by Bodsda on 2009-04-20
> **ubuwatson said:**
> I have been programming in Microsoft Windows environments for over 20 years.  I have been looking around at various programming options for Linux and in general I have been disappointed (or should I state 'confused'). 

I think in general what turns off windows programmers like myself in linux is that information is scattered all over the place and there are too many variables making the whole process rather confusing, plus some of the information that is out there is often dated or incomplete.

I would love to contribute to the community, but Ubuntu users in general need to stop snobbing newbies like myself, I often read post after post where a user is attempting to move from excellent IDEs like that of .NET only to find the typical answer such as IDEs are for beginners and you should learn to use a text editor - these blanket statements are rather uneducated, show a childish bias against Microsoft and don't encourage people like myself to contribute.  In general, if you want to 'grow' linux you need to accept and embrace users like myself so that we can make the development transition and in turn provide the kind of applications that attract users who are thinking of switching from Windows....

Please do us Windows transplants a favor, make this thread one that 'fills in the blanks': give me the information from scratch, post step-by-step screen shots if at all possible.

Just to give things a start, Python looks to be good language to work with and I think i can live in a text editor and learn to program using this language.  I found a good tutorial, but wanted to make sure the concepts applied here are fairly current and that tutorial works with my distro: [http://www.pygtk.org/dist/pygtk2-tut.pdf](http://www.pygtk.org/dist/pygtk2-tut.pdf) as the information is dated from 2005.  

My problem with Python development (and Linux development in general) can be found here: [http://www.pygtk.org/articles.html](http://www.pygtk.org/articles.html).  There are articles about Python development using Cairo, using Glade, using Gnome, using GTK, Widgets, etc.  See my confusion, I just want to know how to develop a GUI using Python in Ubuntu, but the information is all over the place and don't know where to start. Keep in mind I am not asking how to program in linux (I'll figure that part out for myself), what I am trying to learn is how to start programming in linux.

Thanks,
Daniel

So what your asking is, we (people who have trawled the resources to find answers) spend our time putting it all together into a pretty little plot so that someone who has little to no intention of doing any leg work themselves can just waltz in and benefit from others without saying thank you, and before you say you will say thank you, eventually people wont.

I think the attitude you have shown in your original post is one of a user who (on his previous operating system) feels comfortable, knows where things are and expects Linux to be the same. Personally I have no problem in helping, if you ask politely for locations of resources I would oblige by giving them to you, however I am utterly surprised that anyone who posted in this thread gave you an answer. 

You seem very biased towards windows IDE's and very rude towards the community, slating all Ubuntu users as being snobby noob bashers. One of the main reasons people on these forums suggest editors such as vi and emacs over IDE's is because of Linux being inherently command line based. for example, if you ask a builder how to break through a wall, he might suggest a sledgehammer, if you ask a demolitions expert he might suggest dynamite, just because you prefer one group does not mean the other is wrong it just means you prefer your way. Builders dont go personally attacking the Demolitioners because of their preferred way to break through a wall. 

Kind regards.

Bodsda

---

### Post by ubuwatson on 2009-04-20
> So what your asking is, we (people who have trawled the resources to find answers) spend our time putting it all together into a pretty little plot so that someone who has little to no intention of doing any leg work themselves can just waltz in and benefit from others without saying thank you, and before you say you will say thank you, eventually people wont.

Your putting words in my mouth - I am pushing an open issue out there that needs to be resolved and I was asking the community for help resolving it.  Was I blunt in my posting, yes, was it necessary, yes it was.  I wasn't generalizing that everyone is snoobish.

> I think the attitude you have shown in your original post is one of a user who (on his previous operating system) feels comfortable, knows where things are and expects Linux to be the same. Personally I have no problem in helping, if you ask politely for locations of resources I would oblige by giving them to you, however I am utterly surprised that anyone who posted in this thread gave you an answer.

Your attitude seems worse then mine, I was just getting attention to hopefully resolve a problem, I stated several times that I just want to contribute, but I have found countless threads on this forum that go no where because people in this community fail to understand the poster's needs - someone states that they are looking for an environment like .NET and five people reply use a text editor and do 'real' programming.

> You seem very biased towards windows IDE's and very rude towards the community, slating all Ubuntu users as being snobby noob bashers. One of the main reasons people on these forums suggest editors such as vi and emacs over IDE's is because of Linux being inherently command line based. for example, if you ask a builder how to break through a wall, he might suggest a sledgehammer, if you ask a demolitions expert he might suggest dynamite, just because you prefer one group does not mean the other is wrong it just means you prefer your way. Builders dont go personally attacking the Demolitioners because of their preferred way to break through a wall. 

I wasn't rude towards the community, you are taking things out of context and putting words in my mouth. This post is for the community and not just for me, you can hate my post and hate me all you want, but focus on helping others using this thread as a starting point.  Do I like IDEs ? Of course, I am not ashamed to admit it, they are the reason I make a great living - however there is no bias, the bias I have found is here on this forum with 'some' (but not all) Linux users (many people here are great).  I think 'some' linux folks just need to get over themselves.  Linux is fantastic, I love it, but the constant Microsoft bashing and bias shows a weakness or shall I state jealousy in some respects that IMHO hurts the evolution of a great product.  Fine if you don't want to help or choose to argue.  I'll do my best to figure things out for myself, or just give up and continue developing on a windows platform, in the end you are only hurting Linux, not me.

Your post is the typical response I expected, and your signature "The box said "Requires windows XP or better." So I installed Ubuntu" says it all..............

---

### Post by KlinerDraken on 2009-04-20
I like SPE (Stani's Python Editor) for writing python in. I haven't yet gotten to the point of making gui apps yet but I see under "Tools" on the menu there are two gui designers.

Hope that helps

PS... make sure you go in to the preferences and show white spaces, four spaces is not the same as a TAB. That was something that was giving me issues when I first started to learn python.

---

### Post by ddrichardson on 2009-04-20
> **ubuwatson said:**
> I would love to contribute to the community, but Ubuntu users in general need to stop snobbing newbies like myself, I often read post after post where a user is attempting to move from excellent IDEs like that of .NET only to find the typical answer such as IDEs are for beginners and you should learn to use a text editor - these blanket statements are rather uneducated, show a childish bias against Microsoft and don't encourage people like myself to contribute.  In general, if you want to 'grow' linux you need to accept and embrace users like myself so that we can make the development transition and in turn provide the kind of applications that attract users who are thinking of switching from Windows....
In fairness, if you're encountering that kind of attitude then that's not the norm and certainly shouldn't be. Ubuntu members are required to sign a code of conduct and don't tend to engage in this kind of nonsense and while I've seen it I don't think its as prevelant as you suggest.

Also, the forum is not necessarily the best place to begin a transition to Linux development as the dev teams tend to be on IRC and mailing lists.

In defense of posts promoting editors over IDE, the UNIX world in general is not IDE based and never has been, whereas the Windows world is. Its night and day and although there are some good IDE, it is sa long way from become a standard because it doesn't really fit well with the way source tends to be compiled using Makefiles which ultimately links in to the way both packaging and licensing work under most Linux distributions.

Really, if you want to start contributing to Linux and you're experienced and trying to get a feel for the system then the best contribution is to find bugs on a product you're interested in and is similar to one you know from Windows development.

Bug patching is needed and quite rewarding, it certainly lets you familiarise yourself with the system.

I'd also advise reading over [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

I wish you all the best in your endeavours.

---

### Post by gregor171 on 2009-04-20
**Welcome to your new life.** I'm myself ex MS guy or should I say a Trojan horse there.

.NET IDE is a great environment, but when it starts to make you pain it hearts. They never admit bugs before they make new version without it.

However .NET has some good issues in it's object palette. Since I moved to Web I'd suggest PHP (5 or more). It has a great OOP potential.

For desktop apps C++, but I made only a few sample applications. 

IDE's:
Eclipse 3.4 (add PDT for PHP) it's quite extendable and it has a solid intellisense.
Quanta plus I also liked, but doesn't have so nice intellisense (doesn't include autoload objects or am I missing something)
kDevelop for C++

I've never tried Mono since I don't trust it in some advance stuff.

---

### Post by ubuwatson on 2009-04-21
> **ddrichardson said:**
> In fairness, if you're encountering that kind of attitude then that's not the norm and certainly shouldn't be. Ubuntu members are required to sign a code of conduct and don't tend to engage in this kind of nonsense and while I've seen it I don't think its as prevelant as you suggest.

Also, the forum is not necessarily the best place to begin a transition to Linux development as the dev teams tend to be on IRC and mailing lists.

In defense of posts promoting editors over IDE, the UNIX world in general is not IDE based and never has been, whereas the Windows world is. Its night and day and although there are some good IDE, it is sa long way from become a standard because it doesn't really fit well with the way source tends to be compiled using Makefiles which ultimately links in to the way both packaging and licensing work under most Linux distributions.

Really, if you want to start contributing to Linux and you're experienced and trying to get a feel for the system then the best contribution is to find bugs on a product you're interested in and is similar to one you know from Windows development.

Bug patching is needed and quite rewarding, it certainly lets you familiarise yourself with the system.

I'd also advise reading over [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

I wish you all the best in your endeavours.

Thanks for your comments.  I re-read my original post last night and realized I came across very strong, if not rude, and I apologize as this was not my intent, but sometimes what you are thinking and how things come across in post are not always the same thing, I hope I didn't offend anyone.

I also understand the editor vs. IDE thing, though I never assumed IDEs were an exclusive windows initiative, to me the IDE is just the evolution of a 'text editor' into a environment that is best suited for professional development.  At work the IDE offers a robust debugger, forms designer, intellisence, configuration management, etc - none of these things to me should be windows only concepts, these are tools designed to build better products - you can build a great program in a text editor, but when it comes to building applications for corporations (like I do) these tools are essential to reduce bugs, ensure best coding practices and provide a level of CM.  I think the confusion here is that IDEs are designed to make you less of a programmer when in fact I have found that my programming has become more refined by using IDEs and the number of bugs have been reduced by a large margin due to the real-time debuggers and I can spend more time concentrating on delivering a better product instead of coding redundant details.  Could I live without the IDE, of course, could I produce the applications that I do on the tight deadlines without one, it would be very difficult if not impossible.

---

### Post by ubuwatson on 2009-04-21
> **gregor171 said:**
> **Welcome to your new life.** I'm myself ex MS guy or should I say a Trojan horse there.

.NET IDE is a great environment, but when it starts to make you pain it hearts. They never admit bugs before they make new version without it.

However .NET has some good issues in it's object palette. Since I moved to Web I'd suggest PHP (5 or more). It has a great OOP potential.

For desktop apps C++, but I made only a few sample applications. 

IDE's:
Eclipse 3.4 (add PDT for PHP) it's quite extendable and it has a solid intellisense.
Quanta plus I also liked, but doesn't have so nice intellisense (doesn't include autoload objects or am I missing something)
kDevelop for C++

I've never tried Mono since I don't trust it in some advance stuff.

Microsoft has made some bad mistakes over the years and some bad products as well, but .NET is probably one the best products it has ever produced, almost a work of art when it comes to development environments and I don't think anything else comes close.

I might try Python GTK for now, it does seem to be a very good and robust language.

---

### Post by Tibuda on 2009-04-21
> **ubuwatson said:**
> Microsoft has made some bad mistakes over the years and some bad products as well, but .NET is probably one the best products it has ever produced, almost a work of art when it comes to development environments and I don't think anything else comes close.

I might try Python GTK for now, it does seem to be a very good and robust language.

If you like and already know C# or .NET, you should try [Mono and Gtk#]("http://mono-project.com/") with the [MonoDevelop IDE]("http://monodevelop.com/").

---

### Post by gregor171 on 2009-04-21
> Microsoft has made some bad mistakes over the years and some bad products as well, but .NET is probably one the best products it has ever produced, almost a work of art when it comes to development environments and I don't think anything else comes close.

True. Except sometimes they tend to mislead you. Doing ASP.NET for years, I found that is better to create custom controls, than using some of theirs. Some are good, but sometimes there was a better way to make gui with Dreamwaver and copy html to VS studio. Never the less Eclipse does come close. I'd say that using IDE's has some strong points such as intellisense, debugging... Being familiar with text editor helps. As they got colors they started to move towards IDE's. 

So coming from MS environment I was also searching for such IDE and Eclipse gave me some main advantages. I'd change if I'd find better one.

---

### Post by ajackson on 2009-04-21
> **ubuwatson said:**
> Thanks for your comments.  I re-read my original post last night and realized I came across very strong, if not rude, and I apologize as this was not my intent, but sometimes what you are thinking and how things come across in post are not always the same thing, I hope I didn't offend anyone.
Unfortunately it did offend some people. You make wide sweeping generalisations, don't seem to under what your searching throws up (PyGTK **will** be focussed on using Python with the GTK libraries, it is very specific and detailed). You then get upset/angry when someone replies in a roughly identical manner to your opening post.

If you do end up writing apps for general use you will get some complete novices struggling with your app, if you blow up at them when they ask for help it doesn't help.

But if you forget all that (if you haven't worked out how to interact with fellow humans by now you never will). Since you are coming from a .NET background the Mono is the logical choice as it is C# as well. For GUIs I would recommend using Glade (you can hand-craft them but with 20 years of development knowledge I think by now you know what widgets, panes, etc are). If you then decide to switch to Python you can use your Glade files with that as well. So an interesting project might be to write a simple app in Mono (which builds on your existing knowledge) then port it to Python to aid learning that language.

Monodevelop is a very good IDE for Mono, well it was when I used it around a year ago and I'm sure it has got better rather than worse since then.

I'm one of those who prefers text editors, mainly because I used to program on mainframes with no fancy GUIs, so you learnt coding via a text editor or got out of the industry.

Which ever route you take IDE/editor/both, do what you feel most comfortable with, don't listen to others who tell you one way is good and the other is bad.

---

### Post by gali98 on 2009-04-21
I am not much of a programmer, but I noticed no one mentioned netbeans.
I have heard it is a good ide, but I really have no idea.
[http://www.netbeans.org/](http://www.netbeans.org/)
It is in the package manager as well. (package name: netbeans)
Kory

---

### Post by Simian Man on 2009-04-21
> **ubuwatson said:**
> We are living in a modern age of programming where IDEs are part of the development process, use of the text editor for development is fine, but it also archaic as we have come a long way in the development process and now have 'tools' available to us to make some of the common/redundant tasks such as form design less taxing so we can spend more time on the heart of an application.  I get paid to develop sophisticated client/server systems under .NET, and I don't have time to draw each button by hand (I have done that in the past mind you) - my time is better spent on the code behind the scenes and not on the GUI itself and that is where an IDE makes perfect sense. I am not defending the IDE by talking about 'Microsoft Bias', but if you mention .NET around here and it almost seems like you are an outcast.  I just want to help, want to contribute....

I don't think forcing someone to develop in a text editor vs. an IDE necessarily makes them a better programmer, sometimes it's all about getting started and sometimes that requires the path of least resistance.  

The thing is that the concept of IDEs go totally against the [Unix philosophy]("http://en.wikipedia.org/wiki/Unix_philosophy") of making each program do one thing well.  In an IDE, your text editor, build process, GUI designer, debugger, help viewer and other things are integrated into one program.  You can't, at least not easily, replace any part of the tool with something else.

The fact that most Linux developers don't use IDEs doesn't mean that they are relics of a past age, and it *certainly* isn't because they do everything by hand.  The fact is that there are Linux tools that do all of the functions an IDE can handle, *and do them better*.

Vim, Emacs, Kate and Gedit all have way more features then text editors that come roped into IDEs like VS.  Make, autotools and scons have way more flexibility then build processes included with IDEs.  Likewise there are standalone GUI builders (Glade, QT-Creator...), debuggers (ddd, kdbg...), source code searchers (ctags, cscope...) and more.  Not to mention the text manipulation power of a Unix shell!

Once you get up to speed with some of these tools, you will find that they are more powerful and flexible than an IDE that forces you to adopt a particular work flow.  My current project uses: C, Ocaml, Ocamllex, Ocamlyacc and Scheme.  What kind of IDE can handle that?? :)

Of course if you need an IDE, there are some on Linux available.  But don't expect others to accept your view that they are somehow superior to choosing individual tools, because they are not.  And don't expect the Linux community to focus its energy on just one tool because that is completely missing the point.

---

### Post by Yacoby on 2009-04-21
> **Simian Man said:**
> The thing is that the concept of IDEs go totally against the [Unix philosophy]("http://en.wikipedia.org/wiki/Unix_philosophy") of making each program do one thing well.  In an IDE, your text editor, build process, GUI designer, debugger, help viewer and other things are integrated into one program.  You can't, at least not easily, replace any part of the tool with something else.Some IDEs, e.g. Code::Blocks are just a program that brings a series of tools together (except it has its own text editor, but I think that is a library for something else). 
While it has a profiler, all it is in C::B is a plugin, which wraps around the original tool.

The same thing can no doubt be said of other IDEs

---

### Post by ubuwatson on 2009-04-21
> **ajackson said:**
> Unfortunately it did offend some people. You make wide sweeping generalisations, don't seem to under what your searching throws up (PyGTK **will** be focussed on using Python with the GTK libraries, it is very specific and detailed). You then get upset/angry when someone replies in a roughly identical manner to your opening post.

If you do end up writing apps for general use you will get some complete novices struggling with your app, if you blow up at them when they ask for help it doesn't help.

But if you forget all that (if you haven't worked out how to interact with fellow humans by now you never will). Since you are coming from a .NET background the Mono is the logical choice as it is C# as well. For GUIs I would recommend using Glade (you can hand-craft them but with 20 years of development knowledge I think by now you know what widgets, panes, etc are). If you then decide to switch to Python you can use your Glade files with that as well. So an interesting project might be to write a simple app in Mono (which builds on your existing knowledge) then port it to Python to aid learning that language.

Monodevelop is a very good IDE for Mono, well it was when I used it around a year ago and I'm sure it has got better rather than worse since then.

I'm one of those who prefers text editors, mainly because I used to program on mainframes with no fancy GUIs, so you learnt coding via a text editor or got out of the industry.

Which ever route you take IDE/editor/both, do what you feel most comfortable with, don't listen to others who tell you one way is good and the other is bad.

Like I said, I apologize, it was not my intention to offend anyone.  

One thing to keep in mind, I am not 'hung up' on sticking with Microsoft based technologies like .NET.  I am forward thinking and have no problem adapting to Linux, in fact I think I would be better off learning a new language like Python for example.  I am not one of the Microsoft transplants looking to change Linux into Windows, that has never been my intention.

---

### Post by ubuwatson on 2009-04-21
> Of course if you need an IDE, there are some on Linux available.  But don't expect others to accept your view that they are somehow superior to choosing individual tools, because they are not.  And don't expect the Linux community to focus its energy on just one tool because that is completely missing the point.

I never said they were superior, but your blanket statement that they are not superior to the tools found in Linux is subjective to say the very least.  

I am not trying to defend Microsofts IDE, but I have been using .NET for several years now so I feel my experience merits some weight.  When I state that I have built hundreds of projects using .NET, I am being 100% honest with you. We rolled out applications to over 16,000 desktops worldwide with little to no problems and that the applications we produced were somewhat complex touching on a number .NET technologies.

The defensiveness seems to be coming from the Linux side, I could care less about the whole Microsoft vs. Linux thing, I run both and can name just as many pros and cons in each system as I have no bias.

My biggest turnoff to Linux is (some of) the user base which seems to be hung up on being anti-Microsoft.

---

### Post by simeon87 on 2009-04-21
> **ubuwatson said:**
> The defensiveness seems to be coming from the Linux side, I could care less about the whole Microsoft vs. Linux thing, I run both and can name just as many pros and cons in each system as I have no bias.

My biggest turnoff to Linux is (some of) the user base which seems to be hung up on being anti-Microsoft.

So the attitude of a part of the user base has such an influence on your view of Linux in general?

I wonder why you bring it up as criticism against Linux and the Linux community? In general, Linux users support free software and Microsoft has done quite a few things that hinder free software so it's a valid view (one that you may or may not hold). Some indeed bash just because they like to bash but that shouldn't affect those who carefully weigh arguments to make up their mind.

---

### Post by Simian Man on 2009-04-21
[QUOTE=ubuwatson]I never said they were superior, but your blanket statement that they are not superior to the tools found in Linux is subjective to say the very least.[/quote]
It may be debatable as a whole, but in general a program designed for a specific function - such as vim for editing or grep for searching - will be better than a part of a program with greater scope that implements the same feature.

[QUOTE=ubuwatson]The defensiveness seems to be coming from the Linux side, I could care less about the whole Microsoft vs. Linux thing, I run both and can name just as many pros and cons in each system as I have no bias.

My biggest turnoff to Linux is (some of) the user base which seems to be hung up on being anti-Microsoft.[/quote]

Ha ha I am not a fanboy, sorry if I gave that impression.  I run both Windows and Linux too.  I'm not arguing that Linux is better than Windows or anything.  I'm just arguing that the concept of IDEs in general goes against the Linux philosophy so I'm telling you not to expect much in that realm.

If you like them that is perfectly fine.  Obviously other Linux developers do as well because there are quite a few IDEs out there (though admittedly none as well-done as MSVS).  I'm just explaining why most Linux developers don't use them and why there isn't much in the way of learning material for them.

---

### Post by Npl on 2009-04-21
> **Simian Man said:**
> It may be debatable as a whole, but in general a program designed for a specific function - such as vim for editing or grep for searching - will be better than a part of a program with greater scope that implements the same feature.The problem here is that you assume that the programm designed for a specific function **automatically** is better. With that logic, "Notepad" is on the same level as vim, maybe even better because it has less features.
You cant seriously argue that having an IDE which can list functions and classes (and easily jump to their definition), can automatically complete names based on scopes, etc.. cant have an advantage over a generic Text-Editor.
If I were a cynic, which I am, I could say an IDE serves a more specific role (programming and getting your work done) than a texteditor ;)
> **Simian Man said:**
> Ha ha I am not a fanboy, sorry if I gave that impression.  I run both Windows and Linux too.  I'm not arguing that Linux is better than Windows or anything.  I'm just arguing that the concept of IDEs in general goes against the Linux philosophy so I'm telling you not to expect much in that realm.And everything UNIX does is of course way better by definition? Sounds more like religion than technical reasoning.

---

### Post by wsonar on 2009-04-21
It's funny most collage courses will teach you on something like borland


I've tried a few IdE's and will probably try a few more

for now I'm happy with Gedit

---

### Post by wsonar on 2009-04-21
monodevelop is in the jaunty repos so I think I will give it a try

looks kinda cool

---

### Post by gregor171 on 2009-04-21
What is this thing about "Unix philosophy"?
> The fact that most Linux developers don't use IDEs doesn't mean that they are relics of a past age, and it certainly isn't because they do everything by hand. The fact is that there are Linux tools that do all of the functions an IDE can handle, and do them better.
But they do. I've seen also the old gurus using them. .;-)

Looks like you never experienced the true benefits of intellisense in the process when you developed some 100 classes, changed some names and then you have to browse back to see is it form_controler, formControler or form_manager that you want now and fast.

I'm a practical guy. It is not about IDE I use, but about code I write. Nobody is forcing you to use IDE.

---

### Post by Simian Man on 2009-04-21
> **gregor171 said:**
> What is this thing about "Unix philosophy"?
One tool for each job.  By making the tools simple and flexible, the combination is extremely powerful.

> **gregor171 said:**
> Looks like you never experienced the true benefits of intellisense in the process when you developed some 100 classes, changed some names and then you have to browse back to see is it form_controler, formControler or form_manager that you want now and fast.
I have used IDEs for that but find that cscope does the same thing faster.

> I'm a practical guy. It is not about IDE I use, but about code I write. Nobody is forcing you to use IDE.

I was just trying to explain why there aren't many great, ubiquitous IDEs for Linux as there are for Windows - though Eclipse is pretty close.  I definitely am not trying to get people to switch from tools they are comfortable with.

---

### Post by ddrichardson on 2009-04-21
I think the point about IDE that is often missed is that access to debuggers, screen painters and so on are still available in Linux but the distributed nature of the system mean development from first principle is less common.

My first coding job was in a UNIX environment and each person contributing code pushed to a shared server which was de-fragged and compiled each morning. I thought the IDE for Borland C++ was the greatest thing since sliced bread when we got it.

That said, I got into some bad "try it and see" adventures that given debugging time would have been better spent in designing the damn code properly in the first place.

The same tools are all available - it's just that like most OSS there are a number of extremely good, specific tools that no-one really sees the need to re-write.

---

### Post by ddrichardson on 2009-04-21
> **Npl said:**
> The problem here is that you assume that the programm designed for a specific function **automatically** is better. With that logic, "Notepad" is on the same level as vim, maybe even better because it has less features.
You cant seriously argue that having an IDE which can list functions and classes (and easily jump to their definition), can automatically complete names based on scopes, etc.. cant have an advantage over a generic Text-Editor.
If I were a cynic, which I am, I could say an IDE serves a more specific role (programming and getting your work done) than a texteditor ;)
And everything UNIX does is of course way better by definition? Sounds more like religion than technical reasoning.
That very much depends on where you draw the line at "text editor" because there are editors that offer completion and highlighting but I see your point.

At the end of the day, whatever works for you works for you.

---

### Post by gregor171 on 2009-04-21
> I have used IDEs for that but find that cscope does the same thing faster.
;-) good for u. I use vi as well -> there is: if I must.

> I was just trying to explain why there aren't many great, ubiquitous IDEs for Linux as there are for Windows - though Eclipse is pretty close. I definitely am not trying to get people to switch from tools they are comfortable with.
I believe the part of this thread was about IDEs, but it turned to a quest.

U should be more happy when MS guys are turning to Linux.

---

### Post by simeon87 on 2009-04-21
> **gregor171 said:**
> I believe the part of this thread was about IDEs, but it turned to a quest.

U should be more happy when MS guys are turning to Linux.

I think we're just stating our opinion.. which doesn't happen to change when people switch from Windows to Linux.

---

### Post by ubuwatson on 2009-04-21
> **gregor171 said:**
> ;-) good for u. I use vi as well -> there is: if I must.


I believe the part of this thread was about IDEs, but it turned to a quest.

U should be more happy when MS guys are turning to Linux.

Nope, now I am mad and switching back to Vista - ;) NOT !

---

### Post by ddrichardson on 2009-04-21
> **gregor171 said:**
> U should be more happy when MS guys are turning to Linux.
Why?

Just interested, because I'm happy to help anyone regardless of where they come from.

---

### Post by fr4nko on 2009-05-20
Hi,

I'm happy to hear of a Microsoft programmer that want to work on linux! I hope that more and more will follow in the future.

I don't know if I can help you a lot. My favorite development environment is emacs, if someone is interested I've made a post to explain why I'm [happy with emacs]("http://ubuntuforums.org/showpost.php?p=7310511&postcount=904").

Otherwise, I understand your point of view, probably the .NET IDE is very well done and the documentation is very good and well organized. I think that on linux you don't have such a full-featured, polished IDE like .NET for two important reasons:

[LIST]
[*]there isn't any powerful firm like microsoft to develop something similar on linux
[*]the better programmers on linux are used to work with advanced text editors like emacs or vim and the command line tools.
[/LIST]
Probably if you want to switch to linux you should change attitude: with linux you don't have the M$ big brother that takes care of everything, with linux you have the freedom and freedom often came with a price. The price in this case is that the tools are sometimes sub-optimal and the informations are scattered in many different places like you was saying.
But, from my personal point of view, I'm passionate of programming and computer science and I will never work of M$ platforms because their closed source, proprietary tools are just made to take your freedom, make you dependent and make a lot of money from users. I'm forced to use M$ tools at works and for me it is painful, linux is a breathe of fresh air in comparison.

To better explain my point of view let me add something. On linux systems people can get more rich in term of knowledge because everything is shared, from softwares to documentation and to best practices. This is the opposite of proprietary approach that tend to protect and hide the knowledge as much as possible and try to create dependency for their users in order to bind them to their products.

But now luckily the linux and the free software is gaining more and more popularity and nothing will be able to stop this process. A lot of wonderful projects came to life and they are there to last for very long time. Look at GCC, it is there since a very long time and probably it will exists for a very long time since it is a valuable resource for everyone working with computers. The same is also true for emacs, python, yacc, linux and a lot of free softwares of excellent quality.

So, what I want to say is that, if you work on linux probably you have to make some compromise and sometimes you have to work with non-optimal tools but the idea is that the freedom has no price and with some perseverance you can achieve much better results than on proprietary platforms because ***knowledge and best practices are always shared***.

So, keep on going with linux, the future belongs to us! :D

Francesco

---

### Post by albertz on 2009-05-25
Funny thread. :) Even more funny that the people are talking about IDEs and text editors and mostly having different things in mind.

Can somebody give me a definition for a text editor and an IDE?

Because, for example, I would call Vim, Emacs or similar rather an IDE than a simple text editor. nano or pico is a text editor for me.

For me, an IDE is a tool which can interact with other tools (such as GCC, make, ctags, and much more) and has the ability to edit code, with advanced features like code completion and syntax highlighting. It also can show a list of files and you can save a session of files/settings (for example, that when you click debug, it automatically compiles your program via make+gcc and starts it via gdb).

To the topic itself:

I mostly prefer KDevelop for C and C++ work. The main reason I do is because that is the only code completion who fully understands and works with my C++ code. And code completion is something very important for me, you are just much more productive by using it (esp in a project with 200k lines of code). Important is also that KDevelop is very fast, I don't really feel any performance problems with very big projects (it feels just as fast as the simple KWrite).

I also have done some work in Object Pascal in the past - a very powerfull language which has a very powerfull and fast compiler, FreePascal. It's a bit sad that this language become more and more forgotten. There is the very nice Lazarus IDE for FreePascal, which itself is very similar to Delphi (just works in the same way). The code completion has also worked mostly very good for me.

If you are open to a new language, perhaps Object Pascal, or esp Lazarus is worth a look. I feeled very productive while working with it because everything is very much straight forward. And FreePascal supports all major architectures and Lazarus itself supports most important GUI frameworks (GTK, GTK2, Win32, Qt, Carbon(MacOSX), raw bitmaps, and some more; even a CGI interface).

For Python, I know there is the Eric IDE. I haven't done much work with it yet, though.

For Java, I mostly use Eclipse, whereby I don't like it that much (it's very slow). There is also Netbeans but I haven't tried that one yet.

KDevelop also supports a lot of other languages, for example OCaml, Haskell, etc. - whereby I don't know how good that support is. It will have at least syntax highlighting but no idea about code completion (whereby I also don't know any other IDE esp. for OCaml or Haskell).

---

