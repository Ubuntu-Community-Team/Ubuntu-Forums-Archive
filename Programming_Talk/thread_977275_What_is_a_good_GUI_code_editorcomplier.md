---
title: "What is a good GUI code editor/complier?"
date: 2008-11-10
forum: Programming Talk
---

### Post by riahc3 on 2008-11-10
Hey

Im looking for something like Visual Studio 6.0 for Linux (because I havent found a good guide to install VS 6.0 with Wine). With a GUI frontend. More specific, for C programming language.

---

### Post by keplerspeed on 2008-11-10
I would highly recommend eclipse, it is the best open source IDE I have used. other option is the bluefish editor, however I have only used bluefish for html so im not sure if it has c support.

---

### Post by riahc3 on 2008-11-10
Can I write/comply C code in Eclipse?
And Bluefish (As far as I see) allows you to type code, check syntaxis, but it doesnt let you comply and run the complied program.

---

### Post by Kilon on 2008-11-10
I would recommend taking a look at NETBEANS as well, it is mainly a JAVA IDE but supports C++ as well. It is very easy to use and you will find alot of documentation for it. It is said that is easier than eclipse but also lack feature that eclipse has.

[http://www.netbeans.org/images/v6/1/features/cpp.png](http://www.netbeans.org/images/v6/1/features/cpp.png)

[http://www.netbeans.org/features/cpp/index.html](http://www.netbeans.org/features/cpp/index.html)

---

### Post by ad_267 on 2008-11-10
Yes you can use Eclipse for C. Other options are Code::Blocks, Anjuta and NetBeans. This is covered in the [Programming Tools and References for Many Languages]("http://ubuntuforums.org/showthread.php?t=796493") sticky in this forum, so you shouldn't have to start a new post.

---

### Post by dgoosens on 2008-11-10
have a look at the Mono project:
[http://www.mono-project.com/Main_Page]("http://www.mono-project.com/Main_Page")

---

### Post by thelinuxer on 2008-11-10
If you wanna get serious with GUI programming IMHO your best option is Qt (a C++ library). They have created a new IDE fully integrated and a real eye candy! It's also cross platform so your code will work on *nix, windows, mac ...etc
You can download it from here

[http://trolltech.com/developer/qt-creator/qt-creator#download-qt-creator](http://trolltech.com/developer/qt-creator/qt-creator#download-qt-creator)

Tutorials for Qt4 is here

[http://doc.trolltech.com/4.4/tutorials.html](http://doc.trolltech.com/4.4/tutorials.html)

You'll need Qt4 development headers, they are already on Ubuntu repos. 

Good luck

---

### Post by riahc3 on 2008-11-10
Why would I need tutorials for qt4? I want something that is like Visual Studio and is easy to use.

---

### Post by curvedinfinity on 2008-11-10
riahc3, I'd honestly not suggest any IDEs. I learned programming using an IDE (actually, Visual Studio), but as it turns out, using the command line is simply simpler. Try installing g++:
```
sudo apt-get install g++
```
Edit your program in Ubuntu's text editor, GEdit, which has built in syntax highlighting, auto-tabbing, file tabs, and a nice find and replace. Then compile your app with g++ like this:
```
g++ -o HelloWorld main.cpp
```
This command will turn main.cpp into an executable named HelloWorld.

If you want to link to a library and compile another file too:
```
g++ -o HelloWorld main.cpp Class.cpp -lSDL
```
Where -lSDL links to the libSDL library.

If .h files are included in those files, they will be dealt with properly -- no need to add them to the command.

Also, using the command line is also great because it makes the project easier to work with on different OSs. Pretty much all OSs have g++, so you'll be set to compile on other systems with a setup like the above.

---

### Post by LaRoza on 2008-11-10
> **riahc3 said:**
> Why would I need tutorials for qt4? I want something that is like Visual Studio and is easy to use.

Then use Visual Studio ;) For IDE's, editors, and GUI toolkits (including GUI designers), see: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

There is no $800 IDE for non free, restricted environments for Linux that is in common use or that I know of.

---

### Post by directhex on 2008-11-10
> **LaRoza said:**
> Then use Visual Studio ;) For IDE's, editors, and GUI toolkits (including GUI designers), see: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

There is no $800 IDE for non free, restricted environments for Linux that is in common use or that I know of.

[http://www.omnicore.com/en/xdevelop.htm](http://www.omnicore.com/en/xdevelop.htm)

You're welcome!

---

### Post by ad_267 on 2008-11-10
> **riahc3 said:**
> Why would I need tutorials for qt4? I want something that is like Visual Studio and is easy to use.

If you're not willing to learn anything new, why are you using Ubuntu? Nobody can use Visual Studio straight away without having learnt something about programming and how to use it.

---

### Post by directhex on 2008-11-10
> **ad_267 said:**
> If you're not willing to learn anything new, why are you using Ubuntu? Nobody can use Visual Studio straight away without having learnt something about programming and how to use it.

Well, if he wanted to, he could develop .NET apps on Windows/VS.NET and deploy them to Ubuntu.

I suspect though that there's a little misunderstanding going on - he wants an IDE with the usual features like code completion and breakpoints, but is being told to look at tutorials for a C++ toolkit, which is... a change in scope. Especially if he wants an integrated GUI designer (though I think the QT development packages include a GUI designer)

---

### Post by doorman on 2008-11-10
My vote goes to Code::Blocks and NetBeans!

They're so great I can't decide which one to use ;)

If you're moving from VS, I presume you want to design GUI apps, but I dare to suggest you to first do a couple of GUI-less apps and to get to know the linux a little bit more before trying to create GUI apps - it'll simplify your life! :)

---

### Post by LaRoza on 2008-11-10
@OP Linux is very diverse. There is no One Ring to bind everything together. This means, there is no single IDE which does what you want, for various reasons (on of them being the GUI toolkit isn't part of Linux). So you have to pick your tools. You need your compiler (gcc, for C), your GUI toolkit and designer (GTK+, for C), and your editor, which can be an IDE.

---

### Post by thelinuxer on 2008-11-11
> **riahc3 said:**
> Why would I need tutorials for qt4? I want something that is like Visual Studio and is easy to use.

Well if you are a Visual C 6.0 developer then u'll find Qt to be really really easy to learn and use. It's *almost* as easy as Dotnet and Java. Have a look at it you won't be disappointed.

Watch this

[http://www.youtube.com/watch?v=U7yje3D1UM4](http://www.youtube.com/watch?v=U7yje3D1UM4)

---

### Post by riahc3 on 2008-11-12
Im not "migrating" from VS.

I would use VS in Ubuntu if it was supported under WINE but I can't seem to be able to install it.

I would love a VS clone for Linux.

---

### Post by riahc3 on 2008-11-17
Bumping up.

I simply want something like VS; Install, open up the program, make a project, make a source file, write code, comply, and run. I don't want to "learn" anything (I put "" because I find it hard to believe that I have to learn something to migrate from VS to this).

---

### Post by thelinuxer on 2008-11-17
> **riahc3 said:**
> Bumping up.

I simply want something like VS; Install, open up the program, make a project, make a source file, write code, comply, and run. I don't want to "learn" anything (I put "" because I find it hard to believe that I have to learn something to migrate from VS to this).

I guess there are a lot of people here who gave you lots of options. If you don't want to learn anything new then , I am very sorry , you're out of luck. I don't know why you find it hard, I always have to learn new stuff with every new project! It's not like you reached the level where you know all what you need to know! Consider the options you have and if you need any help the community will help you.

---

### Post by pp. on 2008-11-17
> **riahc3 said:**
> Bumping up.

I simply want something like VS; Install, open up the program, make a project, make a source file, write code, comply, and run. I don't want to "learn" anything (I put "" because I find it hard to believe that I have to learn something to migrate from VS to this).

If it is imperative that it is exactly like the product you have learned to use, then use that product. Every other product is guaranteed to be different from the one you're using now. Every later version of the same product also is practically guaranteed to be different.

Er - the verb you want is 'compile', not 'comply'; hence 'compiled', not 'complied'.

---

### Post by Kilon on 2008-11-17
> **riahc3 said:**
> Bumping up.

I simply want something like VS; Install, open up the program, make a project, make a source file, write code, comply, and run. I don't want to "learn" anything (I put "" because I find it hard to believe that I have to learn something to migrate from VS to this).

I have used NETBEANS did all the things you described and did not touch the help file or any tutorial. I find NETBEANS very easy to use, it has a very good GUI deisgner and overall it impressed me with its capabilities.

---

### Post by directhex on 2008-11-17
> **riahc3 said:**
> Bumping up.

I simply want something like VS; Install, open up the program, make a project, make a source file, write code, comply, and run.

That's not a problem. There are plenty of IDEs to chose from. Eclipse is a popular choice. I think even Monodevelop will let you edit C, though the version in Ubuntu is a bit old.

> I don't want to "learn" anything (I put "" because I find it hard to believe that I have to learn something to migrate from VS to this).

That, however, IS a problem. If you want to write the same apps you do already, well, tough - you simply don't have the same APIs available to you (no doubt the APIs you're using right now are tied to Windows, e.g. winapi for drawing GUIs). You've got no real choice here, barring the rather hideous option of linking against WineLib - you've got to learn some new APIs, such as GTK+, to productively produce apps

---

### Post by riahc3 on 2008-11-18
Maybe Ive explained something wrong.

I just want this to do simple stuff such as 

i=0
do{
i=i+1;
}until(i=5)

Nothing serious as this is just for class. 

I don't need (or want) to learn new APIs such as GTK+ which is why I want something simple and easy like VS.
I haven't tried VS 2008 under Wine; Might give it a try and see if it installs (I hope).

---

### Post by dgoosens on 2008-11-18
> **riahc3 said:**
> Maybe Ive explained something wrong.

I just want this to do simple stuff such as 

i=0
do{
i=i+1;
}until(i=5)

Nothing serious as this is just for class. 

I don't need (or want) to learn new APIs such as GTK+ which is why I want something simple and easy like VS.
I haven't tried VS 2008 under Wine; Might give it a try and see if it installs (I hope).

again...
you can code VB style in Mono, if you must... (but you might want to try a "real" language...)

[http://www.mono-project.com/Language_BASIC]("http://www.mono-project.com/Language_BASIC")

you will however have to learn about the new libraries (no WinForms etc.)

Mono = install, code, compile, run...
easy as pie.

---

### Post by directhex on 2008-11-18
> **dgoosens said:**
> again...
you can code VB style in Mono, if you must... (but you might want to try a "real" language...)

[http://www.mono-project.com/Language_BASIC]("http://www.mono-project.com/Language_BASIC")

you will however have to learn about the new libraries (no WinForms etc.)

Mono = install, code, compile, run...
easy as pie.

But you're still relying on the person at the other end having .NET 2.0+ and the VB 8.0 runtime installed

---

### Post by slavik on 2008-11-18
> **directhex said:**
> But you're still relying on the person at the other end having .NET 2.0+ and the VB 8.0 runtime installed
I use Anjuta for bigger C projects and Geany for single file stuff.

---

### Post by directhex on 2008-11-18
> **slavik said:**
> I use Anjuta for bigger C projects and Geany for single file stuff.

Yeah, I used to use Anjuta a while back.

Short answer to what the OP needs:

Install "mingw32" package

Use "i586-mingw32msvc-gcc" compiler

e.g.
```
jms@osc-franzibald:/tmp$ cat hello.c 
#include <stdio.h>
  
  main()
  {
    for(;;)
        { 
            printf ("Hello World!\n");
        }
  }

jms@osc-franzibald:/tmp$ gcc -o hello.bin hello.c 
jms@osc-franzibald:/tmp$ file hello.bin 
hello.bin: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped
jms@osc-franzibald:/tmp$ i586-mingw32msvc-gcc -o hello.exe hello.c 
jms@osc-franzibald:/tmp$ file hello.exe 
hello.exe: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit
jms@osc-franzibald:/tmp$ wine hello.exe 
Hello World!

```

Any editor (including Anjuta, if memory serves) should let you pick the compiler of your choice - i586-mingw32msvc-gcc is that compiler.

---

### Post by riahc3 on 2008-11-18
:( Still people do not understand me....

I want to write/run simple and standard C code/programs. In VS, I select Win32 Console Application and from there a new C/C++ Source File. I simply write my code such as:

i=0
do{
i=i+1;
printf ("%d",i);
}until(i=5)

then press F5 and simply comply/run my code.

---

### Post by dgoosens on 2008-11-18
> **riahc3 said:**
> :( Still people do not understand me....

I want to write/run simple and standard C code/programs. In VS, I select Win32 Console Application and from there a new C/C++ Source File. I simply write my code such as:

i=0
do{
i=i+1;
printf ("%d",i);
}until(i=5)

then press F5 and simply comply/run my code.



please do take TWO minutes and take a look at the mono-project

---

### Post by tarps87 on 2008-11-18
If what you want any IDE will probably do it. I'd suggest using Eclipse or Netbeans, both are in the repositories and both will compile and run your code. (Although I think run is ctrl+f11 :))
There are differences it the librarys used in Linux and you can't escape that but to answer you question have a look at Eclipse or Netbeans.

On a side note I may pay off to also write some code in a text pad and use the command line to compile, this is not necessary but it will help in the long run

(This is assuming you mean C and C++ not a microsoft variant)

---

### Post by directhex on 2008-11-18
> **dgoosens said:**
> please do take TWO minutes and take a look at the mono-project

Which still won't help him with C coursework

---

### Post by directhex on 2008-11-18
> **riahc3 said:**
> :( Still people do not understand me....

I want to write/run simple and standard C code/programs. In VS, I select Win32 Console Application and from there a new C/C++ Source File. I simply write my code such as:

i=0
do{
i=i+1;
printf ("%d",i);
}until(i=5)

then press F5 and simply comply/run my code.

And you're still not understanding the solution is in front of you.

Install mingw32. This contains a compiler for Windows. Install geany, it seems a reasonable enough simple IDE. Install wine. You'll need this to run your Windows apps.

Build, Set Includes & Arguments. Change the "gcc" to "i586-mingw32msvc-gcc" in the top two entries, and change the bottom one to
```
mv "%e" "%e".exe && wine "%e"
```

F9 to build, click Execute to run. The Compile button (F8 ) won't do enough to run, don't use it. Or, if you want the convenience, go back to Set Includes & Arguments and remove the '-c' from the Compile setting.

---

### Post by curvedinfinity on 2008-11-18
riahc3, try this:
[http://storage.curvedinfinity.com/Project.zip](http://storage.curvedinfinity.com/Project.zip)

[list=1]
[*]unzip.
[*]open Applications->Accessories->Terminal
[*]drag install.sh into the terminal
[*]enter your password, and enter Y when prompted
[*]double click compile.sh to compile main.cpp into "executable"
[*]drag executable into the terminal window
[*]press enter to run it
[*]edit main.cpp in the normal text editor -- you can set the normal text editor to do syntax highlighting, automatic tabbing, and all the other normal programming junk.
[/list]

That's everything an IDE does.

---

### Post by lifestream on 2008-11-19
People aren't listening to riahc3
He asked for something very simple. He is learning to program, and you guys are only complicating the matter.

riahc3, give Geany a try. I'm going to make a short video to show you how simple Geany is. You just open it, type stuff, compile, build, execute. That's it. Very simple. I'll post here when I complete the video.

---

### Post by lifestream on 2008-11-19
Here you go.
[http://www.youtube.com/watch?v=ZBjqn2wrQAA](http://www.youtube.com/watch?v=ZBjqn2wrQAA)
Damn, did it get all blurry on youtube or what ;p

I hope you find Geany to be simple enough for a student.\
All you have to do is:
 Projects -> Add new
     name your project and say what folder to put it in
 Write your code and save it
     Build -> Compile
    Build -> Build
    Build -> Execute.

Then you will see that windows-like cmd window show up with your program :)

---

