---
title: "Programming for Linux??"
date: 2006-08-06
forum: Programming Talk
---

### Post by jeff_ on 2006-08-06
I consider myself to be relatively new to linux although I've been using various distros on and off over the past few years. In Ubuntu I think I have finally found a home and would like to start programming on/for it.

I am a Computer Science major and have plenty of experience programming in C/C++/Java/Python and others on windows and would like to transfer that over to linux. I looked through all 17 pages of posts in the programming section of this forum, but didn't see anything about starting to program for linux. I did see a great deal of people asking what IDEs are best etc. I'm mostly wondering how linux handles application-application and application-OS interaction. Is there something for linux comparable to Windows API and/or the windows messaging system?? This is what I think I should be trying to learn (although I'm open to suggestions).

Thanks for any help --Jeff

---

### Post by Harleen on 2006-08-06
The Linux counterpart to the WinAPI would be the POSIX standard. So any POSIX-book should help you out.
Communication between programs can be done using sockets (TCP if portability is needed or Unix Domain Sockets otherwise), Pipes ("man 2 mknod") or shared memory (see /usr/include/sys/shm.h).
I've not used these things for a while (or never for some of them), so I cannot give much more information. But this should guide you into the right direction.

---

### Post by bieber on 2006-08-06
Don't rely too much on POSIX, Linux and GNU aren't completely POSIX compliant.

To get started, I dunno what you used on Windows, but GCC, the GNU Compiler Collection, is the standard set of compilers for a great many languages (there are GCC compilers for C (gcc), C++ (g++), Java (gcj), and a great many others.  For the sake of my introduction, lets say you're going to use C (a grand old language).  GCC works from the command line (there are a bunch of IDEs out there if you don't like command line compiling), and it will compile pretty much any ANSI standard C file.  The syntax to compile a simple .c file is this
```
gcc -o outputfile inputfile.c
```
You can then run the executable with 
```
./outputfile
```.

That's basically all you need for basic command line applications--just learn to use the GNU Standard C library.  If you want to do GUI programming (like what you'd have used the Windows API for in Windows), you'll now have a choice to make.  There is no single API for GNU/Linux, instead, we have basically three you can choose from.  There's the X Window system, which is what powers everything graphical on your system.  You *can* write code that just interfaces with X to display windows and such, but it's not at all reccomended.

The other choices are GTK+, the GUI library used by GNOME, and QT, the GUI library used by KDE.  A quick Google search will turn up references and tutorials for whichever one you choose.  Note that both of them, unlike the Windows API (I used to write Windows programs in assembly, this is a pretty big change), they're both object oriented systems that abstract all the message handling and whatnot that you've gotten used to in Windows.  I can't explain it thoroughly, because I have yet to actually get around to learning GTK, but you should get it quickly enough once you start looking into it.

Oh, and I *believe* QT is only meant to be used in C++.  GTK has bindings for pretty much every language there's ever been, and it's what I personally reccomend...

---

### Post by jeff_ on 2006-08-06
Thanks. I'll give GTK a try as I'm currently running Gnome. Will QT and GTK only work on KDE and Gnome respectively? If so, this would seem to make things difficult as choosing between Gnome and KDE would effectively split your application pool in half, unless software includes support for both. Is this what is done and if so how exactly is this handled?

Thank you one again --Jeff

---

### Post by bieber on 2006-08-06
Not a problem.  The desktop systems are built off of the widget sets, not the other way around.  All a user needs is to have the appropriate libraries installed (GTK+, QT, and the KDE and GNOME libs), and they can run software built using any of them using either desktop system.  I use GNOME, and most of what I use is GTK, but I also keep some KDE apps around, and use them without any trouble (Kate, soundKonverter, kAlarm, and some others)

(Oh, yeah, and amaroK, of course.  If you don't have it yet, get it, right now.  **Best media player ever.**)

---

### Post by jeff_ on 2006-08-06
Gotcha, that makes sense. In that case what is the real difference between using GNOME and KDE? Is it just the basic layout of the desktop environment or if I loaded KDE (used long time ago and have forgotten) would I notice some other important differences?

Also if applications using QT work under GNOME and GTK under KDE (with the right libraries) does it really make a difference if I use QT or GTK?

---

### Post by mogwai on 2006-08-06
If you already know python, you can transfer that knowledge over to Linux quite easily.
I use wxPython(python interface to wxWindows) for GUI and spe(Stani's Python Editor) for an IDE.
Or if you are interested in C#, you could give Mono a go ([http://www.mono-project.com](http://www.mono-project.com) && [http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page))

---

### Post by bieber on 2006-08-06
I'd tend to advise sticking to languages that can compile native binaries, to avoid distribution difficulties.

KDE and GNOME have some sizable differences between them, but both are perfectly capable desktop systems.  It's just a matter of personal preference.  Same goes for using QT or GTK+.  It's just a matter of what library you like working with the best, and you think will work best for your project.

---

### Post by jeff_ on 2006-08-07
How can I interact with other applications windows? i.e. close a window or change the workspace a window is on?

---

### Post by Daverz on 2006-08-07
Take a look at the glibc docs to get an idea of what basic services are available for C programs:

info libc

After that, there's no hard standard for writing apps on Linux, so you have to make some choices, e.g. for GUIs gtk vs. some other C toolkit, or gtkmm vs. qt vs. wxWidgets for C++.  

If you want to work in C, I'd also look at the glib docs at gtk.org, as glib is pretty much guarenteed to be on any modern Linux distro.

If you plan on doing crossplatform work in C++, wxWidgets does try to help with portability of non-GUI APIs like networking.

Java is of course write-once-run-everywhere :roll:, but Python also does a pretty good job of abstracting out OS specific differences, too.  Unless your application requires it, you may never need to write any OS specific code.

---

### Post by Daverz on 2006-08-07
> **jeff_ said:**
> How can I interact with other applications windows? i.e. close a window or change the workspace a window is on?

Could you explain what you're trying to do?

There are standard ways to spawn and communicate with processes on unix, but generally a process would control its own windows/dialogs.   

Is there some reason you can't use whatever MDI is provided by the different toolkits?  It sounds like you would be fighting 
the standard way of writing applications, something guarenteed to frustrate users. 

Note that unless you're writing for a specific desktop, there's no guarentee your users have multiple workspaces.  This is something I would leave up to users, and as long as you follow X11 window manager standards (which is something a decent GUI toolkit will handle for you), they shouldn't have problems.

But maybe I'm being presumptious, and I don't understand what your needs are.

---

### Post by LordHunter317 on 2006-08-07
There are various ways to send commands and request to other windows, depending on what you want to do.

IT has nothing to do with process spawning whatsoever.  X11 clients use ICE to talk to each other, beyond what the X11 protocol provides.  

RPC mechanisms like D-BUS and DCOM also exist, which are more general purpose.

---

### Post by hod139 on 2006-08-07
If interoperability is a concern, check out [freedesktop.]("http://www.freedesktop.org/wiki/")
As for standards, here are a couple of biggies:
[Linux Standard Base]("http://www.freestandards.org/en/LSB")
[X.org]("http://www.x.org/")

[]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1348554")

---

### Post by themusicwave on 2006-08-07
I had similar worries when I recently started programming for Ubuntu.  So far I have learned a bit of GTK, but have mainly been using Java.

The nice thing is I really don't have to change much about how I write Java code, it works the same on Windows and Linux so far.

So if you know Java the switch will be really easy.  I even downloaded the Jbuilder IDE for linux and it works great.  Almost identical to the Windows version I was used to and it's free.

Honestly I dispised most Windows programming, the WIN32 API drove me insane.

---

### Post by jeff_ on 2006-08-07
I actually have nothing particular in mind, just wondering how different things are done on linux. Recently I came across the limitations of Devil's Pie's abilities which is the only reason I asked about changing the workspace a window is on.

Thanks for all the replies --Jeff

---

### Post by David Marrs on 2006-08-09
> **jeff_ said:**
> I actually have nothing particular in mind, just wondering how different things are done on linux.
Thanks for all the replies --Jeff
You can generally rely on your environment's window manager to deal with window behaviour for you, unless there's something specific that you want your windows to be able to do.

There's a good review of gnome 2.4 on ars technica, which explains the Gnome platform very nicely. It also compares it to Windows and Mac OS

[http://arstechnica.com/reviews/os/gnome2.4.ars](http://arstechnica.com/reviews/os/gnome2.4.ars)

---

