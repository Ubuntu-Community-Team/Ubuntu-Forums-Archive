---
title: "Windows Vs Mac Vs Linux programming abilities"
date: 2010-06-14
forum: Programming Talk
---

### Post by 13k on 2010-06-14
Hello,

Windows and Mac seem to be more unified than Linux.  Shouldn't Windows and Mac be better at programming than Linux?  I use Windows XP, I don't want to try Mac, I use Ubuntu and Puppy Linux in a "Live-USB".  I've never taken computer science, engineering, or anything related to computers.  So i ask you, which OS is the best for programming and why?

---

### Post by sdennie on 2010-06-14
Moved to programming talk.

As a side note, there probably is no right answer here.  ;)

---

### Post by DCGStudios on 2010-06-14
There is no "best" OS for programming really.. Linux, as usual, is generally less user friendly and requires slightly more experience to be fully utilized.. Generally the complier and the language itself brings the "abilities" factor. 

If you want something easy, and something where you can focus on your language more then anything, I would say windows. 

If you want to have full utilization of your system and your not afraid to get your hand a little dirty in your OS, then Linux.

---

### Post by soltanis on 2010-06-14
Is this a loaded question or what?

There's no real answer here. Windows, Mac, Linux, they all have their own semantics on how you write programs that work under each. Some, like Mac and Linux (and BSD and other UNIXes), conform to some standards (POSIX, SUS) on how their operating systems behave and export functions to you, with the intention that code you can write on one system can be ported to another. Others, like Windows, are not really interested in you being able to move your code from one platform to another and hence do not conform to standards. I should also point out that while Mac OS X does conform to POSIX and a few other UNIX specs, it has its own little world in which there is a way of doing things completely separate from the UNIX way of doing things, so just be aware of that.

---

### Post by DanielWaterworth on 2010-06-15
I can't really put forward a case for mac or windows, because I don't have much experience programming on them. On Linux however programming is fun. Libraries and header files have places to reside which helps a lot. Libraries complete which sources are easy to download thanks to package managers varies. Linux conforms to POSIX and generally has well designed APIs and pushes good practises. Although Linux is becoming more of a commodity operating system, it has it roots as an OS for coders and it shows if you dig below the surface.

---

### Post by ja660k on 2010-06-15
**DONT** use windows...
Mac and linux are more or less the same. the good thing about linux is you can apt-get install <language-here>

but for mac, you'd have to compile it from source, update $PATH etc, etc. things that apt does automatically.Not that that is bad... but for some people a pain.
and i quite like some of the apps that help programming in mac, such as: 

textmate, a sexy text editor
coda, remote text editor
expandrive, mount remote file-systems like usb devices.(FTP, SFTP etc.)

but these, you all have to pay for.

for the most part, linux is better because really, you dont need a fancy text editor right? and EVERYTHING is at your fingertips...
and the community support cannot be beat, and something like 95% of web servers are some flavour of *nix

---

### Post by trent.josephsen on 2010-06-15
I think the real danger with Windows programming is that it's so frequently done wrong.  There are an awful lot of C# or VB programmers that don't really understand programming beyond their "native language" and have no idea how it should really be done.  Unfortunately, a large number of them think they have the experience to teach others to program, and hence we have a wide range of bad tutorials.

Speaking from personal experience, people who only know how to code on Windows are encouraged to use Microsoft-sanctioned tools, making their code unportable and severely limiting the range of their practical experience, whereas people who code on Linux are encouraged to write portable code and learn a wide range of skills.  Which is to say, "it depends on how you do it."

---

### Post by Queue29 on 2010-06-15
> **trent.josephsen said:**
> I think the real danger with Windows programming is that it's so frequently done wrong.  There are an awful lot of C# or VB programmers that don't really understand programming beyond their "native language" and have no idea how it should really be done.  Unfortunately, a large number of them think they have the experience to teach others to program, and hence we have a wide range of bad tutorials.

Speaking from personal experience, people who only know how to code on Windows are encouraged to use Microsoft-sanctioned tools, making their code unportable and severely limiting the range of their practical experience, whereas people who code on Linux are encouraged to write portable code and learn a wide range of skills.  Which is to say, "it depends on how you do it."

Just stop with the over generalized B.S. It makes you look like a tool.

---

### Post by doas777 on 2010-06-15
in the long run, it;s the dev tools that matter far more than the environment. When your working in Visual Studio, Windows programming seems a snap, but when your writting w32 code in notepad, that feeling is long gone. the same goes for Mac and Linux. 

personally when i need to get somthing out, with a minimum of custom research, I use .net. but if i'm coding for fun or personal, I use python on *nix. linux is just so much more transparent, so you can do some really interesting stuff with it. with MS/Mac, you code the MS/Mac way.  with linux, it's up to you. that can be both a boon an a bane however.

---

### Post by DanielWaterworth on 2010-06-15
> **Queue29 said:**
> Just stop with the over generalized B.S. It makes you look like a tool.

If he's over generalising, you're over sensitive.

It is true that window's programmer are encouraged to use Microsoft tools and that some of these are based on .NET which is abstracted and can cause some programmers to pick up bad practises which could conceivably be passed on to others. He may be stretching it a bit, but that's no reason to slate him.

---

### Post by Milliways on 2010-06-15
> **13k said:**
> Hello,

Windows and Mac seem to be more unified than Linux.  Shouldn't Windows and Mac be better at programming than Linux?  I use Windows XP, I don't want to try Mac, I use Ubuntu and Puppy Linux in a "Live-USB".  I've never taken computer science, engineering, or anything related to computers.  So i ask you, which OS is the best for programming and why?

At the risk of perpetuating this "religious" debate, there is no single answer.
It also depends on what you mean by programming - scripting in 'NIX or Mac is head and shoulders above Windows, but writing a compiled program is a different matter.

I have programmed many different systems (including my own OS), but am not a professional programmer.

If you are writing a command line program there is not much difference, although 'NIX is more suited to applications which are not simple linear programs, due to its support for messages.

GUI programming is a different matter. Windows has a single approach which is documented (if inconsistently and often obscurely), but assumes you are programming in c++. The change to .NET makes a fundamental change.

Mac can't seem to settle on a language, but I don't have enough experience to comment.

'NIX has a number of competing GUI libraries. None are well documented (e.g. there doesn't even seem to be a book on gtk2+)but you can write good portable apps.

---

### Post by conundrumx on 2010-06-15
> **soltanis said:**
> ... I should also point out that while Mac OS X does conform to POSIX and a few other UNIX specs, it has its own little world in which there is a way of doing things completely separate from the UNIX way of doing things, so just be aware of that.

OSX is actually the only "certified" UNIX.  It's POSIX compliant, and everything at the CLI is essentially the same userland as Ubuntu, with some tools being BSD instead of GNU versions.  The only thing that might trip you up is HFS+ is by default case **insensitive.**

> **ja660k said:**
> ...

but for mac, you'd have to compile it from source, update $PATH etc, etc. things that apt does automatically.Not that that is bad... but for some people a pain.

That's not true.  There are two projects which provide package management for OSX, (Fink and Macports) one of which is based on apt.  In addition to that, many large F/OSS projects (such as nmap) provide OSX installers.

---

### Post by trent.josephsen on 2010-06-15
> **Queue29 said:**
> Just stop with the over generalized B.S. It makes you look like a tool.
I wasn't trying to overgeneralize, but to call attention to a pitfall that, in my experience, is common among people who develop exclusively for Windows:  its very popularity can be a crutch for programmers who prefer doing everything the familiar way over improving their craft.

I didn't intend to malign Windows as a programming platform, or Windows programmers in general; I know many good programmers use Windows.  Apologies.

---

### Post by escapee on 2010-06-15
> **Milliways said:**
> 

Mac can't seem to settle on a language, but I don't have enough experience to comment.



Just clarifying, Mac has been settled with Objective-C as the main language for a loooong time now, though support for several other languages exist, most with bridges to C and Objective-C.

---

### Post by dv3500ea on 2010-06-15
I find Linux makes programming the easiest. (I have programmed on Linux and Windows, but not Mac).

Basically, Linux assumes you will want to create your own programs - mainly because it itself is programmed by a lot of the people who use it. 

Most Linux distributions come with lots of languages installed out of the box (eg. C, perl, python). On Windows, you have to install them and to use interpreted languages, you have to get anyone else who wants to use your program to install the language first.

Linux also normally has at least code highlighting supported by its text editors (eg. gedit, nano) and there are plenty of IDEs available to install (such as the excellent [geany]("apt:geany")). On Windows, again, you have to install text editors for programming (like notepad++).

Having to install all these things is all right for advanced users, but for those new to programming it can be very daunting.

---

### Post by doas777 on 2010-06-15
> **trent.josephsen said:**
> I wasn't trying to overgeneralize, but to call attention to a pitfall that, in my experience, is common among people who develop exclusively for Windows:  its very popularity can be a crutch for programmers who prefer doing everything the familiar way over improving their craft.

I didn't intend to malign Windows as a programming platform, or Windows programmers in general; I know many good programmers use Windows.  Apologies.

the other thing to consider is that not every programmer should be "Great" or even "Good" with the economic circumstances of a capitalistic society. some few companies need people that can write drivers in x64 assembler without taking their hands off the keyboard once, but most need lots people to make stupid web apps and flashgames. since the guy who is fluent in assembler starts at 90K USD, they don't want "Great" programmers to work on intranet pages. they want mostly-qualified affordable programmers. 

Community colleges help provide employeers with people that are focused on a platform or series of platforms needed to just get the job done. no manager in a business wants to hear a longwinded dissertation on how C is better than C++. they just want to hear them when it will be done and that it will be on or under budget (and that time better mesh with their preconceptions).

Last week, I solved a server tier problem in an (IMO) incredibly kewl way, doing somthing no one else here could have pulled off, and it works gloriously. Now that it;s done, they are really happy that I fixed it, but their eyes glaze over if i try to tell them how. they just don't care. 

if you work in a business organization, you may realize that no one will ever notice that you correctly nested a try-finally inside a try-catch for file access, and used delegates to provide safe closing. in fact, you may find yourself being eclipsed by a younger guy who writes sloppy unmanageable spaghetti code, simply because they got it going in less time. after all, the user can't see that you wrote an textbook N-tier stack, and that the other guy smerged all his code directly into an ASPX, hardcoding connection strings, and embedding injectable SQL statements. all they can see is that someone else did it faster.

---

### Post by Penguin Guy on 2010-06-15
> **trent.josephsen said:**
> I think the real danger with Windows programming is that it's so frequently done wrong.  There are an awful lot of C# or VB programmers that don't really understand programming beyond their "native language" and have no idea how it should really be done.  Unfortunately, a large number of them think they have the experience to teach others to program, and hence we have a wide range of bad tutorials.

Speaking from personal experience, people who only know how to code on Windows are encouraged to use Microsoft-sanctioned tools, making their code unportable and severely limiting the range of their practical experience, whereas people who code on Linux are encouraged to write portable code and learn a wide range of skills.  Which is to say, "it depends on how you do it."
I've done quite a bit of programming using Windows and Linux and I back you up here. I'd also like to add that Windows tends to give you a lot assistance when programming (properties menus, code snippets, GUI editors, etc), making it easier to make the program, but meaning the program internals aren't pretty and it's less portable.

Linux is for programming well, Windows is for programming quickly.

---

### Post by linux-hack on 2010-06-15
like DCGStudios sad, there is no "best" OS for programming .. It depends on what you like and in witch one you like do develop more ... Each one has some thinks that the other one doesn't but in the end you can do the same thing on all of them.. The question is with programming language is better :D

---

### Post by nrs on 2010-06-15
> **conundrumx said:**
> OSX is actually the only "certified" UNIX.  It's POSIX compliant, and everything at the CLI is essentially the same userland as Ubuntu, with some tools being BSD instead of GNU versions.  The only thing that might trip you up is HFS+ is by default case **insensitive.**
Being a "certified" UNIX doesn't really mean anything other than you had spare $. I'm not saying OS X is completely UNUNIX, but come on, there is no denying it's generally different than most others. 

It doesn't use X for example. Not really a requirement for UNIX, but it is something most UNIXes use. It can obviously run it, but it's more of a 'bonus' feature. The OS doesn't use it in any way AFAIK. 

Consider it's filesystem hier. For development it goes something like /System/Libraries/.../.../... It makes invoking GCC from the command line a very big PITA requiring lots of -Is and -Ls

---

### Post by nrs on 2010-06-15
Personal preference: 
*nix -> OS X (technically a *nix) -> Windows. 
Reason: 
I feel *nix offers a better programming environment. For me it just isn't about the compiler or the libraries, but the whole package. Shell (Bash/Zsh) + Utilities (Sed/awk/grep/...) + filesystem hier + everything else that escapes the top of mind. 

Windows development can only be done semi-painlessly through an IDE like Visual Studio, IMO. I don't really care for Visual Studio. 

I also HATE HATE HATE the Win32 API. Hungarian notation is everywhere and it's horrible. I just don't like the general style of designing GUI applications 'natively' in C/C++.

C# makes things better, but I have no interest in using what is in practice a proprietary environment. Yes, yes, the core is open, there's Mono, etc. but be realistic, if you're a C# developer on Windows you're going to be using all the parts that aren't open, like winforms, etc.

And that's my biggest reason for avoiding Microsoft libraries / technologies: they aren't open or cross-platform. I want to run my applications anywhere I want / can.

---

### Post by conundrumx on 2010-06-15
> **nrs said:**
> Being a "certified" UNIX doesn't really mean anything other than you had spare $. I'm not saying OS X is completely UNUNIX, but come on, there is no denying it's generally different than most others. 

It doesn't use X for example. Not really a requirement for UNIX, but it is something most UNIXes use. It can obviously run it, but it's more of a 'bonus' feature. The OS doesn't use it in any way AFAIK. 

Consider it's filesystem hier. For development it goes something like /System/Libraries/.../.../... It makes invoking GCC from the command line a very big PITA requiring lots of -Is and -Ls

You have no idea what you're talking about.

You define "UNIX" as "Linux," but it's not.  X11 isn't a defining characteristic of UNIX/*nix systems any more than bash is.  Is it a commonly included program?  Of course it is. [I can run X11 on OSX, too.]("http://i.imgur.com/xiqBR.png")  I'm not sure what your gripe about the filesystem has to do with poor $PATH settings, [but the defaults work just fine for invoking gcc.]("http://i.imgur.com/hJGhc.png")

---

### Post by splicerr on 2010-06-15
> **Milliways said:**
> 'NIX has a number of competing GUI libraries. None are well documented (e.g. there doesn't even seem to be a book on gtk2+)but you can write good portable apps.

Bollocks! Both GTK+ and Qt are very well documented.

---

### Post by nrs on 2010-06-15
> **conundrumx said:**
> You have no idea what you're talking about.

You have no reading comprehension. 
> **conundrumx said:**
> 
You define "UNIX" as "Linux," but it's not.  X11 isn't a defining characteristic of UNIX/*nix systems any more than bash is,

> **me]
It doesn't use X for example. *_**Not really a requirement for UNIX**_**, but it  is something most UNIXes use.***
[/QUOTE]
[QUOTE=conundrumx said:**
> 
.  Is it a commonly included program?  Of course it is. [I can run X11 on OSX, too.]("http://i.imgur.com/xiqBR.png")  I'm not sure what your gripe about the filesystem has to do with poor $PATH settings, [but the defaults work just fine for invoking gcc.]("http://i.imgur.com/hJGhc.png")
Mhmm. It's complety the same. Which is why you need the OS X specific -framework option if you want to avoid the problems I mentioned. Try including / linking OpenGL/AL/SDL. -Is-Ls$PATH-framework

---

### Post by nrs on 2010-06-15
> **Milliways said:**
> 
'NIX has a number of competing GUI libraries. None are well documented (e.g. there doesn't even seem to be a book on gtk2+)but you can write good portable apps.
[http://doc.qt.nokia.com/4.4/index.html](http://doc.qt.nokia.com/4.4/index.html)
> 
[http://doc.qt.nokia.com/4.4/examples.html](http://doc.qt.nokia.com/4.4/examples.html)
Categories:
 
[LIST]
[*][ActiveQt]("http://doc.qt.nokia.com/4.4/examples.html#activeqt")
[*][Concurrent  Programming]("http://doc.qt.nokia.com/4.4/examples.html#concurrent-programming")
[*][D-Bus]("http://doc.qt.nokia.com/4.4/examples.html#d-bus")
[*][Desktop]("http://doc.qt.nokia.com/4.4/examples.html#desktop")
[*][Dialogs]("http://doc.qt.nokia.com/4.4/examples.html#dialogs")
[*][Drag  and Drop]("http://doc.qt.nokia.com/4.4/examples.html#drag-and-drop")
[*][Graphics  View]("http://doc.qt.nokia.com/4.4/examples.html#graphics-view")
[*][Help  System]("http://doc.qt.nokia.com/4.4/examples.html#help-system")
[*][Item  Views]("http://doc.qt.nokia.com/4.4/examples.html#item-views")
[*][Layouts]("http://doc.qt.nokia.com/4.4/examples.html#layouts")
[*][Main  Windows]("http://doc.qt.nokia.com/4.4/examples.html#main-windows")
[*][Network]("http://doc.qt.nokia.com/4.4/examples.html#network")
[*][OpenGL]("http://doc.qt.nokia.com/4.4/examples.html#opengl")
[*][Painting]("http://doc.qt.nokia.com/4.4/examples.html#painting")
[*][Phonon  Multimedia Framework]("http://doc.qt.nokia.com/4.4/examples.html#phonon-multimedia-framework")
[*][Qt  Designer]("http://doc.qt.nokia.com/4.4/examples.html#qt-designer")
[*][Qt  Linguist]("http://doc.qt.nokia.com/4.4/examples.html#qt-linguist")
[*][Qt  for Embedded Linux]("http://doc.qt.nokia.com/4.4/examples.html#qt-for-embedded-linux")
[*][Qt  Script]("http://doc.qt.nokia.com/4.4/examples.html#qt-script")
[*][Rich  Text]("http://doc.qt.nokia.com/4.4/examples.html#rich-text")
[*][SQL]("http://doc.qt.nokia.com/4.4/examples.html#sql")
[*][Threads]("http://doc.qt.nokia.com/4.4/examples.html#threads")
[*][Tools]("http://doc.qt.nokia.com/4.4/examples.html#tools")
[*][UiTools]("http://doc.qt.nokia.com/4.4/examples.html#uitools")
[*][WebKit]("http://doc.qt.nokia.com/4.4/examples.html#webkit")
[*][Widgets]("http://doc.qt.nokia.com/4.4/examples.html#widgets")
[*][XML]("http://doc.qt.nokia.com/4.4/examples.html#xml")
[*][XML  Patterns: XQuery & XPath]("http://doc.qt.nokia.com/4.4/examples.html#xml-patterns-xquery-xpath")
[*][Inter-Process  Communication]("http://doc.qt.nokia.com/4.4/examples.html#inter-process-communication")
[/LIST]
  **ActiveQt**

 
[LIST]
[*][COM App]("http://doc.qt.nokia.com/4.4/activeqt-comapp.html")*
[*][Dot Net]("http://doc.qt.nokia.com/4.4/activeqt-dotnet.html")*
[*][Hierarchy]("http://doc.qt.nokia.com/4.4/activeqt-hierarchy.html")*
[*][Menus]("http://doc.qt.nokia.com/4.4/activeqt-menus.html")*
[*][Multiple]("http://doc.qt.nokia.com/4.4/activeqt-multiple.html")*
[*][OpenGL]("http://doc.qt.nokia.com/4.4/activeqt-opengl.html")*
[*][Qutlook]("http://doc.qt.nokia.com/4.4/activeqt-qutlook.html")*
[*][Simple]("http://doc.qt.nokia.com/4.4/activeqt-simple.html")*
[*][Web  Browser]("http://doc.qt.nokia.com/4.4/activeqt-webbrowser.html")*
[*][Wrapper]("http://doc.qt.nokia.com/4.4/activeqt-wrapper.html")*
[/LIST]
  **Concurrent Programming**

 
[LIST]
[*][QtConcurrent  Asynchronous Image Scaling]("http://doc.qt.nokia.com/4.4/qtconcurrent-imagescaling.html")
[*][QtConcurrent  Map]("http://doc.qt.nokia.com/4.4/qtconcurrent-map.html")
[*][QtConcurrent  Progress Dialog]("http://doc.qt.nokia.com/4.4/qtconcurrent-progressdialog.html")
[*][QtConcurrent  Run Function]("http://doc.qt.nokia.com/4.4/qtconcurrent-runfunction.html")
[*][QtConcurrent  Word Count]("http://doc.qt.nokia.com/4.4/qtconcurrent-wordcount.html")
[/LIST]
  **D-Bus**

 
[LIST]
[*][Chat]("http://doc.qt.nokia.com/4.4/dbus-dbus-chat.html")
[*][Complex  Ping Pong]("http://doc.qt.nokia.com/4.4/dbus-complexpingpong.html")
[*][List Names]("http://doc.qt.nokia.com/4.4/dbus-listnames.html")
[*]Ping Pong
[*][Remote  Controlled Car]("http://doc.qt.nokia.com/4.4/dbus-remotecontrolledcar.html")
[/LIST]
  **Desktop**

 
[LIST]
[*][Screenshot]("http://doc.qt.nokia.com/4.4/desktop-screenshot.html")*
[*][System  Tray]("http://doc.qt.nokia.com/4.4/desktop-systray.html")*
[/LIST]
  **Dialogs**

 
[LIST]
[*][Class  Wizard]("http://doc.qt.nokia.com/4.4/dialogs-classwizard.html")*
[*][Config  Dialog]("http://doc.qt.nokia.com/4.4/dialogs-configdialog.html")
[*][Extension]("http://doc.qt.nokia.com/4.4/dialogs-extension.html")*
[*][Find  Files]("http://doc.qt.nokia.com/4.4/dialogs-findfiles.html")*
[*][License  Wizard]("http://doc.qt.nokia.com/4.4/dialogs-licensewizard.html")*
[*][Standard  Dialogs]("http://doc.qt.nokia.com/4.4/dialogs-standarddialogs.html")
[*][Tab  Dialog]("http://doc.qt.nokia.com/4.4/dialogs-tabdialog.html")*
[*][Trivial  Wizard]("http://doc.qt.nokia.com/4.4/dialogs-trivialwizard.html")
[/LIST]
  **Drag and Drop**

 
[LIST]
[*][Draggable  Icons]("http://doc.qt.nokia.com/4.4/draganddrop-draggableicons.html")
[*][Draggable  Text]("http://doc.qt.nokia.com/4.4/draganddrop-draggabletext.html")
[*][Drop  Site]("http://doc.qt.nokia.com/4.4/draganddrop-dropsite.html")
[*][Fridge  Magnets]("http://doc.qt.nokia.com/4.4/draganddrop-fridgemagnets.html")*
[*][Drag  and Drop Puzzle]("http://doc.qt.nokia.com/4.4/draganddrop-puzzle.html")
[/LIST]
  **Graphics View**

 
[LIST]
[*][Colliding  Mice]("http://doc.qt.nokia.com/4.4/graphicsview-collidingmice.html")*
[*][Diagram  Scene]("http://doc.qt.nokia.com/4.4/graphicsview-diagramscene.html")*
[*][Drag  and Drop Robot]("http://doc.qt.nokia.com/4.4/graphicsview-dragdroprobot.html")
[*][Elastic  Nodes]("http://doc.qt.nokia.com/4.4/graphicsview-elasticnodes.html")
[*][Ported  Asteroids]("http://doc.qt.nokia.com/4.4/graphicsview-portedasteroids.html")
[*][Ported  Canvas]("http://doc.qt.nokia.com/4.4/graphicsview-portedcanvas.html")
[/LIST]
  **Help System**

 
[LIST]
[*][Simple  Text Viewer]("http://doc.qt.nokia.com/4.4/help-simpletextviewer.html")*
[/LIST]
  **Item Views**

 
[LIST]
[*][Address  Book]("http://doc.qt.nokia.com/4.4/itemviews-addressbook.html")
[*][Basic  Sort/Filter Model]("http://doc.qt.nokia.com/4.4/itemviews-basicsortfiltermodel.html")
[*][Chart]("http://doc.qt.nokia.com/4.4/itemviews-chart.html")
[*][Color  Editor Factory]("http://doc.qt.nokia.com/4.4/itemviews-coloreditorfactory.html")*
[*][Custom  Sort/Filter Model]("http://doc.qt.nokia.com/4.4/itemviews-customsortfiltermodel.html")*
[*][Dir  View]("http://doc.qt.nokia.com/4.4/itemviews-dirview.html")
[*][Editable  Tree Model]("http://doc.qt.nokia.com/4.4/itemviews-editabletreemodel.html")*
[*][Pixelator]("http://doc.qt.nokia.com/4.4/itemviews-pixelator.html")*
[*][Puzzle]("http://doc.qt.nokia.com/4.4/itemviews-puzzle.html")
[*][Simple  DOM Model]("http://doc.qt.nokia.com/4.4/itemviews-simpledommodel.html")*
[*][Simple  Tree Model]("http://doc.qt.nokia.com/4.4/itemviews-simpletreemodel.html")*
[*][Simple  Widget Mapper]("http://doc.qt.nokia.com/4.4/itemviews-simplewidgetmapper.html")
[*][Spin  Box Delegate]("http://doc.qt.nokia.com/4.4/itemviews-spinboxdelegate.html")*
[*][Star  Delegate]("http://doc.qt.nokia.com/4.4/itemviews-stardelegate.html")*
[/LIST]
  **Layouts**

 
[LIST]
[*][Basic  Layouts]("http://doc.qt.nokia.com/4.4/layouts-basiclayouts.html")*
[*][Border  Layout]("http://doc.qt.nokia.com/4.4/layouts-borderlayout.html")
[*][Dynamic  Layouts]("http://doc.qt.nokia.com/4.4/layouts-dynamiclayouts.html")
[*][Flow  Layout]("http://doc.qt.nokia.com/4.4/layouts-flowlayout.html")
[/LIST]
  **Main Windows**

 
[LIST]
[*][Application]("http://doc.qt.nokia.com/4.4/mainwindows-application.html")*
[*][Dock  Widgets]("http://doc.qt.nokia.com/4.4/mainwindows-dockwidgets.html")*
[*][MDI]("http://doc.qt.nokia.com/4.4/mainwindows-mdi.html")
[*][Menus]("http://doc.qt.nokia.com/4.4/mainwindows-menus.html")*
[*][Recent  Files]("http://doc.qt.nokia.com/4.4/mainwindows-recentfiles.html")
[*][SDI]("http://doc.qt.nokia.com/4.4/mainwindows-sdi.html")
[/LIST]
  **Network**

 
[LIST]
[*][Blocking  Fortune Client]("http://doc.qt.nokia.com/4.4/network-blockingfortuneclient.html")*
[*][Broadcast  Receiver]("http://doc.qt.nokia.com/4.4/network-broadcastreceiver.html")
[*][Broadcast  Sender]("http://doc.qt.nokia.com/4.4/network-broadcastsender.html")
[*][Network  Chat]("http://doc.qt.nokia.com/4.4/network-network-chat.html")
[*][Fortune  Client]("http://doc.qt.nokia.com/4.4/network-fortuneclient.html")*
[*][Fortune  Server]("http://doc.qt.nokia.com/4.4/network-fortuneserver.html")*
[*][FTP]("http://doc.qt.nokia.com/4.4/network-ftp.html")*
[*][HTTP]("http://doc.qt.nokia.com/4.4/network-http.html")
[*][Loopback]("http://doc.qt.nokia.com/4.4/network-loopback.html")
[*][Threaded  Fortune Server]("http://doc.qt.nokia.com/4.4/network-threadedfortuneserver.html")*
[*][Torrent]("http://doc.qt.nokia.com/4.4/network-torrent.html")
[/LIST]
  **OpenGL**

 
[LIST]
[*][2D  Painting]("http://doc.qt.nokia.com/4.4/opengl-2dpainting.html")*
[*][Framebuffer  Object]("http://doc.qt.nokia.com/4.4/opengl-framebufferobject.html")
[*][Framebuffer  Object 2]("http://doc.qt.nokia.com/4.4/opengl-framebufferobject2.html")
[*][Grabber]("http://doc.qt.nokia.com/4.4/opengl-grabber.html")
[*][Hello GL]("http://doc.qt.nokia.com/4.4/opengl-hellogl.html")*
[*][Overpainting]("http://doc.qt.nokia.com/4.4/opengl-overpainting.html")*
[*][Pixel  Buffers]("http://doc.qt.nokia.com/4.4/opengl-pbuffers.html")
[*][Pixel  Buffers 2]("http://doc.qt.nokia.com/4.4/opengl-pbuffers2.html")
[*][Sample  Buffers]("http://doc.qt.nokia.com/4.4/opengl-samplebuffers.html")
[*][Textures]("http://doc.qt.nokia.com/4.4/opengl-textures.html")
[/LIST]
  **Painting**

 
[LIST]
[*][Basic  Drawing]("http://doc.qt.nokia.com/4.4/painting-basicdrawing.html")*
[*][Concentric  Circles]("http://doc.qt.nokia.com/4.4/painting-concentriccircles.html")*
[*][Font  Sampler]("http://doc.qt.nokia.com/4.4/painting-fontsampler.html")
[*][Image  Composition]("http://doc.qt.nokia.com/4.4/painting-imagecomposition.html")*
[*][Painter  Paths]("http://doc.qt.nokia.com/4.4/painting-painterpaths.html")*
[*][SVG  Viewer]("http://doc.qt.nokia.com/4.4/painting-svgviewer.html")
[*][Transformations]("http://doc.qt.nokia.com/4.4/painting-transformations.html")*
[/LIST]
  **Phonon Multimedia Framework**

 
[LIST]
[*][Capabilities]("http://doc.qt.nokia.com/4.4/phonon-capabilities.html")*
[*][Music  Player]("http://doc.qt.nokia.com/4.4/phonon-musicplayer.html")*
[/LIST]
  **Qt Designer**

 
[LIST]
[*][Calculator  Builder]("http://doc.qt.nokia.com/4.4/designer-calculatorbuilder.html")*
[*][Calculator  Form]("http://doc.qt.nokia.com/4.4/designer-calculatorform.html")*
[*][Custom  Widget Plugin]("http://doc.qt.nokia.com/4.4/designer-customwidgetplugin.html")*
[*][Task  Menu Extension]("http://doc.qt.nokia.com/4.4/designer-taskmenuextension.html")*
[*][Container  Extension]("http://doc.qt.nokia.com/4.4/designer-containerextension.html")*
[*][World  Time Clock Builder]("http://doc.qt.nokia.com/4.4/designer-worldtimeclockbuilder.html")*
[*][World  Time Clock Plugin]("http://doc.qt.nokia.com/4.4/designer-worldtimeclockplugin.html")*
[/LIST]
  **Qt Linguist**

 
[LIST]
[*][Hello  tr()]("http://doc.qt.nokia.com/4.4/linguist-hellotr.html")*
[*][Arrow  Pad]("http://doc.qt.nokia.com/4.4/linguist-arrowpad.html")*
[*][Troll  Print]("http://doc.qt.nokia.com/4.4/linguist-trollprint.html")*
[/LIST]
  **Qt for Embedded Linux**

 
[LIST]
[*][Mouse  Calibration]("http://doc.qt.nokia.com/4.4/qws-mousecalibration.html")*
[*][Accelerated  Graphics Driver]("http://doc.qt.nokia.com/4.4/qws-svgalib.html")*
[*][OpenGL for  Embedded Systems]("http://doc.qt.nokia.com/4.4/qws-ahigl.html")*
[*][Double  Buffered Graphics Driver]("http://doc.qt.nokia.com/4.4/qws-dbscreen.html")*
[/LIST]
  **Qt Script**

 
[LIST]
[*][Calculator]("http://doc.qt.nokia.com/4.4/script-calculator.html")
[*][Context2D]("http://doc.qt.nokia.com/4.4/script-context2d.html")
[*][Default  Prototypes]("http://doc.qt.nokia.com/4.4/script-defaultprototypes.html")
[*][Hello  Script]("http://doc.qt.nokia.com/4.4/script-helloscript.html")
[*][Tetrix]("http://doc.qt.nokia.com/4.4/script-tetrix.html")
[*][Custom  Script Class]("http://doc.qt.nokia.com/4.4/script-customclass.html")
[/LIST]
  **Rich Text**

 
[LIST]
[*][Calendar]("http://doc.qt.nokia.com/4.4/richtext-calendar.html")*
[*][Order  Form]("http://doc.qt.nokia.com/4.4/richtext-orderform.html")*
[*][Syntax  Highlighter]("http://doc.qt.nokia.com/4.4/richtext-syntaxhighlighter.html")*
[/LIST]
  **SQL**

 
[LIST]
[*][Cached  Table]("http://doc.qt.nokia.com/4.4/sql-cachedtable.html")*
[*][Drill Down]("http://doc.qt.nokia.com/4.4/sql-drilldown.html")*
[*][Query  Model]("http://doc.qt.nokia.com/4.4/sql-querymodel.html")
[*][Relational  Table Model]("http://doc.qt.nokia.com/4.4/sql-relationaltablemodel.html")
[*][Table  Model]("http://doc.qt.nokia.com/4.4/sql-tablemodel.html")
[/LIST]
  **Threads**

 
[LIST]
[*][Mandelbrot]("http://doc.qt.nokia.com/4.4/threads-mandelbrot.html")*
[*][Semaphores]("http://doc.qt.nokia.com/4.4/threads-semaphores.html")*
[*][Wait  Conditions]("http://doc.qt.nokia.com/4.4/threads-waitconditions.html")*
[/LIST]
  **Tools**

 
[LIST]
[*][Codecs]("http://doc.qt.nokia.com/4.4/tools-codecs.html")
[*][Completer]("http://doc.qt.nokia.com/4.4/tools-completer.html")*
[*][Custom  Completer]("http://doc.qt.nokia.com/4.4/tools-customcompleter.html")*
[*][Echo  Plugin]("http://doc.qt.nokia.com/4.4/tools-echoplugin.html")*
[*][I18N]("http://doc.qt.nokia.com/4.4/tools-i18n.html")
[*][Plug  & Paint]("http://doc.qt.nokia.com/4.4/tools-plugandpaint.html")*
[*]Plug & Paint Plugins: [Basic  Tools]("http://doc.qt.nokia.com/4.4/tools-plugandpaintplugins-basictools.html")* and [Extra  Filters]("http://doc.qt.nokia.com/4.4/tools-plugandpaintplugins-extrafilters.html")*
[*][RegExp]("http://doc.qt.nokia.com/4.4/tools-regexp.html")
[*][Settings  Editor]("http://doc.qt.nokia.com/4.4/tools-settingseditor.html")
[*][Style  Plugin]("http://doc.qt.nokia.com/4.4/tools-styleplugin.html")*
[*][Tree  Model Completer]("http://doc.qt.nokia.com/4.4/tools-treemodelcompleter.html")*
[*][Undo  Framework]("http://doc.qt.nokia.com/4.4/tools-undoframework.html")*
[/LIST]
  **UiTools**

 
[LIST]
[*][Multiple  Inheritance]("http://doc.qt.nokia.com/4.4/uitools-multipleinheritance.html")*
[*][Text  Finder]("http://doc.qt.nokia.com/4.4/uitools-textfinder.html")*
[/LIST]
  **WebKit**

 
[LIST]
[*][Previewer]("http://doc.qt.nokia.com/4.4/webkit-previewer.html")*
[*][Form  Extractor]("http://doc.qt.nokia.com/4.4/webkit-formextractor.html")
[/LIST]
  **Widgets**

 
[LIST]
[*][Analog  Clock]("http://doc.qt.nokia.com/4.4/widgets-analogclock.html")*
[*][Calculator]("http://doc.qt.nokia.com/4.4/widgets-calculator.html")*
[*][Calendar  Widget]("http://doc.qt.nokia.com/4.4/widgets-calendarwidget.html")*
[*][Character  Map]("http://doc.qt.nokia.com/4.4/widgets-charactermap.html")*
[*][Digital  Clock]("http://doc.qt.nokia.com/4.4/widgets-digitalclock.html")*
[*][Group  Box]("http://doc.qt.nokia.com/4.4/widgets-groupbox.html")*
[*][Icons]("http://doc.qt.nokia.com/4.4/widgets-icons.html")*
[*][Image  Viewer]("http://doc.qt.nokia.com/4.4/widgets-imageviewer.html")*
[*][Line  Edits]("http://doc.qt.nokia.com/4.4/widgets-lineedits.html")*
[*][Movie]("http://doc.qt.nokia.com/4.4/widgets-movie.html")
[*][Scribble]("http://doc.qt.nokia.com/4.4/widgets-scribble.html")*
[*][Shaped  Clock]("http://doc.qt.nokia.com/4.4/widgets-shapedclock.html")*
[*][Sliders]("http://doc.qt.nokia.com/4.4/widgets-sliders.html")*
[*][Spin  Boxes]("http://doc.qt.nokia.com/4.4/widgets-spinboxes.html")*
[*][Styles]("http://doc.qt.nokia.com/4.4/widgets-styles.html")*
[*][Style  Sheet]("http://doc.qt.nokia.com/4.4/widgets-stylesheet.html")*
[*][Tablet]("http://doc.qt.nokia.com/4.4/widgets-tablet.html")*
[*][Tetrix]("http://doc.qt.nokia.com/4.4/widgets-tetrix.html")*
[*][Tooltips]("http://doc.qt.nokia.com/4.4/widgets-tooltips.html")*
[*][Wiggly]("http://doc.qt.nokia.com/4.4/widgets-wiggly.html")*
[*][Window  Flags]("http://doc.qt.nokia.com/4.4/widgets-windowflags.html")*
[/LIST]
  **XML**

 
[LIST]
[*][DOM  Bookmarks]("http://doc.qt.nokia.com/4.4/xml-dombookmarks.html")
[*][SAX  Bookmarks]("http://doc.qt.nokia.com/4.4/xml-saxbookmarks.html")
[*][QXmlStream  Bookmarks]("http://doc.qt.nokia.com/4.4/xml-streambookmarks.html")*
[*][RSS-Listing]("http://doc.qt.nokia.com/4.4/xml-rsslisting.html")
[*][XML  Stream Lint Example]("http://doc.qt.nokia.com/4.4/xml-xmlstreamlint.html")*
[/LIST]
  **XML Patterns: XQuery & XPath**

 
[LIST]
[*][C++  Source Code Analyzer Example]("http://doc.qt.nokia.com/4.4/xmlpatterns-xquery-globalvariables.html")
[*][File  System Example]("http://doc.qt.nokia.com/4.4/xmlpatterns-filetree.html")
[*][QObject  XML Model Example]("http://doc.qt.nokia.com/4.4/xmlpatterns-qobjectxmlmodel.html")
[*][Recipes]("http://doc.qt.nokia.com/4.4/xmlpatterns-recipes.html")
[/LIST]
  **Inter-Process Communication**

 
[LIST]
[*][Local  Fortune Client]("http://doc.qt.nokia.com/4.4/ipc-localfortuneclient.html")*
[*][Local  Fortune Server]("http://doc.qt.nokia.com/4.4/ipc-localfortuneserver.html")*
[*][Shared  Memory]("http://doc.qt.nokia.com/4.4/ipc-sharedmemory.html")*
[/LIST]


---

### Post by trent.josephsen on 2010-06-15
> **conundrumx said:**
> OSX is actually the only "certified" UNIX.

There are multiple other Unixes, including AIX, HP-UX, and Solaris, among others.  I think OS X is the only BSD descendant to be registered as a Unix, and it's certainly the only such system typically found on desktop machines; I'm not sure exactly what you meant by "only", or if you merely misspoke.

If memory serves, registration requires accurate accounting of distributed licenses and a per-license fee to the Open Group, which would explain why no Linux or freely distributed BSD distribution has been registered.

---

### Post by ja660k on 2010-06-16
> **escapee said:**
> Just clarifying, Mac has been settled with Objective-C as the main language for a loooong time now, though support for several other languages exist, most with bridges to C and Objective-C.

and its main gui library is cocoa, whihc is written in pure objective-C 
as opposed to the old carbon, which was written in c.

> **trent.josephsen said:**
> I think OS X is the only BSD descendant to be registered as a Unix, and it's certainly the only such system typically found on desktop machines; 
[http://www.apple.com/xserve/](http://www.apple.com/xserve/)
[http://www.apple.com/server/macosx/](http://www.apple.com/server/macosx/)


> **nrs said:**
> 
Windows development can only be done semi-painlessly through an IDE like Visual Studio, IMO. I don't really care for Visual Studio. 

+1
IDE's though they do take some time out of development process, but i like to know what is going on. and especially in Visual Studio its "Do it my way, or i will make it extremely hard otherwise"

---

### Post by trent.josephsen on 2010-06-16
> **ja660k said:**
> [http://www.apple.com/xserve/](http://www.apple.com/xserve/)
[http://www.apple.com/server/macosx/](http://www.apple.com/server/macosx/)

"typically found on desktop machines", I said.  Which is true -- all the others are used for servers almost exclusively, with the possible exception of Solaris.  I'm well aware of the Server abilities of OS X.

---

### Post by KdotJ on 2010-06-16
> **ja660k said:**
> for the most part, linux is better because really, you dont need a fancy text editor right? 

and who said you can't get a fancy editor for Linux? gedit itself, with plugins is in my opinion it's more than enough for coding

---

### Post by DanielWaterworth on 2010-06-16
Wooh gedit, you gotta love gedit, who needs visual studio.

(If that came across sarcastic, it wasn't, I was being serious)

---

### Post by ja660k on 2010-06-16
> **KdotJ said:**
> and who said you can't get a fancy editor for Linux? gedit itself, with plugins is in my opinion it's more than enough for coding

But thats hardly fancy is it?
but its all you need.

---

### Post by conundrumx on 2010-06-16
> **nrs said:**
> You have no reading comprehension. 



Mhmm. It's complety the same. Which is why you need the OS X specific -framework option if you want to avoid the problems I mentioned. Try including / linking OpenGL/AL/SDL. -Is-Ls$PATH-framework

Oh, well if you say so!  Clearly you know everything.

Wait, you mean you have to specify when you want to use specific frameworks?  OH MY GODS.  THAT'S MADNESS.  OSX IS TERRIBLE.  HOW DARE THEY NOT READ YOUR MIND?

You're trying to imply that OSX is somehow not as Unix like as Linux, which is insanity.  It is in fact *more* Unix like.  POSIX is POSIX, and both LSB distros and OSX are compliant.  I can run tons of F/OSS software using the same configurations as BSD would.

Jumping from a shell on an OSX box to a Linux box is essentially indistinguishable, until you try to invoke some GNU specific stuff or BSD specific stuff on the wrong machine.  Obviously development is different, but it's not really sane to say OSX isn't Unix like because it's not like Linux.

---

### Post by nrs on 2010-06-16
> **conundrumx said:**
> Oh, well if you say so!  Clearly you know everything.

Wait, you mean you have to specify when you want to use specific frameworks?  OH MY GODS.  THAT'S MADNESS.  OSX IS TERRIBLE.  HOW DARE THEY NOT READ YOUR MIND?

You're trying to imply that OSX is somehow not as Unix like as Linux, which is insanity.  It is in fact *more* Unix like.  POSIX is POSIX, and both LSB distros and OSX are compliant.  I can run tons of F/OSS software using the same configurations as BSD would.

Jumping from a shell on an OSX box to a Linux box is essentially indistinguishable, until you try to invoke some GNU specific stuff or BSD specific stuff on the wrong machine.  Obviously development is different, but it's not really sane to say OSX isn't Unix like because it's not like Linux.
Mhmm. So now it's more UNIX-like. Right. 
cd / && ls -la 
Is that like most other UNIXes? Hmm? 
Look, I'm not saying it isn't *nix or anything crazy like that, I'm just saying it stands out compared to the rest. It goes against written / unwritten conventions in a lot of areas. Consider Tiger + NFS. 
[http://www.behanna.org/osx/nfs/howto1.html](http://www.behanna.org/osx/nfs/howto1.html)

They've thankfully normalized this in recent versions, but it is another example of Apple doing this.

---

### Post by DCGStudios on 2010-06-16
Honestly, most of the people on here suggesting that one OS is better then another for programming either has a grudge against the opposing OS or is just plain wrong.. 

The limitations and ease of use comes from the complier, the language, and the teacher/user, NOT the OS.

---

### Post by trent.josephsen on 2010-06-16
> **DCGStudios said:**
> Honestly, most of the people on here suggesting that one OS is better then another for programming either has a grudge against the opposing OS or is just plain wrong.. 

The limitations and ease of use comes from the complier, the language, and the teacher/user, NOT the OS.
++

---

### Post by nrs on 2010-06-16
> **DCGStudios said:**
> Honestly, most of the people on here suggesting that one OS is better then another for programming either has a grudge against the opposing OS or is just plain wrong.. 

The limitations and ease of use comes from the complier, the language, and the teacher/user, NOT the OS.
So editors, build utilities, environment in general, .. do not affect the equation at all?

---

### Post by DanielWaterworth on 2010-06-17
> **DCGStudios said:**
> The limitations and ease of use comes from the complier, the language, and the teacher/user, NOT the OS.

And the APIs... set by the OS.

---

### Post by NUboon2Age on 2010-06-17
> **soltanis said:**
>  I should also point out that while Mac OS X does conform to POSIX and a few other UNIX specs, it has its own little world in which there is a way of doing things completely separate from the UNIX way of doing things, so just be aware of that.

We could say that about each of these development "islands". 

For example much of mac island is made up of essentially Mac [Application Programming Interfaces (APIs) and Frameworks]("http://www.oreillynet.com/pub/a/mac/2001/05/23/cocoa_vs_carbon.html") and their fav tool, [Objective C]("http://en.wikipedia.org/wiki/Objective-C").  To a significant degree it is difficult if not impossible to expect to learn this stuff AND have time to learn another set of similar OS-specific API, and [IDEs]("http://en.wikipedia.org/wiki/Integrated_development_environment").  It just takes too much time and energy.  And I think the proprietary computer companies probably realize that and try to use it to their advantage -- if for example you as a developer are spending your time learning how to program for the Mac or iPad, you're not over working on one of the competitors.

Its the same story on Windoze however where you having to learn [Windoze API]("http://en.wikipedia.org/wiki/Windows_API")s[foundation classes]("http://msdn.microsoft.com/en-us/library/aa260845%28VS.60%29.aspx") their (I'm not sure why they call it) [Visual Studio IDE]("http://en.wikipedia.org/wiki/Microsoft_Visual_Studio"), and its language-specific [Visual C++]("http://en.wikipedia.org/wiki/Visual_C%2B%2B") (except [Visual Basic]("http://en.wikipedia.org/wiki/Visual_basic") -- that really is visual -- about the only thing M$ ever really did right imo) and [frameworks]("http://en.wikipedia.org/wiki/List_of_Microsoft_Windows_application_programming_interfaces_and_frameworks").  It used to be at least there were a few competitors for alternative IDEs and APIs, like Borland/Inprise or Semantec but for the most part they've gone by the wayside and Monopol$oft has a monopoly on development for Windoze OS.  So with the proprietary platforms you'll tend to have few major commercial choices (although FLOSS software is providing about the only significant competition).  

Then there's [Linux island]("http://en.wikipedia.org/wiki/Linux#Programming_on_Linux").  Here we have KDE, Gnome, and XFCE and many frameworks available (for example [for Python alone]("http://wiki.python.org/moin/GuiProgramming")).  Overall I think free Linux island looks like a pretty nice place to develop.  Possibly its one weakness is in lack of sophisticated, slick development IDEs and tools.  However I have to say [KDevelop4]("http://www.kdevelop.org/index.html?filename=4.0/screenshots.html") and [Eclipse Galileo]("http://www.eclipse.org/galileo/") are looking mighty fine.

And we do have a number of [cross-platform frameworks]("http://en.wikipedia.org/wiki/Simple_DirectMedia_Layer") or [web frameworks]("http://en.wikipedia.org/wiki/Web_application_framework").  

Then there are APIs for Virtual machines that are designed to be crossplatform like [Java]("http://en.wikipedia.org/wiki/List_of_Java_APIs"), [.NET]("http://en.wikipedia.org/wiki/.NET_Framework") and to an extent Perl and Python.  

So my point is no one has time to learn more than 1 or just a few of these so you end up having to pick (or sometimes your employers picks for you). So you can see you get to that depth of application programming suffice it to say you'll probably end up having to learn about one or more [software frameworks]("http://en.wikipedia.org/wiki/Software_framework"), related to the platform you're programming on and not simply a platform and a language.

---

### Post by NUboon2Age on 2010-06-17
> **Queue29 said:**
> Just stop with the over generalized B.S. It makes you look like a tool.

Actually what they said was dead on. No need to be so harsh.

---

### Post by nvteighen on 2010-06-17
Programming is a human ability that is not bound to any OS.

Ok, I know some OSs make it easier to program than others, but just because there are more and better tools for them, sometimes even available in the OS's default installation. Windows is not worse, it's just that it's targeted to end-users and therefore, you've got to find your own way finding the right tools, while in Ubuntu or Debian, you have a handy repository for that...

About the Win32 API, well, that may be a technical reason. But nothing stops you from using GTK+ or Qt other libraries in Windows.

---

### Post by conundrumx on 2010-06-17
> **nrs said:**
> Mhmm. So now it's more UNIX-like. Right. 
cd / && ls -la 
Is that like most other UNIXes? Hmm? 

I really want to understand your gripe here.  Is it the additional folders on top of the generic bin, usr, local, etc?  I just don't understand why that would be a problem for any sane person or program.  If ~ didn't work, or some other critical variables were missing then sure, it would be a problem; I really hope your whole argument against OSX being the black sheep of *nix like systems is "THE ROOT DIRECTORY HAS UNFAMILIAR STUFF IN IT!!!!!"

---

### Post by DCGStudios on 2010-06-17
> **DanielWaterworth said:**
> And the APIs... set by the OS.

True, Although not completely. 

Linux, Windows, and Apple all provide a public API so that programs can be developed for there platforms, in which you do generally have to recompile for compatibility reasons..

But yes, unfortunately the libraries are not cross-compatible and likely will not be standardized anytime in the near future, But I wouldn't go as far to say it gives "limitations" on the programmer..

EDIT:
> **nrs said:**
> So editors, build utilities, environment in general, .. do not affect the equation at all?

I believe your referring to the compiler and API's here.

---

### Post by DanielWaterworth on 2010-06-17
No, the only way it could be a limitation is if there are things that you can't do because the API is limited or badly documented. However, if the API is just annoying then it will slow you down or to put it another way, limit your development speed. If I have to do windows programming I suffer much more from the latter than the former, but I still haven't worked out how to do a select type call on a namedpipe and a socket and I hate polling but I digress.

---

### Post by themarker0 on 2010-06-17
They all have (a) notepad.
 
So its even.

---

### Post by DanielWaterworth on 2010-06-17
> **themarker0 said:**
> They all have (a) notepad.
 
So its even.

Some people like to do more with a computer than notepad can offer =P (and gedit isn't just a notepad).

I think this thread has gone on far too long. It was set as solved ages ago. To summarise, some people like to use Mac and that's fine, some people prefer Linux, also good, and some people are brain-damaged. Joke. The fact of the matter is, and I hate to admit it, but if you want to write a program that lots of people will use, you can't get away from supporting windows. You don't often get a choice of which platform you'll be writing for.

---

### Post by nrs on 2010-06-17
> **DCGStudios said:**
> 
I believe your referring to the compiler and API's here.
By build utilities I mean: make, autotools, etc. 
editors: emacs, vim, sed, awk, etc.
general environment: shell, standard utilities, and whatever else I'm missing.

---

### Post by sdennie on 2010-06-17
> **nrs said:**
>  
editors: emacs, vim, sed, awk, etc.


I think you accidentally mistyped that.  You meant: "editors: vim".

/me ducks

---

### Post by conundrumx on 2010-06-17
> **sdennie said:**
> I think you accidentally mistyped that.  You meant: "editors: vim".

/me ducks

Because emacs is actually some kind of crazy OS.

Also, he left out nano.

---

### Post by sdennie on 2010-06-17
> **conundrumx said:**
> Because emacs is actually some kind of crazy OS.

And it has a poor editor.

---

### Post by DCGStudios on 2010-06-17
> **nrs said:**
> By build utilities I mean: make, autotools, etc. 
editors: emacs, vim, sed, awk, etc.
general environment: shell, standard utilities, and whatever else I'm missing.

sed, awk, are both languages designed generally for text editing.. emacs and vim have nothing to do with the previously mentioned category.. 

make and autotools are tools used to build & compile programs.. if your dealing with complex programming generally you have a compiler which would be an editor (which can also provide syntax errors for debugging) and a builder/compiler...

shell is a terminal? no idea where you think this fits into the actual programming.. 

This is going far off-topic at this point and really not even making sense..

---

### Post by nrs on 2010-06-18
> **DCGStudios said:**
> and really not even making sense..
I'll agree to that. 

Sed isn't a language, it's an editor. You've got me on Awk, though it's generally used for editing. 

> **DCGStudios said:**
> 
make and autotools are tools used to build & compile programs.. if  your dealing with complex programming generally you have a compiler  which would be an editor (which can also provide syntax errors for  debugging) and a builder/compiler...]

I don't understand that or your point of confusion. I said they were build utilities. They  are utilities to help you build the program, they don't compile / link it. They're there to make life easier. Not that autotools particularly succeeds in that area. 

> **DCGStudios said:**
> 
shell is a terminal? no idea where you think this fits into the actual  programming.. 

It doesn't. Like all the others I mentioned: it provides a nice environment for the programming to take place.

You seem to think that I'm saying all these tools are needed to write your program or are involved in the compilation process. I'm not, I'm saying: all these tools conspire to build an ecosystem particularly conductive to programming.

---

