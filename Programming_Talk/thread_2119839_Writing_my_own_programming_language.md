---
title: "Writing my own programming language"
date: 2013-02-24
forum: Programming Talk
---

### Post by Pradipna on 2013-02-24
Hello, I have been working on this project for some months now and I  want to show it to other people. Basically speaking, it's a programming  language which can be compiled and ran using a virtual machine. Here's a  detailed explanation I wrote in my blog:


> 
So, in last blog post I gave small introduction to my current project  that I am working on. In this blog I want to release the first version  of my current project. You can grab it from here: [http://www.pradsprojects.com/despair.html](http://www.pradsprojects.com/despair.html)
So, this piece of software that I wrote is a system to write portable  programs. It has its own programming language and the program that are  compiled can be executed using a Virtual Machine. The system isn’t  mature and lot of things are lacking but I hope to develop it further in  the future.
 Let me talk a little about how this system works. You write a program  using its programming language (here’s the documentation of programming  language: [http://www.pradsprojects.com/despairLanguageDocumentation/index.html](http://www.pradsprojects.com/despairLanguageDocumentation/index.html))  then compile it using compiler tool that I have written. The compiler  generates a file with ‘.dbin’ extension which can be executed using the  Virtual Machine.
 I have created a small IDE for developing program for this system  which you can download it from the project site (the one that I gave you  on the top). IDE consist of editor to write and manage source code  (which is fairly basic at the moment, no syntax highlighting for the  moment sorry), a compiler to compile the source code and a virtual  machine to run the compiled file.
 Alternately, if you don’t want to create programs for the system but  want to run program created by others, you’re going to have to download  the VM from the project site. There are two types of VM for Windows OS:  interpreter version and JIT version (Dynamic Recompiler). The JIT  version is faster than interpreter version though I am still not very  happy with the JIT performance, I think it can be improved more. I will  port the JIT version to Linux later.
 I want to create the Virtual Machine for various different platforms  like android, iOS, MacOS etc so that the program written using  despairLanguage can be run in different platforms. Currently the VM  works in Windows and Linux.
 P.S: The software is open source and is on github. Links are on the project site.



So, I just wanted you guys to look at it and play around with it. Some feedbacks (good or bad) is highly appreciated.


Thanks!

---

### Post by schauerlich on 2013-02-25
So... it's C with some C++-isms on your own VM?

---

### Post by tehcavil on 2013-02-25
> **schauerlich said:**
> So... it's C with some C++-isms on your own VM?

^ this. skimmed documentation and why make another language if it looks so similar to c/c++? why would we use it over those languages?

---

### Post by JDShu on 2013-02-25
Guys, it's probably just an interesting exercise. Nobody is saying that we should suddenly use it :) Not every programming language effort needs to be ground breaking.

Personally I think it's a cool project and I'm sure OP will learn a lot. It's one of the long list of things I want to try one day.

---

### Post by Pradipna on 2013-02-26
> **JDShu said:**
> Guys, it's probably just an interesting exercise. Nobody is saying that we should suddenly use it :) Not every programming language effort needs to be ground breaking.

Personally I think it's a cool project and I'm sure OP will learn a lot. It's one of the long list of things I want to try one day.

Exactly! Thanks!

This project started out as a hobby. I had the idea about how compiler and low level stuffs work but I just wanted to take the challenge of implementing it. Then I starting to think , if I released it to public maybe someone will have good use of it.

So, the thing is I just wanted to create something that can create portable games. I want homebrew game devs to code and compile just once and that program can be run in various different platform. I will port the VM to most of the modern platform.

I don't know how to describe it, it just started it as a hobby, but now I want to develop it further and see how it evolves.

---

### Post by CptPicard on 2013-02-26
Hey, that's actually very, very classy compared to a lot of the "I'm going to write my own language/kernel/window manager" projects one see here that never amount to anything but dreams and hot air. My hat's off to OP :)

As a suggestion though, if you really are interested in writing languages for a portable VM and to get to something usable, why not work on top of the Java VM?

---

### Post by Pradipna on 2013-02-26
> **CptPicard said:**
> Hey, that's actually very, very classy compared to a lot of the "I'm going to write my own language/kernel/window manager" projects one see here that never amount to anything but dreams and hot air. My hat's off to OP :)

As a suggestion though, if you really are interested in writing languages for a portable VM and to get to something usable, why not work on top of the Java VM?

Thanks!

Writing my own VM was half the fun. It's my creation so I can tweak it in anyway I like. I know nuts and bolts of the system and how it works and can change it to my liking. 
Also, my VM design is more cleaner that JavaVM design. :P

---

### Post by r-senior on 2013-02-26
> **CptPicard said:**
> My hat's off to OP :)
+1

Great work! Getting a new language accepted and used widely is unlikely but what a great project to have under your belt.

=D>=D>=D>

---

### Post by loell on 2013-02-26
OP actually knows his stuff, looking forward for the next version of the IDE. :)

---

### Post by KdotJ on 2013-02-26
Had a good read of your project on the way home from work... I must say I am very impressed.

You've gone to great lengths to do all this plus the documentation and examples etc. Completely not was I was expecting to see after all the other "Creating my own <XXX>" (as CptPicard has already mentioned).

If you have done all of this yourself, then you should feel very proud, regardless of where it goes.

---

### Post by Drakx on 2013-02-26
> **Pradipna said:**
> Hello, I have been working on this project for some months now and I  want to show it to other people. Basically speaking, it's a programming  language which can be compiled and ran using a virtual machine. Here's a  detailed explanation I wrote in my blog:





So, I just wanted you guys to look at it and play around with it. Some feedbacks (good or bad) is highly appreciated.


Thanks!

Genuinely impressed! Looks like a really fun project and I can see a lot of potential for it.

This is going to be one of them projects I keep an eye on.

---

### Post by Pradipna on 2013-02-26
> 
Had a good read of your project on the way home from work... I must say I am very impressed.

You've gone to great lengths to do all this plus the documentation and  examples etc. Completely not was I was expecting to see after all the  other "Creating my own <XXX>" (as CptPicard has already  mentioned).

If you have done all of this yourself, then you should feel very proud, regardless of where it goes.     
> 
Genuinely impressed! Looks like a really fun project and I can see a lot of potential for it.

This is going to be one of them projects I keep an eye on.
Thanks guys, it means a LOT to me.

I am getting feedbacks and bug reports (just fixed some bugs this morning :) ) from people and it feels so good. Keeps me motivated to improve this project even more.
Thanks!

---

### Post by nvteighen on 2013-02-27
Ouch! Why isn't there a 32 bit version so that I can test it out? :(

---

### Post by Virtuality314 on 2013-02-27
This looks incredibly interesting. I'm wondering on how you actually made the compiler - is it from scratch or something else?

---

### Post by Pradipna on 2013-02-27
> **Virtuality314 said:**
> This looks incredibly interesting. I'm wondering on how you actually made the compiler - is it from scratch or something else?
 
I wrote it from scratch. The reason for that is to know what it takes to actually build a working compiler.

---

### Post by Pradipna on 2013-02-27
> **nvteighen said:**
> Ouch! Why isn't there a 32 bit version so that I can test it out? :(

You can build the project from source in 32 bit machine and it should work. (Except for the JIT version of the VM which emits x86_64 code to the buffer)

The editor and compiler should compile without a problem. Here's the github:
[https://github.com/Prads-/despair_editor](https://github.com/Prads-/despair_editor)
[https://github.com/Prads-/despair_compiler](https://github.com/Prads-/despair_compiler)

But you may run into some problems while compiling VM. VM is just the set of classes, and you have to plug the UI component to it in order to run it. I have included only the UI component for Windows OS just to give example of how to plug UI to the VM. So first get VM source code from here:
[https://github.com/Prads-/despair_vm](https://github.com/Prads-/despair_vm)

Then start a new QT Gui project and add all the sources in that project. Next open the build.h file and comment out these:
#define DEBUG_DESPAIR
#define USING_MICROSOFT_COMPILER 
#define BUILD_FOR_WINDOWS

And uncomment this:
#define BUILD_FOR_UNIX

Next thing you do is, replace the main.cpp, mainwindow.cpp and mainwindow.h that QT generated with these:
main.cpp: [http://pastebin.com/90uEE47J](http://pastebin.com/90uEE47J)
mainwindow.cpp: [http://pastebin.com/2JHv1uy7](http://pastebin.com/2JHv1uy7)
mainwindow.h: [http://pastebin.com/QympVCys](http://pastebin.com/QympVCys)

And you should be good to go...

---

### Post by danniel on 2013-03-03
> **Pradipna said:**
> So, I just wanted you guys to look at it and play around with it. Some feedbacks (good or bad) is highly appreciated.

The next step should be making an IDE for it. Have a look at this open-source Eclipse project: [http://www.eclipse.org/Xtext/](http://www.eclipse.org/Xtext/)

---

### Post by Pradipna on 2013-03-04
> **danniel said:**
> The next step should be making an IDE for it. Have a look at this open-source Eclipse project: [http://www.eclipse.org/Xtext/](http://www.eclipse.org/Xtext/)

It does have it's own IDE. But the editor is just too basic for now (doesn't even support syntax highlight, oops lol).

---

