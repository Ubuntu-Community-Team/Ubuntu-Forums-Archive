---
title: "programs and tools to learn C++"
date: 2007-01-07
forum: Programming Talk
---

### Post by cccc on 2007-01-07
hi

which programs and tools could you recommend to learn C++ ?
I have ubuntu 6.10 Edgy Eft installed.

kind regards
cccc

---

### Post by meng on 2007-01-07
Perhaps you're after online tutorials? Here are some that another forum user posted some months ago:
[http://www.bloodshed.net/dev/doc/index.html](http://www.bloodshed.net/dev/doc/index.html)
[http://cplus.about.com/od/beginnerctutorial/l/blcplustut.htm](http://cplus.about.com/od/beginnerctutorial/l/blcplustut.htm)
[http://en.wikibooks.org/wiki/C++](http://en.wikibooks.org/wiki/C++)
[http://www.cplusplus.com/doc/language/tutorial/](http://www.cplusplus.com/doc/language/tutorial/)
[http://www.zeuscmd.com/tutorials/cplusplus/index.php](http://www.zeuscmd.com/tutorials/cplusplus/index.php)

---

### Post by WebDrake on 2007-01-07
> **cccc said:**
> hi

which programs and tools could you recommend to learn C++ ?
I have ubuntu 6.10 Edgy Eft installed.

kind regards
cccc
In terms of packages you will need to install g++ (the C++ front-end to the GNU Compiler Collection).  Things like make, automake and so on can also be useful (essential once you go beyond a certain level of complexity, but not necessary for an absolute beginner).  A good C++ tutorial will probably teach you about things like Makefiles.

KDevelop provides a nice code editing and development environment.  Personally I just use it as a glorified text editor and create Makefiles etc. by hand, but that's because I'm too lazy and have too many other things to do to learn how to use it properly.  Even *as* a glorified text editor it's useful because you can set it up specifically for editing code, while keeping other text editors (Kate, gedit, whatever) free for more general-purpose use.

You might also want to learn about C as well as C++.  At some point you will have to interact with it so it's wise to be aware of the differences in style and focus.

---

### Post by meng on 2007-01-07
If you come across programming problems/questions you can't answer, this (sub)forum is a good place to ask. I recommend you spend some time thinking about such problems and even post your initial thoughts, including things that didn't work. IMO, it enhances the learning process.

(I suppose this approach isn't for everyone, some folks seem to be in a hurry and just want to know the answer without working for it. I guess that's fine too, it's just not my own style.)

---

### Post by Hendrixski on 2007-01-07
There is some speculation as to how much longer C++ will still be relevant.  I mean, the programs that use C++ today are oftentimes solid programs and will be around for a long time, So if you will be working with those then C++ will be relevant.  But new applications are being made with Java,C#, and other new languages.

C++ is still a great place to learn to program.  I have many fun years of programming C++ and I wish you all the best.

---

### Post by Wybiral on 2007-01-07
> **Hendrixski said:**
> There is some speculation as to how much longer C++ will still be relevant.  I mean, the programs that use C++ today are oftentimes solid programs and will be around for a long time, So if you will be working with those then C++ will be relevant.  But new applications are being made with Java,C#, and other new languages.

C++ is still a great place to learn to program.  I have many fun years of programming C++ and I wish you all the best.

I think C++ will be around for a while... Java/C# aren't going to push it out of the way. Many people thought that C++ was going to push C out of the way, and for a portion of C programmers it did, but, but C is still here and strong. I personally don't see C++ going anywhere either, because plain C doesn't always cut it.

Also, I've been learning machine code lately (not just assembly, but byte values of machine opcodes) and I encourage you to open up a command linux program on your computer with a hex editor... For instance, "/bin/ls"... DON'T change anything, but you will see a lot of random characters, and especially a lot of C related stuff... Almost all of the ubuntu system executables like cp, mv, ls, pwd... All written in C. That's something that Java/C# will probably never replace.

And more than that... I'm not just saying C/C++ will just be for kernel stuff, I'm pointing this out to you because those programs work... They are fast... And they are very small... And they use very little CPU power to run. Those are just some of the perks with compiled languages like C/C++ that will make sure that those languages hang around... Trust me, C isn't going anywhere, and since most people like me value the object oriented extensions that C++ offers, C++ probably isn't going anywhere any time soon.

---

### Post by WebDrake on 2007-01-07
> **Wybiral said:**
> And more than that... I'm not just saying C/C++ will just be for kernel stuff, I'm pointing this out to you because those programs work... They are fast... And they are very small... And they use very little CPU power to run. Those are just some of the perks with compiled languages like C/C++ that will make sure that those languages hang around... Trust me, C isn't going anywhere, and since most people like me value the object oriented extensions that C++ offers, C++ probably isn't going anywhere any time soon.
Right.  It depends very much on what you want to achieve.  If you want to write very fast number-crunching code (e.g. scientific simulation), C is the best choice (it used to be FORTRAN but I don't think there's any significant speed difference these days and C probably has a wider range of resources available).  Core bits of an OS, like the kernel, also have such requirements.

If object-oriented but still fast programming is needed, C++ or Objective-C may be useful.  You can build an object-oriented framework in C (see e.g. the GNU Scientific Library or for that matter GTK+) if you want to, but it's much easier with C++ or Objective-C.  The problem is that these languages tend to slow things down somewhat unless you use only a minimum of their snazzy features.  For example I keep getting C++ people telling me to use vector types instead of standard arrays, but I know from experience that slows things down unacceptably for a large-scale simulation.  Still, this is a minor issue unless you're dealing with code that needs to be seriously, seriously fast (and algorithms make far more of a difference than any C versus C++ issues).

I did have one colleague who used C# for simulation; I don't know how its speed compares to C++.  Others use Java, but while this is good for easier implementation, it's not so good for large-scale intensive simulation because it's much slower than comparable C or C++.  If anyone can comment on experiences with Mono, and the speed of C# programs, I'd be very grateful---it might be worth me looking into.

For many applications such speed requirements are not important and it's here that elegant and simple languages like Python come into their own.  It's particularly great if the main focus of development is to be able to write and revise code quickly, but runtime is not a major concern.

---

### Post by phossal on 2007-01-07
> **Wybiral said:**
> ...plain C doesn't always cut it.

Also, I've been learning machine code lately (not just assembly, but byte values of machine opcodes) and I encourage you to open up a command linux program on your computer with a hex editor... For instance, "/bin/ls"... DON'T change anything, but you will see a lot of random characters, and especially a lot of C related stuff... Almost all of the ubuntu system executables like cp, mv, ls, pwd... All written in C. That's something that Java/C# will probably never replace.
...

^This is a good answer. There are plenty of full-time programmers at major companies - think EDS - that spend all day programming and maintaining C code. C and C++ are good, powerful, fast languages.

Wybiral points us in another direction, too, without being blatant, by suggesting we use the hex editor. There are plenty of people using their knowledge of those languages, and assembly/object code, to better understand programs which have already been written, and for which there is no existing (or available) source.

[edit] I use gedit with the extra plugins, gcc, g++, and khexedit, among other things. Though I'm not sure it's a great *learning* tool, Bjarne Stroustrup's book on the language he created, C++, is worth looking at.

---

### Post by Mirrorball on 2007-01-07
When you finally understand what he's talking about, Bjarne Stroustrup's book is the reference for C++. It doesn't leave my desk.

---

### Post by Wybiral on 2007-01-07
> **phossal said:**
> ^This is a good answer. There are plenty of full-time programmers at major companies - think EDS - that spend all day programming and maintaining C code. C and C++ are good, powerful, fast languages.

Wybiral points us in another direction, too, without being blatant, by suggesting we use the hex editor. There are plenty of people using their knowledge of those languages, and assembly/object code, to better understand programs which have already been written, and for which there is no existing (or available) source.

[edit] I use gedit with the extra plugins, gcc, g++, and khexedit, among other things. Though I'm not sure it's a great *learning* tool, Bjarne Stroustrup's book on the language he created, C++, is worth looking at.

Well, yeah... As far as using a hex editor goes, if you're already an assembly programmer and have a pretty basic knowledge of assembly, you can actually read the raw bytes from an executable as assembly, you just have to know what they mean. I've been studying them for an assembling portion of one of my projects where I want it to compile things to an executable, without a bloated assembler back-end.

It's not something you would ever want to write a program in since every opcode+register basically has it's own byte value, and you have to know how to read the executable headers and sections, but once you learn it enables you to cut significant portions of excess off of your executables as well as gain a deeper understanding about how the executables are structured and hence an improved sense of how to optimize them for both speed and size.

It's very simple for smaller executables, less than 2-3kb's but it obviously isn't something you need to worry about for larger files. But it does broaden your sense of understanding as to how your assembly programs are assembled into an executable.

Practical uses don't go much further than optimization, understanding, and compiler/assembler writing.

EDIT:

Here's an example, I compiled a hello world program in c++, it was 4000 bytes.
I wrote an identical program in GAS assembly that assembled to: 284 bytes.
I optimized it manually using a hex editor, the resulting executable was: 96 bytes.

That would probably be the biggest advantage to understanding the byte format in your executables.

---

### Post by pmasiar on 2007-01-07
Language comparison wars quieted for couple days :-) and I don't want to release demons... But there is place for deeper understanding. If you are not open to question tools you use, and see them in bigger context of company marketing, ego trips, and (human and corporate) resistance to change, don't waste your time (and mine) reading any further. 

There is a huge gap opening between ever-increased speed of CPU and slow (if any) increase of programmer's productivity. So we need to look very carefully at the tools we are using - are they appropriate for the tasks we have?

> **Hendrixski said:**
> There is some speculation as to how much longer C++ will still be relevant.  ...  new applications are being made with Java,C#, and other new languages.

In my opinion,  C will be here for **very** long time for people who need raw performance, and is NOT going away any time soon. From C you can smell Assembler - you have almost all power of raw assembler (except register trickery) without the hassle. C++ is natural step up towards OOP goodness.  With C++, you still have full control and full responsibility for resource (mostly memory) allocation.

[OOP]("http://en.wikipedia.org/wiki/Object-oriented_programming") is the only mental trick we found to improve programmer's performance since '60, as we abandoned GOTO and started era of structural programming. Pretty bleak picture, eh? OOP fights are almost over, question is settled and OOP will stay with us. We desperately need some new fresh ideas. [Agile ]("http://en.wikipedia.org/wiki/Agile_software_development") software development and [TDD]("http://en.wikipedia.org/wiki/Test_driven_development") (Test-driven development) seems to be new Holy Grails, but only small minority knows about them - and even smaller minority practices this new religion :-)

There is crop of new "agile" "dynamically typed" languages, like Python, Ruby (and yes Perl is old but loved by some), which shield user from hassle of most memory allocation (preventing the famous "buffer overflow" bug and most memory leaks), delay declaration of variable's type as late as possible to allow the same generic code work with different types, as found at runtime. Introspection can be used to modify code behavior according to what methods are valid for current type - providing tools to build flexible frameworks to solve in generic ways problems from a specific problem area. 

Problem with Java/C# IMHO is NOT that they departed from raw speed - if I need raw speed I'll use C/C++, thank you. Problem with them that they are not radical enough - productivity gap is widening, and you know what will happen if you try to jump over a gap with half-hearted effort... :twisted: Exactly. You don't get productivity increase as agile language has, and you lose most of the speed.

Both Java and C# has also set of own issues. 

C# is Microsoft reimplementation of Java when court order denied them they customary "embrace, extend, choke" route (Sun sued to stop MS proprietary enhancements for Java on Windows) - they created own Clone of Java and C++, gave it cool C-based name, fixed some Java issues and created new ones, :-) and added some secret patented technology to have poison pill for fools trying to reimplement C# on other platforms -- because as far as MS is concerned, there is only one platform to rule them all.

Java has an additional problem: it was attempt to make applications platform independent ("write once run anywhere") which made sense in the middle of '90, when Windows competed against about a dozen proprietary Unix clones competing on server market and about dozen Real-time embedded operating systems on device market. Big Platform Questions was solved now - only 2 survived, Windows and Linux. :-) So what exactly Java buys you? Platform-independent (so inherently less efficient as single-platform optimized solution) reimplementation of all the tools Linux has for free: set of compilers, make (=ant), web server (=tomcat), you name it, Java reimplemented it. It's called [NIH syndrome]("http://en.wikipedia.org/wiki/Not_Invented_Here") (Not Invented Here). And of course the scourge of XML. Forget about XML designers intent to use XML for computers only, not for humans, and check [YAML]("http://en.wikipedia.org/wiki/YAML") to feel sorry how readable data serialization could be if presentation format was decided by programmers and not by PHBs - [Pointy Haired Boss]("http://en.wikipedia.org/wiki/Pointy_Haired_Boss").

I am not foolish enough to suggest that Java will go away in 3 years - not now.  As Java is GPL it will (unfortunately) stink around for another 10-20 years. Way too many people bet the farm on Java, and they have nothing to lose by repeating "Java is The Solution" (and will lose the face is they concede that bet was wrong). People have funny way to look at their decisions and prove to themselves they are still best imaginable, instead of cutting their losses -- it is called "throw good money after the bad". Don't laugh, psychologists found it, it is deeply ingrained human behavior.

So I am in search of language which is easy to read and write (readability is important: you read more often than you write), handles memory allocation for me, allows for flexible data and doesn't hassle me with typecasting. Big bonus would be ability to integrate tests in some painless ways. I do not expect some big rich corporation to build it for me: First users of this language would be extremely productive hackers who cannot stand any BS - they will hardly work for such a big company.

So far (and for me) Python fits the bill - and I explained you why not C# or  Java. IMHO, YMMV. 

Let the flamewars begin ](*,)

---

### Post by Wybiral on 2007-01-07
> bet the farm on Java
lol

I don't see why your post should start a flame war. I think people need to swallow their pride and really step back to look at their situation. One should never tout a language just because they say it's good. They should really analyze why they like their language and what it can do for them. I've went through a hazing lately studying java since it's going GPL and I am now forced to accept it's existence. Personally, I'm not fond of it... But I can't deny that it does have some practical uses.

First I was weary about the VM.. Virtual machine's mean a guaranteed increase in CPU usage and decrease in runtime speed... Then I did research on the just in time compiler, it sounded like the amazing solution to everything... Then I did research on the CPU usage and speed decrease in having to compile a program every time it's ran. It seemed like there was no hope...

I've discovered that small programs do just fine either raw interpreted, virtual machined, or runtime compiled. So java will have a place in the application world for smaller programs. Python fit's in here as well... Being interpreted will definitely mean a decrease in speed, but an increase in safety and productivity. It only matters when you consider what you need it for.

C/C++ are good (IMO) but require a slightly longer development time, and a slightly steeper learning curve. However, becoming sufficient with them can mean an increase in executable speed and independence from VM's and interpreters (with the loss of raw platform independence).

Assembly is still a useful knowledge because it is able to produce the smallest executables with the most specified solutions (instead of using generalized language functionality from within a compiled language)... But, once again there is an even steeper increase in development time, and a steeper learning curve as a cost of the decrease in size and increase in speed.

One thing I will say is this... I don't ever want to hear people say things like "computers are getting faster and able to store more stuff, so why bother creating smaller/faster programs?"

This is exactly why I threw-up on my previous platform and grew to hate their ways of doing things. Even if computers are faster and come with more storage, it is simply unnecessary to be so careless and inconsiderate of your users (who might not be able to afford a 500gb hard drive with 2gb of ram).

If it can be solved in a smaller/faster approach, we should embrace that. I think that's one of the things that is keeping linux's head above the water. We should recognize this and make an effort to preserve this movement.

Decreased development time is great... For the company! But the users will rather a few more month be put into the product than to have it release premature or bloated and slow. Better solutions exist to solve these problems, such as combining faster/smaller languages like C/C++ with safer easier to develop languages like python/ruby/perl.

With a little common sense, we CAN have our cake and eat it.

---

### Post by phossal on 2007-01-07
Publisher O'Reilly still makes available a decade-old book on C, "Practical C Programming" by Oualline, S., which is a fast-paced, relatively painless introduction to C. It doesn't even really cover the C Library, but is a 'good-enough' introduction to the syntax, loops, functions, and pointers. Unlike a lot of the newer books on languages, it offers info on the programming process - information that was considered fundamental - which you might find useful at least as insight into the times.

If you knew nothing of C or C++, needed a quick overview, and were strictly a student of even higher level languages such as python or java, this is a good way to get it. C++ is a superset of C, they say, so this is a good, short, and easy way to dive in.

---

### Post by WebDrake on 2007-01-08
> **phossal said:**
> If you knew nothing of C or C++, needed a quick overview, and were strictly a student of even higher level languages such as python or java, this is a good way to get it. C++ is a superset of C, they say, so this is a good, short, and easy way to dive in.
An excellent C book is *Programming C* by Stephen Kochan.  I must check out your recommendation.

C++ is broadly a superset of C but is not a strict superset, there are some differences.  For example, in C when using malloc it's preferable not to cast it, whereas in C++ it's obligatory.  On the other hand I believe Objective-C is a strict superset of C.

---

### Post by Wybiral on 2007-01-08
Btw, I managed to get my "Hello world!!\n" program down from 96 bytes to 92 bytes...

[http://p13.wikispaces.com/space/showimage/tinyHello](http://p13.wikispaces.com/space/showimage/tinyHello)

I suggest opening it up with a hex editor and checking it out... The average compiler is not going to let you achieve such small executable sizes...

C++ = 4000 byte
C     = 3092 bytes
GAS assmbly     = 284 byte
Hand optimized = 92 bytes

So yeah, understanding assembly is always a nice ability to have, I wouldn't start off a program in assembly, but I certainly would use it to cut excess off and optimize small portions.

"Disassembled" key...
```

b0 04 =               mov al, byte 4
b3 01 =               mov bl, byte 1
b9 07 80 04 08 = mov ecx, (address, offset: 7)
b2 07 =               mov dl, byte 7
cd 80 =               int 80h
b0 04 =               mov al, byte 4
b9 20 80 04 08 = mov ecx, (address, offset: 32)
cd 80 =               int 80h
b0 01 =               mov al, byte 1
cd 80 =               int 80h

```
Remember that all programs are loaded into 0x08048000

---

### Post by phossal on 2007-01-08
> **Wybiral said:**
> So yeah, understanding assembly is always a nice ability to have...

Can you go the other way though? If you're looking strictly at the assembly, can you *see* structures and functions?

---

### Post by Wybiral on 2007-01-08
Depends how complex and optimized the assembly code is. Personally, I think assembly is a bit easier to decipher than some other source code because of the limited keywords and registers. You can just follow the code around and try to keep mental tabs on the register values and the stack.

I'm getting to the point to where I can look at a hex editor with an ELF executable and see the assembly as plain as NASM or GAS.

But, looking at assembly and seeing C or C++ is different, the compilers use techniques to optimize that make it very difficult to follow. Human written assembly is easy to follow, compiler written assembly on the other hand is not. I'm working on it though, I'm right now studying the compiler's output with some small test programs trying to see how it does the things it does.

BTW, that ""Disassembled" key" I showed in the last post is the end of my hello world program, that's the actual assembly in bytes that does it. If you look at the byte offset's 7 and 20, you will notice that the next 7 characters of each of them make up the phrase "Hello world!!\n"

Just looking at that it's pretty easy to see through some of the opcodes in the hex editor.

System call...
"cd 80"

Move ? to al, bl, cl, dl...
"b0 ??"
"b3 ??"
"b1 ??"
"b2 ??"

Move ? to eax, ebx, ecx, edx
"b8 ?? ?? ?? ??"
"bb ?? ?? ?? ??"
"b9 ?? ?? ?? ??"
"ba ?? ?? ?? ??"

---

