---
title: "Alternative to MS Visual C++ Express/Studio"
date: 2008-09-06
forum: Recurring Discussions
---

### Post by Spoodt on 2008-09-06
Hi. I've been using Xubuntu ever since Vista crashed on my laptop while I was in another country, far away from my restore disk. So far, I like it. 

I've entered into an Intro to Programming in C class, that uses Microsoft's Visual C++ software to compile their codes and what not. Because of a nasty turn of events, I couldn't get their software, cant't attend the lab that teaches you how to use it in the first place, and have a pretty good feeling that MS Visual C++ Express/Studio isn't very Xubuntu friendly. I talked to my instructor, and she said that anything will do as long as it can churn out programs that will run on windows machines like the ones at the university.

I've been doing research for a couple of nights, hearing about gcc and eventually emacs. I just spent the last three hours studying the emacs tutorial, and then this one here: [http://www.linuxjournal.com/article/5765](http://www.linuxjournal.com/article/5765) Also, I heard somewhere that emacs aren't bad and that vim is good. If so, I hope vim has a comparable tutorial...

I feel pretty overwhelmed. I don't really know what I'm doing. Most guides assume you know how to work gcc and gdb. I'm not a programmer, but I would like to be one.

Who, What, When, Where, Why, and How? :shock:

---

### Post by forger on 2008-09-06
> I talked to my instructor, and she said that anything will do as long as it can churn out programs that will run on windows machines like the ones at the university.
Since she hasn't restricted to as to which language to use, make it in Perl :D

Any chance she accepts a command with command line arguments?
You could then make it using an IDE such as **geany** or **eclipse** (Applications > Add/Remove)

Or codeblocks: [http://www.codeblocks.org/](http://www.codeblocks.org/)

---

### Post by Spoodt on 2008-09-06
Um, Its a C class, so it can't really be anything else. :/ 

Well, the whole class will entail us making programs that will run on the MS command prompt using for the most part, standard libraries, if that helps. What exactly are those programs?

---

### Post by cmay on 2008-09-06
hi.
i use geany as the main editor since its simple. it works great on xubuntu too. there is for bigger projects a advantage in using kdevelop.

you should try pop in the programming sector at these forums also.

good luck to you with the programming.

---

### Post by Spoodt on 2008-09-06
Alright, I will give geany a try. 

Wait, you mean search for 'pop'?

---

### Post by forger on 2008-09-06
Geany and Eclipse and Code::Blocks and Anjuta are [IDE software]("http://en.wikipedia.org/wiki/Integrated_development_environment")
And.. No, he meant to try asking in Development and programming: [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)
Specifically, Programming talk: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Spoodt on 2008-09-06
Ah, good call.

---

### Post by Spoodt on 2008-09-06
(Taken from Absolute Beginner Talk)

Hi. I've been using Xubuntu ever since Vista crashed on my laptop while I was in another country, far away from my restore disk. So far, I like it.

I've entered into an Intro to Programming in C class, that uses Microsoft's Visual C++ software to compile their codes and what not. Because of a nasty turn of events, I couldn't get their software, cant't attend the lab that teaches you how to use it in the first place, and have a pretty good feeling that MS Visual C++ Express/Studio isn't very Xubuntu friendly. I talked to my instructor, and she said that anything will do as long as it can churn out programs that will run on windows machines like the ones at the university.

I've been doing research for a couple of nights, hearing about gcc and eventually emacs. I just spent the last three hours studying the emacs tutorial, and then this one here: [http://www.linuxjournal.com/article/5765](http://www.linuxjournal.com/article/5765) Also, I heard somewhere that emacs aren't bad and that vim is good. If so, I hope vim has a comparable tutorial...

I feel pretty overwhelmed. I don't really know what I'm doing. Most guides assume you know how to work gcc and gdb. I'm not a programmer, but I would like to be one.

Who, What, When, Where, Why, and How?

I've been recommended Eclipse, Code::Blocks, and a few other IDE. Not that I have any experience using any of them, but from your experience, which one would you suggest?

Spoodt is online now Report Post   	Edit/Delete Message

---

### Post by kjohansen on 2008-09-06
since the rest of the class is using Visual Studio Express you should check out Monodevelop.

```

sudo apt-get install monodevelop

```

---

### Post by rnodal on 2008-09-06
I would recommend [Codeblocks]("http://www.codeblocks.org/").
If you are going to be doing windows development then just install [Mingw]("http://www.mingw.org/") before installing Codeblocks and then follow this tutorial: 

[Codeblocks tutorial]("http://www.cprogramming.com/code_blocks/").

That site should also prove to be useful in C/C++ programming.

I hope that helps. If you need more help then just post your questions.

-r

---

### Post by mike_g on 2008-09-06
If you are doing an introduction to C class then it is unlikely that you will be writing programs that are OS dependent. As the programs will also be small you could use a simple text editor such as gedit. Emacs and Vim have lots of powerful features, but for what you are doing you shouldent have to learn them unless it is something that you want to do. If you are working with a single source file then it is simple to compile via the command line:
```
gcc -Wall sourcefile.c
```
gcc will then create a compiled file in the same directory called a.out which you can run by typing:
```
./a.out
```If you have to use multiple source files then you might want learn how to create a makefile for your prog.

---

### Post by StOoZ on 2008-09-06
I also recommend code::blocks.
the only issue I found with it is :
[http://forums.codeblocks.org/index.php/topic,9123.0.html]("http://forums.codeblocks.org/index.php/topic,9123.0.html")

:(
still didnt figure out a solution for it. (im new to C::B , used netbeans before)

---

### Post by kaspar_silas on 2008-09-06
Surely you could use different development suites at home and at uni.  Doing this exact thing can massively help you to be flexible. (You will start to understand what the development suite's buttons are doing)  

I use Netbeans with the c++ plug in. When my XP or Vista using colleagues need to use my programs normally I just recompile on a window machine. 

Possibly your course might use window specific programs but I would doubt it as it's only a introduction.

---

### Post by LaRoza on 2008-09-06
> **Spoodt said:**
> I've been doing research for a couple of nights, hearing about gcc and eventually emacs. I just spent the last three hours studying the emacs tutorial, and then this one here: [http://www.linuxjournal.com/article/5765](http://www.linuxjournal.com/article/5765) Also, I heard somewhere that emacs aren't bad and that vim is good. If so, I hope vim has a comparable tutorial...

Yes, Vim is much better than Emacs...

[http://ubuntuforums.org/showthread.php?t=23169](http://ubuntuforums.org/showthread.php?t=23169)

> 
I feel pretty overwhelmed. I don't really know what I'm doing. Most guides assume you know how to work gcc and gdb. I'm not a programmer, but I would like to be one.

Then perhaps you could start with another language, some languages are well suited for non-programmers. 

[http://ubuntuforums.org/showthread.php?t=796494](http://ubuntuforums.org/showthread.php?t=796494)

> 
I've been recommended Eclipse, Code::Blocks, and a few other IDE. Not that I have any experience using any of them, but from your experience, which one would you suggest?


And you will only get more personal suggestions here. It is futile.

See: [http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224)

---

### Post by rnodal on 2008-09-06
> **StOoZ said:**
> I also recommend code::blocks.
the only issue I found with it is :
[http://forums.codeblocks.org/index.php/topic,9123.0.html]("http://forums.codeblocks.org/index.php/topic,9123.0.html")

:(
still didnt figure out a solution for it. (im new to C::B , used netbeans before)

That is weird because it works just fine with me. Which version are you using? Believe me, code sensing or whatever you want to call it is a must have feature for any IDE I use including also syntax highlight. 

-r

---

### Post by nsche on 2008-09-06
gvim/vim/vi vs emacs is a religous argument.  There are groups that love either and there are a log of successful unix/linux programmers that have used either or both or neither.  Mike_g has the right idea.  At your stage of the game you really do not need to worry about complicated IDEs etc.  Concentrate on the language and concepts of programming and you will learn more.  Most will not endorse C as a language for learning programming concepts but you have what you have.

On gcc, ```
gcc -Wall file.c -o file
``` will create an executable named file that can then be run (hopefully).  The Wall turns on all warnings.  As far as gdb, I have worked as a professional programmer on unix systems for 25+ years and usually did not use adb/kdb/dbx/gdb.  They are good sometimes but are not all that easy to learn.  Printf is your friend.

---

### Post by Spoodt on 2008-09-06
I'm really glad I've gotten all these responses, thanks people.

So far, the class is pretty easy, and yes the programs will be simple cli ones using standard libraries. I want to make sure that whatever I use now will be most useful to me later on. Right now, I am trying to figure out how to use the CDT on Eclipse. So far, most tutorials  only for Java and CDT recources seem to be for older versions of eclipse and for those who nkow how to use it. From here, I think I might have to move on to Code::Blocks. I'm sure its possible, but time is very important to me.

---

### Post by Spoodt on 2008-09-06
My class requires me to compile executables for windows. What program will do that? Will gcc do that? When I search for it, all I find is information about mingw32, which is FOR windows.

---

### Post by cwsnyder on 2008-09-06
gcc will compile for Windows, if you want it to do so, but you will require the correct headers and libraries to make it a Windows executable.  The default headers and libraries installed under Xubuntu are for Linux, and specifically, Xubuntu.  This would be standard C and C++ code.

Mono will compile C# (pronounced 'see sharp') code, which is subtly different than C++ because it requires even more object orientation, but would compile under .NET Framework under Windows.

---

### Post by cheetaux on 2008-09-06
For a beginner, I would recommend using gedit as the text editor for your programs.  Use of an IDE (eclispe, etc. would be overkill for any projects you would do in class).

Note: be sure to install the GNU compilers, etc:
```
sudo apt-get install build-essential
```

To edit a program named helloworld.cpp for example:

```
gedit helloworld.cpp

```
To compile and link helloword:

```
g++ helloworld.cpp -o helloworld
```

(Note: be sure to install the GNU compilers, etc:)
sudo apt-get install build-essential

If your program requires several source files (for example, main.cpp, sub1.cpp, sub2.cpp) you can compile each file individualy then link the object files as shown below:

```
g++ -c main.cpp
g++ -c sub1.cpp
g++ -c sub2.cpp
g++ main.o sub1.o sub2.o -o program
```

An excellent discussion of C++ programming (including how to use the GNU C++ compiler on Linux) can be found in Bruce Eckels "Thinking in C++" books.  These books are available for free on his website:

[http://mindview.net/Books/TICPP/ThinkingInCPP2e.html]("http://mindview.net/Books/TICPP/ThinkingInCPP2e.html")

You should be able to copy your source code files onto a memory stick then recompile them at the university using Visual C++.

Hope this helps.

---

### Post by kaspar_silas on 2008-09-07
If you are writing the programs. Then as said above if you use the Monodevelop package it will produce executables that run under both OS. 

Or you could use the very basic online compiler
[http://www.codeide.com/]("http://www.codeide.com/")
which has two nice buttons marked compile4windows and compile4linux. 

As far as I know (I may well be wrong) I don't know of any Linux development suite that uses the windows libraries and headers (like windows.h). Hence if you are given example programs that use (or told to make programs using) windows specific libraries you are pretty stuck. There are always ways around or replacements libraries. But it probably won't help learning the basics of C if you have to constantly find these and debug your code at the same time. 

I would ask the teacher if they will use windows specific libraries. If yes then for the stake of learning it's probably worth putting that Vista back on as a dual boot.

---

### Post by bapoumba on 2008-09-07
Threads merged.

---

### Post by abdusamed on 2010-05-03
i can't do any c++ .. lol.. i have vim and build essential and kdevelop installed..none of them is able to compile or run the following code :-

```

#include <iostream.h>

int ()

{
int a;
cout<<"Please Enter Age\n";
cin>>a;
cout<<"Your age is \t"<<a
return 0;
}

```

---

### Post by mmix on 2010-05-03
mingw
[http://sourceforge.net/projects/mingw/files/](http://sourceforge.net/projects/mingw/files/)

---

### Post by MindSz on 2010-05-03
> **abdusamed said:**
> i can't do any c++ .. lol.. i have vim and build essential and kdevelop installed..none of them is able to compile or run the following code :-


What commands are you using to compile the code? Do you get an error messsage? If so, could you post it here, so we can help?

You might find more help in the "Programming Talk" forums...

Maybe this can be a starting point: [http://ubuntuforums.org/showthread.php?t=1470731](http://ubuntuforums.org/showthread.php?t=1470731)

---

### Post by abdusamed on 2010-05-07
> **MindSz said:**
> What commands are you using to compile the code? Do you get an error messsage? If so, could you post it here, so we can help?

You might find more help in the "Programming Talk" forums...

Maybe this can be a starting point: [http://ubuntuforums.org/showthread.php?t=1470731](http://ubuntuforums.org/showthread.php?t=1470731)


thanks.. now is working.. kinda.. After all the apps i downloaded, kdevelop, codilte, vgim... Geany seems to work the best.. or best alternative to visual c++.. Though i can't use #include <iostream.h> in the beginning which lets me leave out using "using std::cout" and all that.. but works great :)

---

### Post by MindSz on 2010-05-07
> **abdusamed said:**
> Geany seems to work the best

+1 for Geany here as well.

> **abdusamed said:**
> Though i can't use #include <iostream.h> in the beginning

I'm not much of a C++'er but I think only in C you include the '.h' ...so instead of ```
#include<iostream.h>
``` try to use ```
#include<iostream>
```

---

### Post by WinterMadness on 2010-05-08
netbeans. its typically seen as a java ide but they have a feature that will download a c++ compiler among many other ones you select.

Netbeans owns all. <---truth

---

