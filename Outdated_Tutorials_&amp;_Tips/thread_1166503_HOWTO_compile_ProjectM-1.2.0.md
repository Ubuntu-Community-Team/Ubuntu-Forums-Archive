---
title: "HOWTO compile ProjectM-1.2.0"
date: 2009-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by dixonstalbert on 2009-05-21
ProjectM allows you to get Winamp's Milkdrop Visualizations under Ubuntu Linux.

Sammydee wrote an excellent howto here:

[http://ubuntuforums.org/showthread.php?t=749793&](http://ubuntuforums.org/showthread.php?t=749793&)

on building ProjectM from daily subversion builds.

Unfortunately, the builds got more and more unstable and thread is now 21 pages long.

The Jaunty repositorys only contain projectM libraries but not the pulseaudio execuatable that allows you to use projectM with your favorite media player. (you could use the libraries themselves with Amarok 1.4 visualization option, but Jaunty's Amarok 2 doesnt have visualization capability)

This post is how to build ProjectM from latest stable release.       


Step 1: Download source for ProjectM-1-2.0

go to this page:

[http://sourceforge.net/project/showfiles.php?group_id=104201](http://sourceforge.net/project/showfiles.php?group_id=104201)

and download the following:

libprojectM
libprojectM-qt
projectM-libvisual
projectM-libvisual-alsa
projectM-pulseaudio


Step 2: Make a directoy 'projectm' in your home directory and uncompress the downloads there. I used Archive Manager and let it use the archives same folder names.

Step 3: open a terminal and paste this command to get Apt to download some dependancies you will need to build ProjectM
 
```
sudo aptitude install libglew1.5 libglew1.5-dev ftgl-dev libpulse-dev subversion cmake libvisual-0.4-dev libsdl-dev libqt4-dev build-essential libxxf86vm-dev
```

Step 4: Build libprojectM-1.2.0
	
	a) open a terminal and cd to libprojectM-1.2.0 directory
	b) Fix Renderer.hpp and fix name of ftgl.h

open Renderer.hpp located in the libprojectM-1.2.0   directory with a text editor and fix Line 23 and Line 27	so they read:
		Line 23-  #include <ftgl.h>
		Line 27-  #include <FTGL/ftgl.h>
		save your changes
(Renderer.hpp attempts to load FTGL.h C++ header file, but in Ubuntu this file is named ftgl.h)
	
	c)Run ccmake command with -Wno-dev switch.

projectM uses cmake to configure the make file. 
While in the libprojectM-1.2.0 directory run this command

		```
ccmake -Wno-dev . 
```
Note the space before the dot, the Wno-dev switch will take care of an error message you will normally get about processor type

	
       d) from sammydees thread:

	Press "c" to configure projectM. Highlight the CMAKE_BUILD_TYPE field, press enter and type "Release" there. Press enter again. Then 		highlight the CMAKE_INSTALL_PREFIX field and change /usr/local to /usr/. Then press "c" again to configure it with those parameters.

	Now that cmake has got it's configuration right, press "g" to generate a makefile and exit.

	Then it's a simple:

	Code:

	```
make && sudo make install
```


Step 5: build libprojectM-qt-1.2.0

(Note: I am not sure if it matters what order you build projectm, projectm-qt, projectm-alsa but this is the order I used and it 		worked. I apparently also built mine with the repository versions of libprojectm installed. this usually causes all sorts of 		problems but it seems to be working okay)

	```
cd  libprojectM-qt-1.2.0
	ccmake -Wno-dev .
	change CMAKE_BUILD_Type to Release and CMAKE_INSTALL_PREFIX from /usr/local/ to /usr
	press 'c' and 'g'
	make && sudo make install
```

Step 6 build projectM-libvisual-alsa-1.2.0

	```
cd  projectM-libvisual-alsa-1.2.0
	ccmake -Wno-dev .
	change CMAKE_BUILD_Type to Release and CMAKE_INSTALL_PREFIX from /usr/local/ to /usr
	press 'c' and 'g'
	make && sudo make install
```

Step 7 build projectM-pulseaudio-1.2.0

	```
cd  projectM-pulseaudio-1.2.0
	ccmake -Wno-dev .
	change CMAKE_BUILD_Type to Release and CMAKE_INSTALL_PREFIX from /usr/local/ to /usr
	press 'c' and 'g'
	make && sudo make install
```


If everything worked okay, you should have a projectM-pulseaudio entry in your applications > Sound and video menu.

Fire up your favorite media player and play something then start projectM-pulseaudio.

Note:

as per sammydee:
(1)if you want to redo cmake configuration, erase the CMakeCache.txt file first to erase your old settings then re-run ccmake -Wno-dev .
(2) projectM will make a .projectM folder in your home directory containing config.inp file. you can tweak the settings in this file if you have poor graphics card and projectM is running really slowly.

I have Intel 915gm integrated graphics and had to set 

```
Texture Size = 512			# Size of internal rendering texture
Mesh X  = 16            	# Width of PerPixel Equation mesh
Mesh Y  = 12  
```

to get it run at 22 fps.

good luck and post how you made out.

---

### Post by diggity on 2009-07-10
Thank you!
Works like a charm.

---

### Post by louloulou on 2009-07-12
Thanks a lot dixonstalbert !!!!!!

---

### Post by quintus314 on 2009-07-24
I've been at this for about an hour, and when I finished...well...it just kind of starts and then quits out. It's open for about a nanosecond.

meh :evil:

So, can anyone tell me what's going on and/or help me fix it?
Thanks a bunch everyone.

Oh this may be useful:
I'm running Ubuntu Studio 9.0.4 and followed the directions EXACTLY.

---

### Post by eltoozero on 2009-07-26
Yes, this did work for me, although I apparently attempted to sudo make install the final projectM-pulseaudio-1.2.0 too early, and it failed.

I resolved this by deleting the directory, re-unarchiving and re-compiling, worked great.

The described settings work well on my Asus Eee 901 and give me good performance.

Thank you!!!

:D

---

### Post by eddier on 2009-07-28
Hmm,getting grief at the compile stage...


```







































































































































































































































































 CMake Error at /usr/share/cmake-2.6/Modules/CMakeDetermineSystem.cmake:144
 (FILE):
   file Internal CMake error when trying to open file:
   /home/eddie/ProjectM/libprojectM-1.2.0/CMakeFiles/CMakeOutput.log for
   writing.
 Call Stack (most recent call first):
   CMakeLists.txt:1 (PROJECT)



 CMake Error: Could not open file for write in copy operation
 /home/eddie/ProjectM/libprojectM-1.2.0/CMakeFiles/CMakeSystem.cmake.tmp

 CMake Error: : System Error: Permission denied

 CMake Error at /usr/share/cmake-2.6/Modules/CMakeDetermineSystem.cmake:156
 (CONFIGURE_FILE):
   configure_file Problem configuring file

CMake produced the following output                                             
                                                     CMake Version 2.6 - patch 2
Press [e] to exit help



```

Ive done as instructed from sammydees thread but seem to be going round in circles.

What am I doing wrong??

eddie

PS. dear oh dear even copy and paste in here is going screwy.  Basically,when  I do the alterations to BUILD_TYPE etc and press 'c' is this whilst on the same screen after pressing 'enter'?  I'm also confused about the 'press 'g' and exit' instruction There is no 'exit' command key.

---

### Post by Cresho on 2009-08-09
this doesnt work anymore. appearantly there are files missing.

any ideas?

---

### Post by quintus314 on 2009-08-09
Okay, I've completely given up with ProjectM.
I've found an alternative, though.

First of all, get WINE.
```
sudo apt-get install wine
```
Then get Winamp. Just get that from [their website]("http://www.winamp.com/").

Go and configure Winamp with nullsoft tiny visualization and put it on advanced mode under config.

Type "go to address" and use linein://
Then Press play, start the visualization, and plug something into the linein port.

Good luck, after a bit of tweaking around this worked just fine for me!

---

### Post by nerdy_kid on 2009-10-08
hmm, getting this error when I make:


```
[  2%] Building CXX object CMakeFiles/projectM.dir/BuiltinParams.o
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp: In member function ‘int BuiltinParams::load_builtin_param_float(const std::string&, void*, void*, short int, float, float, float, const std::string&)’:
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:47: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:48: error: ‘stdout’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:48: error: ‘fflush’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:61: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:62: error: ‘stdout’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:62: error: ‘fflush’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:75: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:76: error: ‘stdout’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:76: error: ‘fflush’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:89: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:90: error: ‘stdout’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:90: error: ‘fflush’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:96: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp: In member function ‘int BuiltinParams::init_builtin_param_db(const PresetInputs&, PresetOutputs&)’:
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:252: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:253: error: ‘stdout’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:253: error: ‘fflush’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:259: error: ‘printf’ was not declared in this scope
/home/jesse/projectm/libprojectM-1.2.0/BuiltinParams.cpp:263: error: ‘printf’ was not declared in this scope
make[2]: *** [CMakeFiles/projectM.dir/BuiltinParams.o] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
```
any idea?  I tryed the svn build which compiled fine (strange enough) but has to many qwircks for me to use so i uninstalled it. ?

---

### Post by nerdy_kid on 2009-10-09
ok, i got it never mind...wouldn't compile on 9.10 i guess, compiled it on 9.04 and copy/pasted the binaries  ;)

---

### Post by seddonym on 2009-11-13
I have the same errors trying to compile libprojectM running Karmic (9.10).

Don't know much about compiling source code and installing, any idea how to fix this?

(I don't have 9.04 installed).

Thanks

EDIT:

I solved this for Karmic (I think it's something to do with the latest version of GCC. This post showed me what to do: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586456.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586456.html)

All I did was edit libprojectM-1.2.0/BuiltinParams.cpp and added the line *#include <cstdio>* after the line *#include "Algorithms.hpp"*.

I then followed the instructions at the top of this thread and everything worked fine.

Thanks

---

### Post by mushr00m on 2009-11-14
Thanks so much.  Love it!

---

### Post by wombalton on 2009-11-21
i got the libprojectM-1.2.0 compiled and installed (on karmic - thanks seddonym) but when i try to configure libprojectM-qt-1.2.0 i get thise message:
```
 CMake Error at CMakeLists.txt:30 (MESSAGE):
   projectM not detected! Please install the projectM module or build from top
   level projectM source directory.

```

how can that be?? any idea? please help

---

### Post by riek on 2009-11-23
I'm stuck here (using Karmic). I changed a bit more in the code, using this diff-files: [http://ubuntuforums.org/showpost.php?p=5716127&postcount=177](http://ubuntuforums.org/showpost.php?p=5716127&postcount=177)
Now i'm that frustrated that i stopped trying...
Perhaps i'll give it sometimes another shot. But i'm using amarok14 anyway, so what the hack... :evil:
```
erik@erik-desktop:~/projectm/projectM-libvisual-alsa-1.2.0$ make && sudo make install
Scanning dependencies of target projectM-libvisual-alsa
[ 16%] Building C object CMakeFiles/projectM-libvisual-alsa.dir/projectM-libvisual-alsa.o
[ 33%] Building C object CMakeFiles/projectM-libvisual-alsa.dir/display.o
[ 50%] Building C object CMakeFiles/projectM-libvisual-alsa.dir/glxdriver.o
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:8:38: error: X11/extensions/xf86vmode.h: No such file or directory
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:70: error: expected specifier-qualifier-list before &#8216;XF86VidModeModeInfo&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c: In function &#8216;native_create&#8217;:
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:132: error: &#8216;XF86VidModeModeInfo&#8217; undeclared (first use in this function)
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:132: error: (Each undeclared identifier is reported only once
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:132: error: for each function it appears in.)
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:132: error: &#8216;modes&#8217; undeclared (first use in this function)
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:146: error: &#8216;GLXNative&#8217; has no member named &#8216;key&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:160: error: &#8216;GLXNative&#8217; has no member named &#8216;deskMode&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:208: error: &#8216;GLXNative&#8217; has no member named &#8216;x&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:208: error: &#8216;GLXNative&#8217; has no member named &#8216;y&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:209: error: &#8216;GLXNative&#8217; has no member named &#8216;width&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:209: error: &#8216;GLXNative&#8217; has no member named &#8216;height&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:209: error: &#8216;GLXNative&#8217; has no member named &#8216;depth&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:211: error: &#8216;GLXNative&#8217; has no member named &#8216;depth&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:218: error: &#8216;GLXNative&#8217; has no member named &#8216;WM_DELETE_WINDOW&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:219: error: &#8216;GLXNative&#8217; has no member named &#8216;WM_DELETE_WINDOW&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:221: error: &#8216;GLXNative&#8217; has no member named &#8216;lastwidth&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:222: error: &#8216;GLXNative&#8217; has no member named &#8216;lastheight&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c: In function &#8216;native_close&#8217;:
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:244: error: &#8216;GLXNative&#8217; has no member named &#8216;deskMode&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c: In function &#8216;native_getvideo&#8217;:
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:304: error: &#8216;GLXNative&#8217; has no member named &#8216;width&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:304: error: &#8216;GLXNative&#8217; has no member named &#8216;height&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:306: error: &#8216;GLXNative&#8217; has no member named &#8216;video&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c: In function &#8216;native_drainevents&#8217;:
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:334: error: &#8216;GLXNative&#8217; has no member named &#8216;lastwidth&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:335: error: &#8216;GLXNative&#8217; has no member named &#8216;lastheight&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:337: error: &#8216;GLXNative&#8217; has no member named &#8216;width&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:338: error: &#8216;GLXNative&#8217; has no member named &#8216;height&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:340: error: &#8216;GLXNative&#8217; has no member named &#8216;video&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:359: error: &#8216;GLXNative&#8217; has no member named &#8216;key&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:368: error: &#8216;GLXNative&#8217; has no member named &#8216;key&#8217;
/home/erik/projectm/projectM-libvisual-alsa-1.2.0/glxdriver.c:378: error: &#8216;GLXNative&#8217; has no member named &#8216;WM_DELETE_WINDOW&#8217;
make[2]: *** [CMakeFiles/projectM-libvisual-alsa.dir/glxdriver.o] Fehler 1
make[1]: *** [CMakeFiles/projectM-libvisual-alsa.dir/all] Fehler 2
make: *** [all] Fehler 2

```

---

### Post by eddier on 2009-11-23
If you are running K.K.

Save yourself a lot of hassle and install Audacious,it comes complete with projectM.

eddie;)

---

### Post by bennyto on 2009-11-27
phew ... i finally succeed in the way that all the stuff has installed OK on Karmic thanks to this 

```
EDIT:

I solved this for Karmic (I think it's something to do with the latest version of GCC. This post showed me what to do: [http://www.mail-archive.com/debian-b...msg586456.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586456.html")

All I did was edit libprojectM-1.2.0/BuiltinParams.cpp and added the line *#include <cstdio>* after the line *#include "Algorithms.hpp"*.

```but now
I get a Segmentation Fault when i open projectM-pulseaudio

```
bennyto@ubuntulaptop:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/bennyto/.projectM/config.inp
MAX SAMPLES:2048
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci-0000_00_14.2.analog-stereo.monitor" 
Erreur de segmentation
```i know i'm close to it but !...! i still need help :-k

any solutions ??[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]

---

### Post by dharmaurchin on 2010-01-06
> **eddier said:**
> If you are running K.K.

Save yourself a lot of hassle and install Audacious,it comes complete with projectM.

eddie;)

Hey,

I installed audacious but projectM doesn't appear in the visualization plugins list.
the libprojectm-1.0.so file is here, and there aren't any errors about failing to load projectm

please help, i feel like i've tried everything to get projectM to work, standalone projectM, xmms projectM, nothing!

---

### Post by dharmaurchin on 2010-01-06
what version of audacious are you using?  do you need the libvisual-projectm package from ubuntu repository?

---

### Post by nerdy_kid on 2010-01-07
have some debs i built with checkinstall if anyone is interested.  Is the pulseaudio projectm....

---

