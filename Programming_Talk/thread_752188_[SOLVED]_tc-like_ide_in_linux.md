---
title: "[SOLVED] tc-like ide in linux?"
date: 2008-04-11
forum: Programming Talk
---

### Post by bhadotia on 2008-04-11
Is there an ide for practicing c/c++ languages like tc 0r tcwin45 (in windows) in linux (ubuntu) .I am doing my first course in c language , so i need a simple learning enviornment like tc etc. Also the book which i am following also recommends tc for beginners.

---

### Post by pedro_orange on 2008-04-11
This is a question for the Programming Talk section really.

But there are loads of C/C++ IDEs out there. 
You can check the stickies in the Programming Talk section.

IDEs I can think off the top of my head:
Eclipse
Geany
...Gedit? lol

---

### Post by bhadotia on 2008-04-11
Also can i use tcwin45 itself (if possible with the help of wine). If so, please tell me how to use a windows application in linux with the help wine . I have never run an application with wine before (actually I am downloading wine right now after having this idea).

---

### Post by pedro_orange on 2008-04-11
All you need to do is:

Install wine.
Open the setup.exe in wine.
It should install to your ~.wine/drive_c/program files/

And then when it's installed it should run within wine just as with windows.
If it fails check WineHQ for other versions of your IDE and their compatibility with wine.

Otherwise you can always have a Windows environment virtualised on ur linux box running tc.

---

### Post by bhadotia on 2008-04-11
So are these IDE's  (gleany, eclipse, .. and of course gedit.. lol) available in add and remove apps/ synaptics.

---

### Post by vinu76jsr on 2008-04-11
this is not an absolute reply but I suggest you to switch your IDE to something powerful like netbeans with c/c++ support it have code completion and lots of other features or for simpler tasks you could try anjuta IDE which is really great for linux

---

### Post by LaRoza on 2008-04-11
> **bhadotia said:**
> So are these IDE's  (gleany, eclipse, .. and of course gedit.. lol) available in add and remove apps/ synaptics.

Yes. See [http://ubuntuprogramming.wikidot.com/Tools](http://ubuntuprogramming.wikidot.com/Tools)

For learning C, Gedit with its plug ins or Geany should be just what you need.

---

### Post by pedro_orange on 2008-04-11
I write my code in gedit with it's plug ins. 
Keeps it simple. 

At work I have to use visual studio, and it's just bloat.
Give me a text editor and a CL compiler anyday,

---

### Post by LaRoza on 2008-04-11
> **pedro_orange said:**
> I write my code in gedit with it's plug ins. 
Keeps it simple. 

At work I have to use visual studio, and it's just bloat.
Give me a text editor and a CL compiler anyday,

I follow that too.

Gedit with its terminal plugin and a few others makes it better than any IDE I have tried.

Vim of course, is the best text editor.

---

### Post by bhadotia on 2008-04-11
how do we open setup.exe in wine . Also I  don't have windows (so I also don't have a C drive either) . Also can please tell me , if I directly paste the tcwin45 folder from cd to my desktop , would it run with wine (I used to do this when i had windows (pasted the folder to C drive ) and the IDE worked)?

---

### Post by LaRoza on 2008-04-11
> **bhadotia said:**
> how do we open setup.exe in wine . Also I  don't have windows (so I also don't have a C drive either) . Also can please tell me , if I directly paste the tcwin45 folder from cd to my desktop , would it run with wine (I used to do this when i had windows (pasted the folder to C drive ) and the IDE worked)?

Right click the .exe and open it with Wine.

---

### Post by vinu76jsr on 2008-04-11
you just have to install the w9ne through synaptic and gnome will configure itself to get along with wine and then just double click on any exe file it will run in wine. but frankly you must try anjuta

---

### Post by pedro_orange on 2008-04-11
When you install wine.
(and do winecfg)

You will notice, if you go into your home dir and press Ctrl+H (Show hidden files/folders) a folder called .wine

Go in there, you'll see a folder called drive_c. This is where wine installs stuff to by default (unless u wanna change it etc)

Thats what I meant.

If you can't choose an item from the GUI to open it, at the bottom should be a drop down where you can type in your own command. Just put "wine" in there and it'll open in wine.

---

### Post by bhadotia on 2008-04-11
I already have anjuta but it never seems to work . In tc io simply used to hit ctrl+f9 to compile a program and run it , how do we do that in anjuta.  

I installed a build plugin but after typing a program when I try to compile it using build the option remains inactive even after saving the program. 



So can you please give me some guidance on how to install the anjuta help doc ; it is not installed by default and I don't know how to install it from its website

---

### Post by pedro_orange on 2008-04-11
You can install Anjuta and it's help/dev docs from Synaptic Package Manager

---

### Post by bhadotia on 2008-04-11
Alright tnanx guys . I am at present downloading eclipse (have already downloaded geany). I will try my luck with all of them . And if none of them work i will try to run tc with wine (which I am also downloading at present).

---

### Post by samjh on 2008-04-11
> **bhadotia said:**
> Is there an ide for practicing c/c++ languages like tc 0r tcwin45 (in windows) in linux (ubuntu) .I am doing my first course in c language , so i need a simple learning enviornment like tc etc. Also the book which i am following also recommends tc for beginners.

By TC and tcwin45, I presume Turbo C?

Although I usually take an open-minded stance on these things (I started learning C using Turbo C), I have to say that **you should avoid Turbo C**.  It is not compliant with the ISO C standard, which means you will have problems if you try to use the code for Turbo C on other compilers like GCC.  You will also learn bad habits and functions that won't work on most other compilers.

As others have suggested, just use Gedit with plugins, and learn to compile the source code using the command-line.

Gedit should already be installed on your Ubuntu system.  Just go to Application -> Accessories -> Text Editor.

To install the Gedit plugins, open your terminal and type:
```
sudo apt-get install gedit-plugins
```

In Gedit, go to Edit -> Preferences -> Plugins tab, and then tick the Embedded Terminal option.  Then go to View in the main menu, and make sure the Bottom Pane is ticked also, so that you can see the terminal area beneath the editor.

If you right-lick on the terminal area, you can click on Change Directory to go directly to the same directory as the opened source file.

To install the appropriate compiler for C and C++, type this in the terminal:
```
sudo apt-get install build-essential
```

To compile C source code using gcc, where myprogram.c is your source file, do this:
```
gcc myprogram.c -o myprogram
```gcc = compiler
myprogram.c = your C source file
-o = output specifier option
myprogram = the name of the compiled executable file

To compile C++ source code, just use g++ instead of gcc.

To run the resulting program:
```
./myprogram
```

---

### Post by bhadotia on 2008-04-11
samjh that was really very helpful. Thank you very much. I  will start practicing the above procedure right a way.  



By the way, someone of you above said "you always virtualise windows enviornment on your linux box running tc".
What does that mean?

---

### Post by LaRoza on 2008-04-11
> **bhadotia said:**
> By the way, someone of you above said "you always virtualise windows enviornment on your linux box running tc".
What does that mean?

Run Windows in a VM like VirtualBox.

---

### Post by samjh on 2008-04-11
> **bhadotia said:**
> By the way, someone of you above said "you always virtualise windows enviornment on your linux box running tc".
What does that mean?

TC is a Windows-only program.  To run a Windows program on Linux, you need either an emulation layer or virtualisation.

Virtualisation is basically running Windows within Linux.  It's a "virtual machine" within your real machine.  Programs like VMWare and VirtualBox lets you do this.

An emulation layer doesn't run the entire Windows operating system, but forms a layer of compatibility so that when a Windows program tries to use Windows functions and resources on a Linux machine, it gets translated to the equivalent functions and resource for Linux.  A very popular emulation layer is Wine ([www.winehq.org](www.winehq.org)).

---

