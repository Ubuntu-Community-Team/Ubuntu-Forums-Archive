---
title: "What Programming Environment is Ready On Ubuntu?"
date: 2006-05-08
forum: Programming Talk
---

### Post by DA_uf on 2006-05-08
I've been frustrated trying to use the wizards that come with Anjuta, KDevelop and I think a few other IDE's.  Standard sample apps simply do not build.  How can I hope to build a wxWidgets app if even the standard apps do not build?

I remember seeing alot of Python this and Python that when installing Warty and I believe the Ubuntu developers use Python.  So maybe I'll try to learn Python.  I think I even read that Python can be compiled.

What programming environment and IDE do the developers of Ubuntu use?  Surely their programming environment is ready and comes with the standard Ubuntu release.  Is this a fair assumption?  That way I will know I am not missing a library or environment variable setting and the build and run will "Just Work".  And perhaps it will even be documented.  I would prefer a graphical drag and drop widget pallete, but I'll be happy if code builds and the API is documented well.

Basically I've been trying since Warty.  [http://ubuntuforums.org/showthread.php?p=84559#post84559](http://ubuntuforums.org/showthread.php?p=84559#post84559)

But I end up going back to MS Windows.

---

### Post by louis_nichols on 2006-05-08
I think the problem of apps not compiling is not caused by any of the IDE's you're using, but rather by missing development headers and libraries. For example, to build wx widgets you have to install libwxgtk2.4-dev (and probably others). The error message will usually tell you that package x is missing, and then you have to install package x-dev or libx-dev.

Python is a different thing, since it's not compiled, but interpreted. It still has a similar principle: it uses bindings. For example, making gui's with gtk requires python-gtk.

EDIT: I'm sure there is no special Ubuntu release for developrs :) they just take the default and install the IDE of choice, just like you can. Anyhow, I'm also pretty sure that most don't actually use IDE's. The Linux guys (I'm still a long way from being able to call myself one) like their vi, which is just a text-editor, and command-line tools. :)

---

### Post by hod139 on 2006-05-08
[codeblocks]("http://www.codeblocks.org/") is fairly new, and looks promising.    It is for C/C++, and also meant to be cross platform.

---

### Post by DA_uf on 2006-05-08
**louis_nichols**,

I have been trying to sort out if I have installed the correct libraries with *-dev.  Thanks.  I did have libwxgtk2.6-dev and some others installed.

_Anjuta wxWidgets (wxWindows project)_
./configure: line 22171: AM_OPTIONS_WXCONFIG: command not found
./configure: line 22172: syntax error near unexpected token `2.3.2,'
./configure: line 22172: `AM_PATH_WXCONFIG(2.3.2, wxWin=1)'
Completed ... unsuccessful

_Anjuta GNOME 2.0 project_
Ok, it's missing libgnomeui-dev.  By the way, the wizard began the build at the end.  I then installed libgnomeui-dev.  How do I attempt a new build at this point?  I may try Build | Auto generate... next time as this is the first line in the Build log tab.  Build | Execute and Build | Build All complained.  Anyway, I closed the project and started again.  The build reports:
Now type `make' to compile.
Completed ... successful

But the only option with "make" in the Build menu is Compile With Make which is dimmed disabled.

Anyway, I'd prefer to work with wxWidgets above.  Earlier in the Build log, there is a note about using m4_pattern_allow and to see the Autoconf documentation.  I had played with this previously with no success although I'm sure it was my negligence.

_KDevelop: C/C++_
Hmm.  It decided to build and run the wxWidgets simple sample application.  Perhaps it needed something from the installation of libgnomeui-dev (a lot of additional packages were installed with that).

[COLOR="Red"]Is there a Widget palette where I can drag and drop widgets onto my GUI and then adjust properties from KDevelop?[/COLOR]

Thank you very much for your help.

**hod139**,
Code::Blocks does look promising.  Can you build it?  I looked at this before also.
From the BUILD file, "The only external library needed to build Code::Blocks is wxWidgets.
You must compile wxWidgets as a DLL. You must also compile contrib/stc and contrib/xrc under the wxWidgets source dir. Refer to the build documentation in the wxWidgets sources on how to do it."

Sounds like fun...NOT.  Even if I was successful at building all the wxStuff, the codeblocks-1.0rc2 source tree does not respond to ./configure or make.  Not exactly the "Ready On Ubuntu" requirement I'm trying to meet.  Thanks anyway.

---

### Post by llonesmiz on 2006-05-09
I think you can solve the problem with WXCONFIG in anjuta by installing the package "wx-common".

---

### Post by hod139 on 2006-05-09
[quote=DA_uf]
** hod139**,
Code::Blocks does look promising.  Can you build it? ...

Sounds like fun...NOT.  Even if I was successful at building all the wxStuff, the codeblocks-1.0rc2 source tree does not respond to ./configure or make.  Not exactly the "Ready On Ubuntu" requirement I'm trying to meet.  Thanks anyway.
[/quote] 
Here is a prebuilt package of their latest stable release that runs on ubuntu.  [http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2-1_i386.deb]("http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2-1_i386.deb")
You don't have to build anything from hand.

---

### Post by DA_uf on 2006-05-11
**llonesmiz**,
Yes, you are correct.  I needed wx-common.  I'm surprised it was not included as a dependency with whatever else I chose for wx support.  That got me to:
```
Now type `make' to compile.
Completed ... successful
```
How do I proceed?  The only option with "make" in the Build menu is Compile With Make which is dimmed disabled at this point as with the Anjuta GNOME 2.0 project.  Thanks.  How did you deduce that?

Ahh, a look in the Anjuta Tutorial offers "Build | Build All" which invokes make.  But```
main.cc:20: error: conversion from 'const char [12]' to 'const wxString' is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t)<near match>
/usr/include/wx-2.6/wx/string.h:632: note:      wxString::wxString(int)<near match>

```
By the way; Is there a way to copy and paste from the Build log?

**hod139**,
Thanks, I'll take a look.  How did you find that?  I've only added the extra repositories listed with Synaptic.  And one other time I added a specific WINE repository.

Hmm, I'm on amd64.  I think the last time I tried an i386.deb, it complained.  In fact it was WINE related.  I thought I could run i386 stuff but apparently not from a Ubuntu amd64 install.  Had I installed the Ubuntu i386, I could use it.  Is my only option to attempt to build this one [http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2.orig.tar.gz](http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2.orig.tar.gz) ?

---

### Post by DA_uf on 2006-05-12
> Is there a Widget palette where I can drag and drop widgets onto my GUI and then adjust properties from KDevelop?
KDevelop Designer

---

### Post by hod139 on 2006-05-12
[quote=DA_uf]
**hod139**,
Thanks, I'll take a look.  How did you find that?  I've only added the extra repositories listed with Synaptic.  And one other time I added a specific WINE repository.
[/quote] I found it on the codeblocks wiki: [http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks]("http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks")

> 
Hmm, I'm on amd64.  I think the last time I tried an i386.deb, it complained.  In fact it was WINE related.  I thought I could run i386 stuff but apparently not from a Ubuntu amd64 install.  Had I installed the Ubuntu i386, I could use it.  Is my only option to attempt to build this one [http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2.orig.tar.gz]("http://neutronic.mine.nu/ubuntu-breezy/codeblocks_1.0rc2.orig.tar.gz") ? Don't use the x86 deb that I pointed you to.  I didn't realize you were on amd64.  If you look at the above wiki I posted, there is no 1.0RC2 amd64 binary available, but there is a development release one available: [http://prdownload.berlios.de/codeblocks/codeblocks_1.0r2235_amd64.deb]("http://prdownload.berlios.de/codeblocks/codeblocks_1.0r2235_amd64.deb").

These are unofficial debs, but probably will work without any problems.

---

### Post by DA_uf on 2006-05-13
> **hod139** - ...there is a development release one available...
I was hoping that this came with wxSmith, so I have some good news and some bad news
> A plugin failed to load because it was built with a different Code::Blocks SDK version.

Plugin: /usr/share/codeblocks/plugins/libwxsmith.so
Plugin's SDK version: 1.6.10
Your SDK version: 1.6.11

Woo hoo.  Burned because I have the latest technology again.  Thoughts?

---

### Post by hod139 on 2006-05-18
The only other thing I can think of is to either try a nightly build
[http://www.codeblocks.org/nightly/](http://www.codeblocks.org/nightly/)
Or take a svn snapshot of the code and try to build yourself (good luck).

The less desireable option is to wait until version 1 is officially released.

---

### Post by narcisgarcia on 2008-05-11
I'm at the same point:
> /media/disco2/programacion/anjuta/prueba_cpp-wx/src/main.cc:35: error: conversion from ‘const char [12]’ to ‘const wxString’ is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
make: *** [main.o] Error 1

I've found an independent visual designer for WX Widgets: [**wxFormBuilder**]("http://wxformbuilder.org/").

---

### Post by DA_uf on 2008-07-13
I've been on Macs since summer 2006.  Richard Stallman was right when he said, "Don't trade one proprietary vendor for another proprietary vendor".  If Apple says an update is available/recommended, guess what; they don't have standard procedures to uninstall the update.  Even when their update hoses your system.

So I'm back doing development on Ubuntu and needed to return to this thread.

NOTE TO SELF: Don't forget the build-essential package.
sudo apt-get install build-essential

---

### Post by CptPicard on 2008-07-13
Well, in a span of two years you surely have become comfortable enough with the base system (like all worthy developers) so that you no longer need any kinds of wizards which are there only to get beginners started ... and are therefore not much of a priority, and therefore are mostly broken.

---

### Post by narcisgarcia on 2008-07-14
Do you really believe that Anjuta is only a set of wizards?

How do you make graphical interfaces? With a GUI, or writing a mental calculation?

---

### Post by LaRoza on 2008-07-14
> **narcisgarcia said:**
> 
How do you make graphical interfaces? With a GUI, or writing a mental calculation?

See the sticky on making GUI and using various tools to design them.

Thread is too old, closed.

---

