---
title: "Newbie - Easy to Run, All-in-One IDE?"
date: 2012-05-21
forum: Programming Talk
---

### Post by mxg284 on 2012-05-21
New to Linux...got tired of Windows and switched over to Ubuntu 12.04 on an HP laptop.

I am an intermediate user of Microsoft Visual Studio and write in C++ for most of my classes.  I normally just use the Microsoft lab computers but would like to be able to practice or even import some of those files into an IDE on Ubuntu.

I have searched the net and tried several IDEs already like CodeBlocks and QT Creator.  While the UI is very nice and similar to what I am used to, I had so much trouble getting them to compile my codes...I always had to download this and then download that based off of the problems others had also.

I am hoping to find an all-in-one IDE that I can download and be done with it.  No more packages to install ect...
Does such an IDE exist?  

Thank you

---

### Post by infectedorganism on 2012-05-21
I'm not really "qualified" to answer this question, but I will anyways, ha.

Have you tried Geany?

---

### Post by QIII on 2012-05-21
Install build-essential for all the background stuff.  I use Netbeans and Eclipse.

---

### Post by adit on 2012-05-22
> I had so much trouble getting them to compile my codes
It is not a problem with the IDE.  The problem is you have not installed the necessary libraries.
Type in terminal
```
sudo apt-get install build-essential
```
This will install the necessary libraries for C and C++.
Second step is you have to configure your IDE to use the installed libraries.
Then only your IDE will work.
The most commonly used IDEs are:
1) Eclipse
2) Netbeans
3) Code Blocks
Use any one of the above. If you still have any problems post it here. We are ready to help.

---

### Post by roelforg on 2012-05-22
You do realise that msvc++ code will not compile on linux, right?
There's no win32 api as it (like the name hints) is specific to windows.
Cause iirc msvs users generally do stuff that depends on win32.
If i'm right, look into libs as qt and gtk, the nice this is that there are windows versions of them as well.

---

### Post by mxg284 on 2012-05-22
Yes, I understand I cannot import Microsoft Visual Studio into these IDEs.  I have been copy and pasting my code into the linux based ones and compiling however.

I have Geany and it is the only one so far to not give me a headache...most likely because it is just like a terminal, not really an IDE.

I would absolutely love to run Eclipse on here.  I have it downloading now from the software center, but understand I have to install the C++ library.  Is this what you mean I have to do in the terminal Adit?

Thank you for the help so far.

---

### Post by roelforg on 2012-05-22
> **mxg284 said:**
> Yes, I understand I cannot import Microsoft Visual Studio into these IDEs. I have been copy and pasting my code into the linux based ones and compiling however.
 
I have Geany and it is the only one so far to not give me a headache...most likely because it is just like a terminal, not really an IDE.
 
I would absolutely love to run Eclipse on here. I have it downloading now from the software center, but understand I have to install the C++ library. Is this what you mean I have to do in the terminal Adit?
 
 
Thank you for the help so far.
 
I meant that win32 CODE (it doesn't matter if you wrote it in msvs or even in notepad) isn't gonna compile under linux unless you're cross-compiling for windows.

---

### Post by mxg284 on 2012-05-22
Is this something I can do with Eclipse?...Work on the program on Linux and then stick it on a flash drive and open it and continue working on it on MSVS and vice versa?

---

### Post by roelforg on 2012-05-22
> **mxg284 said:**
> Is this something I can do with Eclipse?...Work on the program on Linux and then stick it on a flash drive and open it and continue working on it on MSVS and vice versa?
 
 
Well, (don't take this the wrong way) an IDE is nothing more then a plain texteditor (like gedit, nano or notepad) with a lot of bells and whistles.
It's the compilers and system api that matter.
 
As long as you use standard c++ calls (e.g nothing that needs windows.h or derivative) and 3rd party libs (like gtk and qt) and you take versions for win with you, you could.
Simpler would be to use something like [portable ubuntu](http://sourceforge.net/projects/portableubuntu/) and work in, what basically is, a native linux environment while on windows and just edit the files directly when on your linux system.

---

### Post by mxg284 on 2012-05-22
Ah I understand.  Well before I get ahead of myself, once I have installed Eclipse, is there a terminal command for the C++ library I can install?
 
Also, could I also please get a step by step for directing Eclipse to that installed library?

---

### Post by roelforg on 2012-05-22
> **mxg284 said:**
> Ah I understand. Well before I get ahead of myself, once I have installed Eclipse, is there a terminal command for the C++ library I can install?
 
Also, could I also please get a step by step for directing Eclipse to that installed library?
 
```

sudo apt-get install build-essential

```
will install everything you need for c/c++ dev.
If you want to dev in gtk (glade + gtk+-3.0 are dead easy, IMO) as well, you need this:
```

sudo apt-get install libgtk-3-dev

```

---

### Post by mxg284 on 2012-05-22
OK, have that installed, created a new project, but I'm sure there are some settings that need adjusted, as I cannot even select the run program sequence...

In fact, I don't even see a selection option for C++ anywhere while creating a new file.

---

### Post by roelforg on 2012-05-22
> **mxg284 said:**
> OK, have that installed, created a new project, but I'm sure there are some settings that need adjusted, as I cannot even select the run program sequence...

In fact, I don't even see a selection option for C++ anywhere while creating a new file.

Keep in mind that i program using gedit and a terminal.
I write my own Makefiles and know where i link to.
I attached a simple glade app that shows you a simple hello world!
I added a precompiled binary, it's compiled on ubuntu 11.10 32bit.

Here's a good tut, the only problem is that the signals aren't always in the same section as the tut says (example: The destroy signal is in GtkWidget, not GtkObject)
[http://blog.borovsak.si/2009/09/glade3-tutorial-1-introduction.html](http://blog.borovsak.si/2009/09/glade3-tutorial-1-introduction.html)

---

### Post by Cardale on 2012-05-22
Gedit or Kate will do the job fine.

---

### Post by QIII on 2012-05-22
Text editors work fine unless you do complex collaborative projects, need powerful debugging and analysis tools, are under tight schedule deadlines from your clients and, well, want to make a crap load of money.

---

### Post by adit on 2012-05-23
> In fact, I don't even see a selection option for C++ anywhere while creating a new file.
How did you install eclipse?
Remember there are several versions of eclipse each version designed to compile a particular language.
For C++ development you have to install the package called 'eclipse-cdt'. In the terminal type
```
sudo apt-get install eclipse-cdt
```
Then inside eclipse, you can see options to create a new C++ project.
Try the above. If any problems post them here.

---

### Post by roelforg on 2012-05-23
> **QIII said:**
> Text editors work fine unless you do complex collaborative projects, need powerful debugging and analysis tools, are under tight schedule deadlines from your clients and, well, want to make a crap load of money.
 
If i want powerfull debugging and analysis i use gdb and gprof.
I can do more with gdb than most gui debuggers can.

---

