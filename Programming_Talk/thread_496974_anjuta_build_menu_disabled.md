---
title: "anjuta build menu disabled"
date: 2007-07-09
forum: Programming Talk
---

### Post by desijays on 2007-07-09
I just downloaded and installed the latest version of anjuta 2.2.

after it was installed i tried opening a new project and got an error saying it needed autogen 5.

so i downloaded that and installed it and now i am able to create a project.

i made a simple hello world program just to see if everything was working fine.

i compiled it and i got no errors.

Now to get the executable file, i have to build it. But my build menu is completely greyed out. Except for the 'compile' sub-menu everything else in the build menu is greyed out.  I don't why.

I tried this and that and whichever other way I can, but im stumped.

Any idea why its not working?

---

### Post by desijays on 2007-07-10
Am i on my own in this :( ?

---

### Post by slavik on 2007-07-10
did you create a project for the hello world test?

anjuta 2.x only works with projects, no more single file stuff.

---

### Post by angryfirelord on 2007-07-15
I'm also having the same issue. Putting it inot a project does not solve it either.

Instead, I switched to geany, which I found to be just as good. [http://geany.uvena.de/]("http://geany.uvena.de/")

---

### Post by matt1606 on 2007-09-19
I'm having the same problem... I don't know its source. It doesn't exists in anjuta 1.2.4a. Any help?

---

### Post by BuffaloX on 2007-09-20
I couldn't get Anjuta to work either, I installed it because it looked easy. :oops:
So I installed kdevelop, which seems nice.
But then I installed code::blocks, which seems super nice. :)
It autodetects your C/C++ compiler, and it worked immediately with compile and execution of my hello world.
I made a small bug on purpose, just to see if it would be reported correctly inside the IDE, and it was.

So unless something goes horribly wrong, I stay with code::blocks. 8-)

---

### Post by spamalot on 2008-04-13
hi all,

likewise, i can compile, but not build. i switched from eclipse (at least temporarily) to anjuta due to :

[http://ubuntuforums.org/showthread.php?t=654567](http://ubuntuforums.org/showthread.php?t=654567)

using the file browser there is a main.o next to main.cc, but that does not show in the project view within anjuta...

any help would really be appreciated...

another question is: eclipse project wizard asks for whether it is 1) an exec 2) a static library 3) a shared library... where are these choices in anjuta?

PS: also tried KDev, I just got discouraged on the first project (too many options to choose from).

---

### Post by spamalot on 2008-04-13
finally settled for Code::Blocks which delivered its purpose -so far- without problems...but still interested to hear about any fix to the problem above with Anjuta.

---

### Post by JS Lemming on 2008-05-09
I'm having the same problem. I was a big fan of Anjuta too.

---

### Post by slavik on 2008-05-09
> **slavik said:**
> did you create a project for the hello world test?

anjuta 2.x only works with projects, no more single file stuff.

Quoting it as people seem to have missed it.

---

### Post by JS Lemming on 2008-05-09
YES. I didn't miss it.

---

### Post by Vernamon Rakashi on 2008-05-22
I'm having the exact same problem and I was hoping to use Anjuta for me to learn C++. I've looked just about everywhere for help and I would love to know how to fix it.

---

### Post by slavik on 2008-05-22
> **Vernamon Rakashi said:**
> I'm having the exact same problem and I was hoping to use Anjuta for me to learn C++. I've looked just about everywhere for help and I would love to know how to fix it.
see 2 posts above yours.

Anjuta 2.x will not compile a single file the way 1.2 would. In Anjuta 2.x you have to create a project.

---

### Post by shr2004 on 2008-05-29
Without starting a new thread I better use this thread to ask the solutions of my problem.
I have installed Anjuta several times on Hardy, but each time same result: the IDE does not have menu items: Project, Build, Debug, CVS, Setting..at all. 
Then it is just an ordinary editor, not an IDE.
I checked its manual and then surprised to see that all menu items are missing from my installation. I tried with add/remove program, synaptic package manager, from terminal window..from ubuntu repository...all are same.
Any help is appreciated. Otherwise I can move to code:Block or Kdevelop

---

### Post by kboy on 2008-06-24
I have the same problem, and i see no one posted a solution yet.
I hope there is a solution.

---

### Post by slavik on 2008-06-24
post the screenshots of what your anjuta interface and make sure everything (the toolbars) are selected in view ...

---

### Post by korbman on 2008-08-17
Ok, I am another victim of the same problem.
I made both, helloworld test and I also tried with an already
working project. Any suggestion to fix the problem will be welcome.

Cheers,

mk.

---

### Post by spamalot on 2008-08-23
not a techie here. used to have that pb and other pb with eclipse, so switched to Code::Blocks, much better and reliable. just a view among many.

---

### Post by JakcV on 2008-09-09
I cannot create a execute files in anjuta 2.4.1.

---

### Post by rnodal on 2008-09-10
2.2.0 works fine. I will give it a try tomorrow at work since I'm assuming that 2.4.1 is in Ubuntu 8.04 or later.

-r

---

### Post by apricot on 2008-09-22
same problem here, build-essential installed, made a new simple project, and the build option grayed! Help?

---

### Post by slavik on 2008-09-22
> **slavik said:**
> see 2 posts above yours.

Anjuta 2.x will not compile a single file the way 1.2 would. In Anjuta 2.x you have to create a project.

Why am I even quoting myself? Reading is bliss, do it!

---

### Post by apricot on 2008-09-22
i solved my problem. As i made a project and didn't have the option build, a had compile, run autogenerate and execute program options not greyed. I ran the run autogenerate option and it asked me for some packages, i do not remember wich ones, but when i installed them and ran run autogenerate, the build option appeared! 

Answer to shr2004: you must enable plugins in Edit>Preferences>General>Installed Plugins to have that menu items!

---

### Post by apricot on 2008-09-22
> **slavik said:**
> Why am I even quoting myself? Reading is bliss, do it!
In case you do not know to read i mentioned that i made a project. You know to read, right?

---

### Post by slavik on 2008-09-22
> **apricot said:**
> In case you do not know to read i mentioned that i made a project. You know to read, right?
I did ask for screenshots :)

---

### Post by lawentzel on 2008-09-26
So.. is there a way to install the earlier version of Anjuta on Ubuntu 8.04?  Thanks.

---

### Post by peji on 2008-10-01
Hi there,

 I had the same problem and reading the forum of anjuta someone points out the solution, at least for me, Lee Mulcahy said:

In case you have not solved your problem, I had the same problem when I first tried a new project. What the User's Manual does NOT say is that you need a make file before the build options are active. I selected 'Build/Run Autogenerate...' I got a lot of errors that told me I had to download and install some more packages, such as autoconf, libtool, and automake. After I did this, I ran Autogenerate again, with no parameters, and it generated some sort of makefile. After that completed, the Build options were no longer grayed out, I built the program, and it ran.


Cheers.

Jose.

---

### Post by DenKain on 2008-10-02
Using version 2.4.2 I can compile and build. When I try to execute the program though it will not work. Just encase you ask yes I have built a new project and yes I did save it. I can not even run the program in the terminal on my own. I checked the file and it was set to executable. For a while now I have just been using a script I wrote to have g++ compile and name the program. Then I would use another script to execute it to make sure that it runs properly. I am not at home at the moment, I am on an XP box, but when I get home I might give code::blocks a try.

---

### Post by lawentzel on 2008-10-13
I managed to download the old files and install version 1.2.4a.  Everything works exactly like it use to!

---

### Post by UnrealMiniMe on 2008-11-12
I actually have a very similar problem.  I can compile, but most of the Build menu is grayed out.  According to the Anjuta manual, I need to run Build -> Configure Project first, so that GNU autotools can generate a makefile.  **That's all well and good, but...my Anjuta is crashing when I try to configure my project.  This even happens with generic "Hello World" projects in both C and C++.**

When I hit Build -> Configure Project, this Configure Project menu comes up:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DefaultConfig.jpg[/IMG]

**[SIZE="4"]Once I hit the Execute button, Anjuta just silently crashes without an error message.[/SIZE]**  When I open it back up, the build menu is still grayed out, and the only apparent way to rectify the situation is to try configuring the project again...which keeps crashing Anjuta, ad infinitum.  It doesn't matter if I change the configuration, either (and it doesn't matter whether "Regenerate Project" is checked or unchecked).  Here's the stock debug config, which also results in a crash:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DebugConfig.jpg[/IMG]

I just checked Synaptic again, and I have all of Anjuta's dependencies and recommended packages installed, including:
gcc, g++, make, automake, autoconf, autogen, libtool, etc.
I've tried removing (and even completely removing) Anjuta and reinstalling it several times, to no avail.

Any ideas?  I'm running the 64-bit Intrepid.
Thanks!

---

### Post by UnrealMiniMe on 2008-11-13
Sad panda bump. :confused:

---

### Post by UnrealMiniMe on 2008-11-17
> **UnrealMiniMe said:**
> I actually have a very similar problem.  I can compile, but most of the Build menu is grayed out.  According to the Anjuta manual, I need to run Build -> Configure Project first, so that GNU autotools can generate a makefile.  **That's all well and good, but...my Anjuta is crashing when I try to configure my project.  This even happens with generic "Hello World" projects in both C and C++.**

When I hit Build -> Configure Project, this Configure Project menu comes up:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DefaultConfig.jpg[/IMG]

**[SIZE="4"]Once I hit the Execute button, Anjuta just silently crashes without an error message.[/SIZE]**  When I open it back up, the build menu is still grayed out, and the only apparent way to rectify the situation is to try configuring the project again...which keeps crashing Anjuta, ad infinitum.  It doesn't matter if I change the configuration, either (and it doesn't matter whether "Regenerate Project" is checked or unchecked).  Here's the stock debug config, which also results in a crash:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DebugConfig.jpg[/IMG]

I just checked Synaptic again, and I have all of Anjuta's dependencies and recommended packages installed, including:
gcc, g++, make, automake, autoconf, autogen, libtool, etc.
I've tried removing (and even completely removing) Anjuta and reinstalling it several times, to no avail.

Any ideas?  I'm running the 64-bit Intrepid.
Thanks!

:popcorn:

---

### Post by UnrealMiniMe on 2008-11-19
Anyone else having problems with this / not having problems with this?

---

### Post by UnrealMiniMe on 2008-11-24
> **UnrealMiniMe said:**
> Anyone else having problems with this / not having problems with this?

:popcorn:

---

### Post by UnrealMiniMe on 2008-11-30
> **UnrealMiniMe said:**
> I actually have a very similar problem.  I can compile, but most of the Build menu is grayed out.  According to the Anjuta manual, I need to run Build -> Configure Project first, so that GNU autotools can generate a makefile.  **That's all well and good, but...my Anjuta is crashing when I try to configure my project.  This even happens with generic "Hello World" projects in both C and C++.**

When I hit Build -> Configure Project, this Configure Project menu comes up:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DefaultConfig.jpg[/IMG]

**[SIZE="4"]Once I hit the Execute button, Anjuta just silently crashes without an error message.[/SIZE]**  When I open it back up, the build menu is still grayed out, and the only apparent way to rectify the situation is to try configuring the project again...which keeps crashing Anjuta, ad infinitum.  It doesn't matter if I change the configuration, either (and it doesn't matter whether "Regenerate Project" is checked or unchecked).  Here's the stock debug config, which also results in a crash:

[IMG]http://i368.photobucket.com/albums/oo130/UnrealMiniMe/DebugConfig.jpg[/IMG]

I just checked Synaptic again, and I have all of Anjuta's dependencies and recommended packages installed, including:
gcc, g++, make, automake, autoconf, autogen, libtool, etc.
I've tried removing (and even completely removing) Anjuta and reinstalling it several times, to no avail.

Any ideas?  I'm running the 64-bit Intrepid.
Thanks!

:guitar:

---

### Post by UnrealMiniMe on 2008-12-08
i can haz help, plz? :)

---

### Post by mdurham on 2008-12-08
run anjuta from a terminal and see what is reported (if anything!) when it crashes.

---

### Post by UnrealMiniMe on 2008-12-11
Good call, mdurham, and thanks for replying :)
> minime@COMPUTER:~$ anjuta
Installing parsers: Asm, Asp, Awk, BETA, C, C++, C#, Fortran, Java, Lisp, Lua, Make, Pascal, Perl, PHP, Python, Ruby, Scheme, Sh, SML, SQL, Tcl, Vera, Verilog, Vim
    Asm: 
    Asp: 
    Awk: 
    BETA: 
    C: 
    C++: 
    C#: 
    Fortran: 
    Java: 
    Lisp: 
    Lua: 
    Make: 
    Pascal: 
    Perl: 
    PHP: 
    Python: 
    Ruby: 
    Scheme: 
    Sh: 
    SML: 
    SQL: 
    Tcl: 
    Vera: 
    Verilog: 
    Vim: 
OPENING /home/minime/Projects/AnjutaProjects/foobar/src/main.cc as C++ language file

[B](anjuta:27031): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed
Segmentation fault[/B]


The log is the same regardless of whether I start Anjuta with the project open or closed and regardless of whether I first compile before I attempt to configure the project (where it fails).  It seems like Anjuta is calling a GTK method incorrectly...though unless everyone else is getting the same error, I'm not sure what about my computer is triggering it.  I don't think it has to do with any weird residual custom settings or anything either, since I just made a clean install of Intrepid 64 this week.

---

