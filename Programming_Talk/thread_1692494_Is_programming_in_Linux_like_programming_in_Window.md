---
title: "Is programming in Linux like programming in Windows?"
date: 2011-02-21
forum: Programming Talk
---

### Post by GTMoraes on 2011-02-21
Short question - Uh, I think the thread title says it all.

Long question - I'm in Computer Science course, and the Programming teacher uses Windows tools to teach us. She named some open-source programs for me so I could program with, such as Code::Blocks. But what I'm really wondering is:

If I go through the programming class with Linux, will it be the same thing as using Windows, or will she need to teach me differently from the Windows-Users class?

If I wasn't clear, please expose it so I can detail more.

Thank you

P.S.: I mean "same thing" by coding means, it's C/C++.

---

### Post by bouncingwilf on 2011-02-21
Basic "console" programming is reasonably similar but when it comes to GUI programming i.e.Windows API Vs. gnome (gtk+) [http://www.gtk.org/](http://www.gtk.org/) or KDE (QT)  [http://qt.nokia.com/products/](http://qt.nokia.com/products/) then there are some philosophical differences in the model to such an extent that "translating" an App from one to the other is not straightforward ( unless that is, you use the same tools on both systems - ie use gtk+ , wxwidgets or QT on Windows). 

There is a wealth of information out there (almost too much) but in my opinion, the simple answer is no, they are not the same and programming fundamentals apart, you would need to learn two separate "styles"

Bouncingwilf

---

### Post by ve4cib on 2011-02-21
That question can really be answered in two ways from where I'm sitting.

1- The basic concepts of "how to program" and "how to think like a programmer" are applicable no matter what you're programming.  Whether it's a Linux kernel module, a Windows application, something for an embedded system without an OS on it at all, javascript for a website, or anything else you can think of.

Concepts like iteration (using loops to do the same job over and over), conditionals (if-statements to control program flow), recursion (calling a function from itself), data structures (how you represent data inside the program), and suchlike are almost universal.  It doesn't matter what you're programming for, those fundamental concepts will always come up and to be a good programmer you need to have a good grasp of those.

Provided your course is teaching you good fundamentals then no, you won't need to re-learn much other than OS- or domain-specific libraries.


2- Every programming domain and programming language has their own quirks that you do need to learn to be a proficient programmer in that domain.  So from that perspective you do need to re-learn some stuff when moving from Windows to Linux.

The example in an earlier post is very good: if you're programming a GUI application for Windows chances are you'll be using Visual Studio and writing your code in C#.NET.  Windows has a very specific GUI API that you need to use in order to write "proper" Windows applications.  Linux on the other hand uses Qt (the KDE-style UI toolkit) or GTK (the Gnome-style UI toolkit).  Both are very, VERY different from Windows.  So to change from a Windows application programmer to a Linux application programmer you will have  a lot of learning to do in order to translate the look and feel of your application.

However, the back-end data-structures, program flow, error-checking, and the like will translate very easily between Linux and Windows.  So while you worry about learning new operating system-specific libraries your good grasp of the fundamentals of programming will lessen your burden significantly.



**tl;dr version**
The basics of programming -- things like loops, if-statements, recursion, standard algorithms, and good data structures -- are universal to all programming domains.  It's only the specifics like what system libraries you can call and IDEs you will use that will change between programming in Linux and Windows.

---

### Post by Zugzwang on 2011-02-21
Actually, it might we wise to ask your teacher if she is teaching plain ISO C or C++. If the answer is "yes", then you should be fine with Linux. If she says "no", she is using some extensions and/or libraries which are likely not to be cross-platform. If the answer is "what is that? ISO-C++?" then there's a 99% chance that the answer is "no".

---

### Post by efikkan on 2011-02-21
If the course is a basic introduction to programming then I don't think there will be any emphasis on anything outside ISO C/C++, but maybe some debugging i Visual Studio.

Code::Blocks is basically the same on any platform, but it should be possible to use the visual studio compiler on Windows, but I don't see any reason to do that.

Personally I now do all my development in GNU/Linux, and most of it using gedit and terminal (vi or emacs works as well, but I prefer gedit). I've been developing most of my years in Windows, but I don't miss it.

---

### Post by forrestcupp on 2011-02-21
You need to ask if you're going to end up learning Windows API. If you are, you'll have to end up using Windows.

---

### Post by GTMoraes on 2011-02-21
Wow, lot of nice answers. Feels good to have somewhere to rely when you're starting something.
Thank you everybody :)

Okay, I think I got it. Basically, the language I'll learn will, mostly, work with both platforms. However, if I need to go deep into this, I'll have to choose either Windows or Linux, right?

If I choose Linux (I'll only choose Windows if I don't have an option), will it be easy to learn again if I need to code for Windows?

Oh by the way, a douche here with a Mac - Just to clarify: He isn't a douche becuase he has a Mac. That said, let's proceed - and he has some program that auto-detects bugs or something, using cute arrows to show where the error is and which code reefers to one another.. Mostly eye-candy, but in the end, helps alot with big codes. (He uses Composite C, or something)

Thank you everybody again for such nice answers. Surely I can count with the community and when I learn enough, I'll do my best to help users like me right now :)

P.S.: No WINE love for Windows API's? :)
P.P.S.: I don't know if I'm walking straight to a epic battle between programs, but which one is better for me (Starting programmer, knows nothing yet but learns FAST): 
Code::Blocks or Eclipse?

----------
btw, she said we could use Open-Source tools for the class

---

### Post by Shpongle on 2011-02-21
Hey , I would say stay with a text editor and terminal for now. gedit has always worked great for me. Why well the reason being you will learn about the underlying processes such as compiling and linking etc. Also if you use a text editor YOU will have to find the errors in your code and will learn better than having the IDE do the work for you.

---

### Post by GTMoraes on 2011-02-21
Good idea, my brother did that with me when I was 12 and trying to learn PHP. Worked quite right, but I was too young and just wanted to play CS. oh well.

So, how it is supposed to work? I type the codes in gedit and save it on the proper format then use "make filename"? I've tried to do such, but it keeps saying (in a free translation) "There is no program installed for achives code object".

```

#include<stdio.h>
#include<math.h>

int main(){
    float H,D,R,A,V;
    printf("informe o valor de H:");
    scanf("%f",&H);
    printf("informe o valor de D:");
    scanf("%f",&D);
    
    R=D/2;
    A=3.14*R*R;
    V=A*H;
    printf("\nO volume e :%f",V);
    getchar();
    getchar();
    return(0);
}

```
Not sure about what it does, a friend copied it to my pendrive. Works for him.

---

### Post by Vaphell on 2011-02-21
no need to use makefiles when you have 1 tiny file with code
```

gcc my_program.c -o prog

```

gcc is a compiler and you tell it to take my_program.c file, compile it to a binary file named prog
To run the compiled program type
```
./prog
```

that program calculates parameters of a cylinder, which is obvious from looking at the equations. It declares bunch of variables of 'floating point number' type, prompts user fo diameter and height, calculates radius, area of the top/bottom circle and volume of the cylinder. Volume is printed out.

---

### Post by slooksterpsv on 2011-02-21
> **GTMoraes said:**
> ...

Okay, I think I got it. Basically, the language I'll learn will, mostly, work with both platforms. However, if I need to go deep into this, I'll have to choose either Windows or Linux, right?  - That depends, you can use Cross-Platform toolkits for GUI elements like FLTK, GTK+ (which is cross platform), etc. Or you can use the Windows API, or .NET Framework, but you are limited to Windows. Cocoa is limited to Mac.

> 

If I choose Linux (I'll only choose Windows if I don't have an option), will it be easy to learn again if I need to code for Windows?



Sure, you can always use VisualBasic for quick windows programs. Its easy, fast, and  has GUI Drag and drop. Or you can look at a program like REALBasic for complete cross-platform programming (does Linux, Mac, and Windows).

> 

Oh by the way, a douche here with a Mac - Just to clarify: He isn't a douche becuase he has a Mac. That said, let's proceed - and he has some program that auto-detects bugs or something, using cute arrows to show where the error is and which code reefers to one another.. Mostly eye-candy, but in the end, helps alot with big codes. (He uses Composite C, or something)



Yeah XCode is nice, and Objective-C is amazing, but still limited to Mac only. Eclipse is a nice editor for Linux and you can do java, python, c, c++, etc. in it. With C/C++ you just need the CDT Plugin for Eclipse.

> 

P.P.S.: I don't know if I'm walking straight to a epic battle between programs, but which one is better for me (Starting programmer, knows nothing yet but learns FAST): 
Code::Blocks or Eclipse?


Eclipse, is my vote, I love Eclipse. Code::Blocks never did work right for me.

---

### Post by deconstrained on 2011-02-21
> **GTMoraes said:**
> Oh by the way, a douche here with a Mac - Just to clarify: He isn't a douche becuase he has a Mac. That said, let's proceed - and he has some program that auto-detects bugs or something, using cute arrows to show where the error is and which code reefers to one another.. Mostly eye-candy, but in the end, helps alot with big codes. (He uses Composite C, or something)
The "douche" you are referring to was probably using XCode tools. With any luck he'll end up developing iOS apps for a nickel a line and giving Apple 30% of his profits. :p

Any debugger worth its salt can do exactly what you described here - showing where in the code it's messing up. Also, simply setting your compiler flags to print more warning messages can help you eliminate scores of common mistakes and write more clean, strict, standards-compliant code.

As for a development environment:

Many people swear by Eclipse; it's certainly an industrial-strength (and open-source) IDE/SDK, and it's Java so it runs on just about any operating system or platform (Windows, Linux, Mac, Solaris, etc). I personally don't like it; I'm more of an Emacs person. But learning how to use it should be a rewarding experience.

---

### Post by trent.josephsen on 2011-02-21
Is it C, C++, or both?

---

### Post by GTMoraes on 2011-02-22
Jeez, this community is amazing. I'll come back to bother you guys more often (:

I'll try first to use gedit + terminal. Feels like I truly learn this way.
But if I ever need a development environment or something, I think I'll go with Eclipse. It looks.. "comfortable".
But erm.. I'm still a bit confused. I want to use the GTK+ (it's cross-platform, right) but um.. how do I know I'm using it? (Hey, take it easy on me, I want to learn how to program :) )

Thank you to every single one of y'all for helping me and for making this great community. Thank you

[SIZE="1"]P.S.: [offtopic] Just to make things clear, the Douche guy is a very smart guy when it comes to programming and such (I can't talk with him about life, I can't stand him). He knows Objective C (sorry slooksterpsv haha), java, delphi and other languages. He's actually learning the Windows Phone 7 language so he can make apps for it. He works with/for apple or something, I recall him saying something about it and iphone apps. What makes him a douche is the fact that he keeps saying how much he have, how much his things costed, how much he earns and so, even when it doesn't fit into the conversation. So, he's a douche (:[/SIZE]

-------------------------
HEY, THE CODE I POSTED HERE NOW WORKS!! It looks like it cannot run directly from my pendrive (NTFS), so I copied it to my home folder, compiled (is that right? I "compiled" it using "gcc Test.c -o test") and ran there. Worked like a charm! Woohoo my first working program :)

-----------------------------------------------------------------------------------------------------------------------

> **trent.josephsen said:**
> Is it C, C++, or both?
We're going to start with C, then, through the course, go to C++

---

### Post by Vaphell on 2011-02-22
you learn any language/library in the same way. You look for tutorials of 'hello world' type and for good documentation which describes how things work and what built-in tools are available.

e.g. gtk
[http://library.gnome.org/devel/gtk-tutorial/2.90/](http://library.gnome.org/devel/gtk-tutorial/2.90/)
[http://www.gtk.org/documentation.html](http://www.gtk.org/documentation.html)

either way i don't think you are ready to use GUI libraries now. They are quite complicated to understand right off the bat, you are better off writing console programs for some time first to understand the very foundations of programming.

---

### Post by slooksterpsv on 2011-02-22
> **GTMoraes said:**
> ...

But erm.. I'm still a bit confused. I want to use the GTK+ (it's cross-platform, right) but um.. how do I know I'm using it? (Hey, take it easy on me, I want to learn how to program :) )



Oh you'll know when you do includes like GTK.h or that, and use gtk_init or anything that prefixes GTK, but you'll know even before that cause you'll learn GTK+ and then know what you want to program and set it all up to compile with GTK

> 

Thank you to every single one of y'all for helping me and for making this great community. Thank you


Linux is about the community, not who can make the higher buck, bigger dollar, most $$$; it's about people and helping others. =D That's why we all are here, we love to help people and even learn things ourselves =D

> 
...

HEY, THE CODE I POSTED HERE NOW WORKS!! It looks like it cannot run directly from my pendrive (NTFS), so I copied it to my home folder, compiled (is that right? I "compiled" it using "gcc Test.c -o test") and ran there. Worked like a charm! Woohoo my first working program :)

...

Nope you won't be able to compile a program on Windows and run it on Linux, unless you use WINE, they compile a different way. So for example, any program you make and want to transfer from platform to platform, you'll have to compile it on that platform. (Someone correct me if I'm wrong)

Also when you get into directives, you can see some powerful stuff e.g.:

```

...
#ifdef WIN32
 //do some windows stuff here
 ...
#elseif LINUX
 //do some linux stuff here
 ...
#elseif MACOSX
 //do some mac os x stuff here
 ...
#else
 //if none of those fit, do something else hwere
 ...
#endif
...

```

To make compiling easier, anyways that's beyond the scope of this topic, but yeah.

---

### Post by Tony Flury on 2011-02-22
> **Zugzwang said:**
> Actually, it might we wise to ask your teacher if she is teaching plain ISO C or C++. If the answer is "yes", then you should be fine with Linux. If she says "no", she is using some extensions and/or libraries which are likely not to be cross-platform. If the answer is "what is that? ISO-C++?" then there's a 99% chance that the answer is "no".

I would go so far as to say - If the answer is "what is ISO C++" then find another course.

---

### Post by slooksterpsv on 2011-02-22
> **Tony Flury said:**
> I would go so far as to say - If the answer is "what is ISO C++" then find another course.

I whole-heartedly agree!

---

### Post by deconstrained on 2011-02-22
> **GTMoraes said:**
> But erm.. I'm still a bit confused. I want to use the GTK+ (it's cross-platform, right) but um.. how do I know I'm using it? (Hey, take it easy on me, I want to learn how to program :) )
GTK is an API for writing graphical user interfaces that run on Linux/Unix systems. The interfaces of nearly all GNOME applications are based on GTK. So, no, GTK isn't 100% cross-platform, and though it can run on just about any kind of Unix, and non-natively on Mac OS X, no Windows.

If you want truly 100% cross-platform code that doesn't need to be "ported" (meaning, adapted to use the native API of whatever system it's meant for), learn & write code in Java. Java has its own graphical interface API, which, while not very pretty-looking, is practical and works fine.

---

### Post by fct on 2011-02-22
I suggest some tools that might help you:

[http://cppcheck.sourceforge.net/](http://cppcheck.sourceforge.net/) -> Automatic C/C++ error checker. Can detect many things, from simple ones like unused variables to more complicated, like memory leaks.

[http://clang.llvm.org/](http://clang.llvm.org/) -> C/C++ compiler. While incomplete for C++, it's quite advanced and is much more verbose on errors than gcc. It's also the one used in Xcode to compile objective-C on macs.

Also, if you're starting to learn programming, I suggest you **forget about GTK+**, the WIN32 API and so on till you start GUI programming. Toolkits are usually complicated enough to be left as the last topic on the course.

---

### Post by GTMoraes on 2011-02-22
Thank you guys for the answers, again! It's helping me a lot thru the class. I even compiled some codes the teacher told us to. I used gedit and terminal with gcc :)

> **Vaphell said:**
> 
....
either way i don't think you are ready to use GUI libraries now. They are quite complicated to understand right off the bat, you are better off writing console programs for some time first to understand the very foundations of programming.
That's what my programming teacher said to me today. I'll try to learn it when I feel comfortable programming in the console 


> **fct said:**
> I suggest some tools that might help you:

[http://cppcheck.sourceforge.net/](http://cppcheck.sourceforge.net/) -> Automatic C/C++ error checker. Can detect many things, from simple ones like unused variables to more complicated, like memory leaks.

[http://clang.llvm.org/](http://clang.llvm.org/) -> C/C++ compiler. While incomplete for C++, it's quite advanced and is much more verbose on errors than gcc. It's also the one used in Xcode to compile objective-C on macs.

Also, if you're starting to learn programming, I suggest you **forget about GTK+**, the WIN32 API and so on till you start GUI programming. Toolkits are usually complicated enough to be left as the last topic on the course.
You got it right, I've asked today about that in the class, and it's goint to be our last topic

I've got the cppcheck, it's pretty nice and helps a lot. Today I wrote a simple code for salary calculation, and I didn't declare a parameter (ironically, the income tax parameter). It was in the middle of one equation and no way I could find it. It pointed it out and helped me :) Thanks
About clang, installing it, I would use it by "replacing" gcc when compiling my codes?



> **deconstrained said:**
> GTK is an API for writing graphical user interfaces that run on Linux/Unix systems. The interfaces of nearly all GNOME applications are based on GTK. So, no, GTK isn't 100% cross-platform, and though it can run on just about any kind of Unix, and non-natively on Mac OS X, no Windows.
....
In a gross comparation, is GTK+ like Visual Basic?

> **slooksterpsv said:**
> Oh you'll know when you do includes like GTK.h or that, and use gtk_init or anything that prefixes GTK, but you'll know even before that cause you'll learn GTK+ and then know what you want to program and set it all up to compile with GTK
Oh I got it. #include<gtk.h> right?, I thought it was another way to compile things or some kind of IDE name. I was looking for it on Programs Center :P

> **slooksterpsv said:**
> 
Also when you get into directives, you can see some powerful stuff e.g.:

```

...
#ifdef WIN32
 //do some windows stuff here
 ...
#elseif LINUX
 //do some linux stuff here
 ...
#elseif MACOSX
 //do some mac os x stuff here
 ...
#else
 //if none of those fit, do something else hwere
 ...
#endif
...

```

To make compiling easier, anyways that's beyond the scope of this topic, but yeah.
Hm.. that means with a single source code, depending on which platform I'm running the compiler, it compiles in the right, compatible way?

--------
Man, surely I got my back covered when it comes to programming. Thank you guys for all the support, wish I had people like y'all in the class
Thanks

---

### Post by cgroza on 2011-02-22
> **GTMoraes said:**
> 
Hm.. that means with a single source code, depending on which platform I'm running the compiler, it compiles in the right, compatible way?


The compiler produces almost the same machine code, it just produces an exe for Windows and a executable file on Unix. Your statement is true only if the program does not use platform specific libraries, features, code.

---

### Post by ve4cib on 2011-02-22
> **GTMoraes said:**
> In a gross comparation, is GTK+ like Visual Basic?

No.

Visual Basic is a programming language used by some Windows programmers.  (There are VB compilers for other platforms, but by-and-large it is a Windows-dominated programming language.)

GTK+ is a library that can be used to create GUI applications in C, C++, Python, etc...  I think there may even be GTK+ libraries you can use with C# and VB when working under Windows.

---

### Post by fct on 2011-02-22
> **GTMoraes said:**
> About clang, installing it, I would use it by "replacing" gcc when compiling my codes?

Right.

---

### Post by Redache on 2011-02-22
> Visual Basic is a programming language used by some Windows programmers. (There are VB compilers for other platforms, but by-and-large it is a Windows-dominated programming language.)


Sorry to be anal, but I would say VB is more like a scripting language as it has a very strict attachment to Win32/.NET.

If you want some good help whilst writing your code you should look into compiler options. For example if I wanted to know about everything in my code that isn't right or could lead to issues later on I'd use clang/gcc as follows:

```
gcc -Wall -pedantic -std=c89 -o myprogram myprogram.c
```

Wall shows any warnings that the compiler gives (they are suppressed by default) and pedantic means that the compiler gets picky about your code. std refers to the standard of the C you are using, which in this case is C89, it's just a standard defined for that language. The main ones you'll use for C are 89,99 and ansi. For C++ 98 is probably the only one you'll ever set (and is default on the compilers).

-Wall -pedantic are options in gcc,g++ and clang. I recommend using clang because clangs error reporting is **very** nice and helpful. 

I also recommend learning to use lint, which I believe is splint on Ubuntu. It checks your code quality and reports any potential issues, like memory leaks or any code that is inefficient. Combining lint with the compiler options will help you become a good programmer and teach you a lot about the little niggly things that you can play with to improve your code.

I hope I've helped and good luck learning to program.

---

### Post by GTMoraes on 2011-02-23
> **Redache said:**
> ...
If you want some good help whilst writing your code you should look into compiler options. For example if I wanted to know about everything in my code that isn't right or could lead to issues later on I'd use clang/gcc as follows:

```
gcc -Wall -pedantic -std=c89 -o myprogram myprogram.c
```

Wall shows any warnings that the compiler gives (they are suppressed by default) and pedantic means that the compiler gets picky about your code. std refers to the standard of the C you are using, which in this case is C89, it's just a standard defined for that language. The main ones you'll use for C are 89,99 and ansi. For C++ 98 is probably the only one you'll ever set (and is default on the compilers).

-Wall -pedantic are options in gcc,g++ and clang. I recommend using clang because clangs error reporting is **very** nice and helpful. 

I also recommend learning to use lint, which I believe is splint on Ubuntu. It checks your code quality and reports any potential issues, like memory leaks or any code that is inefficient. Combining lint with the compiler options will help you become a good programmer and teach you a lot about the little niggly things that you can play with to improve your code.

I hope I've helped and good luck learning to program.

Thanks for the tip.
I'm getting clang right now, as you and fct recommended it.
One simple question: I know using the line you said above compiles using gcc, but how do I use clang for compiling?

And for lint, it's Splint on Ubuntu, yeah. 
How.. um.. how do I use it? splint myprogram.c?

Thanks for all the tips, that's a nice kickstart for me. Keep 'em coming :)

---

### Post by ve4cib on 2011-02-23
> **Redache said:**
> Sorry to be anal, but I would say VB is more like a scripting language as it has a very strict attachment to Win32/.NET.

I'm going to have to disagree with you about the scripting language part.  VBscript is a scripting language, but visual basic isn't.  VB, like C#, compiles to a binary.  Well, a pseudo-binary that gets run through a virtual machine, just like Java.  So if Java is a scripting language then so is VB, I suppose.

As for it being very strictly tied to Windows, I agree.  I even said that.  But there are VB compilers for other platforms.  They're just very rarely used.

---

### Post by slooksterpsv on 2011-02-23
> **marcellarhughes said:**
> i learn this thread, i encountered most likely similar...great ideas share. :)

OT, but I'll try to post something relevant to the topic after, but I love threads like this, no one's getting flamed, it's a great share of ideas, and we're all learning (at least I and the OP are I know).

Back to the topic:

Umm... the awesome thing about Ubuntu is if you're unsure of how to use a program and have a terminal window open, you can type in:
```

man <command>
#example
man splint

```

But you use splint like so:
```

splint main.c

```

EDIT: For a future fun/test/whatnot of your skills at coding, they did start a Beginners Programming Challenge *x* on here. Here's #1 - [http://ubuntuforums.org/showthread.php?t=876479](http://ubuntuforums.org/showthread.php?t=876479)

I do them sometimes just to see if I can, and it's fun.

---

### Post by GTMoraes on 2011-02-23
> **slooksterpsv said:**
> OT, but I'll try to post something relevant to the topic after, but I love threads like this, no one's getting flamed, it's a great share of ideas, and we're all learning (at least I and the OP are I know).

Back to the topic:

Umm... the awesome thing about Ubuntu is if you're unsure of how to use a program and have a terminal window open, you can type in:
```

man <command>
#example
man splint

```

But you use splint like so:
```

splint main.c

```

EDIT: For a future fun/test/whatnot of your skills at coding, they did start a Beginners Programming Challenge *x* on here. Here's #1 - [http://ubuntuforums.org/showthread.php?t=876479](http://ubuntuforums.org/showthread.php?t=876479)

I do them sometimes just to see if I can, and it's fun.
wow, that "man" thing is great! Very clever and useful.
Thanks for the tip, I would never discover this by myself

That Beginners Programming Challenge is nice, I look forward joining in when I have some basic knowledge :)

---

### Post by deconstrained on 2011-02-24
Just a correction: 

I've been told GTK can be made to work on Windows. Still though, writing interfaces for Windows and for Unix/Linux environments can be a pain, because there are certain conventions (i.e. for placement of buttons, window margins, menu names etc) that apply to different operating systems, so there's nevertheless still nothing truly 'cross-platform' about GUI development, regardless of which API you use.

---

### Post by GTMoraes on 2011-02-24
> **deconstrained said:**
> Just a correction: 

I've been told GTK can be made to work on Windows. Still though, writing interfaces for Windows and for Unix/Linux environments can be a pain, because there are certain conventions (i.e. for placement of buttons, window margins, menu names etc) that apply to different operating systems, so there's nevertheless still nothing truly 'cross-platform' about GUI development, regardless of which API you use.

Oh i see. Can't make greek and trojans happy :)
---

I changed the course. I'm up to a free one (Over here in Brazil, the free, public universities are the best ones) and they'll start with JAVA, instead of C.
So hehe.. which programs do you guys recommend for java programming?

---

### Post by fct on 2011-02-25
eclipse and netbeans.

---

### Post by ve4cib on 2011-02-25
> **GTMoraes said:**
> I changed the course. I'm up to a free one (Over here in Brazil, the free, public universities are the best ones) and they'll start with JAVA, instead of C.
So hehe.. which programs do you guys recommend for java programming?

Honestly I just use Geany.  The terminal pane at the bottom lets me compile and run the program.  Nothing too fancy.

If you're doing anything really complex (dealing with dozens of clases, interfaces, UIs, etc...) then something like Netbeans or Eclipse would probably be useful.  But for basic intro-level coursework those kinds of IDEs are probably overkill.

IMO you're better off using a simple text editor and a terminal window when you're starting off.  Complex IDEs do a lot of extra work behind the scenes, and general WAY more files than you need for your purposes (build files, project files, etc...).  Keep things simple to start and you can build from there.

---

### Post by GTMoraes on 2011-02-25
> **ve4cib said:**
> Honestly I just use Geany.  The terminal pane at the bottom lets me compile and run the program.  Nothing too fancy.

If you're doing anything really complex (dealing with dozens of clases, interfaces, UIs, etc...) then something like Netbeans or Eclipse would probably be useful.  But for basic intro-level coursework those kinds of IDEs are probably overkill.

IMO you're better off using a simple text editor and a terminal window when you're starting off.  Complex IDEs do a lot of extra work behind the scenes, and general WAY more files than you need for your purposes (build files, project files, etc...).  Keep things simple to start and you can build from there.
So, for both C and Java programming, the basic gedit and terminal will do the trick? How do I compile a Java program? (I didn't even start to learn Java by now, will do 03/15)

---

### Post by ve4cib on 2011-02-25
Yes, for C, C++, Java, Python, Perl, Javascript, etc, etc... Geany or Gedit will do just fine.  That's what I tend to use anyway.  Like I said though, for particularly large projects -- especially in a business setting -- a larger, more complex IDE is often very useful.  But when you're just starting off, or for anything that's half a dozen files or less a basic text editor with syntax highlighting is really all you need.


Just like you use gcc to compile C, you use javac to compile java.

You'll need to install a Java SDK (Software Development Kit or something like that) package.  "apt-get install openjdk-6-sdk" will do the trick.  That will include the Java Runtime Environment (JRE) and SDK (compiler, libraries, etc...).

Java is a little different than C in that it does not produce an executable in machine code.  When you compile your java program you'll get a *.class file.  That file is what's called "byte code."  It's designed to be run through a low-level interpreter -- the Java Virtual Machine.

The idea is that you can write and compile your program on any platform (Windows, Linux, Mac, Haiku, Solaris, etc...), and then run it on any machine with the JVM installed.  "Compile once, run anywhere" is the motto.

So, now that I've got the vague, hand-wavey descriptions out of the way let's look at an actual example.

**HelloWorld.java**
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

It's your standard Hello World app, done in Java.  Note that the class name and the file name are the same -- this is **required** in Java.

To compile and run your program you'd do the following: (and the ls commands are simply to show what files are created)

```

$ cd my-code-directory
$ ls .
HelloWorld.java
$ javac HelloWorld.java
$ ls .
HelloWorld.class    HelloWorld.java
$ java HelloWorld
Hello World!
$
```

The "javac" command compiles the specified class, along with any other classes in your source directory that are used by it.  If you've got multiple classes I find it's easiest to just say "javac *.java" rather than manually enter every class name.

To execute the program you use the "java" command.  You provide it the name of the class that contains your main method.  In this case main is in my HelloWorld class, so I say "java HelloWorld"  Note that capitalization is important; everything is case-sensitive.

---

### Post by GTMoraes on 2011-02-26
> **ve4cib said:**
> Yes, for C, C++, Java, Python, Perl, Javascript, etc, etc... Geany or Gedit will do just fine.  That's what I tend to use anyway.  Like I said though, for particularly large projects -- especially in a business setting -- a larger, more complex IDE is often very useful.  But when you're just starting off, or for anything that's half a dozen files or less a basic text editor with syntax highlighting is really all you need.


Just like you use gcc to compile C, you use javac to compile java.

You'll need to install a Java SDK (Software Development Kit or something like that) package.  "apt-get install openjdk-6-sdk" will do the trick.  That will include the Java Runtime Environment (JRE) and SDK (compiler, libraries, etc...).

Java is a little different than C in that it does not produce an executable in machine code.  When you compile your java program you'll get a *.class file.  That file is what's called "byte code."  It's designed to be run through a low-level interpreter -- the Java Virtual Machine.

The idea is that you can write and compile your program on any platform (Windows, Linux, Mac, Haiku, Solaris, etc...), and then run it on any machine with the JVM installed.  "Compile once, run anywhere" is the motto.

So, now that I've got the vague, hand-wavey descriptions out of the way let's look at an actual example.

**HelloWorld.java**
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

It's your standard Hello World app, done in Java.  Note that the class name and the file name are the same -- this is **required** in Java.

To compile and run your program you'd do the following: (and the ls commands are simply to show what files are created)

```

$ cd my-code-directory
$ ls .
HelloWorld.java
$ javac HelloWorld.java
$ ls .
HelloWorld.class    HelloWorld.java
$ java HelloWorld
Hello World!
$
```

The "javac" command compiles the specified class, along with any other classes in your source directory that are used by it.  If you've got multiple classes I find it's easiest to just say "javac *.java" rather than manually enter every class name.

To execute the program you use the "java" command.  You provide it the name of the class that contains your main method.  In this case main is in my HelloWorld class, so I say "java HelloWorld"  Note that capitalization is important; everything is case-sensitive.

Thanks for the reply! Very informative :)
Well.. for the starters, I'm getting the basics.  But I feel there's a lot to learn from the zero now. I've had some experience with PHP, and C somehow looked like PHP for me (With a starting point "int main" etc). I guess GUI Java applications will be a long way from where I'm standing, right? I would like to make some programs for my mobile :P
Oh and by the way, how do I run GUI Java applications here? "java <name>" on Terminal?

Anyway, With Linux and such community, I feel like I've got a powerful tool on my hands :) Lovin' it

P.S.: On my actual course, they decided to go with Java first, and then C. On my last course, we wouldn't learn Java. Any reason for such?

---

### Post by ve4cib on 2011-02-26
> **GTMoraes said:**
> Thanks for the reply! Very informative :)
Well.. for the starters, I'm getting the basics.  But I feel there's a lot to learn from the zero now. I've had some experience with PHP, and C somehow looked like PHP for me (With a starting point "int main" etc). I guess GUI Java applications will be a long way from where I'm standing, right? I would like to make some programs for my mobile :P
Oh and by the way, how do I run GUI Java applications here? "java <name>" on Terminal?

Anyway, With Linux and such community, I feel like I've got a powerful tool on my hands :) Lovin' it

P.S.: On my actual course, they decided to go with Java first, and then C. On my last course, we wouldn't learn Java. Any reason for such?

If your java application has a GUI then launching it from the terminal will open the GUI.  Same as launching Firefox from the terminal.

As for why one course teaches Java and the other doesn't... it's pretty arbitrary.  At my university the introductory courses don't touch C and are entirely Java.  It really depends on what exactly the course covers.

A link you might find useful is [the University of Manitoba COMP1010 Wiki Textbook](http://wiki1010.cs.umanitoba.ca/mediawiki/index.php/COMP1010).  It's the actual "textbook" that's used by the first-year introductory computer science course at UofM.  It covers Java pretty much from zero.  It doesn't cover everything (most notably objects and polymorphism -- two HUGE concepts in Java that are covered in the second introductory course), but it's enough to get you started.

---

### Post by GTMoraes on 2011-02-26
That's exactly what I wanted. Hope I learn enough to start the new university with basic knowledge. Thanks!

Any others recommendations and tips are welcome :)

---

### Post by irrdev on 2011-02-27
Here's how it works: most languages, including C/C++, work identically on all operating systems. That includes Linux and Windows. However, you also need to use libraries, some of which are OS-dependent. If you are taught to use the Windows C library, then that won't work on Linux. However, QT, for example, is a C++ GUI library that works on Windows, Linux and the Mac. It isn't about the programming languages you learn, but the libraries that you use. If you use the default GUI library of each operating system, then that program won't work elsewhere. By using libraries which work on all platforms, however, your work and knowledge will be applicable to any platform.

---

### Post by alegomaster on 2011-02-27
It all depends. If she teaches you information that will be involving GUI, File I/O or internal system calls or commands, then you can't use it in Linux.

---

### Post by GTMoraes on 2011-02-27
But I guess it wouldn't be hard to "convert" it to Linux, am I right?

---

