---
title: "Programming Language"
date: 2011-04-26
forum: Programming Talk
---

### Post by AZBoy28 on 2011-04-26
Hey Everyone

I want to develop Windows Application (Multi-Platform will be better). I need to know which language would suit my needs the best. I have came across C#, VB, Python, C++, C, Java. My applications will need to be stand-alone ones. 

Thanks

*I know I already posted a thread about VB vs C# but I need help to make my final decision* :(

---

### Post by simeon87 on 2011-04-26
As far as I know you can develop multi-platform applications in most, if not all, of those languages. I think Java is the easiest to develop a cross-platform application in. You can simply write an application, create a .jar file and that file will run on each platform with a Java Virtual Machine (JVM).

For C/C++ you need to make sure you're not making any missteps that kill cross-platformness, Python is also okay but more difficult to distribute on Windows. C# is well-supported on Windows with .NET framework and Mono on Linux, its situation is probably similar to Java although I don't speak from experience.

---

### Post by dodle on 2011-04-26
For Python, the Python interpreter will need to be installed on each machine that runs the program. Or you can use programs like py2exe and cx_freeze to create standalone windows executables out of your scripts.

C or C++ would probably be the best choice for native standalone executables.

Java needs the Java Virtual Machine like simeon says, but a good portion of computers already have that installed.

**------ Edit ------**

For making Windows apps, I prefer C/C++ over Python because cx_freeze and py2exe make large executables.

---

### Post by r-senior on 2011-04-26
It is certainly easy to develop cross-platform apps with Java Swing - one code base and one binary if you write the code using all the platform-independent stuff

The downside with Java Swing apps is that they can be disappointing in terms of looking truly native because the GUI widgets are emulated rather than using the actual widgets. One solution is to use the SWT toolkit that Eclipse IDE uses. I can't remember the details but IIRC there's a trade-off in terms of being fully cross-platform.

This site has some nice tutorials that you could use as evaluation programs, including Java Swing and SWT:

[http://zetcode.com/](http://zetcode.com/)

Perhaps you could try running a few of these for your target platforms and see what works well. (It would be great to see screenshots if you do).

---

### Post by cgroza on 2011-04-26
I would say Python or Java. For Windows, you can use py2exe to freeze the python program into an .exe.

---

### Post by JupiterV2 on 2011-04-26
If using C, you need to make sure you write "portable" C. No POSIX extensions, etc. You'll need to address cross-compiling in some fashion too, either by using mingw and/or msys or a building your own cross-compiler. You'll also have to address multi-platform libraries like using a GUI toolkit like GTK+ or create separate Win API vs. Linux toolkit (again, with GTK+ or QT). It can be done in C but I would imagine that using Python with py2exe (if you want create an .exe file for windows) or Java would be easier/faster.

---

### Post by directhex on 2011-04-26
Do it in C#. Windows users will have .NET already, and most Linux users will have Mono already.

---

### Post by cgroza on 2011-04-26
> **directhex said:**
> Do it in C#. Windows users will have .NET already, and most Linux users will have Mono already.
Same goes for Java.:D

---

### Post by Horseboy on 2011-04-26
Python is probably one of the easiest programming languages ever made, the syntax is simple, clean. And you can build just about anything you dream up with it, CLI programs, standalone applications, web development (like PHP). Blogger actually uses Python (I think, perhaps Google changed things when they acquired Blogger). I suggest you take a look at this: [http://learnpythonthehardway.org/index](http://learnpythonthehardway.org/index)

Very useful introduction, if you like it's simplicity, go for it ;)

---

### Post by nvteighen on 2011-04-26
> **cgroza said:**
> I would say Python or Java. For Windows, you can use py2exe to freeze the python program into an .exe.

IMO, Java is more practical for this. py2exe packages the Windows version of the Python interpreter and adds your code... Curiously, doing that makes that specific binary completely Windows specific, while distributing .py or .pyc files preserves the ability to run the same file in all platforms. 

OK, I know installing Python in Windows is harder than in repository-based GNU/Linux distros and that in some cases, well, a py2exe generated program may be a good option, but you have to understand that that isn't exactly what is understood as a "cross-platform" solution. It's more like recompiling a C source code for Windows instead of asking people to install ELF support (I don't even know if that's possible) on their own as a prerequisite to install your program.

Java follows the "Compile once, run everywhere" philosophy. That's way more practical and that explains Java's success... Of course, the language isn't marvelous, it's just a better C++, but the platform is quite impressive.

---

### Post by cgroza on 2011-04-26
> **nvteighen said:**
> IMO, Java is more practical for this. py2exe packages the Windows version of the Python interpreter and adds your code... Curiously, doing that makes that specific binary completely Windows specific, while distributing .py or .pyc files preserves the ability to run the same file in all platforms. 

OK, I know installing Python in Windows is harder than in repository-based GNU/Linux distros and that in some cases, well, a py2exe generated program may be a good option, but you have to understand that that isn't exactly what is understood as a "cross-platform" solution. It's more like recompiling a C source code for Windows instead of asking people to install ELF support (I don't even know if that's possible) on their own as a prerequisite to install your program.

Java follows the "Compile once, run everywhere" philosophy. That's way more practical and that explains Java's success... Of course, the language isn't marvelous, it's just a better C++, but the platform is quite impressive.
I was for both, now it depends on the skill and the options of the programmer.

---

### Post by juancarlospaco on 2011-04-26
Python or Jython

---

### Post by Horseboy on 2011-04-26
> **juancarlospaco said:**
> Python or Jython

Python... lol

---

### Post by cgroza on 2011-04-26
> **Horseboy said:**
> Python... lol
What's so funny?:confused:

---

### Post by Learning Linux 2011 on 2011-04-26
Part of it depends on whether you want compiled or interpreted.

---

### Post by Abscissa on 2011-04-26
I would rule out VB.NET. In my (limited) experience, VB.NET apps tend to have problems under Mono. AIUI, VB.NET apps generally depend on some special VB-specific CLI assemblies that Mono hasn't fully implemented.

---

### Post by trollger on 2011-04-26
I highly recomend you start with c++. Even if you don't use it much the education you will aquire will be phenomenal. Also among the languages discussed c/c++  is the only language(s) that are compiled as opposed to being interpreted. 

(note: c and c++ are simular in manny ways but are not the same)

---

### Post by cgroza on 2011-04-26
> **trollger said:**
> I highly recomend you start with c++. Even if you don't use it much the education you will aquire will be phenomenal. Also among the languages discussed c/c++  is the only language(s) that are compiled as opposed to being interpreted. 

(note: c and c++ are simular in manny ways but are not the same)
+1, C++ really helps you get a concrete knowledge on how stuff work. In languages like python some things may appear as magic to a beginner, until you go in the underground and see how stuff really work.

---

### Post by cgroza on 2011-04-26
> **trollger said:**
> 

(note: c and c++ are simular in manny ways but are not the same)

C++ is basically OOP added to C, and with OOP in, you get loads of other things added to the language which makes it kind of different. Although valid C is also valid C++.

---

### Post by dodle on 2011-04-26
> **cgroza said:**
> What's so funny?:confused:

I think that horseboy thought that juan was asking a question.

---

### Post by juancarlospaco on 2011-04-27
> **dodle said:**
> I think that horseboy thought that juan was asking a question.

No

---

### Post by AZBoy28 on 2011-04-27
Hey

Thanks, my languages I am considering are C#, VB, Python. The language I choose needs to be simple  to learn.

Thanks

---

### Post by Horseboy on 2011-04-27
> **AZBoy28 said:**
> Hey

Thanks, my languages I am considering are C#, VB, Python. The language I choose needs to be simple  to learn.

Thanks

Go with Python, trust me, it will give you a good entrance to the Programming world, then learn things like C++ etc. Trust me.

---

### Post by AZBoy28 on 2011-04-27
Hey Everyone

thanks for the information. I kind of like the Visual Studio designing enviroment, how you can add Buttons, Text Box, etc…(it makes life easier)which python does not have. But I am also considering Python with py2exe  I want to do programming for my Career and want a good programming language to stay with. My choice are VB, C#, python (with py2exe). I need something that is easy to learn (since I'm new) and can design good interactive applications.

Thanks. 

=)

---

### Post by AZBoy28 on 2011-04-27
Can someone tell me what famous programs are made with Python, C#, VB? 
And can someone give me a comparison between C#, VB, Python

=)

---

### Post by nvteighen on 2011-04-27
> **trollger said:**
> I highly recomend you start with c++. Even if you don't use it much the education you will aquire will be phenomenal. Also among the languages discussed c/c++  is the only language(s) that are compiled as opposed to being interpreted.

(note: c and c++ are simular in manny ways but are not the same)

I highly recommend not to start with C++... Better start with C if you like the low-level -> high-level approach (which I do not like, although there are some fair arguments in favor of it).

C++ is a complete mess... it mixes levels of abstraction without hiding them properly, aims to be low and high-level at the same time and with poor results. Why are references limited by stack calls? Why are std containers homogeneous? A language where there are reinterpret_cast and dynamic_cast instead of implementing a duck type system is plainly schizophrenic... In other words, C++ tries to solve the abstraction vs. efficiency trade-off by trying to deny that trade-off exists! C may be very low-level and veryy limited, but it's true to its foundations!

> **cgroza said:**
> +1, C++ really helps you get a concrete knowledge on how stuff work. In languages like python some things may appear as magic to a beginner, until you go in the underground and see how stuff really work.

Absolutely not. OK, I agree with you in that some Python tutorials explain stuff like it were magic, instead of resorting to general CompSci concepts (like SICP did, using Scheme). No, high-level programming aspects are general to all languages because they are implementation-independent. A list is a concept which can be modelled using a Python list object, by Lisp cons'es, a C struct, a C++ class or the Forth main stack. On the contrary, a pointer or structure byte alignment are concepts that only make sense in a certain level of abstraction.

C++ and C help you understand how things work from the point of view of a certain level of abstraction in a certain platform. And be aware that they do not show you what is really happening: they are low-level, but not the lowest level of abstraction. Man, not even ASM is the lowest level these days (x86 ASM is emulated by the microprocessor).

There's also a problem: ok, let's say some beginner wants to know what input buffering is and works... What will std::cin teach him that, let's say, Common Lisp read-line won't? Or are you suggesting that people get into the C++ or C Standard Library's source code??

What I do concede is that some OS specific APIs should be learned using C or C++ (depending in what language they were originally written). But exactly because they are OS specific and therefore, they fall into the real domain of those languages. For example, I'd highly recommend learning POSIX from C, not from Python. Not so sure about Qt, though.

> **cgroza said:**
> C++ is basically OOP added to C, and with OOP in, you get loads of other things added to the language which makes it kind of different. Although valid C is also valid C++.

Be careful: valid C89 is valid C++98, but there are some issues with type casting, because C is a weakly typed language whereas C++ is a strongly typed one. Another subtle difference is how C and C++ interpret a signature *type f()* as different things; in theory this could introduce subtle bugs in function pointers: C would interpreted it as a function accepting an arbitrary amount of parameters, while C++ would consider it a function accepting no parameters... And in theory, the current C99 may have added stuff that's incompatible with the current C++98 standard, so I would think twice before relying on that assumption. (Don't know whether C++0x assumes C99 as a subset or not).

Also, don't confuse OOP and syntax support for OOP. C++ introduces just the latter and IMO, it makes things really worse: it forces the usage of certain features that are completely particular to the very weird vision C++ holds of OOP; i.e. classes are types. OOP has been done in C since it was created, by using structs... Take a look on GTK+ and you'll know what I mean. Ok, you don't get the object.method() syntax invented by the Simula programming language, but Smalltalk doesn't either and it features a much richer OOP system.

---

### Post by Horseboy on 2011-04-27
> **AZBoy28 said:**
> Can someone tell me what famous programs are made with Python, C#, VB? 
And can someone give me a comparison between C#, VB, Python

=)

Google Blogger was created in Python.

---

### Post by directhex on 2011-04-27
> **AZBoy28 said:**
> Can someone tell me what famous programs are made with Python, C#, VB? 
And can someone give me a comparison between C#, VB, Python

=)

On your desktop right now? No VB apps - the only VB.NET app in Ubuntu is the VB.NET compiler itself. There's no good development environment for it. C#? On Natty you have gBrainy, Tomboy and Banshee preinstalled. Python? A bunch of system things, including the Software Centre.

---

### Post by CptPicard on 2011-04-27
> **cgroza said:**
> In languages like python some things may appear as magic to a beginner, until you go in the underground and see how stuff really work.

I'm willing to bet you haven't actually gone to read Python's source to gain some additional insight of how things "really work" and then applied that in your Python.

The thing is, the low level is not "how it really works". This follows strictly from theory -- because the underlying implementation could be *anything* Turing-complete, the lower-level implementation is irrelevant and *can't* communicate anything upwards. If it could, then the implementation would not be interchangeable anymore.

Languages simply are, as they are defined. That's it.

(Nvteighen, I'm surprised I have not seen it this clearly and concisely before...)

---

### Post by llanitedave on 2011-04-27
> **AZBoy28 said:**
> Hey Everyone

I want to do programming for my Career and want a good programming language to stay with. 

This is an important point, I think.  If you want to program for a living, and make a career out of it, the answer would be "all of the above".  Python is a good introduction, and probably a good general-purpose application language, but you'll need C and C++ when performance demands get heavy, and you'll probably want to add javascript and html and css if you're going to be called on to do web apps.

A professional pilot learns to fly more than one type of airplane.  A professional athlete learns to play more than one position, or more than one sport. A professional ecologist studies more than just a single ecosystem, and a professional geologist works with more than one kind of rock.

There's no reason why a professional programmer should limit himself to just one language.  You'd probably want to add the other languages just to round out your professional development.

---

### Post by brpylko on 2011-04-27
Although you have narrowed it down to Python, C#, and VB I hope I can give you some more advice.

Python I think of as more of a scripting language to write really simple programs.
I don't think I have ever seen a professional application written in VB, anything that requires any more than basic graphics will have low performance at best in VB.
C# is almost exactly Java, the difference is I usually see programs that really need to be cross-platform written in Java, and programs that need high graphics performance(games, window managers, etc.)

I hope this helps!

---

### Post by Jinren on 2011-04-27
+1 to what llanitedave said.

However, I think there are two different paths, depending on what your priorities are.

If you want to get good at the theoretical stuff over the long term, I'd say none of the above, because they're all pretty mixed. Instead go for C, following *The C Programming Language* by Kernighan and Ritchie (costs money), and Scheme, following *The Structure and Interpretation of Computer Programs* by Abelson and Sussman (available for free). The first will teach you a low-level way to think about programs, similar to how the machine will probably run them, and the second will teach you much more abstract and expressive techniques.

If you want a practical language to use right now, Python and C# are both great options. VB.NET I thought is really just a dumbed-down C#, so it's not worth your time if you're able to choose between the two. If you have time, try to use both (C# and Python) as they also show two sides of the same coin, although not to the same extreme as the two mentioned above. I think C# will open more work to you in business, but the work available with Python will be better. If you can find work with Python, it's probably the better option.

The thing is, because these languages are so very practical and easy to use, it's easy to learn a moderate amount of cool stuff that does what you want, and then stay still from a learning point of view. That's why I suggested starting with the harder, more constrained languages: they're more focused. You can still learn to be a great programmer with C# or Python, but you have to actually push yourself.

Hmm, I think I just repeated what nvteighen said.

---

### Post by unknownPoster on 2011-04-27
> **brpylko said:**
> 

Python I think of as more of a scripting language to write really simple programs.


That's one of the most misinformed "facts" that's thrown around against python.


Many complex, and robust applications are written in or make heavy use of python. Here is a short list:

[LIST]
[*]EVE Online, a fairly popular sci-fi mmo
[*]YUM, the package manager for RedHat and Fedora
[*]PackageKit, a gui frontend to YUM
[*]Blender, one of the biggest animantion/rendering suites
[*]DropBox, cloud based backups
[*]VegaStrike, sci-fi game
[*]Battlefield 2
[*]Civilization 4
[/LIST]
A more comprehensive list can be found here: [http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

So yeah, it's false to say python is only used for "simple applications."

---

### Post by lisati on 2011-04-27
> **nvteighen said:**
>  Man, not even ASM is the lowest level these days (x86 ASM is emulated by the microprocessor).

I remember having a "What the <adjectives deleted>?" moment when I first heard of [microcode]("http://en.wikipedia.org/wiki/Microcode"), a level of abstraction that sits between ASM and the hardware.

---

### Post by slavik on 2011-04-27
> **unknownPoster said:**
> That's one of the most misinformed "facts" that's thrown around against python.


Many complex, and robust applications are written in or make heavy use of python. Here is a short list:

[LIST]
[*]EVE Online, a fairly popular sci-fi mmo
[*]YUM, the package manager for RedHat and Fedora
[*]PackageKit, a gui frontend to YUM
[*]Blender, one of the biggest animantion/rendering suites
[*]DropBox, cloud based backups
[*]VegaStrike, sci-fi game
[*]Battlefield 2
[*]Civilization 4
[/LIST]
A more comprehensive list can be found here: [http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

So yeah, it's false to say python is only used for "simple applications."
it's also a misinformed fact that python is the bee's knees ... either way ... use Java, done.

Python is still not a cross platform as Java.

Java is the answer (make a jar and it will work anywhere, simple example that I use: sc2gears).

---

### Post by AZBoy28 on 2011-04-27
Hey.

Thanks for the reply. It looks like my choices have narrowed down to C# and Python with py2exe. But one thing that Python is missing out on that C# has is its Graphical  Designer(Not what it is actually called) how you can drag and drop buttons and text boxes etc..

Thanks

---

### Post by simeon87 on 2011-04-28
> **AZBoy28 said:**
> Hey.

Thanks for the reply. It looks like my choices have narrowed down to C# and Python with py2exe. But one thing that Python is missing out on that C# has is its Graphical  Designer(Not what it is actually called) how you can drag and drop buttons and text boxes etc..

Thanks

You can use Glade for the GTK+ toolkit. You can then load the GUI from Python: [http://glade.gnome.org/](http://glade.gnome.org/) Glade allows you to drag-and-drop controls easily.

---

### Post by simeon87 on 2011-04-28
> **Jinren said:**
> The thing is, because these languages are so very practical and easy to use, it's easy to learn a moderate amount of cool stuff that does what you want, and then stay still from a learning point of view. That's why I suggested starting with the harder, more constrained languages: they're more focused. You can still learn to be a great programmer with C# or Python, but you have to actually push yourself

Becoming a great programmer doesn't depend on the language that you start with but on the languages that you learn afterwards. If you learn 1 language and stay there, you'll become mediocre or good in that language but you won't be exposed to other ideas and languages. Improving your programming skills is more like a path where you go from language to language to learn new concepts and ways to express your ideas in code.

---

### Post by directhex on 2011-04-28
> **unknownPoster said:**
> [LIST]
[*]EVE Online, a fairly popular sci-fi mmo
[*]YUM, the package manager for RedHat and Fedora
[*]PackageKit, a gui frontend to YUM
[*]Blender, one of the biggest animantion/rendering suites
[*]DropBox, cloud based backups
[*]VegaStrike, sci-fi game
[*]Battlefield 2
[*]Civilization 4
[/LIST]
A more comprehensive list can be found here: [http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

So yeah, it's false to say python is only used for "simple applications."

It's worth pointing out, in the interests of honesty, that Python was dumped in Civ5, for performance reasons - they moved to Lua. And for games "written in or making heavy use of" C#, and specifically Mono, there's Second Life and The Sims 3, both of which embed Mono (not MS.NET). Non-C languages are used for less performance critical pieces of games - basically for scripting events and actions. 3D engines are almost always C or C++

---

### Post by llanitedave on 2011-04-28
> **directhex said:**
> It's worth pointing out, in the interests of honesty, that Python was dumped in Civ5, for performance reasons - they moved to Lua. And for games "written in or making heavy use of" C#, and specifically Mono, there's Second Life and The Sims 3, both of which embed Mono (not MS.NET). Non-C languages are used for less performance critical pieces of games - basically for scripting events and actions. 3D engines are almost always C or C++

The point being, as several have already pointed out, that there is no one single "ideal" programming language.  Most can do pretty much everything, but none of them do everything *well*.

Learning several languages allows a good programmer to combine them or split them out as needed to leverage the strong points of each.  To me, it seems like Python and C/C++ would come the closest to providing the full complement of strengths, especially since Python easily binds to lower level languages.  Some, obviously, will say that Java comes closest to having it all in one package.  Since web apps are such a big part of the ecosystem, I'd think javascript should also be part of the repertoire.

---

### Post by unknownPoster on 2011-04-28
> **slavik said:**
> it's also a misinformed fact that python is the bee's knees ... either way ... use Java, done.

Python is still not a cross platform as Java.

Java is the answer (make a jar and it will work anywhere, simple example that I use: sc2gears).

No where did I say that Python is the "bee's knees."

I'm just a defender of programming languages in general, and to say that Python is only used for simple programs/projects is false.

For example, many people tend to say Java can't be used to make successful games, and I'd kindly point them to Minecraft. :)

---

### Post by LoneWolfJack on 2011-04-28
Back in the 80s, people would start with something like BASIC. Today, the best idea is to start with one of the scripting languages (PHP, Perl, Python...). It absolutely makes sense to learn Python first (even though I'd still recommend PHP instead because of the excellent documentation and the code style that is very similar to a lot of other languages).

I'd also suggest not to use OOP for starters. Procedural programming is much more straightforward and will give a beginner much less headache.

Once you've gained a reasonable understanding of PHP/Python - say, in two or three years from now -, you can move on to something like C. 

Learning C is much, much easier if you already have a programming background. C will make you a better programmer because you will have to deal with stuff that PHP/Python does automatically at the expense of performance.

If you feel bold, you can then move on to LISP or Assembly - or you learn a language you can actually do something with, like Java.

Obviously, this is from my perspective. I started out with BASIC back in the late 80s, then moved to Perl and C, jumped on the PHP wagon in 94 or 95 and learned Java around 00/01. I also had some fun with LISP, Assembly and Cobol along the way, even though I never used those in a professional context.

---

### Post by AZBoy28 on 2011-04-28
Hey

I might go with C#. But others in other forums have told me I should stay with VB. 
Please Help!!!

Thanks

---

### Post by worseisworser on 2011-04-29
> **AZBoy28 said:**
> Hey

I might go with C#. But others in other forums have told me I should stay with VB. 
Please Help!!!

Thanks

Do you need a vote count?

---

### Post by directhex on 2011-04-29
> **AZBoy28 said:**
> Hey

I might go with C#. But others in other forums have told me I should stay with VB. 
Please Help!!!

Thanks

You cannot develop GUI apps on Ubuntu with VB.NET, unless you do the GUI in code by hand.

Clear enough?

---

### Post by simeon87 on 2011-04-29
> **directhex said:**
> You cannot develop GUI apps on Ubuntu with VB.NET, unless you do the GUI in code by hand.

Clear enough?

I develop the GUI by hand too for some projects, what's wrong with that? :) But between C# and VB I'd 200% go for C#.

---

### Post by directhex on 2011-04-29
> **simeon87 said:**
> But between C# and VB I'd 200% go for C#.

I would urge people not to use VB.NET.

And it's my package.

---

### Post by cgroza on 2011-04-29
> **simeon87 said:**
> I develop the GUI by hand too for some projects, what's wrong with that? :) But between C# and VB I'd 200% go for C#.
I code the GUI by hand for all my projects. It simply offers you more flexibility and teaches you the APIs.

---

### Post by worseisworser on 2011-04-30
Glade as a UI designer for GTK+ stands on its own; it isn't bound to any specific IDE or programming language/environment in particular. Hence any language with at least GTK+ bindings (and some trivial bindings to the Glade "connection" APIs) has support for design of UIs using a graphical tool; i.e. not only "by hand".

---

### Post by nvteighen on 2011-04-30
> **cgroza said:**
> I code the GUI by hand for all my projects. It simply offers you more flexibility and teaches you the APIs.

IMO, that's great for learning but utterly impractical when you're coding a real project.

For GTK+, I'd follow worseisworse's advice and use Glade.

---

### Post by rich1939 on 2011-04-30
> **Horseboy said:**
> Python is probably one of the easiest programming languages ever made, the syntax is simple, clean. And you can build just about anything you dream up with it, CLI programs, standalone applications, web development (like PHP). Blogger actually uses Python (I think, perhaps Google changed things when they acquired Blogger). I suggest you take a look at this: [http://learnpythonthehardway.org/index](http://learnpythonthehardway.org/index)

Very useful introduction, if you like it's simplicity, go for it ;)

+1 for Python. After have used many other languages for work or play, Python seems the best for me. It's quite easy to write Python programs for Linux and port them directly to Windows, or vice-versa.

---

### Post by shadylookin on 2011-04-30
> **AZBoy28 said:**
> Hey Everyone

thanks for the information. I kind of like the Visual Studio designing enviroment, how you can add Buttons, Text Box, etc…(it makes life easier)which python does not have. But I am also considering Python with py2exe  I want to do programming for my Career and want a good programming language to stay with. My choice are VB, C#, python (with py2exe). I need something that is easy to learn (since I'm new) and can design good interactive applications.

Thanks. 

=)

Unless you're planning on an incredibly short career you'll probably be using a different language than the one you started off with anyway. That or you'll be doomed to a soul crushing career of dealing with legacy code. 

If you use java/python/c# your users will have to have VMs/interpreters for them so you'll have to take into account market share for them. 

If possible you might want to consider writing it as a web app which alleviates the worry of cross platform compatibility issues(though does bring up cross browser issues)

---

### Post by DarkHackerX on 2011-05-04
Well best one for cross-platforming and web apps would be Java. But for your first language, I would say C++, since C++ can start with the simple procedural approach and work your way into OOP. C++ might only be specific platform, unless you write it with preprocessors distinguishing compiling for on platform or another(a lot of work depending on what you want to do). But you will notice after learning C++, a lot of languages use similar semantics. But as earlier comments go, the language you start with might not be the only language you use. I learned C++ first, then Java, awk, Python, etc. So far, using most of them. Just look for good coding resources, since a lot of code in C++ is written poorly, i.e. spaghettification. Since the procedural will become obsolete after learning how to do classes for the most part. But you have to walk before you run. After you learn a few different languages, you should begin seeing the advantages and disadvantages to different languages.

---

### Post by AZBoy28 on 2011-05-24
Hi

I have chosen C#. Thanks for all you help :)

Can anyone recommend any books that can get me started. I have came across 

*C# 2010 For Dummies
*Microsoft Visual C# Step By Step.

Are those good books that can give me the basics to develop good programs and I can look back to for help? And for anyone that has read these which is better for someone that is completely new to programming and I can look back for a reference. 

And again I am always looking for other books, so please suggest some..

Thanks for your support :)

---

### Post by AZBoy28 on 2011-05-26
? :)

---

### Post by nvteighen on 2011-05-26
> **AZBoy28 said:**
> ? :)

Well, good luck and, above everything, enjoy it! And you know we're here glad to help you :)

---

