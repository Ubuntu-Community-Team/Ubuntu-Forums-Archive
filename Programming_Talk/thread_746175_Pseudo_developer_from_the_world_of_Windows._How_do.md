---
title: "Pseudo developer from the world of Windows. How do I proceed?"
date: 2008-04-05
forum: Programming Talk
---

### Post by alliterationArtiste on 2008-04-05
Hi all. I have around 30 years experience in IT. Virtually all of it in Windows. Got a love of Xenix on an old Altos system about twenty years ago but Bill was where the money was so I never followed it up.

Well I think Ubuntu is just about ready to take over the world and I would like to contribute. Selfishly I suppose I would like to code solutions to my specific issues - namely integrating my Sony-Ericsson phone.

My question is really how to proceed. I have been coding for years, firstly as an amateur but did an Open University degree in Information Technology and Development so I know the *theory* of software design. I routinely code in C# but started out in C and later C++ but that was many years ago.

There are gaps in my knowledge because of the piecemeal nature of my learning curve. e.g. I didn't really understand the memory management concept in C (or lack of it) for years and had memory leaks galore as a result.

I'm aware that I probably need to get to grips with the OS first. Things are intuitive for me in Windows and the struggle I have in Linux breeds some resentment which I have to fight to overcome. I hate being *just ordinary* again. Some guidance on basic Linux operation would be useful. Specifically on the startup process and how the hell devices work would be a good place to start. Anyone recommend any good web sites?

Conceptually I grasp the OS courtesy of my Xenix days. xWindows is still a closed book (didn't have it on on the Xenix flavours I used!) and that is scary. I played with Ubuntu using the server version first before I felt brave enough to try something with X in it.

All my development experience (console based) was in Borland C++  then a big break (ten years) before diving into C# and the world of windows programming.

It seems to me that C# hides the detail of actually creating windows from the developer. The only experience of Windows programming in C++ I have is reading a piece of code to pop up the ubiquitous 'hello world' window which was several pages of code. Put me right off!!

I can also code in Java (did this in Websphere) and use Javascript quite a lot.

So three specific questions:

What should I learn to develop in the wonderful world of Linux? People talk python, perl (scripting languages?) of which I have no experience. Worth dusting off my K&R books?

After question 1, what tools do I need to develop with? Again my Borland/.NET worlds have pretty integrated systems in which I write code and press the compile button. I get the feeling that it's not so *elegant* in Linux :)

Ideally I would like to be able to develop code that will travel nicely between Windows and Linux. Java springs to mind here but I know it can be limiting (thinking of my phone integration thing here) when it comes to talking to hardware.

I'm not averse to learning new languages given the constraints mentioned above. During my degree course I spent a year with Smalltalk and loved it. Objective C looks interesting but seems to have a strong mac flavour to it which covers neither Windows or Linux!

Any advice and direction would be greatly appreciated.

aa

---

### Post by Zugzwang on 2008-04-05
> **alliterationArtiste said:**
> 
What should I learn to develop in the wonderful world of Linux? People talk python, perl (scripting languages?) of which I have no experience. Worth dusting off my K&R books?

Usually you'll be most productive with the stuff you already know. So you can use C++ and use some multi-platform toolkits, like QT or wxWindows. This will make your programs compile on Linux, Windows, and also Mac (Don't know if that's true for QT as well).

> **alliterationArtiste said:**
> 
After question 1, what tools do I need to develop with? Again my Borland/.NET worlds have pretty integrated systems in which I write code and press the compile button. I get the feeling that it's not so *elegant* in Linux :)

Ok, so most people here would state that you need know how to run/compile programs from the command line before using IDEs like Borland C++ Builder and Visual Studio in Windows. The reason is that one of the key philosophies in Linux is that "everything" consists of small pieces that are plugged together to work. So the way you organize your programming here is normally fundamentally different. Someone else will be able to point you to good books which cover Makefiles/Compile tools/automake/etc. to get you started if you want to go this way. Alternatively, stick with Java.

In Borland C++ Builder, for example, you never had to care about compiler options and so on, here you have to because the IDEs are just frontends to the compiler so you occasionally get errors which you can only solve if you know what happens behind the scenes.

> **alliterationArtiste said:**
> 
Ideally I would like to be able to develop code that will travel nicely between Windows and Linux. Java springs to mind here but I know it can be limiting (thinking of my phone integration thing here) when it comes to talking to hardware.

Certainly true. But most hardware functions you can access with command line tools, too (if speed isn't crucial, like in 3D games or so). Your Java programs could use those.

Another option is to learn programming totally from scratch and conform to the usual habits in Ubuntu. In this case you might want to look into Python.

Oh, you can still use C# in mono. There are also portable GUI bindings you might want to consider. This is another option.

---

### Post by pmasiar on 2008-04-05
For phones, there are open frameworks, OpenMoko and Android. Android is Google's own reimplementation of Java (and this time, done right), not sure what OpenMoko uses. I know that Nokia uses Python a lot.

If you liked Smalltalk, you may like Python a lot - same dynamic typing (but no IDE - IDLE does nto compare). There are other editors, I use free SPE, there are many paid IDEs.

In any case, you don't need to learn too many scripting languages, they are all equivalent. Perl is widely used but becoming obsolete (hard for really big programs), Python is replacing it. Ruby is another "new kid on the block", even more "everything is an object", but not as widespread as Python (and developed in Japan).

All those "scripting" languages have memory managed by garbage collector, so you shold relax. :-)

Linux has "embarrasment of the rich" - many many tools and projects, and unlike proprietary companies, projects want to be compatible, and link to other projects in same area (to pick their brain and features of course :-) ).

Python is language you can use for 80% of generic work, beyond 5 lines of bash, and it's source is quite portable. Usually is fast enough (so you can program high level, without type Nazis harrasment), and easy to extend in C.

Bottom line: find a project you like, and learn the language they use. :-)

---

### Post by alliterationArtiste on 2008-04-06
Thanks for the info guys. wxWindows looks interesting as does the python/pearl tie-in. And thanks for additional info on phones. However I've just hit a new snag. Went to import my contacts into evolution and couldn't. I think there's scope there for a more configurable import. Perhaps in the form of a plugin. This might be a good place to start. Your comment about picking a project and learning their development code sounds like a good one. Might have a sniff around the Evolution site and see if I can do a plugin that would make contact imports easier.

Interesting that nobody mentioned objective C :)

Off to play. Thanks for the pointers...

---

### Post by pmasiar on 2008-04-06
> **alliterationArtiste said:**
> However I've just hit a new snag. Went to import my contacts into evolution and couldn't. I think there's scope there for a more configurable import. Perhaps in the form of a plugin. This might be a good place to start. 

Yup. This looks like best start: you know what you want to do, so you can focus - and when (and if) you have some result, your code could accepted and help others. Scratch your own itch - and build from there. :-)

---

