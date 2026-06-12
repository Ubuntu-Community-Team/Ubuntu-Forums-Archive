---
title: "Honest Opinions Needed Regarding C#"
date: 2007-05-15
forum: Programming Talk
---

### Post by jlacroix on 2007-05-15
Hello everyone!

I've not talked about programming here before but it is something I enjoy even though I don't know as much about it as I would like.

I've only ever programmed on Windows. As things are right now, I have a small Windows XP partition for programming and my Ubuntu partition does everything else. 

The reason why I program is to design games. I'm using a tool right now called "Game Maker" (which some of you may be aware of) and have fun with that.

Microsoft recently released their XNA SDK, and I've heard good things about it and gave it a try, I ordered a few books to learn C# and I absolutely love that language. It's a ton of fun for me and I enjoy it.

Eventually I want to design something cross platform. It would be real sweet if I designed a game that ran on Ubuntu also, and that got me thinking, C# is basically a Microsoft language, right? Now I'm afraid to get too attached. I want to program with C# but want to do so in a way that I can make Ubuntu software too.

So I guess I could consider learning a second language or I could find a way to make C# work for me with Ubuntu also.

If I learn a second language, which one should I learn that's versatile for 3D or 2D game development? Is C# "Ubuntu Friendly" enough for me to just stick with that? (Since I already know I like the language). If I chose to learn a second language, learning one is hard enough, how do some of you juggle multiple languages without mixing up the syntax?

Sorry I wish my questions were more structured. I'm hoping to reach a resolution so I can continue studying.

---

### Post by Jussi Kukkonen on 2007-05-15
> Eventually I want to design something cross platform. It would be real sweet if I designed a game that ran on Ubuntu also, and that got me thinking, C# is basically a Microsoft language, right? Now I'm afraid to get too attached. I want to program with C# but want to do so in a way that I can make Ubuntu software too.

C# the language is fine for many situations. What you need to be careful about are the libraries (the framework you are using): Check mono-project.com for information on which parts of the .NET framework have been implemented in mono. Be especially careful with stuff that deals with graphics.

> If I learn a second language, which one should I learn that's versatile for 3D or 2D game development?
Especially for 3D development, the question is often not about the language, it's about the 3D engine you'll be using... 
Anyway, there is no correct answer to you question: if you want code a 3D engine, you'll probably want to learn C, if you want to code the UI parts and use an existing game engine you might want to check out Lua... These two examples are from two ends of the spectrum, anything in between may also be prefect for some situations,
 Sorry I'm not more helpful, but that's the way it is.

> If I chose to learn a second language, learning one is hard enough, how do some of you juggle multiple languages without mixing up the syntax?
It's not that difficult, actually -- just like knowing swedish rarely makes me mix english and swedish. Then again, knowing the syntax is only a tiny part of being a good programmer.

---

### Post by kknd on 2007-05-15
> **jlacroix said:**
> Hello everyone!

I've not talked about programming here before but it is something I enjoy even though I don't know as much about it as I would like.

I've only ever programmed on Windows. As things are right now, I have a small Windows XP partition for programming and my Ubuntu partition does everything else. 

The reason why I program is to design games. I'm using a tool right now called "Game Maker" (which some of you may be aware of) and have fun with that.

Microsoft recently released their XNA SDK, and I've heard good things about it and gave it a try, I ordered a few books to learn C# and I absolutely love that language. It's a ton of fun for me and I enjoy it.

Eventually I want to design something cross platform. It would be real sweet if I designed a game that ran on Ubuntu also, and that got me thinking, C# is basically a Microsoft language, right? Now I'm afraid to get too attached. I want to program with C# but want to do so in a way that I can make Ubuntu software too.

So I guess I could consider learning a second language or I could find a way to make C# work for me with Ubuntu also.

If I learn a second language, which one should I learn that's versatile for 3D or 2D game development? Is C# "Ubuntu Friendly" enough for me to just stick with that? (Since I already know I like the language). If I chose to learn a second language, learning one is hard enough, how do some of you juggle multiple languages without mixing up the syntax?

Sorry I wish my questions were more structured. I'm hoping to reach a resolution so I can continue studying.

C# and .NET Framework is supported in Linux by the Mono project.

IMHO: I studding Java for one year, and I was learning something of C# (the syntax and style are 75% like Java, so it was more easy to learn the basics).

C#, for me, its a Java + Cpp  (bloated) mix. Its a nice language, but currently the number of docs, users (mono) and tools do not favor C#.

My other opinion: There is a lot of programming languages out there. Its not the language that make a good developer! Choose one that you like, and go on!

---

### Post by seamless on 2007-05-15
Since you are looking specifically at making games keep your eye on [http://code.google.com/p/monoxna/]("http://code.google.com/p/monoxna/") which just like Mono is an open implementation of .Net, MonoXNA is an open implementation of XNA. With C# and XNA, as long as you stay within in the frameworks, will allow your game to run on Linux and Windows. That is once Mono and MonoXNA are far enough along to facilitate this. Basically since you like and have experience with C# stick with it and be sure to check out Monodevelop if you decide to switch coding on Ubuntu.

---

### Post by pmasiar on 2007-05-15
> **jlacroix said:**
> The reason why I program is to design games. I'm using a tool right now called "Game Maker" (which some of you may be aware of) and have fun with that.

Yes, GM is *the best* introduction to programming games IMHO. 10 years old can create game and have fun doing it - no code at all!

> Eventually I want to design something cross platform. It would be real sweet if I designed a game that ran on Ubuntu also, and that got me thinking, C# is basically a Microsoft language, right? Now I'm afraid to get too attached. I want to program with C# but want to do so in a way that I can make Ubuntu software too.

So I guess I could consider learning a second language or I could find a way to make C# work for me with Ubuntu also.

If I learn a second language, which one should I learn that's versatile for 3D or 2D game development? 

Best crossplatform combination for games is IMHO Python and Pygame -  library for programming games. When you need speed, you can reimplement bottleneck (found not by guessing but by profiling) in C, it's easy to link.

If you like GameMaker, and are interested in nice project, I would like to talk to you about implementing GM in Python/pygame. It would be something *very* cool to have on $100 laptop, WDYT? Msg me if interested.

> Is C# "Ubuntu Friendly" enough for me to just stick with that? (Since I already know I like the language). If I chose to learn a second language, learning one is hard enough, how do some of you juggle multiple languages without mixing up the syntax?

IMHO C# will always be 2nd citizen in Linux. Even with Mono, it is hard to try to catch up with Microsoft: they have couple thousands very smart and dedicated developers working on new features and pretty IDE full time. C# is just slightly improved Java with incompatible libraries. Also, many developers say that beyond Java, FOSS has C, C++, D and bunch of RAD languages like Python and Ruby, we do not need new language like C#. Especially language with potential patent issues. Patent issues might fizzle, but many people just do not see why even take the risk?

I added bunch of links to [my answer](http://ubuntuforums.org/showpost.php?p=2663382&postcount=26) in thread [ What language is used in the professional world](http://ubuntuforums.org/showthread.php?t=443418) which are relevant also here

---

### Post by jlacroix on 2007-05-17
Thanks everyone! From reading about Mono I think I will stick with C#. Are there any good online documentations that I could read that are compatible with Mono? If I focus on Mono, it seems that I should be fine for cross platforming.

I read all of your replies, I couldn't reply until now because I've been having a hectic IT work-week so far. Sorry guys, but I do appreciate all of you taking the time to post in my thread.

I'm designing a game in Game Maker that I'm really excited about, I wonder if it would be possible to hack it and convert it to Linux when I finish it? That would be the best thing ever.

I think what I've decided is to learn C# as much as I can and then add another language on. I've been looking at Ruby. I don't know why but Ruby seems cool to me but I know nothing about it. I'll read the documentation in this forum to learn more, when it comes time for me to add another language. Are you guys fluent in it? What do you think?

You guys rock!

---

### Post by yatt on 2007-05-17
> **jlacroix said:**
> Thanks everyone! From reading about Mono I think I will stick with C#. Are there any good online documentations that I could read that are compatible with Mono? If I focus on Mono, it seems that I should be fine for cross platforming.

I read all of your replies, I couldn't reply until now because I've been having a hectic IT work-week so far. Sorry guys, but I do appreciate all of you taking the time to post in my thread.

I'm designing a game in Game Maker that I'm really excited about, I wonder if it would be possible to hack it and convert it to Linux when I finish it? That would be the best thing ever.

I think what I've decided is to learn C# as much as I can and then add another language on. I've been looking at Ruby. I don't know why but Ruby seems cool to me but I know nothing about it. I'll read the documentation in this forum to learn more, when it comes time for me to add another language. Are you guys fluent in it? What do you think?

You guys rock!
You'd probably have to buy a book to learn C#. The how to start programming sticky doesn't even have an online tutorial listed.

---

### Post by seamless on 2007-05-18
> **jlacroix said:**
> Thanks everyone! From reading about Mono I think I will stick with C#. Are there any good online documentations that I could read that are compatible with Mono? If I focus on Mono, it seems that I should be fine for cross platforming
Any C# reference, tutorial or documentation that does not call native libraries should work with Mono. There are no 100% guarantees but 99% is close enough. Google search for C# tutorial or something similar and you can find plenty of documentation on line. Also MSDN has a wealth of knowledge. If there is anything Mono specific you need to look up then install monodoc (be sure to install the gui component) and you have access to all of the Mono documentation regarding C#.

---

### Post by emperon on 2007-05-19
We are doing a very complex project on mono here. I can say as of mono 1.2.4, it is quite stable. The only lacking issues are about MonoDevelop, that there is no functional debugger. Mono team says these will be fixed till the end of summer. 

For my personal opinion, I have experience with c, c++ , java , c#,, ruby , pyhton and perl. Ruby and Python are very joyful languages. Ruby has some problems with its unicode things and also it does use green threads. Python is also great but rather slow (usually you don't need speed though). I can clearly say syntax of Ruby and Python are far better than C#, but I still like C# , since it is a very disciplined language. If you want something between you could also try boo. It is a python like .net language. Oh yes there is IronPython now also. IronPython as of 1.1 works fine in mono. The problem with IronPython 1.1, that you cannot build dll 's and you cannot use attributes. That's pretty annyoing to me. There is a new IronPython release coming which is based on DLR. 

For java and C++, don't go there. they are ugly and bloated. java is currently the most popular programming language. But stupid Sun made it very bloated and ugly. It didn't develop java in the name of backwards compatibility. that's a lie. Look at linux kernel! Every few months we see a new kernel release , with brand new features yet it still works like charm.
,
For documentation, go through any .net book , and it will apply to mono

---

### Post by slavik on 2007-05-20
before it used to be that if you wanted to easily create windows apps, you used visual basic. now that there is a form designer for C# and C# code can be interleaved with visual basic.net code (by using libraries) (furthermroe, they are compiled to the same bytecode), I see not real reason for C# and visual basic .net to exist together.

IMO, C# is formely Java++ which was Microsoft's implementation of Java (in which they did 'bad' things for which Sun sued them).

EDIT: I also like GTK+ which worries about windows resizing (so I don't have to).

---

### Post by Game_Ender on 2007-05-20
C++ is anything but bloated.  All console games are written in C or C++ and they are very demanding in terms of resource usage and efficiency.  Also all the games developed by EA are in C++ and despite what you may think of there quality, they make a *ton* of games.  C++ is really the only language to use if you wish to have a high performance cross platform game, but it is not the best for beginners to get started in.

If you know C# already and are interested in game development, but would like to make a game that is compatible with Ubuntu you should stick to libraries which already run on Ubuntu (MonoXNA is pre-alpha and not very close to being usable).  For simple starter games SDL.NET which does run on both Windows and Ubuntu would be a good base to make 2D games with.

If you don't really know C# I would go with python as suggested above.  Once you have created some simple games with PyGame you can step up to the next level with something like Python-Ogre which has an entire set of cross platform libraries (coded in C++ but wrapped for python) for sound, physics, input and graphics at your finger tips.

---

### Post by jespdj on 2007-05-21
> **slavik said:**
> IMO, C# is formely Java++ which was Microsoft's implementation of Java (in which they did 'bad' things for which Sun sued them).

Before Microsoft came up with C#, they had J#, which was Java done the Microsoft way (i.e. the Java programming language with Windows-specific API's in addition to the standard Java API's).

The C# programming language looks a lot like Java, it's clear that they've borrowed a large part from Java.

---

### Post by jlacroix on 2007-05-21
Wow, thanks guys. Perhaps when its time for me to develop my first game using a real programming languages, I should post the source here and we can all work together on it to make sure it works on Ubuntu. :)

I'm excited about this. I'm currently designing a Game Maker game that I need to finish first.

---

