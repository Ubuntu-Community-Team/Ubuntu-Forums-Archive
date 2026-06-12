---
title: "Seriously... Does anybody use Tcl/Tk?"
date: 2007-01-27
forum: Programming Talk
---

### Post by Vox754 on 2007-01-27
As you know, Tcl/Tk was developed as an aid to link C programs and provide them of a simple graphical interface, especially for UNIX environments.
However, to this day I don't think many people use the language or even care to mention it.
Actually, I hadn't heard of it until a month ago.

I'm telling you this because I'm going to work on an interface to a program that allows us to solve Power Flow problems in transmission lines, already written in C.
I would like to read and discuss your experiences with Tcl/Tk.

And in case you are wondering, no, I'm not going to try to use anything else; for the moment it is going to be only Tcl/Tk. If I have time in the next semester, then I may try other things.

Interestingly, I must add that, even if this is a Linux forum, I'll be using the Windows version of Tcl/Tk, along with the Visual Tcl found around.
Strangely, if you go to [the sticky in this forum]("http://ubuntuforums.org/showthread.php?t=333867") you'll see that the person discussing Tcl says that he has never used Tk, which is odd to me, since apparently Tcl and Tk are always supposed to be used together.
I can't conceive using Tcl alone.

---

### Post by geek_Man on 2007-01-27
I kinda started learning Tkinter (which is Tk for Python) on my Windows box (strangely enough, too). Maybe it was Python, maybe it was Tk, but the overall experience I got from it was just "eh". 
You're going to be using it with C, I'm guessing?

---

### Post by dwblas on 2007-01-27
I use Tkinter, as stated previously it is Tk for Python.  I use it because I like PMW - PythonMetaWidgets.  You might want to see if  you can find some extensions, etc. for c/c++.  Widgets are here to make displays easier and prettier, not so we can reinvent the wheel, so if someone has already done it...  I used qt before Tk, and don't see a whole lot of difference.  You have to define a widget, call back, etc. whatever toolkit you are using.  That is if you write all of the code yourself.  If you want to use one of the programs that generates the code, then you want whichever does what you want.  As for the person who uses TCL only, they probably never learned Tk.  TCL is used in terminal mode, Tk is an Extension of TCL to use a windowing system AFAIK.  This is a link to activestate's tcl/tk page.  The cookbook link has program snippets.
[http://aspn.activestate.com/ASPN/Tcl](http://aspn.activestate.com/ASPN/Tcl)

---

### Post by meng on 2007-01-27
Most of the hard-copy documentation for GUI programming in Python deals with Tkinter, so I assume it's a popular first choice. There are plenty of other choices though: wxpython, pyqt, pygtk. Documentation is a bit sparser, although the internet is a great thing.

---

### Post by jblebrun on 2007-01-27
A variant of Tcl called OTcl is used in the ns2 network simulator.

---

### Post by Vox754 on 2007-01-28
[QUOTE="dwblas"]As for the person who uses TCL only, they probably never learned Tk. ...Tk is an Extension of TCL to use a windowing system...[/QUOTE]
Yeah, that's what I mean, odd. Why would anyone want to use Tcl without an interface, since there are already lots of good languages for that?

Another thing that calls my attention is that, supposedly, Tcl/Tk is more like an "interpreted" language, rather than a "compiled" one. This is, "programs" run while you have the interpreter installed, but if missing then they cannot work since they are not in binary form.
It seems that ActiveState provides retail support and tools for compiling, but this doesn't concern me right now.

I don't have experience with Python, or for that purpose with any other language, but I guess most graphical toolkits are used in compiled applications.

---

### Post by Lord Illidan on 2007-01-28
Seriously, I hate the really ugly guis that result from it, almost like GTK 1...Has this been solved?

---

### Post by geek_Man on 2007-01-28
Yeah, it's called GTK2. Kidding...

---

### Post by SuperMike on 2007-01-28
You know, the thing to do these days is either the Python/PyGTK GUI experience, or the newer XUL GUI experience. I vote for XUL -- it's cleaner and takes less time to get going once you learn from a good starting point like the [[COLOR="DarkOrange"]**_simplexul_**[/COLOR]]("http://code.google.com/p/simplexul/") project.

---

### Post by psychicdragon on 2007-01-28
> **meng said:**
> Most of the hard-copy documentation for GUI programming in Python deals with Tkinter, so I assume it's a popular first choice.
This is more due to the fact that that Tkinter is part of Python's standard library, meaning it is shipped with Python. I have my doubts about it being a popular choice for GUI programming.

---

### Post by Vox754 on 2007-05-25
I'm just bumping this thread in case anyone wishes to say anything new.

I also want to say that I've been using Tcl/Tk for some months now and I feel quite comfortable with it. It is so... well, easy; just "words" separated by space. Words are command names or command actions, names of variables or widgets, and optionally followed by pairs of options and values.
Note how each word, or more accurately "string", is delimited by space or can be grouped with double quotes (allowing substitution of variables) or with braces (without substitution).

```

command word
command widget option value option value
for {set a 1} {$a <= $limit} {incr a} {body of the loop}
foreach a $list {body of the loop}
frame .f -borderwidth 1 -relief solid
set b1 [button .f.b1 -command {puts "Information"} ]
button .f.b2 -command "$b1 invoke"
button .f.b2 -command {.f.b1 invoke}

```

I must recommend ActiveState distribution, ActiveTcl, which has a wide variety of packages, and includes comprehensive documentation.

About the GUI interface. Yes, it is not very appealing to most Linux users because it mimics the old Motif Toolkit. However this is supposed to be improved in Tcl/Tk 8.5. On Windows, however, toplevels, fonts and widgets look very natural.

What only seems strange to me is that some widgets take a lot of time to load changes on them. For example, when I fill several tables with information, it takes up to 40 seconds at 100 % CPU usage to redraw the window. I'm not sure if there is something wrong with my code, or if the Toolkit and X Server are simply not that fast.
Oh, and also it takes like 3 minutes to print to a new file (5000 lines) the information read.

I'm definitely not an expert but at least I feel comfortable enough to spend some time trying different things.

I'm already thinking to port my application to Python and GTK since everybody talks about them.
It was a nice experience to program in Tcl/Tk, even if they are mostly unknown. If they have such a power, I wonder what I can expect from Python or GTK, which are worldwide renowned.

---

### Post by cwaldbieser on 2007-05-26
I like using Tkinter for building simple GUIs for my python programs.  Tkinter may not be the snappiest GUIs out there, but they get the job done, and I find Tkinter to be both simple and powerful.

I learned a little Tcl/Tk later on.  It is an interesting language, but the basic libraries leave a little bit to be desired.

In the preface to "TCL and the TK Toolkit", John Ousterhout writes that he developed TCL in 1988 so that he could have a reusable command language as a C library package.  Tk was developed in response to Apple's HyperCard system.

These days, there are more powerful options for embedding scripting languages into your C programs (such as  Python, Ruby, etc.).  However, TCL still seems to fill some niches.  Tkinter in python is built on top of Tk, for example.

---

### Post by xtacocorex on 2007-05-27
The commercial program TecPlot uses Tcl/Tk for it's GUI and it's a very comprehensive and power program.  It may not be as full featured as GTK+ or QT, but don't discredit it as unusable since it works well when you don't need a beuatiful GUI.

---

### Post by Vox754 on 2007-06-13
[QUOTE=cwaldbieser]
In the preface to "TCL and the TK Toolkit", John Ousterhout writes that he developed TCL in 1988 ...
[/QUOTE]

I have the book right here and you know what, nowhere it says "TCL", with capitals.
It's not a big deal really, I just think some words look better in capitals and others don't. That is why I also hate when people write PERL, I mean, ugly!
On the other side, FORTRAN looks so right written that way.

I also hate the supposedly correct pronunciation, Tcl/Tk, "tickle" and "tee-kay". What the heck is that! (Don't get me started with TeX)

So, if you are going to invent a new language make sure it has a catchy name. I like Python, Perl, and the awesome combination "Ruby on rails".

I have already named my nonexistent invention, the scripting language known as "Pup".

---

### Post by SNYP40A1 on 2007-06-13
Funny you mention this topic now...I just learned enough of it last weekend to use the Tcl interface that sqllite supports.  Not sure why they chose Tcl, but it was not too painful to learn the bare minimum that I needed to know.

---

### Post by antonc on 2007-06-14
Hi

I've been an avid Tcl/Tk user for quite a few years (>6 or so).
It's a great language for hacking together quick apps to 'scratch an itch', and works really well (as was intended) as a 'glue' language.

The largest app I've written in it was a custom image processing app with the speed-critical stuff in C using the ImageMagick libraries, and the GUI and everything else in Tcl/Tk - worked out to about 50 000 lines or so. (Yup, it was a -pain- to maintain, problem is that the client is still using it, so I'll probably be maintaining, debugging, and updating it till the day I die.. :-))

It works really nicely for string processing, parsing files, talking to databases, etc. There are some -really- nice web app frameworks using Tcl (take a look at AOLserver/OpenACS). Lots of libraries available for various things. I still turn to pure Tcl (and Expect) whenever I need to throw together any little shell-script type things.

ActiveState's packages are great. ActiveTcl, and the packages to produce Starpacks and Starkits (single-file Tcl executables) are awesome. Quite some time back I developed a small database app (for tracking political party branch membership), using Tcl/Tk and Metakit db - the app was to be deployed on Windows (Aargh!), so I wrote it -entirely- under Linux, (using the appropriate cross-platform conventions), and created a Windows executable from that, and viola! deployed on windows... Worked perfectly, and didn't have to get my hands dirty.

And of course, VisualTcl, a really nice IDE and GUI builder.

That being said, I'm now learning Python.. I like the fact that it can use gtk2 (yup, TK apps can look lousy, fonts aren't AAd, and the widget default settings look -bad-, it takes a lot of tweaking to get things looking nice), and that Python can work seamlessly in within the context of a Gnome desktop, with bindings for all the appropriate Gnome-related libraries and services.

Just my 2c worth....

---

### Post by Vox754 on 2007-06-15
> **antonc]
I've been an avid Tcl/Tk user for quite a few years (>6 or so).
[/quote]
Congratulations,  you are officially the current Tcl/Tk expert.

[quote=antonc]
...the packages to produce Starpacks and Starkits...
...I wrote it -entirely- under Linux, ...
And of course, VisualTcl, a really nice IDE and GUI builder.
[/quote]
I think that you need to pay for the developer's kit in order to create those single-file executables.
Currently I may only afford free solutions, but yeah, it should be nice if you can use them.

That is one thing I forgot to mention: Tcl can be used in Linux but the resulting application may work perfectly in Windows. I did it.
When I started, I used Windows but then I almost switched entirely to Ubuntu to develop things said:**
> 
That being said, I'm now learning Python...

It happens to all of us. You think Tcl is great but then you hear lots of good stuff about Python and you cannot resist.
Nevertheless, I think the core developers are planning big updates to Tcl/Tk 8.5, like a better GUI in Unix systems, using the "tile" packages to give them a better look and feel, and also the fonts are going to be fixed. I'm sure I read it somewhere.

---

