---
title: "Microsoft Visual Studio and C++"
date: 2007-10-14
forum: Programming Talk
---

### Post by WarholsGhost on 2007-10-14
Hello,

I am taking a C++ class and we are using Microsoft Visual Studio under windows xp. I need a good and easy to use replacement for linux becasue i want to be able to do my projects at home. 

I need it to be as close to Visual Studio as possible, as i am just beginning and i would like to have something consistent. 

thanks in advance.

---

### Post by CptPicard on 2007-10-14
Umm, sorry, Windows is Windows and Linux is Linux... there are IDEs but consistency is not something you're going to get on the IDE or project management level.

That said, Eclipse's CDT, Anjuta, Code::Blocks, KDevelop are all good.

In particular if this is an introductory C++ class it's a bit dumb to require a particular IDE on some OS... I don't understand why American(?) schools do this. All you need at that level is a text editor and a compiler, both of which Linux provides in spades.

---

### Post by j_g on 2007-10-14
There is nothing on Linux compatible with Visual C++. MSVC directly creates its makefile (versus using any GNU "auto tools"), so you'll need to use Visual C++ if you expect to turn in any "project" that is compileable under Visual C++.

Furthermore, if your projects use Microsoft Foundation Classes (MFC), then you definitely need MSVC.

---

### Post by aks44 on 2007-10-14
Hmm you're gonna have hard time I fear.

There are many compatibility problems between MSVC and G++, the biggest one IMHO being the make system (Linux's makefiles vs MS' XML project files).

Plus MSVC is far from implementing standard C++ (although 8.0 is way less worse than the previous ones), it has many "features" that are not standard and it doesn't support some standard features.

And let's hope your class won't require you to use Win32 APIs...


As you must use it for school, my best bet would be to use MSVC8 Express Edition (free to download from MS) inside a XP VM on Ubuntu. Or to dual boot. Anyway I'm pretty confident it won't work under Wine as it requires .NET 2.0 runtime IIRC, and AFAIK there is no FOSS IDE that can handle (read AND write) MSVC's project files.


Good luck anyway, and if you find such a beast please let me know I'd be quite interested. ;)


EDIT: lol I'm a bit late on this one :p

---

### Post by WarholsGhost on 2007-10-14
um i have to do win32 programs

i guess i will just spend time in the lab to do my projects. 

sadly enough, myself and the teacher are the only ones who do not use windows. 


UG!

---

### Post by WarholsGhost on 2007-10-14
> **CptPicard said:**
> Umm, sorry, Windows is Windows and Linux is Linux... there are IDEs but consistency is not something you're going to get on the IDE or project management level.

That said, Eclipse's CDT, Anjuta, Code::Blocks, KDevelop are all good.

In particular if this is an introductory C++ class it's a bit dumb to require a particular IDE on some OS... I don't understand why American(?) schools do this. All you need at that level is a text editor and a compiler, both of which Linux provides in spades.

do you have any suggestions for compilers, most of my coding has been in html so text based editing is quite easy for me.

---

### Post by CptPicard on 2007-10-14
GCC is, de facto, *the* compiler on Linux... and in particular the g++ part of it for C++. No contest. :)

---

### Post by aks44 on 2007-10-14
> **WarholsGhost said:**
> do you have any suggestions for compilers, most of my coding has been in html so text based editing is quite easy for me.

G++

```
$ sudo apt-get install build-essential
```


then to compile & test something:
```
$ g++ -o testoutput main.cpp other.cpp yetanother.cpp
$ ./testoutput
```

---

### Post by slavik on 2007-10-14
> **CptPicard said:**
> Umm, sorry, Windows is Windows and Linux is Linux... there are IDEs but consistency is not something you're going to get on the IDE or project management level.

That said, Eclipse's CDT, Anjuta, Code::Blocks, KDevelop are all good.

In particular if this is an introductory C++ class it's a bit dumb to require a particular IDE on some OS... I don't understand why American(?) schools do this. All you need at that level is a text editor and a compiler, both of which Linux provides in spades.
Because professors don't want to learn 20 different IDEs in case a student comes with a problem with an IDE they use.

Other than that, they only care about the source code.

If it's an intro to C++, I suggest Geany.

---

### Post by Natr0n on 2007-10-14
> **slavik said:**
> Because professors don't want to learn 20 different IDEs in case a student comes with a problem with an IDE they use.If all they'd use in class is a text editor and the command line there wouldn't be any questions about IDE's.

---

### Post by TreeFinger on 2007-10-14
The text editor in windows sucks. You pretty much have to use an IDE for development in windows.

I think I am the only linux user in my class of about 20. My teacher requires us to print out our source code and out put results so it doesn't matter where I compile.

---

### Post by slavik on 2007-10-14
> **Natr0n said:**
> If all they'd use in class is a text editor and the command line there wouldn't be any questions about IDE's.
I know a professor who teaching intro C++ in a classroom with Solaris systems, little help that did.

---

### Post by Bushfire on 2007-10-14
> 
um i have to do win32 programs


In an introductory C++ course? If I may be so bold: What the hell? Just between you, me, and the Internet, if this is indeed supposed to be an introductory course (that's the impression I got), I personally wouldn't trust whoever's organising the course.

---

### Post by CptPicard on 2007-10-14
> **slavik said:**
> I know a professor who teaching intro C++ in a classroom with Solaris systems, little help that did.

Actually, an IDE is way too complex for a beginner, especially in a teaching situation. The command line is really simple, gives you a restricted command set that is hard to misunderstand or misuse if you're given good examples, the text editor does the job just fine and perhaps doesn't let you off the hook too easily with syntax before it's time... and the end product of the exercise is not so tied to the IDE that you need the right one just to run your Hello World :)

---

### Post by LaRoza on 2007-10-14
There is a sticky in this forum, which addresses such situations.

---

### Post by j_g on 2007-10-14
There's a bit of confusion here.

You say that you're writing "Win32 software". But then you say that your professor requires only the source code and "output". I presume then that you're writing what would be referred to as a "console mode" program?

When you create your project in MSVC++, what kind of project do you create? You create a "Win32 Console Application", right? This means that you have a main() function, and when you run your executable, Windows automatically opens a console window to which you output text using printf, fprints, puts, or some other such console-output function.

You're not creating a "Win32 Application" project, right? This would mean that you have a WinMain() function (instead of main). When you run the executable, Windows does not open any console for you. Your program is expected to create its own window with calls to functions like CreateWindow, CreateDialog, or DialogBox. And you can draw both text and graphics to the window.

You're also not creating a "MFC AppWizard (exe)" project, right? Again, this means that you don't get a console window. Your app creates its own windows, but since you're using MFC, this framework's startup code actually does the calls to CreateWindow for you, to create a "main application" window into which you can open "document windows".

(All of the other MSVC projects create either "components" such as ATL things, or shared libs).

If you're doing a Win32 console app, then you can code using any C/C++ compiler, such as Linux's gcc/g++. If you develop on Linux, comment out the following line at the top of your source files (but put the line there at the top of every source file):

```
//#include "windows.h"
```

Write your code, compile, and test on Linux. Then take _only_ your source file(s) to your lab -- ie, perhaps copied to a USB stick or CDROM. (We'll assume you have two source files named main.c and file.c).

Run MSVC's IDE, and select the "File -> New" menu command. This brings up the New (Project) dialog. Select "Win32 Console Application". Enter any name you wish for the project. (Here we'll assume "example"). Click the Ok button. This will next present a dialog asking you what kind of console app you want. Select "an empty project", and click the "Finish" button.

MSVC will create a project (named "example", in a newly created directory with the same name) without any source files in it. Copy your source files to that new directory that MSVC created. (Above that was our "example" directory). You should see a couple files already there, created by MSVC, such as example.dsp, example.opt, example.ncb, etc. Edit your source files to uncomment that line including windows.h. (ie, Remove the two // characters at the start of the line).

Now select MSVC's "Project -> Add to Project -> Files..." menu item. This will bring up a file dialog showing the contents of your project directory. You should see your two source files listed there. Click on both names, while holding down the Ctrl key, to highlight them both. Then select the Ok button. Your two files have now been added to your project.

Now, go to "Build -> Build example.exe" (or "Build -> Rebuild all") to compile your source into a Win32 exe.

Once your exe is tested, and everything is fine, close down MSVC++. (You have to close it to ensure that it finalizes all changes you made when creating the project). Go into your example directory, and save your sources files, as well as the 3 files that end in the following extensions:

.mak
.dsp
.dsw

You don't need the .ncb, .opt, nor other files.

Give these 3 files (and your source files) to your instructor if he needs to recompile it under MSVC++.

---

