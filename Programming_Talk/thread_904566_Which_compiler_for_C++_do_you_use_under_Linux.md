---
title: "Which compiler for C++ do you use under Linux?"
date: 2008-08-29
forum: Programming Talk
---

### Post by Shadowmeph on 2008-08-29
I might be asking the question Wrong a while back I was using windows and started reading the book C++ primer third edition and would do the exercises using Bloodsheds Dev-C++ 4 compiler  I am now a strict Linux user and since I am going to restart teaching myself C++ again I am wondering which compilers/texted editors others are using because I am doubting that the bloodshed Dev C++ compiler text editor combination will work in Hardy So any suggestions would be helpful for a beginer like me

---

### Post by nrs on 2008-08-29
Dev-C++ isn't a compiler, it's an IDE that utilizes mingw, a Windows port of GCC.

---

### Post by LaRoza on 2008-08-29
The sticky answers all your questions.

g++ for the compiler (gedit + plugins for editor, you can use it from the terminal plugin)

Or any IDE of your choice.

---

### Post by ilrudie on 2008-08-29
gcc/g++ is the way to go.

---

### Post by happysmileman on 2008-08-29
Generally all C++ compiling is done with g++, and all C compiling is done with gcc, it's the standard, I don't even know of any others for Linux except the Intel compiler (which AFAIK costs money).

Dev-C++ uses a windows port of g++ anyway, so you'll basically be using the same compiler that you were using on Windows, but I think it may perform better on Linux and get more updates.

---

### Post by Shadowmeph on 2008-08-29
> **LaRoza said:**
> The sticky answers all your questions.

g++ for the compiler (gedit + plugins for editor, you can use it from the terminal plugin)

Or any IDE of your choice.

ok well I have gedit and the gedit-plugins installed and I can open it by typeing ( in terminal) gedit but what about the g++ acoring to my synaptic pacage manager it is installed but I am not sure how to load it up
Oh and By the way Thank you for helping/pointing me in the right dirrection

---

### Post by signifer123 on 2008-08-29
You could also look at KDevelop. It's pretty much the linux version of Visual Studio.
VDK Builder I never tried. And GNOME has Ajunta..
And Eclipse works on both platforms.

Open a terminal, and call 'g++ sourcefile'
 It will save the output to a.out, add '-o outputname' to change what the executable is saved to.

You should probably become familiar with makefiles as well.


I personally use GEdit and a terminal though.

---

### Post by dfreer on 2008-08-29
> **Shadowmeph said:**
> ok well I have gedit and the gedit-plugins installed and I can open it by typeing ( in terminal) gedit but what about the g++ acoring to my synaptic pacage manager it is installed but I am not sure how to load it up
Oh and By the way Thank you for helping/pointing me in the right dirrection

Kate and notepad++ are both great text editors you can use when writing your code, I prefer them over gedit.

---

### Post by mike_g on 2008-08-29
> ok well I have gedit and the gedit-plugins installed and I can open it by typeing ( in terminal) gedit but what about the g++ acoring to my synaptic pacage manager it is installed but I am not sure how to load it up
Oh and By the way Thank you for helping/pointing me in the right dirrection
I am sure the answer to that must be in the sticky. something like:
**sudo aptitude install build-essential**
then tpo compile:
**g++ myprog.c**
to run:
**./a.out**

---

### Post by ilrudie on 2008-08-29
> **happysmileman said:**
> Generally all C++ compiling is done with g++, and all C compiling is done with gcc, it's the standard

There is some confusion here.  Many people believe gcc stands for the gnu c compiler but these days its actually the gnu compiler collection.  One of the compilers in the collection is g++ and it can be invoked by calling gcc on a .cpp file.

[http://gcc.gnu.org/onlinedocs/gcc-4.3.2/gcc/G_002b_002b-and-GCC.html#G_002b_002b-and-GCC](http://gcc.gnu.org/onlinedocs/gcc-4.3.2/gcc/G_002b_002b-and-GCC.html#G_002b_002b-and-GCC)

---

### Post by LaRoza on 2008-08-29
> **Shadowmeph said:**
> ok well I have gedit and the gedit-plugins installed and I can open it by typeing ( in terminal) gedit but what about the g++ acoring to my synaptic pacage manager it is installed but I am not sure how to load it up
Oh and By the way Thank you for helping/pointing me in the right dirrection

Oh, in the menu's "gedit" is labelled "Text Editor", so you can use that.

If you are going to use the Terminal Plugin, make sure the bottom pane is visible.

To use g++, see the sticky for a step by step guide.

I see this is becoming a "what IDE" thread with people giving random recommendations. The sticky has text editor and IDE thread, contribute to that.

---

### Post by jespdj on 2008-08-29
Another nice, small and easy editor / IDE is [Geany](http://geany.uvena.de/).

---

### Post by LaRoza on 2008-08-29
> **LaRoza said:**
> 
I see this is becoming a "what IDE" thread with people giving random recommendations. The sticky has text editor and IDE thread, contribute to that.

> **jespdj said:**
> Another nice, small and easy editor / IDE is [Geany](http://geany.uvena.de/).

Yes, I know. It is in the thread about IDE's!

---

### Post by raedbenz on 2008-08-29
try NETBEANS.
it works fine for on Ubuntu

---

### Post by StOoZ on 2008-08-29
Using g++ compiler, with the latest Netbeans IDE :guitar:

---

### Post by jimi_hendrix on 2008-08-29
i use gedit with plugins for fast use then i use geany for debugging because it highlights where the errors are then i use g++ for compiling in terminal because i cant get geany's exicute thing to work

---

### Post by LaRoza on 2008-08-29
Everybody, read what I wrote. It is silly to go over what is already in a list in an easy to find thread!

If the thread is missing information, please contribute to it.

---

### Post by samjh on 2008-08-29
> **Shadowmeph said:**
> I might be asking the question Wrong a while back I was using windows and started reading the book C++ primer third edition and would do the exercises using Bloodsheds Dev-C++ 4 compiler  I am now a strict Linux user and since I am going to restart teaching myself C++ again I am wondering which compilers/texted editors others are using because I am doubting that the bloodshed Dev C++ compiler text editor combination will work in Hardy So any suggestions would be helpful for a beginer like me

You can use Gedit.  In Gnome, go to Applications -> Accessories -> Text Editor.
(In Kubuntu, use Kate. See the KDE menu.)

I highly recommend installing and enabling the Terminal plugin.  Install using this command in the terminal: ```
sudo apt-get gedit-plugins
```...and then enable the plugin in Gedit by going to Edit -> Preferences -> Plugins -> tick the Embedded Terminal box.  Then enable the bottom panel, by going to View -> tick Bottom Pane.

To use g++, you need to install the build-essential package:
```
sudo apt-get install build-essential
```

Here's an example on compiling a program using g++, assuming that your source file is myprogram.cpp, and you're in the same directory as that file:
```
g++ myprogram.cpp -o myprogram
```...this will produce an executable file named, myprogram.


I've lost count how many times I've posted these instructions. ;)

---

