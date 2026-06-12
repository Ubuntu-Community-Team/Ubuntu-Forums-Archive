---
title: "C/C++ dev -- IDE versus command line"
date: 2007-02-18
forum: Programming Talk
---

### Post by j_g on 2007-02-18
In another thread (that has been closed), someone asked about using an IDE versus just invoking the compiler/linker via a command line. Since I just started Linux C programming a few weeks ago, I'd like to give my own observations/opinions to a fellow programming newbie. I realize that others may disagree with these observations/opinions, but that doesn't make my own invalid. In fact, since the OP has already expressed a frustration over some of the very same things I found frustrating, it's likely that my observations/opinions would be more applicable to him than the opinions of someone who would simply disagree without having any empathy/understanding for the OP's point of view.

I have to say that I love IDEs. A good IDE should have a logical, easily-navigated UI to create applications. The UI should allow the enduser to easily enter all of the data needed to compile/link the app, and the IDE _should_ do whatever needs to be done to successfully invoke the compiler/linker to create the app.

An example of a good IDE that does exactly that is Microsoft's Visual Studio. It uses fully complete wizards to guide the process, and its underlying tools are well integrated with the IDE. When you finish the wizard, Visual Studio directly creates the needed makefile. It's easy and painless to develop Win32 apps using MS tools.

An example of a bad IDE that doesn't do this very well is Anjuta. Anjuta's wizard takes you only half-way gathering all the info it needs, then it runs some not-so-well-integrated GNU tools which, too independently of Anjuta, try to analyze your system and come up with the remaining necessary info to create the makefile. It's painful and difficult to develop Linux apps with Anjuta.

Part of the problem is that Anjuta is buggy. It recently got a _long-overdue_ update, but I get the impression that too little development time is being devoted to a tool that needs much more attention than it gets. Sometimes Anjuta works and sometimes it doesn't. For example, once I got the scintella editor to work on editing source files, but usually that locked up Anjuta as soon as I selected it, and I had to use the GtkTextEditor (or whatever it was called) instead. Of course, I haven't used the latest Anjuta version because I couldn't get the thing to compile on my system, using the previous version of Anjuta, and the "Anjuta project file" with the newer sources. When an IDE can't even make a new version of itself, given its own project file, that's a really bad sign. The Ubuntu repository still doesn't have the newer Anjuta. And I needed the newer Anjuta because I used Glade2 to create my UI, and the older version of Anjuta didn't support it.

So right there, I'd advise you to swear off of Anjuta, because I don't believe the support is as good as it needs to be for hassle-free development.

Another part of the problem is that Anjuta uses a lot of the GNU tools (autoconf, automake, etc), which strive to create "universal" dev files that take into consideration every possible configuration quirk of the thousands of Linux distributions made by Tom, Dick, Harry, and their dogs Spike, Fido, and Spot. But this is a nightmare for a newbie who wants to just compile, link, and run his C/C++ program on his single installation of Ubuntu. He doesn't need to take into consideration some quirk of "Martian Christian Linux", yet another pointlessly trivial variation of Linux which, for god knows what reason, is supposedly better for Martians who also happen to be christians.  The GNU tools spout out dev files that are humanly unreadable and uneditable by all but the extraterrestrial beings who devised the incomprehensible, needlessly convoluted alien "language" that these tools use. This is bad news if you need to hand modify one of these files because Anjuta didn't quite get something right (and believe me, it's a good bet that Anjuta's "output window" will demonstrate blissful ignorance as it chuffs out autoconf error messages telling you to hand edit your configure file to add this or that). Anjuta isn't smart enough to parse the error output of the GNU tools and follow the instructions given to you, even though it's supposed to be the job of a good IDE to maintain and "edit" the underlying compiler/linker support files instead of telling you to do so. Otherwise, what's the point of an IDE?

For this reason, I opted to get rid of Anjuta. I simply installed gcc, and all the dev libraries I personally needed, such as libglade2, gtk2, etc. Then I wrote my code with gedit, created a simple makefile for my needs, and just ran the make utility for a terminal window. It worked for me much better for me than Anjuta did.

One of the real breakthroughs I made with regards to specifying libraries in a makefile is use of the utility pkg-config, with its --cflags and --libs options. These options will look up the Include path, and library path of a particular package. For example, open a terminal window and type:

pkg-config --list-all

This will list all of the packages installed on your system. Let's assume that you've installed gdk2 (Gnome) package, and so "gdk-2.0" appears in the list. Now type

pkg-config --cflags gdk-2.0

This will spit out a line such as:

-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include ... etc.

It is essentially what you supply to gcc when you want to tell it all the paths to the include files for an app that uses gdk2.

Now type

pkg-config --libs gdk-2.0

This spits out a line that is what you supply to gcc when you want to tell it all the libs to link to for an app that uses gdk2.

So to put it all together, here's how you'd specify a makefile to use pkg-config to compile a source file named MySource.c into MySource executable, specifying include files and libraries for the gtk2, and libglade2 packages. Note that you need to surround each pkg-config invocation with ` characters.

CFLAGS=`pkg-config --cflags libglade-2.0` `pkg-config --cflags gtk+-2.0`
LIBS=`pkg-config --libs libglade-2.0` `pkg-config --libs gtk+-2.0`
OBJECTS=MySource.o
# Comment the next line to create a version without debugging
LDFLAGS=-g

MySource: $(OBJECTS)
	gcc $(LDFLAGS) -o $@ $(OBJECTS) $(LIBS)

MySource.o: MySource.c
	gcc -Wall -c $^ $(CFLAGS)


And that's it. Just name the above file "makefile" (in the same directory as MySource,c), and type "make" at the terminal. This is a hell of a lot less painful than dealing with an IDE that isn't quite up to the task of hassle-free development.

---

### Post by cybrid on 2007-02-18
I cannot make a response according to your statements since I haven't tested anjuta that deeply, but I must say that a lot more of attention should be put on it since I belive that gnome needs a good, solid, fast IDE, that way I think that much more programmers would be interested in doing GTK bassed apps. Personally I feel a lot more confortable programming in the windows enviroment using MS VS.NET, and I really would like to develop apps for Gnome but setting it up everything is a pain in the *** and so it's using anjuta :(

---

### Post by lnostdal on 2007-02-18
ok, i'll put up a third writing ( [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) ) by the end of the day and i'll show that it is really-really simple and fast to do GTK+ development .. and no anjuta is needed (or you can bypass all the problems in anjuta by making anjuta use your own simple build-tools/scripts) :)

..will post here again when it is done..

---

### Post by lnostdal on 2007-02-18
Ok, `ubuntu-programming3.pdf' is up at [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) 

..can anyone confirm that Anjuta is able to use Scons directly in the manner described (very briefly) at the end? I'm hoping that would solve some problems as Scons is "good enough"(#1) in most cases while still being simpler and more human-readable than most of the autoconf/makefile hair produced by Anjuta (IMHO YMMV ..etc.).

#1: Heck; Doom 3 was compiled using it!

---

### Post by cybrid on 2007-02-18
Damn, there is a myriad of buld/conf tools around, Inostdal since you seem to know what you're doing, could you put a list of tools? and what they're for?, it would be great not having to search for them, you know, autoconf, autobuild, scons, automake, auto . . . .

---

### Post by j_g on 2007-02-18
I read your PDFs, but to be honest, I didn't care for some of the tools you picked out, starting with your choice of text editor, and ending with your choice of frontend for gdb. Using those tools makes me feel like I'm back in 1986 using my Amiga 1000. They have very dated UI's. Although they may work fine for you now that you've spent a lot of time getting accustomed to them and setting up your own environment, I don't think that the UI's of the tools you're using are apropos for beginners who weaned themselves on modern UI's. And I fail to see the point of using tools with arcane UI's to develop apps for a modern UI with modern UI toolkits such as GTK+ and libglade.

I would recommend that a beginner use a more modern text editor such as gedit. I also found kdbg to be a fairly serviceable frontend to dbg. It's definitely not as nice as Visual Studio's debugger, but it at least has a serviceable UI including such things as Watch windows, and unlike Anjuta's dbg frontend, it isn't buggy as hell. I haven't been able to find a decent dbg frontend for Gnome, but kdbg works.

I looked over SCons, but my reaction is that it is definitely no substitute for an IDE frontend to a compiler/linker. It is therefore simply yet another variation of the same approach taken by GNU's dev tools (ie, the programmer must learn yet another "programming syntax" in order to write a hand-written "make file"). For this reason, I don't consider it any more or less useful to a newbie programmer. There are things about it that may make it easier to hand write/edit the make file than with the GNU tools, but it's still a complex and error-prone task for a newbie. I would neither recommend nor dissuade a new programmer from using it. I would simply say that it is an alternative to the assortment of complex "make tools". SCons may have some advantages in some ways, but nevertheless is complex and difficult for a new programmer to use.

(As an aside, in looking over the SCons docs, I noticed that the SharedLibrary example does not issue the -fPIC compiler option. I'm not sure if this tool is designed for creating dynamically loaded shared libs. Furthermore, the docs completely neglect detailing how SCons would be used in conjunction with a packaging tool like rpmbuild. Therefore, it may not be appropriate for a programmer wishing to package his software for a "repository". So there may be disadvantages to this tool, compared to GNU alternatives).

---

### Post by lnostdal on 2007-02-18
> **j_g said:**
> I read your PDFs, but to be honest, I didn't care for some of the tools you picked out, starting with your choice of text editor,


That choice doesn't really matter. Any editor that can call external tools and parse output could be used there.

Main point is to show usage/setup of a distributed set of tools that are able to communicate instead of an integrated set of tools. But pick your set of tools as you wish here.


> 
And I fail to see the point of using tools with arcane UI's to develop apps for a modern UI with modern UI toolkits such as GTK+ and libglade.


Hm, is there any point in-itself in only using a single UI-toolkit when there are tools out there using a different UI-toolkit that _might_ (imagine this even if you feel this isn't so in reality) be better? For instance, I use both Motif, QT and GTK+ applications under Ubuntu. I do not view that as a "point", as if I "must" use tools that use different UI-toolkits - or even a real problem(#1). 

The only "point" for me is to use good tools that work -- regardless of UI-toolkit. I prefer tools which do specialized tasks well: [http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy) (but again make your own picks here)

What UI-toolkit the tool use doesn't really matter at all as long as it is _good_ at what it actually _does_. This immediately turn what UI-toolkit the tool uses barely noticeable -- at least for me. :)


> 
I would recommend that a beginner use a more modern text editor such as gedit.


Well, can gedit parse the output of GCC and jump to the line/file the messages from GCC refers to? Can it split windows so you can view multiple files at the same time? Can it fold code? Does it have an auto-complete feature? Class/symbol/function-browsing? ..etc..

I don't really know the answer to those questions; that's probably why I picked the tools I did. :) But about the "modern"-part; gedit only has a fraction of the features Emacs has - that I am sure of. So modern can mean different things depending on how you look at it. 

But again the main point with the articles is to try to show usage of a distributed set of tools that are able to communicate (GCC --compile-messages--> Emacs). Pick another editor if you like. :)


> 
 I also found kdbg to be a fairly serviceable frontend to dbg. It's definitely not as nice as Visual Studio's debugger, but it at least has a serviceable UI including such things as Watch windows, and unlike Anjuta's dbg frontend, it isn't buggy as hell. I haven't been able to find a decent dbg frontend for Gnome, but kdbg works.

I don't see what's wrong with DDD. You mention watch-windows; DDD has those of course!

Actually, at first sight - DDD seem to have a lot of features kdbg lack. But I might be wrong about that - and it doesn't really matter. You're free to pick any front end and that is a good thing IMHO. :)


> 
I looked over SCons, but my reaction is that it is definitely no substitute for an IDE frontend to a compiler/linker.

Ok, I fully disagree here. I think this question is like the Vim vs. Emacs question.

So we disagreeing here doesn't matter(#2) in regards to the article as there are many people on "both sides". The article is for people who already want to take the distributed-tools approach and not the IDE-approach. :)

But just to make sure; you do not think using Scons means that you actually have to call Scons from the terminal? That is exactly what I'm trying to show how to avoid while still keeping tools separated!



> 
 It is therefore simply yet another variation of the same approach taken by GNU's dev tools (ie, the programmer must learn yet another "programming syntax" in order to write a hand-written "make file"). For this reason, I don't consider it any more or less useful to a newbie programmer. There are things about it that may make it easier to hand write/edit the make file than with the GNU tools,


Yes, and that's the whole point.

The other approach of using an IDE with everything "in it" is something I had no intention of criticizing(#3) or writing about - as I know almost nothing of those things.

The article was however posted as a reaction seeing as there has been a lot of people having problems getting started with GTK+/Glade using Anjuta or the IDE-approach in general(?) and there didn't seem to be _anyone_ who could help them with these problems(?). I couldn't really help them with these problems using their approach, so I chose to post an article that shows another approach. Feel free to post a response showing how to do these things in Anjuta or another IDE. I'd actually enjoy that as I haven't checked out Anjuta or KDevelop in many years.


#1: Actually this diversity in toolkits might have brought good things. The good tools might not have been created if the developers had only one choice in toolkit and would happen to not like that one toolkit.

#2: But I do understand the topic here of "approach as a whole" vs. "other approach as a whole". I'm just not very interested in discussing that. I'd like to leave that up to you guys if I can (yay .. no lord .. lol) while focusing on helping the people who might want to try this approach. :)

#3: Well, I did mention "hair" and "mess" in context with Anjuta .. but still :}

---

### Post by lnostdal on 2007-02-18
> **j_g said:**
> (As an aside, in looking over the SCons docs, I noticed that the SharedLibrary example does not issue the -fPIC compiler option.


```
env.SharedLibrary('lib/oxymora-util', Split(""" ..... """))
....
g++ -o oxymora/util/debug.os -c -g -Wall -fPIC oxymora/util/debug.cpp
....

```

It has both support for creation of static and dynamic libraries. It's not a problem.

> Furthermore, the docs completely neglect detailing how SCons would be used in conjunction with a packaging tool like rpmbuild.

This shouldn't be a problem either, but I can't help you with this off-hand as I haven't used rpmbuild before.

---

### Post by cybrid on 2007-02-18
Hey, you both, this was begining to be a very helpfull thread about begining GTK with commandline tools, now it seems more like a rant GUI vs Command Line (well, that thread's title) and I think helping is better than ranting so. please Inostdal, could you continue with your tutorials?. They are helpful. If needed this could be moved to another separated thread :)

The fact is that since I began programming C/C++ under Windows and MS VS, I didn't know what a makefille was for untill today, after reading Inostdal tutorials, so thank you :D

---

### Post by lnostdal on 2007-02-18
thank you for your response :)  ..any suggestions as to what i should write about next? (#1)

> If needed this could be moved to another separated thread
yes, that might be a good idea .. i'll post the next tutorial in a separate thread dedicated to these little articles alone


#1: i had some sort of plan or a list of things i was going to write about (in response to often asked questions etc.) somewhere but i seem to have misplaced it .. :P

---

### Post by cybrid on 2007-02-18
I think that a small tutorial about "definitions" would be great, I think a lot of programmers comming from a windows enviroment get confused (like me) with the ton of tools GNU/Linux offers.

Maybe something explaining the difference between the different tools and things like what a makefile is, the packaging utilities and so...

---

### Post by j_g on 2007-02-19
I know _exactly_ where you're coming from. I'm a Windows developer. I've used various GUI driven dev tools such as VB.NET, MSVC, etc. I always knew what a makefile was for, even when I was using those tools. It's just that I never had to actually hand-edit any makefile, nor create _any_ other convoluted text file containing any kind of "macro/shell language" for the purpose of creating a make file. I never had to, because the IDEs were capable of completely managing the makefiles via data that I entered exclusively through the UI.

If you go to the GNU website, you'll find tons of "manuals" that explain to you in excruciating detail what each tool is for, and how it works. Here's a URL to get you started on your quest through dozens and dozens of pages:

[http://www.gnu.org/manual/manual.html](http://www.gnu.org/manual/manual.html)

Now I suppose someone can write even more detailed tutorials than these pages, and take you along the way at a slower pace (although it would probably take a person a few years of work to come up with such a volume of text), but here's the bottom line:

These are very complicated, convoluted, and frankly from a perspective such as yours and mine, unintuitive tools to use. You can read all these manuals until your eyes fall out, and your brain can maybe retain enough of the voluminous details of each tool such that you'll actually be able to do something useful with them. (I know, because I'm actually creating Linux software with them right now). But they will never be easy to use. They will never be as easy as VB.NET. Never. They will never be half as easy as VB.NET. They will never be a quarter as easy as VB.NET. These tools are designed to take into account so many variables/installations/quirks in the entire Linux universe, that they can never be anything but tremendously complicated and convoluted and unintuitive. Think about it. Someone somewhere at this very moment is taking a Linux distribution, and for god knows what reason, changing one damned thing about it supposedly to make it better, and releasing yet another distribution. And now the GNU tools have yet one more quirk to take into consideration. Let's see, shall we accomodate it by making yet another "implicit rule", or maybe a "macro", or how about an "environment variable"? How about all 3 of them? Hey, it's free software so it's not like you have to pay 3x as much for all 3 things. And wait, this is getting really hard to use what with all this stuff heaped on top of it. So let's make another utility that spits out a bash script that makes the data file needed by the first utility. And of course, let's not make this second utility UI based, with controls the programmer can click on to select his features, and enter filenames, and such. No, let's make this second utility text-based just like the first one, so that you need to learn yet another "macro/shell/syntax language" and have even more data files to keep track of. And of course, as more and more deviations happen in the Linux world, we'll add stuff to this second utility too.

Finally, someone gets the idea to make things "easier" than those tools. What does he do? He makes another text-based utility of course, with yet another macro/shell/syntax language that tries to cover the exact same ground as the first set of tools. Yep, this one is going to be all things to all people too, but somehow it's going to be better. Now we have two tool sets that essentially do the same thing, and even in essentially the same way, but they're different for the sake of being different. But wait. Now we need to transfer data between the two of them, so we need to make a utility to do that. And no, let's not make just one such utility. Let's divide our resources making dozens of them, each one doing essentially the same job, but in an arbitrarily different way that will somehow mean that support personnel will have to deal with yet more quirks/inconsistencies/variations on the exact same theme.

Madness. Sheer madness.

These dev tools are so complicated that even the IDE that tries to make them easier, is itself convoluted, complex, and ultimately unintuitive.

This is what you're dealing with in Linux. The only way to avoid it is to go back to my very first message in this thread. Fire up Gedit to write your C source. Go ahead and write a C file that compiles only on Ubuntu. What's that? Tom's distribution doesn't have a "sys/types.h" include file? And it puts its "socket.h" file in the "sys" directory instead of the main include directory? Too bad. Tom wants to use something that achieves essentially the same results, but arbitrarily chooses to do it differentl? Then, let Tom deal with the hassle of incompatibility.

Then use Gedit to write a very, very simple makefile like I described. Forget about all those "auto" utilities. Go ahead and write a makefile that works only on Ubuntu. Say no to every other Linux distribution quirk. Let's start forcing people to think twice before they create yet another package that is essentially the same thing as dozens of other packages, but just different for the sake of being different. Pick one UI toolkit, such as Gtk+, and stick with it. Say no to the plethora of alternatives that amount to essentially the same thing, except made by someone else, with a different way of achieving the exact same result. Install all the dev files for your chosen toolkit.

Name your makefile "makefile" and put it in the same directory as all your C sources. Open up a terminal, cd to that directory, and just type "make". Don't worry about "installing" it. You know where it is.

After all is said and done, this is as easy as it gets (under Linux).

---

### Post by cybrid on 2007-02-19
And I thought that a shell utility was maid for anyone could write a gui interface for it instead of being tied up to just one :-s

---

### Post by j_g on 2007-02-19
Yeah, but this isn't just one "shell" (ie, text-based, command-line issued) program. You've got autoscan, which generates a text-based configure.scan file. Then, you've got automake, which takes a text-based makefile.am file and generates one or more text-based makefile.in files. Then, you've got autoconf, which takes a text-based makefile.in,  and text-based configure.am file, and generates a very convoluted, text-based configure file. Then, the configure file generates a whole boatload of other text-based files.

You're an intelligent being capable of easily reading text and applying deductive reasoning to it. A computer can crunch numbers fast, but it's not so good at deductive reasoning and making complex choices by analyzing text. If you can barely make sense of the above tools and their output, what luck does an IDE have?

The problem isn't necessarily that an IDE is riding atop of text-based tools. Microsoft's Visual Studio does that too. The problem is that an IDE is riding atop of a whole mess of text-based tools that churn out way too much information, in a format that is way too free-flowing and poorly structured, all for the sake of trying to be all things to all people from the ancient past (in computer terms), to now, to the day that the last Linux guy ever forks another package and therefore causes another inconsistency to accomodate.

---

### Post by Jimmy_r on 2007-02-19
I am glad there are other people than me thinking about this...

In a perfect universe, I could start SuperIDE(oops the name is in use, nevermind), choose my programming language and write my code.
When finished, I would click the "Create Distributable packages" button and have it output a deb, a rpm, a tarball, an ebuild etc, which would be installable on all systems.
Even better, output one .package package, which would be installable everywhere...

In fact, to package a simple python program(see signature) properly I had to spend two days.

I even tried downloading an other packaged python project(alacarte) to see how it was packaged, but it was using some pycentral thing which I found no documentation about whatsoever...

And I was unsuccessful until I found this video: [http://showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37](http://showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37)
A 23 minute long video... That speaks for itself.

I just find it ridiculous that it is harder to learn how to compile and package software than it is to learn a new programming language.
I never needed a video to learn python, not even to learn C++...

---

### Post by lnostdal on 2007-02-19
While I agree with a lot of the problems you describe j_g, I'd like to mention that tools like for instance scons and cmake where actually added for a very good reason as there are some very real and fundamental flaws and problems with make.

But yeah, the differences between distros and the problem of distributing software because of this is something we're stuck with for the time being.

I take the easy "brute force" way out though; I do not bother with .deb, .rpm, automake, autoconf etc. at all.  I make a simple `install-ubuntu.sh' file (and a `uninstall-ubuntu.sh' file for later) that calls apt-get and gets all the required dependencies before installing the software itself either in /usr/local/, so it does not "disturb" other stuff - or in the users home directory. Basically because I do not have time to bother with the "ideal solution" that try to be compatible with everything at once. This works well for me, at least for the time being.

---

### Post by cybrid on 2007-02-19
Hmm, maybe a good solution for everyone could be using XML for make files and a common api. What do you think of this?

---

### Post by lnostdal on 2007-02-19
maybe .. but it will be hard to describe anything else than declarative stuff then .. i mean; how would you do things like `if-then-else', in general describing imperative actions - using XML? .. it would end up quite hairy i think

while a common api(#1) might have been ideal if it was what everyone agreed is the "best api" for their task -- it's not going to happen for the same reason some people prefer python, some people prefer ruby and some people prefer lisp .. or some prefer emacs while others prefer vim .. or even some prefer windows while others prefer linux .. etc.etc.


#1: i'm not sure what API we're talking about; do you mean a GUI API here?  ..assuming you mean a GUI-API:

is this a real problem? isn't GTK+ or QT common already because they are _available_ (the installer can just call apt-get libgtk2.0-0 or emerge libgtk2.0 (on gentoo .. etc.) -- well, or create a .deb or an .ebuild-script ofc.) on _all_ distros - even ones "dedicated" for only kde or only gnome? 

i actually view this as a good thing as i'm certain most developers here wouldn't like to be forced into using one they didn't like or one that would not be as suitable as the other for the task at hand

on win32 you have the same problem - but with no package-managers available at all so i'm not sure that situation is in any way better btw. .. or you can just use the one that is "common"; low-level win32 gui programming is not very nice .. (as a note here xlib is "common" in the same sense on linux here)

..a problem i do see is how GTK+/Gnome and QT/KDE (and others) use different libraries to communicate between applications etc. .. this should be handled in a library beneath both GTK+ and QT (and others) and i think this is what DBUS and the libraries around it is trying to solve atm. .. it would be nice to see something that worked with both local and remote IPC though

---

### Post by yaaarrrgg on 2007-02-19
> **lnostdal said:**
> maybe .. but it will be hard to describe anything else than declarative stuff then .. i mean; how would you do things like `if-then-else', in general describing imperative actions - using XML? .. it would end up quite hairy i think


In the Java world, Apache Ant uses XML.   Also, there's an additional modules for conditional compilaton (like AntContrib), and other things.  I believe C compilation is supported to some degree as well, but have never tested this.

---

### Post by j_g on 2007-02-19
> scons and cmake were added (because) there are some very real and fundamental flaws and problems with make.

Oh absolutely. I don't argue with that. I just wonder why the authors choose essentially the same paradigm that the GNU tools already use (ie, the programmer has to hand-create a text-based data file written with a particular "syntax language", using a text editor that is not specifically integrated with that dev tool). If that's all they were going to do, then they should have instead taken the GNU sources and "fixed" the flaws in them. It would have ultimately amounted to the same thing in practical, useable terms.

But we have Gnome and QT. We've had them for years. They are supposed to be mature. These are the technologies that are making Linux a competitor to Windows. So why are developers _not_ leveraging them in making dev tools? (And I'm not counting IDEs that ride on top of these too convoluted, poorly structured, free-flowing text-based approaches, because things like Anjuta show the perils of this approach). Why didn't the SCons folks say?:

"OK, let's start with the premise that this tool is going to be UI based. Let's pick a mature UI toolkit that does what we need. Now let's make a UI that lets the user enter all the data we need via controls. And let's store the data in a binary format since the user will _never_ manually edit it. A binary format is _much_ easier for software to parse and analyze than a convoluted text format, especially one with all manner of 'conditional expressions'. Let's not be stupid about it. Let's pick an extensible binary format such as IFF which has been successfully used for years and years, or something that at least supports the concept of 'tagged data' such as XML. What? Some guy over there doesn't have support for this mature UI, and still wants to use a text editor to hand-create a text-based 'make file' that has all manner of conditional expressions in its syntax so that he can accomodate systems that also don't support the mature tech we're using? So let him use the GNU tools. This tool is not intended for him. Enough is enough. This tool is supposed to represent progress/change, which is what Linux needs."

> how would you do things like `if-then-else', in general describing imperative actions

You mean like;

#ifdef WIN32

#elif AIX

#else

#endif

Very easy, if you're using a file format that supports "tagged data". For example, in XML, if the user selects the check box labeled "IBM AIX" (inside a frame labeled "Target OS"), then the following data tag will appear in the file (within another, appropriate tagged-data "header").

<TARGET>AIX</TARGET>

If he selects "Windows" instead (and maybe selects the radio button labeled "32-bit" rather than "64-bit"), then the above tag will not be found in the file. Instead, the file will contain:

<TARGET>WIN32</TARGET>

If he is allowed to select both AIX and 32-bit Windows, and he does, then both tags will appear in the data file.

If he selects the "None of the above" box, then neither of the above tags appears in the file.

And of course, when the dev tool reloads the data file, it should note what is selected and use this info to create output files (like an executable, installer, or sources) geared for the selected systems. If it's too difficult to accomodate a particular system because it's too oddball and/or limited, then don't support it. Let people who make convoluted, poorly structured/integrated, "I'm all things to all people" dev tools, such as GNU tools, support those folks. And let the oddball folks use that stuff. They _deserve_ it. Don't inflict it upon the rest of us.

Those of us who were weaned on operating systems that were not based upon Unix (typically text-based data files) or MS-DOS (typically non-extensible, non-tagged data files) were weaned on tagged-data, extensible binary formats, so this stuff is all old hat. Linux programmers need to come up to speed on this stuff. I mean, it's good that we're starting to see newer versions of software (such as gconf 2, and glade) finally grasp the concept of tagged data, but what took Linux programmers so long, and why are the dev tool programmers _still_ not "getting it"?

> if it was what everyone agreed is the "best api" for their task...

Please believe me that I'm not attacking you personally. I know what point you're making here. It's just that, while I support the concept, and your affirmation, of "choice", I believe that the "implementation of choice" on Linux leaves much to be desired. A real choice isn't:

I can get a hamburger at McDonald's, or I can get a hamburger at Burger King, or I can get a hamburger at Wendy's.

Real choice is:

I can get a hamburger at McDonald's, or I can get a specialty gourmet exotic dish at the restaurant next door, etc.

If Linux is so big on choices, why are so many Linux developers (particularly the ones making dev tools) fixated upon making an offering that attempts to "be all things to all people"? I mean, if you're making something that ends up being all things to all people, why does anyone need anything else?? And why are so many Linux developers all using the same paradigm for their software? What's the point of choices if they're all essentially the same hamburger?

I initially chose Anjuta because I was running a Gnome-based distribution (Ubuntu) and planned to develop GTK+ based apps. Why didn't I pick KDevelop, or Eclipse, or something else? Well, I thought:

"Anjuta purports to be especially geared for Gnome development. I'm assuming that it is written using Gnome libraries, and will be easier for me to develop Gnome apps with it because its IDE will have lots of Gnome-specific stuff to help guide me, and it will produce output files that will be geared to install/distribute my stuff for Gnome distributions like mine. It will integrate better with my Gnome desktop. Etc.".

What I discovered is that Anjuta is more of a "Gnome facade". It really rides on top of these "I'm trying all be all things to all people" GNU dev tools, and relies upon them to do too much work. It  isn't geared for Gnome distributions. It's yet another tool that ultimately tries to be all things to all people, and ultimately fails at being particularly good for anyone in particular. It's yet another one of those typical Linux apps which screams "I'm pretty much the same thing as those other 300 'choices', all of which are pretty much the same thing as me, but we have minor variations in the way we implement the same paradigm, so my ultimate purpose is to just make you deal with yet more inconsistencies, dependencies, variations on a theme, and other stuff that doesn't offer you any real added value. I just offer you more of the same headaches.". Welcome to the Linux concept of "choice".

We need more people addressing specific target audiences, and offering truly different paradigms, and a whole lot less people forking stuff and just making their own versions of everybody else's 'choices' just so they can say "My 'choice' does all the same things as these other 'choices' plus one or two more things. But what I've neglected to tell you is that it basically is another rehash of the same approach, and yet, because I've heaped a few more things on top of it, it's going to be at least as convoluted, unintuitive, inefficient, and difficult to learn/use as all the other 'choices'.".

Ok, whomever swiped my soapbox, you bring that thing back here right now!

> I am glad there are other people than me thinking about this.

I believe there are lots of people thinking about this. Often, they are afraid to voice their opinions because folks who were weaned on Unix, and have never really spent any time using any other paradigm (especially GUI-driven stuff), insist that things would be "better" for everyone if we all just attempted to acclimate to convoluted, unintuitive, text-based "I'm trying to be all things to all people" offerings. And I also believe a lot of those former people are looking at Linux and rejecting it because of the nature of its 'choices'. I can't tell you how many times I, as a Windows user/developer, installed versions of Linux, tried them out a bit, and then rejected them. This is the first time, after several years of evaluation, that I finally have taken a serious plunge into Linux. I did so because, for the first time, I felt that things like the UI, installation of available software in "repositories", ease of administration, etc, met or surpassed at least my minimal standards of usability. Then, I went to develop Linux software, and man, after pulling my hair out to hunt down some tools that actually work for me, and being an experienced enough developer to figure out how to deal with some compiler/linker issues, I've found that it just barely... and I mean, just barely... is usable. This is a perilous state of affairs if Linux intends to attract any Windows developers. Linux dev tool makers need to start thinking differently because what they're doing is not working well versus the Windows competition.

---

### Post by Mirrorball on 2007-02-19
Windows developers have those tools to help them, because there are only a few Windows versions. On the other hand, there are thousands of Linux distributions and there will always be. Linux is about choice. If this makes development harder, there is nothing to be done about it. Of course you can create the magic tool that will be able to solve all dependency problems in all distributions, but currently this magic tool doesn't exist.

But hey, we are writing free applications. Maybe you don't have to learn any of those complicated tools. You *can* just write your app as if only Ubuntu existed and then ask someone else to integrate it with other distributions. We don't have the tools you want, but we have people to help you. Lots of people how to use those complicated auto tools. You don't have to learn them if you don't want to.

---

### Post by Keffin on 2007-02-19
Disclaimer: Please note that I actually have little to no knowledge of scons. I do however know cmake, and believe from what I have read that scons is similar and (probably) has made many similar design decisions. So while most of the discussion has been wrt scons, I'm hoping my knowledge of cmake applies ;).

> Oh absolutely. I don't argue with that. I just wonder why the authors choose essentially the same paradigm that the GNU tools already use (ie, the programmer has to hand-create a text-based data file written with a particular "syntax language", using a text editor that is not specifically integrated with that dev tool). If that's all they were going to do, then they should have instead taken the GNU sources and "fixed" the flaws in them. It would have ultimately amounted to the same thing in practical, useable terms.

Simply put, cmake does not choose the same "paradigm" as the GNU autotools. cmake uses a syntax that it seems would be simple (as simple as such things can be) to wrap a nice gui interface around, so you can never look at it again if you don't want.

But you also have the flexibility of - in the meantime before cmake takes over the world and people write these gui tools - being able to hand edit the files as well. Note that the whole build system of KDE 4 is cmake, so said gui tool will I'm sure be well integrated into KDevelop 4.

Fixing the GNU auto-tools to be simple to create gui tools around, or even to make them vaguely simple to hand write (:P) requires chucking it in the bin and starting again imo. And that is what has happened.

> Why didn't the SCons folks say?:
 
 "OK, let's start with the premise that this tool is going to be UI based. Let's pick a mature UI toolkit that does what we need. Now let's make a UI that lets the user enter all the data we need via controls. And let's store the data in a binary format since the user will _never_ manually edit it.

I do not know exactly how the cmake project started, but I could very well believe it was exactly like this. Except why should you force people to use a certain toolkit (you even say later in your post you wanted anjuta because it blends with **your** choice of desktop)? i.e. lets make a back-end that people can build gui tools on top of easily. And for the love of god don't ever put these things in dodgy binary formats, make it text based so the people who want to can use it without IDE lock-in. XML (as you suggest) or cmake syntax work fine for this.

However, your main point seems to be that there should be a friendly face to these things, which I agree with. On the plus side, I do think it's coming, and the frameworks to build them (yes them - you can't be all things to all people :)) on are taking shape nicely.

---

### Post by cybrid on 2007-02-19
Soooooo. Can anyone name a tool-set (IDE-Make-Other...) that is constistent and fast to learn to develop gnome (GTK) apps ?. I normaly code in C / C++ or Java. I use Netbeans for Java, so for C / C++ ?

---

### Post by lnostdal on 2007-02-19
> **j_g said:**
> Oh absolutely. I don't argue with that. I just wonder why the authors choose essentially the same paradigm that the GNU tools already use (ie, the programmer has to hand-create a text-based data file written with a particular "syntax language", using a text editor that is not specifically integrated with that dev tool).

probably because they prefer that paradigm for various reasons .. in my opinion make is so broken that you cannot really build upon it; not with a UI or anything


> **j_g]
 If that's all they were going to do, then they should have instead taken the GNU sources and "fixed" the flaws in them. It would have ultimately amounted to the same thing in practical, useable terms.
[/quote]
probably because sometimes starting from scratch is less work than trying to work on a very broken code-base or design


[quote=j_g]
But we have Gnome and QT. We've had them for years. They are supposed to be mature. These are the technologies that are making Linux a competitor to Windows. So why are developers _not_ leveraging them in making dev tools?
[/quote]
i can't speak for others but i'm happy with what i'm currently using .. many of the tools i use use old toolkits because they where made back when only those toolkits where available - and it is considerable work rewriting these for new toolkits said:**
> 
Why didn't the SCons folks say?:
....

i guess because they had different goals and views on how things should be done .. 

making a build-tool UI based sounds like a bad idea to me .. wrapping a dedicated UI around it sounds reasonable - but i don't feel a need to do that or even use something like that myself if it existed


> **j_g]
You mean like said:**
> 
no, not quite -- this wasn't what i meant .. to use your example; the build tool should itself (no user interaction) be able to "select AIX" and do different things based on that

this might be needed even while targeting only one kind of distro/system


[quote=j_g]
Those of us who were weaned on operating systems that were not based upon Unix (typically text-based data files) or MS-DOS (typically non-extensible, non-tagged data files) were weaned on tagged-data, extensible binary formats, so this stuff is all old hat. Linux programmers need to come up to speed on this stuff. I mean, it's good that we're starting to see newer versions of software (such as gconf 2, and glade) finally grasp the concept of tagged data, but what took Linux programmers so long, and why are the dev tool programmers _still_ not "getting it"?

right .. :) in any sane parallel universe we would actually all write lisp on lisp-OS'es and code would be data and data would be code .. everything could receive and send data from/to everything else; no need to parse at "character-level" ..etc..


> **j_g]
Please believe me that I'm not attacking you personally. I know what point you're making here. It's just that, while I support the concept, and your affirmation, of "choice", I believe that the "implementation of choice" on Linux leaves much to be desired. A real choice isn't:

I can get a hamburger at McDonald's, or I can get a hamburger at Burger King, or I can get a hamburger at Wendy's.

Real choice is:

I can get a hamburger at McDonald's, or I can get a specialty gourmet exotic dish at the restaurant next door, etc.
[/quote]
oh, i disagree .. there is a lot of difference between for instance GTK+ and QT IMHO .. same with improved make-tools compared with old make

edit: maybe you view everything the same because you're missing details .. i remember once as a kid going to a school where there where many asian people..  i could not tell the difference between them said:**
> 
If Linux is so big on choices, why are so many Linux developers (particularly the ones making dev tools) fixated upon making an offering that attempts to "be all things to all people"? I mean, if you're making something that ends up being all things to all people, why does anyone need anything else?? And why are so many Linux developers all using the same paradigm for their software? What's the point of choices if they're all essentially the same hamburger?

i'm not sure what you mean here .. scons and make are build tools; i don't think they are trying to "be everything" - i actually think they are trying to avoid doing or being something like that 

or - well, since scons actually is python - scons has more potential to be "misused" in being used for everything .. but since the python-language is quite a bit less broken (or more flexible) than the make-language this might not be a bad thing


[quote=j_g]
I initially chose Anjuta because I was running a Gnome-based distribution (Ubuntu) and planned to develop GTK+ based apps. Why didn't I pick KDevelop, or Eclipse, or something else? Well, I thought:

"Anjuta purports to be especially geared for Gnome development. I'm assuming that it is written using Gnome libraries, and will be easier for me to develop Gnome apps with it because its IDE will have lots of Gnome-specific stuff to help guide me, and it will produce output files that will be geared to install/distribute my stuff for Gnome distributions like mine. It will integrate better with my Gnome desktop. Etc.".
[/quote]
yes, this sounds reasonable..

[quote=j_g]
What I discovered is that Anjuta is more of a "Gnome facade". It really rides on top of these "I'm trying all be all things to all people" GNU dev tools, and relies upon them to do too much work. It  isn't geared for Gnome distributions. It's yet another tool that ultimately tries to be all things to all people, and ultimately fails at being particularly good for anyone in particular. 
[/quote]
.. ah, you're going somewhere - this makes sense; you want a specialized IDE for Gnome/GTK+ development that "just works" .. fair enough :)

..but i wouldn't want to remove the GNU-tools, make, or improved make-tools like scons or text-based build-files in general and "replace" them with this..   the Anjuta you wish for can leverage the best tools, or it can do something entirely else (not use external tools at all?) -- but these things aren't mutually exclusive

..and if something like that existed, say if anjuta improved - i'd still use my old approach with a setup of small separate tools that communicate; as it works very well for me .. but this might just be the emacs vs. vim thing again

---

### Post by j_g on 2007-02-19
> Can anyone name a tool-set (IDE-Make-Other...) that is constistent and fast to learn to develop gnome (GTK) apps... for C/C++?

I already answered this in my very first post that kicked off the thread, and expounded upon it even more in further replies.

If you've already looked at Anjuta and rejected it as not very good, then you've already looked at the "best" and "easiest" Gnome oriented IDE for C/C++. That's it. There it is.

But if, like me, you found it to be flakey, unrefined, unintuitive, and too difficult/frustrating to use, then I recommend you go back to my first message and follow my instructions for learning how to write a simple, rudimentary makefile that works on your own Ubuntu system.

By all means, you absolutely should get the Glade 2 UI Builder to create your UI. It's pretty good, and you won't feel that out of place from the UI builder in something like VB.NET. It creates an XML data file. And of course, read a tutorial about how you use the libglade library in your C/C++ code. libglade takes that XML data file, loads it on the fly when you call libglade's glade_xml_new() function, and creates all of the window/controls (the latter are called "widgets" in Linuxland) for you. Think of it as a very, very fancy version of Windows API DialogBox where you're loading a UI from a "resource" you created with a UI builder.

Then you call glade_xml_get_widget() to get a "handle" to a widget, just like you'd call GetDlgItem to get a handle to a Win32 control. But whereas Win32 controls use binary "ID numbers" to identify them, Gnome widgets are identified by a "text-based string name" you give each one. (Everything about linux is text-based). And whereas Win32 controls send you a "message" when something happens, Gnome widgets don't do that. You have to write some C/C++ function, and then tell a specific widget, for example a button, "call this here function when the enduser clicks on you". Every widget has a whole bunch of "actions" to which you can register your own "callbacks" and each action has a (bet you'd never guess) text-based string name, such as the "clicked" event for the aforementioned button.

That part of Gnome development is not that difficult.

But if you're looking for a GUI-based tool to help you manage/maintain/debug/package your Gnome application, forget it. As someone who is coming to Linux from Windows, you have nothing to look forward to except some very frightening, disturbing, and other-worldly things.

Write your C code in something like GEdit, forget about all of these auto-whatever utilities, or python-assisted "make systems", or what have you. Just learn the very rudimentary basics of a make file (name it "makefile"), open a terminal window, and simply type "make". That's really as easy as it gets, and this is coming from a guy who loves IDEs and uses MS "Visual tools" nearly every day.

---

### Post by Mirrorball on 2007-02-20
Once upon a time, there was a clock on a wall at my school. I hate wearing watches, they make my wrist itch, and this clock was just at the perfect location to help me not miss classes. Whenever I wanted to know the time, I just had to look up. I was really mad when the clock broke and it wasn't substituted immediately. How was I supposed to know when it was time to go to class after the break? Stupid clock, but I was totally dependent on it. It was so irritating when I forgot that it was broken and I looked at it and the hands were pointing to absurd numbers. Unfortunately I had no one to complain to and the clock was broken for a very long time. I guess I was the only one that cared. So I (grudgingly) started checking the time on my cell phone. And after a while it became just as natural and convenient.

Maybe it's a silly example but I never forgot it because years ago it served me well years ago when I tried to persuade a guy that he didn't really need [insert silly MS Outlook feature], he could live without it. Are the auto tools really so bad? Or aren't they just different from what you expect? Do you really need the tools you miss?

---

### Post by j_g on 2007-02-20
> Are the auto tools really so bad?

I think so. Personally, I think that they're mostly all unusable. The only one I use is Make, and then I employ only the most minimal, rudimentary make file. My makefiles are really very spartan (a typical example you'll see in my very first post in this thread). I would never use any of those GNU tools for anything more than that.

> aren't they just different from what you expect?

Very much so. But that still doesn't make them usable for me.

> Do you really need the tools you miss?

Technically, no. I am getting done what I need to, with a lot of hassle and expenditure of time. But I've ended up essentially going back to developing software the way I did for an Amiga in 1986. When I moved to Windows, and started with GUI-based tools such as IDEs, I quickly became more prolific, and efficient. I distinctly remember telling people within the first few weeks of my switch, "This is better than what I was doing before".

Despite the fact that I'm now an even more experienced programmer, I've not experienced the same thing in my endeavor with Linux. Quite the contrary. I've become a lot less prolific and efficient. What I did the first week in my Windows programming seems to be taking me a month in Linux. Rather than saying "This is better than what I was doing before", I'm saying "This is a lot worse than what I was doing before". Again, I don't _need_ those tools. And I'm willing to "waste some time and effort" anyway in order to develop some Linux stuff. But I can definitely see many other people not being nearly as generous with their time and effort. At certain points during my ordeal with Linux dev tools, I could very, very easily imagine other people throwing up their hands and saying "This isn't worth it. I'd rather spend my time and effort doing something else".

I'd say it's a fair conclusion that a lot of other people _do_ need those tools that I miss.

---

### Post by lnostdal on 2007-02-20
i would not recommend a newbie(#1) using make for even simple tasks .. it does not even handle dependencies between files automatically: [http://www.gnu.org/software/make/manual/make.html#Automatic-Prerequisites](http://www.gnu.org/software/make/manual/make.html#Automatic-Prerequisites)

..and there are a lot of other problems with it .. in general i'd really consider using a better build-tool .. almost anything else is better than plain make and is quick and easy to learn and use..


#1: or anyone else starting a new project where they have the opportunity to use something else

---

### Post by cybrid on 2007-02-20
So what would you recommend for a newbie to start with Linux/GTK development?

---

### Post by lnostdal on 2007-02-20
he should probably start by using anything else than make .. i've already shown one way of getting started in the writings(#1) i linked to back here

edit:
note that this is if we limit ourselves to only using C for development under Linux using GTK+ .. build-tools like make and scons aren't needed for Python, Ruby or Lisp development for instance

#1: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

---

### Post by Jimmy_r on 2007-02-20
> **Mirrorball said:**
> Are the auto tools really so bad?

Automake and friends?
Just ask the KDE developers...

Or, let me ask one for you:
[http://aseigo.blogspot.com/2006/04/over-cmake-speedbump.html](http://aseigo.blogspot.com/2006/04/over-cmake-speedbump.html)
> moving away from autohell was probably a good idea.

> portability, maintainability, the annoyance that is recursive make jobs, the god awful syntax used in configure scripts, the size of the build system (in application releases, the build infrastructure in admin/ was often larger than the source code, icons and data files put together) were all amongst the issues that pushed us away from auto*

Especially note the flattering name they have come up with for autotools.

---

### Post by cybrid on 2007-02-20
Just a stupid question, are CMake and SCons for the same porpuse?

---

### Post by lnostdal on 2007-02-20
> **cybrid said:**
> are CMake and SCons for the same porpuse?
yup

[http://en.wikipedia.org/wiki/CMake](http://en.wikipedia.org/wiki/CMake) "CMake is an extensible, open-source system that manages the build process .."
[http://en.wikipedia.org/wiki/Scons](http://en.wikipedia.org/wiki/Scons) "SCons is an open source software build tool .."

---

### Post by cybrid on 2007-02-20
Well, after searching a bit, CMake seems the way to go nowadays for C / C++ projects. so I think i'll give it  a try, and also, there may be a gedit plugin to integrate CMake into a project, witch would be cool :)

---

### Post by Mirrorball on 2007-02-20
autohell :lol:
Disclaimer: I don't use the autotools myself, because I don't distribute the software I write. I use Eclipse for C++ and PHP, text editor for everything else and it's very simple. I have already written very simple Makefiles too and it was easy.

---

### Post by amiga_os on 2007-02-23
I totally agree with j_g.

I'm writing an SDL/OpenGL game which has hit the rocks.  It's got nothing to do with SDL, OpenGL, C or C++... it's simply got to do with my having to change dev environments all the time.

I wrote substantial amounts of the code in KDevelop (which is largely a great IDE), however, that tied me to a KDE desktop (which, to be honest, I can't stand, Gnome is so much more intuitive).  But KDevelop uses autohell(tools) which mean that substantial parts of my application code are complete gobbledegook to me.

This is bad, because, for some reason KDevelop can compile & link my code, but, from the command line (emulating everything KDevelop does exactly) g++/make/etc can't... which means my program is undistributable outside of people with KDevelop.

Furthermore the "Create package" menu in KDevelop doesn't work, so I can't export the project.

The gcc/g++ debugger is too hard for me, so I need to debug in KDevelop, then move all my source code into a new directory, and write my own Makefile to release it.  Don't even get me started on Anjuta... it simply does not do what it's supposed to.

This is all really, really rubbish.  How can people contribute to the community if they can't compile stuff.  I've wasted more time in the last 8 months of moving to Linux learning the tools than I have learning the languages and API's I want to use.

Development tools are caught between the two stalls of universality and simplicity.  I think that to help more noobs like me move into *nix programming there needs to be some kind of visual IDE that majors heavily on simplicity.  Only then can the net be broadened and other stuff supported, when SimpleIDE does one thing really well.  Also, it's better to have lots of developers who have come in through an easy route then start thinking about the universality of their code, rather than filtering people at the first hurdle.

I understand the ideas of "choice" and "freedom"... however when I first moved to Ubuntu, I got excited about "contributing" and playing my part... I wanted to do something.  I wanted to contribute code... but I didn't have a clear idea how or where.  Rather than exercising choice all I did was go for the lowest common denominator and start developing something I could actually compile and then see working.

<DREAM>
It would be great if there was an "Integrated Ubuntu Development Environment".  An IDE which was specifically written for easy development on Ubuntu.  Maybe at first it may only support C/C++ and Python (these seem to be the favourite languages around here), it's geared toward making GTK development very easy... and if a program works and is compilable then a nice GUI will allow you to edit .deb dependancies and a .deb is created with one click.  Another output option would give you a src-deb...

Simple is key... eventually more support would be added for Ubuntu .deb's for other architectures (64bit, SPARC, etc.).  The wizards would be expanded to make development with more and more API's easier (e.g. SDL, OpenGL, OpenAL, OGRE - that last one is a nightmare to get the latest version working).

The output options could be extended also - to include .rpm, compilable source tarballs, slack, ebuilds, etc. then other languages could be added.

Every version would focus primarily on ease-of-use over features, so the feature-set would be slow in coming, but stable and not buggy when there.  The IUDE would be modular and extensible.  The IUDE would be built using code from existing Open Source IDE's, but not at the expense of fully integrated that borrowed code into IUDE's well designed structure.

The IUDE would be a breeze for newcomers, a training ground for aspirants and a flexible tool for old hats.
</DREAM>

Never going to happen.  Instead, we get Anjuta...

---

### Post by lnostdal on 2007-02-23
ok, trying to grok your post here .. 

1. your main problem seem to be that the build-scripts generated by KDevelop are not human readable or maintainable

2. it seems (is?) impossible to compile the project without using the same IDE you do; users are tied to the IDE

3. using GDB by itself is hard or time-consuming; you want to use an interface for debugging


while i agree on these points -- what i fail to understand is _why_ people insist on holding on to this way of doing things (edit: still looking for the `Start'-button in the corner when you want to shut down?); why do you not split things into more independent maintainable pieces?

1: write your own build-scripts .. it is in most cases _very_ simple .. if you want i can or _might_ take a look at your project and show you a build-script that is human readable, expandable (adding new files etc. is easy), usable from any (non-sucking) environment (editor, ide, terminal) and maintainable 

2: make sure the build-scripts can easily be used from any environment .. starting with the command-line usually enables you to use it from any other environment also .. your editor should be able to call the build-tool triggering it to start the process, then it should be able to parse the output generated when the build-tool calls GCC  .. in short the tools must be able to communicate

3: use DDD which i can confirm works well -- or some other interface (someone mentioned KDBG)

i know i would never-ever contribute to a project that required me to use any given IDE because that is just bad design .. IMHO things _should_ be split out into independent human-maintainable pieces where it makes sense .. one tool for building, one for debugging and one for editing -- every tool should work by itself

---

### Post by amiga_os on 2007-02-23
Inostdal...

I totally respect where you are coming from.  Please understand that I do agree that having lots of choices and options of tools to do things is a healthy environment.  Also having tools that are designed specifically to do particular things well is a great idea, and that's fantastic.

However... there is a reason why I (and probably others) really like the idea of tight tool integration... it's not just because I'm wedded to one particular way of doing things.  It's because while a collection of tools that do one thing well is a good solution for various reasons, the tightly integrated and visual solution is good for other reasons.  It seems to me that the Linux community often leans towards the power-user, feature-laden, mega-steep-learning-curve approach a lot more than it leans towards the scared-noob, simple-to-operate, learning-can-be-fun approach.

While your solutions are great... and it seems your tutorials are also :) (thanks for them)... there is a place for the ideal Linux Visual Studio also.  It's not that ddd, etc aren't really really good... it's just that they are good in a particular way and, well frankly, I want things to be really really good in another way.

I started with Ubuntu about June last year... back then, if the three things you mentioned in your last post were the only way of programming and compiling in Linux, then I wouldn't have started.  I needed KDevelop, simply because it was simple and not scary.  But even then some things were a nightmare... finding out that I needed to set linker flags took me a week of teeth-gnashing.  Now, I learnt, and now I set linker flags otherwise my code won't compile... however I think I learnt much more in quantity, quality and efficiency programming with SDL and OpenGL, they are well documented, and they compiled quickly (apart from the linker problem).  So I spent most of my time beginning to learn about how to debug my code really well, and how to write code efficiently.

Take g++ on the other hand... just figuring out how to make the ddd debugger work is taking me ages.  At the end of the day I want to get good at debugging code, not using a debugger.  The debugger is a tool, and there are two ways a tool can be really good.  Firstly it can be really really useful and do lots of things.  Secondly it can be very easy to use, and not get in your way, letting you focus on the job, not on the tool.

What I'm saying is two things.  I'm saying that "this way of doing things" (i.e. go for simple, integrated, gui focussed IDE) is good for these reasons in particular:

1) It really does help noobs start a lot sooner (and thus in the long run learn the harder things better, they're (we're!) more likely to get to grips with the harder stuff, if we learn to walk before learning to sprint)

2) It is a more productive way of working for some people (in fact, heck, for many people)... not for everyone, maybe not for you (and that's fine :) )... but for many of us it is.

Traditionally *nix seems to have catered a lot more for the really clever/(masochistic?:)) people.  Ubuntu seems to me a fantastic distribution for people like me... interested in computers, willing to contribute, but without a degree from MIT.

---

### Post by lnostdal on 2007-02-23
hm, be sure to get the wording right:

* gdb is the debugger .. used directly from the console
* ddd is a graphical frontend or interface to the gdb-debugger
* g++ is the c++ compiler/linker 
* gcc is the c compiler/linker

remember to compile with the -g option so gcc/g++ generates info gdb/ddd can use when debugging(!) ..if you're having problems getting started with gdb/ddd i'd be happy to help .. maybe write a small text about gdb/ddd would be an idea .. it's not complicated or hard to use at all -- really, it's actually not a problem at all ..

.. you'll save very much time working _with_ the tools instead of working _against_ them ..   :)

i must say to you that the stuff you mention about linking with libraries and some other things are really _totally_ non-issues and is very much the first basic stuff you'd have to learn how to do in any environment (IDE or non-IDE) both on Windows and under Linux .. i take it understanding the relation/difference between header-files and libraries is something you've only recently started to understand? and that the build-process is a two-step process; you compile each file first, then link the set of resulting binaries to a library or an executable file  - and that the linker-flags are needed for the second _linker-step_ (not for the compilation as you stated)..? .. you might just be sloppy with the wording; i don't know -- but it might also reflect that you do not really properly understand how a C or a C++ build-process works in general .. this is really something you should be aware of even if you use an IDE that has a pre-setup that works "at the moment" .. i haven't read TCPL in years(#3) but i think it at least mentions something about compilation units, headers and the linking process(#1)

while i agree with your first point, mentioned near the end - that it might get the n00b started faster and that it might be valid for motivational reasons etc. -- i do not agree that it is more productive in the end as that n00b will have to back-paddle _very soon_ as he wants to do something that falls outside that pre-setup environment

it does not matter whether the n00b has to fill in the linker flags in an IDE text-field or in a build-script; in _both cases_ he must know and understand that there exists a linking step, he must understand linking, that it happens after compilation (so he must understand the surrounding environment/reasons for it) and that it takes certain arguments that describe how and what to link to/with .. 

not to seem like an ******* (but i am .. lol :)) -- i'm afraid that in the end lack of knowledge is the only real problem here as this is not something any IDE will help the n00b understand in general.. and it is not something that is time-consuming and leads to a focus on spending time on tools instead of problem-solving in a major way .. it is, IMHO - the exact opposite in the not-so-long-actually run

note that you can get both human-readable and easily maintainable build-scripts not depending on a specific IDE/editor, _and_ a productive environment(#2) -- at the _same time_


#1: i also link to some good resources specifically for usage of the gcc/g++ compiler/linker in the writings i've posted

#2: just because i _can_ use the tools from the console if i want to doesn't mean i do so while working normally with the code - which i do 97% of the time! i press one key and every changed file is saved and only the changed ones are recompiled before the result is linked together as an updated library/executable - it's fully automated and happens instantly .. this is also described in the writings i've posted

#3: heck; i haven't even coded c++ in a long time  .. moved on to lisp some time ago and only use plain c when optimization is needed (almost never)

---

### Post by amiga_os on 2007-02-23
I'm not asking for specific help with the gnu tools.  I was being liberal in my use of g++/gcc/ddd to refer to "that whole set of tools from gnu".

My reference to linking was just an example of how I can struggle with "lack of knowledge" and learn something, but that struggle was - essentially - pointless.  When I struggle with trying to solve a programming problem, then I'm actually *learning skills*, and working through something that will make me a better programmer down the line.  I'm learning the "art of programming".

However... the linker program was... as you yourself say, simply, lack of knowledge.  In trailing through internet sites because it wasn't obvious to me that I needed to set the linker flags (for a number of reasons), or indeed to set the linker flags in the particular way KDevelop wants you to do it - I didn't learn anything.  Yes I have a little more "knowledge", but I have a lot less "learning" than if I'd spent that time trying to connect quads together in the most efficient manner.  I only mention the linker issue as an illustration of this bigger point.

If I was starting again, and I didn't have KDevelop, there is no way I would have the knowledge I have at the moment.  I wouldn't have come as far as I have if right from the word go I was having to write my own configure and make files.  Now that I've seen the IDE do all that for me, it is much more intuitive, I understand why I need them.

But having said that, if I had an IDE that sorted all that out for me, that outputted a tar ball that could be "./configure make make install"'d on someone's system.  Then I wouldn't really care about not knowing about how the tools worked.  If I needed to find out, then I would.  But I wouldn't feel like I'm missing out on much if I didn't need to.

In essence, unless you program using assembly, then there is some level of "knowledge" you are fine not having.  The debate is really where we draw that line.  Very few people (maybe some crazy 31it3 hacker somewhere) will say that g++ mollycoddles because it allows you to program and never even think about the machine code - shock horror!  Well why can't I program an application, click a button, and never have to thik about the makefile or the packaging - it just does it...

I want to have a lack of knowledge about the intimate workings of the GNU tools, and the only reason that might be longer in the long term is because "one day I'll have to".  Well, one day I don't want to have to... but even if I did want to, then I think the transition from

1 - "absolutely no idea what a linker is"... to
2 - "writing my own configure scripts and makefiles"...

 is a lot longer and seems a lot less fun than simply adding the transitional steps...

1.5 - "writing and compiling programs using a really simple IDE"
1.7 - "hmm, now I'll take a look under the hood to see how this works because *now I know what I'm looking at!*"

If I found an IDE that auto installed necessary -dev's from the repository and automatically se the linker flags meaning that I wouldn't need to ever know about it, I would not say that I was any less the richer a programmer.  What I would think is that I can spend more time actually learning about the things I want to - how to use the language and API to achieve the desired result in particular circumstances.

---

### Post by amiga_os on 2007-02-23
This is a good example of the point I'm trying to make:
> I think python is a good language to start learning programming because I think the most important is to learn how to solve general programming problems.
If the problem at hand is "Write a program that checks wheter a word taken from keyboard input is a palindrome" then I think it is better if the first thing the new programmer thinks is "Then I should probably check the first and last character in the string for equality and move towards the middle" instead of "How do I get input from the keyboard"?
It's from this thread:
[http://www.ubuntuforums.org/showthread.php?t=233405]("http://www.ubuntuforums.org/showthread.php?t=233405")
In that particular thread they're talking about what programming language to learn first.  That's not my point... the point I want to draw out is that I agree with the principle that the first thing a new programming should think is "how do I solve this problem?" rather than "how do I do something mundane to allow me to think about this problem?"

Heck... new programmer or not, I always want to be asking the first question over and above the last one... hence why I want simple, intuitive, visual tools that take care of a load of stuff for me without me ever having to think about it.  It's not that I'm lazy... I just want to get stuck on solving logical problems rather than banal ones.

---

### Post by lnostdal on 2007-02-23
some tidbits that i'm not sure are directly related -- just random initial thoughts bumping into my currently very tired and buzzed-out head as i read your posts:

* i do not know how to get input from the keyboard in python...

* ...i am certain this is a problem with lack of knowledge from me but i am also certain that this knowledge is relevant to me solving the "actual problem" within "the realms of python"

* i've noticed that if i spend a short time preparing then i usually get an initial result fast -- but finish very late...

* ...and i've further noticed that if i spend a lot of time preparing then i get initial result very slow -- but last steps go very fast and is often more flexible and leads to saved time in the long run as non-trivial things (which turn out to be most things actually) tend to end up needing unforeseen changes or "being" different things than predicted

* you mention the word "line" somewhere; i think it is important to keep a line between what currently exists and how to use that as best we can -- and what would be ideal if it existed .. that way we can develop the ideal things faster

* that previous point is not to criticize your wish for ideal situations, as the ability to _imagine_ an ideal solution (even if i have problems imagining or understanding a couple of your points) is the _only chance_ of seeing changes in a direction/goal we all, of course - would want

---

### Post by cybrid on 2007-02-23
Hmm, just a lil break of your conversation; surfing I've found this simply fantastic web, witch I think can be a great timesaver for the newbie GNU/Linux programmer.

[http://users.actcom.co.il/~choo/lupg/tutorials/index.html](http://users.actcom.co.il/~choo/lupg/tutorials/index.html)

---

### Post by amiga_os on 2007-02-24
Inostdal... I don't think we're getting anywhere :) 

We seem to be talking across each other a lot.  e.g. I don't really care about python... it's just that the principle that person I quoted was applying was similar to the principle I'm trying to apply, so even if they're factually wrong on something, it doesn't matter, that's just detail, not the point.

Your tutorials are very helpful though, even if we don't see eye to eye on what the ideal tool is for a programmer to use :) 

And cybrid... thanks for that link... I guess I'm just going to resign myself to learning to use the auto tools and the rest of the gnu system, since that looks like the only way I can get my project finished... but that doesn't mean I'm happy about it! :lolflag:

---

### Post by j_g on 2007-02-25
Ok, I just have to say this. You Linux programmers desperately need to use some Microsoft development tools to see what an IDE is all about. If all you know is Linux IDEs, then you don't know a good IDE. I've written and debugged... well, I can't even tell you how many Windows programs. Suffice it to say that I've used MS dev tools just about every day for many years. And yet, I cannot even tell what the linker flag is to include debugging info. I think that there are a few of them, and they all begin with -g or -G. Whatever. So given that I've been debugging Windows software for years, how is it that I don't know what that linker flag is? I never needed to know. It's irrelevant. I simply select "Debug build" rather than "Release build" from the combobox labeled "Target". That's it.

And that's just one example of how I don't need to clog my brain with minute, trivial tool details when using MS tools. I don't frankly know *any* of the compiler and linker flags. Never need to. Visual Studio creates the makefile directly, using the info I supply via the IDE. No, we do not just "type into a text box" the same thing that we'd type on the command line when directly running the compiler/linker. If that's how someone thinks MS IDEs work, then he's never used one.

But, that isn't the case with Linux IDEs that use that autotools crap. It is the autotools that are generating the makefile, with all the compiler/linker flags, not the IDE. And that's why Anjuta doesn't have a handy combobox where you select "Debug build" or "Release build". Anjuta can't do anything with that info, because the autotools write the makefile, not Anjuta.

The GNU autotools are unusable. Even someone who doesn't want to use an IDE to develop for Linux should still not use these "tools". He should hand-write a very simple, basic make file like I describe in my first post in this thread. Avoid any IDE that uses the autotools. It's more trouble than it's worth, and it sure as hell isn't anywhere near the quality of MS tools for that reason alone.

There are things that MS does really well, and making dev tools is definitely one of them. They know how to do it right. What I've seen on Linux is numerous examples of how not to do it right.

P.S. I don't recommend DDD, for reasons I mentioned in a previous post. I'd recommend using Kdgb instead. It's of course a graphical frontend to gdb. Even though it is written using QT libs, you can run it under a Gnome desktop, and debug non-QT (ie, X Windows, Motif, GDK+, etc) apps with it. It's not just to debug QT apps.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> Ok, I just have to say this. You Linux programmers desperately need to use some Microsoft development tools


already tried that; didn't like it (edit: but i realize that this just might be me and that there are linux-developers out there who want this ...)


> **j_g]
I never needed to know. It's irrelevant. I simply select "Debug build" rather than "Release build" from the combobox labeled "Target". That's it.
[/quote]

ok, compare it with changing this..
```
env = debug
```
..to this..
```
env = release
```

..what's the difference? you need to know something in both cases .. i move my cursor in the single file that controls the build-process of my whole project(#1), press ctrl-backspace and type in "release" then press F5 and the entire project is instantly recompiled in "release mode"


[quote=j_g]
No, we do not just "type into a text box" the same thing that we'd type on the command line when directly running the compiler/linker. 
[/quote]
technically you are finding the key of a key/value-pair amongst graphical menus then typing in the value-part .. while i, or some build-tool - supply key/value-pairs as text:

```
-l mylib
```
..i can imagine this graphically using a GUI -- what's the real difference? you need to know both the key (-l) and the value (mylib) in both cases


[quote=j_g]
But, that isn't the case with Linux IDEs that use that autotools crap. It is the autotools that are generating the makefile, with all the compiler/linker flags, not the IDE.
[/quote]

stop using those tools and those IDEs then .. find something that works for you -- it's not hard


[quote=j_g]
Even someone who doesn't want to use an IDE to develop for Linux should still not use these "tools". He should hand-write a very simple, basic make file like I describe in my first post in this thread.
[/quote]

no-no, stop saying this! .. he should be using something like scons or possibly cmake (i have not tried cmake yet) .. 

using make is not a matter of taste or simple preferences said:**
> 
P.S. I don't recommend DDD, for reasons I mentioned in a previous post. 

what reasons? i didn't see any besides the "it looks old"-reason and that should not be what ultimately judge a tool like this .. but seeing as i do not know much about the front-end you mention i do not know if KDGB might be "better" than DDD - but i haven't seen you mention anything relevant yet .. but really; if you're happy with KDBG and feel that you can recommend it that is fine .. heh :)

edit2: here's another interface i've found good/useful: [http://sourceware.org/insight/](http://sourceware.org/insight/) (and yes, it too is using an arcane UI-toolkit ..)


#1: you might say i view the file as a graphical menu or interface ..

---

### Post by j_g on 2007-02-25
>  i move my cursor in the single file that controls the build-process of my whole project(#1), press ctrl-backspace and type in "release" then press F5 and the entire project is instantly recompiled in "release mode".

you are... typing in the value-part

Um no, that's not how a combobox works under Windows. I simply click on the desired item from the toolbar. There is no separate file (that I need to be aware of) that controls the build-process, no need to press ctrl-backspace, and no need to type in anything. In fact, I can see whether I'm bulding a debug or release just by glancing at the toolbar combobox.

Are you _sure_ that you've used MS dev tools? Which?

> i didn't see any besides the "it looks old"-reason

Read my messages more carefully. I mentioned erratic response to the mouse, an unreadable font, an inability to set/clear a breakpoint by clicking on the desired source line, and noted that it couldn't load/debug executables that Kdbg had no trouble with.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> 
Um no, that's not how a combobox works under Windows. I simply click on the desired item from the toolbar.

no, you are typing in the filenames of the libraries you want to link with .. that's the typing .. no real difference

..while the combo-box switch is made by referring to another variable `release' instead of `debug' .. it's easy ..

..i actually do not understand how anyone can have serious problems with understanding or using something as simple like this at all .. what's currently stopping you?


[quote=j_g]
There is no separate file (that I need to be aware of) that controls the build-process,
[/quote]
the things you need to be aware of are just in different places .. you still need to be aware of the same amount of stuff


edit:
[quote=j_g]
an inability to set/clear a breakpoint by clicking on the desired source line
[/quote]
try right-clicking (on whitespace) ... or double-clicking (on the left of a code-line) .. this stuff is explained well in the manual

this discussion is getting quite boring and pointless .. i see no mention of real, _actual_ problems

---

### Post by j_g on 2007-02-25
> no, you are typing in the filenames of the libraries you want to link with

Incorrect. Now I _know_ that you haven't used MS IDE's (and why you didn't answer my question put to you about that).

> i actually do not understand how anyone can have serious problems with understanding or using something as simple like this at all

I have no problems using MS IDEs. Your assumption is incorrect.

> you still need to be aware of the same amount of stuff

Incorrect again. I've already given a particular example to illustrate my point. Your assertation is unfounded and disproven.

> try right-clicking (on whitespace) ... or double-clicking (on the left of a code-line)

Didn't work. But then, the program seemed to exhibit a lot of erratic behavior to the mouse. Sometimes clicking on something would work, and sometimes it wouldn't. I didn't experiment with the program a lot because I found more than enough reasons straight off for preferring Kdbg, most notably, it's failure to load several of the exes that I had created.

> i see no mention of real, _actual_ problems

Yes, I've noticed that. But that's not my fault.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> Incorrect. Now I _know_ that you haven't used MS IDE's (and why you didn't answer my question put to you about that).


oh .. so you are selecting what libraries to link with from a combo-box with pre-filled in entries? how does the IDE know what libraries to show in that combo-box? .. doesn't sound very reliable and consistent at all

i have used VC++ 5.0 to 7.0

in the end no matter what you're the one losing out .. i can get a project up and running in no time using this .. the only problem you're having is your inability to learn new things

edit: btw .. you're starting to sound exactly like the troll `lordhunter317'

---

### Post by j_g on 2007-02-25
> so you are selecting what libraries to link with from a combo-box with pre-filled in entries? 

i have used VC++ 5.0 to 7.0

No, you absolutely have _not_ used any version of VC++ 5.0 to 7.0. If you had, you'd already know that your description above is totally incorrect. _Totally_ incorrect.

> the only problem you're having

I don't have any reason to believe that your assumptions about what I know, what I'm doing, and who I supposedly am, are any more accurate than your assumptions about MS dev tools.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> No, you absolutely have _not_ used any version of VC++ 5.0 to 7.0. If you had, you'd already know that your description above is totally incorrect. _Totally_ incorrect.

then tell me how it works

edit: this looks familiar: [http://www.coin3d.org/windows/tutorial/msvcsettings](http://www.coin3d.org/windows/tutorial/msvcsettings)

[quote=j_g]
I don't have any reason to believe that your assumptions about what I know, what I'm doing, and who I supposedly am, are any more accurate than your assumptions about MS dev tools.[/QUOTE]

oh shut up Adam .. you're just as boring as always and you're not getting anywhere

---

### Post by Wybiral on 2007-02-25
There are some subjects which programmers seem to hold sacred. Two of the greatest amongst these subjects are: language of choice and editor of choice.

But why... Why? Can't programmers discuss things things happily? And why are there always personal attacks instead of simple information.

Why does it always turn into a war?

As far as "IDE versus command line" (the title of this post) I would say command line for myself. Thats all you need. I'm sure some people find IDE's helpful, but you really don't NEED them. And my computer isn't top-of-the-line, plus I get distracted by esoteric buttons and menu's, so I stay away from IDE's. I like to keep it plain and simple... Text editor + command line. A makefile if I need to compile multiple object files over and over.

---

### Post by j_g on 2007-02-25
> then tell me how it works

Why don't you already know how it works??? You claim that you've used three versions of Microsoft Visual C++. How could you have possibly created even one executable if you don't know how the linker settings are setup?

This is a rhetorical question. Of course, the answer is because you have not used the products you claim to have used. You don't know how it works.

P.S. One of the versions you've claimed to use doesn't even exist. There is no Visual C++ 7.0. After 6.0, Microsoft switched to NET development, and released Visual .NET 2002 (which supports C++ development, but it's not "Visual C++ 7.0". I'm sure that's an easy mistake to make given that you've never really used any version of VC++, and your alleged claim is based upon third party "information", some of which is probably also misrepresented).

> this looks familiar

I do not see anything on that page that substantiates your claim that you've used three versions of VC++.

Since when does reading a web page that describes a product qualify you as having, and claiming, personal experience with that product?

I think it's obvious now that your discussion of the merits of IDEs suffers from a total lack of experience with, and familiarity with, the most widely used IDEs in the world. I had suspected as much given some of the statements you've made, but now, my suspicion is confirmed.

How about if we swap URLs? I'll give you a URL where you can download dozens of WIN32 software, to which I own copyright, and have written using VC++. You do the same so we can see evidence that you actually know something about these tools based upon your alleged personal use. Let's see a little credibility here.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> Why don't you already know how it works??? You claim that you've used three versions of Microsoft Visual C++. How could you have possibly created even one executable if you don't know how the linker settings are setup?

the reason i'm asking is not this obvious

[quote=j_g]
P.S. One of the versions you've claimed to use doesn't even exist. There is no Visual C++ 7.0. After 6.0, Microsoft switched to NET development, and released Visual .NET 2002 (which supports C++ development, but it's not "Visual C++ 7.0". I'm sure that's an easy 
[/quote]
nah, it is known under both names

[quote=j_g]
I do not see anything on that page that substantiates your claim that you've used three versions of VC++.
[/quote]
that wasn't the point either

---

### Post by j_g on 2007-02-25
> Why? Can't programmers discuss things things happily?

I'm perfectly happy allowing for dissension. In fact, I very, very much believe in dissension. I know that there are people who think command line invocation of tools is great, and it suits their purposes fine. Great. But there are other people who find _good_ IDEs (such as MS dev tools) a godsend to productivity and ease of use.

I'm not wild about people who have little or no experience in IDEs attempting to insist that there is no difference in productivity nor ease of use between the two. This is an ignorant point of view. But in a world where dissension is allowed, it is an _acceptable_ point of view.

But where I draw the line is when someone outright misrepresents himself, and his experience, in order to try to lend credibility to his views. I had suspected that lnostdal had far too little experience with IDEs to comment credibly on their advantages. And again, that doesn't disqualify him from commenting (although folks should accordingly take into consideration his lack of personal experience when evaluating his comments). But frankly, he has flat out misrepresented his personal knowledge of MS dev tools. He doesn't have the experience he claims to have. He doesn't have the knowledge of such he claims to have. His opinions about such exclude any working knowledge of these very well-respected, widely utilized tools, and yet, he has claimed otherwise. That's dishonest. I consider it unacceptable. You don't tell someone you've used/evaluated something if you haven't, and then go on to make assertations based upon your alleged personal knowledge. Dishonesty is not equivalent to legitimate dissension.

> command line for myself. Thats all you need. I'm sure some people find IDE's helpful, but you really don't NEED them.

I think that most all people acknowledge this (although "need" is subjective. If someone who is considering Linux dev finds the dev tools to be too frustrating, confusing, unstable, etc, to work with, he may rightfully decide that it's not worth his time to develop for Linux. In that case, I'd say that he "needs" better dev tools, which may "need" to be an IDE for him if he refuses to have to learn what various compiler/linker switches do what).

But the thread I started here was not about "need" per se. It was about the advantages of an IDE. I know that there are people who want to turn the discussion into one about "technical need", but that is only because they lack the personal experience with IDEs to frame their discussion in any other context. (ie, The lack the experience to make effective points about the advantages of IDEs. After all, IDEs are simply things that they don't use, and nothing more than that). If those folks want to pipe up and express opinions, that is their right (just as it's my right to discount views coming from people who don't have personal experience with what they're attempting to discuss). But I draw the line at outright misrepresentation.

---

### Post by j_g on 2007-02-25
> the reason i'm asking is not this obvious

There is no reason to be asking about something that you claim to already know.

> it is known under both names

Please point out to me where you see "Microsoft Visual C++ 7.0" listed on Microsoft's official page of VC versions.

[http://msdn2.microsoft.com/en-us/visualc/aa336419.aspx](http://msdn2.microsoft.com/en-us/visualc/aa336419.aspx)

If it exists, shouldn't it be right there between "Visual C++ 6.0" and "Visual C++ .NET 2002"?

Oh wait, I get it. It is known to _you_ because that's what you heard from the same people who told you everything else that you know about MS dev tools.

---

### Post by lnostdal on 2007-02-25
> **j_g said:**
> 
There is no reason to be asking about something that you claim to already know.

yes there is -- i'm asking to see how you'd explain it

[quote=j_g]
Please point out to me where you see "Microsoft Visual C++ 7.0" listed on Microsoft's official page of VC versions.

[http://msdn2.microsoft.com/en-us/visualc/aa336419.aspx](http://msdn2.microsoft.com/en-us/visualc/aa336419.aspx)

If it exists, shouldn't it be right there between "Visual C++ 6.0" and "Visual C++ .NET 2002"?
[/QUOTE]
you know perfectly well that it is known as 7.0 and further 7.1 for the .NET 2003 version

---

### Post by cybrid on 2007-02-25
Oh cmo'n you two, this is getting odd and tottaly out of context, this discussion is pointless and has no sense other than just arguing, please stop it.

Oh, and hi Wybiral, I didn't know you were in ubuntuforums too ;). Haven't gone through tweaking gp3d lately, univ is consuming most of my spare time.

---

### Post by psychicist on 2007-02-28
In my search for C/C++ programming information I have read this thread over the past days and I don't seem to understand what the problem is.

Someone is too attached to his Windows IDE and some other person is a multi-platform programmer who presumably feels at home in either environment.

I have used both MS Visual Studio 6.0 and 7.0 (aka .Net) but don't see them as the holy grail in programming, particularly because of their platform dependence. Nowadays I'd prefer something like mono for C#. Not to mention the horror called MFC programming.

For some more insights read this: [Does Visual Studio Rot the Mind?]("http://charlespetzold.com/etc/DoesVisualStudioRotTheMind.html")

Over the past weeks I have started to use Netbeans for Java programming (after using it when it was called Forte4j a few years ago on Windows) and I like it for debugging purposes, even though I prefer just Kate and command line scripts for compiling and testing.

I have installed the C/C++ pack as well and am starting to learn to program Linux programs. Even though the IDE compiles source files I haven't managed to get it to generate executables.

After that I tried KDevelop. Having tried to learn autotools a few times before and not having had enough patience to persevere I decided to create test C/C++ cmake projects.

The projects presumably build but I haven't got them to output anything meaningful like an executable. I'll have to look into that when time permits. For now I just call an [scons]("http://www.scons.org") command line script that builds the desired executables.

The documentation for it is pretty good and you can do away with archaic make and its makefiles.

If there is a way to integrate scons into either IDE I'd appreciate it if someone let me know how. But it is not necessary to reach the ultimate goal of getting your executable/library.

BTW I am not an Ubuntu/Kubuntu user. I have installed it a couple of times for friends and relatives, but I prefer the stability and simplicity of Slackware. I have customised it to be the ultimate development workstation.

But this thread is kind of interesting. That's why I've registered.

---

### Post by lnostdal on 2007-02-28
> If there is a way to integrate scons into either IDE I'd appreciate it if someone let me know how.
the KDevelop FAQ mentions creating a simple makefile that calls scons .. i haven't tried it though

[http://www.kdevelop.org/mediawiki/index.php/FAQ#How_can_I_set_up_a_project_with_SCons.3F](http://www.kdevelop.org/mediawiki/index.php/FAQ#How_can_I_set_up_a_project_with_SCons.3F)

if i'm right it should still parse the GCC messages and enable you to navigate directly to the file/line each message refers to

---

### Post by j_g on 2007-02-28
> MS Visual Studio 6.0 and 7.0 (aka .Net) but don't see them as the holy grail in programming, particularly because of their platform dependence.

Nobody is advocating using MS Visual C++ for anything other than Windows programming. What is being discussed to the quality, and completeness, of the tools. VC++ takes you from writing the source code, all the way to packaging your result as an installable file, all without needing to hand-edit make/build files, look up obtuse compiler/linker switches, struggling to piece together a working dev system from tools that don't integrate well, nor deal with other nuisances like Linux dev tools do.

> Not to mention the horror called MFC programming.

I use Visual C++ nearly every day. I never use MFC. The two are not dependent at all.

> Having tried to learn autotools a few times before and not having had enough patience to persevere I decided to create test C/C++ cmake projects.

The projects presumably build but I haven't got them to output anything meaningful like an executable.

Well see, these are the sort of "I tried these tools and I can't get them to work" stories you constantly hear from people trying to develop Linux software. The problem is not so much that people are incapable of learning how to program as it is that the tools are so unintuitive, convoluted, and illogical. When a programmer is having more trouble getting his dev tools to work than he is having trouble actually coding, then there's something very wrong with the tools.

---

### Post by Wybiral on 2007-02-28
I don't get it... I have yet to be stumped or perplexed using makefiles and gcc. Write, compile, assemble, link... End of story. I have a pretty good understanding of how the compiler/assembler/linker work, so I usually know what the error messages mean and how to treat them. Personally, I think that's part of programming (or at least software design)... You should at least understand what is going on.

Unfortunately I've only developed for Windows and Linux, and never at the same time... So my build system hasn't had to be super portable or anything... Maybe that's why I have such a hard time understanding. But, since GCC is available for Windows, if you understand the processes involved, I don't see why you would have so many problems. Learn the flags, learn the processes and you don't have to worry if your IDE or build system are up to par... You can work around that.

---

### Post by nickoli_02 on 2007-03-01
Just thought I'd put in my personal opinion about IDE/command line programming... 

For beginners who are just starting to learn the basics of programming and/or projects small in size, there really is no need for an IDE environment, and in fact I think you can learn more about how compiling works when using just a simple text editor and a command line compiler. For a beginner programmer, it's too easy for them to get caught up with the intricacies of the IDE environment instead of focusing on their code. Now, once the beginner has learned enough of the language and is working on larger sized projects, then it would be time to start using an IDE. Even then, I believe in the philosophy that you should understand how the tools work before you use them, so it's useful to write your own makefiles to gain at least a basic understanding of what their purpose is before you let the more powerful tools take over and do all the work for you. 

Personally, I've never had the need to use an IDE, and I won't use one unless I have to. However, my programming experience is limited to university courses, I haven't worked on any large projects, and I probably never will :)

---

### Post by Wybiral on 2007-03-01
> **nickoli_02 said:**
> Just thought I'd put in my personal opinion about IDE/command line programming... 

For beginners who are just starting to learn the basics of programming and/or projects small in size, there really is no need for an IDE environment, and in fact I think you can learn more about how compiling works when using just a simple text editor and a command line compiler. For a beginner programmer, it's too easy for them to get caught up with the intricacies of the IDE environment instead of focusing on their code. Now, once the beginner has learned enough of the language and is working on larger sized projects, then it would be time to start using an IDE. Even then, I believe in the philosophy that you should understand how the tools work before you use them, so it's useful to write your own makefiles to gain at least a basic understanding of what their purpose is before you let the more powerful tools take over and do all the work for you. 

Personally, I've never had the need to use an IDE, and I won't use one unless I have to. However, my programming experience is limited to university courses, I haven't worked on any large projects, and I probably never will :)

Amen... That's exactly how I feel... Learning a language AND and IDE is actually learning two things... Learn one to begin with, and that is the language. Worry about an IDE later, IF you even need it.

---

### Post by j_g on 2007-03-01
> I have yet to be stumped or perplexed using makefiles and gcc.

Are you arguing with a strawman?

Because I'm not talking about the same things you are.

> You should at least understand what is going on.

You're arguing with a strawman again. I do know what is going on.

> since GCC is available for Windows

Why on earth would I use GCC for Windows??? I already have MS dev tools.

---

### Post by yaaarrrgg on 2007-03-01
Personally, I started out with Microsoft Visual Studio (for Windows), but gradually found I prefer the command line for most things now.  I suppose this is really more of a cultural difference between Windows and Linux programming.   Although, I think it's a valid complain if there's not good GUI IDE tools on Linux.

I don't think one approach is "better" than the other, but some of the pros and cons are:

Visual Studio pros:

Intellisense, integrated debugging, and WYSYWIG design screens are all nicely intergrated and make life easier.  I'm fairly impressed with Visual Studio in this respect... I had little interest in learning C# for example, but it was so easy to use, I felt I could actually do the job without investing much thought at all. :)  In other words, it spoon-feeds the programmer, and it's kinda nice (especially if you're not all that interested in the platform).  It almost thinks for you! :)

Visual Studio cons:

After spending more time on Linux, what frustrated me most about Visual Studio is that the actual text editor is fairly underpowered, and it's hard to extend.  If I have to make any kind of repetive or complex edit, I'll usually fire up a "real" text editor :) like vim, or write a quick vim macro.  There is a vim plugin for VS (I've seen) but haven't purchased it. 

The second major problem with GUI IDE's is that they tend to abstract the prgrammer away from the actual problem, so that all that's really learned is the IDE.  I'm amazed talking to Windows programmers, many have no idea what's actually happening when they click the magic buttons. 

The third problem is it's hard to automate Visual Studio tools.  Sure a button is easier at the beginning, but my comand line build scripts can do really anything (for example, install software on remote machines).  How do you automate a series of button clicks?  It's an interface that designed to be easy more than powerful.

CLI IDE's pros:

What I've found is that the command line tools are very reliable, fast, tuned to one particular task, can be be combined in a nearly infinite number of ways, and do the job well.  While the GUI's look better, they are often buggier, slower, or simply don't do what I want.  Visual Studia tools sometime kinda feel like a toy at times.  

CLI IDE's cons:

These require a much larger investment of learning up front.  Finding, and learning the tools and switches, configuring build scripts can take some time   Plus, there's usually a large group loosely of tools, so gettingn everything to work together can be frustrating, especially for someone learning a new language and platform.   I thought Linux in general was needlessly overcomplicated and disorganised when I first saw it...

IMO, the closest thing to Visual Studio for Linux is NetBeans (maybe), although this is for Java programming.  I'm not sure there is as much interest currently in writing better C++ IDE's, since I'm guessing most Linux C++ programmers aren't that unhappy with the command line tools.

---

### Post by Wybiral on 2007-03-01
> **j_g said:**
> Are you arguing with a strawman?

Because I'm not talking about the same things you are.



You're arguing with a strawman again. I do know what is going on.



Why on earth would I use GCC for Windows??? I already have MS dev tools.

Well, I'm glad you took that so personal (it makes me feel special) but I wasn't talking about you at all or "arguing". I just constantly see people say that makefiles and command line build systems are too difficult or faulty to use, so people use IDE's. I just disagree.

But, since you mention it... Why use GCC on windows? Because not all MSVC++ is compatible with anything other than MSVC++, so good luck compiling it on Linux.

But, once again... That wasn't about you, so stop taking things so personal... I wasn't "arguing" with you.

---

### Post by j_g on 2007-03-01
> people say that makefiles and command line build systems are too difficult or faulty to use, so people use IDE's. I just disagree.

The discussion, right from the start (because I posted the first message in this thread), was well beyond such a general observation. It has been all about specific implementations. So, you'll have to forgive me for assuming that you were commenting upon the preceding messages rather than talking about something that has no particular relevancy to this thread.

> Why use GCC on windows? Because not all MSVC++ is compatible with anything other than MSVC++, so good luck compiling it on Linux.

But I write real Windows software with a UI interface. Windows endusers en masse do not use command line driven programs. Why would I use GCC to create Windowed apps when I already have MSVC++? It has all of the tools built-in for that, they're well-integrated, and they are among the best tools for creating Win32 apps.

And since Win32 apps don't run natively on Linux, I don't care about Linux support. When I want to write something that runs on Linux, I write a Linux app, using whatever tool makes that  easiest for me there. (Right now, that seems to be Glade and GTK+).

---

### Post by lnostdal on 2007-03-01
> But I write real Windows software with a UI interface.  Windows endusers en masse do not use command line driven programs.

lol? gcc/mingw can produce GUI-applications on Win32 .. gtk+ for instance is portable to Win32

> 
 Why would I use GCC to create Windowed apps when I already have MSVC++?

oh, i can think of several reasons:

* you'd have to make the build-system support msvc also (i think scons has some support for this, but i've never bothered)
* portable libraries, like gtk+ for instance - has better support for gcc and the gnu-toolchain than the MS ones

but let's assume we're not only talking about you, but others in general .. they might not:

* have msvc
* know how to use msvc

..or -- we can turn the whole thing upside down and then have you ask yourself; what if msvc was available on both linux on windows? what would you do? .. well imagine this; for gcc this is already true


> 
And since Win32 apps don't run natively on Linux, I don't care about Linux support. When I want to write something that runs on Linux, I write a Linux app, using whatever tool makes that  easiest for me there. (Right now, that seems to be Glade and GTK+).


oh right -- fine; then write your apps twice

---

### Post by j_g on 2007-03-01
> gcc/mingw can produce GUI-applications on Win32

Theoretical comparisons mean nothing to me. I use MS Dev tools on Windows, rather than the alternatives, because I can more easily and quickly create/debug Win32 software with the former. Why would I therefore choose the latter?

> you'd have to make the build-system support msvc also

I never have to worry about "the build-system" with MS dev tools. They completely manage things from inception to creating the final installable file.

> portable libraries, like gtk+ for instance

I don't use gtk+ on windows. I use, and write, Windows software that takes full advantage of the native UI. I utilize the unparalleled sources of documentation, examples, and tools that are available for such to produce software that runs natively. I write Windows software that Windows users want to use, and in fact, have actually told me that they chose over other, cross-platform alternatives due to a variety of reasons that mostly boil down to "it runs better, easier, and offers me more under my chosen OS".

> what if msvc was available on both linux on windows? what would you do?

I would use the Linux version only if it was better than other Linux offerings, and if it didn't give me headaches like, for example, Anjuta does. I don't choose tools simply because they are available, but rather, evaluate them based upon individual merit.

> write your apps twice

I don't write my apps twice. I write Windows apps, and I write Linux apps. I don't consider them to be the same, because the operating system is not the same. But that's also because I don't consider a clunky, flakey, less flexible, less intuitive "cross-platform" aberation to be the same thing as a native app. Of course, you've gone completely off-topic, because this thread is not supposed to be about cross-platform development. It appears that advocates of the current state of Linux dev tools have run out of steam in defending the lack of usability of many of those tools. I'm not surprised.

---

### Post by lnostdal on 2007-03-01
> **j_g said:**
> Theoretical comparisons mean nothing to me. I use MS Dev tools on Windows, rather than the alternatives, because I can more easily and quickly create/debug Win32 software with the former. Why would I therefore choose the latter?

uhm, i dunno .. i mean; what are we talking about again?


> 
I never have to worry about "the build-system" with MS dev tools. They completely manage things from inception to creating the final installable file.

no, you can't just dump a bunch of source-files in a directory and have the dev-tools automagically figure out that a.cpp and b.cpp should link to a library while app.cpp and some-class.cpp should link to an application that uses the previous library .. or whatever

you have to define the build-process in on way or another

> 
I don't use gtk+ on windows.

fine, but do not say that gcc/mingw can't create GUIs on Windows .. that's false  

oh, and you can also program "native" win32 guis using gcc/mingw .. not that i'd _ever_ do such a thing though; in the same way i'd _never_ develop a "native" xlib app either

> 
 I utilize the unparalleled sources of documentation, examples, and tools that are available for such to produce software that runs natively.

omg .. bring in the FUD next -- get Balmer; quick!


> Of course, you've gone completely off-topic, because this thread is not supposed to be about cross-platform development.

you're the one talking about how gcc/mingw could not create GUIs on Win32 .. feel free to take the discussion anywhere you want though; doesn't matter to me as what i do works in all cases:

* only linux
* only win32
* or cross-platform; both linux and win32

> 
 It appears that advocates of the current state of Linux dev tools have run out of steam in defending the lack of usability of many of those tools.

i wouldn't worry about that

---

### Post by Wybiral on 2007-03-01
I don't see why you would want to use native windows api when there are cross platform alternatives. Especially since you're on a Linux forum right now...

Programs I used to use in Windows that I still use in Linux:
GIMP, Blender, Audacity, Google Earth, Firefox... To name a few.

I don't think these programs look bad or run with any less quality in either Windows or Linux.

Do what you want, if you want to write Windows specific code, fine.

But why would you want to limit your user base to one OS? Especially if you're a Linux user yourself.

The only reason I could think of is that it's part of your job or clients specification. But if you're developing it yourself, why not make it portable?

---

### Post by j_g on 2007-03-01
> do not say that gcc/mingw can't create GUIs on Windows

I never said that. Your accusation is specious.  

> you're the one talking about how gcc/mingw could not create GUIs on Win32

Again, your accusation is specious. Do not attribute alleged quotes to me that were never made by me.

---

### Post by lnostdal on 2007-03-01
> **j_g said:**
> 
[quote=lnostdal]do not say that gcc/mingw can't create GUIs on Windows
I never said that.
[/quote]
right, here is the quote, with context:

[quote=j_g]
[quote=Wybiral]
Why use GCC on windows? Because not all MSVC++ is compatible with anything other than MSVC++, so good luck compiling it on Linux.
[/quote]
But I write real Windows software with a UI interface. Windows endusers en masse do not use command line driven programs. 
[/quote]

again: you can create GUI applications on Windows using GCC, GTK+, Glade (the new version is nice) .. or QT, QT Designer .. etc.

---

### Post by j_g on 2007-03-01
> here is the quote, with context

And nowhere in the quote do I say "gcc/mingw can't create GUIs on Windows".

Your dishonesty knows no bounds apparently. Stop attributing quotes that were never made.

---

### Post by Wybiral on 2007-03-01
What did you mean by...

> But I write real Windows software with a UI interface. Windows endusers en masse do not use command line driven programs. 

Anyway?

What does the command line have to do with GCC?

---

### Post by lnostdal on 2007-03-01
> **j_g said:**
> And nowhere in the quote do I say "gcc/mingw can't create GUIs on Windows".

yes you did .. here, again:

[quote=j_g]
But I write real Windows software with a UI interface. Windows endusers en masse do not use command line driven programs.
[/quote]

(thus, ofc - implying that this is not possible using gcc) 

do you want to waste any more space/time on this?

---

### Post by j_g on 2007-03-01
> What does the command line have to do with GCC?

It means that gcc by itself doesn't have any features that facilitate Win32 Windowed app development, which is what I make. Visual C++ ships with a very complete Windowed app wizard and "dialog editor" that is fully integrated into the IDE, a full set of Win32 libs and includes for Windowed development, online docs for such in the IDE, and all the many other amenities I get with VC++. I get all of this just by popping my Visual C++ CDROM in the drive. It works splendidly.

Given that I make Win32 Windowed apps, and already have a tool that works splendidly, why would I use gcc? You're the one who said:

> Since GCC is available for Windows, if you understand the processes involved, I don't see why you would have so many problems.

There's an implicit, and incorrect, assumption that Windows developers would chose gcc just because it's available for Windows. That's why I challenged that assumption with my above question.

(Actually, I think a big part of the problem is that Linux folks who twiddle around with other peoples' code as a hobby, and just run gcc from a command line, or use variations on the autotools paradigm such as Scons, always assume that no one needs anything beyond what they're using for their exceedingly simple needs. So if anyone even has the nerve to criticize the quality of Linux dev tools, for example, he needs to be told that whatever he finds lacking isn't even needed at all, by anyone. And when I say "anyone", I do mean it. These Linux fanboys are so fervid that they'll even argue that Windows developers don't need anything but that limited selection of Linux dev tools! Talk about advocacy gone astray!)

---

### Post by j_g on 2007-03-01
> thus implying that this is not possible using gcc

I see the problem. Your interpretation is incorrect and illogical. My statement is about what _I_ make, not about what gcc or some other tool makes.

Now that your misinterpretation has been corrected, please stop attributing quotes that I never made.

---

### Post by j_g on 2007-03-01
> no, you can't just dump a bunch of source-files in a directory and have the dev-tools automagically figure out that a.cpp and b.cpp should link to a library while app.cpp and some-class.cpp should link to an application that uses the previous library .. or whatever

you have to define the build-process in on way or another

Now see, if you had some actual experience using MS dev tools (rather than your unfounded claim that you have), you'd know how this is handled using those tools, and finally understand why they are, and have been, the most widely used IDEs the world over.

It's difficult to argue something with someone who clearly has not had personal experience with the tools he is discussing.

P.S. MS is offering free downloads of .NET dev tools. Go get them, and use them, so you can finally see what other people are talking about.

---

### Post by Wybiral on 2007-03-01
> **j_g said:**
> Given that I make Win32 Windowed apps, and already have a tool that works splendidly, why would I use gcc?

Because you can make win32 apps in gcc with MinGW.

And since GCC is available for more operating systems then VC++, your code will be much more portable.

But I see the difference is that you don't care about portability and would rather settle on strictly windows specific programs... So, in that case you don't have a use for GCC.

But if you ever do have to port one of your programs to mac or linux from VC++ you are going to have much more trouble than if you used gcc and a portable windowing library.

---

### Post by lnostdal on 2007-03-01
> **j_g said:**
> 
[quote=lnostdal]
no, you can't just dump a bunch of source-files in a directory and have the dev-tools automagically figure out that a.cpp and b.cpp should link to a library while app.cpp and some-class.cpp should link to an application that uses the previous library .. or whatever

you have to define the build-process in on way or another

this is handled **(automatically .. as if the IDE by magic know what you intend to do)** using those tools
[/quote]

stop lying .. instead go get Balmer; throw some chairs or something

edit: added the stuff in bold

edit2: do you really need this to get any more stupid than it already is? .. i mean; what should we do about these lies? -- get over it, ok?

---

### Post by j_g on 2007-03-01
> Because you can make win32 apps in gcc with MinGW.

But I already have a tool that does that splendidly, and came all integrated quite nicely. (I will say though that I once took a took the "GUI builder" that came with Ming, and loaded it into a disassembler to see what it's doing. This guy didn't even bother to error check the returns from his malloc calls to see if they return NULL. And that was just the tip of the iceberg in the number of bugs and dubious design flaws I saw. Shiver. I'll stick to the GUI builder in MS' IDEs, thanks).

> your code will be much more portable.

I don't want to write Win32 software that looks and feels like it was designed for Linux, and vice versa. I want people to prefer my stuff over such software.

> you don't care about portability and would rather settle on strictly windows specific programs.

Or Linux specific programs. Or rather, Linux specific programs that target distros that support widespread standards in installation of software, file hierarchy, etc.

> if you ever do have to port one of your programs to mac or linux from VC++ you are going to have much more trouble.

I'm not having that much trouble. I'm having a lot more trouble getting the Linux dev tools to do what I want, than I'm having writing the actual code.

---

### Post by Kindred on 2007-03-01
I would suggest to anyone, if you don't like the current approach, do something to help fix it.  Whining about how someone else hasn't done all the work to implement the tools you want seems totally the wrong way to go about doing anything productive in this case.

---

### Post by j_g on 2007-03-01
> f you don't like the current approach, do something to help fix it.

That's what I've always done. I've put on my "to do" list, "make a useable C IDE for Ubuntu/Gnome". When I'll get to it, I don't know, because I've got several other things on the to do list that take priority. But definitely, this is something that desperately needs to be done. And it needs to be done by people who don't think that autotools and that paradigm are the right approach.

Nevertheless, this thread was started for the benefit of newbie programmers who are just now experiencing the pain of autotools and "IDEs" based upon such. The fact that no one has a solution to offer them is unfortunate, but doesn't render moot the need to advise them to steer clear of tools that will likely be more a hindrance than a help to them, especially if they've come from the Windows world and are expecting Linux dev tools to be as intuitive, simple, and well-integrated as Windows counterparts.

---

### Post by dcraven on 2007-03-02
> **Kindred said:**
> I would suggest to anyone, if you don't like the current approach, do something to help fix it.  Whining about how someone else hasn't done all the work to implement the tools you want seems totally the wrong way to go about doing anything productive in this case.

In my ever-so humble opinion, this is the best piece of advice given in this thread yet. We all know the philosophy of development around these parts. If you have an itch, write something that scratches it. It sounds as though some folks here have a very clear idea what they'd like to see in a set of development tools. That's a good start to modifying an existing project, or even spawning a new one.

Personally, I use autotools for all of my code. It's a bit of a pain, but it is "the generally accepted way" and it does work. I agree that they are a touch cryptic for the newcomer though.

I came from Windows too (I suppose most of us did), and one of the first things I looked for was an IDE like I was used to. That and a graphical FTP program :).You could say that I've sort of de-evolved now though because you would have to pry Vim and xterms out of my cold, dead hands if you wanted to take them away from me. I'm not exactly sure when or how that happened, but I haven't given any of these IDEs a second thought since sometime in 2002. Even my FTP program is command line only now (FTP seems to be a thing of the past these days anyways).

Now I'm not suggesting that people toss their fancy IDEs out the window and fire up an xterm and Vim like a real man. I suggest you use what works for you and you feel most comfortable with. I *am* suggesting, however, that I feel the tools that are available on platforms outside of Windows are quite usable, and do the job well (admittedly after a sometimes steep learning curve.).

I wish you and those who feel the same as you the best of luck with your new project. Just keep in mind that other developers may not share the same ideals as you do, and that they may find the available tools equally productive if not more so, than their GUI counterparts on other platforms. Arguing about which set of tools is best will never end well, if it ever ends at all.

Cheers,
~djc

---

