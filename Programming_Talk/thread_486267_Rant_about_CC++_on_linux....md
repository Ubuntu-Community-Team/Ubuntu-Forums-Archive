---
title: "Rant about C/C++ on linux..."
date: 2007-06-27
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-06-27
Hi all, just a rant more than a query, but does anyone else out there agree with me that compiling C/C++ programs in Linux is getting overly complicated?  

Now, I've got many years programming experience and am a Java certified programmer by trade, however I find myself stymied whenever I try anything with the whole configure, make nonsense.  In fact I can't remember I successfully compiled a 3rd party application from source!

I've just tried to redo a simple C++ program I've made (a couple of source + header files, and a short 1 line command to compile and build it) using Anjuta 1.2.4a to try it out.  Firstly it failed because gtkmm-2.0 was not found (no kidding- 2.4 has been out for a while now), apparently the latest 2.2 fixes this, but sure enough I couldn't compile it.  grrr....

Out of curiousity I checked the empty (non-working) project it created:
34 files and directories in the parent directory
5 symlinked files
12+ configuration files
1 actual (ten line) program file

Now, I am aware this is probably more Glades doing rather than Anjuta, but whatever- I wonder how many budding code-gurus have been put off because of the unnecessary complexity?

I guess I'll be sticking to VI and g++ on the command line

</rant> (thanks for letting me get that off my chest! :P )

---

### Post by xtacocorex on 2007-06-27
That is why you don't use an IDE to compile simple programs; you use a homebrew makefile. 

As for big projects, it is important to have configure scripts to check to make sure libraries are installed.

This is why I'll never use an IDE unless I'm required to.

---

### Post by Paul820 on 2007-06-27
I find it complicated aswell. The first time i turned to linux i used anjuta and tried to build a simple project, the amount of stuff anjuta spits out confused the hell out of me. I didn't have a clue what it all was. Yeah, it put me off using it. Although i am still learning to program C++,  i have gone onto using geany now. Much simpler to use until i am a bit more experienced at programming and i have learnt what it all means. Codeblocks is an IDE i also use but it doesn't use all the dependencies that anjuta puts together, so eventually i am going to have to use something like anjuta. I am starting to enjoy programming more now i'm completely using ubuntu. :D

---

### Post by AlexThomson_NZ on 2007-06-27
Hey cheers Paul820, hadn't heard of geany, but have installed it and had a quick play and it is exactly what I've been looking for!  Talk about a hidden gem :)

---

### Post by sonofusion82 on 2007-06-27
Although I don't do much programmig in linux, I use M$ Visual Studio and have to say it is one of the very few piece of "ok/good" software that M$ makes (definitely not Windows).
For KDE, I have tried KDevelop and I feel pretty at home with it.
For small simple programs, recently i trying python with pyqt or pygtk, they are great! C/C++ is for serious and performance hungry stuffs.

---

### Post by Angry on 2007-06-27
My first forays into programming in Linux (specifically dealing with Anjuta) had pretty much the same outcomes as you describe.  As a result, I turned to gedit and a makefile - which turned out to be boon.

While most people would scoff at the idea of having to learn how to write makefile when all they want to do is compile a simple 'hello world' app, I found the experience relatively painless and easy to pick up.  Granted, my skill level is minimal - but that is enough for my purposes.

Now I am sure people are having great success using Anjuta (or some other such IDE), and more power to them.  But my daily professional life consists of MS Visual Studio, and while it is a more than capable IDE, I find that it is heading into the direction of "Doing Everything for Everyone", resulting in a heavier, more cumbersome beast.  As a result, I am enjoying the "bare-bones' approach to programming.

---

### Post by wkulecz on 2007-06-29
I think the biggest problem, and it applies to win32 programming too, is there are at least three different ways of doing anything with precious little guidance on the advantages/disadvantages of each  (if they are really equivalent, randomly delete all but one in the next release and bring some sanity back to programming!), leading to lots of time wasted in trial and error testing or taking the path of least resistance and using whatever sample programs one can find as a guide, which could be the wrong choice for your project.

For example I'm working on a real time image processing application, but the question is in v4l2 are mmapped transfers or user pointers better?  I ended up doing mmapped as I'm more familar with it, but if my user pointers were mmapped to a file, streaming video to the hard drive might be more efficient (I don't need to do this, I send the results of the analysis to the disk instead).  If you wanted to write a video application, how would you choose?

--wally.

---

### Post by skullmunky on 2007-06-30
the reason why automake/configure/etc is so complicated is that it's designed to take care of any possible scenario - checking for missing libraries, different locations of files, porting and cross-compiling on different platforms, etc.  compiling for just one target, say, win32, is a lot simpler so the build system doesn't have to be as complex and robust.  

i can't tell you much about anjuta, i also mostly just use makefiles unless it's a really big project.  or just use the command line, e.g. 

g++ hello.cpp -o hello `pkg-config gtkmm-2.4 --cflags --libs`

makefile syntax -is- famously cryptic, so another option is something like Jam; i'm also seeing  people use another strategy, which is just to script the build in Python, which is way easier to read :)

---

### Post by lisati on 2007-07-03
Kia ora Alex

Good question







p.s. to the non NZers, "Kia Ora" means "hello"

---

### Post by runningwithscissors on 2007-07-03
I agree that autotools is hideously complicated, but as skullmunky said, it is designed to be able to handle all manner of software builds.

There are alternative and simpler build systems available however, so you needn't rant.

SCons and Rake being two of them.

---

### Post by DrMega on 2007-07-03
I use Visual Studio in my job, and have to say I like it. I remember using text editors and a command line compiler back in the early 90's when I still a trainee, and I liked it, but I prefer a proper IDE.

The way I look at it is like this, if something is going to take away the tedious parts of the job, it leaves me more time and energy to do the actual development. Microsoft have realised this, which is why they've released free cut down versions of most of their most current development tools (eg C# Express).

I've looked at the development tools available for Linux (the ones I could find that is) and while it is not fair to compare free open source tools to very expensive commercial products, I am a little bit disappointed with the apparent lack of good IDEs on Linux.

---

### Post by LaRoza on 2007-07-03
> **DrMega said:**
> I use Visual Studio in my job, and have to say I like it. I remember using text editors and a command line compiler back in the early 90's when I still a trainee, and I liked it, but I prefer a proper IDE.

The way I look at it is like this, if something is going to take away the tedious parts of the job, it leaves me more time and energy to do the actual development. Microsoft have realised this, which is why they've released free cut down versions of most of their most current development tools (eg C# Express).

I've looked at the development tools available for Linux (the ones I could find that is) and while it is not fair to compare free open source tools to very expensive commercial products, I am a little bit disappointed with the apparent lack of good IDEs on Linux.

Make one.

---

### Post by runningwithscissors on 2007-07-03
> **DrMega said:**
> I use Visual Studio in my job, and have to say I like it. I remember using text editors and a command line compiler back in the early 90's when I still a trainee, and I liked it, but I prefer a proper IDE.I used to use Visual Studio at my job too. It's the complete opposite for me. I have to say, I hate it. I remember using IDEs back in the mid-to-late 90s when I was a student and I liked it, but I prefer text editors.

Visual Studio positively crawls. It is so slow. If I open more than 10 files, it just turns nasty. Maybe the terminal server I am using is just overloaded, but it's very unpleasant. Also, it messes with my curly brackets. I can set it to use "block indent", which means it won't care where I put my braces, but as soon as I paste something, the indentation is automatically formatted the wrong way.

> **DrMega said:**
> The way I look at it is like this, if something is going to take away the tedious parts of the job, it leaves me more time and energy to do the actual development. Microsoft have realised this, which is why they've released free cut down versions of most of their most current development tools (eg C# Express).
I'm not saying that IDEs are bad or anything. Just that they have never worked for me. Great for those who like them.

I am sitting here and looking at a small program I wrote over the past week (about 3000 lines or so) in C#, and it was written using EditPlus and compiled at the command prompt. And yes, this is no hobby program. It was written for my job.
And before someone says, "Ah! but IDEs are used for programs much larger than that". Yes, I know. I've written programs much larger than this without an IDE.

> **DrMega said:**
> I've looked at the development tools available for Linux (the ones I could find that is) and while it is not fair to compare free open source tools to very expensive commercial products, I am a little bit disappointed with the apparent lack of good IDEs on Linux.As you can see, I am lucky to be sort of a luddite.

---

### Post by public_void on 2007-07-03
No IDE is perfect, however having used Anjuta and Visual Studio I like parts of each. The debugger in VS is easy to use and pick up, yet powerful when necessary. GDB can be an effort when I what something simple, although the GUI wrappers for GDB are okay. The VS Intellisense is brilliant on non-C/C++ projects, but becomes non-existent on C/C++ projects, and creates huge 17MB files for the project. Anjuta is much more stable than VS, after a 2 hour session VS just crashed, and can become unresponsive. Anjuta's code completion is okay, better than nothing. As for the project files it is a bit crazy with all those files, I'd rather write a makefile.

---

### Post by vambo on 2007-07-03
My tuppence worth is basically, for *nix (not kust Linux) systems learn the in and outs of make. A half decent
makefile all but does away with the need for all those over bloated IDE's. That, and emacs of course ;)

---

### Post by DrMega on 2007-07-03
I quite like Anjuta, but the code completion and intellisense is the main feature I miss. That said, I've only looked at version 1, and I understand v2 is out now.

I agree with all comments about VS being slow. VS.NET 2005 can be a real pain in the rear end. It is feature rich, and I like the intuitive nature of it, but at the same time, it is loaded with bugs.

A long time ago, there was a happy medium in PC land. Borland's turbo C (unless I'm looking back with rose tinted glasses). I seem to remember there being some syntax colour, context sensitive help etc and an interactive debugger, without it being bloated and full of bugs.

In open source land, there is one damned good IDE that I really like, but it is for Windows. SharpDevelop is superb, tons faster that VS, and has most of the features most people would need. MonoDevelop looks similar, but I haven't really given any IDE on Linux much of a chance yet.

---

### Post by AlexThomson_NZ on 2007-07-04
I don't know if anyone here have done any stuff on Delphi for Windows, but I think to date that has been my favourite editor, and would love to see something similar (in C/C++ though) on Linux, ie:
 * not having to use annoying layout containers
 * double-clinking on a widget creates a method for it's default signal, etc. and takes you to it.
 * automatically generated code is hidden (or collapsed)
 * IDE/Glade native & transparent refactoring

Unfortunately, while they keep Glade and the IDE component as seperate entities, I don't think this can happen.  The closest I have seen so far is NetBeans, but the C support seems very half-arsed at this stage.  You would think since so much still needs to be done in Linux, they would try to attract developers with great development tools! (I mean even better than VS which I agree is fantastic...)

---

### Post by AlexThomson_NZ on 2007-07-04
BTW- Has anyone managed to build and try out Anjuta 2 yet?  Any word on when a package is likely to hit the repo's?

---

### Post by rodo-&gt;dave on 2007-07-04
I like Anjuta more and more as I keep using it.  I was using geany for a couple of weeks but now that I got anjuta running I like it.  I also really like monodevelop.

I still use vi for most of my coding though :)

If you haven't read this excellent book (HTML), then I happily recommend it:
[http://developer.gnome.org/doc/GGAD](http://developer.gnome.org/doc/GGAD)

---

### Post by AlexThomson_NZ on 2007-07-04
Thanks for the tip robo->dave!

Surprising few resources on beginning Gnome programming on the net.

The only other one I found was [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) which is what everyone else seems to link to anyway (I swear I can code that Scribble program blind-folded by now! :) )

I am a bit wary of mono/java and even python coding for native apps, because I feel they lose a bit of the "stand-alone"-ness that C and C++ offer (anal I know!), and Java, while I love it, has the dramas with look & feels, classpaths, Java installation, etc. which really make it feel "non-native"- how does Mono compare? (I have never used it before)

---

### Post by rodo-&gt;dave on 2007-07-04
Mono uses GTK for the default gui. So there is a pretty big diff between win/linux gui creation.  
But mono supports system.window.forms (which is what win32 c# uses)... I have successfully ran a c# .net app (no compile) on linux that was written on win32 in visual studio.

There are many more 'ebooks' on the website [http://developer.gnome.org/doc/GGAD](http://developer.gnome.org/doc/GGAD) too... just remove the GGAD :) but I prefer having a real book :)

later.

---

### Post by AlexThomson_NZ on 2007-07-04
Hmmm I'm coming to the conclusion that Gnome development documentation is severly lacking!

I think you can tell a lot about a project's documentation by looking at its FAQ.  Check out Gnome's official developer FAQ: [http://developer.gnome.org/doc/FAQ/html/](http://developer.gnome.org/doc/FAQ/html/) (appalling!)

Looking at many of those links (mainly tutorial links) point to articles in between 5-7 years old (that's a long time in Linux-land!).  You know of any other good tutorial sites for gnome programming?  (even that one points to the one site that I have found).

Yeah I know- this is OSS and I should add documentation myself, but I would prefer to get a good understanding of it before I add too much wrong information to the gnome dev site (although I am making notes as I go)

---

### Post by loell on 2007-07-04
I could always find what i want in **devhelp** , if you ever want gnome development and refference

---

### Post by AlexThomson_NZ on 2007-07-04
Cheers loell,

Am I missing something though- all I see in there are references to things like Evince, Rhythembox, etc. APIs?

Jeez I feel like such a n00b- you wouldn't think I've over 20 years programming experience!

robo->dave hey that online book has more stuff in it than I thought- is actually quite good!

---

### Post by loell on 2007-07-04
yeah, all of those apis are heavily used by gnome, :D

may i ask what you would like to do? any particular project?

---

### Post by AlexThomson_NZ on 2007-07-04
Nah nothing in particular at the moment- just thought I should broaden my horizons a bit, and wanted to try gnome development using C.  I have plenty of C/C++ GUI experience in windows, but all my Linux GUI development has been in Java thus far...

---

### Post by AlexThomson_NZ on 2007-07-05
If anyone's interested, I have just been playing around with glade-3, and rather than using the auto-generated code (it has been removed in glade-3), just using libglade, and a small makefile.  Really starting to get my head around this stuff now...

---

### Post by runningwithscissors on 2007-07-05
I don't know how you get this on Debian, but I've got very good GTK+ documentation installed at /usr/share/gtk-doc. Also, there are a few good examples provided with the library install at /usr/share/gtk-2.0/demo.

I'm sure you can get the same on Debian or Ubuntu.

---

