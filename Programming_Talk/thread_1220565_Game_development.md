---
title: "Game development"
date: 2009-07-22
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-22
What are the prerequisites of learning game programming.
what all languages are used,especially for big games like fifa?

---

### Post by c0mput3r_n3rD on 2009-07-22
Check [this]("http://www.cppgameprogramming.com/cgi/nav.cgi?page=index") out. 
:)

---

### Post by Sockerdrickan on 2009-07-23
> **nipunreddevil said:**
> What are the prerequisites of learning game programming.
what all languages are used,especially for big games like fifa?
C++0x, OpenGL 3.2, OpenAL and SDL 1.3

There, you go learn those and you'll have the next killer game for any platform. :popcorn:

---

### Post by SunSpyda on 2009-07-23
Java is getting big in this respect. Finally, Java has full full screen support, better game I/O support & the rest of it. C++ people pounce on Java's poor speed, but in reality Java is fast enough - and it's getting faster.

The fact it runs on many platforms, and can run within browsers in quite cool as well. But in reality, applets for real games doesn't work, and you really only need to target Windows OSes to get a good market.

But by using Java, you can make it work on most other platforms without code alteration. Hey presto, it works on Linux.

The libraries you would want for game development are already with the JRE. Except maybe *good* 3D graphics, which you can get many cross platform libs for like JOGL.

Okay, but let's say you want to use the language people are using *now*. C++, simple as. And using the C++0x would be better, as Tux0r said. You will have to go library hunting a lot more than if you used Java though. But C++ definitly has its advantages.

I only did a bit of hobbyist game development, so take my opinion with a vat of salt. I preferred Java when I was doing it. But I prefer C++ for nearly everything else.

---

### Post by JordyD on 2009-07-23
> **SunSpyda said:**
> Java is getting big in this respect. Finally, Java has full full screen support, better game I/O support & the rest of it. C++ people pounce on Java's poor speed, but in reality Java is fast enough - and it's getting faster.

Java is not (IMO, of course) be fast enough for *big* games. With small games you'll probably be able to get away with it, and it might be better to learn it the Java way and go to C++ when you start noticing slow games, since they're so similar. But larger games take up way too much CPU to even consider anything but C/C++. Maybe when computers get faster, which would probably make using languages like Java worth it (like the transition from Assembly to C, when games started needing less speed). Anyways, any application I've used that has been written in Java has been slow, so I have a bias against it.

> But by using Java, you can make it work on most other platforms without code alteration. Hey presto, it works on Linux.

Libraries like SDL and SFML make this possible with C++.

---

### Post by Mirge on 2009-07-23
Writing games in assembly could not have been fun... ugh lol.

---

### Post by JordyD on 2009-07-23
> **Mirge said:**
> Writing games in assembly could not have been fun... ugh lol.

:D I recently pressed the 'Show Assembly Code' button in XCode (Mac app) in a simple application. There were 16658 lines of Assembly. That was the point were I was thinking 'God, I'm glad I wasn't born during that time.'

**EDIT:** Now that I think about it, it could probably be lessened if you count the libraries I was using, which are definitely *not* simple. I only had 69 lines of code that I wrote myself.

---

### Post by SunSpyda on 2009-07-23
In all honesty though, Java only a short while back was laggy, slow and used to crawl. But it really has been getting fast (Many benchmarks are showing that's it's close behind C++... but I really doubt it.). But I have found that Java vs C++ speed isn't anywhere near as bad as implementing the wrong algrithm for putting textures on polygons.

All I'm saying, is that Java worked fine for something that the C++ people told me would definitly be slow in Java. I think the way games are programmed would have a far bigger impact to whether it is Java or C++.

Also, if the OP wants to make games single handidly (Which is a very hard task, as we all know) having a language like Java would help over C++. I know you can use cross platform libs in C++, but it is a hell of a lot more integrated and it works out the box on Java.

I prefer C++, but I think for hobbyist game development, Java is the winner. All my opinion though.

Java's poor speed is more due to poor coding then slow language performance these days. Java people say that C++ always has memory leaks due to no GC, but I know that a good C++ coder doesn't allow that to happen. Same thing with Java - C++ people say it's slow, but it's plenty fast enough now, and most bottle necks are down to the coder, not the JRE - But it's only recently been like this - but JRE's poor performance in the past seems to have stuck in people's minds.

---

### Post by nipunreddevil on 2009-07-23
> **SunSpyda said:**
> I prefer C++, but I think for hobbyist game development, Java is the winner. All my opinion though.

So at present c++ is pretty much the standard or c++0x,what about the future?Will Java still be thought as hobbyist gaming language

---

### Post by SunSpyda on 2009-07-23
Again, remember that all of this is my opinion, not fact. But I think C++ will start to lose ground to C#/Java over time - it's inevitable.

The thing is games are extremely complex and difficult to make. The higher level features in C# and Java will make it more appealing for game developers. GC, autoboxing, symbolic includes, more compile/runtime error checks, integrated libs and all the rest of it.

But for apps I wouldn't touch Java/C# - I personally don't need all those high level features for app coding. I like to have the power of C (With the inline ASM) with OOP, even if it is a little ugly - so C++ it is. But those little things that C#/Java take care of really shine when massive things like games get made.

---

### Post by JordyD on 2009-07-23
> **SunSpyda said:**
> In all honesty though, Java only a short while back was laggy, slow and used to crawl. But it really has been getting fast (Many benchmarks are showing that's it's close behind C++... but I really doubt it.). But I have found that Java vs C++ speed isn't anywhere near as bad as implementing the wrong algrithm for putting textures on polygons.

All I'm saying, is that Java worked fine for something that the C++ people told me would definitly be slow in Java. I think the way games are programmed would have a far bigger impact to whether it is Java or C++.

Also, if the OP wants to make games single handidly (Which is a very hard task, as we all know) having a language like Java would help over C++. I know you can use cross platform libs in C++, but it is a hell of a lot more integrated and it works out the box on Java.

I prefer C++, but I think for hobbyist game development, Java is the winner. All my opinion though.

Java's poor speed is more due to poor coding then slow language performance these days. Java people say that C++ always has memory leaks due to no GC, but I know that a good C++ coder doesn't allow that to happen. Same thing with Java - C++ people say it's slow, but it's plenty fast enough now, and most bottle necks are down to the coder, not the JRE - But it's only recently been like this - but JRE's poor performance in the past seems to have stuck in people's minds.

Maybe you're right. I've never used Java, because I don't like the slowness of the Java apps I've used, so I'm probably not the one to ask anyways.

I don't like the way Java is cross-platform. It means that everyone that uses your app needs to have the JRE installed. As far as I know, not many people do. If I ever installed a game that wanted the JRE, I would immediately be thinking "Ugh, why did they use that?"

On the other hand, I love the 'purity' of Java. Java is definitely OOP, and I like languages that know what they are. C++, on the other hand is like 'C with Classes'. It feels to me like a Frankenstein language; it doesn't know what it wants to be, it only knows that it wants to be more than C. Of course, that's all aesthetics, and it doesn't stop me from using C++ over Java.

---

### Post by JordyD on 2009-07-23
> **SunSpyda said:**
> Again, remember that all of this is my opinion, not fact. But I think C++ will start to lose ground to C#/Java over time - it's inevitable.

The thing is games are extremely complex and difficult to make. The higher level features in C# and Java will make it more appealing for game developers. GC, autoboxing, symbolic includes, more compile/runtime error checks, integrated libs and all the rest of it.

But for apps I wouldn't touch Java/C# - I personally don't need all those high level features for app coding. I like to have the power of C (With the inline ASM) with OOP, even if it is a little ugly - so C++ it is. But those little things that C#/Java take care of really shine when massive things like games get made.

I'd have to agree with this. As computers get faster, the need for C++ will be little. Higher-level languages will take over the Game Programming market.

---

### Post by Sockerdrickan on 2009-07-23
> **nipunreddevil said:**
> So at present c++ is pretty much the standard or c++0x,what about the future?Will Java still be thought as hobbyist gaming language
Java is not the hobbyist gaming language...

> **JordyD said:**
> I'd have to agree with this. As computers get faster, the need for C++ will be little. Higher-level languages will take over the Game Programming market.
Computers will get faster and games will get more advanced, C++ is not going anywhere.

---

### Post by Dullstar on 2009-07-24
What about Python?  There's even an extension for it called Pygame.

---

### Post by matmatmat on 2009-07-24
I think pygame is good for small games

---

### Post by Leslie Viljoen on 2009-07-24
Currently most games are written in C++ (as wasmentioned). C++ is hard work though, mostly because of the labour involved with doing your own memory management. Java can be fast, but since there's the extra bytecode interpretation step, not quite as fast as C++. Still, many smaller games, such as the ones running on cellphones, are written in Java. Check out [http://lwjgl.org](http://lwjgl.org) for a nice lib, and a gallery of games using it.

It is also possible to get the best of both worlds by using C++ to do heavy lifting and an easy, dynamic language to do the rest. PyGame takes that approach, though I don't think it offloads enough to the C++ layer. Even Quake had "quake C" so they could have a higher level layer of code. I am playing around with Ruby, Gosu and Chipmunk right now. I got a fast and fun little game going in a few hours and very few lines of code.

Here's one demo: [http://www.youtube.com/watch?v=FdNFJ5pO14g](http://www.youtube.com/watch?v=FdNFJ5pO14g)

---

### Post by jespdj on 2009-07-24
> **JordyD said:**
> Java is not (IMO, of course) be fast enough for *big* games.
Really, how do you know, are you still stuck in the "Java is slow" cliché which people seem to repeat over and over and over, even though hasn't been true anymore for years? Do you have proof that Java isn't fast enough?

I don't know any big 3D graphics games that have been programmed in Java, but I have seen some pretty impressive demos of serious software for tracking airplanes, which was written in Java, which contained a lot of graphics. That software had very high performance requirements, for example the screen had to be updated every so many milliseconds, and the people who were demo'ing it explained how they got it all to work in Java.

[JOGL](https://jogl.dev.java.net/) is the Java binding for OpenGL. The project page for JOGL contains links and screenshots to projects where it has been used, including a number of games.

> **JordyD said:**
> Maybe you're right. I've never used Java, because I don't like the slowness of the Java apps I've used, so I'm probably not the one to ask anyways.
That's probably because those apps where programmed badly, not because Java itself is slow.

> **Leslie Viljoen said:**
> Java can be fast, but since there's the extra bytecode interpretation step, not quite as fast as C++.
Java works with a just-in-time compiler. The Java byte code is compiled to native machine code on the fly, and that machine code runs just as fast as native code from a C++ compiler. In fact, it can in theory run even faster, because the just-in-time compiler can do certain optimizations using runtime performance data that an ahead-of-time compiler (which is used for C++) doesn't have.

---

### Post by Sockerdrickan on 2009-07-24
> **jespdj said:**
> Java works with a just-in-time compiler. The Java byte code is compiled to native machine code on the fly, and that machine code runs just as fast as native code from a C++ compiler. In fact, it can in theory run even faster, because the just-in-time compiler can do certain optimizations using runtime performance data that an ahead-of-time compiler (which is used for C++) doesn't have.
Then how come it does not?

---

### Post by CptPicard on 2009-07-24
The more interesting question about Java and things like games is the impact of the garbage collector on achieving a stable frame rate. But yeah, when it comes to things like game engine development, you probably want a language like C++ for it...

---

### Post by Leslie Viljoen on 2009-07-24
> **jespdj said:**
> Java works with a just-in-time compiler. The Java byte code is compiled to native machine code on the fly, and that machine code runs just as fast as native code from a C++ compiler. In fact, it can in theory run even faster, because the just-in-time compiler can do certain optimizations using runtime performance data that an ahead-of-time compiler (which is used for C++) doesn't have.

True, but could you really write Quake in pure Java? I don't know and I haven't seen anyone try anything like that yet. 

There's quite a detailed discussion of Java and graphics in the comments here:
[http://books.slashdot.org/article.pl?sid=07/07/11/147243](http://books.slashdot.org/article.pl?sid=07/07/11/147243)

---

### Post by CptPicard on 2009-07-24
> **Leslie Viljoen said:**
> True, but could you really write Quake in pure Java? I don't know and I haven't seen anyone try anything like that yet. 

Original Quake? Should be possible, even with a Java software renderer... but, that's not the point ofc... ;)

---

### Post by Sockerdrickan on 2009-07-24
Quake 3 was written in C by Carmack, how the hell did he manage to...

---

### Post by Leslie Viljoen on 2009-07-24
> **Leslie Viljoen said:**
> True, but could you really write Quake in pure Java? I don't know and I haven't seen anyone try anything like that yet.[]("http://books.slashdot.org/article.pl?sid=07/07/11/147243")

Here is an answer to my question: [http://bytonic.de/html/jake2_webstart.html](http://bytonic.de/html/jake2_webstart.html)
If you wonder about whether Java can hack it, give it a try.

---

### Post by JordyD on 2009-07-24
> **jespdj said:**
> Really, how do you know, are you still stuck in the "Java is slow" cliché which people seem to repeat over and over and over, even though hasn't been true anymore for years? Do you have proof that Java isn't fast enough?

> **jespdj said:**
> That's probably because those apps where programmed badly, not because Java itself is slow.

So, you're saying that the speed difference between Eclipse and Netbeans vs Code::Blocks is all because the people writing Eclipse and Netbeans are incompetent, and the Code::Blocks people were not?

I speak of just the text editing parts. I've used all three, and if I'm typing more than an inch a minute, the whole program hangs, while with Code::Blocks, it does not. I'm afraid to use 'backspace' in Eclipse. I'm also afraid to type my #includes.

And yet, the features I was using in both programs were the same: syntax coloring and code completion.

I'd like to believe that Java is no longer slow. I have nothing against it as a language, it's just that all the applications I use in Java are slow. I can hardly believe that all of them were from incompetent programmers.

---

### Post by jero3n on 2009-07-24
> **JordyD said:**
> I'd like to believe that Java is no longer slow. 
This is true. As long as modern computers are getting faster.

---

### Post by Can+~ on 2009-07-24
> **JordyD said:**
> I speak of just the text editing parts. I've used all three, and if I'm typing more than an inch a minute, the whole program hangs, while with Code::Blocks, it does not. I'm afraid to use 'backspace' in Eclipse. I'm also afraid to type my #includes.

Waaaait, did you used the Eclipse on the repository?

I remember having similar issues with older Eclipse (and cdt), newer versions solved that annoying problem with auto-completion.

---

### Post by JordyD on 2009-07-24
> **Can+~ said:**
> Waaaait, did you used the Eclipse on the repository?

I remember having similar issues with older Eclipse (and cdt), newer versions solved that annoying problem with auto-completion.

Um, yes, I always use the repos.

Err, I guess I'll try the one at eclipse.org, then?

---

### Post by Mirge on 2009-07-24
I use PDT 2.1.0 on a daily basis (am actually using it this second). I've used the latest CDT from the site... and I've used Code::Blocks too. Code::Blocks is faster for me. That said, I still prefer Eclipse over it. Maybe because I'm more familiar with it now and have gotten used to it. I don't know. Eclipse for me isn't THAT much slower... and it "feels" a lot better.

I don't know Java, don't really have any immediate plans on learning it. I've used some terribly slow Java apps in the past, but the same can be said about C++ too. A lot DOES depend on the programmer, but I would say overall Java is becoming quite a bit faster than it used to.

---

### Post by JordyD on 2009-07-24
> **Mirge said:**
> Eclipse for me isn't THAT much slower...

After using the latest Eclipse from their site, I'd have to agree with this. The latest Eclipse is definitely not slow anymore.

Anyways, that destroys much of my 'Java is slow' argument.

---

### Post by CptPicard on 2009-07-24
> **JordyD said:**
> 
Anyways, that destroys much of my 'Java is slow' argument.

Also, a lot of the "Java is slow" argument comes from the perception of slowness from Swing... as a number-cruncher, Java is not all that bad actually.

---

### Post by Reiger on 2009-07-24
Swing isn't very "responsive" but it isn't slow. It's a bit like talking to a person who mainly communicates through non-committal grunts or jerks and occasionally a full sentence. That person may very quickly understand what you want, and may produce answers fast; still: he or she doesn't give you the impression that he/she does which makes the whole process feel a lot more difficult than it actually is.

---

### Post by Leslie Viljoen on 2009-07-25
I find Netbeans to be the slowest editor of all. Visual Studio is much faster, running on Windows in a Virtualbox. Which is a pity because I really really like Netbeans and consider it the best IDE out there (once the VI mode is turned on of course). Its great for Ruby too.

---

### Post by LepeKaname on 2009-09-28
> **Leslie Viljoen said:**
> I really really like Netbeans and consider it the best IDE out there (once the VI mode is turned on of course).

I totally agree, Netbeans + VI is what made me like it even more. If you turn off some unnecessary auto-complete options (to manual), I have no problem of speed at all. I found CSS parser the only slow feature there.

I was working in the development of a 3D CAD tool with some 3D libraries and it was really smooth (of course, it didn't require so much processing).

---

### Post by grayrainbow on 2009-09-30
Why the Linux kernel is written in C? :)
If you look at really big game source code, you'll see a lot of stuff that simply are impossible in any interpreted language(read you must be an idiot to not using C/C++ for that).  Low level language give you extreme control over machine, that mean better user experience(yes that's mean more work for developers, but if you are laze in any case you are going nowhere with big game).
Considering the future and our desktops becoming super computers... [http://en.wikipedia.org/wiki/Deep_Blue_(chess_computer)]("http://en.wikipedia.org/wiki/Deep_Blue_%28chess_computer%29") this won't be possible in near 10 years in any language on desktops and there's only one way to go near it :)

P.S. The problem with cross platform languages(and OpenGL) is that they are not cross platform :) That's nothing new, there just need to be standardization(as everything in Linux), couse now not everything running on Ubuntu will run on SuSe for example.

---

### Post by TheBuzzSaw on 2009-09-30
I used to be a big Java fan, but I became frustrated with so many aspects that I eventually reverted back to C++. Frankly, I am happier using C++.

First off, the cross-platform magic of Java is easily achieved in C++. Not only are many C++ APIs cross-platform already, Java still requires tweaking to work on all three platforms. Despite the magical claims of Java "working everywhere", Java programs are *still* often distributed on a per-platform basis. In the long run (with complicated/large projects), you are going to have to tweak for each platform anyway. I decided I'd rather cut out the middleman (the JVM) in the process.

Second, I have beef with anyone who claims how "difficult" memory management is in C++. Sure, it is significantly easier in Java thanks to the garbage collector... but this has also resulted in some rather bogus programming. This idea of "unhook all pointers and let the JVM handle it" causes problems all over the place. Several Java games I have played slow down drastically after playing for a while because the JVM finally decides to clean up 500 MB worth of dead data. This can be overcome with tricks such as invoking the garbage collector early, but I feel much more comfortable handling the cleanup myself (especially when it comes to writing a very performance-sensitive game engine). With a little practice and discipline, you can eliminate all memory leaks early in C++. I suspect the claims against C++ memory management come from people who finished huge projects and then tried going back and plugging the leaks because yeah, that is next to impossible.

Third, if you want to make a quality product, then you *want* to deal with all the platform-specific issues. Rather than putting your faith into something you have minimal control over (the JVM), you can make low-level tweaks that ensure that the game performs equally well on all platforms. Granted, sometimes you are a slave to an API just as you could be a slave to the JVM, but I find that I can overcome API-specific issues. With the JVM, I'm essentially outta luck...

Not all the best games out there are written in C++, but I can assure you that they certainly are not written in Java. :)

(Plus, it's really nice when the end user is not required to install the JVM first. Fully compiled programs work right out of the box.)

---

### Post by jkysam on 2009-09-30
This discussion seems to have deviated from the OP's original question. Going back to it though:
What you need to know depends on what aspect of game development you are looking to work on. As many people noted here if you would like to work on the game engine focusing on C/C++ is a must. But aside from that be ready to spend a lot of time studying and working on data structures and algorithms related to computer graphics. These include mathematical tools and graphics concepts related to things like geometric modeling  anti-analysing etc... 
However, if you would like to work on the artistic design of the game, which a lot of people are, then learning how to use Maya, and 3DS is much more important.

If you are really interested in the idea try looking for open source projects that are developing games and see if you can pick up on what is happening and maybe help the development community for that game. Even if you don't help with the game engine development you can get a feel for what is involved in making a game. I just saw one today that seems really interesting and you might want to take a look at: [http://wildfiregames.com/0ad/](http://wildfiregames.com/0ad/)

---

### Post by Can+~ on 2009-09-30
> **grayrainbow said:**
> Why the Linux kernel is written in C? :)

Because it interacts with a different abstraction layer that a game shouldn't dare to touch?

> If you look at really big game source code, you'll see a lot of stuff that simply are impossible in any interpreted language **(read you must be an idiot to not using C/C++ for that)**.

I disagree. Scripting languages can do things pretty much anything of the things that lower level languages can in the context of game dev. 3D rendering, collision, etc. Are all problems that can be solved better on a higher abstraction layer, without having to deal with memory management.

Only the game engine should be written in C/C++ for that purpose, you can add bindings to another language, thus improving the addition of new features, without having to recompile the core. (UnrealEngine solves the problem that way, they've got their own language (UnrealScript) for that matter, or Blender with Python bindings). Having an abstraction also brings other advantages, being able to keep the game code intact even if the core changes.

The current problem with game development is that there's people that still have the solid idea that C++ is the only possible language to ever code games in and stick to that refusing to change, or even dare to add another abstraction layer to the solution, because they were spoon fed with the idea (probably started coding with the idea "I'll make my own game! Forum post: What should I use as a first language? Response: C++ of course; cycle repeats years later").

My hope is that, eventually, have well coded engines that we won't even have to touch them in the future, just modify them via higher-level abstraction and adapt to the future. An scalable system. I really hope that [Opengl in firefox]("http://people.mozilla.com/~vladimir/xtech2006/") really takes off to prove that point.

---

### Post by grayrainbow on 2009-10-01
Can+~
Yep, big games got their own specific scripts used by designers(not programmers!). Everything else > /dev/null

Back to the OP. What languages are used in games: C and C++, and for specific scripts most popular is lua. Forget about all non real life good wishes like python, java, etc. Feauture is...well consider standart gui programming... lazy people may use script for ui creation, smart people use drag&drop :)
So, if one want a job in gamedev industry or want to start his/her absolutly great game project C/C++ is what you need as beginnig, than graphics(expect a lot of low level stuff here for real 3D hardwer accelerated stuff), AI, physics, sound. And about PC games...remember that 1Gb of ram is not 1Gb of ram on PC whit 1Gb ram(on my machine Ubuntu get about 300Mb for normal use, expect in future this to be expanded), that mean that even your code size(not only algorithms and formulas in use), including .so(.dll), matters. And...yep, there's no real solution for Linux when it comes to games, so it will be great if someone go and make one(but it will need OS support as well) :)

---

### Post by CptPicard on 2009-10-01
grayrainbow, considering you're new here, check out [this thread]("http://ubuntuforums.org/showthread.php?t=851794") -- I get the feeling that this would be recommended reading  ;)

C/C++ have the benefit of runtime speed and hardware access, but that's about it really. The more you are able to push to higher-level programming languages, the better -- doing everything on the low level just for the sake of it does not glorify anyone's efforts. Besides, higher-level languages often allow for more interesting structure in the code itself, while taking care of the mundane, pretty much "manual" stuff automatically.

> 
lazy people may use script for ui creation, smart people use drag&drop

I am not really sure what you mean here. I would say lazy people use GUI designers which produce crappy code... a good scripting language GUI bindings allow for much more exact design. (Then again the way you design your GUIs is not bound to what kind of language you use)

---

### Post by grayrainbow on 2009-10-01
CptPicard, are you saying that interpreter usually produce garbage? :)
> **CptPicard said:**
> I would say lazy people use GUI designers which produce crappy code...
I know how much people love their language of choice and simply denied everything what is against it, but then...it's good people to speak for things they know, and since here the subject are games, actually big computer games...Are you familiar with the phrase "Do not rediscover a wheel!"? I was "killed" with that one(plus speed explanation) last time I propose to use python instead of lua in project. It's simple when it comes to games you'll use C/C++ even for the single reason - there's people doing this for 20years and that's the only way you can learn from them, with any other language you are on your own and going to rediscover a wheel a lot!(IMO pretty much for same reason Linux kernel has exactly 0 lines of C++ code :) ).

The problem with people who not programm frequently in low level language is that, it seems they froget how much system call cost(imagin if you do that from some lib binding), how much "great" exception handlig cost, what happen when you do dynamic bindings, etc. I write that once now I perephrase myself - if you wnat to know how your system realy works, you have to have your hands dirty. For the rest...there's all be some tools, script or drag and drop doesn't matter.

Anyway, one more thing about games: on Linux one obviusly will talk to X for graphics, for programming design preferable solution is data driven(not xml couse its slow), how you achieve it with low level language...well gtk is object oriented but plain C, and open source btw :)

P.S. If you are realy afraid of hard work with C, I suggest to use flash for games ;)

---

### Post by Reiger on 2009-10-01
> **grayrainbow said:**
> Why the Linux kernel is written in C? :)

The original Linux kernel was about as much I386 assembly as it was C (or at least Linus basically said it was that), and even today if you take out the assembly modules the whole kernel falls apart.

Also: fun fact, there is a Java OS which is an OS implemented entirely in Java save for a mini VM which is implemented in assembly (IIRC). As a consequence the Java OS is as much written in Java as Linux is written in C: the proverbial 99% of it is, but that crucial 1% of it is not.

> 
If you look at really big game source code, you'll see a lot of stuff that simply are impossible in any interpreted language(read you must be an idiot to not using C/C++ for that).  
> Low level language give you extreme control over machine, that mean better user experience(yes that's mean more work for developers, but if you are laze in any case you are going nowhere with big game).

Irrelevant since virtually all games use hardware abstraction layers such as SDL, or the DirectX libs. Precisely because you really don't want to muck about in the lower levels since it forces you to write code which will only run on a very platform specific lower level -- and while it may be true the Windows market is large enough for some, the combination of AMD 64 X2 5200+, ATI Sapphire X1650 Pro and onboard Realtek sound is probably a tiny fraction of that. We haven't, even, gotten to the demands of multiplayer games yet which typically involve low-latency networking.

Also: fun fact, IIRC AMD has Python bindings for its Atom BIOS allowing you to program ATI cards that have that BIOS directly in Python.

> 
Considering the future and our desktops becoming super computers... [http://en.wikipedia.org/wiki/Deep_Blue_(chess_computer)]("http://en.wikipedia.org/wiki/Deep_Blue_%28chess_computer%29") this won't be possible in near 10 years in any language on desktops and there's only one way to go near it :)

> P.S. The problem with cross platform languages(and OpenGL) is that they are not cross platform :) That's nothing new, there just need to be standardization(as everything in Linux), couse now not everything running on Ubuntu will run on SuSe for example.

Actually what you are talking about here is 99% dependencies: having the right versions of all the dependencies tends to solve most of those issues. That is what software requirements are for, and that issue is nothing specific to *nix either. Using cross-platform languages (those with proper standards & reference implementations) does not guarantee you 100% portability; but it does guarantee you a basic core you can rely on; hence why &#8216;POSIX&#8217; is so important for shells & boot scripts.

---

### Post by grayrainbow on 2009-10-01
OS written in suns copy of Lisp? Well, unfortunately for open source [http://channel8.msdn.com/Posts/Cosmos-the-C-OS-that-you-can-play-with/](http://channel8.msdn.com/Posts/Cosmos-the-C-OS-that-you-can-play-with/)
is much better. But after all people got similar toys from long time [http://en.wikipedia.org/wiki/Lisp_machine ]("http://en.wikipedia.org/wiki/Lisp_machine")
:)
Reiger, don't get too much in details, couse we easy can get to conclusion that without compiler optimization, there won't be any programs, except opcode ofcourse :) btw no one can escape from 512 :) But never mind, I like how you use "directly" and "bindings" in one sentence. In realyty beta testing software/hardware usualy comes with easy to use extensions, couse nobody will test it otherwise, espesially if its proprietary.
Back to programs...one single big, time critical, working application written in something different than C/C++(I guess in Fortran is possible) [https://www.llnl.gov/](https://www.llnl.gov/)
Btw have you ever try to use Eclipse C++ code asistance? Have you ever compare its enourmus speed with...kdevelop for example(I bet emacs+etags+cedet is much faster than Eclipse, nomatter that is mostly written in interpreted language as well).
About HAL...nobody say that game programm directly hardware(with some exceptions), just gamedevs get as much low level as possible(what your computer do when you watch movie on it?), simply couse that's the only way to go.
Depending on platform, software dependency are actually hardware dependency, and again sometimes depending on platform sofware dependency are unresolvable. And btw C++ is really height level cross platform language [http://qt.nokia.com/products](http://qt.nokia.com/products)
even with point&clicky gui creator :)

P.S. Notice that except my "absolutly amazing and right" thoughts there's some stuff that one can actually point and click in my post. Anyway. Good night

---

### Post by kumoshk on 2009-10-02
> **nipunreddevil said:**
> What are the prerequisites of learning game programming.
what all languages are used,especially for big games like fifa?

It depends on how you want to make it, and what kind of game you want.

If you know nothing now, you'll find that learning C++, OpenGL and all that will take some time to master&#8212;although in the long run, it's probably a good idea.

However, if you want something easier to learn, I'd recommend looking into Löve (uses Lua) and PyGame (a game library for Python). Löve is a lot faster than games with PyGame, though, and the games generally seem to be more stable; plus, it seems that it's even easier to use than PyGame. Löve isn't a library for Lua, but it's something made with Lua that you can use a form of Lua code within to create games.

Lua is used with games a lot (not just with Löve programming, but even in games like World of Warcraft and countless others you're sure to have heard of)&#8212;typically for game logic, configuration, etc. I'd recommend learning Lua if you're serious about games&#8212;it could save you a lot. It's a scripting language (granted a fast one), so you probably won't want to make the entire game in Lua if it's a resource-hungry game, as most new commercial ones seem to be. Lua blends with many other languages quite well.

I would recommend using LuaJIT instead of the normal Lua interpreter if you find that you need more speed (LuaJIT is a lot faster, although it may not be available on as many platforms).

I might also recommend looking into the D programming language. It's a lot like C++, only newer, cleaner and easier to use. Because it is newer, however, you may find some obstacles. However, you'll find a lot more information on how to learn game programming with C++ than D, I'm sure.

You might also be interested in something like FreeBasic for hobbyist purposes if you've done some BASIC programming in the past. It's a compiled language&#8212;so it's fairly fast (I'm not sure how it stacks up to C, though just about any language that compiles to native code will be fairly fast).

Just a note about Java. People often say it's unbearably slow, but you should know why they think that. Java is fairly fast, actually&#8212;however, the virtual machine takes forever to load, initially, it seems. So, you have a delay before it actually does anything, but when it does get to doing that stuff it does it 'fairly' fast (some think in some cases it's actually faster than C++, although I'm not sure what those cases are; I'm sure most of the time it's significantly slower, although it is faster than a scripting language, typically, discounting the delay; you don't find a huge delay like that in scripting languages, usually, so scripting languages will 'appear' faster on the surface, until you get to processing things in the millions).

---

### Post by CptPicard on 2009-10-02
> **grayrainbow said:**
> CptPicard, are you saying that interpreter usually produce garbage? :)

No. What would make you think so? Please elaborate.

> 
I know how much people love their language of choice and simply denied everything what is against it

Seems to me you're assuming things about me and putting words into my mouth. By last count I have been writing stuff in a couple of dozen languages, and am able to choose a tool that fits the job for practical reasons, but have admittedly always found higher-level languages very interesting for their combination of letting me work directly on the problem, the insights I get from them regarding the nature of programming itself, and the way they push the algorithmic manual labour onto the computer so that I can focus on applying my mind where it needs to be -- where the computer can't do work.

I would say I actually have a rather broad understanding of how programming works, and there is little I would actually just flat out "deny".

I sincerely suggest you read the thread I linked to, this sort of stuff is all covered there.

> Are you familiar with the phrase "Do not rediscover a wheel!"?

Indeed. This is why there should be libraries. But a lack of them rarely is a fault of a language's design, it's just a lack of people having written them :)

> there's people doing this for 20years and that's the only way you can learn from them, with any other language you are on your own and going to rediscover a wheel a lot!

Only a copy-paste programmer would "learn" from implementation-specifics like that. You learn the idea, then you're able to hopefully implement in some language, making use of however that language idiomatically would do it.


> 
The problem with people who not programm frequently in low level language is that, it seems they froget how much system call cost(imagin if you do that from some lib binding), how much "great" exception handlig cost, what happen when you do dynamic bindings, etc.

That is relevant only when it is relevant. In all programming, for pragmatic reasons, you need to understand the speed implications of whatever you're doing. In general though, I value in another programmer much more an ability to "see the big picture" than bit-twiddling skills... the former lets the programmer solve problems in pretty much any language.

Add to that that my own leanings are more towards algorithmics than hardware, you will understand that a constant-time cost of a system call is a bit of a triviality that becomes a problem if it becomes a problem -- profilers are for that :)

>  I write that once now I perephrase myself - if you wnat to know how your system realy works, you have to have your hands dirty.

This here is such an interesting question. I am in sort-of agreement -- a decent programmer needs an understanding of the workings of the whole stack. "The system" however is just one programming abstraction among many, and as such, it is one more suitable for a compiler than a human programmer...

> 
 For the rest...there's all be some tools, script or drag and drop doesn't matter.

If that were true then we'd have tools for automated programming. As it happens, they don't exist. The actual act of creating stuff is always by the human being, and the difference between, say, Python and C is nothing but programmatic stuff that is processable by the computer, that is, there's "boring crap" offloaded to the computer that it is perfectly good to handle, so that the interface to the human brain becomes richer and more productive.

> 
P.S. If you are realy afraid of hard work with C, I suggest to use flash for games ;)

You know, these kinds of provocations from C-fanatics are getting really old. I hope you folks at least got to know the people you come slapping before doing it.

---

### Post by grayrainbow on 2009-10-02
> Seems to me you're assuming things about me and putting words into my mouth. By last count I have been writing stuff in a couple of dozen languages, and am able to choose a tool that fits the job for practical reasons, but have admittedly always found higher-level languages very interesting for their combination of letting me work directly on the problem, the insights I get from them regarding the nature of programming itself, and the way they push the algorithmic manual labour onto the computer so that I can focus on applying my mind where it needs to be -- where the computer can't do work.
I don't see your mouth, so I don't put anything in there :)
Indeed, choosing the right tool for the job is why games are written in C/C++. If I'm going to check how many files in one folder are change after some date I'll definitely go with python not C(if I don't need that in the big application of course :) ).

> I would say I actually have a rather broad understanding of how programming works, and there is little I would actually just flat out "deny".
Is basicly denied by:
> Only a copy-paste programmer would "learn" from implementation-specifics like that. You learn the idea, then you're able to hopefully implement in some language, making use of however that language idiomatically would do it
Look, game programming is veeery different from web programming(no matter that it uses web stuff in some situations), its even different from image/animation  coding for programs such as Maya, 3D Max, Gimp, etc. Note, there's also shader languages not only C/C++(but it's not 20 years old :) ).

> Add to that that my own leanings are more towards algorithmics than hardware, you will understand that a constant-time cost of a system call is a bit of a triviality that becomes a problem if it becomes a problem -- profilers are for that :smile:
Well, system calls are not exactly constant time, but this is really very platform specific(most nobly it really depends when you do it)! That's one of the reasons among gamedevs to live phrase like "Are we going to use fast engine or platform independent one?".

> This here is such an interesting question. I am in sort-of agreement -- a decent programmer needs an understanding of the workings of the whole stack. "The system" however is just one programming abstraction among many, and as such, it is one more suitable for a compiler than a human programmer...
Well, "system" is not abstraction, it's just a word :) and we obviously put different meanings in it. Let's say that for me JVM is not a system, it's just a normal program, like my browser and any other program on my PC(OS is the one exception, but good for programming OS will give you chance to bypass it in some situations). Is it more suitable for compiler...I'm really in opinion that one should trust the compiler, but nomatter moder really advance compiler technologyes, what man can do is really imposible for machine(for now).

> If that were true then we'd have tools for automated programming. As it happens, they don't exist. The actual act of creating stuff is always by the human being, and the difference between, say, Python and C is nothing but programmatic stuff that is processable by the computer, that is, there's "boring crap" offloaded to the computer that it is perfectly good to handle, so that the interface to the human brain becomes richer and more productive
I have to repeat my self again: automated tools do exist, no matter how you call them, scripts, mathlab, drag&drop, spredsheers, etc. And these tools are in use all over the world by mathematisions, designers, artists, economists, etc. The difference between script and C is that with C one programm computer(in most general term), with script one programm onother person programm :) (Note that I'm compleatly agree with you that in some situations one should definetly use script not C/C++)

We really got far, far away from OP(a lot of fold is mine), but I hope that if someone is really interested in game programming can find something usefull, but most notably this will be much more of a help [http://www.gamedev.net/](http://www.gamedev.net/)

---

### Post by fallenshadow on 2009-10-02
Quick question.... for a small game which is better? 

Pygame or C++ with SDL. Take into account that I already have a bit of C++ experience but none of Python.

---

### Post by scragar on 2009-10-02
Really depends, pygame will drasticly improve your performance in writing it, even with little knowledge of python already, but then c++ offers such a high level of control and power.

Really I think pygame would be built faster, no matter how well you know C++, but that's not to say it's the best solution.

---

### Post by CptPicard on 2009-10-02
grayrainbow, first of all, we simply have a rather different view of what the truly important issues are. I again refer to the thread I linked to, this is a discussion I have participated in over and over again. We're in basic agreement regarding the need for runtime efficiency for the specific case of game engines, but probably not other matters.
> **grayrainbow said:**
> If I'm going to check how many files in one folder are change after some date I'll definitely go with python not C(if I don't need that in the big application of course :) ).

Actually, writing a "big application" completely from ground up hugging the hardware sounds unreasonable.


> 
... Is basicly denied by: ...


I really can't see how. As I said above, having a fairly flexible high-level understanding of your problem and its programmatic solutions will allow for a suitable implementation in any language. This is why having a handle on abstractions not available in C is useful, and exercising them in other languages is important. For example, it is interesting how even my C is very much influenced by how I would do things in Lisp. Actually, it seems to me that regardless of what actual language I happen to program in these days, I tend to think in terms of Lisp and then just force the target language to emulate... of course, if I did not have *technical* constraints, a lispish language would be all I'd ever need for the expression of the actual computational process. Rest is unimportant detail.

> 
Look, game programming is veeery different from web programming(no matter that it uses web stuff in some situations)

Who said anything about web programming? It's the most code-monkeying programming I can think of. Of course, a well-designed general purpose programming language will probably also be a good web application development language....

> 
Well, "system" is not abstraction

It always is an abstraction. From the program's perspective, there really is nothing but the definition of the execution rules of the language. This is why stuff like functional programming is very interesting... it shows that mechanistic computation (that is, according to algorithmic rules) can be viewed in fairly high level terms. Rest is, again, something that can be relatively trivially offloaded to the computer.


> and we obviously put different meanings in it. Let's say that for me JVM is not a system, it's just a normal program, like my browser

No. They all are Turing-equivalent execution environments. They have the same theoretical capabilities and limitations, and it is up to the human programmer to really "breathe life" into them just the same. Some environments simply are less actively annoying than others.

>  Is it more suitable for compiler...I'm really in opinion that one should trust the compiler, but nomatter moder really advance compiler technologyes, what man can do is really imposible for machine(for now).

Your error here is thinking that not using the compiler is fundamentally superior to using a compiler. Personally I do not really consider random asm-level hacks to be of real importance, and doing the rest as matter of principle would be drudgery. They are bits of trivia, but in the end, the compiler produces a provably fully equivalent code transformation from a more abstraction-friendly format to a form that is less so. Give me a good high-level language such as Lisp and I can always produce a much better compiler using Lisp, for... say, Lisp. Or anything else. (For reference, SBCL is pretty much written in Lisp itself)

> 
I have to repeat my self again: automated tools do exist, no matter how you call them, scripts, mathlab, drag&drop, spredsheers, etc.

No, there is no "automated programming", this is an impossibility as per the halting problem. You can have very specialized languages, but they can end up being not Turing complete, or only so in a very contrived fashion (see XSLT, C++ templates).

> 
 And these tools are in use all over the world by mathematisions, designers, artists, economists, etc.

There's nothing wrong with bring the programming interface closer to the representation to the human that is actually using it. In particular, for programmers, you want a general purpose programming interface that is the most flexible for actually representing computational processes. Whether this actually is as close to the hardware as you seem to think is very much questionable IMO :)

> 
 The difference between script and C is that with C one programm computer(in most general term), with script one programm onother person programm :)

Programming languages are supposed to represent programs. I am all for having a programming language that communicates as efficiently as possible about whatever I am programming to a fellow other human being!

---

### Post by grayrainbow on 2009-10-02
Not very quick answer:
fallenshadow, as kumoshk already pointed - use lua :)

CptPicard, seems we are really on different opinions...for me Lisp is pretty much as...C++0x(full of stuff that I won't use), you should think of therms of Scheme :P And btw remember that Turing machine by definition may need unlimited resources. But programmers always like to cheat [http://en.wikipedia.org/wiki/NP-complete](http://en.wikipedia.org/wiki/NP-complete)
In games one cheat a lot(that's one of the best programming thing IMO :) )

---

### Post by Khushboo_khan on 2009-10-08
i think C++ and java becouse game programing is very easy in that.

---

### Post by kumoshk on 2009-10-08
I just wanted to add something to my previous post that I didn't know to suggest then.

Try using Vala. It's an awesome language. Very flexible and easy to use. You can use SDL and OpenGL on it, and making GUI applications with GTK is really easy.

Anyway, the vala compiler compiles all your code into C code and then to native code (small, fast executables).

Anyway, do yourself a favor and try it out.

---

### Post by kayosiii on 2009-10-09
Ok - I work with game engine technology as my day job....

Heres a break down... 
Most game engines (for big title games) exist in two layers. The graphics engine and the game logic layer.

The graphics engine is pretty much always written to run as close to the hardware as possible. That means C++ or C and maybe assembler where it makes sense. It also means making use of a hardware API like OpenGL or DirectX. In this case Automatic Garbage Collection is really not optimal for the way that this stuff works and highly optimised manual memory management is a requirement (its usually a fairly simple and brute force scheme - memory efficiency is usually sacrificed to avoid fragmentation as memory latency is important. 

I can't see a language like java or C# being a serious choice for this part of the engine for the forceeable future. For some genres of game though getting the best performance out of the hardware is really not an issue and higher level languages are just fine.

On top of the graphics engine is layered a high level scripting language that runs the game logic, I have seen Lua used for this purpose also python - at the moment I work with something that is basically an interpreted c.

For modern games though the creation of assets is really even more important than the programming. And consumes much time and effort. You pretty much want to have team. 

If I was going to try to create a game... My first stop would probably be the blender game engine (it's part of blender)... Go to apricot.blender.org for a really good sample game. After that I would probably look at working on some of the existing open-source engines openscenegraph (is highly regarded and used by quite a few projects) also ogre and crystal space.

---

### Post by SunSpyda on 2009-10-09
Sorry for being a little off topic, but why are people so obsessed with a specific layer of abstraction?

Saying that C is used in kernels, so its OO brother must be better at games than languages like Java or Python, is trying to paint all problems with the same 'abstraction paint'.

Need low-level, portable(ish) code, with little overhead? Then languages like C are the answer. Need a large game with loads of libraries required, solid OOP, & more abstraction? Java & C# is the modern world are probably more viable solutions.

This is all reminding me of stories of ASM coders who used to mock C coders, saying it was to slow for games. Deja vu...

Also, the 'JRE dependency' argument is pretty much dwarfed by the compatibility, dependency & portability problems faced by C++ projects when things like game programming is concerned. Has any C++ coder even entered the wonderful world of Java game programming, where so much of the game can be done using nothing but standard Java SE libraries? To duplicate the functionality of the JFCs for games, C++ coders would have to tie in their code to many, many dependencies, making the game as a whole, far harder to distribute vs the Java game with a JRE. Perhaps the JFCs can be rough round the edges, but I still think they're better than the equivalent C++ libraries, provided by different companies, not designed to work with one another, & many of which won't be on as many platforms as the JFCs.

I've also noted a trend. The C++ coders who believe it's a end-all language seldom know anything lower level, & usually can't read ASM code. This is all ironic, considering it's usually those types who accuse people like me of not operating at a low enough level by using languages like Java.

---

### Post by TheBuzzSaw on 2009-10-09
> **SunSpyda said:**
> I've also noted a trend. The C++ coders who believe it's a end-all language seldom know anything lower level, & usually can't read ASM code. This is all ironic, considering it's usually those types who accuse people like me of not operating at a low enough level by using languages like Java.
I know you weren't referring to me, but I am here to counter your argument. :)

I do believe C++ is infinitely more useful than Java, but I *can* read ASM code, so at least I can back it up.

As I mentioned earlier in this discussion, my beef with Java is that the compatibility dream is just that: a dream. Very rarely do I see large projects result in a single JAR file that people just pass around amongst operating systems. Often, I still see three distinct releases: a Windows release, a Mac release, and a Linux release. To me, that defeats the whole point of using Java. If I have to address OS-specific problems anyway, why am I using Java? I may as well just use C++, see some performance gains, and avoid dealing with the middleman (the JVM in this case).

I used to be a huge Java fan, but I ran into those exact issues. Different operating systems have different quirks that have to be addressed. I find that C++ grants me much finer control over these issues. In Java, I am a slave to the JVM's whims/limitations imposed as Sun sees fit.

---

### Post by shadylookin on 2009-10-09
Well I guess it's already been answered a billion times, but most games are written in c++. I've heard that some are switching to c# now however. It might also be worth looking into objective-c if you want to build a game for mac or iphone. 

> **TheBuzzSaw said:**
> I know you weren't referring to me, but I am here to counter your argument. :)

I do believe C++ is infinitely more useful than Java, but I *can* read ASM code, so at least I can back it up.

As I mentioned earlier in this discussion, my beef with Java is that the compatibility dream is just that: a dream. Very rarely do I see large projects result in a single JAR file that people just pass around amongst operating systems. Often, I still see three distinct releases: a Windows release, a Mac release, and a Linux release. To me, that defeats the whole point of using Java. If I have to address OS-specific problems anyway, why am I using Java? I may as well just use C++, see some performance gains, and avoid dealing with the middleman (the JVM in this case).

I used to be a huge Java fan, but I ran into those exact issues. Different operating systems have different quirks that have to be addressed. I find that C++ grants me much finer control over these issues. In Java, I am a slave to the JVM's whims/limitations imposed as Sun sees fit.

Java provides automatic gc, large standard library, easier syntax, fewer runtime issues, and better exception handling. 

Don't want to start yet another language war, but java brings more to the table than just pseudo-cross platform compatibility. I wouldn't use it for a "big game" however.

---

### Post by SunSpyda on 2009-10-09
> **TheBuzzSaw said:**
> I know you weren't referring to me, but I am here to counter your argument. :)

I definitely wasn't :) Y'know the sort I'm on about... they have been using C++ for 2 weeks & they think it is the solution for all the programming problems under the sun.

> **TheBuzzSaw said:**
> 
I do believe C++ is infinitely more useful than Java, but I *can* read ASM code, so at least I can back it up.
I agree with you. C++ is definitely more useful. But I'm talking exclusively about games here. Just for the record, I'm more of a C++ guy than a Java guy, but I'm personally convinced that C++ will be taken over by Java or C# for game programming. Just an opinion though.

> **TheBuzzSaw said:**
> 
As I mentioned earlier in this discussion, my beef with Java is that the compatibility dream is just that: a dream. Very rarely do I see large projects result in a single JAR file that people just pass around amongst operating systems. Often, I still see three distinct releases: a Windows release, a Mac release, and a Linux release. To me, that defeats the whole point of using Java. If I have to address OS-specific problems anyway, why am I using Java? I may as well just use C++, see some performance gains, and avoid dealing with the middleman (the JVM in this case).
 Personally, I have never had a issue with this. I made sure I didn't hit portability traps when using it. Also, isn't most of the different versions just different native installers to make setting up easier? I don't think the actual Java bytecode itself is very different on the different platforms.

> **TheBuzzSaw said:**
> 
In Java, I am a slave to the JVM's whims/limitations imposed as Sun sees fit.
That's pretty much a given with any interpreted language though. And the mainstream will certainly be using interpreted languages in the future over compiled-to-machine-code ones. So us native-language fans should at least get used to it :)

---

### Post by TheBuzzSaw on 2009-10-09
> **shadylookin said:**
> Java provides automatic gc, large standard library, easier syntax, fewer runtime issues, and better exception handling. 

Don't want to start yet another language war, but java brings more to the table than just pseudo-cross platform compatibility. I wouldn't use it for a "big game" however.
I would argue that automatic GC is a crutch in many situations. The libraries and syntax are indeed nice. Those are some of the big reasons I miss coding in Java, but I find myself happier coding in C++ in the long run.

> **SunSpyda said:**
> I definitely wasn't :) Y'know the sort I'm on about... they have been using C++ for 2 weeks & they think it is the solution for all the programming problems under the sun.
Yeah, I knew what you meant.

> **SunSpyda said:**
> I agree with you. C++ is definitely more useful. But I'm talking exclusively about games here. Just for the record, I'm more of a C++ guy than a Java guy, but I'm personally convinced that C++ will be taken over by Java or C# for game programming. Just an opinion though.
I can easily see Java and/or C# stepping up the realm of lower end games (I love 2D games in particular). As they become more accessible to more people, the numbers will clearly favor those languages. That's why I am glad to be part of the C++ elite! :P

> **SunSpyda said:**
> Personally, I have never had a issue with this. I made sure I didn't hit portability traps when using it. Also, isn't most of the different versions just different native installers to make setting up easier? I don't think the actual Java bytecode itself is very different on the different platforms.
For smaller projects, it's not an issue. It's when the project starts growing that you start to notice unusual discrepancies. I digress that C/C++ isn't free from this issue either. I've noticed that certain GTK apps run fabulously in Linux but rather pathetically in Windows (GIMP is a big one for me).

> **SunSpyda said:**
> That's pretty much a given with any interpreted language though. And the mainstream will certainly be using interpreted languages in the future over compiled-to-machine-code ones. So us native-language fans should at least get used to it :)
I certainly hope not. Compiling bridges that gap between human-readable and machine-readable. Interpreted languages force the computer to behave like a human, and I hate that. XD

Personally, I will hang onto compiled languages as long as possible. Granted, I am a CS major who can handle working at that level. I don't expect the majority to work that way, but I will cry the day compiled languages die. :(

---

### Post by shadylookin on 2009-10-09
> 
I would argue that automatic GC is a crutch in many situations. The libraries and syntax are indeed nice. Those are some of the big reasons I miss coding in Java, but I find myself happier coding in C++ in the long run.


I don't really see how it's a crutch. It's not as if there's a group of Computer Scientists that awards points to people who work unnecessarily harder to complete a task. I know the GC can be a hassle on high performance games because it gets called whenever it pleases(unless you specify otherwise)

---

### Post by TheBuzzSaw on 2009-10-09
> **shadylookin said:**
> I don't really see how it's a crutch. It's not as if there's a group of Computer Scientists that awards points to people who work unnecessarily harder to complete a task. I know the GC can be a hassle on high performance games because it gets called whenever it pleases(unless you specify otherwise)

That's my point. It is fairly unpredictable. Memory cleanup in C++ is not difficult. Yes, it is one more thing to watch out for, but the only people who complain about memory cleanup in C++ are the ones who create massive projects only to *then* go back and take care of the mess. By then, it is impossible.

---

### Post by kumoshk on 2009-10-09
> **SunSpyda said:**
> &#8230; Also, the 'JRE dependency' argument is pretty much dwarfed by the compatibility, dependency & portability problems faced by C++ projects when things like game programming is concerned. &#8230; To duplicate the functionality of the JFCs for games, C++ coders would have to tie in their code to many, many dependencies, making the game as a whole, far harder to distribute vs the Java game with a JRE. &#8230;

This doesn't look like a distribution issue, seeing as C++ games usually aren't distributed in source code form. It appears a matter of programming and/or compiling convenience.

Hmm. I'd rather have the programmers (who actually know how to do it) deal with dependencies than the users (who may, or more likely, may not&#8212;or even /more/ likely, may not want to bother). I think having one person/team/entity do all the work there, rather than countless, over and over again, is a good deal.

Now, with Java, I'm guessing you mostly just need what comes with the JRE, most of the time (at least, if it comes with such as OpenGL and SDL ports by default, which I'm not sure that it does)&#8212;so that's not /too/ bad. However, when dealing with languages like Python, this is a much larger issue (unless you distribute .so files with your program or something&#8212;although they're platform dependant, and that might defeat the purpose of using Python).

You have to keep in mind that Java (well, you did point this out, I guess), in and of itself, is a dependency, and that once compiled, something in C or such no longer has dependencies (unless you add them on purpose)&#8212;they're only there before the compiling.

Now, if you expect the programmer to embed all the extra libraries along with the JRE in the program so that the users don't have to, that's all well and good, but&#8212;hmm, I wouldn't expect anyone but very intense programmers to want to do that once they find how much work it is to get it to search the dynamic paths and all (i.e. you might have to recompile the JRE with certain parameters). It's not /that/ hard, I guess (at least with LuaJIT; I can't speak for Java), but it takes a lot of figuring out. But then, I guess we are talking about professional-grade games to a certain extent. To the rest of the extent, I'm talking about convenience (since that's what I thought you meant about the cross-platform/dependency issues). Another problem with such embedding is that if users use multiple programs like this, there's a lot of redundancy (i.e. lots of virtual machines instead of just the desired one).

On Ubuntu, I think this is /largely/ a moot point if the program is installed through a .deb package. Although you do have to enable the restricted repositories if you want to install Sun's Java /and/ have it be fully integrated with your OS (and not all users will want to do that). Python and such don't have that issue, though.

On Windows, users have to figure out more about paths when it comes to using external libraries, seeing as all the programs don't always know where the other ones are as they so often (not always) do on Ubuntu.

Now, don't get me wrong, I'm not meaning to condemn the use of Java in games, as it certainly does have potential. I just wanted to point out an extra point of view or two, and some reasons why not everyone will prefer it.

As a side note, I'm not particularly a C++ proponent, but I certainly am a proponent of compiled languages, including, but not limited to, D and Vala. I like Vala, myself, and I certainly hope people end up preferring it over C# when the day comes (although that's not why they made it, I'm sure). Lua is a nice scripting language to embed into compiled languages.

---

### Post by kayosiii on 2009-10-10
> **SunSpyda said:**
> Sorry for being a little off topic, but why are people so obsessed with a specific layer of abstraction?

Saying that C is used in kernels, so its OO brother must be better at games than languages like Java or Python, is trying to paint all problems with the same 'abstraction paint'.

Need low-level, portable(ish) code, with little overhead? Then languages like C are the answer. Need a large game with loads of libraries required, solid OOP, & more abstraction? Java & C# is the modern world are probably more viable solutions.

This is all reminding me of stories of ASM coders who used to mock C coders, saying it was to slow for games. Deja vu...

Also, the 'JRE dependency' argument is pretty much dwarfed by the compatibility, dependency & portability problems faced by C++ projects when things like game programming is concerned. Has any C++ coder even entered the wonderful world of Java game programming, where so much of the game can be done using nothing but standard Java SE libraries? To duplicate the functionality of the JFCs for games, C++ coders would have to tie in their code to many, many dependencies, making the game as a whole, far harder to distribute vs the Java game with a JRE. Perhaps the JFCs can be rough round the edges, but I still think they're better than the equivalent C++ libraries, provided by different companies, not designed to work with one another, & many of which won't be on as many platforms as the JFCs.

I've also noted a trend. The C++ coders who believe it's a end-all language seldom know anything lower level, & usually can't read ASM code. This is all ironic, considering it's usually those types who accuse people like me of not operating at a low enough level by using languages like Java.

It's all about choosing the best tool for the job. Java doesn't let you do manual memory management... If you need to do manual memory management (and in game engines there are big advantages to doing so) then java is not going to do the job. If you need to access specific hardware features then you you may have to use assembler. There is also sometimes value in optimising your most performance critical code to assember (still even today - after you have looked at algorithmic speedups of course).

The most common approach used by commercial game engines (the type they use to make AAA titles like the original poster asked). Is to use a high level language for most of the game (so far I have come accross Python, Lua, small and custom built languages). What can't be done a high level languages or is significantly slower is done in C++ (or sometimes C) and what can't be done in C/C++ or is significantly slower is done in assembler. It does vary a little bit depending on the target platform (playstation 2 for instance was pretty much all assembler for instance). 

Very few game studios in this day and age produce their own game engine from scratch - It is more common to license a game engine from another company - these licensing costs are usually in the 5 to 6 digit range and are considered cheaper than building your own. That should give a good estimation on how much resources go into a world class game engine.

---

### Post by kumoshk on 2009-10-10
> **kayosiii said:**
> Very few game studios in this day and age produce their own game engine from scratch - It is more common to license a game engine from another company - these licensing costs are usually in the 5 to 6 digit range and are considered cheaper than building your own. That should give a good estimation on how much resources go into a world class game engine.

I'm curious (because I don't know&#8212;I'm not implying anything):
Was the same true before the 3D era? I mean your whole post, and not just this part.

---

### Post by kayosiii on 2009-10-10
I am not really sure either but I have not seen any records of companies doing this before ID. Even a generation or two ago it was much more common to see in house engines. My understanding is that the game industry did not function this way say 5 or 10 years ago.

---

