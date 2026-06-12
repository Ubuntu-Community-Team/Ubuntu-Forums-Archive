---
title: "Programming (Windows -&gt; Linux)"
date: 2006-06-07
forum: Programming Talk
---

### Post by Agent Smit on 2006-06-07
Hello everyone,

I know there must be hundreds off posts (I have searched) on programming Linux for newbies like me.

Here's my situation...

1. I can hold my own when it comes to Windows programming.
2. I know and use Assembly, C, PowerBasic.
3. I've written some Windows programs (GUI and console) that I now want to convert/port to Linux.
4. I am a complete newbie on the Linux programming front.

So, with that said, what direction could you kind folks point me in?

This is a list of the kinds of things (I think) I need to learn...

1. GUI programming under Linix (gnome GTK?, Buttons, Scrollbars, etc...)
2. TCP/IP + Encryption + ZLIB
3. Custom database (general file handling)
4. Graphics (The Linux version of GDI)

Thanks in advance for any help ;)

---

### Post by toojays on 2006-06-07
Your list sounds pretty decent. As far as "the Linux version of GDI" goes, your best bet is probably [cairo](http://www.cairographics.org). I've actually recently started using this in a Windows project, safe in the knowledge that it will be easier to port that application to GNU/Linux later.

Another thing you need to learn is whatever toolchain you want to use to build your project. My suggestion is GNU Emacs (or other text editor if you already have a preference) and GNU Make.

One thing you didn't mention is if you still want your old applications to be able to be built for Windows in the future. If this is the case, you may find mingw32 and Wine useful. Mingw32 is a Windows compiler you can install on Ubuntu (i.e. it makes Windows exe files). Wine is a system which allows you to run those exe files under Ubuntu.

I have done a bit of this kind of stuff. Depending on how much non-portable stuff your app has in it, it can be quite slow going. Good luck.

---

### Post by Agent Smit on 2006-06-07
Hey toojays,

Thanks for the reply :)

I had a look at Cario and to be honest I was leaning towards using that in Windows as well before I got the itch to "jump ship" on Microsoft. Perhaps you could point me in the right direction with Cario as well?

Toolchain, I've seen a lot of terms thrown around like Vi, Emacs, Gcc, Eclipse, Glade, etc... so to be honest I have no idea, but I do know this...

1. I am looking at using C, C++
2. I need a GUI editor of some sort (Glade? I was using Visual Studio before)

To be honest, I would rather just abandon the Windows platform all together.

My reason for leaving is as follows...

1. Our software is used "in the field" meaning way out in the middle of nowhere. Because of that support is REALLY difficult.

2. Windows has been a major pain in the butt mainly because our users have everything from Windows 98 and up. So I've had to code special paths for each version and just plain leave out things because they weren't possible across the board.

3. The "Live CD" idea sounds really cool. Build a Linux Live CD with our software on it so the user can just drop in the disc and away they go. This also comes in handy if there computer breaks, just move over to another one and boot off the CD again.

That last one is actually the straw that broken the camels back for me. Over the past couple of days one of the users computers (Laptop with WinXP) "somehow" ended up with a corrupt boot file so the entire machine was rendered useless. The poor sap is at least 2 days away from civilization so there isn't a shop he can get it fixed at near by. The only other option is to loose his data and reinstall from the "recovery discs" that came with the laptop.

I should also add, most of these users don't know S!@T from wild honey let alone know how to fix a problem like that. Even with tech support over the phone this can be a real problem.


So in a nutshell, I want to move to a Linux Live CD with our software on it and save the users data to a USB drive.


Thanks again for the suggestions!

:)

---

### Post by ssam on 2006-06-07
if you dont want to start from scratch i believe it is possible to use winelib as a sort of scaffold. you start with the orginial source code for you application on windows, and compile it against winelib. then you can gradually port parts to more linux friendly libraries. [http://winehq.org/](http://winehq.org/) has far more information than i know.

---

### Post by Agent Smit on 2006-06-07
Hello ssam,

Thanks for the tip :)

Actually, I would love to start from scratch. I can't think of a better way to get my feet wet and possibly make the software better at the same time.

What I need is some bare bones examples of how to make a windowed program (GUI based). The thing that is really confusing me is the amazing number of libraries and "ways" of programming on the Linux platform. I mean just reading through all the post on here would take a life time :D

Coming from the windows side, everything was just as simple as calling functions in the SDK/API. But with linux it seems as though there are hundreds of different libraries to choose from, not to mention development tools.

I have to admit, I have Ubuntu 6.06 running in VMWare and for the life of me I have no idea what packages I need to install to get GCC, Glade up and running LOL

Thanks again for your patience ;)

---

### Post by Agent Smit on 2006-06-07
Update,

I just got my hand on Linux Programming Unleashed - SAMS. It seems a little dated but it's a start I guess.

Can anyone recommend some books like the above? I don't mind reading so long as I've got the general direction right :wink: 

Thanks!

---

### Post by Lews Therin on 2006-06-08
[QUOTE=Agent Smit]Hello everyone,

I know there must be hundreds off posts (I have searched) on programming Linux for newbies like me.

Here's my situation...

1. I can hold my own when it comes to Windows programming.
2. I know and use Assembly, C, PowerBasic.
3. I've written some Windows programs (GUI and console) that I now want to convert/port to Linux.
4. I am a complete newbie on the Linux programming front.

So, with that said, what direction could you kind folks point me in?

This is a list of the kinds of things (I think) I need to learn...

1. GUI programming under Linix (gnome GTK?, Buttons, Scrollbars, etc...)
2. TCP/IP + Encryption + ZLIB
3. Custom database (general file handling)
4. Graphics (The Linux version of GDI)

Thanks in advance for any help ;)[/QUOTE]

You'll want to learn either GTK+ (and GNOME) or QT (and KDE) for GUI programming. If you are using Ubuntu or Xubuntu, learn GTK+/GNOME. If Kubuntu, QT/KDE.

QT and GTK+ can create full GUI applications, and both are also available on Windows. The KDE or GNOME libraries are optional, and used for integration into the desktop environment (things like notification tray applets). I've found that GTK+ doesn't need the GNOME libraries for integration as much as QT applications need the KDE libraries.

Networking is handled with BSD sockets, encryption would be OpenSSH, and zlib has a Linux version.

I don't know what you mean by custom database / general file handling. Opening, reading files, etc is generally done with either the standard C/C++ functions. fopen, fread, etc for C and fstreams for C++. Some libraries, like GNOME or QT, have fancy file handling functions for things like access to remote machines.

Simple 2D graphics will be with either Cairo (GTK+), or Arthur (QT). 3D graphics are done with OpenGL.

---

### Post by Agent Smit on 2006-06-08
Thanks Lews!

That's the kind of info I was lookin for. I finally managed to install gcc with the following command...

sudo apt-get install build-essential

It worked and I tested it with a simple little "hello, world" proggy.

So my next question is, how do I go about installing the GTK+ and  Gnome libraries for gcc, or are they already included with the above?

Thanks :grin:

---

### Post by snoop on 2006-06-08
For a gui toolkit, I would say try wxWidgets. It is a fantastic widget set with really nice, simple api. WxWidgets is also cross platform. It will also be a help in linux cause you wont have to depend on qt or kde because each user is likely to have something different and loading those libraries (like kde) if using gnome or xfce can be a massive strain on a computer with not enough ram.

For 2d programming, there is always sdl. For 3d, opengl.

To see if you have the libraries, just open up synaptic and search for gtk libs and see if they are installed. 

If you need an IDE, there is always anjuta.

---

### Post by toojays on 2006-06-08
I have used wxWidgets for some of my software, it's quite good. If you install the packages libwxgtk2.6-dev and wx-common in Synaptic this will bring in everything you ned for wxWidgets. This will also pull in the GTK+ development libraries  as well. I used the xrced program for the GUI builder, but there are others available. You can get xrced by installing the python-wxtools and python2.4-xml packages. There is a wxWidgets book advertised on the wxWidgets web site, but I haven't read it myself.

GTK+ and Qt are both very capable as well. Unless one of these libraries has some feature which is a "killer feature" for your program, it doesn't really matter which you choose IMO. If you prefer to code in straight C, then you will be happier with GTK+. wxWidgets uses fairly basic C++, whereas Qt seemed to make much more use of "advanced" features like templates last time I looked.

Regarding ssam's suggestion of using winelib as a scaffold: it's a decent way to go if you can figure out an approach for pulling out non-portable libraries one at a time. If anyone is going to do this, I highly recommend [Working Effectively with Legacy Code](http://www.amazon.com/gp/product/0131177052/sr=8-1/qid=1149771157/ref=pd_bbs_1/102-6144914-9694521?%5Fencoding=UTF8) by Michael Feathers. Although it doesn't address the topic directly, it provides some excellent advice about how you can make drastic modifications to software while still being able to test things as you go and make sure they work. It really changed my mind about the whole "re-implement versus port" debate.

---

### Post by Agent Smit on 2006-06-08
Hello again,

First off, I want to say Thank You for all your help so far. This is the exact kind of help I was looking for.

I'm gonna take some time now and read my brains out about GTK GNOME GCC and the like. I may chime in a little later on if I have any more questions.

Honestly, great forums, great people!

See you around ;)

---

### Post by simplyw00x on 2006-06-08
If you really want a visual interface designer your best bet is probably using glade to make GTK interfaces.

---

### Post by Atof on 2007-11-02
Well, its been an year that this post ended, however my post (which i was about to make after meticulous but futile searching through the forums till i came acroos this post :) )...... would not have been much different that what Agent Smit has written !

I have been a windows user all my life, with a little experimentation along the way in Redhat. My programming experience includes:

1) writing codes in Borland Turbo C (for DOS based softwares / projects), 
2) Visual basic (GUI and Hardware Interfacing through USB /Serial / parallel ports), 
3) Codevision AVR (for AVR system development in C / Asm)
4) Keil UV2 for 8051 and variants (C/Asm)

NOW this is what i have read, and done so far. Please correct me if i am wrong:

a) Installed GCC... for cmd line compilation of C / Cpp files
b) Anjuta IDE for GUI Based Compiler for C/CPP files
3) Eclipse for the same.
d) Glade (got installed with Anjuta) as an alternate to VB.

Now, i am having issues with understanding how to get started with these software ?! :confused: Like, Anjuta doesnt build my existing cpp / c files (previously developed in windows environment), even the simple hello world ones :(. 

For the AVR, i believe that AVR GCC will do the trick. No problems here.

For the Keil Alternative, i have no idea as yet.

Also, my Thesis requirements are such that i need to program in Ubuntu, and i am loving the experience (General Ubuntu usage-Coming from Redhat, its downright easy :)).
I have to write software with which i have to control robot(s) through USB / Firewire / Serial ports. To begin with my programming experience in Linux:

Please guide me how to Edit/compile simple dos programs in a GUI based environment. Is Anjuta/Eclipse OK? 

Other things are reserved for another post :) (coz this one os getting toooo long !)

---

### Post by Tomosaur on 2007-11-02
I have never really used Anjuta, but in Eclipse you may need to do some configuration after you've installed the C/C++ plugins. I seem to remember I needed to manually point eclipse to the include directories and such-like.

I have had a better C/C++ experience with KDevelop. I didn't need to do any extra configuration after I had it installed.

It also has a real, live, terminal embedded into the GUI - meaning you can do other stuff rather than read output. If you want you can use KDevelop as a fancy text editor then compile everything manually at the command line.

---

