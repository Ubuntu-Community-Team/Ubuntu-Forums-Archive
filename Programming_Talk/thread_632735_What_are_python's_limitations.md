---
title: "What are python's limitations?"
date: 2007-12-05
forum: Programming Talk
---

### Post by jacensolo on 2007-12-05
I finally switched over to ubuntu completely on my laptop, my desktop always has games so I never used it much. Coming from bits and pieces of windows programming, python seems to be "it" for linux users. I understand it's a powerful scripting language as many claim, but what can it really do? For example I haven't seen any full GUI programs written in python. 

So basically I'm wondering how far I could get using it. I don't have any specifics in mind right now, besides a fun project would be a small music player. I also heard python is good for connecting parts of programs made in other languages; could somebody explain to me how this works?

---

### Post by ghostdog74 on 2007-12-05
I assumed when you say "switched over to Ubuntu" , you are talking about newly using it. If that's the case,  so my suggestoin to you is, learn how to use your OS first. No i am not talking about GUI. I am talking about command line. Learn how to use shell commands, learn shell scripting..before you embark on your journey to Python..or whatever next.

---

### Post by jacensolo on 2007-12-05
> **ghostdog74 said:**
> I assumed when you say "switched over to Ubuntu" , you are talking about newly using it. If that's the case,  so my suggestoin to you is, learn how to use your OS first. No i am not talking about GUI. I am talking about command line. Learn how to use shell commands, learn shell scripting..before you embark on your journey to Python..or whatever next.

I'm new to using it full time, but not new to the os.  I'm fairly acquainted with the terminal - I can manage files around and change permissions etc.

---

### Post by ghostdog74 on 2007-12-05
> **jacensolo said:**
> I'm new to using it full time, but not new to the os.  I'm fairly acquainted with the terminal - I can manage files around and change permissions etc.
that's really not enough. learn to use find, grep,sed,awk,split,join,paste,cut,wc,vi,chmod,chown etc.These are some of the most commonly used tools you will need.
Also if you have time go to your /usr/bin directory, do a directory listing and see what commands are available that you can learn. And yes, remember to learn some shell scripting as well.

---

### Post by Geekkit on 2007-12-05
Python, like other languages out there is run in a virtual machine.

Advantages are:

[LIST]
[*]Easy to develop because of being a high level language
[*]Don't have to compile for every flavor of OS (e.g., a C program must be recompiled for 32 and 64 bit architectures
[/LIST]

Like interpretive environments (the byte codes are interpreted for the most part) such as Java, C#, Python suffers from:

[LIST]
[*]Extremely large memory footprints (e.g., take a look at the amount of memory for gDesklets, or in Java, Netbeans 6 which is a behemoth)
[*]Did I say large memory footprint?
[/LIST]

---

### Post by LaRoza on 2007-12-05
> **ghostdog74 said:**
> that's really not enough. learn to use find, grep,sed,awk,split,join,paste,cut,wc,vi,chmod,chown etc.These are some of the most commonly used tools you will need.
Also if you have time go to your /usr/bin directory, do a directory listing and see what commands are available that you can learn. And yes, remember to learn some shell scripting as well.

awk is another programming language, so learning it before Python goes against the recommendation to learn the shell first. Vi is an editor, another app, and sed is also an editor.

Python will be in /usr/bin, and the contents of that directory are all programs, not shell commands.

---

### Post by wolfbone on 2007-12-05
You can do just about anything with it: [http://www.exaile.org/](http://www.exaile.org/)

Interfacing with foreign libraries etc. is relatively straightforward and not something unique to python anyway. Read the docs.

Its limitations aren't really worth pointing out. All I can think of ATM is that it isn't lispy enough, it's purely interpreted (unlike lisp) it's syntax heavy compared to lisp, it doesn't have lisp macros, it isn't lisp.... ;-)

---

### Post by LaRoza on 2007-12-05
> **jacensolo said:**
> I finally switched over to ubuntu completely on my laptop, my desktop always has games so I never used it much. Coming from bits and pieces of windows programming, python seems to be "it" for linux users. I understand it's a powerful scripting language as many claim, but what can it really do? For example I haven't seen any full GUI programs written in python. 

So basically I'm wondering how far I could get using it. I don't have any specifics in mind right now, besides a fun project would be a small music player. I also heard python is good for connecting parts of programs made in other languages; could somebody explain to me how this works?

Python can be used almost anywere, [http://chandlerproject.org/](http://chandlerproject.org/), is in Python and wxWidgets. The Ubuntu installer uses Python. Oblivion uses Python as do many games.

Python can be used for short scripts to large applications. 

My wiki, [http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python) is a good place to start.

It cannot be used for low level access, as it is interpreted. Learning C and Python is a good combination. As mentioned before, Python is interpreted, but you can overcome the potential slowness by writing the most important parts in C, and using them in Python.

---

### Post by ghostdog74 on 2007-12-05
> **LaRoza said:**
> awk is another programming language, so learning it before Python goes against the recommendation to learn the shell first. Vi is an editor, another app, and sed is also an editor.

Python will be in /usr/bin, and the contents of that directory are all programs, not shell commands.

Have you shell scripted before?

---

### Post by LaRoza on 2007-12-05
> **ghostdog74 said:**
> Have you shell scripted before?

Yes.

---

### Post by LaRoza on 2007-12-05
> **ghostdog74 said:**
> Have you shell scripted before?

Yes.

> 
 assumed when you say "switched over to Ubuntu" , you are talking about newly using it. If that's the case, so my suggestoin to you is, learn how to use your OS first. No i am not talking about GUI. I am talking about command line. Learn how to use shell commands, learn shell scripting..before you embark on your journey to Python..or whatever next.


> 
that's really not enough. learn to use find, grep,sed,awk,split,join,paste,cut,wc,vi,chmod,chow n etc.These are some of the most commonly used tools you will need.


Learning shell scripting is useful, but is highly OS specific. Python will run on any OS with a Python interpreter, and is more powerful.

The next quote is strange, you listed several shell commands, two editors, and a programming language. Why not Python (or Perl)? Both of which are installed on Ubuntu.

---

### Post by ghostdog74 on 2007-12-06
> **LaRoza said:**
> Yes.

then you should know that all these tools work together in shell scripts to perform tasks. If the shell one uses does not support text manipulatoin, then one just use tools readily available that does that. Just like in Python, you import modules to perform a task. eg you want to use regular expressoin for complex string manipulations , so you import re. Same in shell scripts, one would "import" (note the double quotes) tools like awk/sed which can do regexp. Agree?

> 
Learning shell scripting is useful, but is highly OS specific. Python will run on any OS with a Python interpreter, and is more powerful.

Not  a problem there is it? There are cygwin for Windows or other unix tools ported to windows. for newer MAC OS , the underlying is still Unix. not to argue with you on portability here. 

> 
The next quote is strange, you listed several shell commands, two editors, and a programming language. Why not Python (or Perl)? Both of which are installed on Ubuntu.
What i listed are all commands/tools that are commonly seen and used in the world of shell scripting long before Python/perl existed. Yes, Python/Perl may be installed in Ubuntu by default, but may not be for other distributions, not by default anyway.

Anyway, I only suggested OP to learn to familiarise with his OS first by trying out common tools on his system and learn shell scripting. He can use Python/perl later for all he wants. so I am not going to say anymore on that.

---

### Post by LaRoza on 2007-12-06
> **ghostdog74 said:**
> then you should know that all these tools work together in shell scripts to perform tasks.

Not  a problem there is it? There are cygwin for Windows or other unix tools ported to windows. for newer MAC OS , the underlying is still Unix. not to argue with you on portability here. 

What i listed are all commands/tools that are commonly seen and used in the world of shell scripting long before Python/perl existed. Yes, Python/Perl may be installed in Ubuntu by default, but may not be for other distributions, not by default anyway.

Python can do the same with the -c switch, as can Perl. I wasn't saying those tools are less useful but that learning 4 other things (shell commands, two editors (sed and vi), a programming language (awk)) is overkill, when one could start with a single language and whatever editor the user is familiar with.

Yes, there is Cygwin, which I use, but that is much larger, and takes longer to install than Python or Perl. On Windows, use Batch files or scripts using the Windows Script Host.

Yes, they are older than Python or Perl, but that has nothing to do with this. CGI scripts were once written is shell scripts, but this should never be done anymore. (Also, CGI is outdated, and shouldn't be used anyway).

---

### Post by yabbadabbadont on 2007-12-06
Not that you would want to, but you can't create either a boot loader, or an operating system using python.  :D

---

### Post by ghostdog74 on 2007-12-06
> **LaRoza said:**
> Python can do the same with the -c switch, as can Perl. I wasn't saying those tools are less useful but that learning 4 other things (shell commands, two editors (sed and vi), a programming language (awk)) is overkill, when one could start with a single language and whatever editor the user is familiar with.

FYI you need to learn how various methods, functions, classes, modules etc in Python work too. if you are reading up on the re module and how to use regexp, i may be reading the man page of sed. So what's the difference ultimately? 

> 
Yes, they are older than Python or Perl, but that has nothing to do with this. CGI scripts were once written is shell scripts, but this should never be done anymore. (Also, CGI is outdated, and shouldn't be used anyway).

let's not detract. remember, my post to OP is only to suggest he learn the shell and its commands/program whatever you call it first. Before he jumps to more feature rich languages...At least, he should get a feel of how his system is like! I am a Python user like you, in fact my number language of choice, however, when it comes to questions like this, I would still try to be objective as possible. Beginners to *nix should always try to learn the shell and its abundance of tools first, before anything else.

---

### Post by SupaSonic on 2007-12-06
To return to the topic:

I've used python a little, it can do a lot. There are however some issues: 
1. The syntax is not so strict as in, say, java. For some it is a good thing, but really, for me not knowing the type of a variable that is passed to a method made me feel really uncomfortable. Also, I couldn't use any aids like Ctrl+space in Java, because again, no type was specified. Ultimately I coded slower than in Java.
2. It's trickier to use in Web-based apps than PHP or Java.

Maybe I'm missing something, I really didn't use much Python. I was however able to create a kind of small parser-type application with GUI and then successfully port it to Windows.

---

### Post by Wybiral on 2007-12-06
> **yabbadabbadont said:**
> Not that you would want to, but you can't create either a boot loader, or an operating system using python.  :D

I doubt most of us could create an operating system in any language (at least not one worth using) :)

EDIT (to the OP):

Python can do a lot! One of the most powerful things about Python is the shear number of libraries available for it. When you're using Python, the most important thing to remember is to look around first because chances are someone has already written the code you're about to write. It's very powerful in that respect. Some of it's modules are simply amazing. Also, whatever isn't possible in Python itself and doesn't already have a module for, it's incredibly simple to write your own modules using C or C++.

---

### Post by pmasiar on 2007-12-06
> **jacensolo said:**
> I haven't seen any full GUI programs written in python. 

yes you did, many of ubuntu admin GUI tools are written in Python.

---

### Post by pmasiar on 2007-12-06
> **ghostdog74 said:**
> learn to use find, grep,sed,awk,split,join,paste,cut,wc,vi,chmod,chown etc.These are some of the most commonly used tools you will need.


I don't use sed and awk, and when (rarely) using any shell command I just look it up in "Linux in a nutshell" book. 

I guess it depends what you do: If you are sysadmin, you play with shell all the time. I am app developer, I set up my environment once and then work hours in it without any changes, adding features and debugging my app.

When I (rarely) need to do something OS-related with files etc, for me (as Python app developer) it is simpler to do it in Python, which has excellent modules for shell tasks, than learning specialized tool with different syntax.

---

### Post by pmasiar on 2007-12-06
> **Geekkit said:**
> 
Like interpretive environments (the byte codes are interpreted for the most part) such as Java, C#, Python suffers from:
[*]Extremely large memory footprints 


IIUC, C# is compiled in .NET.
Python also can be compiled, but most people does not care, because speed is not an issue - code is fast enough (and not too slow as you implied). Ie if my web app needs to access database and send page to browser, DB query delay and HTTP transfer delay dwarf delay by non-compiled code in all cases except google search :-)

Memory footprint is also not an issue in most cases - and if it is, buying 1GB of extra RAM for $100 USD if faster than spending 3 more hours programming it in C, and helps all other programs on the desktop/server  too. Every boos prefers solution with ROI of 3 hours!

Of course, if you have only 16K of RAM, you should be using Forth instead: in can run editor, interactive shell and compiler in 16K (with no OS), and enough is left for code and data :-) I don't think C can do that!

---

### Post by Steveway on 2007-12-06
> **yabbadabbadont said:**
> Not that you would want to, but you can't create either a boot loader, or an operating system using python.  :D

I'm gonna build a Hardware-python intepreter just to prove you wrong. ^^
Well, python is a good choice and you can do everything you want (almost) it is turing complete so go ahead and dive in.

---

### Post by pmasiar on 2007-12-06
> **ghostdog74 said:**
> if you are reading up on the re module and how to use regexp, i may be reading the man page of sed. So what's the difference ultimately? 

Difference is, that in Python, you can do 80% of tasks requiring matching strings without re. 

bigstring.startswith(), bigstring.endswith() and 'pattern' in bigstring works without knowing re, 80% of the time are enough, and are much more intuitive.

Also, even if I need re, Python allows me to do stuff which sed does not: ie sorting files by patterns in filename (yes, you say bash can do that - but I don't want to learn bash regex handling either). 

> suggest he learn the shell and its commands/program whatever you call it first. Before he jumps to more feature rich languages...

My suggestion is, decide what you want to be: 
- shell expert, making living by administering the system, or 
- application expert, like 95% of people are, making living from solving other people problems.

If you are application expert, learn minimum of shell which allows you to squeak by, and then learn universal "scripting" language like Python, which lets you to handle most of task for which admin might use specialized tools, but without learning those tools at all.

Don't misunderstand me, I appreciate admin experts. But they are needed only to enable us solving real world outside problems, build applications which earn money - also for admin's salary.

> Beginners to *nix should always try to learn the shell and its abundance of tools first, before anything else.

I consider that wasted time. I switch between Linux and Windows, and try to squak by, learn minimum of admin tricks to let me solve my real problems, as defined by outside world. I could not care less about awk or sed.

---

### Post by pmasiar on 2007-12-06
> **Steveway said:**
> I'm gonna build a Hardware-python intepreter just to prove you wrong. ^^

Good way to do it could be to implement PyPy in Forth. PyPy is Python in Python, so if you can run it on Forth, you are done. I've seen Pascal in Forth, it was all of 11 pages of commented Forth text (including P-code interpreter). Forth can run on bare metal.

---

### Post by pmasiar on 2007-12-06
> **SupaSonic said:**
> 
1. The [Python] syntax is not so strict as in, say, java. ... for me not knowing the type of a variable that is passed to a method made me feel really uncomfortable. 

Why you care about the type? Use generic functions: len() works on many types. also, type() will give you type if you really need it, but why? Once you get feeling about duck typing, there is no way back.

>  I couldn't use any aids like Ctrl+space in Java, because again, no type was specified. Ultimately I coded slower than in Java.

Some people like IDE, I heard WingIDE is really smart about type inferencing (I never used it myself). I mostly use the same bunch of libraries and just learn the API. But I love that I don't have to cast elements out of a container to proper types, like I have to in Java. And I really hate java's static exceptions, they slow me down a lot. Just plain pain for no gain. Many people convert most exceptions to a runtimeexception and are done with it.

> 
2. It's trickier to use in Web-based apps than PHP or Java.

Not if you use any of leading Python web app frameworks, like TurboGears or Django. Java's Struts was for me  just plain pain to use for small site (less that 100 pages), and PHP code is such a mess unless you are very strict.

---

### Post by skeeterbug on 2007-12-06
> **pmasiar said:**
> 
Some people like IDE, I heard WingIDE is really smart about type inferencing (I never used it myself). I mostly use the same bunch of libraries and just learn the API. But I love that I don't have to cast elements out of a container to proper types, like I have to in Java. And I really hate java's static exceptions, they slow me down a lot. Just plain pain for no gain. Many people convert most exceptions to a runtimeexception and are done with it.


PyDev in Eclipse gives intellisense for a lot of things too. A nice GUI written in Python that comes to mine, is the Postgres database manager (pg-admin).  I also don't see how Django or TurboGears would be more difficult than struts.

---

### Post by pmasiar on 2007-12-06
> **skeeterbug said:**
> I also don't see how Django or TurboGears would be more difficult than struts.

Did you tried both Struts and TG? I did.

---

### Post by skeeterbug on 2007-12-06
> **pmasiar said:**
> Did you tried both Struts and TG? I did.

I didn't want too. I tried reading through the documentation for the springs framework. I told myself I wasn't going there.

---

### Post by CptPicard on 2007-12-06
It's not just Struts, trust me. Problems come when you start integrating a lot of stuff WITH something Struts-like.

Anyway, from my POV, it's pmasiar ftw +1 here on the shell tools issue. In particular for a beginner it is just way easier to learn something like Python and use it for everything, and to learn shell tools if and when they need them. I would recommend reading through some kind of a general list of them early on though, so that you know where to look *if* you don't want to implement something in Python.

The problem with bash+tools is that they are such a rat's nest of tools that each have their own syntax and behaviour glued together by  a shell that does not have the best possible syntax. I mean... all of those tools work differently, and data transfer is through... pipes? Come on. A n00b can have a better environment than that.

That said, my friend's business processes a lot of data and I managed to convince him to let me write him a set of tools on Linux. I refused to work on Windows as I would have had to reimplement a lot. Stuff is implemented as a set of command-line tools as is the unix way, and some of them are Python, some are C programs, some are awk, some are sed, some are combinations of the above... best tool for the job and all that.

---

### Post by pmasiar on 2007-12-06
> **skeeterbug said:**
> I didn't want too. I tried reading through the documentation for the springs framework. I told myself I wasn't going there.

I was forced to learn Struts, and then was lucky enough to be allowed to use TG for couple of small projects, so I can tell from experience, and not from prejudice of reading docs of one system (Struts) to express opinions about other systems: "I tried reading through the documentation for the springs framework... don't see how Django or TurboGears would be more difficult than struts."

Or do you argue that TG and Dj are simpler than Struts? Then we agree.

I used TG (and read about Django - quite similar), and they both are **much simpler** to use than Struts. Even not considering that they use much simpler language, Python, instead of Java.

Let me tell you that Struts is about 100 times more pain to use than TG, for small site with less than 100 pages. I was told that if you have a lot of different  (hundreds and thousands) pages, that pain will pay off, but I don't plan to build that big sites any time soon, so I don't care :-) Springs is rumored to be simpler than Struts, but it is still in clunky Java, so I don't care either.

---

### Post by yabbadabbadont on 2007-12-06
> **Steveway said:**
> I'm gonna build a Hardware-python intepreter just to prove you wrong. ^^
Well, python is a good choice and you can do everything you want (almost) it is turing complete so go ahead and dive in.

That would just move the boot loader into the firmware, and it wouldn't be in python...  It would also make the hardware python-**interpreter** the OS and not the actual python code.  Thank you for playing, please try again.  :D

---

### Post by Geekkit on 2007-12-06
> **pmasiar said:**
> Memory footprint is also not an issue in most cases - and if it is, buying 1GB of extra RAM for $100 USD if faster than spending 3 more hours programming it in C, and helps all other programs on the desktop/server  too.

I'm a bit of a memory cheapskate but more importantly I like to see it run on less resources just to prove that bloatware (i.e., M$ OS methodology) isn't needed. :)

You do have a point about RAM being dirty cheap these days though. I'm still running at 512 MB and I love seeing the fact that Ubuntu 7.04 sits in at a cool 130-ish MB without apps loaded whereas XP sits in at about 180 MB and Vista sits in anywhere between 480 MB and 550 MB in my experience. :)

Plus I guess I'm a sucker for punishment and like feeling the pain of C programming. :)

---

### Post by Wybiral on 2007-12-06
I have 512mb ram too, but I haven't noticed Python causing any memory usage issues. It's not surprising since Python and most of it's libraries were written in C.

---

### Post by Steveway on 2007-12-06
So my CPU is my Operating System because it interpretes the commands that are sent to it?
Well, we could argue till the end of time but the thing that counts is: Python rocks!
EDIT: If Memory or speed are requirements then write the computing-intensive parts in C and use Python for the rest, this is the way most people do it so they get the speed from C and the ease from Python.

---

### Post by yabbadabbadont on 2007-12-06
> **Steveway said:**
> Well, we could argue till the end of time but the thing that counts is: Python rocks!Agreed.  :D
> **Steveway said:**
> 
EDIT: If Memory or speed are requirements then write the computing-intensive parts in C and use Python for the rest, this is the way most people do it so they get the speed from C and the ease from Python.Agreed... again.  :lol:

---

### Post by skeeterbug on 2007-12-06
> **pmasiar said:**
> I was forced to learn Struts, and then was lucky enough to be allowed to use TG for couple of small projects, so I can tell from experience, and not from prejudice of reading docs of one system (Struts) to express opinions about other systems: "I tried reading through the documentation for the springs framework... don't see how Django or TurboGears would be more difficult than struts."

Or do you argue that TG and Dj are simpler than Struts? Then we agree.

I used TG (and read about Django - quite similar), and they both are **much simpler** to use than Struts. Even not considering that they use much simpler language, Python, instead of Java.

Let me tell you that Struts is about 100 times more pain to use than TG, for small site with less than 100 pages. I was told that if you have a lot of different  (hundreds and thousands) pages, that pain will pay off, but I don't plan to build that big sites any time soon, so I don't care :-) Springs is rumored to be simpler than Struts, but it is still in clunky Java, so I don't care either.

Sorry I was saying TG and Django are easier than struts, in agreement.

---

### Post by ghostdog74 on 2007-12-06
> **pmasiar said:**
> Difference is, that in Python, you can do 80% of tasks requiring matching strings without re. 

bigstring.startswith(), bigstring.endswith() and 'pattern' in bigstring works without knowing re, 80% of the time are enough, and are much more intuitive.

Also, even if I need re, Python allows me to do stuff which sed does not: ie sorting files by patterns in filename (yes, you say bash can do that - but I don't want to learn bash regex handling either). 

You don't have to iterate all these things, i know what they are and the different stuffs Python can do which sed cannot. And the whole point I think isn't arguing about re and its specifics either. My whole point is, when one starts to use *nix , maybe or maybe not on a daily basis or as beginners, one should learn about how they work first before anything else. The *nix world doesn't revolve around Python only. 

> 
My suggestion is, decide what you want to be: 
- shell expert, making living by administering the system, or 
- application expert, like 95% of people are, making living from solving other people problems.

my suggestion is only at the standpoint of learning how to use a *nix system. 

> 
If you are application expert, learn minimum of shell which allows you to squeak by, and then learn universal "scripting" language like Python, which lets you to handle most of task for which admin might use specialized tools, but without learning those tools at all.

that, i think, is not a very good advice. An application expert learns everything he can, even the shell. if you can find a job doing only python, good for you. But most don't. 

> 
Don't misunderstand me, I appreciate admin experts. But they are needed only to enable us solving real world outside problems, build applications which earn money - also for admin's salary.

you have a misconception that says admin only does admin and nothing else. I am a system admin, and i can solve Java ( my environment doesn't do python) problems better than my Java app developers, and i don't use Java everyday. Remember, Python is my number one choice. There are lots of different situations happening in this world, so please be more objective.


> 
I consider that wasted time. I switch between Linux and Windows, and try to squak by, learn minimum of admin tricks to let me solve my real problems, as defined by outside world. I could not care less about awk or sed.
that's because you are different. I try to learn everything i can as much as possible, before I die.

---

### Post by jacensolo on 2007-12-06
I went through part of the python tutorial and there some nifty features that weren't in c# or the bit of c++ I treaded through. I'm loving it thus far. 

It just comes naturally, and seems more powerful than vb and basic is.

---

### Post by cwaldbieser on 2007-12-06
I agree that learning some shell tools can be valuable.  Also, when I use python, I tend to use it to write command line tools I can use in conjunction with other shell tools.  Knowing how to use several different types of tools allows you to be more flexible in your approach to different problems.

---

