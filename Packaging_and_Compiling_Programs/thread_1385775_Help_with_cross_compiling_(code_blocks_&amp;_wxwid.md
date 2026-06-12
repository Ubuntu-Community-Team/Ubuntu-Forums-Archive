---
title: "Help with cross compiling (code blocks &amp; wxwidgets)"
date: 2010-01-19
forum: Packaging and Compiling Programs
---

### Post by scared0o0rabbit on 2010-01-19
So I've spent a couple hours now looking at this, and I just can't figure it all out.  It seems like most of the information I've found is somewhat old.

I started with using this guide:
[http://wiki.codeblocks.org/index.php?title=Cross_Compiling_wxWidgets_Applications_on_Linux](http://wiki.codeblocks.org/index.php?title=Cross_Compiling_wxWidgets_Applications_on_Linux)

but I'm stuck at the step of wxWidgets Cross Build.  That is to say that the guide references some prebuilt binaries on their server or compiling from source from their server or the wxwidgets website.  I'm just totally lost.

What I really just want to do, and I don't care if I can't do it from within code blocks truthfully, is to compile my wxwidget program into a windows executable.  If I don't worry about compiling from within codeblocks I then find this: [http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux](http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux)

However, I'm running into problems with these steps: 

[LIST]
[*] Download wxWidgets source
[*] Compile with   ./configure --prefix=/usr/local/i586-mingw32  --host=i586-mingw32msvc --build=i686-linux *--your_optional_switches*
[/LIST]
I have no idea what I should do with the source once I get it, and I have no idea how to use/compile with ./configure.

So why don't I just compile my program in windows you ask?  Well I did try that after looking at this stuff for a couple of hours.  I then went over into windows and found that to use wxwidgets in windows I have to compile it there first too.  Following the directions (which look like they might be outdated as well) I never did manage to get it to compile (or at least compile totally I never did manage to get it to find wx wxprec.h), which as a result meant that I couldn't compile my program natively.

I find it hard to believe that it could be so hard to get something compiled for both linux and windows.  It seems like there should be a step by step guide somewhere to setting up codeblocks to work with wxwidgets without having to go out and find some other code and compile it and manually configure codeblocks to look in the right place for it in windows.  Or there should be a step by step, copy and paste this, do exactly this, guide to compiling a wxwidget for windows.  It was a piece of cake to set up code blocks and wxwidgets together to compile for Linux, why does it have to be so complicated for windows?


Edit:

I guess I'm just very frustrated that I've spent hours trying to compile a windows executable without any success.  My widget works great in Ubuntu and shouldn't have any trouble compiling for Windows (it's really quite simplistic).  If anyone can tell me what I need to know I'd greatly appreciate it.  As it is, I've got minGW32 installed, but I don't even know what to do to compile a windows executable with it in ubuntu, so anything at all will help.

---

### Post by SevenMachines on 2010-01-20
hi there, i can't help much with how to set up codeblocks but trying out a few things on [http://wiki.codeblocks.org/index.php?title=Cross_Compiling_wxWidgets_Applications_on_Linux](http://wiki.codeblocks.org/index.php?title=Cross_Compiling_wxWidgets_Applications_on_Linux) suggests that the guide should work fine.

as it says, there are 2 ways you could get the cross compiled wxwidgets installed

1. build from source
- download and extract the source from [wxwidgets]("http://www.wxwidgets.org/")
- enter the source directory from the command line and then run the commands
```
$./configure prefix=/usr/i586-mingw32msvc --host=i586-mingw32msvc --enable-unicode --build=`./config.guess` --disable-shared
$make
$make install
```which seems to work fine

or, perhaps the simpler way

2. add jens repository to /etc/apt/sources.list by adding the lines 
```
deb http://apt.jenslody.de/ any main
deb-src http://apt.jenslody.de/ any main
```then update and install the package libwxmsw2.8-dev which will install all the necessary windows libraries which you would have done manually if you built from source in [1] above.
The packages from jens repository seem to work fine so this is probably the quickest and easiest way

Then you can move on to setting up codeblocks as described in the guide

---

### Post by scared0o0rabbit on 2010-01-20
Thanks!  That was more helpful than you might think.  I wasn't exactly sure what I needed to get, and that tells me.  I'll take another crack at this in a few hours when I've got time to sit down and mess with it.

---

### Post by scared0o0rabbit on 2010-01-20
Well it compiles and runs.  Have some weird graphical things going on that I think I can fix.  Thanks for the help!

---

