---
title: "Want to build C++ apps for windows using Linux"
date: 2009-03-13
forum: Programming Talk
---

### Post by trakker01 on 2009-03-13
Hi,

I'm new to Linux (about 30 hrs) and right now it is installed on my laptop without any Window OS.  What my goal is, is to be able to learn and produce dbase type applications in other languages  such as Pascal & C++ for use in Windows and also some for use in Linux.  Is this possible?  Are there C++ and other language development applications complete with compilers, debuggers, etc. for Windows and Linux ?

---

### Post by e24ohm on 2009-03-13
I am not a programer by any means, but I have done some "C" programming for embedded systems in the past, which were mostly fire control units.

To build "C++" apps you will use g++ to compile your code. You can use "nano", vi or any other editor to write your code.

I have been looking at the Mono project and recently the GTK+ project, and these solutions/Projects might interest you as well.

Good luck

E

---

### Post by Can+~ on 2009-03-13
> **trakker01 said:**
> Hi,

I'm new to Linux (about 30 hrs) and right now it is installed on my laptop without any Window OS.  What my goal is, is to be able to learn and produce **dbase** type applications in other languages  such as Pascal & C++ for use in Windows and also some for use in Linux.  Is this possible?  Are there C++ and other language development applications complete with compilers, debuggers, etc. for Windows and Linux ?

"database type applications"? Like writing your own DBMS, or a program that interacts with an existing database?

---

### Post by mcla0203 on 2009-03-13
If you start making a UI for your app... I might try running it in Wine.  Not all Windows apps work in Wine, but I am guessing if it runs in Wine it will run in Windows.  

It does sound a little twisted to me to develop in linux environment for windows apps, but if thats what you savvy give it a shot!  It would be interesting to see how it goes.

---

### Post by stevescripts on 2009-03-13
If you are dead set on using C++, take a look at mingw/msys:

[http://www.mingw.org/wiki/msys](http://www.mingw.org/wiki/msys)

There are other, higher-level languages (scripting languages), such as Tcl, Python, Ruby, Lua, etc, which are cross-platform, and all have libraries to deal with database applications, and all have GUI toolkits.

Mono may also be a viable alternative.

Steve

---

### Post by Krupski on 2009-03-13
> **trakker01 said:**
> Hi,

I'm new to Linux (about 30 hrs) and right now it is installed on my laptop without any Window OS.  What my goal is, is to be able to learn and produce dbase type applications in other languages  such as Pascal & C++ for use in Windows and also some for use in Linux.  Is this possible?  Are there C++ and other language development applications complete with compilers, debuggers, etc. for Windows and Linux ?

There is a VERY nice C/C++ compiler, debugger and editor system (free too!) for Win32. Check out this link:

_**[http://www.q-software-solutions.de/downloaders/get_name](http://www.q-software-solutions.de/downloaders/get_name)**_

(then click on "get me to the downloads" button).

I only do VERY simple console mode programs (utilities mostly) in Windows console mode and in Linux.

The LCC Win32 system is actually a nice IDE that I usually use to develop my program, then when it works I remove the carriage returns from the source ( :) ) then import it into Linux and use GCC to compile it.

For the simple stuff I do, it usually compiles perfectly with no editing (or at worst 1 or 2 minor changes).

For bigger programs and/or graphical stuff, I have no idea how code would carry over. My guess is that it wouldn't (since the Windows API and Linux API is so much different).

Good luck!

-- Roger

---

### Post by Tibuda on 2009-03-13
> **stevescripts said:**
> If you are dead set on using C++, take a look at mingw/msys:

You can [install MingW cross-compilers from Ubuntu repositories]("apt:mingw32").

---

### Post by albandy on 2009-03-13
> **trakker01 said:**
> [...] and other language development applications complete with compilers, debuggers, etc. for Windows and Linux ?

If you want an esay way to run your software in both systems you can use java.

Netbeans it's a good IDE and works in both systems (Linux and Windows).

with Netbeans you can build graphical applications, web applications, console applications, debugin ...

---

### Post by jimi_hendrix on 2009-03-13
> **stevescripts said:**
> 
There are other, higher-level languages (scripting languages), such as Tcl, Python, Ruby, Lua, etc, which are cross-platform, and all have libraries to deal with database applications, and all have GUI toolkits.


you forgot perl in there

another compiler that will produce a windows executable that runs in linux is cygwin...its more of a linux 'environment' that runs on either linux or windows

---

### Post by kavon89 on 2009-03-13
Run a copy of windows virtually with VirtualBox. Its open source and I highly recommend it over VMware and other virtualization programs.

---

### Post by stevescripts on 2009-03-13
> **jimi_hendrix said:**
> you forgot perl in there

another compiler that will produce a windows executable that runs in linux is cygwin...its more of a linux 'environment' that runs on either linux or windows

No, I didn't forget PERL, I just choose to ignore it ;)

FWIW, I get better results with mingw/msys than cygwin, but,
use whatever floats your boat

Steve
(yes, I do use PERL from time to time, rarely... )

---

### Post by trakker01 on 2009-03-14
Thanks for response.  I'm starting to look at the suggestions.

Thanks again

---

### Post by trakker01 on 2009-03-14
Yes that's what I want to do.  Make stand alone apps that will use exusting data bases or make new ones that are specific and personalizes. 

Thanks for response,
trakker01

---

### Post by trakker01 on 2009-03-14
Hi,

Not really twisted, but maybe a little fanciful.  I believe that in the best of worlds that an operatin system should allow you to produce  apps for any system;  seems as though it would ideally be set up so that you would just select the type of system and you developing ide would set itself to make use of that code in its compiler and debugger.  Is that too much to ask?  Maybe we are not quite there yet, but one can and should hope.

Thanks for response,
trakker01

---

### Post by trakker01 on 2009-03-14
Thanks Steve,  
I'm trying to look these suggestions up and study them.
Thanks again,
trakker01

---

### Post by trakker01 on 2009-03-14
Thanks Roger, gonn give it a try and see what happens.  Nothing immediate, still too new to all this.

Thanks again,
trakker01

---

### Post by trakker01 on 2009-03-14
Thanks, Apple,
Tried to look at that, but couldn't get on the web page.  Will try again.
Thanks again,
trakker01

---

### Post by trakker01 on 2009-03-14
Thanks for the suggestion.  Java seems kind of scarey to me, but second thought shows that it just might be doable.

Thanks again,
trakker01

---

### Post by trakker01 on 2009-03-14
Thanks for the suggestion.  Really going to have to try this one.

Thanks again,
trakker01

---

### Post by rich1939 on 2009-03-15
> **trakker01 said:**
> Hi,

I'm new to Linux (about 30 hrs) and right now it is installed on my laptop without any Window OS.  What my goal is, is to be able to learn and produce dbase type applications in other languages  such as Pascal & C++ for use in Windows and also some for use in Linux.  Is this possible?  Are there C++ and other language development applications complete with compilers, debuggers, etc. for Windows and Linux ?

I've been using the CODE::BLOCKS development environment along with the GLADE user-interface development package to build a fairly comprehensive database-intensive application that uses the PostgreSQL database as its backend. I'm using the C language and the GTK+ UI toolkit, but you can also use C++ with those components as well.

CODE::BLOCKS has a nice WYSIWYG editor, debugger interface, compiler interface, etc. You can specify what kind of project you want to build and CODE::BLOCKS sets up all of the build, compile, and debugger interfaces for you. The GTK+ libraries provide cross-platform abilities and CODE::BLOCKS, GLADE, GTK+ and PostgreSQL are all available for use on Windows as well as Linux.

---

