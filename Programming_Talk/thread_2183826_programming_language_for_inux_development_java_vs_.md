---
title: "programming language for *inux development java vs python vs c++"
date: 2013-10-26
forum: Programming Talk
---

### Post by adi06 on 2013-10-26
Hi everyone,

i am student of computer science, and have learned the basic of programming.
I have been working for 1 year on following language and have beginners understanding of them.
C++(25%), VB/C#(40%), Java(40%), PHP(50%), Javascript(20%), Jquery(20%), XML(1.00%), SQL(30%)
That's how much i know about the language if rated out of 100%, estimately!

As recently i started my journey to convert from windows user to Linux Ubuntu 5 days ago. I started to gain interest in developing for Linux based application, for sake of knowledge and fun.

For web part its straight forward to get lampp installed and get going, but for desktop apps, i'm not sure what language to start with.
Please suggest me based on the following criteria, what will suit better. **Learning curve is not an issue, i can start from base if new language is purposed**.
[B]Contenders are: C++, Java & Python
[/B]
Python: i searched a lot of java VS python and most of the ppl choose python BCOZ ITS EASY & LESS CODE.
I Don't care for more lines of code then python's one line=> print "hello world", so besides that, none of the posters mentioned why its better then java.

I'm looking for 1 language and 1 platform/tool-set  i.e(python+quickly) or (c++ & UbuntuGDK) for non-commercial & commercial apps, with NO paid license from the tools i use.
I read pyGT or something don't remember, the problem with that  was the apps created through that were free for non-commercial use and  paid license for commercial.
**I will be making non-commercial apps,  but i don't want to be limited for a paid license for my app if at some  point i want to sell an app.

And if all of that is not available in free license & 1  platform/tool-set, and i had to choose 2  platform/tools, then please suggest some easier transition, i won't want  to learn 2 languages for different consumers and 2 platform/tools. Try to make it relevant to only 1 language & 2 platforms/tool if possible. If not possible, Then my luck, suggest me what i can do then.

I am interested in GUI apps like Variety wallpaper changer, which is made in python, which can interact with online servers/APIs and fetch the info on desktop.
I liked that idea, as i'm new in development, such thing fascinates me. And there might be some point where my desktop app will interact with website for authentication/app registration or downloads of products etc.

A GUI based platform that could do out of box everything, if possible. like bash scripts, system calls, web services, and a **Good looking GUI**, this is probably most important. No OpenGL type hand codded GUI, that would be a overkill for me :)

Python is slow in speed: c > c++ > java > python. Don't know how much that would effect.

Sorry for my noobiness, please help me on this.

---

### Post by JKyleOKC on 2013-10-26
I would choose python over java, mostly because python is more widely used these days and expertise with it would be a more valuable asset in my repertoire. However, I personally prefer bash scripts for almost everything that I do; my commercial programming for quite a few years now has been done with Delphi, which is sort of a cross between Visual Basic and Pascal with the ease of building GUI apps found in VB, and the performance found in Pascal. Like all tools, it has suffered a bad case of bloat over the years and consequently I'm still using version 5.1, which reached end-of-life many years ago but which still serves my needs. Note that almost all my commercial work is still for the Windows platforms; while I use Linux as my primary system, my clients are still with Microsoft!

For many years I used C, starting from the original K&R version, and became quite fluent in it. C++ began basically as a wrapper around C itself, to provide object-oriented capabilities, but quickly developed component libraries that turned it into essentially a separate language.

In your position, the first thing to decide should be exactly what you want to do with a language. Automating office procedures requires a vastly different tool set from tweaking the operating systems, and while any Turing-complete language could do either job, no single language can handle both types of task efficiently.

No matter what language you choose, though, try to become comfortable with the underlying hardware. It helps greatly if you know what has to be happening behind the scenes, although the days of being able to debug a program by single-stepping through the machine-language commands are pretty much history...

---

### Post by Bashing-om on 2013-10-26
adi06; Well, well ...

Programming in general is using what you are accustomed to using. Linux is very liberal with your choice.
Keep in mind though that in linux, there is the kernel, and all is added to this kernel as a module. How you make and attach that module varies widely with the application in particular to what it's end function may be. Editing an existing module, you are going to be working with that source code, in what ever language/prolog that was used originally, prior to (re-)compiling. There is no better teacher than reading and understanding some one else's code.

For ubuntu, you can never go wrong learning - as you now know - some flavor of "C", and python. But one warning I have learned the hard way, If you want to be proficient in "C" have a good understanding of assembly. As one instance; pointers in "C" are difficult to grasp if you do not know assembly; and what is actually going on at the hardware level.  It is all a matter of addressing and moving data about.

"C" Has been around for many many years while many others have fallen out of favor. The reason "C" is still prevalent ? .. Because it works and is versatile, applicable to any condition.

If you can think in "C" you can do anything you can imagine, however, other tools might make the chore somewhat easier ... as in python with it's libraries of support.

This is just my opinion, and it is prejudiced as I prefer "C", That was also the 1st high level language I learned ! That foundation has served me well.

Programming is learned by programming -> learning what tools suites you best for a given objective.

[INDENT][INDENT]any start is better than no start
[/INDENT][/INDENT]

---

### Post by adi06 on 2013-10-26
@[[COLOR=#000000]JKyleOKC[/COLOR]]("http://ubuntuforums.org/member.php?u=374258") thanks for your input, as you prefer python over java, can you point me any GUI editor or platform, i .e (quickly+python) or any good library or system for desktop development. (i just saw a short clip of 'quickly' and don't even know what it is, only that it uses python and used to make GUI aps)
 As linux is built on C, will i be able to hook modules of python to Linux kernel, as Bashing-om described, and can Python run bash scripts.
My understadning is as python is just a language, then what i need to make GUI of python app? as  C# works with .net controls and forms in VS. what is its equivalent for python for Linux GUI apps?

@Bashing-om thanks for your reply,  the big thing i would have to learn is memory management, which can cause quite a mess if not handled, but i'm scared if ASM the 1s,0s are scary 101010101010101
Ok an other thing, u mentioned C but what about C++, where is its role? i don't see any post on linux apps with C++.
Can i use C++ instead of C. and is there anything i must know about the difference of using either one?
I also read that C++ compiles libraries can't be used with C compiled libraries, but C can work with c++.

---

### Post by llanitedave on 2013-10-26
Another advantage of Python is the rich diversity of libraries you can use with it.  For GUIs you have your choice between Tkinter, wxPython, PyQT, and a couple of others.  For numeric processing there's numpy, for nice looking charts you have Matplotlib, and if you want raw performance it's easy to use Cython.

There are lots of editors available, I use Geany but your choices are almost infinite.

---

### Post by jamesisin on 2013-10-27
Like I mentioned in our PM, Ruby(Rails) is a good area for someone interested in Linux.  I also really like Perl and JavaScript when I was programming.  And most definitely learn BASh (and then move on to another shell if it suits you).

---

### Post by adi06 on 2013-10-27
@[[COLOR=#000000]llanitedave[/COLOR]]("http://ubuntuforums.org/member.php?u=41459") thanks for your reply, great information.
I guess i'll go with python, i heard about Geany, and i think i;ll try that as well.
Too many GUI tools, what about UbuntuGDK, or something, what is that? is it GUI toolkit or some library for ubuntu programming.

@[[COLOR=#000000]jamesisin[/COLOR]]("http://ubuntuforums.org/member.php?u=612780") thanks. i will try Bash scripting, and will follow your post on ur site. Also i see a lot of people using Pearl, i think i must learn that as well. Thanks mate :)

---

### Post by adi06 on 2013-10-27
Also Can someone please explain what are Qt, QML and Ubuntu SDK, and what advantages i get over those instead of Python, except for mobile compatibility, i won't be going in mobile.

 Also can i make linux widget or modification to Desktop interface with python? like custom theme, custome menues and behavior or modification to DASH or Settings etc.

---

### Post by JKyleOKC on 2013-10-27
> **adi06 said:**
> @[[COLOR=#000000]JKyleOKC[/COLOR]]("http://ubuntuforums.org/member.php?u=374258") thanks for your input, as you prefer python over java, can you point me any GUI editor or platform, i .e (quickly+python) or any good library or system for desktop development. (i just saw a short clip of 'quickly' and don't even know what it is, only that it uses python and used to make GUI aps)
 As linux is built on C, will i be able to hook modules of python to Linux kernel, as Bashing-om described, and can Python run bash scripts.
My understadning is as python is just a language, then what i need to make GUI of python app? as  C# works with .net controls and forms in VS. what is its equivalent for python for Linux GUI apps?Sorry, I can't help much with such details because I don't use python myself (nor java either). When I need to get that close to the machine, I use C in Linux or Delphi in Windows, but I try to stay with the Unix philosophy and use shell scripts to the greatest extent possible.

C has been described as simply a wrapper for DEC PDP-8 assembly language, and when you study its history there's a lot of truth in that. Don't be frightened of the 1s and 0s -- they're "machine language" and "assembly language" is a step above that. It's using opcodes such as "LDA Someplace" to stand for the bit pattern that means "Load Register A from" (LDA) and the unrelated bit pattern that's the address of a memory location (Someplace) so that the human mind doesn't have to deal with bit patterns, and can concentrate on the intent behind such instructions.

A language like C, then, hides the whole idea of registers and memory addresses behind another layer of symbols, so that the programmer can concentrate more intently on the reason behind the instructions.

And every higher-level language continues that process; once somebody came up with a way to draw a GUI and wrote a working set of instructions in C or some other language, that package could be re-used by anyone else -- and the idea of "components" or "objects" was born.

Every language in use today, so far as I know, contains some method for launching an object without knowing what the "birth language" of that object might be. This implies, correctly, that once an object is compiled into a sequence of machine language bit patterns (AKA an executable routine or program) then any other language will be capable of using it. In some cases, making the "launch" routine and the target object fully compatible may be more trouble than it's worth, though -- although certain "calling conventions" are sufficently universal that this isn't usually a significant problem.

Bottom line: any language with which you become comfortable will suffice for desktop development. Some, however, will be more effective than others. The tradeoff between comfort and effectiveness, unfortunately, is something you'll have to decide for yourself along the way. For me, "bash" (the language of shell scripts in *buntu) fits, most of the time. It's far more powerful than it might appear at first look!

Second bottom line: you can never know too many computer languages. At times you can become confused when you work with two different languages that are almost, but not quite, clones of each other -- such as C and Delphi/Pascal. However, the more languages you know, the better will be your ability to pick the "right" tool for any task you face.

Hope this helps!

---

### Post by adi06 on 2013-10-27
Thanks for such detailed information. I will certainly remember that. Too many votes for learning BASH, I'lll definitely learn it.
Besides many people have suggested Python. And it seems good option for me as well.
Pearl is next to do after Python and Bash scripting.

Now looking for GUI toolkit and can't decide which to choose.
I would go for one that supports Python3 which is TKinter and QT, TKinter GUI is old school QT is currently most popular and rich featured.
I'm looking forward to PyQT. But not sure where to begain, what IDE and what else to know by using PyQT, still searching.
its 3am here and searching 2 hours.

Well i hope for best :)

---

### Post by JKyleOKC on 2013-10-27
Most any text editor will do at the start; a full-fledged IDE is nice once you know what you are doing, but at the start it only offers an additional layer of details to be learned. I use "leafpad" and sometimes "mousepad" as my editors but "gedit" is the one that comes with mainstream Ubuntu. I'd also suggest getting at least a starting handle on bash before diving into any lower-level languages. Nothing builds confidence so much as putting together a sequence of instructions and seeing that they do actually accomplish what you intended them to do...

---

### Post by Bashing-om on 2013-10-27
adi06;

Take JKyleOKC's advise on bash scripting (very powerful in it's own right). As in introduction to programming on a linux system, can do no better.
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by adi06 on 2013-10-27
> **JKyleOKC said:**
>  I'd also suggest getting at least a starting handle on bash before diving into any lower-level languages. Nothing builds confidence so much as putting together a sequence of instructions and seeing that they do actually accomplish what you intended them to do...

On my way sir, Great advise. Will go for it. Thanks,

Also i have made a decision to choose PySide as a GUI framework bcoz of Free LGPL License. and its also a good framework.
Will start looking at Bash now on.

---

### Post by Bachstelze on 2013-10-28
I would beg to differ on Bash. Unless you are a system administrator who needs to perform a lot of tasks on the command line, only the most rudimentary knowledge of bash scripting (&&, ||, if conditionals and for loops) is needed. Of course, you can always learn Bash as a programming language in its own right if you are so inclined, but Bash knowledge is certainly not a prerequisite for anything, and I would argue Bash is not at all the ideal first language.

---

### Post by GeneralZod on 2013-10-28
> **adi06 said:**
> 
Ok an other thing, u mentioned C but what about C++, where is its role? i don't see any post on linux apps with C++.


Pretty much the entirety of KDE (from toolkit - "Qt" - to practically all of its apps) are written in C++, as are popular apps such as Firefox, Chromium,  Open/LibreOffice, Abiword etc.  gcc was pure C but is steadily adopting more and more C++ into its codebase.

> 
Can i use C++ instead of C. and is there anything i must know about the difference of using either one?


Of course.  C vs C++ is a pretty common discussion (or flame-war :)).  C++ is certainly much more complex than C and is a bit of a mess of a language, but I personally find that the mess of the C++ language itself translates to much less messy code with much less tedious (and error-prone) boilerplate, which often runs at precisely the same speed as the corresponding C.  

> 
I also read that C++ compiles libraries can't be used with C compiled libraries, but C can work with c++.

That's mostly correct, but you can always write a thin "C" wrapper around your C++ code.  C++ libraries such as [llvm](http://llvm.org/) do precisely this.

---

### Post by JKyleOKC on 2013-10-28
> **Bachstelze said:**
> Bash knowledge is certainly not a prerequisite for anything, and I would argue Bash is not at all the ideal first language.I agree with the first half of that sentence, but disagree with the second. My recommendation of it as a first language is based on two points: first, it gives immediate results the student can see, and thus builds confidence; second, it's a well-structured language and thus serves as an introduction to all the building blocks of what used to be called "structured programming" and now goes by the name "best practice."

There's really no need to try to memorize all of the exotic capabilities built into the latest bash versions, though. Simply being aware that they exist is adequate. And the FullBashGuide blog that Bashing-om linked to above is great! Even though I've been a bash enthusiast for more years than I can count at the moment, I learned a few new things from it (and more than a few things to avoid, such as attempting to parse the output of "ls" in a script).

---

### Post by adi06 on 2013-10-28
@[[COLOR=#000000]GeneralZod[/COLOR]]("http://ubuntuforums.org/member.php?u=17961") Thankfor your reply, you explained my questions well.
I would go for C++ if i would after python bcoz i already know basic C++, class, objects, inheritense, polymorphism and other stiff.

@[[COLOR=#000000]Bachstelze[/COLOR]]("http://ubuntuforums.org/member.php?u=51114") thanks for your suggestion. I know when it comes to programming everyone have their opinion. thats why i tried to limit my question based on criteria of mine.
Only language for development i will chose for now is python as suggested by many. But Bash is a powerful scripting language, and can automate quite a list of task easily. and my OS teacher always Rant about BASH/shell so thats why i thought it would be a nice idea to learn it along.

Only problem i'm facing right now is less tutorial or books on PySide **than **PyQT, i know there is not much difference, but i'm too new to be bullied by the migration of tutorials fro one to another. Besides there are no binaries for Ubuntu for 13.10, so i have to compile them myself. and that is what i'm not familiar with, but i hope i'll get it done some way. Off to Google for that hehe.

Thanks all for replying.

---

### Post by Bachstelze on 2013-10-28
> **adi06 said:**
> 
Only problem i'm facing right now is less tutorial or books on PySide then PyQT,

There is [an excellent book]("http://www.amazon.com/dp/0132354187/") on PyQT. Although I am a very low-level type of guy, I find it very helpful when I want to quickly code a small graphical app to do something.

EDIT: Never mind, I see you have chosen PySide (first time I ever hear of it). You meant "than", not "then". ;)

---

### Post by adi06 on 2013-10-28
> **Bachstelze said:**
> There is [an excellent book]("http://www.amazon.com/dp/0132354187/") on PyQT. Although I am a very low-level type of guy, I find it very helpful when I want to quickly code a small graphical app to do something.

EDIT: Never mind, I see you have chosen PySide (first time I ever hear of it). You meant "than", not "then". ;)

Thanks for typo, i corrected it. And i have read many suggestion for that book.
PySide is like Free version of PyQT; PyQT is paid for comercial development and almost same except some library names or some functions. so Its easy to follow that same book for either framework. but as i'm new there might be probably quite no of differences, and i'm hesitated for PyQT books for PySide :wink:

But i'll use that book.

---

### Post by llanitedave on 2013-10-29
The book seems a bit dated.  Both Python and QT have evolved significantly since 2007.  Unfortunately, I  have no better suggestions at the moment.  I went with wxPython for my own work, since it seemed better documented at the time, but there's a lot to like in QT.

---

