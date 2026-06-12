---
title: "Old dog wants to learn new tricks..."
date: 2006-12-03
forum: Programming Talk
---

### Post by Bob Unitt on 2006-12-03
I've been a systems/applications programmer for >30 years, mainly on Windows using MS 'C' 6.0 (_not_ C++) and SyBase SQL. I've recently become interested in Unix, and have now created for myself a UBUNTU 'Dapper' set-up to play with. I'd like to both create new programs on Unix, and see if I can port some of my old Windows apps across. As far as programming languages go, I'd rather stick with straight 'C' for now, although I do intend to try some PHP stuff as well.  

My (initial) questions are :-

1) What 'C' compiler/IDE should I use ?
2) What replaces the Windows API's for interface and system functions ?
3) Where do I find the libraries for 2) ?
3) How 'standard' an SQL is 'MySQL', and can it be invoked programatically from anything other than PHP ?

TIA.

---

### Post by Houman on 2006-12-03
Hi there;

I also used to program and I now have completely switcherd to Ubuntu, so we have something in common (except I have 2 years of experience rather than 30 :( )

Anyways, here are my answers to your questions:

1-  For compiler use gcc (the standard default compiler on any Linux/Unix machine), you can install it by typing ```
sudo aptitude install build-essential
```  As for an IDE, I suggest you use none! try to use a good text editor like vi or emacs, I suggest this because it will be very different to what youre used to and will force you to do do things differently and maybe learn something in the process (like writing makefiles instead of having your IDE take care of that stuff). This is how a lot of Linux programmers work. But if you see thats just hard to get used to use KDevelop, its the closest thing to Visual Studio (but definitely not as polished).

2- Windows API is consisted of several sub categories (GDI, base services, networking..) whereas in Linux you have the Kernel functions, and you have the Xlib functions for any graphical utilities and etc , so its not an all on one thing like Windows. But if you're gonna build a GUI you can use one of several interesting libraries, for instance the gtk library which is used to build the gnome desktop. I personally prefer wxwidgets because you can compile it on windows as well (its a cross platform library). So Linux is a bit different than Windows in that different Win API functionalities are provided by different libraries (thats my understanding).

3- I am assuming you want to build GUIs here, so just install the development libraries for whatever library you prefer (gtk, QT, or wxwidgets or ...) some of these libraries provide much more than GUI capabilities, I guess you can look up each on wikipedia and then decide what to use, although I suggest wxwidgets because its somewhat similar to MFC syntax on windows. But the downside is that it has a C++ interface, so if you just want to use plain old C , maybe you should consider gtk (once you settle on the library you want to use you can come back and ask how to install/use it)

4- MySL is standard enough that if youve used sql on any other database platform you'll be able to use it, ive only used mysql, but my friend who uses oracle discusses stuff with me, and it all seems very similar (i guess except for a few small places), also mysql commands can be issued from any program that has the mysql library and drivers installed. I used to write perl code that issues mysql command, my friend used C# and basically you can do it from inside any programming language as long as you have the proper libraries installed.

hope this helps;

Houman

---

### Post by lnostdal on 2006-12-03
> **Bob Unitt said:**
> I've been a systems/applications programmer for >30 years, mainly on Windows using MS 'C' 6.0 (_not_ C++) and SyBase SQL. I've recently become interested in Unix, and have now created for myself a UBUNTU 'Dapper' set-up to play with. I'd like to both create new programs on Unix, and see if I can port some of my old Windows apps across. As far as programming languages go, I'd rather stick with straight 'C' for now, although I do intend to try some PHP stuff as well.  

My (initial) questions are :-

1) What 'C' compiler/IDE should I use ?

GCC and Emacs. Use Scons when building your projects. Assign a shortcut key in Emacs that calls `scons -u'.

> **Bob Unitt said:**
> 
2) What replaces the Windows API's for interface and system functions ?


That depends on what you're doing.

GTK+ for GUI: [http://www.gtk.org/](http://www.gtk.org/)

> **Bob Unitt said:**
> 
3) How 'standard' an SQL is 'MySQL', and can it be invoked programatically from anything other than PHP ?


I believe PostgreSQL is "more standard". Both can be used from almost any language since the client-part has a C-API.

[http://dev.mysql.com/doc/refman/5.0/en/c.html](http://dev.mysql.com/doc/refman/5.0/en/c.html)
[http://www.postgresql.org/docs/8.1/static/libpq.html](http://www.postgresql.org/docs/8.1/static/libpq.html)

---

### Post by mcglnx on 2006-12-03
> **Bob Unitt said:**
> 

1) What 'C' compiler/IDE should I use ?
2) What replaces the Windows API's for interface and system functions ?
3) Where do I find the libraries for 2) ?
3) How 'standard' an SQL is 'MySQL', and can it be invoked programatically from anything other than PHP ?

TIA.

Hi, 

1) gcc will compile for you. IDE - Try KDevelop, Emacs, or certainly any other from the package manager. 
2) POSIX function will be sufficient. If you need graphical libraries, try Gnome-dev for C or KDE-dev for C++.
3) package manager.
3) can be invoked by virtually any languages. MySQL sit will tell you the level of SQL compliances.

Cheers,
M.

---

### Post by Bob Unitt on 2006-12-04
Thanks you all - the story so far...

[U]My (initial) questions are :-

1) What 'C' compiler/IDE should I use ?[/U]

KDevelop, EMACS and GNU C installed and running - I can now compile and run the default 'Hello World' text-based program (but see below).

[U]2) What replaces the Windows API's for interface and system functions ?
3) Where do I find the libraries for 2) ?[/U]

**houman** - 'wxwidgets' being like MFC doesn't help, as I've avoided MFC like the plague under Windows (we C control freaks like to have command of every line of code...). 

I'll have a prowl around the suggested libraries and see what takes my fancy. I'm not after anything particularly exotic by way of graphics etc., just a good workmanlike library for commercial data processing (and I think that phrase gives my age away...), so I'll probably go with GTK. Is there a GTK-based 'Hello World' program I can play with, just to crib the basics ?  

Is there a UNIX equivalent to Petzold's 'Programming Windows' books (which is how I taught myself the Windows API) ?

_4) How 'standard' an SQL is 'MySQL', and can it be invoked programatically from anything other than PHP ?_

Thanks for the confirmation that I can embed SQL in my programs, that will be useful.

**Inostdal** - I think I'm stuck with MySql, as that the database system my ISP provides on his web-server.

I do have one issue with my 'Hello World' program; it runs OK, but the following appears in the debug window :-

  X Error: BadDevice, invalid or unitialised input device 166
  Major opcode 144
  Minor opcode 3
  Resource ID 0x0
  Failed to open device

Which doubtless means something highly significant to somebody but, unfortunately, not me. A gentle nudge in the right direction would be 
appreciated...

---

### Post by lnostdal on 2006-12-04
hello world/petzoldish ..etc..: [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

---

### Post by Houman on 2006-12-04
hi there;
glad to know progress is being made, if you're looking somewhere to start programming gtk the best place would be here [http://www.gtk.org/tutorial/]("http://www.gtk.org/tutorial/").
There is actually a "hello world" program at the beginning.

Also if you are a control freak (which I think is great if you're a programmer) throw away KDevelop and write your files in a text editor and compile it from command line. I personally hate when the IDE does a ton of stuff behind the scenes which I have no control over. (although you can later on tweak all the generated files, but still).

Also you mentioned you had a problem with your code, that error is completely new to me. Do you mind posting the code? and how you compiled it? I cant see how would a simple printf("hello world") program geenrate such a weird error.

Also, once you get going, you might wanna start programming Win API on linux! I highly recommend you keep programming it, I am very envious of people who know Win API well. You can do that by installing [WINE]("http://en.wikipedia.org/wiki/WINE") and [MinGW]("http://en.wikipedia.org/wiki/Mingw").

regards

Houman

---

### Post by bonzini on 2006-12-05
Bob Unitt says:

> I've been a systems/applications programmer for >30 years

me too, Bob.

> mainly on Windows using MS 'C' 6.0 (not C++) and SyBase SQL

well, you've got me beat there.  I've been programming in Pascal, and C, and Java, and Python, on Unix machines, and lately just Java and Python on Linux.

Here is what my experience suggests.

[LIST=1]
[*]try Python.  it's just wonderful.  you can get a lot of useful little things working very quickly, and you can also write some pretty impressive large-scale stuff.  start learning it by going to [http://www.python.org](http://www.python.org) and checking out the tutorial.  Python has a number of great interfaces to relational databases.  (I'm trying to get to the stage where I write in Python to solve little problems instead of in the shell and in awk.  almost there).

[*]try Java.  it's just wonderful, too.  then anything you write can run on Linux or Windoze or MacOS.  plus it's not too big a jump from C (not like C++).  you can use JDBC to get at your relational databases.  there are many ways to learn Java but IMHO O'Reilly has a huge and worthwhile selection of books to read on the subject.

[*]I'm a fan of using vi, or some other text editor, and compiling on the command line.  but if you want to learn an IDE, try NetBeans at [http://www.netbeans.org](http://www.netbeans.org) - if I'm not mistaken you can use this for C/C++ too.
[/LIST]

Good luck!

---

### Post by ArtechnikA on 2006-12-05
> **bonzini said:**
> Bob Unitt says:
there are many ways to learn Java but IMHO O'Reilly has a huge and worthwhile selection of books to read on the subject.

Jumping in a little late here...  First, thanks for the pointers to the GTK tutorial - I had that very question myself, and I see that it has already been asked and answered.

Not to hijack the thread, but, regarding the O'Reilly Java books - I find the selection of worthwhile Java books a little -too- huge; I'm having trouble finding the one or two I need to start with.  I'm an experienced C and C++ (and other too numerous to mention) programmer.  I know programming, I 'get' objects.  I need a (ideally) single book that lays out the specifics of the Java syntax perhaps with a few targeted code examples, for the "useful" stuff that forms the basis of practical applications: data types and structures, flow control, formatted I/O.

Following this thread with great interest - thanks !

---

### Post by Bob Unitt on 2006-12-06
> **lnostdal said:**
> hello world/petzoldish ..etc..: [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

That looks to be what I was after, thanks.

---

### Post by Bob Unitt on 2006-12-06
**Quoting Houman**

_Also if you are a control freak (which I think is great if you're a programmer) throw away KDevelop and write your files in a text editor and compile it from command line._

I'll leave learning about make-files for later - one thing at a time is enough for me...

_Also you mentioned you had a problem with your code, that error is completely new to me. Do you mind posting the code? and how you compiled it? I cant see how would a simple printf("hello world") program geenrate such a weird error._

It's the 'Simple Hello world program' from the 'Create New Project' entry in 'C' on KDevelop, using the GCC C-compiler. I simply created, built and executed the project exactly as supplied. It runs OK both from within KDevelop and from a command in the bash-shell; but this wierd error appears when running from KDevelop. The source the project generates is just :-

[INDENT]#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  printf("Hello, world!\n");

  return EXIT_SUCCESS;
}
[/INDENT]

_Also, once you get going, you might wanna start programming Win API on linux! I highly recommend you keep programming it, I am very envious of people who know Win API well. _

The important thing to remember about the Win API is that 90% of it is pure bloatware - if you stick to the basics it's actually a very usable GUI-etc interface.

Thanks for your help so far, I'll doubtless be back for more later...

---

### Post by Bob Unitt on 2006-12-06
> **bonzini said:**
> 
Bob Unitt says:_About 30 years programming:_
me too, Bob.


Maybe we should start a forum for greybeards ;) 

> 
well, you've got me beat there.  I've been programming in Pascal, and C, and Java, and Python, on Unix machines, and lately just Java and Python on Linux.


Mainly C for me of late, although there's Pascal, Cobol, Fortran, RPG and proprietary system languages for various machines somewhere in my past - although I think those particular brain-cells are long-gone by now.

> 
Here is what my experience suggests.


Java's on my list of things to be investigated in due course, but I'll give the others a miss for now.

Good luck!

---

### Post by HolyJoe on 2006-12-06
and other problem: 
How to programming in assembly language for ubuntu? and where to start?
can illustrate with a simple sample?

---

### Post by Bob Unitt on 2006-12-06
> **Houman said:**
> ... if you're looking somewhere to start programming gtk the best place would be here [http://www.gtk.org/tutorial/]("http://www.gtk.org/tutorial/").
There is actually a "hello world" program at the beginning.


I'm a bit confused...

I thought I'd see if GTK could be installed via Ubuntu's 'Synaptic Package Manager'; there's any number of references to GTK in the list of packages but I can't figure out which, if any, are the libraries I'm looking for.

Also, is it possible to install a GTK project template in the KDEvelop IDE, so i can just add GTK projects from scratch ?

TIA

---

### Post by Houman on 2006-12-06
> 
and other problem:
How to programming in assembly language for ubuntu? and where to start?
can illustrate with a simple sample?



I googled up couple of links for you:

[http://tldp.org/HOWTO/Assembly-HOWTO/index.html]("http://tldp.org/HOWTO/Assembly-HOWTO/index.html")
[http://docs.cs.up.ac.za/programming/asm/derick_tut/]("http://docs.cs.up.ac.za/programming/asm/derick_tut/")

But unlike languages like python or Perl you cant start coding assembly by reading couple of samples, you probably need a bit of knowledge about the underlying computer architecture (understand what are registers, interrupts, stack...).

So i suggest if you are serious about programming Asm on Linux to buy a book, I recommend this book:

[http://www.amazon.com/Guide-Assembly-Language-Programming-Linux/dp/0387258973/ref=cm_taf_title_featured?ie=UTF8&tag=tellafriend-20]("http://www.amazon.com/Guide-Assembly-Language-Programming-Linux/dp/0387258973/ref=cm_taf_title_featured?ie=UTF8&tag=tellafriend-20")

It's a step by step guide and very tailored towards the beginners, it covers everything from installation of a Linux distro to digital logic to computer architecture and its very accessible.

regards

Houman

---

### Post by Houman on 2006-12-06
> 
I thought I'd see if GTK could be installed via Ubuntu's 'Synaptic Package Manager'; there's any number of references to GTK in the list of packages but I can't figure out which, if any, are the libraries I'm looking for.


I always find these things by thinking, ok there should be gtk in the name of the package, there should also probably be a "lib" in the package name (because its a library) also there should probably be the letters "dev" in the package name because its a development library, so i just search for these words "dev" "lib" and "gtk" in the package name :D and from all the candidates the one that fits the bill most is "libgtk2.0-dev" which you can install just by typing "sudo aptitude install libgtk2.0-dev".

> 
Also, is it possible to install a GTK project template in the KDEvelop IDE


Im no KDevelop expert, but it seems it only has a gtkmm template (C++ wrappers for the gtk library). Im thinking maybe there is a way to add a gtk template, but if you're going to do a lot of gtk programming maybe youre better off with Anjuta which is another IDE better geared towards gtk programming. I don't know much about Anjuta either, but what do the other members think? 

As for the error you have with your code, I have no idea :(

regards

Houman

---

### Post by Bob Unitt on 2006-12-06
And for my next trick...

I've got exactly the same problem as described in :-
<http://ubuntuforums.org/showthread.php?t=248233>

Does anybody know of an answer to it ?

---

### Post by MadMan2k on 2006-12-06
you have to make sure that you are invoking gcc with pkg-config:
```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`
```
so it can find the gtk headers.

---

### Post by Bob Unitt on 2006-12-06
> **MadMan2k said:**
> you have to make sure that you are invoking gcc with pkg-config:
```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`
```
so it can find the gtk headers.

Thanks for that. I found that additionally, in order to compile within KDevelop, I needed to add the string `pkg-config --cflags --libs gtk+-2.0` to both the 'Project Options' / 'Configure Options' fields 'CCPFLAGS' and 'LDFLAGS'.

I'm now building and running the GTK 'Hello World' successfully, although I still get the strange error message I mentioned in an earlier posting.

---

### Post by Bob Unitt on 2006-12-06
> **Houman said:**
> *On finding* "libgtk2.0-dev".

It turned out that I had the libraries all along, although I'm not at all sure when they were installed - I was actually missing some settings in the KDevelop configuration.

---

### Post by Régis B. on 2006-12-07
Hello Bob,
I had the same problem as you and realized the problem is linked to some wacom devices indicated in /etc/X11/xorg.conf. The problem and adequate solution are described here:
[http://www.ubuntuforums.org/showthread.php?t=212025&highlight=x+error+baddevice](http://www.ubuntuforums.org/showthread.php?t=212025&highlight=x+error+baddevice)
What you have to do is simply to comment out a few lines and reboot. 

Yes, I know, it's weird, but it worked for me.

Régis

---

### Post by Hendrixski on 2006-12-07
> **Houman said:**
> 

 As for an IDE, I suggest you use none! try to use a good text editor like vi or emacs, I suggest this because it will be very different to what youre used to and will force you to do do things differently and maybe learn something in the process (like writing makefiles instead of having your IDE take care of that stuff). This is how a lot of Linux programmers work.

That's how I learned how to program.  I learned C++ on emacs, and then discovered vi and I never touched emacs again. 

I've been using IDE's like Eclipse and .NET the last few years and even after a quick introduction I found my productivity went way up. While I respect that some people want to keep old traditions alive, I think that IDE's are in fact the way to go, especially for GUI's where it's faster and easier to drag and drop visual components and then add code as needed.

I know I lose nerd points by saying that easier is better but my boss (and my customers) don't care if I use the nerd-approved way of coding or not.  They just want to see more code, faster.  It was hard for me to give up the VI + commandline habits, but soon everyone else will as well.

Having said that, I still use VI when I write SQL with lots of cut and paste and macro work because I can do it in half the time of Toad or SQL*Plus.  But for Java, C++, C#, and Object PASCAL, I am sold on the IDE.

---

### Post by Houman on 2006-12-07
> 
That's how I learned how to program. I learned C++ on emacs, and then discovered vi and I never touched emacs again. 


Unlike you, I learned to program on Visual Studio. As a result, for a long time I thought I am a good programmewr eventhough I didnt really know whats heppening behind the scnenes. Thats why now I do everything on command line even though its really hard for me because of my long term dependence and addiction to Visual Studio (the best and the greatest of IDEs). That is why I suggested that Bob use the commmandline approach even though it will probably reduce his productivity, but my point was that he will be "forced to learn a few things".

But I absolutely agree with you, if you're programming at work on a large projects it would be a pretty bad idea to use the command line (unless you're writing small scripts or SQL snippets as you said).

So, you're right and I am right :D I don't think I can ever code as fast as I used to with MSVC when I code with emacs, but if I am coding at home for hobbies I don't care much about productivity, rather about learning and having complete control over things. And thats what Bob was doing, he is experimenting and playing for the sake of learning.

Also I would never get into one of those arguments (text editing vs IDEs).  I think each approach is good for certain scenarios (I'd never teach my kids programming with an IDE for instance).


regards

Houman

---

### Post by Bob Unitt on 2006-12-07
Régis,

> **Régis B. said:**
> I had the same problem as you and realized the problem is linked to some wacom devices indicated in /etc/X11/xorg.conf. The problem and adequate solution are described here:
[http://www.ubuntuforums.org/showthread.php?t=212025&highlight=x+error+baddevice](http://www.ubuntuforums.org/showthread.php?t=212025&highlight=x+error+baddevice)
What you have to do is simply to comment out a few lines and reboot. 

Thanks, that's fixed it.

---

### Post by Bob Unitt on 2006-12-07
Houman,

> **Houman said:**
> ...And thats what Bob was doing, he is experimenting and playing for the sake of learning...

Not exactly - I do actually program computers for a living. What I'm trying to do is 
a) expand my horizons, and 
b) make my products more attractive to customers by removing the dependency on a single operating system.

OTOH, I have to agree it is indeed more fun than doing the washing-up or mowing the lawn...

---

### Post by lloyd mcclendon on 2006-12-10
[www.yoxos.com/ondemand](www.yoxos.com/ondemand)

build your version of eclipse.  best development environement ever

---

