---
title: "Compiling KexxBros"
date: 2010-04-23
forum: Packaging and Compiling Programs
---

### Post by xzcallaway on 2010-04-23
Hello, I'm trying to compile KexxBros, but cant even get past the first step.  When I run make in the terminal I get the following stuff:

zach@zach-laptop:~/Desktop/kexxbros-0.1.3/src$ make
Compiling kexxbros.cpp
In file included from data.h:26,
                 from intro.h:25,
                 from kexxbros.h:24,
                 from kexxbros.cpp:19:
caimagemanipulation.h:42: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
caimagemanipulation.h:42: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
caimagemanipulation.h:43: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
caimagemanipulation.h:43: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
caimagemanipulation.h:44: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
caimagemanipulation.h:44: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from intro.h:25,
                 from kexxbros.h:24,
                 from kexxbros.cpp:19:
data.h:50: error: &#8216;CL_Surface&#8217; was not declared in this scope
data.h:50: error: template argument 1 is invalid
data.h:50: error: template argument 2 is invalid
data.h:51: error: &#8216;CL_Surface&#8217; was not declared in this scope
data.h:51: error: template argument 1 is invalid
data.h:51: error: template argument 2 is invalid
data.h:55: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
data.h:55: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
data.h:56: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
data.h:56: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
data.h:57: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
data.h:57: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from kexxbros.h:24,
                 from kexxbros.cpp:19:
intro.h:47: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
intro.h:47: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
intro.h:48: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
intro.h:48: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
intro.h:49: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
intro.h:49: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from mainmenu.h:28,
                 from kexxbros.h:25,
                 from kexxbros.cpp:19:
startgame.h:36: error: &#8216;CL_Font&#8217; has not been declared
startgame.h:57: error: ISO C++ forbids declaration of &#8216;CL_Font&#8217; with no type
startgame.h:57: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
startgame.h:69: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
startgame.h:69: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
startgame.h:70: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
startgame.h:70: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
startgame.h:71: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
startgame.h:71: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
startgame.h:72: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
startgame.h:72: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
startgame.h:73: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
startgame.h:73: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from mainmenu.h:29,
                 from kexxbros.h:25,
                 from kexxbros.cpp:19:
about.h:52: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
about.h:52: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
about.h:53: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
about.h:53: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
about.h:54: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
about.h:54: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
about.h:56: error: ISO C++ forbids declaration of &#8216;CL_Font&#8217; with no type
about.h:56: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from kexxbros.h:25,
                 from kexxbros.cpp:19:
mainmenu.h:60: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:60: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:61: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:61: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:62: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:62: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:63: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:63: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:64: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:64: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:65: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:65: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:66: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:66: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:67: error: ISO C++ forbids declaration of &#8216;CL_Surface&#8217; with no type
mainmenu.h:67: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:69: error: ISO C++ forbids declaration of &#8216;CL_Font&#8217; with no type
mainmenu.h:69: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:70: error: ISO C++ forbids declaration of &#8216;CL_Font&#8217; with no type
mainmenu.h:70: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:76: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
mainmenu.h:76: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:77: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
mainmenu.h:77: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:78: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
mainmenu.h:78: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mainmenu.h:79: error: ISO C++ forbids declaration of &#8216;CL_InputButton_Group&#8217; with no type
mainmenu.h:79: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from kexxbros.cpp:19:
kexxbros.h:32: error: expected class-name before &#8216;{&#8217; token
cc1plus: warnings being treated as errors
kexxbros.cpp: In member function &#8216;virtual char* KexxBrosApplication::get_title()&#8217;:
kexxbros.cpp:34: error: deprecated conversion from string constant to &#8216;char*&#8217;
kexxbros.cpp: In member function &#8216;virtual int KexxBrosApplication::main(int, char**)&#8217;:
kexxbros.cpp:64: error: &#8216;strcmp&#8217; was not declared in this scope
kexxbros.cpp:82: error: &#8216;init_display&#8217; is not a member of &#8216;CL_SetupCore&#8217;
kexxbros.cpp:86: error: &#8216;CL_Display&#8217; has not been declared
kexxbros.cpp:96: error: &#8216;CL_MouseCursor&#8217; has not been declared
kexxbros.cpp:100: error: &#8216;CL_MouseCursor&#8217; has not been declared
kexxbros.cpp:103: error: &#8216;CL_Display&#8217; has not been declared
kexxbros.cpp:104: error: &#8216;CL_Display&#8217; has not been declared
kexxbros.cpp:105: error: &#8216;CL_Display&#8217; has not been declared
kexxbros.cpp:106: error: &#8216;CL_Display&#8217; has not been declared
kexxbros.cpp:111: error: &#8216;init_sound&#8217; is not a member of &#8216;CL_SetupCore&#8217;
make: *** [kexxbros.o] Error 1

Can somebody tell me what to do to get past this.  You can download the tar.gz at: 
[http://xzcallaway.synthasite.com/problems.php](http://xzcallaway.synthasite.com/problems.php)

---

### Post by SevenMachines on 2010-04-23
It seems as though that version of kexxbros is incompatible with the newer clanlib libraries, unsurprising since it looks like the last change was 10 years ago. Someone would need to rewrite probably quite a lot of it to make it work in 2010, unless its moved development from sourceforge to somewhere else and is still being worked on

---

### Post by gmargo on 2010-04-23
With a handful of minor patches, I got it to compile and run on 8.04 Hardy.  At least it puts up a display; I didn't figure out how to play it yet.

Attached is the patch to the kexxbros-0.1.3 source code.

---

### Post by xzcallaway on 2010-04-24
Thank you for the patch.  but I haven't been able to figure out what to do with it yet.  Can you tell me where to put the patch in order to compile or run kexxbros.

---

### Post by gmargo on 2010-04-24
Patching concept:[_http://en.wikipedia.org/wiki/Patch_(Unix)_.]("http://en.wikipedia.org/wiki/Patch_%28Unix%29")

The file I posted is a "patch" file, which is the output of a "diff -r -u" between the original directory and the working directory.

Copy the attachment (kexxbros-0.1.3-patch-hardy.txt.gz) to your workspace, and apply the difference with the **patch(1)** command.  Since your source code is in ~/Desktop/kexxbros-0.1.3, I will use that path as an example.
```

$ mv kexxbros-0.1.3-patch-hardy.txt.gz ~/Desktop
$ gunzip kexxbros-0.1.3-patch-hardy.txt.gz
$ cd kexxbros-0.1.3
$ patch -p1 < ../kexxbros-0.1.3-patch-hardy.txt

```The output you should see is:
```

$ patch -p1 < ../kexxbros-0.1.3-patch-hardy.txt
patching file src/Makefile
patching file src/about.cpp
patching file src/caimagemanipulation.h
patching file src/data.cpp
patching file src/intro.cpp
patching file src/kexxbros.cpp
patching file src/kexxbros.h
patching file src/loading.h
patching file src/mainmenu.cpp
patching file src/startgame.cpp

```
If you open the kexxbros-0.1.3-patch-hardy.txt in a text editor, you will see how the diffs are represented.  Quite simple really, just line additions and deletions.

---

