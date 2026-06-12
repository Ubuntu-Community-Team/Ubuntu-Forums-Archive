---
title: "C++ or C#, For Game Design"
date: 2007-12-05
forum: Programming Talk
---

### Post by jlacroix on 2007-12-05
Hello all, I've been programming off and on for a while, and I've mostly grown accustomed to C-like languages. I dabble in Ruby from time to time, but when I found out it was a scripting language it kinda turned me off because I was looking for a language that compiled.

Anyway, here is my predicament. I enjoy programming in C++ and C#. I'm not an expert in either, I just have fun doing it so I try to learn as much as I can but I'm learning at a slow pace.

Is it hard to study both C++ and C#? I really don't want to pick one over the other, but here are the pros and cons of each language to me personally (if I'm wrong on my assumptions below, please tell me):

**C#**
Pros: Microsoft supplied tools (Game Studio Express) for game design to make designing games easier, Forms for designing interfaces.

Cons: Probably proprietary to Microsoft, games I make with it may not work on other platforms.

**C++**
Pros: Support for almost every platform

Cons: Harder to make games (not as many tools available like Game Studio Express), everything must be done by hand

So there's my predicament, I like both, and I'm not sure if I should study both. If not, it's hard for me to choose which one I should focus on. With C++ I can code for all platforms, with C# making games is made easier, but proprietary. 

Do you guys have any advice?

---

### Post by HeavyAl on 2007-12-05
I have to say that I personally like C# as it integrates a lot of good programming concepts in a very streamlined fashion and comes with a slick dev UI. 

That said, if you are going to program any serious game chances are you're going to need to write a lot of your own custom libraries which C# isn't going to help you with. Added to that is the layers of .Net crap that you need to get a C# game going and you put yourself in a position to just be cranking out a lot of proprietary crap that no one in the open source community is going to really benefit from in the long run.

C++ on the other hand is portable. It compiles with minor adjustments on just about all platforms and when you build a library for particular groups of functions you know in the end what every piece of your code is doing and don't have to make any guesses or assumptions about the end users software environment because you take account of all that from the get-go.

Further, if you are interested in making a game that is beneficial to the open source community you're likely going to be building it with OpenGL if it's graphics intensive. From what I've seen C# favors the DirectX method of doing things so I would imagine most of their tools (like Game Studio Express) are geared that way which would make it problematic for implementing as a native binary on a Linux machine. Yeah, you could always put your finished work in WINE, but why add the extra step? Just program in OpenGL and be done with it.

I hope none of that sounds like trolling. It's just my opinion and YMMV.

---

### Post by iharrold on 2007-12-05
Just a question, but has anyone implemented an OpenGl wrapper to accept DirectX and translate it to OpenGL?  If its even possible.

---

### Post by jlacroix on 2007-12-05
> **HeavyAl said:**
> I have to say that I personally like C# as it integrates a lot of good programming concepts in a very streamlined fashion and comes with a slick dev UI. 

That said, if you are going to program any serious game chances are you're going to need to write a lot of your own custom libraries which C# isn't going to help you with. Added to that is the layers of .Net crap that you need to get a C# game going and you put yourself in a position to just be cranking out a lot of proprietary crap that no one in the open source community is going to really benefit from in the long run.

C++ on the other hand is portable. It compiles with minor adjustments on just about all platforms and when you build a library for particular groups of functions you know in the end what every piece of your code is doing and don't have to make any guesses or assumptions about the end users software environment because you take account of all that from the get-go.

Further, if you are interested in making a game that is beneficial to the open source community you're likely going to be building it with OpenGL if it's graphics intensive. From what I've seen C# favors the DirectX method of doing things so I would imagine most of their tools (like Game Studio Express) are geared that way which would make it problematic for implementing as a native binary on a Linux machine. Yeah, you could always put your finished work in WINE, but why add the extra step? Just program in OpenGL and be done with it.

I hope none of that sounds like trolling. It's just my opinion and YMMV.
Thanks! That was all really helpful. I am leaning more towards C++ as of right now, I just need a good book on the subject.

If I did create a game with MS' Game Studio, I wonder if the code could be ported to OpenGL easily?

---

### Post by Ioky on 2008-01-19
Well, personally, I wrote my games with either, the very basic 2D games with C++ with my text editor, or some more complex games like 3D games with Panda 3D, still with C++, and python. I recommend for anyone who try to write program or games, start with C++, because it is easy to learn and it is powerful. using software that automatic done thing for you is not a good idea, because you wouldn't understand what is really going on with the program, and you are limited with the software. believe or not, text editor is your best friends.

---

### Post by slavik on 2008-01-19
C++ pro: available on any platform.

C# con: doesn't have OpenGL library bindings.

as for translating DirectX to OpenGL, that is what WINE does, but if you want true cross-platform compatibility, use OpenGL.

---

### Post by pmasiar on 2008-01-19
Python has very decent game library, pygame, and compiles into bytecode (.pyc files) automagically. And you can compile it even further with psyco if you need it. Or even better, write your game, profile it, find parts which use 90% of the runtime and are speed bottleneck, and recode those 5% of the code in C. You will have 95% sedelopment speed of Python and 90% runtime speed of C.

And Python is very cross-platform. Some popular games used Python, like Galcon or Eve-online, as "secret weapon".

I am not sure why you consider "scripting language" in some way inferior. "Scripting", or better "dynamically typed" languages increase programmer's productivity by providing automatic memory management (no leaks) and simpifying screation complicated data structures and their processing. Less lines of code - less chance for bugs. Will you like it more if instead of "scripting" Python will be called "glue" language? You can glue together calls to C libraries. Most of Python's graphis libraries are exactly same C libraries, just with added wrapper to simplify their use.

Of course you are free to use a language which works hard to increase your coding productivity  (Python) or a language forcing **you* to handle all low-lvel minor details, like C/C++ does. After all, you waste only your own time, postponing final release, you are not hurting anyone else. :-)

---

### Post by aks44 on 2008-01-19
> **pmasiar said:**
> <snipped the usual Python evangelism ;)>

or a language forcing **you* to handle all low-lvel minor details, like C/C++ does.
<rant>
pmasiar, you should know better than treating C and C++ as a single language...

While I agree that C does force one to handle quite low level details, C++ doesn't. Granted one *can* go that deep if needed, but most of the time any decent C++ code doesn't even have to manage memory or any other low level stuff.

I can understand your love affair with Python, but this doesn't condone you willingly misinforming people, especially knowing that you are perfectly aware of the differences between C and C++ thanks to the numerous previous discussions here where you took part.
</rant>

No hard feelings though. ;)

---

### Post by LaRoza on 2008-01-19
You can use whatever you want...

What kind of game is this?

For starting out with games, you might like PyGame. There are also game engines for Python, that would enable you to write 3d games.

(As for my opinion, C++)

---

### Post by Sam on 2008-01-19
If you plan to make a CPU intensive game (ie. 3D) you should go with C++, you'll get better performances.

---

### Post by Wybiral on 2008-01-19
If it's a 3d game, it doesn't matter. You're crazy if you plan to write a decent 3d game from the ground up. A sane person would use a game engine, in which case there is likely to be a binding for that engine in several languages.

Two really good engines for C++ would be [OGRE]("http://www.ogre3d.org/") and [Irrlitch]("http://irrlicht.sourceforge.net/downloads.html"). Each of which have bindings in other languages such as [PyOGRE]("http://www.ogre3d.org/wiki/index.php/PyOgre") and [Pyrr]("https://opensvn.csie.org/traccgi/pyrr"). There's also [Ogre4J]("http://ogre4j.sourceforge.net/") and [Jirr]("http://jirr.sourceforge.net/") (though I haven't looked too far into these).

If you plan to write a graphics / game engine, then you will probably have to use C or C++, but don't plan on completing a game (as both of them are quite an undertaking on their own, it's rare for someone to actually succeed with both simultaneously).

---

### Post by LaRoza on 2008-01-19
> **Sam said:**
> If you plan to make a CPU intensive game (ie. 3D) you should go with C++, you'll get better performances.

As a first game, it may not be all that intense...

---

### Post by Sam on 2008-01-19
> **LaRoza said:**
> As a first game, it may not be all that intense...

If he plans to do one later, it will be a good training for him.

---

### Post by LaRoza on 2008-01-19
> **Sam said:**
> If he plans to do one later, it will be a good training for him.

There are many options (as this thread shows).

For me, I'd think it would be easier doing it in Python and using the appropriate libraries and be better training. 

The OP wants C++/# so I'd go with C++ also.

---

### Post by pmasiar on 2008-01-19
> **aks44 said:**
> <rant>
pmasiar, you should know better than treating C and C++ as a single language... 

While I agree that C does force one to handle quite low level details, C++ doesn't. Granted one *can* go that deep if needed, but most of the time any decent C++ code doesn't even have to manage memory or any other low level stuff.

I can understand your love affair with Python, but this doesn't condone you willingly misinforming people, especially knowing that you are perfectly aware of the differences between C and C++ thanks to the numerous previous discussions here where you took part.
</rant>

OK I should not be lazy and wrote C **or** C++ instead of shorthand C/C++. BTW IIRC in C logical OR is "|"? We in Python have "or", so I used notation closer to C :-)

But rest of my comment is still valid, it stands unchallenged. Ignoring this issue (that writing game in Python/Pygame uses **exactly** same C libraries, just is more productive than using them from C or C++) IMHO **is**, as you said "willingly misinforming people", especially because any of previous commenters is  "perfectly aware of the differences between [using libraries from Python and using same libraries from C] thanks to the numerous previous discussions here where you took part" :-)

So there :-)

---

### Post by aks44 on 2008-01-19
> **pmasiar said:**
> But rest of my comment is still valid, it stands unchallenged. Ignoring this issue (that writing game in Python/Pygame uses **exactly** same C libraries, just is more productive than using them from C or C++) IMHO **is**, as you said "willingly misinforming people", especially because any of previous commenters is  "perfectly aware of the differences between [using libraries from Python and using same libraries from C] thanks to the numerous previous discussions here where you took part" :-)
As you probably noticed it, I refrained myself to express my views on the topic, mainly because I'm getting tired of those "which language is better" discussions (even if it's in context, ie. "for that peculiar task"). When it comes to language discussions I have decided to try to stick to *technical facts* without making *any* value judgement.

So my rant really was about the (unfortunately common) misrepresentation of "C++ being a low level language just like C" that you expressed (granted, I couldn't help teasing you a bit about the "usual Python evangelism" thing, but I guess you'll agree that it's not far from the truth ;)).

Anyway I have to congratulate you about diverting my rant in such a way. Two words: well done. :D

> **pmasiar said:**
> in C logical OR is "|"? We in Python have "or", so I used notation closer to C :)
FWIW, in C the logical OR is || while a single | is the bitwise OR (which mixes bits of both operands together). So you were indeed merging both languages into a single one. Good try, that really made me laugh, but I'm just as playful as you... :p

</OT>

---

### Post by Majorix on 2008-01-19
C++ is ideal. It (I believe) with VS2008 also supports Game Studio Express or whatever that is called, but to ensure you, GSE won't work under Linux.

C# is in my eyes only good for developing Windows Forms with. I don't use it for anything else.

---

### Post by Druke on 2008-01-21
I'm personally looking into developing 3d engines with mono(OSS c#) and tao(.net OpenGL binds).

thats gives c# a chance on all cliets, also if you code it well, you have can have a single binary for ALL(windows, mac, and linux)

---

### Post by KPexEA on 2008-01-25
I used to program games for a living before I retired 8 years ago. When I started we did games in assembly language, 6502, 68000, 65816, 8088, mips etc. Then we switched to c and finally c++ The nice thing about c and c++ as opposed to other languages that are interpreted is that you have much more control over tuning for speed and memory usage. Optimizing for speed is the #1 issue with games back then and it is still that way today. The other thing that is nice about c and c++ is that they can be written in a very platform independent way and easily recompiled to run on a different system (assuming that you have a x platform library for drawing & sound & input ). The same cannot be said for assembly languages or proprietry languages. I haven't used it but I have heard that libsdl (Simple Direct Layer ) is a cross platform sound and graphics framework that will allow games written using it to be run on Windoze, Linux and Mac. I think there are a bunch of open-source games on sourceforge.net that use libsdl and with those you can download the source and modify them so you don't have to start from scratch.

Cheers,
Kevin

---

### Post by LaRoza on 2008-01-25
> **KPexEA said:**
> I used to program games for a living before I retired 8 years ago. When I started we did games in assembly language, 6502, 68000, 65816, 8088, mips etc. Then we switched to c and finally c++ The nice thing about c and c++ as opposed to other languages that are interpreted is that you have much more control over tuning for speed and memory usage. Optimizing for speed is the #1 issue with games back then and it is still that way today. The other thing that is nice about c and c++ is that they can be written in a very platform independent way and easily recompiled to run on a different system (assuming that you have a x platform library for drawing & sound & input ). The same cannot be said for assembly languages or proprietry languages. I haven't used it but I have heard that libsdl (Simple Direct Layer ) is a cross platform sound and graphics framework that will allow games written using it to be run on Windoze, Linux and Mac. I think there are a bunch of open-source games on sourceforge.net that use libsdl and with those you can download the source and modify them so you don't have to start from scratch.

Cheers,
Kevin

Wow, you must have had quite a career.

"Optimzing for speed" is a big thing. But, there is a balance of programmer time and computer time. 

The most intensive parts are written in C (or similar language) with smatterings of Assembly, but much of a game doesn't need to be so efficient. Games like Oblivion use Python and C together for a great game (I hear).

One can easily write code in C and use them from Python, the best of both worlds.

What kind of games where you involved in? Anything I may have heard about?

---

### Post by KPexEA on 2008-01-25
Test Drive
Stunts
Fifa Soccer

In my career as a game programmer the hardest part of development was the typical 2-3 months of debugging a game at the end of the project. The nice thing about having all of the code in C or C++ is when you come across a bug you can typically find it in YOUR code and squish it. With interpreted languages you have a lot of code that is not yours and therefore harder to debug and if the game is for many different platforms you can have totally different implementations of the scripting languages that expose you to bugs on some machines that aren't on other machines.

Just my 2 cents...
Cheers,
Kevin

---

### Post by Wybiral on 2008-01-25
> **KPexEA said:**
>  ... 

Well, IMO it all depends what you're doing. If you're about to write a board game or a simple 2d game, you're definitely not going to need the speed. An interpreted language will do just fine and you'll probably get it done a lot faster. If you plan to write the next [CryENGINE]("http://en.wikipedia.org/wiki/CryENGINE"), well, gear up for some C or C++ hacking. But, notice that I used an engine as an example, I did so because modern games are so complex that they almost always rely on sophisticated game engines which has split the game development world in two, game implementation developers and game engine/backend developers. It's highly impractical to write an engine and a game at the same time, unless you're writing a simple game (such as a small 2d or board game) in which case, as I mentioned, an interpreted language will do just fine. A large number of these engines have bindings to interpreted languages, since implementation is usually just calling engine functions and handling objects, you generally aren't going to notice much of a speed difference.

Not interested in using one of the well established and tested game engines out there? Fear not! Most interpreted language can be extended using C or C++. If you write your game in something like Python only to discover that you can't squeeze out enough FPS, it's OK, you can just code your bottlenecks in C or C++. That way you get the development time perks and increased portability of using a more dynamic language, but the speed (only when needed) of a compiled language. But, I've written plenty of 3d applications in Python and have only had to whip out the compiled code for a few small routines (such as rendering models or collision detection, two things that are usually handled by a game engine anyway).

---

### Post by Wybiral on 2008-01-25
> **KPexEA said:**
> Test Drive
Stunts
Fifa Soccer

In my career as a game programmer the hardest part of development was the typical 2-3 months of debugging a game at the end of the project. The nice thing about having all of the code in C or C++ is when you come across a bug you can typically find it in YOUR code and squish it. With interpreted languages you have a lot of code that is not yours and therefore harder to debug and if the game is for many different platforms you can have totally different implementations of the scripting languages that expose you to bugs on some machines that aren't on other machines.

Just my 2 cents...
Cheers,
Kevin

IMO, this problem theoretically exists in both worlds. I've never experienced any portability issues in Python, but I have in C (due to either compiler differences or processor architecture). Keep in mind that compiled languages like C and C++ have different compilers for those different platforms (which generate different code) and they also have different implementations of the standard libraries. Sure, they are standardized and *should* be the same on each platform, but such is rarely the case.

---

### Post by KPexEA on 2008-01-25
I don't disagree, but I've never used Python, Ruby on Rails, Javascript of any other of these fancy schmancy interpreted / scripted languages. Since learning C and C++ I've never had the need nor desire to use any of them. Of course languages are just tools that you use to get the job done and my Hammer of choice is C++ 

To answer the original thread title:
"C++ or C#, For Game Design"

I would use gedit or wordpad for "game design".

Cheers,
Kevin

---

### Post by Wybiral on 2008-01-25
> **KPexEA said:**
> Of course languages are just tools that you use to get the job done and my Hammer of choice is C++

That's fair enough for me. But as a side note, you certainly shouldn't restrict yourself, if you get the chance, try a HLL out just so you can add that tool to your belt. I too used to program in assembly, C, and C++, so I know how easy it is to get used to them, but after trying more dynamic languages I've noticed my development time getting shorter and shorter (especially as I become more familiar with HL design strategies). I'm sure you notice this whenever you go from assembly to C, or C to C++... The higher you go, the faster you develop. But, as you mentioned, languages are tools, so if all of your projects require lower level languages, then I can see why you would have no need to learn any HLLs.

---

### Post by slavik on 2008-01-26
> **pmasiar said:**
> And Python is very cross-platform. Some popular games used Python, like Galcon or Eve-online, as "secret weapon".

I love it when people say that Eve-online is cross-platform because it is written in Python ... the sheer hypocrisy from the statement makes my day.

C is cross-platform, too, no? Except I doubt that my pthread/ncurses based code will compile at all on Windows.

---

### Post by LaRoza on 2008-01-26
> **slavik said:**
> I love it when people say that Eve-online is cross-platform because it is written in Python ... the sheer hypocrisy from the statement makes my day.

C is cross-platform, too, no? Except I doubt that my pthread/ncurses based code will compile at all on Windows.

Ansii C is with Ansii compilers.

I don't think the Eve reference was to justify it being cross platform, but for game use.

pmasiar made two statements: "Python is very cross-platform" and "Some popular games used Python". This address two different issues, Python is cross platform and it can be used for games. The OP should find this useful.

---

### Post by rosegarden78 on 2008-01-26
I guess you need to understand OOPS for C++ but yes it's "faster" depending on how you define speed.  I've never used C but I'm told Python using a "pythonic" syntax that emphasizes code clarity rather than convolution.

---

### Post by rosegarden78 on 2008-01-26
I guess you need to understand OOPS for C++ but yes it's "faster" depending on how you define speed.  I've never used C but I'm told Python uses a "pythonic" syntax that emphasizes code clarity rather than convolution.  I guess it ultimately depends on your goals.  You can use freeware BASIC compiler with a GUI designer if that's all your task requires and don't mind generating binaries.

---

### Post by LaRoza on 2008-01-26
> **rosegarden78 said:**
> I guess you need to understand OOPS for C++ but yes it's "faster" depending on how you define speed.  I've never used C but I'm told Python using a "pythonic" syntax that emphasizes code clarity rather than convolution.

[php]
/*In C */
while (x < 10)
{
    printf("%i",x);
    x++;
}

if (x == 0)
{
    printf("%s","X is 0");
}

int function(int  x)
{
    x = x * x;
    return x;
}
[/php]

[php]
# In Python
while x < 10:
    print x
    x+=1

if x == 0:
    print "%s" % "X is 0"

def function(x):
    x = x * x
    return x
[/php]

Syntax is easy, and logical.

---

### Post by rosegarden78 on 2008-01-26
Have you seen LaRoza's Programming Wiki y'all? :KS
[http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python)

---

### Post by jacksaff on 2008-01-26
I would look to do the game logic and AI in something easy to understand ahead of something fast. Lisp, or if you don't_get/hate lisp, Ruby or Python. Anything that has to be fast, rip off of someone else...

---

