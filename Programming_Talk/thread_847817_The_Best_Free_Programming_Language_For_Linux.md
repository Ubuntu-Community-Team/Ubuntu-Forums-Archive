---
title: "The Best Free Programming Language For Linux"
date: 2008-07-02
forum: Programming Talk
---

### Post by Spaceman9 on 2008-07-02
There seem to be a lot of  programming languages for writing apps for linux.  I”m wondering which language one would the programmers say is the most commonly used free programming language for writing apps for linux. It needs to be a compiled language and it needs to be free.  Would python or icon be good languages to use? Thankx for any help.

P.S. I have done some programming in MS BASIC and in MS C and in GRASP.

---

### Post by farrell2k on 2008-07-02
Python is interpreted.  C or C++.

---

### Post by dominiquec on 2008-07-02
Python is used for a lot of the applications and customizations in Ubuntu.  You might want to start with that.

If you're looking for something with a bit more speed, try C.

Enterprise business applications? Java.

Too many to mention, each one with their own niches (and zealots.) :-)

---

### Post by pmasiar on 2008-07-02
> **Spaceman9 said:**
>  which language one would the programmers say is the most commonly used free programming language for writing apps for linux. It needs to be a compiled language 

Why it needs to be compiled? Are you aware that static typing for compilation decreases productivity, and JIT compilers can create better code if compiled on runtime?

Best combination for both productivity and speed is to develop in Python, then reimplement parts which slows you down in C, if needed. Most time, it will **not** be needed, because what slows you down are net traffic or database access, and it's out of your control - you cannot speed up those, so why waste time?

---

### Post by Spaceman9 on 2008-07-02
Thankx farrell2k. I kind of hate to go back to c. All those indentations made me feel like I was watching a tennis match. Is python a lot slower or only a little slower?  I could live with a little slower.


Thankx dominiquec. Ok you said python too. How do I get python? Is it in Synaptic?

Zealots? Oh no. I don't want to have to join a religion.LOL


Thankx pmasiar. I only thought it needed to be compiled to run fast. What I wrote for Win apps needed to be compiled to run fast. May be it's different with Linux...I don't know.

---

### Post by kknd on 2008-07-02
> **Spaceman9 said:**
> 

I suggest that you don't care for speed comparisons for *now*. Actually, Python is like 20x slower than C ([http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)), but for real applications, it doesn't works that way =). Usually, the application spends more time waiting for user input, or, for number crunching, you can use a mix of C and a interpreted language (Lua, Python, etc).

---

### Post by dominiquec on 2008-07-02
Hey, Spaceman:

Python is already pre-installed with Ubuntu.  Actually, it comes as a default in almost all major distros.

If you're just starting out, look for the resources in [http://www.python.org](http://www.python.org).  There's documentation in [http://python.org/doc/](http://python.org/doc/).  Go through the tutorial.

Don't jump into GUI programming immediately.  Python is pretty powerful as a scripting language (I use it to get some simple but repetitive tasks done.)  But when you're ready for it, there's lots of GUI toolkits to explore.

If you're a bit more experienced as a programmer, you might want to look at [http://www.diveintopython.org/](http://www.diveintopython.org/).  Actually, there's tons of stuff there even for novices.  You can also install the Dive into Python book directly from the repositories: 

sudo apt-get install diveintopython

It's that popular.

I hope this helps!

---

### Post by Spaceman9 on 2008-07-02
Thank you very much for all the info dominiquec. I looked at all the menus in Gnome but I don't see python anywhere. I'm sure I'll find though. Must be one of those command line things I guess.

---

### Post by JudgeFudge on 2008-07-02
> **Spaceman9 said:**
> Thank you very much for all the info dominiquec. I looked at all the menus in Gnome but I don't see python anywhere. I'm sure I'll find though. Must be one of those command line things I guess.

Just type 'python' on the command line.

---

### Post by HotCupOfJava on 2008-07-02
Well I am VERY partial to Java, but that is an interpreted language :).
You could use C/C++ . Use Synaptic Package Manager to download the compilers for free. It will also handle setting up the paths for you. I might recommend getting the NETBEANS package - it is a powerful Integrated Development Environment (IDE) and you will be able to compile C/C++ AND write Java (if you so choose). Heck, you could even do Ruby. Netbeans will install under your "Applications" menu, and when you open it you have the ability to choose which kind of project you want to work on, and it has a VERY smart textual editor for writing the code. It will allow you to design GUIs and generate the code for you (which is WAY better than trying to manually manipulate the code for appearance, believe me). It is free and and open-source.

---

### Post by Spaceman9 on 2008-07-03
> **JudgeFudge said:**
> Just type 'python' on the command line.

Thank you JudgeFudge. I got this:

bruce@bruce-desktop:~$ python
Python 2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> help
Type help() for interactive help, or help(object) for help about object.
>>> help()

Welcome to Python 2.5!  This is the online help utility.

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at [http://www.python.org/doc/tut/](http://www.python.org/doc/tut/).

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, or topics, type "modules",
"keywords", or "topics".  Each module also comes with a one-line summary
of what it does; to list the modules whose summaries contain a given word
such as "spam", type "modules spam".

help> 

What do I use to save the code Though? Can I just copy and paste it into a text editor?

---

### Post by Wybiral on 2008-07-03
> **Spaceman9 said:**
> What do I use to save the code Though? Can I just copy and paste it into a text editor?

The command line is for exploration and testing. It's good to learn the language with. If you're learning, you probably don't need to save anything to a file, right?

Later, when you're ready to start building something, just open up a text editor and write your program there, save it as "something.py" and execute it from the command line using "python something.py"

---

### Post by pmasiar on 2008-07-03
see wiki in my sig for into to Python, including how to use interactive shell (BTW one of the coolest features Python has - you can learn the language one line at a time)

To edit Python files, any decent editor has Python mode: set "replace tabs with spaces" and "tab is 4 spaces", don't mix tabs and spaces - and you'll be fine.

SciTE is simple good editor, and IDLE is very simple IDE (with all features beginner needs, but no more).

---

### Post by HotCupOfJava on 2008-07-03
Quote:
Originally Posted by Spaceman9 View Post
What do I use to save the code Though? Can I just copy and paste it into a text editor?

Try using the VIM editor in the terminal. It is very minimal, but if you are going to be working from the terminal anyway, you might as well. Just type "VIM <filename>" and the editor pops up. Type "i" to begin typing. Hit "escape" to return to command mode, then "ZZ" (in caps) to exit and save the file.

---

### Post by LaRoza on 2008-07-03
> **HotCupOfJava said:**
> 
Try using the VIM editor in the terminal. It is very minimal, but if you are going to be working from the terminal anyway, you might as well. Just type "VIM <filename>" and the editor pops up. Type "i" to begin typing. Hit "escape" to return to command mode, then "ZZ" (in caps) to exit and save the file.

Vim isn't minimal (well, Ubuntu uses vim-tiny by default); it is a full featured editor with advanced features.

---

### Post by Spaceman9 on 2008-07-03
Thank you Wybiral. That sounds really easy.

 
Thank you pmasiar. Looks like there's a lot to read about this python.


Thank you HotCupOfJava. I was reading a thread here about IDE's. I'll start with VIM and see how it goes. Is there any editor that corrects your syntax for python? I remember the compiler for C did that.

---

### Post by Spaceman9 on 2008-07-03
> **LaRoza said:**
> Vim isn't minimal (well, Ubuntu uses vim-tiny by default); it is a full featured editor with advanced features.

Thank you LaRosa. If it's full featured then may be VIM is all I need. Perhaps that will make my code full of VIM and vigor...haha...or may be not...

---

### Post by LaRoza on 2008-07-03
> **Spaceman9 said:**
> 
Thank you HotCupOfJava. I was reading a thread here about IDE's. I'll start with VIM and see how it goes. Is there any editor that corrects your syntax for python? I remember the compiler for C did that.

Python doesn't have a syntax to really correct :-)

Gedit is a great editor, it is the default on Ubuntu. Get its plugins (search synaptic for gedit plugins) and you can have more than you'll need for programming, including a terminal plugin, and a python shell in the editor.

> **Spaceman9 said:**
> Thank you LaRosa. If it's full featured then may be VIM is all I need. Perhaps that will make my code full of VIM and vigor...haha...or may be not...

Vim is my favourite editor, but it has a learning curve.

---

### Post by Spaceman9 on 2008-07-03
> **LaRoza said:**
> Python doesn't have a syntax to really correct :-)

Gedit is a great editor, it is the default on Ubuntu. Get its plugins (search synaptic for gedit plugins) and you can have more than you'll need for programming, including a terminal plugin, and a python shell in the editor.


Vim is my favourite editor, but it has a learning curve.

I searched for VIM in Synaptic. Oh golly, there's a lot here. Should I install everything for VIM or what do I really need?

---

### Post by LaRoza on 2008-07-03
> **Spaceman9 said:**
> I searched for VIM in Synaptic. Oh golly, there's a lot here. Should I install everything for VIM or what do I really need?

Just install "vim"

```

sudo aptitude install vim

```

vim-full also installs the "gvim" which is really a crime.

---

### Post by Spaceman9 on 2008-07-03
Thank you LaRosa. What about the vim-addon-manager, vim-doc, vim-python, vim-gnome, vim-scripts? vim common is the only thing installed so far.

---

### Post by LaRoza on 2008-07-03
> **Spaceman9 said:**
> Thank you LaRosa. What about the vim-addon-manager, vim-doc, vim-python, vim-gnome, vim scripts? vim common is the only thing installed so far.

I don't know, the "vim" package is enough for me :-)

Vim isn't the easiest editor to start with, you might want to use Gedit first while learning then learn Vim.

Whatever you do, don't install the package "emacs". It wipes your system and installs another OS that lacks a decent editor.

---

### Post by Spaceman9 on 2008-07-03
Ok, I'll start with Gedit and work up to VIM.

And I won't install emacs. But now I need to google emacs. Thankx very much for all your help. Now I'm going to google land.

---

### Post by mssever on 2008-07-03
More vim vs. emacs wars....


I personally install vim-full, which provides syntax highlighting for more languages and file formats than Ubuntu's default. I also like to have gvim: when firefox wants to open up some file, it's quicker to start then gedit with the plugins I use, and starting a terminal program from a GUI application is non-trivial (unless you just start another terminal, in which case you might as well use gvim). Gvim is also a good way to discover new commands: just look through the menus.

Since I learned vim, I haven't seen any reason to spend more time learning emacs. Although, if I ever get around to learning lisp, and wind up liking it, then the case for using emacs would become much stronger.

For programming, I use vim as my general-purpose editor, and gedit with plugins for extended programming sessions or situations that involve editing many files at once. Sometimes I use Scribes--I like its template feature--but that's mostly when I'm forced to use an inferior language such as PHP which can benefit more from extensive code completion tools.

---

### Post by LaRoza on 2008-07-03
> **mssever said:**
> 
I personally install vim-full, which provides syntax highlighting for more languages and file formats than Ubuntu's default. I also like to have gvim: when firefox wants to open up some file, it's quicker to start then gedit with the plugins I use, and starting a terminal program from a GUI application is non-trivial (unless you just start another terminal, in which case you might as well use gvim). Gvim is also a good way to discover new commands: just look through the menus.


vim provides the syntax highlighting, but doesn't install gvim.

---

### Post by xlinuks on 2008-07-03
I consider Visual Basic the best choice for Linux. Some people might disagree.

---

### Post by Spaceman9 on 2008-07-03
Thank you mssever. VIM is a bit hard to understand...with no sleep...I'll figure it out though.


Thank you xlinuks. I'll look into Visual Basic. Is that free? Is it in Synaptic? There are so many different one's to think about.


I discovered cream. It runs on top of VIM. So now every morning I can have cream and vim...yum, yum... If you haven't tried cream with VIM try it.

---

### Post by Wybiral on 2008-07-03
The church of emacs looks down on this conversation.

---

### Post by LaRoza on 2008-07-03
> **Spaceman9 said:**
> 
Thank you xlinuks. I'll look into Visual Basic. Is that free? Is it in Synaptic? There are so many different one's to think about.

It is a Windows only language and generally worthless for most programming needs.

---

### Post by xlinuks on 2008-07-03
> **LaRoza said:**
> It is a Windows only language and generally worthless for most programming needs.

> This new and improved compiler, which supports Visual Basic 8.0 code, is bundled in Mono 1.2.3. In addition to Visual Basic support, this version includes many bug fixes and an almost complete ASP.NET 2.0 API (application programming interface) implementation. WebParts, however, still isn't completely supported. 
[http://www.linuxdevices.com/news/NS9725385854.html](http://www.linuxdevices.com/news/NS9725385854.html)


[http://www.theregister.co.uk/2007/02/21/visual_basic_mono_linux/](http://www.theregister.co.uk/2007/02/21/visual_basic_mono_linux/)

---

### Post by kknd on 2008-07-03
> **LaRoza said:**
> It is a Windows only language and generally worthless for most programming needs.

+1.

It damages your head. Badly.

---

### Post by pmasiar on 2008-07-03
> **xlinuks said:**
> I consider Visual Basic the best choice for Linux. Some people might disagree.

You are in very small minority, and **most** people (95% or more) certainly disagree.

VB on Linux may have sense for someone who knows it, and is not mentally capable learn anything else, or has some existing VB code in need to run on Linux.

Most programmers are ready to learn more than one language, and often chose languages used based on use in other projects - because of support from the community.

Python is easy to learn and one of 3 main languages used by Google, and main language to develop web-based apps - Google App Engine uses Python only. Other 2 languages used in Google (C++ and Java) are used for system functions and where speed (even for price of less flexibility) is important.

And let's not descend into language wars again, I an going to ignore any following flamebaits from this poster.

---

### Post by ByteJuggler on 2008-07-03
I personally would also recommend you get going on Python.  As for editors, use "IDLE", the default Python "IDE" for now, or use Gedit.  Can't remamber if "IDLE" is installed by default on Ubuntu or not, but if not it should be easy to install (and should show up on your menu's under "Programming".)  Learn VIM or Emacs later if you want, at your leisure.

If you feel like it you might try this challenge which helps in learning python: [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/)

(I'm up to level 17 now... :)  )

---

### Post by mssever on 2008-07-03
@Spaceman9,

It's not clear to me whether you understand that a) some of the comments here are intended to be humorous and shouldn't be taken literally, and b) that some opinions are less valuable than others.

Both languages and editors are subjects that spur much debate and have started many a flamewar. In particular, there is a long-standing dispute between vim and emacs. We haven't heard very much from the emacs people, but there are very good programmers on both sides of the dispute. Neither editor is friendly to newcomers.

Then, some opinions are pretty much worthless. I'm not going to single out any in this post, but remember, every recommendation is merely the poster's opinion. Some of those opinions are based on experience and wisdom. Some (like my own) aren't.

---

### Post by Spaceman9 on 2008-07-03
It's been years since I thought about visual basic. I forgot it's for windbloz. Silly me.

pmasiar, xlinuks was just joking. If I hadn't been so tired I supposed I would have remembered visual basic is for Windows and I would have posted LOL instead of asking questions about it. I haven't thought about visual basic since 1993. And I can't say I wanted to then either LOL



ByteJuggler ta very much for the help mate. I'll d/l IDLE and have a butchers.



mssever I'm just learning about python so at this point one could say I'm not entirely sure what to believe. I am sure though most people will be helpful and I personally like a good joke. I just forgot visual basic is for windbloz. By the by, I just started using linux last June so linux is still new to me as well. I'm not an old hand at linux.

---

### Post by ByteJuggler on 2008-07-04
> **Spaceman9 said:**
> I
ByteJuggler ta very much for the help mate. I'll d/l IDLE and have a butchers.


No problem.  Feel free to private-message me if you want.  I'm also still learning Python but I'll help if I can. (I do have quite a lot of general programming experience, being a programmer for a living, which helps.)  Anyway, I decided to learn Python as it's apparently a wonderfully capable language (with the multi platform advantage) that looks like it should have value in many ways, and secondly it is used a lot in Ubuntu in particular, so should you ever want to write/contribute to Ubuntu in any way (which is where I'm headed), Python should stand you in good stead.

---

### Post by danbuter on 2008-07-04
> **LaRoza said:**
> I don't know, the "vim" package is enough for me :-)

Vim isn't the easiest editor to start with, you might want to use Gedit first while learning then learn Vim.

Whatever you do, don't install the package "emacs". It wipes your system and installs another OS that lacks a decent editor.

Just so you know, the emacs thing is a joke/lie. It will not delete your OS. Look up vim vs emacs to see why. Also, good luck learning vim or emacs AND python at the same time.

---

### Post by danbuter on 2008-07-04
IDLE is already on your Ubuntu install, btw.

---

### Post by LaRoza on 2008-07-04
> **danbuter said:**
> Just so you know, the emacs thing is a joke/lie. It will not delete your OS. Look up vim vs emacs to see why. Also, good luck learning vim or emacs AND python at the same time.

Oh, yeah. It was a joke (sort of, but the practicle aspects are the same)

I also don't recommend learning the editor and language at the same time.

> **danbuter said:**
> IDLE is already on your Ubuntu install, btw.

It is? It usually isn't.

---

### Post by Spaceman9 on 2008-07-04
Ta ByteJuggler. I do want to write apps for Ubuntu of course. And apps that can be used on any linux distro and also port them to other platforms as well and all. 


Thank you danbuter for your help. I realize now LaRoza was joking. I'm exploring vim and emacs and also I discovered this gui for vim called Cream. Cream with vim and a few marmite soldiers sounds like a jolly good breakfast.

By the by, I had to install IDLE from Synaptic. It wasn't installed with Ubuntu. Not to worry though. No one can be right all the time. I know sometimes I'm left, but usually I find my way back.

---

### Post by danbuter on 2008-07-04
Oops, sorry about the IDLE thing. I think it used to be installed by default in a prior release. Or maybe that was a different distro... (I am feeling old and confused :)).

---

### Post by GeoffreyBernardo on 2008-12-11
> **dominiquec said:**
> You can also install the Dive into Python book directly from the repositories: 

sudo apt-get install diveintopython


Hi Dominique,

I have installed Dive into Python from the command line, but I can't find it. The same thing with the python documentation, which I installed with symentic.

Please help.:confused:

---

### Post by nvteighen on 2008-12-11
Open /usr/share/doc/diveintopython in Nautilus or even Firefox or Epiphany.

---

### Post by wd5gnr on 2008-12-11
Not to resurrect the Visual Basic thing since I am a crusty old C guy for the most part (and yeah, C++, and Java, and a dozen others back to PL/1 and Fortran). But if you really want the VB RAD sort of thing, try gambas2. It is in the repos, although if you are using 64 bit Hardy it is broken there. You can always go get the DEB from the home page.

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

[http://gambasrad.org/](http://gambasrad.org/)

Pretty slick. Only problem I see is that distributing it requires the interpreter to be correctly in place which is a problem on 64-bit Hardy, for example. Haven't really looked at how you'd widely distribute anything with it though.

---

### Post by directhex on 2008-12-11
> **wd5gnr said:**
> Not to resurrect the Visual Basic thing since I am a crusty old C guy for the most part (and yeah, C++, and Java, and a dozen others back to PL/1 and Fortran). But if you really want the VB RAD sort of thing, try gambas2. It is in the repos, although if you are using 64 bit Hardy it is broken there. You can always go get the DEB from the home page.

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

[http://gambasrad.org/](http://gambasrad.org/)

Pretty slick. Only problem I see is that distributing it requires the interpreter to be correctly in place which is a problem on 64-bit Hardy, for example. Haven't really looked at how you'd widely distribute anything with it though.

Or vbnc is available in Jaunty, if you want something more VB.NET-flavoured

---

### Post by wd5gnr on 2008-12-11
vbnc is ok when coupled with monodevelop but it doesn't have the polish that Gambas has in my opinion. I do have a major C# app I wrote on Windows that I keep thinking I'll port to mono just to see how it does.

---

### Post by ByteJuggler on 2008-12-15
If you want the RAD sort of thing, then also have a look at [Lazarus]("http://www.lazarus.freepascal.org/").  Write-once compile anywhere (meaning Linux/Windows.)

---

