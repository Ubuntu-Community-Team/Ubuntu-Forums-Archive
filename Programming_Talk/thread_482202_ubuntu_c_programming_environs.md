---
title: "ubuntu c programming environs"
date: 2007-06-23
forum: Programming Talk
---

### Post by nss0000 on 2007-06-23
Gents:

After a break of many years I've started C-programming again. Got my copy of K&R and a couple tutorials. While 'old bones break easy' it's come back pretty quick. Recently retired I'm in no rush .... though I'm pointed toward scientific/HW related tasks. 
Now I'm looking for a visually attractive and useful coding "environment?" -- one that obeys the rules of any good fiction and will amuse, console and enlighten as-well-as process keystrokes.

Currently I use GEDIT for typing, and along with  CLI <gcc> it's not bad --- though a long way from my kindly remembered BORLANDx16 bit environment. The 'V-word' or 'E_word' are not even to be considered in respectable company.    

So ... for snuggly, eyecandy_laden C-coding environs what's out-there?

nss
*****

---

### Post by Choad on 2007-06-23
scribes is an amazing editor. not a full blown environment tho

---

### Post by volanin on 2007-06-23
Well, it's not a simple editor, but I personally love Eclipse, with the CDT plugins installed.
Great IDE for coding in C/C++.

---

### Post by WW on 2007-06-23
The IDEs (for C/C++ in particular) that I've heard of are:

Anjuta
KDevelop
Eclipse with CDT plugins
Code::Blocks
Netbeans with the C/C++ Development Pack

I haven't used any of them enough to pick a clear winner. I tend to use Code::Blocks when I want to use an IDE.  For opinions, check out the sticky thread "What's your Favorite IDE?" (but be sure you have some time to spare--it currently has 575 replies :).

---

### Post by MAZDA on 2007-06-23
I suggest to use the Anjuta C/C++ IDE.

From my side of view one of the best C/C++ IDE for LINUX.
[http://anjuta.sourceforge.net/screen-shots](http://anjuta.sourceforge.net/screen-shots)

Extremly fast for building big projects.
Has a very smart wizard for importing Programm Projects that are build with the autconf tools.
Has sveral build in Plugins like SVN, CVS for importing the Sources directly from the Reps !
Live Debuggers and Watchdogs are also included !

This  howto here describe how to build the freshest version of Anjuta in Ubuntu !

[http://groups.google.com/group/anjuta/web/building-anjuta-from-sources-on-ubuntu](http://groups.google.com/group/anjuta/web/building-anjuta-from-sources-on-ubuntu)

Tell me if it works for you !

---

### Post by nss0000 on 2007-06-23
WW:

Thanks to you and others who have responded. At first I did not understand what I took to be  very conservative comments. Surely -- I thought --  advances must be HUGE in IDEs. Then as advised I read the "sticky".

Many POV are given there, yet a theme comes thru ... quoting one gent:

  
".... As to the best for beginners: no IDE at all. Use a text editor and commandline compiler. All the wizzards and stuff in IDEs will prevent you from learning the language and instead make you learn the tool ...."

Very reasonable ... however, there is the issue of GLADE .....

nss
******

---

### Post by WW on 2007-06-23
I have two responses to that argument:

1. How far do you take the logic?  For example, a compiler is just a tool to create machine code.  So maybe you shouldn't learn C, and instead learn assembler.  Using C prevents you from learning what the machine is *really* doing.

2. If you buy the "no IDE at all so you really learn C" argument, you still reach a point where you know the language, and you would like to take advantage of the increased productivity that can from using a good IDE (code completion, code folding, automatic generation of build dependencies, etc). Then you are back to the original question: which IDE to use?

---

### Post by moma on 2007-06-23
Hello all,

I usually preach about Code::Blocks IDE.  The installation instructions are here:
[http://ubuntuforums.org/showthread.php?p=1962696#post1962696](http://ubuntuforums.org/showthread.php?p=1962696#post1962696)

But today I want to recommend some [COLOR="SeaGreen"]light-weight development environments[/COLOR]. Many of these are rather old and will not (normally) provide ready-made .deb packages, so we must compile them from source.  

**OpenLdev**: The first and maybe the best candidate is
[http://www.openldev.org/](http://www.openldev.org/) 

Read the INSTALL or README file for howto build it. 

It requires several GNOME and GTK+ related packages (AFAICR.)
$ [COLOR="SeaGreen"]sudo apt-get install libgtksourceview-dev libvte-dev  libgnomeprintui2.2-dev  libgtk2.0-dev[/COLOR]
And maybe others..

There is a tiny bug in one of the source files which you must fix before compilation. 
It is easy to do.  See: [http://i1.no/04k5/](http://i1.no/04k5/)

Run "Auto generate" from the build-menu after you create a new c project.
---------------------------------------------------------------------------------------

**Geany** is absolutely worth mentioning. 
It is still in early development, version 0.11 came out in may.  But give it a try anyway ;-)
[http://geany.uvena.de/](http://geany.uvena.de/)
---------------------------------------------------------------------------------------

**Other IDEs** which I haven't tried on modern Ubuntus are:     (I think: some of these resembles the old BORLAND c environment)
XWPE:  [http://identicalsoftware.com/xwpe/](http://identicalsoftware.com/xwpe/)  

FLDev: [http://www.hardl.de/fldev/](http://www.hardl.de/fldev/)

The Motor: [http://thekonst.net/motor/](http://thekonst.net/motor/)

---

### Post by MAZDA on 2007-06-23
> **nss0000 said:**
> 
Many POV are given there, yet a theme comes thru ... quoting one gent:

  
".... As to the best for beginners: no IDE at all. Use a text editor and commandline compiler. All the wizzards and stuff in IDEs will prevent you from learning the language and instead make you learn the tool ...."

Very reasonable ... however, there is the issue of GLADE .....

nss
******

From my side of view this gent has never worked or used a modern C/C++ IDE.
Thats why i would like to say that his comment has nothing to do with the reality.

If this gent has one time used a IDE he could exactly say at least which IDE prevent a begiiner to learn the programming Language C and he can also say since when a IDE prevent a beginer to learn the Programming language C.
The argument that a IDE prevent persons to learn the programming language C is for me totaly new !

Learning a programm Language like C need as first a good Programming Environment that can tell the begninner what he has written wrong. If a beginner use the stupid stone age tools like vim or gedit for writing C code he will after two day of unsuccessfull programming stop the hole adventure.

Learning C mean understanding what the commands has for effects. For Understanding the effects of the C command you need a powerfull IDE with a extremly good debugger that show you the values of Variables
at the run time or stop the programm at given breakpoints to do a step by step run.

I itself has used LINUX IDE's more than 3 Years.
The same thing also for the Microsoft Visual Studio.

From my programming experince the biggest mistake for a beginner how want  to learn a programming language like C is if he decide to use stone age tools that have nothing to do with programming itself.

---

### Post by KaeseEs on 2007-06-23
> **MAZDA said:**
> From my side of view this gent has never worked or used a modern C/C++ IDE.
Thats why i would like to say that his comment has nothing to do with the reality.

If this gent has one time used a IDE he could exactly say at least which IDE prevent a begiiner to learn the programming Language C and he can also say since when a IDE prevent a beginer to learn the Programming language C.
The argument that a IDE prevent persons to learn the programming language C is for me totaly new !

Learning a programm Language like C need as first a good Programming Environment that can tell the begninner what he has written wrong. If a beginner use the stupid stone age tools like vim or gedit for writing C code he will after two day of unsuccessfull programming stop the hole adventure.

Learning C mean understanding what the commands has for effects. For Understanding the effects of the C command you need a powerfull IDE with a extremly good debugger that show you the values of Variables
at the run time or stop the programm at given breakpoints to do a step by step run.

I itself has used LINUX IDE's more than 3 Years.
The same thing also for the Microsoft Visual Studio.

From my programming experince the biggest mistake for a beginner how want  to learn a programming language like C is if he decide to use stone age tools that have nothing to do with programming itself.

Well, I'm living proof that your theory is bunk, having learnt C on 'stone-age tools'.  I've continued to use vim after picking it up, after using Anjuta as well.  While I have no problem with modern IDEs, I prefer vim/gvim, as with the proper toolset I have all the features I want and none that I don't.  Really the only thing vim doesn't do well that I want it to is folding, but I don't miss it as much as I miss vim's editing features when using another editor.

As for C being so complex that a programmer needs an IDE to code effectively, this is rubbish.  Honestly, while pointer-heavy code can get tricky, it's seldom the best approach, and the rest of the language just isn't that hard.  Architectural complexity in a nontrivial C program will always be greater than syntactic complexity, and this is best tackled by utilizing a modular design.


Now, as for the OP, I second whoever recommended Anjuta and Code::Blocks.

---

### Post by MAZDA on 2007-06-23
Hello KaeseES

> **KaeseEs said:**
> Well, I'm living proof that your theory is bunk, having learnt C on 'stone-age tools'.I've continued to use vim after picking it up, after using Anjuta as well. 
I dont regret that you are a living proof for howto learn a programming Language like C on Linux.

[B]The only thing what i regret is the question if you are really a good living proof for learning a Programming Language !

What i also regret is the Question since when a IDE prevent persons to learn a programming Language like C
[/B]

Using VIM for programming is from my side of view just stupid.
Is the same thing like using a fork or a knife for eating a soup.
Inteligent people normally use a spoon for eating a soup.
Sorry to tell you that.

---

### Post by loell on 2007-06-23
each to his own environment. whether it lightwieght or heavyweight editor.

---

### Post by KaeseEs on 2007-06-23
> **MAZDA said:**
> Hello KaeseES


I dont regret that you are a living proof for howto learn a programming Language like C on Linux.

[B]The only thing what i regret is the question if you are really a good living proof for learning a Programming Language !

What i also regret is the Question since when a IDE prevent persons to learn a programming Language like C
[/B]

Using VIM for programming is from my side of view just stupid.
Is the same thing like using a fork or a knife for eating a soup.
Inteligent people normally use a spoon for eating a soup.
Sorry to tell you that.


Well, your view is rather foolish.  I suppose Linus Torvalds is an idiot for using MicroEmacs?  What you seem to misunderstand is that the advantages you claim for IDEs are all available with proper editors - indeed, they generally predate the existence of IDEs!

---

### Post by pbrockway2 on 2007-06-23
I'm another forking stupid person who would question the early and enthusiastic use of an IDE over a plain text editor (Kate, or whatever).

2c:

The context is that of a beginner - not someone learning *a* programming language (easy), but someone learning programming (difficult).  And a few of the problems as I see them are:

(1) There is no motivation to learn the syntax of the compile/link/build tools, or the concepts underlying them. Take a look at any Java forum to see the number of people who show no clue about the concept of the "classpath", although it's central to the use of that language.  Early use of command line would clear the problem up, but the hapless programmer is stuck wailing "But it works in <insert IDE>!"

(2) Problems cannot be easily diagnosed by a beginner as belonging to the misuse or misconfiguration of the IDE, or the misuse of the language.  And, in any case, they must learn *both*.

(3) Problems cannot be easily (and accurately, completely etc) described.  The ability to describe a problem *in a way that others can reproduce it* is a skill that beginning programmers have to learn if they want help on the internet.  Early adoption of an IDE hinders them in a couple of ways:  the configuration of the IDE must be described as it may be contributing to the problem (point 2), and help is limited to those who use (or, at any rate, are familiar with) the IDE.

(4) Great middens of autogenerated, do-not-edit-below-this-line, code which add nothing to the beginner's understanding and, with their awful variable name and other code conventions, set a continual bad example.

(5) The ever present temptation that the beginner will be seduced away from programming and drawn to losing hours fluffing about with GUIs.

These are just the things that occur to me - and I haven't mentioned the obvious merits that an IDE offers a beginner (... because they're obvious!).  I have been led to change my mind about this problem: from out-and-out opposition to the IDE's to a recognition that it depends very much on the person (their abilities/personality/experience etc) how much of a danger IDEs can be.  The question is best judged by an in-person teacher (or whoever might be playing that role): but the dangers are there.

---

### Post by MAZDA on 2007-06-24
> **KaeseEs said:**
> Well, your view is rather foolish. I suppose Linus Torvalds is an idiot for using MicroEmacs?

Linus Torvalds not only use MicroEmacs for Programming he even tell the People to use Ubuntu with KDE rather than Ubuntu with Gnome !
[http://www.osnews.com/story.php/12956/Torvalds-Use-KDE/](http://www.osnews.com/story.php/12956/Torvalds-Use-KDE/)
> If you think your users are idiots, only idiots will use it. I don't use Gnome, because in striving to be simple
Thats why you are working on Ubuntu Feisty Fawn 7.04 with Gnome and not like Linus Torvalds say on Kubuntu Feisty Fawn 7.04 with KDE right KaeseES !

---

### Post by nss0000 on 2007-06-24
Gents:

I appreciate the lively discussion ; one point that comes thru to me is that  different people have found different programming environs most helpful to their own creative efforts. One size does NOT fit all. 

Even in my "early recovery" stages --- working into K&R Ch4 (functions) in parallel with the quicky on-line tutorial at:

     [http://einstein.drexel.edu/courses/CompPhys/General/C_basics/#compute](http://einstein.drexel.edu/courses/CompPhys/General/C_basics/#compute)

... I can see virtues to both my current simple text_editor and an IDE ( will I NEVER stop making typos, and where-the-heck  is  ' line 35...error before }?????' ) . For some-strange-reason, passing strings-to-functions seems enormously amusing. Of course for scientific programming the show_stoppers are multi-dim arrays ( matrix algebra makes theory work ) and drivers ( makes the HW work ).

Anyrate, based on several comments I have DLoaded and looked at the ide ANJUNTA --- I can see why many like the unified interface. I suspect someplace in K&R Ch6 (structures) I'll feel-the-need to try it.

One tidbit I can pass along. Before cracking K&R I put myself thru a 4-week "bootcamp" in bash_shell programming. Nothing too fancy, mind ... I still write one-a-day , and feel that the code/shell interaction & de_bugging practice polished up some (very) rusted edges.

 Thanks for sharing your valuable personal experiences. I'll keep posting as I progress.

nss
******

---

### Post by ankursethi on 2007-06-24
Geany is small and does the job. It's really just an average text editor with some added features of an IDE at the moment, and that's what I like best about it.

BTW, I agree with the OP that nothing in the market beats the good ol' Borland IDE's from the early nineties. The ugly VGA graphics make using it all the more fun. One thing that comes close is Vim/Emacs in the terminal with some added customization scripts.

---

