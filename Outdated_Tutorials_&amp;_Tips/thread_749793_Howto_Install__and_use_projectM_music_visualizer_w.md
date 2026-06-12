---
title: "Howto: Install  and use projectM music visualizer with pulseaudio support on Hardy"
date: 2008-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by sammydee on 2008-04-08
[SIZE="4"]**NEWS UPDATE 23/08/08: It seems the recent svn releases are becoming more and more broken recently and are becoming harder to compile/run without issues. I recommend installing the 1.2 release version instead of attempting to get svn to work for now, unless you are very brave.**[/SIZE]

[SIZE="5"]**_Introduction:_**[/SIZE]

Recently I finally got completely sick of Goom and went on a hunt for other visualizations for linux. I found libvisual which gave me about eight more effects, but I still wasn't really satisfied. Some of you out there may have heard of or used milkdrop, a visualization framework for winamp on windows. Milkdrop has been around for years, thousands of so called "presets" have been written for it, and it uses hardware acceleration and iterative processing to produce some seriously stunning and very trippy music visualizations.

[Here]("http://www.youtube.com/watch?v=TmBNkX5iTiU") is a youtube video showing a (very small) selection of presets available in milkdrop and what they look like.

There is a port of this framework to linux and opengl called [projectM.]("http://projectm.sourceforge.net/") ProjectM contains plugins for xmms, alsa (experimental), libvisual, jack, and most importantly, pulseaudio. With pulseaudio support comes projectM's real strength - it can produce visualizations for ANY program or sound stream that pulseaudio handles. Here's a screenshot of the sort of thing projectM is capable of:

[IMG]http://img.photobucket.com/albums/v663/seivadmas/screenshot2.png[/IMG]

This guide will demonstrate how to install the latest svn projectM on Hardy Heron. This method will probably work fine on gutsy too but I haven't tested it myself. At the time of writing there IS a version in the repos for hardy, but I couldn't make it work and it is very old anyway, plus it has no pulseaudio support.

*NOTE: ProjectM uses opengl and heavy iterative processing. You will need a good video card with decent opengl drivers and a fast cpu to get pleasing performance. Based on my (albeit limited) experience I would recommend at least a 2ghz pentium 4 and a gpu at least as powerful as a nvidia 6400. You absolutely CANNOT make this work without hardware opengl support.*

**_[SIZE="5"]Install:[/SIZE]_**

We will compile projectM with libvisual and pulseaudio support. First thing we will need to do is install the dependencies:

```
sudo aptitude install libglew1.5 libglew1.5-dev ftgl-dev libpulse-dev subversion cmake libvisual-0.4-dev libsdl-dev libqt4-dev build-essential
```

[I]**IMPORTANT NOTE: I may have missed something here, if ANYONE gets compilation errors, pm me immediately and I'll add the missing dependencies to this list.**
[/I]
With the dependencies in place, it's time to download the source:

```
cd ~
mkdir projectm
cd projectm
svn co https://projectm.svn.sf.net/svnroot/projectm/trunk projectM-Trunk
```
[I]
NOTE: Svn can take a long time to fetch all the code, so be patient while it downloads.[/I]

When it has finished, change to the source directory:

```
cd projectM-Trunk/src
```

ProjectM does NOT use autoconf, so there is no ./configure to do, we will use cmake instead:

```
ccmake .
```
[I]
NOTE: See the '.' above? That's important! You must include it in your command or it won't work.[/I]

Now cmake will load. Press "c" to configure projectM. Highlight the CMAKE_BUILD_TYPE field, press enter and type "Release" there. Press enter again. Then highlight the CMAKE_INSTALL_PREFIX field and change /usr/local to /usr/. Then press "c" again to configure it with those parameters. If you want to use projectM with jack or xmms, you will need to hunt down the dependencies for these on your own, they aren't covered here (yet?).

*NOTE: If you run into dependency problems when trying to configure cmake, it can usually be solved by doing "rm CMakeCache.txt" in the src directory.*

Now that cmake has got it's configuration right, press "g" to generate a makefile and exit.

Then it's a simple:

```
make && sudo make install
```

*NOTE: If you get build errors, please see the build errors section at the bottom of the guide.*

Great! ProjectM should be installed.

*NOTE: I used to suggest testing projectm with projectm-test or projectm-test-texture here, but it really isn't necessary unless you are a developer or debugging and in which case already know what you are doing. There used to be an issue with projectm-test where it locked up the mouse cursor, but I think this is fixed in the latest svn. Either way there isn't really any need for a normal user to run either of these commands anyway.*

Now that it's working, you can finally use projectM with some music! Put a good tune on (I recommend some pink floyd) go to applications/sound and video and click on projectm-pulseaudio.

*NOTE: You can also run it from a terminal using:*

```
projectM-pulseaudio
```

*NOTE 2: The first time I tried it, my fonts looked disgusting. This is due to a bug in qt4, so you may want to check out the workaround [here]("http://ubuntuforums.org/showthread.php?t=672272").*

Woo! We have funky visuals! Now on to...

**_[SIZE="5"]Usage:[/SIZE]_**

You can launch projectM-pulseaudio from the terminal or from the gnome menu under sound and video.

Controls (these are listed in the menu under "hotkeys":

m - brings up a menu
f - toggles fullscreen on/off
l - "locks" to a particular preset
y - toggles shuffle mode
n - next preset
p - previous preset
r - selects random preset

F1 - Help menu
F2 - Toggles song title on/off (doesn't work in libvisual or pulseaudio as far as I can tell)
F3 - Toggle preset name on/off
F4 - Toggel rendering info on/off
F5 - Shows fps

**_[SIZE="5"]Presets:[/SIZE]_**

This is the fun part! ProjectM comes with loads of good presets already, but I recommend searching the web for some more that you like, there are literally thousands out there. My favourite package is the Better Life Through Chemicals compilation, available as a torrent [here]("http://thepiratebay.org/tor/4124453/").

When you download a preset package, you will need to extract all the files to a directory where projectM can find it. I put mine in ~/projectM/presets and then did:

```
cd /usr/share/projectM/presets && sudo ln -s ~/projectm/presets/ others
```

I think this is probably the cleanest way of doing it, because having to become root to add new presets to a /usr/ directory every time is a pain.

*NOTE: For those that don't understand the command, it creates a symbolic link in the projectM presets directory that links to a directory in your home folder. Any preset you put in this directory will be seen and can be used by projectM.*

**_[SIZE="5"]Configuring projectM to look AWESOME:[/SIZE]_**

Go to settings/configure projectM in the menu to change performance options. You will want to tweak the projectM settings to get the most awesome looking visuals on your pc. Here is a quick guide to getting the most out of projectM, the options are numbered from most important to least important:

**1)** Far and away the best thing you can do to IMMEDIATELY get much better looking graphics is to make sure the texture size is at least 1024. If you have a fairly decent graphics card (nvidia 6600gt or better) you can probably get away with making this higher. I use a nvidia geforce go 7400 and I couldn't get texture sizes about 1024 with compiz turned on without severe stuttering. 1024 is easily enough to make it look good however.

**2)** The second most important thing to do is enable sync to Vblank in your graphics options! Otherwise you will get tearing and it looks horrible. For nvidia cards with binary drivers you can do this in the nvidia-settings utility (if you don't have this installed, you can install it by doing "sudo aptitude install nvidia-settings".). For other cards you will need to use whatever control utility you usually use. Cards with open source drivers use driconf I believe.

**3)** Third most important thing to do is set the maximum fps to the refresh of your monitor. The standard for LCDs is 60 hz. If you have a monitor with a very high refresh (eg 120hz) it is probably a good idea to set maximum fps to a fraction of this. Anything over 40hz and below 60hz is probably ok. If you have a low end system and you are getting stuttering, if all else fails you may need to set the max frame rate to about 20-30fps. Be warned, it takes away a lot of the aesthetics of the effects to be run at a lower fps (in my opinion, anyway).

**4)** Mesh size should be set as large as possible. Whilst the three previous settings should have been configured mainly with graphics card power in mind, the mesh size setting is pretty much solely cpu limited. The first mesh size parameter is the x axis, the second is the y axis. You should set these with the aspect ratio of your monitor in mind for best performance. I have a resolution of 1280x800 and a 1.8GHZ core duo cpu. The largest mesh size I can comfortably use is 48 x 30. If you have a 4:3 monitor you will need to change mesh size ratios accordingly.

**5)** The easter egg parameter... It's a mystery parameter! Set it to whatever you like. (HINT: If you really want to find out what it does, google is your friend).

That's pretty much it for performance, the other options should be fairly obvious.

*NOTE: An important point to remember - at the moment, projectM does NOT apply the settings to the currently running application. When you have finished configuring it, you will need to save the config, exit then relaunch projectM.*

**_[SIZE="5"]Other/misc stuff[/SIZE]_**

**_Milkdrop 2.0 support AKA cool shader effects_**

If you have a newer nvidia card, you're in luck! You can enable shader effects and get some awesome effects with milkdrop 2.0 presets. First you need to:

```
sudo aptitude install nvidia-cg-toolkit
```

then enable cg in cmake and compile. This will not change behavious with the standard presets, but try the presets in the projectM-Trunk/presets_milkdrop_200/ directory and see some awesome effects. This is still very experimental and probably won't work with anything other than nvidia 6xxx, 7xxx 8xxx or 9xxx cards.

**_Jack support:_**

You will need the jackd and libjack-dev libraries, then turn on jack support in cmake before configuring. I have installed this, but I have NOT tested it (actually I don't know how to use jack!) so you are pretty much on your own here. If you succeed in making it work, let me know and I'll integrate it into the howto.

**_Updating:_**

ProjectM seems to get updated fairly often, so it's always nice to have the latest version. You can do this by changing into the projectM-Trunk directory and typing "svn update", then reconfiguring, making and installing again.

**_Further help/documentation:_**

Some of this guide is referenced from the [wiki pages]("http://projectm.wiki.sourceforge.net/Installation+Instructions") on projectM. This guide covers most of what is there, but you might want to check it out anyway. I've also found the developer on IRC to be most helpful, the channel is #projectm on irc.freenode.net.

**_Pulseaudio support:_**

Don't forget that because projectM uses pulseaudio, it can do everything that pulseaudio can do. In the menu, you can select which pulseaudio source to use as the music input to the visualizations. This includes network sound resources.[SIZE="4"] Yes, you CAN use projectM as a visualizer for the music ANOTHER PC is playing![/SIZE]

It's easy to do this. In the projectm-pulseaudio menu, go to Settings/Pulse audio settings. Uncheck the tick box that says "try first available playback monitor, and choose which source to use! It's automatic, zero configuration and perfectly synchronized even over high latency networks (don't ask me how, I don't understand it either, it's like magic :-) ). You can also use this to select different sound cards on the same machine if you want to.
[B][U]
Build errors:[/U][/B]

UPDATE: It seems as though some or all of the following issues are solved now. If you get these or any other build errors with the latest version of projectm, please post in this thread saying what the problem was and how you encountered it.

[I]1) Due to some bizarre bug in cmake, or the way the code is packaged, in my version of projectm I got an error from make install saying something about /projectM-engine/config.inp not found. If this happens to you, execute the following command:

```
cp config.inp projectM-engine/config.inp && sudo make install
```

2) Some users have reported build errors looking something like this:

> CMake Error: Error in cmake code at
/home/$user/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake:341:
FILE INSTALL cannot find file "/home/$user/projectm/projectM-Trunk/src/libprojectM.pc" to install.
Current CMake stack: 
[2]	/home/$user/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake
[1]	/home/$user/projectm/projectM-Trunk/src/cmake_install.cmake
make: *** [install] Error 255

If you get these errors, johnl has kindly offered the following solution:

```
sudo make install # this should fail
cp projectM-qt/libprojectM-qt.pc ./
cp projectM-engine/libprojectM.pc ./
sudo make install # now we should be ok
```

3) Some users have reported build problems related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148") in libqt4-opengl-dev. Solution is documented [here]("http://ubuntuforums.org/showpost.php?p=4993288&postcount=87").

4) If you have any other problems building/installing, from now on I will not add these to this howto, as it is starting to get unmanageably long. It's probably better to read through the entire thread to see if somebody else has encountered the same problem. If nobody has, post in the thread and see if somebody can help.
[/I]

That concludes the projectM install and usage tutorial. If you have any problems/suggestions, please post in this thread, and someone will help you out. Enjoy your awesomely trippy eye candy!

---

### Post by struktured on 2008-04-09
One note on the very well written tutorial above:

The cmake issue of "config.inp.in" not being copied correctly has been resolved (hopefully), so don't fret over that concern.

---

### Post by punkrockguy318 on 2008-04-11
I can compile okay when I turn FTGL support off, but when I try to copmile with FTGL I get this error:
```

[ 43%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TimeKeeper.o
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [projectM-engine/libprojectM.so.2.00] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
lukas@lukas-desktop:~/Desktop/projectm/projectM-Trunk/src$ 

```

Also, projectm runs very sketchy when compiz is running.  

One feature that I miss from milkdrop that would be simple to implement would be desktop mode.

I eventually got it to compile after turning font support off and changing the SDL prefix to /usr.  I also had to copy some *.pc files into the src directory for the make install to work.


AWESOME program, but I just hope to see the build process cleaned up in the future.  It's getting better, but it's still not working completely.



Oh, and by the way I do have the ftgl-dev lib installed at version 2.1.2-3

Thanks for your time, and thanks for your work on this awesome app.

---

### Post by kefurd06 on 2008-04-12
i get an error while fetching dependencies...
```

Couldn't find any package whose name or description matched "lib-glew1.5"
Couldn't find any package whose name or description matched "lib-glew1.5-dev"
Couldn't find any package whose name or description matched "lib-glew1.5"
Couldn't find any package whose name or description matched "lib-glew1.5-dev"

```
and subsequently i get an error when i try to MAKE...
```

In file included from /home/kevin/projectm/projectM-Trunk/src/projectM-engine/Renderer.hpp:4,
                 from /home/kevin/projectm/projectM-Trunk/src/projectM-engine/projectM.cpp:58:
/home/kevin/projectm/projectM-Trunk/src/projectM-engine/FBO.hpp:32:21: error: GL/glew.h: No such file or directory

```

a little help?

---

### Post by punkrockguy318 on 2008-04-12
```
sudo apt-get install libglew1.5 libglew1.5-dev
```

---

### Post by sputty01 on 2008-04-13
```
CMake Error: Error in cmake code at
/home/sputty01/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake:341:
FILE INSTALL cannot find file "/home/sputty01/projectm/projectM-Trunk/src/libprojectM.pc" to install.
Current CMake stack: 
[2]	/home/sputty01/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake
[1]	/home/sputty01/projectm/projectM-Trunk/src/cmake_install.cmake
make: *** [install] Error 255

```
:confused:

---

### Post by quadm on 2008-04-13
> **sputty01 said:**
> ```
CMake Error: Error in cmake code at
/home/sputty01/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake:341:
FILE INSTALL cannot find file "/home/sputty01/projectm/projectM-Trunk/src/libprojectM.pc" to install.
Current CMake stack: 
[2]	/home/sputty01/projectm/projectM-Trunk/src/projectM-engine/cmake_install.cmake
[1]	/home/sputty01/projectm/projectM-Trunk/src/cmake_install.cmake
make: *** [install] Error 255

```
:confused:

I get the same thing every time i try.

---

### Post by johnl on 2008-04-13
I was able to get it to install by doing the following after getting the same errors you guys did:

(from the src/ directory)
```

sudo make install # this should fail
cp projectM-qt/libprojectM-qt.pc ./
cp projectM-engine/libprojectM.pc ./
sudo make install # now we should be ok

```

---

### Post by sputty01 on 2008-04-14
Thanks johnl :) worked a treat, its users like you that make using linux such an awesome experience!

---

### Post by atlas95 on 2008-04-14
Hello,
Thanks for this howto, this is working, but I have a nvidia 8400GS on my dell m1330 and I search the best settings, I only have 256mb of ram on the graphic card, and 4gb ddr.
My resolution is 1280x800, I want to obtain the better render.

Best regards

---

### Post by sammydee on 2008-04-15
Hi all, I have included johnl's fix for the cmake error in the main howto - thanks to johnl for pointing out this problem, let's hope it's fixed in svn quickly.

Yes, the build process is unnecessarily complicated. Unfortunately I don't have the knowledge yet to build good quality debian packages to make it easier for everyone. If anyone has problems, please post here in this thread and I'll do my best to help.

Also, don't forget to try IRC, I got a lot of help from the dev(s) when I posted there.

atlas95: Have you read the "Configuring projectm" section in the main tutorial?

---

### Post by atlas95 on 2008-04-15
Sorry it is good, I have read this at to soon :-\"

---

### Post by punkrockguy318 on 2008-04-15
On the 64 bit ubuntu, I cannot compile projectm with the font support.  Anyone have any ideas on that?

But currently there is a conflict between projectm and compiz.  When they run together, you'll experience flicker.  Hopefully this bug will be fixed.  However, until then you can run metacity (the fallback window manager) when you run projectm.  when you run my script, the fallback window manager will be used so the flicker will be eliminated.

```

#!/bin/sh
metacity --replace &
projectM-pulseaudio
compiz --replace &

```

---

### Post by sammydee on 2008-04-15
oops, double post. mods delete this please.

Sam

---

### Post by sammydee on 2008-04-15
> **punkrockguy318 said:**
> On the 64 bit ubuntu, I cannot compile projectm with the font support.  Anyone have any ideas on that?

But currently there is a conflict between projectm and compiz.  When they run together, you'll experience flicker.  Hopefully this bug will be fixed.  However, until then you can run metacity (the fallback window manager) when you run projectm.

punkrockguy318:

With regard to the font support on 64 bit systems, I believe this is a known issue and  is documented in the projectm wiki linked in my original tutorial. Your best bet is to ask someone on the projectm irc channel.

With regards to compiz - what video card/drivers are you using. I am using a nvidia geforce go 7400 with 169.12 binary drivers and don't have any problems at all with projectm and compiz.

Sam

---

### Post by punkrockguy318 on 2008-04-15
I've tried two different computer both with ATI cards (a radeon and a 3850).  Perhaps its an ATI issue.

---

### Post by struktured on 2008-04-16
I have been trying to fix these *.pc and *.inp copy issues for a while now. I need feedback- are people still having problems with the latest svn updates?

Thanks

---

### Post by sammydee on 2008-04-16
Struktured:

If you UPDATE the svn, could the old *.pc and *.inp files be left over from the last configuration?

Wouldn't it be better to test by checking out a whole new version?

Sam

---

### Post by struktured on 2008-04-16
I have tried this (on 3 different linux machines) and it still worked- this is why I'm confused as to how users are still having problems.

---

### Post by punkrockguy318 on 2008-04-16
To users that are still having problems:

Delete your projectm folders and follow the instructions of the TC again.  There were some problems in the build code but they've since been fixed, so try just removing your projectm folders and rebuilding.

---

### Post by Saint Angeles on 2008-04-16
> **sputty01 said:**
> Thanks johnl :) worked a treat, its users like you that make using linux such an awesome experience!
awww how sweet!

i like it when people are authentically grateful for help... instead of just expecting it.

---

### Post by punkrockguy318 on 2008-04-16
> **Saint Angeles said:**
> awww how sweet!

i like it when people are authentically grateful for help... instead of just expecting it.

I'm also very grateful for your guide.  However, I am still in hopes that projectm will package their app for ubuntu so it will be easier to install.

---

### Post by sammydee on 2008-04-17
Anyone can package it for the ubuntu repositories if they know how to make debian packages.

I did have a quick look at the debian packaging guide but it doesn't look all that easy.

Sam

---

### Post by punkrockguy318 on 2008-04-17
> **sammydee said:**
> Anyone can package it for the ubuntu repositories if they know how to make debian packages.

I did have a quick look at the debian packaging guide but it doesn't look all that easy.

Sam

Yeah making debs is quite a complicated process.  I coded a compile apps and compiled them into debs, but the package creation processes was more time consuming than the coding.

---

### Post by sammydee on 2008-04-17
Both fedora and mint have these packages already, if enough people would benefit from this becoming a package (I certainly think they would) perhaps we could ask the Ubuntu packaging team?

Is there something like an official wish list for debian packages?

Sam

---

### Post by sofamensch on 2008-04-18
Same problem as earlier with 64 bit font support here as todays release.

---

### Post by struktured on 2008-04-18
What same problem?

---

### Post by sofamensch on 2008-04-18
Well i fixed this myself, but it should be interesting for any 64bit user who gets stuck at the "make" with some error..
(solution included)
[http://ubuntuforums.org/showthread.php?t=623919]("http://ubuntuforums.org/showthread.php?t=623919")

---

### Post by struktured on 2008-04-18
This is a tough one. Please post the contents of "/usr/lib/pkgconfig/*ftgl*.pc" on your system. For instance, mine (Gentoo) is  "/usr/lib/pkgconfig/ftgl.pc" and contains:

prefix=/usr
exec_prefix=${prefix}
libdir=/usr/lib64
includedir=${prefix}/include

Name: ftgl
Description: OpenGL frontend to Freetype 2
Version: 2.1.2
Requires:
Libs: -lGLU -lGL -lfreetype -lz -L${libdir} -lftgl
Cflags: -I${includedir}/FTGL  -I/usr/include/freetype2

---

### Post by punkrockguy318 on 2008-04-25
Error with current svn:

```

Linking CXX shared library libprojectM.so
[ 43%] Built target projectM
Scanning dependencies of target projectM-qt
[ 44%] Building CXX object projectM-qt/CMakeFiles/projectM-qt.dir/qprojectm_mainwindow.o
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp: In member function ‘virtual void QProjectM_MainWindow::keyReleaseEvent(QKeyEvent*)’:
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:524: error: jump to case label
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:515: error:   crosses initialization of ‘bool projectM_HadFocus’
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:536: error: jump to case label
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:515: error:   crosses initialization of ‘bool projectM_HadFocus’
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:551: error: jump to case label
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:515: error:   crosses initialization of ‘bool projectM_HadFocus’
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:561: error: jump to case label
/home/lukas/Desktop/projectm/projectM-Trunk/src/projectM-qt/qprojectm_mainwindow.cpp:515: error:   crosses initialization of ‘bool projectM_HadFocus’
make[2]: *** [projectM-qt/CMakeFiles/projectM-qt.dir/qprojectm_mainwindow.o] Error 1
make[1]: *** [projectM-qt/CMakeFiles/projectM-qt.dir/all] Error 2
make: *** [all] Error 2
lukas@lukas-desktop:~/Desktop/projectm/projectM-Trunk/src$ 


```

---

### Post by struktured on 2008-04-25
Fixed. Thanks for making me aware of this. Been coding projectM on the mac more than anywhere else lately and apple apparently has looser sensitivities to C++ syntax than linux.

---

### Post by punkrockguy318 on 2008-04-25
> **struktured said:**
> Fixed. Thanks for making me aware of this. Been coding projectM on the mac more than anywhere else lately and apple apparently has looser sensitivities to C++ syntax than linux.

Fixed.  Compiles and works fine on hardy x86.  However, an older version of ftgl is required if font support is wanted.  How much work would it be to make projectM compatible with the ftgl-dev in Ubuntu?

---

### Post by struktured on 2008-04-25
Well I have been slowly getting the ambition to install hardy on something for a variety of reasons, but before then it's not that easy to verify the FTGL problem until I get more feedback from users or I finally get access to an ubuntu machine.

- Carmelo

---

### Post by El Lance-O on 2008-04-26
I compiled this on Hardy just fine on one computer, but it segfaulted on another when I tried to run projectM from a terminal.

Unfortunately it doesn't want to work after the first try like it did for the writer of this tutorial.

Any suggestions? I don't get anything other than 'Segmentation fault', so I don't know what to do here.

---

### Post by digbybare on 2008-04-26
I tried following this guide, but at the ccmake step it tells me that there's no CMakeList.txt

Any ideas?

---

### Post by Penguin Power on 2008-04-26
Great howto, I have it all running perfectly at 1920x1200 now :)

Next step, network visualisations :popcorn:

---

### Post by digbybare on 2008-04-26
Okay, I got redownloaded the source, and it compiled.

However, I keep getting segmentation faults when I run projectM-test.

---

### Post by mocha on 2008-04-27
> **digbybare said:**
> Okay, I got redownloaded the source, and it compiled.

However, I keep getting segmentation faults when I run projectM-test.

Same here.  Running an nvidia card.

---

### Post by Xzavier on 2008-04-28
> **mocha said:**
> Same here.  Running an nvidia card.

ditto
xzavier@Dragon:~/projectm/projectM-Trunk/src$ projectM-test
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1680 x 1050
MAX SAMPLES:2048
Segmentation fault

Apr 28 22:04:45 Dragon kernel: [  251.296999] projectM-pulsea[5858]: segfault at 00000000 eip 00000000 esp bfec05dc error 4
 i'm ](*,)

---

### Post by sammydee on 2008-04-29
Have the people running projectm-test actually tried just running projectm-pulseaudio?

The test if probably only useful for developers and debugging anyway, I might remove it from the tutorial.

Sam

EDIT: Has been removed from the tutorial, it was a useless additonal step anyway. Why care if the test fails as long as the actual program works?

---

### Post by sammydee on 2008-04-29
> I tried following this guide, but at the ccmake step it tells me that there's no CMakeList.txt

Any ideas?

Have you tried removing the Cmake cache as detailed in the tutorial? Please post the exact command output you get with this error.

Sam

---

### Post by digbybare on 2008-04-29
> **sammydee said:**
> Have the people running projectm-test actually tried just running projectm-pulseaudio?

The test if probably only useful for developers and debugging anyway, I might remove it from the tutorial.

Sam

EDIT: Has been removed from the tutorial, it was a useless additonal step anyway. Why care if the test fails as long as the actual program works?

I tried projectM-pulseaudio right after I tried projectM-test a few times. It segfaults as well.

digby@velvet:~$ projectM-test
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1680 x 1050
MAX SAMPLES:2048
Segmentation fault
digby@velvet:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
MAX SAMPLES:2048
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_24c5_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault

I'm using an ATI Radeon Mobility 9000.

---

### Post by sammydee on 2008-04-29
I don't think I can help. Have you tried the IRC channel?

Sam

---

### Post by struktured on 2008-04-29
I can't really trace your problem without seeing it in gdb. Please change the CMAKE_BUILD_TYPE to "Debug", rebuild / install the project again, and run projectM-test via "gdb projectM-test". Then post the gdb's stack trace to the forum.

---

### Post by castles on 2008-04-30
projectM-test works fine for me after compiling, projectM does nothing in terminal (bash: projectM: command not found). 

I can select ProjectM in Mythtv settings.. but when I try and playback music the visualizations is just a white page. If I maximize the visualization i get a segmentation fault.

I have a Nvidia 6800GT

Edit.. I should say I'm using mythbuntu with xfce window manager

---

### Post by peddy on 2008-04-30
> **punkrockguy318 said:**
> I can compile okay when I turn FTGL support off, but when I try to copmile with FTGL I get this error:
```

[ 43%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TimeKeeper.o
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [projectM-engine/libprojectM.so.2.00] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
lukas@lukas-desktop:~/Desktop/projectm/projectM-Trunk/src$ 

```



can anyone please tell me how to recompile it correctly (perhaps with different flags)?

I get this error when Making: 

```
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [projectM-engine/libprojectM.so.2.00] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

Thanks

---

### Post by castles on 2008-04-30
Have you tried "-DCMAKE_BUILD_TYPE=RELEASE" mentioned  [here]("http://www.mythtv.org/wiki/index.php/ProjectM")?

---

### Post by sammydee on 2008-04-30
> **castles said:**
> projectM-test works fine for me after compiling, projectM does nothing in terminal (bash: projectM: command not found). 

I can select ProjectM in Mythtv settings.. but when I try and playback music the visualizations is just a white page. If I maximize the visualization i get a segmentation fault.

I have a Nvidia 6800GT

Edit.. I should say I'm using mythbuntu with xfce window manager

castles: The command is:

```
projectM-pulseaudio
```

Use tab autocompletion, it's much easier :-)

---

### Post by castles on 2008-04-30
> **sammydee said:**
> castles: The command is:

```
projectM-pulseaudio
```

Use tab autocompletion, it's much easier :-)

Thanks Sammy,

I was trying it with a lowercase "M" (might be worth updating the tutorial).

I get the following error now: 
```
Connection failure: Connection refused
ASSERT failure in QCoreApplication::sendEvent: "Cannot send events to objects owned by a different thread. Current thread 808ea78. Receiver 'QProjectM_MainWindow' (of type 'QWidget') was created in thread 8064118", file kernel/qcoreapplication.cpp, line 274
Aborted
```

---

### Post by sammydee on 2008-04-30
Hi castles.

Tutorial updated, the other segfault you get is way beyond my abilities to decipher so we'd better wait for Struktured to comment.

Sam

---

### Post by TehDooMCat on 2008-04-30
Hey, is there a way to compile it to -not- use PulseAudio?

I'm using OSS4, and while PulseAudio would be useful over it I can't even use PA with it because it only supports OSS3.

The test app looks very slick on my comp though, even with all my Compiz settings ramped right up and the texture size on projectM doubled :D

---

### Post by struktured on 2008-04-30
castles,

The "Connection failure: connection refused" line probably implies that your pulse audio setup is not working correctly. When projectM-pulseaudio can't open a legitimate pulse audio connection to the server, it doesn't always handle shut down very gracefully (a known bug I let pass for the 1.1 release). 

However, the ASSERT failure makes me nervous- I hope that's not a separate issue. Either way, make sure your pulse daemon is running properly, and I'll someday get around to fixing some of the shutdown bugs and report a nice pretty error in a qt dialog window...

---

### Post by struktured on 2008-04-30
TehDoomCat,

Run "ccmake ." in projectM-Trunk/src

After pressing 'c' and maybe 'g' you should see options like INCLUDE-PROJECTM-PULSEAUDIO. Turn that one off. Turn on/off anything else you care about. For instance, if you don't want jack or pulse audio turn off projectM-qt as well. There is no projectM-test with the qt back end yet.

---

### Post by castles on 2008-05-01
> **struktured said:**
> castles,

The "Connection failure: connection refused" line probably implies that your pulse audio setup is not working correctly. When projectM-pulseaudio can't open a legitimate pulse audio connection to the server, it doesn't always handle shut down very gracefully (a known bug I let pass for the 1.1 release). 

However, the ASSERT failure makes me nervous- I hope that's not a separate issue. Either way, make sure your pulse daemon is running properly, and I'll someday get around to fixing some of the shutdown bugs and report a nice pretty error in a qt dialog window...

Thanks struktured, maybe its got something to do with the fact that I've been trying to run projectM in xfce. I managed to get it working fine on my other computer running a default Hardy install. So I'm following the steps fine.

I haven't had much of a chance but I will see if pulse audio is working. Does anyone know if mythbuntu comes with pulse by default?

---

### Post by TehDooMCat on 2008-05-04
> **struktured said:**
> TehDoomCat,

Run "ccmake ." in projectM-Trunk/src

After pressing 'c' and maybe 'g' you should see options like INCLUDE-PROJECTM-PULSEAUDIO. Turn that one off. Turn on/off anything else you care about. For instance, if you don't want jack or pulse audio turn off projectM-qt as well. There is no projectM-test with the qt back end yet.

I tried compiling projectM without PA/Jack/ALSA etc., no dice - is the only projectM standalone app projectM-pulseaudio? How can I set it up/run it through gst-visualize-0.10? It can't see it on any media players that use libvisual.

---

### Post by struktured on 2008-05-05
First of all, make sure "INCLUDE-PROJECTM-LIBVISUAL" is turned on. Change your CMAKE_INSTALL_PREFIX (I believe) to = "/usr" as the tutorial suggests. Then press 'g' and do a make install. If it installed ok, find the directory that contains your libvisual plugins. Something like...

```

ls /usr/lib/libvisual-0.4/actor/*.so

/usr/lib/libvisual-0.4/actor/actor_bumpscope.so  /usr/lib/libvisual-0.4/actor/actor_lv_analyzer.so
/usr/lib/libvisual-0.4/actor/actor_corona.so     /usr/lib/libvisual-0.4/actor/actor_lv_gltest.so
/usr/lib/libvisual-0.4/actor/actor_flower.so     /usr/lib/libvisual-0.4/actor/actor_lv_scope.so
/usr/lib/libvisual-0.4/actor/actor_gdkpixbuf.so  /usr/lib/libvisual-0.4/actor/actor_madspin.so
/usr/lib/libvisual-0.4/actor/actor_gforce.so     /usr/lib/libvisual-0.4/actor/actor_nastyfft.so
/usr/lib/libvisual-0.4/actor/actor_infinite.so   /usr/lib/libvisual-0.4/actor/actor_oinksie.so
/usr/lib/libvisual-0.4/actor/actor_jakdaw.so     /usr/lib/libvisual-0.4/actor/libprojectM_libvisual.so
/usr/lib/libvisual-0.4/actor/actor_JESS.so


```

Does it appear there like mine does? Another good test is to run "amarok_libvisual" with no arguments:

```

amarok_libvisual

jess
bumpscope
corona
lv_flower
gdkpixbuf
gforce
infinite
jakdaw
lv_analyzer
lv_gltest
lv_scope
madspin
nastyfft
oinksie
projectM

```

Tell me what happens from these two tests

- struktured

---

### Post by mocha on 2008-05-10
For those of us with the seg faults, when you're in the cmake just turn "off" USE_FBO.  Works like a charm now!

---

### Post by punkrockguy318 on 2008-05-11
It seems like there is some developer activity in this thread; I have a question: where is a good place for feature requests?

It would be really nice for double clicking on a projctm instance to toggle between fullscreen and windowed mode.  Perhaps right click could be next preset.

---

### Post by bejurne on 2008-05-12
Thanks for this extensive howto. 

I get this error when I try to configure with ccmake:
```

 CMake Error: This project requires some variables to be set,
 and cmake can not find them.
 Please set the following variables:
 QT_FONTCONFIG_LIBRARY (ADVANCED)
 QT_XI_LIBRARY (ADVANCED)
 QT_XRANDR_LIBRARY (ADVANCED)
 QT_XRENDER_LIBRARY (ADVANCED)

```

I did install the dependencies you listed in the beginning of the howto.
I wouldn't mind setting these values manually, if I knew what values to set these variables to...
Some pointers would be appreciated.

_BTW_: I had to force the install of libqt4-opengl-dev to work around _[this]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148")_ bug (#228148 ). Before I worked around this bug with dpkg --force-overwrite, ccmake wanted to know the value of "QT_QTOPENGL_INCLUDE_DIR"

UPDATE: I figured out how to fix this myself with some synaptic search. The following additional packages need to be installed to make this work
```

libfonconfig1-dev
libxi-dev
libxrandr-dev
libxrender-dev

```
Would be cool, if you added this to your howto to spare others the trouble.

---

### Post by sammydee on 2008-05-13
> **punkrockguy318 said:**
> It seems like there is some developer activity in this thread; I have a question: where is a good place for feature requests?

It would be really nice for double clicking on a projctm instance to toggle between fullscreen and windowed mode.  Perhaps right click could be next preset.

Another nice feature would be cursor hiding in full screen mode after maybe five seconds, just like when watching a video.

Sam

---

### Post by struktured on 2008-05-14
Both very doable in the Qt4 framework (or any gui of course). I will consider these simple mods and possibly implement them when my work dies down.

Please post your feature requests on our sourceforge tracker accessible via 

[http://projectm.sf.net](http://projectm.sf.net)


-struk

---

### Post by struktured on 2008-05-14
mouse hiding is implemented on trunk r1016. Let me know if its the desired behavior.

---

### Post by El Lance-O on 2008-05-14
I used this guide to compile ProjectM on gutsy, and it worked wonders, no problems at all.

But now...

When I run projectM-test, nothing happens. At all.

When I run projectM-pulseaudio, the qt menu comes up, but if I try switching to another visual, or wait for it to switch by itself, I get

```
ellanceo@TheThinGreyBox:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/ellanceo/.projectM/config.inp
MAX SAMPLES:2048
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor" 
terminate called after throwing an instance of 'int'
Aborted
```

Help?

Please?

I really really REALLY love ProjectM, and it is definitely one of the highlights of my lappytop.

---

### Post by punkrockguy318 on 2008-05-14
> **struktured said:**
> Both very doable in the Qt4 framework (or any gui of course). I will consider these simple mods and possibly implement them when my work dies down.

Please post your feature requests on our sourceforge tracker accessible via 

[http://projectm.sf.net](http://projectm.sf.net)


-struk

Mouse hiding works like a charm :)

---

### Post by struktured on 2008-05-14
El-Lance-O - not easy to trace that. Try giving me a stack trace of it, maybe that will reveal something? That is, build in debug mode, then run it in gdb.

---

### Post by El Lance-O on 2008-05-14
How would I go about doing that?

I am quite new to compiling things, and I couldn't find a list of arguments for projectM to run it in say verbose mode or anything of the sort so that I might get more feedback.

---

### Post by struktured on 2008-05-15
Do same steps as shown in tutorial, but change CMAKE_BUILD_TYPE to Debug rather than Release. Then type "gdb /usr/bin/projectM-pulseaudio" . Then type the command "r" inside of gdb to run it. If it crashes then type "bt" for a backtrace and post the results.

---

### Post by DarrenCT on 2008-05-16
I'm new to this ProjectM thing, but am a big fan of the milkdrop visualizations.  I have installed "libprojectm1 & libprojectm1-data & libprojectm-dev" from the Hardy repos, and I try to run the command "projectM-pulsaudio" and nothing happens, just "command not found".  the one from the repos seems to be version 1.01-5.  There doesn't seem to be a binary listed under the properties for libprojectm1 ... just libraries, and docs.  I'm sure pulseaudio is working, as I have tested it through the sound option.  Please let me know how I can make this work.  

Thanks

---

### Post by punkrockguy318 on 2008-05-16
> **DarrenCT said:**
> I'm new to this ProjectM thing, but am a big fan of the milkdrop visualizations.  I have installed "libprojectm1 & libprojectm1-data & libprojectm-dev" from the Hardy repos, and I try to run the command "projectM-pulsaudio" and nothing happens, just "command not found".  the one from the repos seems to be version 1.01-5.  There doesn't seem to be a binary listed under the properties for libprojectm1 ... just libraries, and docs.  I'm sure pulseaudio is working, as I have tested it through the sound option.  Please let me know how I can make this work.  

Thanks

the projectm from the hardy repos do not include the projectM-pulseaudio program.  it's recommended that you either follow the instructions on the first page to build projectM from the latest source, or wait for projectM to release 1.2

---

### Post by Steve Fisher on 2008-05-16
How to uninstall projectM?

---

### Post by struktured on 2008-05-16
Can't do it easily unfortunately (cmake doesn't support make uninstall out of the box). The only way if its installed by source is to manually delete everything.

---

### Post by Steve Fisher on 2008-05-16
Riiiiight 

So everything in my ~/projectm directory, and everything in /usr/share/projectM

Anywhere else I should look?

Edit: Nevermind. I did
```
gksudo gnome-search-tool
```
and searched for projectM, modified less than 1 day ago, and deleted everything that came up.

---

### Post by WildeBeest on 2008-05-16
I get the following errors.

I'm using Hardy 64 bit.

Scanning dependencies of target projectM
[  1%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/projectM.o
[  2%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/FBO.o
[  3%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/InitCond.o
[  4%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Expr.o
[  5%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PCM.o
[  6%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Parser.o
[  7%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Preset.o
[  8%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BeatDetect.o
[  9%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerPixelEqn.o
[ 10%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Param.o
[ 12%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/CustomWave.o
[ 13%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/CustomShape.o
[ 14%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Func.o
[ 15%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Eval.o
[ 16%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerFrameEqn.o
[ 17%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerPointEqn.o
[ 18%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/fftsg.o
[ 19%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/KeyHandler.o
[ 20%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/timer.o
[ 21%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/wipemalloc.o
[ 23%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BuiltinFuncs.o
[ 24%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BuiltinParams.o
[ 25%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Renderer.o
[ 26%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetLoader.o
[ 27%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetChooser.o
[ 28%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetFrameIO.o
[ 29%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetMerge.o
[ 30%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/ConfigFile.o
[ 31%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/IdlePreset.o
[ 32%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TextureManager.o
[ 34%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TimeKeeper.o
[ 35%] Building C object projectM-engine/CMakeFiles/projectM.dir/image_DXT.o
[ 36%] Building C object projectM-engine/CMakeFiles/projectM.dir/image_helper.o
[ 37%] Building C object projectM-engine/CMakeFiles/projectM.dir/SOIL.o
[ 38%] Building C object projectM-engine/CMakeFiles/projectM.dir/stb_image_aug.o
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [projectM-engine/libprojectM.so.2.00] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

---

### Post by punkrockguy318 on 2008-05-16
> **WildeBeest said:**
> I get the following errors.

I'm using Hardy 64 bit.

Scanning dependencies of target projectM
[  1%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/projectM.o
[  2%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/FBO.o
[  3%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/InitCond.o
[  4%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Expr.o
[  5%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PCM.o
[  6%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Parser.o
[  7%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Preset.o
[  8%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BeatDetect.o
[  9%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerPixelEqn.o
[ 10%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Param.o
[ 12%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/CustomWave.o
[ 13%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/CustomShape.o
[ 14%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Func.o
[ 15%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Eval.o
[ 16%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerFrameEqn.o
[ 17%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PerPointEqn.o
[ 18%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/fftsg.o
[ 19%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/KeyHandler.o
[ 20%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/timer.o
[ 21%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/wipemalloc.o
[ 23%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BuiltinFuncs.o
[ 24%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/BuiltinParams.o
[ 25%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Renderer.o
[ 26%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetLoader.o
[ 27%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetChooser.o
[ 28%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetFrameIO.o
[ 29%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/PresetMerge.o
[ 30%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/ConfigFile.o
[ 31%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/IdlePreset.o
[ 32%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TextureManager.o
[ 34%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/TimeKeeper.o
[ 35%] Building C object projectM-engine/CMakeFiles/projectM.dir/image_DXT.o
[ 36%] Building C object projectM-engine/CMakeFiles/projectM.dir/image_helper.o
[ 37%] Building C object projectM-engine/CMakeFiles/projectM.dir/SOIL.o
[ 38%] Building C object projectM-engine/CMakeFiles/projectM.dir/stb_image_aug.o
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [projectM-engine/libprojectM.so.2.00] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

You need to downgrade your libftgl-dev package.  I've attached the libftgl-dev package that you need.  I grabbed it from this forum, somewhere...

---

### Post by WildeBeest on 2008-05-16
Thanks for the info.

Now how do I down grade?

---

### Post by punkrockguy318 on 2008-05-16
> **WildeBeest said:**
> Thanks for the info.

Now how do I down grade?

just download the deb file i've attached in my previous post an open it with the gdebi package installer.

---

### Post by El Lance-O on 2008-05-17
> **struktured said:**
> Do same steps as shown in tutorial, but change CMAKE_BUILD_TYPE to Debug rather than Release. Then type "gdb /usr/bin/projectM-pulseaudio" . Then type the command "r" inside of gdb to run it. If it crashes then type "bt" for a backtrace and post the results.

Alright, here is the backtrace:

```
#0  0xb7fc5410 in __kernel_vsyscall ()
#1  0xb6f16085 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6f17a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7ecaaeb in BuiltinFuncs::insert_func (func=0x80fa608)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/BuiltinFuncs.cpp:152
#4  0xb7ecabb5 in BuiltinFuncs::load_builtin_func (name=@0xbffbec0c, 
    func_ptr=0xb7ecda48 <FuncWrappers::int_wrapper(float*)>, num_args=1)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/BuiltinFuncs.cpp:37
#5  0xb7ecac22 in BuiltinFuncs::load_all_builtin_func ()
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/BuiltinFuncs.cpp:58
#6  0xb7ecc325 in BuiltinFuncs::init_builtin_func_db ()
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/BuiltinFuncs.cpp:126
#7  0xb7e9b556 in projectM::initPresetTools (this=0x826ebb0)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/projectM.cpp:741
#8  0xb7e9ba86 in projectM::projectM_init (this=0x826ebb0, gx=32, gy=24, 
    fps=35, texsize=1024, width=512, height=512)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/projectM.cpp:454
---Type <return> to continue, or q <return> to quit---
#9  0xb7e9d648 in projectM::readConfig (this=0x826ebb0, configFile=@0xbffbee9c)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/projectM.cpp:218
#10 0xb7e9ea7c in projectM (this=0x826ebb0, config_file=@0xbffbee9c, flags=1)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-engine/projectM.cpp:126
#11 0xb7f9b55d in QProjectM (this=0x826eba8, config_file=@0x81404ec)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-qt/qprojectm.hpp:23
#12 0xb7f9b9dd in QProjectMWidget::initializeGL (this=0x81404d8)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-qt/qprojectmwidget.hpp:192
#13 0xb76c115f in QGLWidget::glInit () from /usr/lib/libQtOpenGL.so.4
#14 0xb76c1332 in QGLWidget::glDraw () from /usr/lib/libQtOpenGL.so.4
#15 0xb76c081f in QGLWidget::updateGL () from /usr/lib/libQtOpenGL.so.4
#16 0xb76efdb6 in QGLWidget::qt_metacall () from /usr/lib/libQtOpenGL.so.4
#17 0xb7f9b12e in QProjectMWidget::qt_metacall (this=0x81404d8, 
    _c=QMetaObject::InvokeMetaMethod, _id=27, _a=0xbffbf000)
    at /home/ellanceo/projectm/projectM-Trunk/src/projectM-qt/moc_qprojectmwidget.cxx:79
#18 0xb7645cf4 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#19 0xb76468c2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#20 0xb7664167 in QTimer::timeout () from /usr/lib/libQtCore.so.4
#21 0xb764c88e in QTimer::timerEvent () from /usr/lib/libQtCore.so.4
---Type <return> to continue, or q <return> to quit---
#22 0xb76448b4 in QObject::event () from /usr/lib/libQtCore.so.4
#23 0xb783c28d in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#24 0xb783fce7 in QApplication::notify () from /usr/lib/libQtGui.so.4
#25 0xb7632c1b in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#26 0xb7659e89 in ?? () from /usr/lib/libQtCore.so.4
#27 0xbffc08d0 in ?? ()
#28 0x08173268 in ?? ()
#29 0xbffbf878 in ?? ()
#30 0x08091f30 in ?? ()
#31 0xbffbf890 in ?? ()
#32 0x08173268 in ?? ()
#33 0x00000000 in ?? ()
```

Also when I ran it in gdb with "r" that gave me an error in a gui window:
```

There was a problem trying to open the playlist
"/usr/share/projectM/ProjectMPlaylist.ppl"/ The file may no longer exist or you may not have permission to read the file
```

This refers to the playlist file that I backed up so that I didn't have to rate everything over again (I recently did a fresh install because Hardy was dying on me).

ProjectM worked fine before, even with Hardy obviously failing after an unsuccessful update.

Annndd..I just realized I deleted that playlist file. Awesome.

---

### Post by denham2010 on 2008-05-17
Hi, hoping someone can help here. 
 
Last night I installed ProjectM from SVN, following the guide at the start of this post. 
 
All worked perfectly and I had a fully functioning ProjectM. 
 
 
This morning, there were some updates for my system (running Xubuntu 8.04). The following files were updated: 
 
```
Commit Log for Sun May 18 08:43:28 2008 
 
Upgraded the following packages: 
gdm (2.20.5-0ubuntu3) to 2.20.6-0ubuntu1 
libglib2.0-0 (2.16.3-1) to 2.16.3-1ubuntu1 
libglib2.0-data (2.16.3-1) to 2.16.3-1ubuntu1 
libglib2.0-dev (2.16.3-1) to 2.16.3-1ubuntu1 
libgphoto2-2 (2.4.0-8ubuntu6) to 2.4.0-8ubuntu7 
libgphoto2-port0 (2.4.0-8ubuntu6) to 2.4.0-8ubuntu7 
libnautilus-extension1 (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6 
libtotem-plparser10 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2 
nautilus (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6 
nautilus-data (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6
```
 
Since the updates, I am getting the following problem whenever I try to launch projectM-pulseaudio: 
 
```
:~$ projectM-pulseaudio  
dir:/usr/share/projectM/config.inp  
reading ~/.projectM/config.inp  
configFile: ~/.projectM/config.inp 
MAX SAMPLES:2048 
configFile: ~/.projectM/config.inp 
MAX SAMPLES:2048 
Failed to insert builtin function "int" into collection! Bailing... 
Aborted
```
 
Thinking something had just been broken between the original configuring and installing of ProjectM and the updates, I fully removed ProjectM and re-installed from SVN this morning (zero errors during ccmake, make and make install). 
 
Unfortunately, I am still getting the same error. 
 
All help is greatly appreciated, I have been looking for a visualiser for quite some time that doesn't slow my system to a crawl, and after using ProjectM last night, it fit's the bill perfectly!

(I have also posted this on the ProjectM sourceforge forum to try and cover both bases!)
 
Thanks.

*** UPDATE ***

Ok, I tried fully removing ProjectM, and then downgrading the packages that were previously updated, as these were the only changes that occurred between ProjectM working and failing.

I then re-installed ProjectM, and I'm still getting the same error.....it's rather frustrating as it was working perfectly until these updates, and now it just refuses to work.

Any ideas? I would really like to get this one solved!

Thanks.

*** SOLVED ***

After figuring out how to debug from reading other posts, I found ProjectM was looking for a saved playlist, which no longer existed.

From this, I eventually found that not only does ProjectM create a ~/.projectM folder for your settings, it also creates a ~/.config/ProjectM folder, which happens to store the deafult playlist to look for upon opening.

Since the playlist no longer existed, ProjectM would no longer start.

Deleting my ~/.projectM and ~/.config/ProjectM folders and then restarting solved the issue.

---

### Post by El Lance-O on 2008-05-18
Awesome!

That totally just solved my problem! Thanks for doing all the hard work I didn't know how to do.

It's nice having projectM back. And kudos on getting the mouse to disappear with the new release.

Very awesome. :)

---

### Post by WildeBeest on 2008-05-18
> **punkrockguy318 said:**
> just download the deb file i've attached in my previous post an open it with the gdebi package installer.

The package installer won't allow me to install it.

It gives me the following message and the install button is disabled.

[COLOR="Red"]Error: A later version is already installed[/COLOR]

---

### Post by punkrockguy318 on 2008-05-18
> **WildeBeest said:**
> The package installer won't allow me to install it.

It gives me the following message and the install button is disabled.

[COLOR="Red"]Error: A later version is already installed[/COLOR]

You're probably running an older version of Ubuntu, aren't you?

---

### Post by Xzavier on 2008-05-18
Following errors during ccmake .
```
CMake Error: This project requires some variables to be set,
 and cmake can not find them.
 Please set the following variables:
 QT_QTOPENGL_INCLUDE_DIR (ADVANCED)
```

found the issue is with  libqt4-opengl tried removing/installing   libqt4-opengl-dev 
```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ sudo apt-get install libqt4-opengl-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libqt4-opengl-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/39.1kB of archives.
After this operation, 233kB of additional disk space will be used.
(Reading database ... 144249 files and directories currently installed.)
Unpacking libqt4-opengl-dev (from .../libqt4-opengl-dev_4.4.0-1ubuntu4~hardy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu4~hardy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/pkgconfig/QtOpenGL.pc', which is also in package libqt4-dev
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu4~hardy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xzavier@Dragon:~/projectm/projectM-Trunk/src$ 
```

i

would love some help..

get:
[code]

---

### Post by bejurne on 2008-05-18
@Xzavier:
as I posted earlier, this is a known [_bug_]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148"). You can work around it by using "dpkg -i --force-overwrite package-name" to install the package. It will work then.
You can find the package in "/var/cache/apt/archives/" if apt-get/synaptic already downloaded it.

---

### Post by Xzavier on 2008-05-18
> **bejurne said:**
> @Xzavier:
as I posted earlier, this is a known [_bug_]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148"). You can work around it by using "dpkg --force-overwrite package-name" to install the package. It will work then.
You can find the package in "/var/cache/apt/archives/" if apt-get/synaptic already downloaded it.

my apologizes i must have over looked.. i did dig all the entries looking for a same situation.. i will attempt.. thank you

=-=

it appears my syntax is incorrect..
```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ sudo dpkg --force-overwrite /var/cache/apt/archives/libqt4-opengl_4.4.0-1ubuntu4~hardy1_i386.deb
dpkg: need an action option
```
reading the man pages. i didnt find them very helpful on this issue..

---

### Post by pallavis11 on 2008-05-19
See the info below:

[http://a2zhowto](http://a2zhowto) .blogspot.com/

[http://learnphpwithme](http://learnphpwithme) .blogspot.com/

---

### Post by WildeBeest on 2008-05-19
> **punkrockguy318 said:**
> You're probably running an older version of Ubuntu, aren't you?

Nope, Hardy 64 bit.

---

### Post by bejurne on 2008-05-19
> **Xzavier said:**
> 
it appears my syntax is incorrect..
```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ sudo dpkg --force-overwrite /var/cache/apt/archives/libqt4-opengl_4.4.0-1ubuntu4~hardy1_i386.deb
dpkg: need an action option
```
reading the man pages. i didnt find them very helpful on this issue..
my bad
just add the -i option, so dpkg knows you want to install ;) 
so you get:

```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libqt4-opengl_4.4.0-1ubuntu4~hardy1_i386.deb

```

This should be added to the howto, there will be more people with this problem...

---

### Post by Zularan on 2008-05-19
Having the same issue when running 'ccmake .'

```
 CMake Error: This project requires some variables to be set,
 and cmake can not find them.
 Please set the following variables:
 QT_QTOPENGL_INCLUDE_DIR (ADVANCED)
```

Tried ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libqt4-opengl_4.4.0-1ubuntu4~hardy1_i386.deb

```
which turns up no errors.  Synaptic says the libqt4-opengl is installed, however I get the following error when trying to install the -dev.
```
E: /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu4~hardy1_i386.deb: trying to overwrite `/usr/lib/pkgconfig/QtOpenGL.pc', which is also in package libqt4-dev
```
Have I missed something or is this not do-able till the bugs fixed?

---

### Post by Zularan on 2008-05-21
Not sure where I mucked up earlier but managed to get libqt4-opengl-dev installed with ```
sudo dpkg --force-all -i /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu4~hardy1_i386.deb
```
(--force-overwrite didn't work for me)

I redownloaded the projectM svn and ran 'cmake .' which didn't give me the blue interface while compiling like the first time which seemed odd but seemed to complete and make/install anyway. When invoking projectM-pulseaudio I get ```
/usr/local/bin/projectM-pulseaudio: error while loading shared libraries: libprojectM-qt.so.1: cannot open shared object file: No such file or directory
```
I realised I used 'cmake .' instead of 'ccmake .' oops... It installed into /usr/local instead.. Realised that when I was about to edit the makefile luckily... So compiled again with 'ccmake .' and all went well and is working great!

Is there a way to 'uninstall' from the cmake since it installed into /usr/local the first time (instead of /usr like the guide says)?

Fantastic guide thanks for taking the time and sharing.

---

### Post by sammydee on 2008-05-24
Hi Zularan:

I don't believe ccmake support uninstalls yet, so you'll have to go into /usr/local and manually remove the files if it bothers you I'm afraid.

Sam

---

### Post by sensimilla on 2008-05-26
Many thanks for the tutorial :KS

Got it working great here on 64-bit Hardy with an 8800gt and it looks absolutely superb. I Just had to downgrade the ftl-dev package, I did this by uninstalling the original version via synaptic and then double clicking and installing the .deb file linked to in this thread. No command line required ;-)

ProjectM has really improved from the last time I tried it, maybe 9 months ago. I could'nt get the standalone version to compile then, so it only worked in Amarok and I couldn't get it to start on my TV, also a lot of the presets didn't work well and were very glitchy and full of artifacts. I guess that switching from an ATI to an Nvidia card might of helped some. So massive props out to the developers :guitar:

If people want to uninstall projectM then you should install it using checkinstall this is a bit of software that builds packages from make files.

```
sudo apt-get install checkinstall
```
Then instead of using
```
make && sudo make install
```
just do
```
make
```
then if that completes 
```
sudo checkinstall
```

checkinstall will start and you can type in a description, follow the directions, you also might need to change the name to projectm. Checkinstall should then build a .deb package and install it for you. This can then be uninstalled in the usual way via apt-get or synaptic.

I hope this is clear enough. There is a lot more info on checkinstall in these forums so do a search if you need more guidance or ask here

---

### Post by sammydee on 2008-05-26
sensimilla: I almost suggested using checkinstall in the howto, but when I actually tried to install projectM with checkinstall, it didn't install properly, so I didn't include it in the end.

Did it work properly for you?

sam

---

### Post by sensimilla on 2008-05-28
Yep, checkinstall is working for me using build 1024.

I have only 4 presets installed by default, now I seem to remember there were more when I did a make install but I updated from cvs before that so I'm not really sure what has caused this or if that is just normal. The torrent pack has fixed that anyhow :)

---

### Post by Xzavier on 2008-05-31
Alright I've resolved my issues with ccmake and qt not playing together nicely. all is compiled, and with running the app Segmentation fault..

```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
trying to create ~/.projectM/config.inp 
created ~/.projectM/config.inp successfully
configFile: /home/xzavier/.projectM/config.inp
MAX SAMPLES:2048
load config END 
Segmentation fault
```

---

### Post by diegomedaglia on 2008-05-31
> **mocha said:**
> For those of us with the seg faults, when you're in the cmake just turn "off" USE_FBO.  Works like a charm now!

Worked for me too! Thanks!

---

### Post by Xzavier on 2008-05-31
Well i made some progress.. but apparently hit another large wall.. I really do appreciate all the help thats been provided.

```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ projectM-pulseaudio 
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/xzavier/.projectM/config.inp
MAX SAMPLES:2048
load config END 
Connection failure: Connection refused
QGLContext::makeCurrent(): Failed.
*** glibc detected *** projectM-pulseaudio: double free or corruption (out): 0xbfbebc70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c6fa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6c734f0]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb6e15b11]
/usr/lib/libQtGui.so.4(_ZN7QActionD0Ev+0x184)[0xb7607894]
/usr/lib/libQtCore.so.4(_ZN14QObjectPrivate14deleteChildrenEv+0x4c)[0xb7372e3c]
/usr/lib/libQtGui.so.4(_ZN7QWidgetD2Ev+0x15e)[0xb7659d1e]
/usr/lib/libQtGui.so.4(_ZN11QMainWindowD2Ev+0x31)[0xb79b4a21]
/usr/lib/libprojectM-qt.so.1(_ZN20QProjectM_MainWindowD0Ev+0x36a)[0xb7f2545a]
projectM-pulseaudio(_ZN17QPulseAudioThread22context_state_callbackEP10pa_contextPv+0x7c)[0x8055bac]
/usr/lib/libpulse.so.0[0xb7e03f62]
/usr/lib/libpulse.so.0[0xb7e04567]
/usr/lib/libpulse.so.0[0xb7e04aba]
/usr/lib/libpulse.so.0[0xb7e050fe]
/usr/lib/libpulse.so.0[0xb7e344f5]
/usr/lib/libpulse.so.0(pa_mainloop_dispatch+0x291)[0xb7e0e6e1]
/usr/lib/libpulse.so.0(pa_mainloop_iterate+0x51)[0xb7e0e9a1]
/usr/lib/libpulse.so.0(pa_mainloop_run+0x34)[0xb7e0ea64]
/usr/lib/libpulse.so.0[0xb7e1a753]
/usr/lib/libpulse.so.0[0xb7e3bac9]
/lib/tls/i686/cmov/libpthread.so.0[0xb70bd4fb]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb6cdae5e]
======= Memory map: ========
08048000-0805e000 r-xp 00000000 08:01 705604     /usr/bin/projectM-pulseaudio
0805e000-0805f000 rw-p 00016000 08:01 705604     /usr/bin/projectM-pulseaudio
0805f000-0869d000 rw-p 0805f000 00:00 0          [heap]
b0eb7000-b0eb9000 r-xp 00000000 08:01 3620958    /lib/libnss_mdns4.so.2
b0eb9000-b0eba000 rw-p 00001000 08:01 3620958    /lib/libnss_mdns4.so.2
b0ece000-b0f4e000 rw-s 2a448000 00:0e 13174      /dev/nvidia0
b0f4e000-b104f000 rw-p b0f4e000 00:00 0 
b104f000-b11a3000 rw-s e5ef4000 00:0e 13174      /dev/nvidia0
b11a3000-b12f7000 rw-s e5ef4000 00:0e 13174      /dev/nvidia0
b12f7000-b144b000 rw-s e2304000 00:0e 13174      /dev/nvidia0
b144b000-b144c000 ---p b144b000 00:00 0 
b144c000-b1c4c000 rwxp b144c000 00:00 0 
b1c4c000-b1e4d000 rw-s 00000000 00:14 53566      /dev/shm/pulse-shm-4038625804
b264e000-b264f000 ---p b264e000 00:00 0 
b264f000-b2e4f000 rwxp b264f000 00:00 0 
b2e4f000-b2e50000 rw-s 00000000 00:09 524301     /SYSV00000000 (deleted)
b2e50000-b2e51000 rw-s 00000000 00:09 884760     /SYSV00000000 (deleted)
b2fd0000-b2fd1000 rw-s 00000000 00:09 3342388    /SYSV00000000 (deleted)
b2fd1000-b2fd2000 rw-s 00000000 00:09 2326576    /SYSV00000000 (deleted)
b3085000-b3094000 r-xp 00000000 08:01 3638654    /lib/tls/i686/cmov/libresolv-2.7.so
b3094000-b3096000 rw-p 0000f000 08:01 3638654    /lib/tls/i686/cmov/libresolv-2.7.so
b3096000-b3098000 rw-p b3096000 00:00 0 
b3098000-b309c000 r-xp 00000000 08:01 3638641    /lib/tls/i686/cmov/libnss_dns-2.7.so
b309c000-b309e000 rw-p 00003000 08:01 3638641    /lib/tls/i686/cmov/libnss_dns-2.7.so
b30b2000-b31b3000 rw-p b30b2000 00:00 0 
b31d1000-b32d2000 rw-p b31d1000 00:00 0 
b32d2000-b32d3000 rw-s 00000000 00:09 2719799    /SYSV00000000 (deleted)
b32d3000-b33d3000 rw-s e8723000 00:0e 13174      /dev/nvidia0
b33d3000-b33d7000 rw-s 34ba6000 00:0e 13174      /dev/nvidia0
b33d7000-b34d9000 rw-s e8620000 00:0e 13174      /dev/nvidia0
b34de000-b34e0000 r-xp 00000000 08:01 3620959    /lib/libnss_mdns4_minimal.so.2
b34e0000-b34e1000 rw-p 00001000 08:01 3620959    /lib/libnss_mdns4_minimal.so.2
b34f2000-b34f4000 rwxp 00000000 00:0e 1062       /dev/zero
b34f4000-b34f6000 rwxp 00000000 00:0e 1062       /dev/zero
b34f6000-b34f8000 rwxp 00000000 00:0e 1062       /dev/zero
b34f8000-b34fa000 rwxp 00000000 00:0e 1062       /dev/zero
b34fa000-b34fc000 rwxp 00000000 00:0e 1062       /dev/zero
b34fc000-b34fe000 rwxp 00000000 00:0e 1062       /dev/zero
b34fe000-b3500000 rwxp 00000000 00:0e 1062       /dev/zero
b3500000-b3502000 rwxp 00000000 00:0e 1062       /dev/zero
b3502000-b3504000 rwxp 00000000 00:0e 1062       /dev/zero
b3504000-b3506000 rwxp 00000000 00:0e 1062       /dev/zero
b3506000-b3508000 rwxp 00000000 00:0e 1062       /dev/zero
b3508000-b350a000 rwxp 00000000 00:0e 1062       /dev/zero
b3510000-b3519000 rwxp 00000000 00:0e 1062       /dev/zero
b351a000-b357d000 rw-p 00000000 00:0e 1062       /dev/zero
b357d000-b3cb5000 rw-s e0000000 00:0e 13174      /dev/nvidia0
b3cb5000-b3cd6000 rw-p b3cb5000 00:00 0 
b3cd6000-b3d00000 rw-s 00000000 00:09 0          /SYSV00000000 (deleted)
b3d00000-b3d08000 r-xp 00000000 08:01 1172987    /usr/lib/qt4/plugins/iconengines/libqsvgicon.so
b3d08000-b3d09000 rw-p 00008000 08:01 1172987    /usr/lib/qt4/plugins/iconengines/libqsvgicon.so
b3d09000-b3d0a000 ---p b3d09000 00:00 0 
b3d0a000-b450a000 rwxp b3d0a000 00:00 0 
b450a000-b450b000 ---p b450a000 00:00 0 
b450b000-b4d0b000 rwxp b450b000 00:00 0 
b4d0b000-b4d0c000 ---p b4d0b000 00:00 0 
b4d0c000-b550c000 rwxp b4d0c000 00:00 0 
b550c000-b551e000 r--p 00000000 08:01 827437     /usr/share/fonts/type1/gsfonts/n019004l.pfb
b5c00000-b5c21000 rw-p b5c00000 00:00 0 
b5c21000-b5d00000 ---p b5c21000 00:00 0 
b5d1f000-b5d70000 r-xp 00000000 08:01 2171351    /usr/lib/libtiff.so.4.2.1
b5d70000-b5d72000 rw-p 00050000 08:01 2171351    /usr/lib/libtiff.so.4.2.1
b5d72000-b5dbf000 r-xp 00000000 08:01 707631     /usr/lib/libQtSvg.so.4.4.0
b5dbf000-b5dc1000 rw-p 0004c000 08:01 707631     /usr/lib/libQtSvg.so.4.4.0
b5dc1000-b5dee000 r-xp 00000000 08:01 2171109    /usr/lib/liblcms.so.1.0.16
b5dee000-b5df0000 rw-p 0002c000 08:01 2171109    /usr/lib/liblcms.so.1.0.16
b5df0000-b5df2000 rw-p b5df0000 00:00 0 
b5df2000-b5e5d000 r-xp 00000000 08:01 2171137    /usr/lib/libmng.so.1.1.0.9
b5e5d000-b5e60000 rw-p 0006a000 08:01 2171137    /usr/lib/libmng.so.1.1.0.9
b5e60000-b5e74000 r--p 00000000 08:01 827434     /usr/share/fonts/type1/gsfonts/n019003l.pfb
b5e74000-b5e93000 r-xp 00000000 08:01 2171093    /usr/lib/libjpeg.so.62.0.0
b5e93000-b5e94000 rw-p 0001e000 08:01 2171093    /usr/lib/libjpeg.so.62.0.0
b5e94000-b5e95000 rw-s 00000000 00:09 2752559    /SYSV00000000 (deleted)
b5e95000-b5e96000 rw-s 2a4c2000 00:0e 13174      /dev/nvidia0
b5e96000-b5e97000 rw-s e69ca000 00:0e 13174      /dev/nvidia0
b5e97000-b5e98000 rw-s e69cc000 00:0e 13174      /dev/nvidia0
b5e98000-b5e99000 rw-s 34ba5000 00:0e 13174      /dev/nvidia0
b5e99000-b5e9d000 r-xp 00000000 08:01 1122760    /usr/lib/qt4/plugins/imageformats/libqtiff.so
b5e9d000-b5e9e000 rw-p 00003000 08:01 1122760    /usr/lib/qt4/plugins/imageformats/libqtiff.so
b5e9e000-b5ea1000 r-xp 00000000 08:01 1122734    /usr/lib/qt4/plugins/imageformats/libqsvg.so
b5ea1000-b5ea2000 rw-p 00003000 08:01 1122734    /usr/lib/qt4/plugins/imageformats/libqsvg.so
b5ea2000-b5ea7000 r-xp 00000000 08:01 1122759    /usr/lib/qt4/plugins/imageformats/libqmng.so
b5ea7000-b5ea8000 rw-p 00004000 08:01 1122759    /usr/lib/qt4/plugins/imageformats/libqmng.so
b5ea8000-b5eb1000 r-xp 00000000 08:01 3638643    /lib/tls/i686/cmov/libnss_files-2.7.so
b5eb1000-b5eb3000 rw-p 00008000 08:01 3638643    /lib/tls/i686/cmov/libnss_files-2.7.so
b5eb3000-b5ebb000 r-xp 00000000 08:01 3638647    /lib/tls/i686/cmov/libnss_nis-2.7.so
b5ebb000-b5ebd000 rw-p 00007000 08:01 3638647    /lib/tls/i686/cmov/libnss_nis-2.7.so
b5ebd000-b5ed1000 r-xp 00000000 08:01 3638637    /lib/tls/i686/cmov/libnsl-2.7.so
b5ed1000-b5ed3000 rw-p 00013000 08:01 3638637    /lib/tls/i686/cmov/libnsl-2.7.so
b5ed3000-b5ed5000 rw-p b5ed3000 00:00 0 
b5ed5000-b5f1d000 r-xp 00000000 08:01 705820     /usr/lib/libORBit-2.so.0.1.0
b5f1d000-b5f27000 rw-p 00047000 08:01 705820     /usr/lib/libORBit-2.so.0.1.0
b5f27000-b5f54000 r-xp 00000000 08:01 706109     /usr/lib/libgconf-2.so.4.1.5
b5f54000-b5f57000 rw-p 0002d000 08:01 706109     /usr/lib/libgconf-2.so.4.1.5
b5f57000-b5f92000 r-xp 00000000 08:01 706057     /usr/lib/libgobject-2.0.so.0.1600.3
b5f92000-b5f93000 rw-p 0003b000 08:01 706057     /usr/lib/libgobject-2.0.so.0.1600.3
b5f93000-b5f94000 rw-s 34ba4000 00:0e 13174      /dev/nvidia0
b5f94000-b5f95000 rw-s ec830000 00:0e 13174      /dev/nvidia0
b5f95000-b5f96000 rw-s 00000000 00:09 2523181    /SYSV00000000 (deleted)
b5f96000-b5f9f000 r-xp 00000000 08:01 1122757    /usr/lib/qt4/plugins/imageformats/libqjpeg.so
b5f9f000-b5fa0000 rw-p 00008000 08:01 1122757    /usr/lib/qt4/plugins/imageformats/libqjpeg.so
b5fa0000-b5fa6000 r-xp 00000000 08:01 1122749    /usr/lib/qt4/plugins/imageformats/libqico.so
b5fa6000-b5fa7000 rw-p 00005000 08:01 1122749    /usr/lib/qt4/plugins/imageformats/libqico.so
b5fa7000-b5fa9000 r-xp 00000000 08:01 70586cleanupAbortedxzavier@Dragon:~/projectm/projectM-Trunk/src$ 



```
If i run the cmd again then this comes

```
xzavier@Dragon:~/projectm/projectM-Trunk/src$ projectM-pulseaudio 
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/xzavier/.projectM/config.inp
MAX SAMPLES:2048
load config END 
Connection failure: Connection refused
X Error: BadAccess (attempt to access private resource denied) 10
  Extension:    128 (Uknown extension)
  Minor opcode: 5 (Unknown request)
  Resource id:  0x156
projectM-pulseaudio: Fatal IO error: client killed

```

[b]since posting this i reinstalled pulseaudio and enabled it under  System -> apps -> sound
and now appears to work.. but this opened up a whole nother can of worms.. appears i cannot play audio files as well as videos on the web and other such things at the same time..[/b]

---

### Post by MinkeyMan on 2008-06-01
For all of you having diffculty installing ProjectM on Hardy:

[http://www.filefactory.com/file/562c66]("http://www.filefactory.com/file/562c66")

Try this deb file, it's the RC4 version. I'll try and compile the SVN and make a deb of that too. This is the Pulseaudio version only.

---

### Post by Jojo12a on 2008-06-01
well, can you please add the following to your control-file? Then no deb system can come into strange problems now or in future... ;)

```
Replaces: libprojectm2, libprojectm1-data, libvisual-projectm
Conflicts: libprojectm2, libprojectm1-data, libvisual-projectm, libqt4-gui (>= 4.4.0)
```

This will lead to conflicting projectM 1.0 files being properly removed... adding something like projectm-pulseaudio and libprojectm-qt1 is also good, but who knows how the valid packages will be called later ;(


doesn't work anyway for me, have you got backports' Qt 4.4.0 or main's Qt 4.3.4? I just realized that this could be the cause of my problems... ;(

well, Qt 4.4.0 is really a problem that break libprojectm-qt, so I have added it to the conflicts ;)

I've got a script for making DEB packages from SVN for libprojectm and libprojectm-qt (see attachment), but for projectM-pulseaudio, I will update it later... for now, you can use the binary which I will attach too. It works if you have the build dependencies installed (for now, I haven't managed to build in a check). You will need at least debuild, subversion, build-essentials, debhelper and libqt4-dev, besides the given build-depends. If you get an error, this will probably be because of some missing packages ;) ... it can obviously eat your cat, make your grandma explode etc., so NO WARRANTY! ;)

---

### Post by MinkeyMan on 2008-06-01
[QUOTE=jojo12a]well, can you please add the following to your control-file? Then no deb system can come into strange problems now or in future...[/QUOTE]

Jeepers, I forgot about the repository version of projectM. :) Thanks for reminding me. I'm using the main version of QT, not the backports version BTW.

I just tested this on my PC and a virtual machine with a clean install so it should work:

[Download projectm_1.1RC4_i386.deb.]("http://www.filecrunch.com/fileDownload.php?sub=fe8ee3ff304a0f349eeba737c114ad0e&fileId=152957")

Hope this works. Oh, and I apologise for the crazy array of free hosting sites.

---

### Post by Jojo12a on 2008-06-02
I have just completed Version 0.2 (the first try was 0.1) of my svn-to-deb tool for projectM... it can now compile the pulseaudio frontend. The libvisual frontend will be done later and is up to now impossible to build with my tool... just unpack the attached tarball and execute the shellscript inside. I have also added some lines of code to ask some questions which are necessary to build the packages correctly and to know what to build. For Pulseaudio, please answer 'y' to Qt and PulseAudio... if any error occurs while the packages are compiled, it's either because I missed some build-deps or because of some errors in my code or the upstream SVN code, so please tell me if there are any problems ;)...

Disclaimer: this tool can obviously eat your cat, poison your grandma, create an earthquake or do any other unexpected harm, so I don't provide any warranty whatsoever ;)

---

### Post by struktured on 2008-06-04
That's a cool little tool you got there...I wonder if it should be in our repository or not, and how I could properly add it. Perhaps "make deb" or something along those lines?

---

### Post by Jojo12a on 2008-06-04
I think it should be most wise to add a debian/ subdirectory under each projectM part (engine, qt, pulseaudio, libvisual, xmms and so on) with a rules file and things like that... then you can build each package by typing "debuild binary" or "dpkg-buildpackage -rfakeroot" in the directories... I just created customized debian/ directories based on the 1.01 package in the ubuntu repos and created a script to do that on new SVN versions... You would have to dynamically create the version number in debian/rules if you take the dirs upstream, however... My files are all in the +files subdir of the tarball...

Another question: Is it known at upstream that projectm-qt is up to now incompatible to Qt 4.4? At least it's like that with the version from backports. It would be nice if people using the backports repos would be able to stop holding back Qt 4.4 in order to get projectM 1.1+ to run ;)

---

### Post by El Lance-O on 2008-06-06
ProjectM has been working pretty good for me recently after my problems and the help from you folks.

But now I have two problems:

I REALLY hate PulseAudio. It doesn't work like ALSA where you can play multiple sources of sound. So if I want to hear my music play in Totem while on the web, I have to close Firefox. ProjectM doesn't even work with Firefox anymore as it did before.

Is there anyway to get it to work with ALSA?

And also, the disappearing mouse trick is no longer entertaining. It disappears completely now and won't come back. I have to reload metacity or compiz to get it back. This is QUITE the hassle.

I've had so many problems lately, it's horrible. :(

---

### Post by Jojo12a on 2008-06-06
For the pulseaudio things, refer to [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) and [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), especially the alsa applications section... PulseAudio's job is exactly playback from multiple sources, it just has to be setup correctly ;)

projectM will (even though I'm not the project's programmer ;) ) not support input from alsa because AFAIK alsa doesn't provide something to get the mixed data that goes to the sound card ;(

I can't say much to the rest, though ;)

---

### Post by sammydee on 2008-06-06
I can confirm the mouse disappearing trick problem... It disappears and won't come back even if the application is unfullscreened... :-(

As for pulseaudio - if you are using binary flash, you are likely to have problems with it, but only because adobe refuses to use standards compliant audio outputs - everything else should work perfectly in pulseaudio - if it doesn't, file a bug!

Sam

---

### Post by Jojo12a on 2008-06-08
I have just added libvisual support to my script... only xmms, jack and test are pending... usage is like the the last version, use it at your own risk ;)

---

### Post by El Lance-O on 2008-06-09
> **Jojo12a said:**
> For the pulseaudio things, refer to [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) and [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), especially the alsa applications section... PulseAudio's job is exactly playback from multiple sources, it just has to be setup correctly ;)

projectM will (even though I'm not the project's programmer ;) ) not support input from alsa because AFAIK alsa doesn't provide something to get the mixed data that goes to the sound card ;(

I can't say much to the rest, though ;)

That seems like an immense amount of work for something that ALSA already does. Not to mention I have to configure each aspect of my system individually to make it work? Sheesh...

I've been such a huge fan on Ubuntu for years, but ever since Gutsy...the most simple of tasks take a RIDICULOUS amount of time to achieve.

I'll go cry about it some more somewhere else. :)

---

### Post by sammydee on 2008-06-09
Wow what problems are you having with pulseaudio?

Pulseaudio SOLVED a multitude of irritating problems for me. It's far more capable than alsa, plus its about a million times easier to configure than .asoundrc, which, let's be honest, is pretty much voodoo magic for 99.999% of ubuntu users.

Pulseaudio is exactly what linux sound has been needing for years.

Sam

---

### Post by Jojo12a on 2008-06-09
Of course mixing is not the ONLY job PA has, but one of multiple ;).

You can configure it much better at runtime because it isn't at kernel level like alsa, but in userspace. You can change volumes for all input streams seperately, and PA makes standalone projectM possible ^^.

I think that, at least if all apps would right now implement the PA API or at least the ALSA API correctly, PA wouldn't have many problems anymore ;). So IMHO the problem is not PA, but the developers of apps using sound.

And now back to topic! AFAIK, ALSA output devices can't be used as input, so a soundserver is necessary, anyway. Thus, PA or another more sophisticated soundserver is needed for a standalone visualization app. IMHO, that means PA problems don't belong here anyway ;). If you don't think like that, continue complaining (I obviously can't command you, I am no mod...), but I think if you have problems with PA, discuss them in a more fitting thread ;)...

Let's discuss about ProjectM here instead ;).

---

### Post by struktured on 2008-06-09
Sorry guys,

Since I moved and I can't get my stupid verizon wireless broadband device working in linux, I've only had internet access in windows lately.

As for the mouse bug, I'll look into- although I'm confused because I haven't touched since I added the feature. Did Qt change?

For the record, PLEASE post bug reports in our tracker at:

[http://sourceforge.net/tracker/?group_id=104201](http://sourceforge.net/tracker/?group_id=104201)

I don't check the ubuntu forums all the time, so it could be much longer until I find out about a bug posted here.

Cheers and 1.2 is coming soon (fixing a couple outstanding bugs first),

struk

---

### Post by struktured on 2008-06-09
In regards to "alsa input" support,

there is alsa-based line in and mic support available via the project-libvisual-alsa subdirectory (turn on INCLUDE-PROJECTM-LIBVISUAL-ALSA and rebuild to test it out).

---

### Post by Jojo12a on 2008-06-09
It would be nice if you could also make some more or less official ubuntu packages for the 1.2 version... then nobody would have to wait for much too long times until the MOTUs do something ;)

---

### Post by struktured on 2008-06-10
Well the projectM developers (Pete and I) don't actually use ubuntu- so rather than wasting time not developing, we prefer that an ubuntu guru who likes projectM puts in the effort to do it (with our help if necessary). Also, we are terrible at making releases to begin with!

- struk

---

### Post by Jojo12a on 2008-06-10
No problem with that, I just asked ;).

Anyway: Could you implement an optional internal FTGL like you did for GLEW, at least if it's not too much work? FTGL hasn't released something new since 2004 (seems dead to me), it is statically linked anyway, and it hasn't got a that huge codebase, so it shouldn't be much of a problem. An internal and thus known-to-work FTGL would help much, especially because all FTGL versions in ubuntu since edgy lead to segfaults (both the edgy/feisty/gutsy/hardy "-3"s and intrepid's "-4"), at least since version 1.1 (It worked in ubuntu's 1.01). I suppose keeping it optional would still be the better way to go ;). I don't know how much work it is, but I think you should at least consider that.

And please make ProjectM compatible to Qt4.4 before 1.2, I would like to stop holding back the update to Qt4.4 ;).

And for the last, a bigger feature request that came over me while writing this post - I will gladly post it at sourceforge if you wish, but as we discuss here anyway, I'll better port it here: If it isn't already planned, add (optional) DBus support to the Qt backend (fits there most because it is only needed for standalone apps anyway and because Qt4 has DBus bindings - article: [http://doc.trolltech.com/qq/qq20-dbus.html](http://doc.trolltech.com/qq/qq20-dbus.html)). This would allow scripting in Amarok and a multitude of other things because it could allow for example track name display in the standalones. 

If you don't want me to make these requests here, I wouldn't have a problem to post it to the sourceforge wishlist, but as we discuss here anyway, I think asking here is better, 2 of 3 problems are helping this thread anyway ;). For an official package in intrepid, I really think that the first two problems have to be resolved first, as intrepid will certainly contain qt4.4 and doesn't up to now contain a working ftgl-dev.

Excuse me for the much too long post ;).

---

### Post by sammydee on 2008-06-18
One feature request that I posted at the bug tracker that should be pretty trivial to implement (I think) would be a sync to vblank on/off switch in the projectm preferences pane. Would save users having to force it on in their respective card control panels, and it certainly does make projectm look MUCH nicer :-)

Sam

---

### Post by Hells_Dark on 2008-06-20
It works like a charm !

---

### Post by trappy on 2008-06-21
Thanks for the howto, however I got those errors with the make commands;
```

/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returnerade avslutningsstatus 1
make[2]: *** [projectM-engine/libprojectM.so.2.00] Fel 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Fel 2
make: *** [all] Fel 2
```

Any ideas? Really wanna get this to work, thanks in advance!

---

### Post by Hells_Dark on 2008-06-21
I've got something annoying : 
When i fullscreen projectM, the mouse disappears.
And then, never goes back..

---

### Post by Jojo12a on 2008-06-21
compile with "-DUSE_FTGL=OFF" because the ubuntu ftgl-dev package isn't working correctly with projectM...

---

### Post by benow on 2008-07-03
struktured, not sure if you're still following, but I'm getting the same "terminate called after throwing an instance of 'int'" error.  Here's the backtrace after crash switching to next vis:

```
connectHelper:  "alsa_output.pci_10de_371_sound_card_0_alsa_playback_0.monitor" 
[Thread 0x4466d950 (LWP 28879) exited]
terminate called after throwing an instance of 'int'

Program received signal SIGABRT, Aborted.
[Switching to Thread 0x7f1cb745c820 (LWP 28869)]
0x00007f1cb2a08095 in raise () from /lib/libc.so.6
(gdb) bt
#0  0x00007f1cb2a08095 in raise () from /lib/libc.so.6
#1  0x00007f1cb2a09af0 in abort () from /lib/libc.so.6
#2  0x00007f1cb300c0e4 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#3  0x00007f1cb300a076 in ?? () from /usr/lib/libstdc++.so.6
#4  0x00007f1cb300a0a3 in std::terminate () from /usr/lib/libstdc++.so.6
#5  0x00007f1cb300a18a in __cxa_throw () from /usr/lib/libstdc++.so.6
#6  0x00007f1cb6f12f51 in Preset::initialize (this=0xa21ad0, 
    pathname=@0x8e7b10)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/Preset.cpp:291
#7  0x00007f1cb6f14283 in Preset (this=0xa21ad0, absoluteFilePath=@0x8e7b10, 
    presetName=@0x8e9b20, presetInputs=@0x7ef510, presetOutputs=@0x7ef630)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/Preset.cpp:67
#8  0x00007f1cb6f453e4 in PresetLoader::loadPreset (this=0x8904b0, index=0, 
    presetInputs=@0x7ef510, presetOutputs=@0x7ef630)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/PresetLoader.cpp:141
#9  0x00007f1cb6f03a38 in PresetChooser::directoryIndex (this=0x890520, 
    index=0, presetInputs=@0x7ef510, presetOutputs=@0x7ef630)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/PresetChooser.hpp:194
---Type <return> to continue, or q <return> to quit---
#10 0x00007f1cb6f03aa6 in PresetIterator::allocate (this=0x890540, 
    presetInputs=@0x7ef510, presetOutputs=@0x7ef630)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/PresetChooser.hpp:146
#11 0x00007f1cb6f32224 in projectM::default_key_handler (this=0x7ef450, 
    event=PROJECTM_KEYDOWN, keycode=PROJECTM_K_n)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/KeyHandler.cpp:171
#12 0x00007f1cb6f3276b in projectM::key_handler (this=0x7ef450, 
    event=PROJECTM_KEYDOWN, keycode=PROJECTM_K_n, 
    modifier=PROJECTM_KMOD_LSHIFT)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-engine/KeyHandler.cpp:89
#13 0x00007f1cb721cd93 in QProjectMWidget::keyReleaseEvent (this=0x777c20, 
    e=0x7fffbf6536b0)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-qt/qprojectmwidget.hpp:185
#14 0x00007f1cb6464db8 in QWidget::event () from /usr/lib/libQtGui.so.4
#15 0x00007f1cb6046491 in QGLWidget::event () from /usr/lib/libQtOpenGL.so.4
#16 0x00007f1cb64223ab in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#17 0x00007f1cb642670c in QApplication::notify () from /usr/lib/libQtGui.so.4
#18 0x00007f1cb5d60a40 in QCoreApplication::notifyInternal ()
---Type <return> to continue, or q <return> to quit---
   from /usr/lib/libQtCore.so.4
#19 0x00007f1cb646c12c in ?? () from /usr/lib/libQtGui.so.4
#20 0x00007f1cb649511f in ?? () from /usr/lib/libQtGui.so.4
#21 0x00007f1cb6496fb9 in ?? () from /usr/lib/libQtGui.so.4
#22 0x00007f1cb647533e in QApplication::x11ProcessEvent ()
   from /usr/lib/libQtGui.so.4
#23 0x00007f1cb64983ea in ?? () from /usr/lib/libQtGui.so.4
#24 0x00007f1cb1ab8262 in g_main_context_dispatch ()
   from /usr/lib/libglib-2.0.so.0
#25 0x00007f1cb1abb516 in ?? () from /usr/lib/libglib-2.0.so.0
#26 0x00007f1cb1abb9af in g_main_context_iteration ()
   from /usr/lib/libglib-2.0.so.0
#27 0x00007f1cb5d81c51 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#28 0x00007f1cb649820f in ?? () from /usr/lib/libQtGui.so.4
#29 0x00007f1cb5d5ff28 in QEventLoop::processEvents ()
   from /usr/lib/libQtCore.so.4
#30 0x00007f1cb5d60046 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#31 0x00007f1cb5d62291 in QCoreApplication::exec ()
   from /usr/lib/libQtCore.so.4
#32 0x000000000040f6ec in main (argc=1, argv=0x7fffbf654b28)
    at /archive/incoming/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:120

```

Your instructions worked fine on previous install, but getting that error on current fresh install.

Thanks!

---

### Post by struktured on 2008-07-03
A preset is failing to load on your system. My code throws an unhandled exception in that case. I will improve the error handling. Do you know what preset it is trying to load up? Is the path valid?

---

### Post by quanumphaze on 2008-07-17
Is there any way to make it faster? It slows my system to a crawl and runs at ~5fps.

I'm running this on pretty weak hardware (Intel 945GM) but Milkdrop worked very fast in Winamp back then where I had that running at full 1280x1024

Does ProjectM add more advanced cycle eating stuff that I can turn off?

---

### Post by trappy on 2008-07-18
Still no amd64 deb file that works? :(

---

### Post by sammydee on 2008-07-18
> **quanumphaze said:**
> Is there any way to make it faster? It slows my system to a crawl and runs at ~5fps.

I'm running this on pretty weak hardware (Intel 945GM) but Milkdrop worked very fast in Winamp back then where I had that running at full 1280x1024

Does ProjectM add more advanced cycle eating stuff that I can turn off?

What settings do you have in the projectm preferences panel? Are you running compiz at the same time?

Sam

---

### Post by quanumphaze on 2008-07-18
> **sammydee said:**
> What settings do you have in the projectm preferences panel? Are you running compiz at the same time?

Sam

What's the command for that? The howto mentions that it's in "settings/configure projectM" but it doesn't seem to exist on my system.

I used checkinstall, would this have caused it?

---

### Post by sammydee on 2008-07-18
> **quanumphaze said:**
> What's the command for that? The howto mentions that it's in "settings/configure projectM" but it doesn't seem to exist on my system.

I used checkinstall, would this have caused it?

I had problems using checkinstall with projectm but I doubt that would cause performance issues. To get the settings screen up, launch projectm-pulseaudio and press m to bring up the menu. Settings/configure projectm should be there now.

sam

---

### Post by quanumphaze on 2008-07-19
Got it! Thanks.

[IMG]http://lh6.ggpht.com/quantumphazor/SIF6KlvGjNI/AAAAAAAAAEM/KZpHZUYmkEQ/s800/Screenshot-projectM%20Settings.png[/IMG]

---

### Post by sammydee on 2008-07-19
Hmm shouldn't be slow with those settings on that video card, are you sure you aren't running compiz at the same time?

Sam

---

### Post by quanumphaze on 2008-07-19
I am definitely not using Compiz.

The speed becomes acceptable when I reduce the size of the window to thumbnail size.

It is really slow still when I reduced the values of texture size=8, and halved the mesh size values. In fact I would say it's the exact same speed. I have no idea what's going on, I can play 3d games fine on this machine, why is this slow?

When it starts up it prints:

```
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/andrew/.projectM/config.inp
MAX SAMPLES:**2048**
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor"
```
I don't like the look of that 2048. Can that be reduced?

---

### Post by sammydee on 2008-07-19
Are you using projectm-pulseaudio?

sam

---

### Post by quanumphaze on 2008-07-19
> **sammydee said:**
> Are you using projectm-pulseaudio?

Yes

(PS: I'm going to bed so I won't be responding for a while)

---

### Post by quanumphaze on 2008-07-20
Just did some googling and found some bug reports that may be effecting me:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg764070.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg764070.html)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/177492)

My xorg.conf```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"euro"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"True"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"FramebufferCompression"	"off"
	Driver		"intel"
	Option 		"AccelMethod" 			"XAA"
	Option 		"XAANoOffscreenPixmaps" 	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual		2048 2048
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

I'll try to use EXA and comment out the XAANoOffscreenPixmaps.

---

### Post by quanumphaze on 2008-07-20
Didn't work.

---

### Post by sammydee on 2008-07-20
What about other opengl apps? Do they run ok? If they do, I highly doubt any changes to xorg.conf are going to resolve this.

If it is still running slow even 8x8 texture size that's a serious problem somewhere that playing around with the settings panel in projectm won't fix. You could try pulling down the mesh size to something ridiculously small and see if it's a cpu bottleneck? What is cpu usage like?

Sam

---

### Post by quanumphaze on 2008-07-20
Playing with xorg.conf did nothing

I reduced the mesh sizes to 1x1 and the texture size to 2 and it still guzzles 100% CPU to give my a low framerate. Reducing the window to within 100x100 ups the framerate to acceptable levels but that is hardly usable.

Glxgears gives me very good framerates over 800 fps so there shouldn't be any problems with OpenGL.

There must be something breaking at compile time. Either that or the projectM code isn't optimised for speed for on-board cards yet. Does projectM use more complex mathematics than Milkdrop?

When it starts up it says "MAX SAMPLES:2048" can I change this setting to something lower?

---

### Post by Jester_Racer on 2008-07-20
Hi all! I'm trying to install projectM like you do it in this tutorial but i get this error:
```
CMake Error: Cannot find source file "/usr/src/projectm/projectM-Trunk/src/projectM-engine/UserTexture.cpp" for target "projectM"
```

Any suggestions? Thanks

Edit: Actually I use Debian 64bit, but I don't think this is the problem.

---

### Post by diggity on 2008-07-20
I had the same issue. To fix it, go here...
[https://projectm.svn.sf.net/svnroot/projectm/trunk/src/projectM-engine/](https://projectm.svn.sf.net/svnroot/projectm/trunk/src/projectM-engine/)
Right-click on "UserTexture.cpp" and click "Save Link As..." and save it in your projectM-engine folder.
Do the same with UserTexture.hpp
You should be able to generate the makefile.

---

### Post by vmxmv on 2008-07-20
While making, I got the following error:
```

[  1%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Renderer.o
/home/mcv/tmp/project-m/projectM-Trunk/src/projectM-engine/Renderer.cpp: In member function ‘void Renderer::reset(int, int)’:
/home/mcv/tmp/project-m/projectM-Trunk/src/projectM-engine/Renderer.cpp:587: error: ‘shaderEngine’ was not declared in this scope
make[2]: *** [projectM-engine/CMakeFiles/projectM.dir/Renderer.o] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

Could someone help me with this, please?

---

### Post by Jester_Racer on 2008-07-20
Thank You, diggity! I searched on the net but didn't find these files...
Now I'm trying to make it... :)

---

### Post by sammydee on 2008-07-21
> **quanumphaze said:**
> Playing with xorg.conf did nothing

I reduced the mesh sizes to 1x1 and the texture size to 2 and it still guzzles 100% CPU to give my a low framerate. Reducing the window to within 100x100 ups the framerate to acceptable levels but that is hardly usable.

Glxgears gives me very good framerates over 800 fps so there shouldn't be any problems with OpenGL.

There must be something breaking at compile time. Either that or the projectM code isn't optimised for speed for on-board cards yet. Does projectM use more complex mathematics than Milkdrop?

When it starts up it says "MAX SAMPLES:2048" can I change this setting to something lower?

No idea what is going on here at all. You should probably log on to #projectm and let the devs know about this problem, sounds like a serious bug somewhere.

Sam

---

### Post by sammydee on 2008-07-21
> **vmxmv said:**
> While making, I got the following error:
```

[  1%] Building CXX object projectM-engine/CMakeFiles/projectM.dir/Renderer.o
/home/mcv/tmp/project-m/projectM-Trunk/src/projectM-engine/Renderer.cpp: In member function ‘void Renderer::reset(int, int)’:
/home/mcv/tmp/project-m/projectM-Trunk/src/projectM-engine/Renderer.cpp:587: error: ‘shaderEngine’ was not declared in this scope
make[2]: *** [projectM-engine/CMakeFiles/projectM.dir/Renderer.o] Error 1
make[1]: *** [projectM-engine/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

Could someone help me with this, please?

Did you enable cg shader effects in cmake? If so, try installing nvidia-cg-toolkit, or disable the cg option in cmake.

Sam

---

### Post by quanumphaze on 2008-07-21
Also worth mentioning is that when I try to play Warzone 2100 (really old), the game plays fine for 5 seconds then the framerate drops down to 3fps. This is at the lowest settings.

The weird thing is that it runs at a normal framerate for 5 seconds then drops. The 2 issues may be related (though projectM is slow from the instant the window appears). All other games seem to play fine.

The problems I have may be deeper than projectM. I shall try another distro to see if it's just Ubuntu and my computer (Arch, if I fail that then Mandriva).

---

### Post by quanumphaze on 2008-07-21
Please disregard the part about Warzone 2100. I really should try harder to solve my own problems.

FYI: the problem for it was that texturesize must be <=64 on the :~/.warzone2100-2.1/config file, from [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=472403")

---

### Post by punkrockguy318 on 2008-07-22
ccmake . and g is giving me an error about libvisual-0.4 not being installed, when it and -dev is clearly installed.  not sure what to do here

---

### Post by gnrathon on 2008-07-22
The program 'ccmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake
bash: ccmake: command not found


brian@brian:~$ sudo apt-get install cmake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cmake is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@brian:~$

---

### Post by hansoffate on 2008-07-23
I've tried following the guide twice.  I keep getting the same error. The make gets up to 21% and then stops because of something associated with Renderer.  Any ideas?

Thanks,
Hans

```
[ 21%] Building CXX object libprojectM/CMakeFiles/projectM.dir/Renderer.o
/home/hansoffate/projectm/projectM-Trunk/src/libprojectM/Renderer.cpp: In member function ‘void Renderer::reset(int, int)’:
/home/hansoffate/projectm/projectM-Trunk/src/libprojectM/Renderer.cpp:587: error: ‘shaderEngine’ was not declared in this scope
make[2]: *** [libprojectM/CMakeFiles/projectM.dir/Renderer.o] Error 1
make[1]: *** [libprojectM/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by Grimmwolf on 2008-07-23
Same problem here.
Does anyone have a solution for this?

---

### Post by sammydee on 2008-07-23
> **Grimmwolf said:**
> Same problem here.
Does anyone have a solution for this?

Yes, you enabled cg in ccmake. This allows shader effects in milkdrop 2.0 presets with compatible cards/drivers. You need to install the package nvidia-cg-toolkit then compile again.

---

### Post by Grimmwolf on 2008-07-24
Hmm, I enabled CG (it was not enabled in ccmake before) and installed the toolkit. It then compiled fine, but upon running projectM-pulseaudio it crashes with a fatal cd compiler error. Probably because I am testing this on an on-board intel laptop card.

---

### Post by sammydee on 2008-07-24
I talked to the dev about it, apparently the cg stuff is experimental and I'd be very surprised if it worked at all on anything other than nvidia cards. However, the intel drivers do support shaders so it's not technically impossible.

If it is not compiling even with cg disabled then that's a bug and should be reported to the devs on irc, channel is #projectm on irc.freenode.net. They're on there most of the time.

Sam

---

### Post by Xzavier on 2008-07-25
assistance? 

```

xzavier@Dragon2:~/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/xzavier/.projectM/config.inp
MAX SAMPLES:2048
Cg: Initialized profile: gp4fp
(0) : fatal error C9999: *** exception during compilation ***
Cg compiler terminated due to fatal errorxzavier@Dragon2:~/projectM-Trunk/src$

```

---

### Post by Sigiken on 2008-07-25
Everything installed fine but when I try to run projectM-pulseaudio it gives me the folowing error:
```

jonas@jonas-desktop:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/jonas/.projectM/config.inp
MAX SAMPLES:2048
Cg: Initialized profile: gp4fp
(0) : fatal error C9999: *** exception during compilation ***
Cg compiler terminated due to fatal errorjonas@jonas-desktop:~$ 
```

---

### Post by redroad55 on 2008-07-26
here's what I get /home/john/Desktop/Screenshot.png

---

### Post by redroad55 on 2008-07-26
oops here's the shot

---

### Post by Cas07 on 2008-08-01
got the same issue with the make failing with renderer issue if i turn off use_CG but if it is on and i have the nvidia tools installed it will build but the app will not run (fatal error C9999) ...

---

### Post by sammydee on 2008-08-05
> **Caos said:**
> got the same issue with the make failing with renderer issue if i turn off use_CG but if it is on and i have the nvidia tools installed it will build but the app will not run (fatal error C9999) ...

Better report this bug directly to the devs, they don't look here very often. You can find them on the oft mentioned (in this thread) irc channel.

Sam

---

### Post by psperl on 2008-08-05
Hi, I'm Pete, projectM's lead dev.

Yesterday I saw a newly-converted friend of mine using Ubuntu on a new laptop and I was blown away by the integration and degree of "it just works".  I'ma a Gentoo/KDE guys so needless to say it was quite a shock. Then I accidentally came across this forum and thought I should probably help you guys out as Ubuntu seems to be the future (and present) and most projectM users are probably also Ubuntu users.

So, I have fixed that compile bug when USE_CG is off, it was a careless mistake, sorry.  However, projectM trunk is under going serious rework at the moment for projectM 2.0 (pixel shaders + milkdrop 2.0 compatability), so I may accidentally break it again.

I also do not understand why projectM is crashing with a C9999 error when USE_CG is enabled.  It would be very useful if someone could run 'ddd projectM-pulseaudio' or 'ddd <any projectM app>', press Run, and report the stacktrace or line number where it crashes. 

Also, does projectM work with USE_CG on for anyone?  Cause if it does, you should check out the presets in trunk/presets_milkdrop_200 and you'll some high-tech shader goodness!

Good luck.

             -Pete

---

### Post by sammydee on 2008-08-06
Thanks pete, this is great news.

When the next stable release comes out hopefully we can convince somebody to do a good job of packaging it up properly for the repos. Compiling from svn is not always an easy task for new users and a lot of people are probably missing out on projectm because it is too difficult to install and/or run.

If necessary I will try to learn how to package it myself because I really think a lot of people are missing out on some great software just because it's not as easy to install as it should be.

Sam

---

### Post by skram on 2008-08-07
Hi pete,

I'm not familiar with linux debuggers, but I will give it a try:

```

(gdb) frame 0
#0  0xffffffff85b8bda0 in ?? ()
(gdb) frame 1
#1  0x00007ff8854c43e5 in SOIL_internal_create_OGL_texture (data=0x108ac40 "", width=256, height=256, channels=4, reuse_texture_ID=0, flags=41, opengl_texture_type=3553, opengl_texture_target=3553, texture_check_size_enum=3379) at /home/rainer/work/src/projectm/projectm/src/libprojectM/SOIL.c:1247
(gdb) frame 2
#2  0x00007ff8854c2bb4 in SOIL_load_OGL_texture_from_memory (buffer=0x7ff8854df780 "", buffer_length=27965, force_channels=0, reuse_texture_ID=0, flags=41) at /home/rainer/work/src/projectm/projectm/src/libprojectM/SOIL.c:275
(gdb) frame 3
#3  0x00007ff8854ad102 in TextureManager::Preload (this=0x1053c80) at /home/rainer/work/src/projectm/projectm/src/libprojectM/TextureManager.cpp:72
Current language:  auto; currently c++

```

I hope this may help you. If not, please tell me how to get the required infos. 

Edit:

I tried to use devil instead of internal soil, but then I got following error:

```

[ 30%] Building CXX object libprojectM/CMakeFiles/projectM.dir/TextureManager.o
/home/rainer/work/src/projectm/projectm/src/libprojectM/TextureManager.cpp: In member function »GLuint TextureManager::getTextureFullpath(std::string, std::string)«:
/home/rainer/work/src/projectm/projectm/src/libprojectM/TextureManager.cpp:191: Fehler: »width« wurde in diesem Gültigkeitsbereich nicht definiert
/home/rainer/work/src/projectm/projectm/src/libprojectM/TextureManager.cpp:192: Fehler: »height« wurde in diesem Gültigkeitsbereich nicht definiert
make[2]: *** [libprojectM/CMakeFiles/projectM.dir/TextureManager.o] Fehler 1
make[1]: *** [libprojectM/CMakeFiles/projectM.dir/all] Fehler 2
make: *** [all] Fehler 2

```

The compile error with CG=off ist still present in svn repository (revison 1127)


Cya(o) 
. . . Rainer

---

### Post by samantha543 on 2008-08-10
Hi, just want to start this off by saying I am a complete linux n00b (just installed it yesterday). The command line interface scares me, but I've been trying my best with it. 

I followed all the instructions but got an error with CG off that wouldn't allow me to complete the installation. I then installed the nvidia thing and compiled with CG on and the installation completed successfully... but now when I try to run the actual program it crashes upon opening it.

Since I know very little about how to fix this, I think I would like to remove the program entirely and wait for a more stable/user friendly release. How do I remove it? Can you tell which directories I need to delete and how I should delete them?

Thank you,
Sam

---

### Post by sammydee on 2008-08-11
Hi samantha.

Try downloading the 1.1 release instead of the svn, it compiles very easily and doesn't have any problems with cg. It's not that old at all either.

Sam

---

### Post by MaxIBoy on 2008-08-11
The install process from SVN went like normal (except for a number of warnings in ccmake,) but it won't work. If I run it from the menu, a window appears for a split second and disappears. Here's what I get if I run it from the terminal:

```
maxtothemax@maxtothemax-laptop:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/maxtothemax/.projectM/config.inp
MAX SAMPLES:2048
No Textures Loaded from /usr/share/projectM/textures
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault
maxtothemax@maxtothemax-laptop:~$ 

```

I find it hard to believe that someone would do an SVN commit with code that has a segfault in it, so it's probably something at my end.

---

### Post by skram on 2008-08-11
Just compiled rev 1128. Compiles fine with cg=off), but error when starting programm:

```
(gdb) frame 4
#4  0x00007f679921d57a in TextureManager (this=0xad4900, _presetURL=@0x7fffa1930910) at /home/rainer/work/src/projectm/projectM-Trunk/src/libprojectM/TextureManager.cpp:44
(gdb) frame 3
#3  0x00007f679921d2ee in TextureManager::Preload (this=0xad4900) at /home/rainer/work/src/projectm/projectM-Trunk/src/libprojectM/TextureManager.cpp:72
(gdb) frame 2
#2  0x00007f679922ca34 in SOIL_load_OGL_texture_from_memory (buffer=0x7f6799249680 "", buffer_length=27965, force_channels=0, reuse_texture_ID=0, flags=41) at /home/rainer/work/src/projectm/projectM-Trunk/src/libprojectM/SOIL.c:275
Current language:  auto; currently c
(gdb) frame 1
#1  0x00007f679922e265 in SOIL_internal_create_OGL_texture (data=0xad49f0 "", width=256, height=256, channels=4, reuse_texture_ID=0, flags=41, opengl_texture_type=3553, opengl_texture_target=3553, texture_check_size_enum=3379) at /home/rainer/work/src/projectm/projectM-Trunk/src/libprojectM/SOIL.c:1247
(gdb) frame 0
#0  0xffffffff998f3da0 in ?? ()
```


Cya(o)
 . . . Rainer

---

### Post by sammydee on 2008-08-12
It's pretty useless reporting these sort of showstopping bugs here. Although I wrote the guide, I am NOT a dev and these sort of issues are really way out of my league to fix. It's much more useful if you let the devs know directly.

Get on IRC or the bug tracker and tell them their app is broken!

Sam

---

### Post by Jojo12a on 2008-08-13
Just one comment to my package builder: I will pretty much discontinue it now, because there is a version 1.2 now (I just realized that it is out for 2 months now :lolflag: ) and SVN is becoming more and more unstable and unusable anyway. I think that they are beginning to develop version 2.0 ;)

I found out that the Qt 4.4 incompatibility only occurs with non-english locales... In order to fix it, just execute projectm-pulseaudio like that:

```
LC_NUMERIC=C projectm-pulseaudio
```

I have uploaded some packages for version 1.2, including the sources (not in dsc/tar.gz/diff format, but just as one tarball)... the sources are meant for Qt4.4, as otherwise the build-dependency libqt4-opengl-dev is not met. I will do this in two posts...

---

### Post by Jojo12a on 2008-08-14
followup upload
please strip the .zip off the .7z file, this is NOT a zip file, I needed compression in order to make the file smaller than the limit, you will need one of the p7zip* packages...

PS: Everything is only for Qt4.4 because the packaging structures have changed... and everything can eat your cat and such things ;)

---

### Post by airtonix on 2008-08-14
one thing : you mention that mikdrop is used by winamp for visualistaions.

i thought it was the advanced visualisation studio that winamp used? to me this is the one thing i always wanted in linux.

---

### Post by RSingh on 2008-08-22
Getting the same problem:

```
sandman@procyon:~/projectm/projectM-Trunk/src$ projectM-test
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1280 x 800
configFile: /home/sandman/.projectM/config.inp
MAX SAMPLES:2048
No Textures Loaded from /usr/share/projectM/textures
Segmentation fault

```
](*,)](*,)

I will try contacting the devs about this and reply in time

---

### Post by RSingh on 2008-08-22
> **MaxIBoy said:**
> The install process from SVN went like normal (except for a number of warnings in ccmake,) but it won't work. If I run it from the menu, a window appears for a split second and disappears. Here's what I get if I run it from the terminal:

```
maxtothemax@maxtothemax-laptop:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
configFile: /home/maxtothemax/.projectM/config.inp
MAX SAMPLES:2048
No Textures Loaded from /usr/share/projectM/textures
load config END 
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault
maxtothemax@maxtothemax-laptop:~$ 

```

I find it hard to believe that someone would do an SVN commit with code that has a segfault in it, so it's probably something at my end.





I think I have found it!

try turning off the "USE FBO" parameter when doing ccmake. Worked for me:guitar:

---

### Post by sammydee on 2008-08-22
I think this is because only nvidia cards have drivers that support framebuffer objects at the moment, so intel cards will fail.

sam

---

### Post by durand on 2008-08-22
I'm trying to get this working in Intrepid but I'm getting an error at the start of compilation. I think this has something to do with new updates to svn.

> -- Generating done
-- Build files have been written to: /home/durand/Stuff/Source/projectm/projectM-Trunk/src
[  0%] Building CXX object libprojectM/CMakeFiles/projectM.dir/projectM.o
In file included from /home/durand/Stuff/Source/projectm/projectM-Trunk/src/libprojectM/projectM.cpp:59:
/home/durand/Stuff/Source/projectm/projectM-Trunk/src/libprojectM/Renderer.hpp:28:23: error: FTGL/FTGL.h: No such file or directory
In file included from /home/durand/Stuff/Source/projectm/projectM-Trunk/src/libprojectM/Renderer.hpp:29,
                 from /home/durand/Stuff/Source/projectm/projectM-Trunk/src/libprojectM/projectM.cpp:59:
/usr/include/FTGL/FTGLPixmapFont.h:29:5: warning: #warning This header is deprecated. Please use <FTGL/ftgl.h> from now.
make[2]: *** [libprojectM/CMakeFiles/projectM.dir/projectM.o] Error 1
make[1]: *** [libprojectM/CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2


I'm not sure what the problem is here :|

Thanks in advance.

---

### Post by RSingh on 2008-08-23
> **sammydee said:**
> I think this is because only nvidia cards have drivers that support framebuffer objects at the moment, so intel cards will fail.

sam

Precisely, FBO is used in stuff like Blur and MBlur in compiz and those things don't due to the broken implementation of FBO in intel cards. Due to this reason the entire thing has to be rendered via software and thus ProjectM runs like s*** if compiled without FBO and segfaults if done otherwise.:(

---

### Post by MaxIBoy on 2008-08-30
> **Jojo12a said:**
> Just one comment to my package builder: I will pretty much discontinue it now, because there is a version 1.2 now (I just realized that it is out for 2 months now :lolflag: ) and SVN is becoming more and more unstable and unusable anyway. I think that they are beginning to develop version 2.0 ;)

I found out that the Qt 4.4 incompatibility only occurs with non-english locales... In order to fix it, just execute projectm-pulseaudio like that:

```
LC_NUMERIC=C projectm-pulseaudio
```

I have uploaded some packages for version 1.2, including the sources (not in dsc/tar.gz/diff format, but just as one tarball)... the sources are meant for Qt4.4, as otherwise the build-dependency libqt4-opengl-dev is not met. I will do this in two posts...

Yay, works now. Had to wade into dependency hell for about twenty minutes, luckily the packages I needed could be downloaded from Ubuntu's Intrepid repository (I run Hardy) through Firefox.

---

### Post by Jojo12a on 2008-08-31
> **MaxIBoy said:**
> Yay, works now. Had to wade into dependency hell for about twenty minutes, luckily the packages I needed could be downloaded from Ubuntu's Intrepid repository (I run Hardy) through Firefox.
Well, actually this package IS meant for hardy, but with activated backports. I always had the problem that my package didn't run correctly with Qt4.4 installed, so this package is there just to fix exactly that problem... the problem is that it was also compiled with Qt4.4 libraries, so that it won't work with Qt4.3... so, if you activate the backports repo in the "Package Sources" (don't know how it is called in the english locale), then you won't have a problem.

And one comment to the fact that I needed so long until I realized that 1.2 was out: projectM hasn't mentioned on their homepage that 1.2 was released, so I just browsed their SF repository and found out that there IS such a version...

EDIT: I have now successfully compiled libvisual-projectm 1.2, the files are attached, and can - as usual - eat your cow or kill your grandma, even though this is as unlikely as with the original sources ;).

---

### Post by Kedster on 2008-09-01
Now cmake will load. Press "c" to configure projectM. Highlight the CMAKE_BUILD_TYPE field, press enter and type "Release" there. Press enter again. Then highlight the CMAKE_INSTALL_PREFIX field and change /usr/local to /usr/. Then press "c" again to configure it with those parameters.

I didnt do that art how do i correct this part

---

### Post by Jojo12a on 2008-09-02
hm... as this is a cmake based project, the usual "make distclean" won't work. Before doing the following, if you want to clean up your install, delete all the files mentioned in cmake_install.cmake, unluckily cmake doesn't have a "make uninstall" :(... then you usually just have to do the following, assuming you are in the build directory, then everything should be as before:

```
make clean
# look at the comment below before doing this
rm -r CMakeFiles/ CMakeCache.txt cmake_install.cmake config.inp install_manifest.txt Makefile
```

If you want to overcome this situation the next time, just do a so called "out-of-source build" by not running "ccmake ." but "ccmake *directory*" from outside the place your sources reside in. Then you can just delete the new directory and start right back from the beginning ;).

---

### Post by xtrondo on 2008-09-02
Hi, 
  
 I bump on this thread while searching for another thing, and just like to add some info, I port recently audacious with projectM 1.2.0 to opensolaris
and I also get and fix the same 2 issues listed on this thread , the one about the include is just because FTGL change include to lower case, and the segmentation fault in FBO is the glew support code, follows are the 2 patchs I use, and libprojectM is working without any issue with FBO and pixel shaders, performance is great on my Nevada laptop (openSolaris build96), I guess this could be used also here, hope it helps.

 Kind Regards,
 Carlos Almeida, 

both patchs in "attach"

---

### Post by hansoffate on 2008-09-10
I saw on pages 11  and 12 people mentioned the mouse disappearing issue.

I've loved projectM but this is starting to become a real big annoyance.  Is there anyway to fix this other then restarting x?

Thanks,
Hans

---

### Post by sammydee on 2008-09-10
Yes, reloading the window manager fixes it, try alt-f2 and executing compiz --replace or metacity --replace depending on your preference.

Not ideal but it works.

Sam

---

### Post by struktured on 2008-09-18
Hey guys,

I still can't replicate the mouse disappearing issue. Anyone speculating as to why it only happens to some users?

-struk

---

### Post by sammydee on 2008-09-20
Could be an issue with a compositing window manager?

Also, I'm running projectm in gnome, maybe it only affects gtk applications?

Sam

---

### Post by punkrockguy318 on 2008-09-27
2.0 is working fine for me, however cmake has trouble detecting that pulseaudio is installed.  i had to take out the pulseaudio checking lines in the cmake scripts to get it to compile, but it works great other than that

---

### Post by fizyxnrd on 2008-10-14
I installed the projectM and libvisual packages from the canonical repository for hardy.  This got the libvisual plugins and the projectM libvisual plugin working in amarok.  However, the projectM plugin did not behave well (graphical artifacts), and when I tried to bring up the menu (F1) the cursor locked and I could not recover without a restart.
I installed using the current svn and didn't have any luck either.  I have the projectM-libvisual plugin made, but amarok doesn't recognize it in amarok_libvisual.  
```
amarok_libvisual
libvisual CRITICAL: amarok_libvisual: visual_plugin_get_references(): Cannot load plugin: libgomp.so.1: shared object cannot be dlopen()ed
jess
bumpscope
corona
lv_flower
infinite
jakdaw
lv_analyzer
lv_gltest
lv_scope
madspin
nastyfft
oinksie

```

When I run projectM-pulseaudio, I get this error:
```
projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
projectM-pulseaudio: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
Aborted


```

Finally, when I run projectM-test, I get the following output:
```
projectM-test
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1280 x 1024
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
configFile: /home/knielson/.projectM/config.inp
MAX SAMPLES:2048
No Textures Loaded from /usr/share/projectM/textures

```

and the projectM window refuses to close.  I compiled this with FBO turned off.  When I compiled with FBO on, I got the same output followed by a seg fault, and no window.

I am using Gnome, and running on an integrated S3 ProSavage 8.
Are these details helpful?  What can I do to get things running?

---

### Post by fizyxnrd on 2008-10-15
Well, I went ahead and installed projectM and libvisual through amarok on a friend's ubuntu system, and everything worked reasonably well.  I'm forced to conclude that the S3 ProSavage GMA is just friggin' old.  Hope this helps anyone with similar problems.

---

### Post by Rangua on 2008-10-28
hi, i've tried to install projectm from synaptic, but after it installs the command isn't available... i've tried looking for the program but it seems it didn't got installed.. i've also tried doing the svn thing, but i get an error saying (on make): 
> /home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:31:26: warning: character constant too long for its type
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:32:34: warning: character constant too long for its type
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:33:25: warning: character constant too long for its type
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp: In function &#8216;std::string getConfigFilename()&#8217;:
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:31: error: invalid conversion from &#8216;int&#8217; to &#8216;const char*&#8217;
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:31: error:   initializing argument 2 of &#8216;char* strcpy(char*, const char*)&#8217;
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:32: error: invalid conversion from &#8216;int&#8217; to &#8216;const char*&#8217;
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:32: error:   initializing argument 1 of &#8216;size_t strlen(const char*)&#8217;
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:33: error: invalid conversion from &#8216;int&#8217; to &#8216;const char*&#8217;
/home/rangua/projectm/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:33: error:   initializing argument 1 of &#8216;size_t strlen(const char*)&#8217;
make[2]: *** [projectM-test/CMakeFiles/projectM-test.dir/getConfigFilename.cpp.o] Error 1
make[1]: *** [projectM-test/CMakeFiles/projectM-test.dir/all] Error 2
make: *** [all] Error 2


and i've also tried downloading the source and installing it, but when i do make install i can't find where the binary went (probably happens the same with the .deb).. here are the last lines of make install:
-- Up-to-date: /usr/share/projectM/fonts/Vera.ttf
-- Up-to-date: /usr/lib/pkgconfig/libprojectM.pc
-- Installing: /usr/share/projectM/config.inp
-- Up-to-date: /usr/include/libprojectM/projectM.hpp
-- Up-to-date: /usr/include/libprojectM/event.h
-- Up-to-date: /usr/include/libprojectM/dlldefs.h
-- Up-to-date: /usr/include/libprojectM/fatal.h
-- Up-to-date: /usr/include/libprojectM/PresetFrameIO.hpp
-- Up-to-date: /usr/include/libprojectM/PCM.hpp

up from here all goes into /usr/share/projectM... 
help? please... :confused:

i'm using intrepid, amd64

---

### Post by lamelos on 2008-10-29
> **durand said:**
> I'm trying to get this working in Intrepid but I'm getting an error at the start of compilation. I think this has something to do with new updates to svn.



I'm not sure what the problem is here :|

Thanks in advance.

I had the same problem, but seem to have 'fixed' it now.
The problem seems to be that FTGL.h is in lowercase (on my pc it was anyway - Intrepid 8.10) and thus it can't be found by the 'make'-command.

This is how i fixed it:

Before you do 'make'
```
cd libprojectM
gedit Renderer.hpp

```

then edit lines 28-30 from
this:
```
#include <FTGL/FTGL.h>
#include <FTGL/FTGLPixmapFont.h>
#include <FTGL/FTGLExtrdFont.h>
```
to this:
```
#include <FTGL/ftgl.h>
/**#include <FTGL/FTGLPixmapFont.h> */
/**#include <FTGL/FTGLExtrdFont.h> */
```

after this, exit gedit
and
```

cd ..
make

```

now the make succeeds, and you can proceed with 
```

sudo make install

```

Hope it works for you as well.

---

### Post by Zularan on 2008-11-05
Just confirming this works fine for Intrepid.

Steps I used were:

```
sudo aptitude install libglew1.5 libglew1.5-dev ftgl-dev libpulse-dev subversion cmake libvisual-0.4-dev libsdl-dev libqt4-dev build-essential
```

```
cd ~
mkdir projectm
cd projectm
svn co https://projectm.svn.sf.net/svnroot/projectm/trunk projectM-Trunk
```

```
cd projectM-Trunk/src
```

```
ccmake .
```

> Now cmake will load. Press "c" to configure projectM. Highlight the CMAKE_BUILD_TYPE field, press enter and type "Release" there. Press enter again. Then highlight the CMAKE_INSTALL_PREFIX field and change /usr/local to /usr/. Then press "c" again to configure it with those parameters.

Had some warnings that looked like 
> CMake Warning (dev) at projectM-libvisual/CMakeLists.txt:14 (ADD_DEFINITIONS):
  Policy CMP0005 is not set: Preprocessor definition values are now escaped
  automatically.  Run "cmake --help-policy CMP0005" for policy details.  Use
  the cmake_policy command to set the policy and suppress this warning.
This warning is for project developers.  Use -Wno-dev to suppress it.


I went on anyway.

First make failed but lamelos' fix worked fine.

> **lamelos said:**
> 
```
cd libprojectM
gedit Renderer.hpp

```

then edit lines 28-30 from
this:
```
#include <FTGL/FTGL.h>
#include <FTGL/FTGLPixmapFont.h>
#include <FTGL/FTGLExtrdFont.h>
```
to this:
```
#include <FTGL/ftgl.h>
/**#include <FTGL/FTGLPixmapFont.h> */
/**#include <FTGL/FTGLExtrdFont.h> */
```

after this, exit gedit
and
```

cd ..

```
Now cmake . worked
```
cmake .
```

> **lamelos said:**
> ```
make

```

now the make succeeds, and you can proceed with 
```

sudo make install

```



projectM-pulseaudio should be in Menu -> Sound and Video 
or cli ```
projectM-pulseaudio
```

Worked today with svn revision 1198 on Intrepid.

---

### Post by mocha on 2008-11-06
I thought projectM was supposed to be in Intrepid repositories?  I haven't upgraded yet.

---

### Post by arkmundi on 2008-11-06
Thanks to the folks working on this.  I'm the kind of Ubuntu user that balks at 'programming' my machine - just want to reach into the repository and get what works.  So I ditched MS Windows, bought a Dell 1525, went through the learning curve, upgraded to 8.04 Hardy and continued on the path of finding replacements for everything windows.  I'm satisfied, except for that winamp-milkdrop thing.  Found my way here.  Hope one of you ubuntu projectm-libvisual-pulseaudio stalwarts will post a message letting us know when.  Looks close.  Many thanks!

---

### Post by durand on 2008-11-06
Seems like only the libvisual version is in the repos, not pulseaudio :( but compiling it was really fast and works great! Too bad I don't have a use for visualisations..

---

### Post by cbsim on 2008-11-10
> **trappy said:**
> still no amd64 deb file that works? :(

[attach]92040[/attach]

---

### Post by Hitchhiker427 on 2008-11-28
Can someone please post a newer .deb?  I installed the one posted previously, and it works, however, Synaptic keeps trying to upgrade my libs to 1.2.0-1 rather than 1.2, which breaks the projectm-pulse package.  I've tried numerous times to compile the svn, but I simply can't get it to build.  Thanks.

---

### Post by skram on 2008-11-28
> **hitchhiker427 said:**
> can someone please post a newer .deb? 

REV 1199 with following options:
 > use_cg                           on
 use_devil                        off
 use_fbo                          on
 use_ftgl                         on
 use_gles1                        off
 use_native_glew                  off
 use_openmp                       on

---

### Post by Hitchhiker427 on 2008-11-28
> **skram said:**
> REV 1199 with following options:
Oh, I'm sorry.  Thanks a lot for posting that, but I need a 32-bit version.  THanks again.

EDIT:  I did some searching, and finally got it to compile (rev. 1199).

---

### Post by ratdog on 2008-12-30
My sound would not work at all when I switched to pulseaudio from alsa in Hardy 64.  I retraced my steps and switched back to alsa to fix the sound, but still would love to get projectm working.  

What can I do to get projectm reacting to my computers line in input without using pulseaudio??

---

### Post by tjwhaynes on 2009-01-27
> **Rangua said:**
> hi, i've tried to install projectm from synaptic, but after it installs the command isn't available... i've tried looking for the program but it seems it didn't got installed.. i've also tried doing the svn thing, but i get an error saying (on make):

You are hitting the same thing I hit on check out from SVN.
 
/home/toby/progs/svn/projectM-Trunk/src/projectM-test/getConfigFilename.cpp:31:26: warning: character constant too long for its type

I'm no CMake expert, but I'm a hardened C hacker and this has an easy (if crappy) fix.

PROJECTM_PREFIX should be set to "/usr" (assuming you set this when you did ccmake .). For some reason, CMake has messed this up.

The HACK: In each affected .cpp file, just add the following lines:

#undef PROJECTM_PREFIX
#define PROJECTM_PREFIX "/usr"

and compile. If someone can pick apart the CMake stuff and provide a proper fix, I'd be interested. Until then, I have a working ProjectM install on my Intrepid AMD64 box.

Cheers,
Toby Haynes

---

### Post by swornbrother on 2009-01-29
I've been reading that people have had trouble running Compiz while using ProjectM.  Running both was working fine for me on Jaunty Alpha 3, until I ran some updates yesterday, and now it ProjectM runs so slow it's unusable :( (that's what I get for running alpha).  It will still work under metacity though...  Has anyone else experienced this?

---

### Post by peddy on 2009-01-29
> **swornbrother said:**
> I've been reading that people have had trouble running Compiz while using ProjectM.  Running both was working fine for me on Jaunty Alpha 3, until I ran some updates yesterday, and now it ProjectM runs so slow it's unusable :( (that's what I get for running alpha).  It will still work under metacity though...  Has anyone else experienced this?

Fine for me with Jaunty and Compiz.

---

### Post by christopinka on 2009-02-20
I'm having problem running make with below:

user@noctifer:~/projectm/projectM-Trunk/src$ make && sudo make install[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o
c++: no input files
/bin/sh: -fPIC: not found
make[2]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o] Error 127
make[1]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/all] Error 2
make: *** [all] Error 2
 
Any ideas?  It seems I don't have -P option for bin/sh Bourne shell?  Can I change compile to use Bash?

Thanks,

Chris

---

### Post by spacesearcher on 2009-03-09
SO I made a mistake and made the settings way to high quality now i cannot open project m is there any way i can change the settings for the quality with out opening project m? or some how reinstalling it? i tried reinstalling it but somehow the settings stuck.

---

### Post by skram on 2009-03-09
You can reset the settings, by deleting the config file.

```
rm ~/.projectM/config.inp

```

---

### Post by Roanoke on 2009-03-09
Which package should I download from [http://sourceforge.net/project/showfiles.php?group_id=104201](http://sourceforge.net/project/showfiles.php?group_id=104201) if I don't want SVN?

---

### Post by Chillawowa on 2009-03-10
When starting projectM from amarok a black window appears and then disappears.
When running projectM-pulseaudio, there is no command found, but projectM-test shows that there is an error with:

dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1400 x 1050
configFile: /home/moritz/.projectM/config.inp
*** glibc detected *** projectM-test: double free or corruption (out): 0x084129e0 ***

and then a further error message from backtrace.
Is there anyway to fix this?

---

### Post by sammydee on 2009-03-12
Projectm from sv has been broken for ages. Next time a proper release is made I'll write a guide up here on how to install it, until then you're best off sticking with one of the older releases.

Sam

---

### Post by Roanoke on 2009-03-12
Yes, but which one should I download?

---

### Post by unchartedstarr on 2009-03-31
i installed, everything seemed to have worked, but when i try to run the program from the terminal i get this:

starr@yggdrasil:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Cannot open file ':/images/icons/prjm16-transparent.svg', because: Unknown error
Cannot open file ':/images/icons/prjm16-transparent.svg', because: Unknown error
Segmentation fault

when i try to run it from the applications menu, nothing happens at all. i have no idea what to do here. help!

---

### Post by Killer Tofu on 2009-04-02
> **unchartedstarr said:**
> i installed, everything seemed to have worked, but when i try to run the program from the terminal i get this:

starr@yggdrasil:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Cannot open file ':/images/icons/prjm16-transparent.svg', because: Unknown error
Cannot open file ':/images/icons/prjm16-transparent.svg', because: Unknown error
Segmentation fault

when i try to run it from the applications menu, nothing happens at all. i have no idea what to do here. help!

Yeah I installed projectM recently and have had the same problems except a window actually pops up but then is instantly closed. so yeah sorry i cant be of any help but i hope someone can. helping you, helps me

---

### Post by Psychopump on 2009-04-16
> **Killer Tofu said:**
> Yeah I installed projectM recently and have had the same problems except a window actually pops up but then is instantly closed. so yeah sorry i cant be of any help but i hope someone can. helping you, helps me


I have the EXACT same issue.
Anyone able to help!?

---

### Post by unchartedstarr on 2009-04-18
a window sort of pops up for me, too, actually... i don't actually see a window but i do see it in the taskbar for a second before it closes. so i think we really are having the EXACT same problem.

---

### Post by Psychopump on 2009-04-21
With so many of us experiencing the same issue, maybe someone will pick this up.

BTW: Milkrop/ProjectM ran fine on my machine when I was running XP.

---

### Post by delysid on 2009-04-29
I'm having the same problem as well.
Didn't start happening til i installed 1.2.0 though.
1.0 worked fine

I really want to see the pixel shaders in action :(

---

### Post by Malart on 2009-05-17
i get this when i attempt to continue after configuring ccmake with Release and /usr/

 CMake Error: Error in cmake code at
 /home/malart/projectm/projectM-Trunk/src/libprojectM/CMakeLists.txt:5:
 Unknown CMake command "cmake_policy".


really not sure whats going on, I'm new to Linux but excited to learn

---

### Post by Malart on 2009-05-21
im not sure if im not providing enough info or not... if not can someone tell me what to offer up? :D

---

### Post by jamfreak on 2009-05-24
Hi, I'm fairly new to Ubuntu and running Ubuntu 8.10. I installed ProjectM-Pulseradio the way it's described in the first post.
Whenever I try to open  ProjectM with 'Applications>SoundAnd Video>ProjectM-Pulseradio' it tries to open a window and immedeately closes it. I tried to run it from Terminal and get the following message:

 volker@volker:~$ projectM-pulseaudio
dir:/usr/./share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/volker/.projectM/config.inp
No Textures Loaded from /usr/./share/projectM/textures
set pipeline broken FIX ME
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[projectM] warning: no valid files found in preset directory ""
call factory clear here?
call factory clear here?
Segmentation fault
volker@volker:~$ 

Can anyone help? It seems I have to change my default directory to a different directory...how do I do that?
Any help is very much appreciated!

---

### Post by jamfreak on 2009-05-25
OK, so I re-installed it with the right directory and now get this message after trying to start in Terminal:

volker@volker:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/volker/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
set pipeline broken FIX ME
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[projectM] warning: no valid files found in preset directory ""
call factory clear here?
call factory clear here?
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault
volker@volker:~$ 


Anyone has any help?

---

### Post by redmistpete on 2009-05-25
Followed the tutorial step-by-step. Didn't work; it fell at the last hurdle - it says: 

cMake Error: Error in make code at
/home/peter/projectm/projectM-Trunk/src/libporjectM/cMakeLists.txt:5:
Unknown CMake command "cmake_policy".

Any ideas as to what wet wrong please? Cheers.

---

### Post by Malart on 2009-05-25
Thank god im not the only one lol... was starting to feel kinda lonely

---

### Post by aYs-Halo on 2009-05-28
Same problem here.

(cmake_policy..)

---

### Post by Mr. Rogers on 2009-05-29
Hi,

the building proces works for me. But if I use the QT-Frontend, I just have a black screen. The menu works and I see all the .milks in the list. But no visualization.

If I install the debs postet some side before, the QT-Frontend seems to work. But the visualization is just crap. It is allways the same. If i try to change the .milk in the menu, the visualization doesnt chance. Just the line changes from red to blue or from circle to line. Circle is always centered in the lower left corner. This is wired behavior.

Does anyone know why the behavior is so strange? At startup it (projectM-audiopulse) alway shows the line, that it had not found any valid presets in "".



projectM-test always works fine. Perfect, no gtk, no qt! I just have no menu there to see some information, but I read somewhere, that it was disabled. Maybe I find out how I can enable it in sourcecode. Maybe someone can help me here, or point me in the right direction.

---

### Post by fedevit on 2009-05-31
> **Mr. Rogers said:**
> Hi,

the building proces works for me. But if I use the QT-Frontend, I just have a black screen. The menu works and I see all the .milks in the list. But no visualization.

If I install the debs postet some side before, the QT-Frontend seems to work. But the visualization is just crap. It is allways the same. If i try to change the .milk in the menu, the visualization doesnt chance. Just the line changes from red to blue or from circle to line. Circle is always centered in the lower left corner. This is wired behavior.

Does anyone know why the behavior is so strange? At startup it (projectM-audiopulse) alway shows the line, that it had not found any valid presets in "".



projectM-test always works fine. Perfect, no gtk, no qt! I just have no menu there to see some information, but I read somewhere, that it was disabled. Maybe I find out how I can enable it in sourcecode. Maybe someone can help me here, or point me in the right direction.



I have the very same problem here. ubuntu 9.04 32bit.
That's a shame, I was really thrilled and hoping to see this in action, anyone can help? thanks in advance

---

### Post by fedevit on 2009-05-31
I get this working by running *projectM-test* but, as said Mr.Roger, it has no menu.
Any help?

---

### Post by krul on 2009-05-31
Followed tutorial, and it is working great!!

Any idea how to get this to work as wall paper or screensaver?

---

### Post by aYs-Halo on 2009-06-01
> **redmistpete said:**
> Followed the tutorial step-by-step. Didn't work; it fell at the last hurdle - it says: 

cMake Error: Error in make code at
/home/peter/projectm/projectM-Trunk/src/libporjectM/cMakeLists.txt:5:
Unknown CMake command "cmake_policy".

Any ideas as to what wet wrong please? Cheers.

Fixed this by upgrading from 8.04 to 9.04.

I have then run into the "segmentation fault" problem described here:
[http://ubuntuforums.org/showthread.php?t=1125440](http://ubuntuforums.org/showthread.php?t=1125440)

the fix at the very end > **Grindolin said:**
> 
I tried to change the options in the ccmake configuration to get projectM work. 
When I switched the use of frame-buffer objects off (set USE_FBO to "off") it  finally worked..

worked for me there.

I then ran into the blackscreen problem here: [http://sourceforge.net/tracker/?func=detail&aid=2050179&group_id=104201&atid=637260](http://sourceforge.net/tracker/?func=detail&aid=2050179&group_id=104201&atid=637260)
Using the workaround described there worked.


I'm using Ubuntu 9.04 on a Nvidia Geforce mx440, german (non-english).
Since all this took me a while I'll post this here.. hope it helps someone :)


Kind Regards :)

---

### Post by Mr. Rogers on 2009-06-01
Thanks for the tip. After changing the local it realy works. Now the wired behaviour also makes sense, if dots are changed with commas...

Only problem I have now is, how can I set LC_NUMERIC=C in the .desktop file? So that I can start it without the terminal.

---

### Post by fedevit on 2009-06-01
Thanks a lot!

It works for me too. The only thing I needed to do was to launch the program by typing:

LC_NUMERIC=C projectM-pulseaudio


instead of

projectM-pulseaudio



cheers ;);)

---

### Post by Mr. Rogers on 2009-06-01
To fix the localization problem (switching , and . when reading presetfile) do the following:

Open file projectM/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp. And go to line 91:

After the line "QApplication app ( argc, argv );" you should add a new line with "setlocale(LC_NUMERIC, "C"); // Fix".

The code should now look like that:
```
int main ( int argc, char*argv[] )
{
    int i;
    char projectM_data[1024];

    QApplication app ( argc, argv );
    
    setlocale(LC_NUMERIC, "C"); // Fix

    std::string config_file;
    config_file = read_config();

    
    QMutex audioMutex;
```Now you can recompile and start the application normaly.

Greetings Mr. Roger

---

### Post by aYs-Halo on 2009-06-02
Anyone know how i would start projectM in fullscreen mode?

changing the "fullscreen =" line to true (in the config.inp) doesnt work.

Nevermind.. I didnt think of the possibility that there is a checkmark in the gui for this. Way too easy :D

---

### Post by fedevit on 2009-06-02
> **aYs-Halo said:**
> Anyone know how i would start projectM in fullscreen mode?


open ProjectM

type

m

then click "settings"
and tick "Fullscreen on startup"

restart projectM and you're done!

---

### Post by Malart on 2009-06-02
> **aYs-Halo said:**
> Fixed this by upgrading from 8.04 to 9.04.

I have then run into the "segmentation fault" problem described here:
[http://ubuntuforums.org/showthread.php?t=1125440](http://ubuntuforums.org/showthread.php?t=1125440)

the fix at the very end 

worked for me there.

I then ran into the blackscreen problem here: [http://sourceforge.net/tracker/?func=detail&aid=2050179&group_id=104201&atid=637260](http://sourceforge.net/tracker/?func=detail&aid=2050179&group_id=104201&atid=637260)
Using the workaround described there worked.


I'm using Ubuntu 9.04 on a Nvidia Geforce mx440, german (non-english).
Since all this took me a while I'll post this here.. hope it helps someone :)


Kind Regards :)


You mean in order to get it to work on Hardy.... I have to use Intrepid?

rofl

---

### Post by aYs-Halo on 2009-06-03
I don't know, I'm sure there's another way.. but that's what worked for me.

---

### Post by unimatrix on 2009-06-05
This is total ********. ProjectM sucks. It works like CRAP. It uses all of my CPU even in windowed mode, and works at like 10FPS in fullscreen.

MilkDrop via Winamp on Windows XP however runs at 35% CPU when windowed and 50% CPU in fullscreen - PERFECTLY (read: same as monitor's refreshrate).

I'm running a nVidia 6600, so don't tell me it's "not good enough". The state of video acceleration in Linux is really just sad.

---

### Post by Mr. Rogers on 2009-06-06
Do you have your drivers installed correctly?

For me it runs with the same values you posted for winamp. But Values change if preset changes. If your graphicsdriver does not call a graphicsfunction, it could emulate it ,so you get the full opengl range, even your graphicscard does not have the special feature. That means, that the function will not hardware accelerated, but calculated on cpu.

But you mentioned that you have different values in fullscreen or window mode. This makes not much sense, cause the computated image is the same size. only the mapping to the window is an other size. Do you have framebuffer disabled in your version of projectm? Maybe it is because of this. Or what settings do you have in projectm? Maybe the calculated image is to big.

---

### Post by unimatrix on 2009-06-06
> Do you have your drivers installed correctly?
Yes. Unless Ubuntu installed it wrong, they are set up correctly.

> For me it runs with the same values you posted for winamp. But Values change if preset changes.
That's true. Most of the presets run fairly well, but with some you can see it's not smooth.

> 
If your graphicsdriver does not call a graphicsfunction, it could emulate it ,so you get the full opengl range, even your graphicscard does not have the special feature. That means, that the function will not hardware accelerated, but calculated on cpu.

My graphic driver works fine.

> 
But you mentioned that you have different values in fullscreen or window mode. This makes not much sense, cause the computated image is the same size. only the mapping to the window is an other size.

Well, it's generally worse in fullscreen.

> 
Do you have framebuffer disabled in your version of projectm? Maybe it is because of this.
You mean USE_FBO ?
It's enabled.

> 
Or what settings do you have in projectm? Maybe the calculated image is to big.
I have that image size thing set to 1024.


I don't understand why it has to use all of my CPU. This is GUP's work for ***** sake.

---

### Post by Mr. Rogers on 2009-06-06
Ok, seems you have the same settings as I. So I could not help you.

> I don't understand why it has to use all of my CPU. This is GUP's work for ***** sake.     It is audiovisualization. So the CPU has to compute the values out of the audiostream. The calculated values are floatingpoint ones. So more time is needed to compute these. Other point I mentioned above. Software OpenGL instead of Hardware OpenGL.

Greetings Mr. Rogers

---

### Post by unimatrix on 2009-06-06
> **Mr. Rogers said:**
> Ok, seems you have the same settings as I. So I could not help you.

It is audiovisualization. So the CPU has to compute the values out of the audiostream. The calculated values are floatingpoint ones. So more time is needed to compute these. Other point I mentioned above. Software OpenGL instead of Hardware OpenGL.

Greetings Mr. Rogers

Doesn't happen on Windows.
Try again.

---

### Post by sammydee on 2009-06-06
> **unimatrix said:**
> Doesn't happen on Windows.
Try again.

It's free software, if you don't like it, don't use it.

If you want to file a bug, better tell the projectm developers rather than on here where nobody is actually involved with the project.

---

### Post by unimatrix on 2009-06-06
That's the thing, I don't think it's a bug. I probably did something wrong when I installed it.
Now, how come I didn't need to compile anything on windoze and everything worked best out of the box? There goes the "installing stuff on linux is easy" argument again...

EDIT: Sorry, I've had a bad day and linux is pissing me off. (PS: I can't -not- use it, don't have the money to buy expensive windoze)

---

### Post by dosephjowney on 2009-06-07
i am getting this when i try to press c in cmake any ideas? thanks

 CMake Error: Error in cmake code at
 /home/joe/projectm/projectM-Trunk/src/libprojectM/CMakeLists.txt:5:
 Unknown CMake command "cmake_policy".

---

### Post by aYs-Halo on 2009-06-08
Linux upgrade ;)
-> [http://ubuntuforums.org/showpost.php?p=7380743&postcount=223](http://ubuntuforums.org/showpost.php?p=7380743&postcount=223)

I googled about 3 hours on this to get a more simple solution, until I finally gave up

---

### Post by dosephjowney on 2009-06-09
thank you

---

### Post by Mikolaj.Q on 2009-06-16
Hi,
I can not compile projectM on ubuntu Karmic. I've installed all suggested dependencies (i think). So that's what I get after I run 'make':
```

vampire@vampire-desktop:/media/sda5/work_folder/projectM-Trunk/src$ make
Scanning dependencies of target NativePresetFactory                     
[  1%] Building CXX object libprojectM/NativePresetFactory/CMakeFiles/NativePresetFactory.dir/NativePresetFactory.o  
Linking CXX static library libNativePresetFactory.a                                                                  
[  1%] Built target NativePresetFactory                                                                              
Scanning dependencies of target Renderer                                                                             
[  2%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o                                        
[  3%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/MilkdropWaveform.o                           
[  4%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerPixelMesh.o                               
[  5%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Pipeline.o                                   
[  6%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o                                   
[  7%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/ShaderEngine.o                               
[  8%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/UserTexture.o                                
[  9%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Waveform.o                                   
[  9%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Filters.o                                    
[ 10%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerlinNoise.o                                
[ 11%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PipelineContext.o                            
[ 12%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderable.o                                 
[ 13%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/BeatDetect.o                                 
[ 14%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Shader.o                                     
[ 15%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/TextureManager.o                             
[ 16%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/VideoEcho.o                                  
[ 17%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/RenderItemDistanceMetric.o                   
[ 18%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/RenderItemMatcher.o                          
[ 18%] Building C object libprojectM/Renderer/CMakeFiles/Renderer.dir/SOIL/image_DXT.o                               
[ 19%] Building C object libprojectM/Renderer/CMakeFiles/Renderer.dir/SOIL/image_helper.o                            
[ 20%] Building C object libprojectM/Renderer/CMakeFiles/Renderer.dir/SOIL/SOIL.o                                    
[ 21%] Building C object libprojectM/Renderer/CMakeFiles/Renderer.dir/SOIL/stb_image_aug.o                           
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/Renderer/SOIL/stb_image_aug.c: In function ‘getn’:            
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/Renderer/SOIL/stb_image_aug.c:446: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result                                                           
Linking CXX static library libRenderer.a                                                                             
[ 21%] Built target Renderer                                                                                         
Scanning dependencies of target MilkdropPresetFactory                                                                
[ 22%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/BuiltinFuncs.o     
[ 23%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/Func.o             
[ 24%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/MilkdropPreset.o   
[ 25%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/PresetFrameIO.o    
[ 26%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/CustomShape.o      
[ 26%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/Eval.o             
[ 27%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/MilkdropPresetFactory.o                                                                                                                 
[ 28%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/PerPixelEqn.o      
[ 29%] Building CXX object libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/BuiltinParams.o    
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp: In member function ‘int BuiltinParams::load_builtin_param_float(const std::string&, void*, void*, short int, float, float, float, const std::string&)’:                                                                                                        
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:47: error: ‘printf’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:48: error: ‘stdout’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:48: error: ‘fflush’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:61: error: ‘printf’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:62: error: ‘stdout’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:62: error: ‘fflush’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:75: error: ‘printf’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:76: error: ‘stdout’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:76: error: ‘fflush’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:89: error: ‘printf’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:90: error: ‘stdout’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:90: error: ‘fflush’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:96: error: ‘printf’ was not declared in this scope                                                                                         
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp: In member function ‘int BuiltinParams::init_builtin_param_db(const PresetInputs&, PresetOutputs&)’:                                       
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:267: error: ‘printf’ was not declared in this scope                                                                                        
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:268: error: ‘stdout’ was not declared in this scope                                                                                        
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:268: error: ‘fflush’ was not declared in this scope                                                                                        
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:274: error: ‘printf’ was not declared in this scope                                                                                        
/media/sda5/work_folder/projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.cpp:278: error: ‘printf’ was not declared in this scope                                                                                        
make[2]: *** [libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/BuiltinParams.o] Error 1        
make[1]: *** [libprojectM/MilkdropPresetFactory/CMakeFiles/MilkdropPresetFactory.dir/all] Error 2                    
make: *** [all] Error 2               
```

please help

---

### Post by MaxIBoy on 2009-07-04
Mikolaj, I had the same problem as you! Fortunately, there is a workaround:
Go to the file projectM-Trunk/src/libprojectM/MilkdropPresetFactory/BuiltinParams.hpp and find this section:
```
#include <string>
#include "PresetFrameIO.hpp"
#include "Param.hpp"
#include <map>
```
Modify it so it looks like this:
```
#include <string>
#include "PresetFrameIO.hpp"
#include "Param.hpp"
#include <map>
#include <cstdio>
```

Then try it again. If you get the same error on another file, that file will be a .cpp file. Go to the corresponding .hpp file and add that same line. 


Other programs have been getting similar errors, and apparently it's got something to do with newer versions of GCC.

---

### Post by Mikolaj.Q on 2009-07-05
Thank You a lot, works fine for me!
I've just edit BuiltinParams.hpp but also getConfigFilename.cpp file in projectM-test folder the way you said. Works perfect.
Thanks for useful advice.

---

### Post by Floyd1973 on 2009-07-08
Hi all,
 I'm trying to intall this grate program, but when I use the command:

```
ccmake .
```

in the src directory and press [c] to compile, i recive this message:

```
 CMake Error: Error in cmake code at
 /home/guybrush/Musica/ProjectM/ProjectM-Trunk/src/libprojectM/CMakeLists.txt:5
 :
 Unknown CMake command "cmake_policy".
```

Hi can I do? I have no idea 8-/

---

### Post by Cresho on 2009-08-09
i get the same error.  been trying on hardy 64bit.  i had no issues last year on hardy 32bit.

---

### Post by shipwreck2 on 2009-08-18
Hey guys,

spent hours on installing this. The Howto works fine, thanks for that, but if I'm trying to "make" it, I get the following bunch of errors:

```
konne@Konne:~/projectm/projectM-Trunk/src$ make install
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o
In Datei, eingefügt von /usr/include/FTGL/ftgl.h:32,
                 von /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 von /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/ft2build.h:56:38: Fehler: freetype/config/ftheader.h: No such file or directory
In Datei, eingefügt von /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 von /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/ftgl.h:33:10: Fehler: #include erwartet "DATEINAME" oder <DATEINAME>
/usr/include/FTGL/ftgl.h:34:10: Fehler: #include erwartet "DATEINAME" oder <DATEINAME>
/usr/include/FTGL/ftgl.h:35:10: Fehler: #include erwartet "DATEINAME" oder <DATEINAME>
In file included from /usr/include/FTGL/ftgl.h:110,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPoint.h:75: Fehler: expected »,« or »...« before »&« token
/usr/include/FTGL/FTPoint.h: In constructor »FTPoint::FTPoint(int)«:
/usr/include/FTGL/FTPoint.h:77: Fehler: »ft_vector« wurde in diesem Gültigkeitsbereich nicht definiert
In file included from /usr/include/FTGL/ftgl.h:111,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBBox.h: At global scope:
/usr/include/FTGL/FTBBox.h:75: Fehler: expected `)' before »glyph«
In file included from /usr/include/FTGL/ftgl.h:114,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGlyph.h:58: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTGlyph.h:112: Fehler: »FT_Error« bezeichnet keinen Typ
/usr/include/FTGL/FTGlyph.h:196: Fehler: »FT_Error« bezeichnet keinen Typ
In file included from /usr/include/FTGL/ftgl.h:115,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBitmapGlyph.h:50: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTBitmapGlyph.h:77: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
In file included from /usr/include/FTGL/ftgl.h:116,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferGlyph.h:49: Fehler: expected `)' before »glyph«
In file included from /usr/include/FTGL/ftgl.h:117,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTExtrdGlyph.h:59: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTExtrdGlyph.h:97: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
/usr/include/FTGL/FTExtrdGlyph.h:97: Fehler: expected primary-expression before »float«
/usr/include/FTGL/FTExtrdGlyph.h:98: Fehler: expected primary-expression before »float«
/usr/include/FTGL/FTExtrdGlyph.h:98: Fehler: expected primary-expression before »float«
/usr/include/FTGL/FTExtrdGlyph.h:99: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTExtrdGlyph.h:99: Fehler: initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
In file included from /usr/include/FTGL/ftgl.h:118,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTOutlineGlyph.h:56: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTOutlineGlyph.h:88: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
/usr/include/FTGL/FTOutlineGlyph.h:88: Fehler: expected primary-expression before »float«
/usr/include/FTGL/FTOutlineGlyph.h:89: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTOutlineGlyph.h:89: Fehler: initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
In file included from /usr/include/FTGL/ftgl.h:119,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPixmapGlyph.h:50: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTPixmapGlyph.h:77: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
In file included from /usr/include/FTGL/ftgl.h:120,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPolyGlyph.h:57: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTPolyGlyph.h:92: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
/usr/include/FTGL/FTPolyGlyph.h:92: Fehler: expected primary-expression before »float«
/usr/include/FTGL/FTPolyGlyph.h:93: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTPolyGlyph.h:93: Fehler: initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
In file included from /usr/include/FTGL/ftgl.h:121,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTTextureGlyph.h:59: Fehler: expected `)' before »glyph«
/usr/include/FTGL/FTTextureGlyph.h:92: Fehler: »FT_GlyphSlot« wurde in diesem Gültigkeitsbereich nicht definiert
/usr/include/FTGL/FTTextureGlyph.h:92: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTTextureGlyph.h:93: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTTextureGlyph.h:93: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTTextureGlyph.h:94: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTTextureGlyph.h:94: Fehler: expected primary-expression before »int«
/usr/include/FTGL/FTTextureGlyph.h:94: Fehler: initializer Ausdrucksliste als zusammengesetzten Ausdruck behandelt
In file included from /usr/include/FTGL/ftgl.h:123,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTFont.h:128: Fehler: »FT_Int« wurde nicht deklariert
/usr/include/FTGL/FTFont.h:137: Fehler: »FT_Encoding« wurde nicht deklariert
/usr/include/FTGL/FTFont.h:151: Fehler: »FT_Encoding« als »virtuelles« field deklariert
/usr/include/FTGL/FTFont.h:151: Fehler: expected »;« before »*« token
/usr/include/FTGL/FTFont.h:363: Fehler: »FT_Error« bezeichnet keinen Typ
/usr/include/FTGL/FTFont.h:378: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTFont.h:378: Fehler: expected »;« before »(« token
/usr/include/FTGL/FTFont.h:411: Fehler: expected »,« or »...« before »(« token
/usr/include/FTGL/FTFont.h:451: Fehler: »FT_Encoding« wurde nicht deklariert
/usr/include/FTGL/FTFont.h:467: Fehler: expected constructor, destructor, or type conversion before »*« token
/usr/include/FTGL/FTFont.h:579: Fehler: »FT_Error« bezeichnet keinen Typ
In file included from /usr/include/FTGL/ftgl.h:124,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLBitmapFont.h:81: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLBitmapFont.h:81: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:125,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferFont.h:79: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTBufferFont.h:79: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:126,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLExtrdFont.h:82: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLExtrdFont.h:82: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:127,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLOutlineFont.h:81: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLOutlineFont.h:81: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:128,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPixmapFont.h:81: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLPixmapFont.h:81: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:129,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPolygonFont.h:81: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLPolygonFont.h:81: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:130,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLTextureFont.h:81: Fehler: »MakeGlyph« als »virtuelles« field deklariert
/usr/include/FTGL/FTGLTextureFont.h:81: Fehler: expected »;« before »(« token
In file included from /usr/include/FTGL/ftgl.h:132,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/konne/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTLayout.h:134: Fehler: »FT_Error« bezeichnet keinen Typ
/usr/include/FTGL/FTLayout.h:187: Fehler: »FT_Error« bezeichnet keinen Typ
make[2]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o] Fehler 1
make[1]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/all] Fehler 2
make: *** [all] Fehler 2

```There seems to be missing something quite elementary. Any suggestions?
Some of the code is german. If needed, I will post it again in complete English unless someone tells me how to change the output language.

Thanks.

---

### Post by Riozaku on 2009-08-23
Problem!!!!!!!!!!!!!


riozaku@ubuntu:~/projectm/projectM-Trunk/src$ make && sudo make install
Scanning dependencies of target NativePresetFactory
[  1%] Building CXX object libprojectM/NativePresetFactory/CMakeFiles/NativePresetFactory.dir/NativePresetFactory.o
Linking CXX static library libNativePresetFactory.a
[  1%] Built target NativePresetFactory
Scanning dependencies of target Renderer
[  2%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o
[  3%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/MilkdropWaveform.o
[  3%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerPixelMesh.o
[  4%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Pipeline.o
[  5%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o
In file included from /usr/include/FTGL/ftgl.h:32,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/ftgl.h:33:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/ftgl.h:34:10: error: #include expects "FILENAME" or <FILENAME>
/usr/include/FTGL/ftgl.h:35:10: error: #include expects "FILENAME" or <FILENAME>
In file included from /usr/include/FTGL/ftgl.h:110,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPoint.h:75: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/FTGL/FTPoint.h: In constructor ‘FTPoint::FTPoint(int)’:
/usr/include/FTGL/FTPoint.h:77: error: ‘ft_vector’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:111,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBBox.h: At global scope:
/usr/include/FTGL/FTBBox.h:75: error: expected `)' before ‘glyph’
In file included from /usr/include/FTGL/ftgl.h:114,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGlyph.h:58: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTGlyph.h:112: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTGlyph.h:196: error: ‘FT_Error’ does not name a type
In file included from /usr/include/FTGL/ftgl.h:115,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBitmapGlyph.h:50: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTBitmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:116,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferGlyph.h:49: error: expected `)' before ‘glyph’
In file included from /usr/include/FTGL/ftgl.h:117,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTExtrdGlyph.h:59: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTExtrdGlyph.h:97: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTExtrdGlyph.h:97: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:98: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTExtrdGlyph.h:99: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTExtrdGlyph.h:99: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:118,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTOutlineGlyph.h:56: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTOutlineGlyph.h:88: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTOutlineGlyph.h:88: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTOutlineGlyph.h:89: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTOutlineGlyph.h:89: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:119,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPixmapGlyph.h:50: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTPixmapGlyph.h:77: error: ‘FT_GlyphSlot’ was not declared in this scope
In file included from /usr/include/FTGL/ftgl.h:120,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTPolyGlyph.h:57: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTPolyGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTPolyGlyph.h:92: error: expected primary-expression before ‘float’
/usr/include/FTGL/FTPolyGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTPolyGlyph.h:93: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:121,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTTextureGlyph.h:59: error: expected `)' before ‘glyph’
/usr/include/FTGL/FTTextureGlyph.h:92: error: ‘FT_GlyphSlot’ was not declared in this scope
/usr/include/FTGL/FTTextureGlyph.h:92: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:93: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: expected primary-expression before ‘int’
/usr/include/FTGL/FTTextureGlyph.h:94: error: initializer expression list treated as compound expression
In file included from /usr/include/FTGL/ftgl.h:123,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTFont.h:128: error: ‘FT_Int’ has not been declared
/usr/include/FTGL/FTFont.h:137: error: ‘FT_Encoding’ has not been declared
/usr/include/FTGL/FTFont.h:151: error: ‘FT_Encoding’ declared as a ‘virtual’ field
/usr/include/FTGL/FTFont.h:151: error: expected ‘;’ before ‘*’ token
/usr/include/FTGL/FTFont.h:363: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTFont.h:378: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTFont.h:378: error: expected ‘;’ before ‘(’ token
/usr/include/FTGL/FTFont.h:411: error: expected ‘,’ or ‘...’ before ‘(’ token
/usr/include/FTGL/FTFont.h:451: error: ‘FT_Encoding’ has not been declared
/usr/include/FTGL/FTFont.h:467: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/FTGL/FTFont.h:579: error: ‘FT_Error’ does not name a type
In file included from /usr/include/FTGL/ftgl.h:124,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLBitmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLBitmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:125,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTBufferFont.h:79: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTBufferFont.h:79: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:126,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLExtrdFont.h:82: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLExtrdFont.h:82: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:127,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLOutlineFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLOutlineFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:128,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPixmapFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLPixmapFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:129,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLPolygonFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLPolygonFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:130,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTGLTextureFont.h:81: error: ‘MakeGlyph’ declared as a ‘virtual’ field
/usr/include/FTGL/FTGLTextureFont.h:81: error: expected ‘;’ before ‘(’ token
In file included from /usr/include/FTGL/ftgl.h:132,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:27,
                 from /home/riozaku/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/usr/include/FTGL/FTLayout.h:134: error: ‘FT_Error’ does not name a type
/usr/include/FTGL/FTLayout.h:187: error: ‘FT_Error’ does not name a type
make[2]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o] Error 1
make[1]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/all] Error 2
make: *** [all] Error 2




This is the second time I have tried to install projectM. PLEASE HELP

---

### Post by eltoozero on 2009-08-24
I'm happy to report successful build and operation of projectM-pulseaudio in Karmic Koala alpha 4.

There are a couple of requisite fixes which have been discussed previously in this thread, but here are my working instructions:

Compiling projectM-1.2.0 Steps:
1. install prerequisites for projectM:
&#8226; libglew1.5 libglew1.5-dev ftgl-dev libpulse-dev cmake libvisual-0.4-dev libsdl-dev libqt4-dev build-essential cmake-curses-gui

2. unpack the source distribution and run the following commands to compile each package
&#8226; ccmake .
&#8226; (Note: There's a "space" then "dot" after ccmake.)
&#8226; Press "c" to enter the cmake configure screen.
&#8226; Change the "CMAKE_INSTALL_PREFIX" value from "/usr/local" to "/usr".
&#8728; Change the "CMAKE_BUILD_TYPE" to "Release".
&#8226; Press "g" to generate your changes, which will create your makefile needed for compiling.
&#8226; Press "q" after that has been generated.

3. order of install
&#8226; libprojectM, libprojectM-qt, projectM-pulseaudio, projectM-libvisual

4. compile and install
&#8226; make
&#8226; sudo make install

4a. fixing compile errors
* Go to the file BuiltinParams.hpp and find this section:
#include <string>
#include "PresetFrameIO.hpp"
#include "Param.hpp"
#include <map>

Modify it so it looks like this:
#include <string>
#include "PresetFrameIO.hpp"
#include "Param.hpp"
#include <map>
#include <cstdio>

Then try it again. If you get the same error on another file, that file will be a .cpp file. Go to the corresponding .hpp file and add that same line.

4b. Fix Renderer.hpp and fix name of ftgl.h
&#8226; open Renderer.hpp located in the libprojectM-1.2.0 directory with a text editor and fix Line 23 and Line 27 so they read:
Line 23- #include <ftgl.h>
Line 27- #include <FTGL/ftgl.h>
save your changes
(Renderer.hpp attempts to load FTGL.h C++ header file, but in Ubuntu this file is named ftgl.h)


Bibliography:
&#8226; ProjectM Homepage on Sourceforge.net - [https://sourceforge.net/projects/projectm/](https://sourceforge.net/projects/projectm/)
&#8226; Ubuntu Howto: Install projectM Audio Visualizer - [http://www.ubuntugeek.com/ubuntu-howto-install-projectm-audio-visualizer.html](http://www.ubuntugeek.com/ubuntu-howto-install-projectm-audio-visualizer.html)
&#8226; Milkymist Embedded projectM - [http://www.milkymist.org/](http://www.milkymist.org/)
&#8226; Fixing Karmic compile errors - [http://ubuntuforums.org/showthread.php?t=749793&page=25](http://ubuntuforums.org/showthread.php?t=749793&page=25)
&#8226; HOWTO Compile projectM-1.2.0 (ftgl.h and performance settings) - [http://ubuntuforums.org/showthread.php?t=1166503](http://ubuntuforums.org/showthread.php?t=1166503)

---

### Post by skram on 2009-09-05
> **Riozaku said:**
> 

/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory


The problem is that ftheader.h is not in frretype/config , but in freetype2/config.

There are 2 solutions for this:

1. Compile without FTGL: type 'ccmake .' in the src dir, then press c to configure and change USE_FTGL to off. Now press 'c' to configure and 'g' to generate Makefiles. After that you can compile with make.

2. type 'ccmake .' in the src dir, then press c to configure. Now press 't' to toggle to advanced mode. Now you havte to change 3 lines:

```

...
 CMAKE_BUILD_TYPE                 release
...
 CMAKE_CXX_FLAGS_RELEASE          -O3 -DNDEBUG -I/usr/include/freetype2
...
 CMAKE_C_FLAGS_RELEASE            -O3 -DNDEBUG -I/usr/include/freetype2

```
After changing press 'c' to configure and 'g' to generate Makefiles. After that you can compile with make.

Cya(o)
...   Rainer

---

### Post by Le Gluon du Net on 2009-09-22
Hello Sammydee, I would like to thank you for this tutorial, what a gain of time and it is always up to date with the last svn from today.

Last things: projectM is a must to have, it rocks!!!
It's a pity I can not use it on Gnome with VLC TOTEM RYTHMBOX or like a wallpaper with compiz \\:D/
Have fun

---

### Post by durand on 2009-09-22
> **Le Gluon du Net said:**
> Hello Sammydee, I would like to thank you for this tutorial, what a gain of time and it is always up to date with the last svn from today.

Last things: projectM is a must to have, it rocks!!!
It's a pity I can not use it on Gnome with VLC TOTEM RYTHMBOX or like a wallpaper with compiz \\:D/
Have fun

You can use it with vlc, totem, rhythmbox. Thats kinda the whole point of pulseaudio support, that you can use it with any application that works with pulseaudio...which is a lot.

---

### Post by Le Gluon du Net on 2009-09-23
Yeah, that's a great evolution of projectM. But it will be great too if gnome developpers integrate it in gnome multimedia apps. Perrhap's they don't want because the projectM code is not 100% gpl?

---

### Post by durand on 2009-09-23
Oh, you mean the visualisations... I thought I saw a configure option to compile a module for the gstreamer visuals. If you can get that to work, you should be able to use projectm in totem and rhythmbox.

---

### Post by Ardit on 2009-09-24
How do I uninstall projectM from ubuntu? I installed it it following the directions on the first page telling me to use cmake now I want to know how to completely remove it.

---

### Post by NoTownKasper on 2009-09-28
My apologies if this isn't the appropriate place to post this, but it -seemed- appropriate.

I'm not using Hardy, I'm using Intrepid, and projectM is available via Synaptic...or at least it seems to be. So I installed all the available packages with the exception of the dev package (libprojectm2, libprojectm-data and libvisual-projectm)...so ok, now what? There's no listing for projectm under my sound-video menu, nor do any of the terminal commands I've found for running it seem to do anything. Obviously I missed a step somewhere...anyone mind telling me what it is? Cuz if I have to compile my own version of it...I'm afraid I can live without...

Perhaps one of the only 2 linux drawbacks that keep me in Windoze...piss-poor instalation procedures (for some programs) and the complete lack of -real- gaming support. (Which is more a commercial problem than a linux problem anyway.)

---

### Post by Le Gluon du Net on 2009-09-29
> **Ardit said:**
> How do I uninstall projectM from ubuntu? I installed it it following the directions on the first page telling me to use cmake now I want to know how to completely remove it.

 did you try "make uninstall" from the folder source?

---

### Post by Le Gluon du Net on 2009-09-29
> **NoTownKasper said:**
> My apologies if this isn't the appropriate place to post this, but it -seemed- appropriate.

I'm not using Hardy, I'm using Intrepid, and projectM is available via Synaptic...or at least it seems to be. So I installed all the available packages with the exception of the dev package (libprojectm2, libprojectm-data and libvisual-projectm)...so ok, now what? There's no listing for projectm under my sound-video menu, nor do any of the terminal commands I've found for running it seem to do anything. Obviously I missed a step somewhere...anyone mind telling me what it is? Cuz if I have to compile my own version of it...I'm afraid I can live without...

Perhaps one of the only 2 linux drawbacks that keep me in Windoze...piss-poor instalation procedures (for some programs) and the complete lack of -real- gaming support. (Which is more a commercial problem than a linux problem anyway.)

 The projectM version from ubuntu packages is too old. that's why it is better to install it from svn.

---

### Post by FokkerCharlie on 2009-10-21
Cool!

Been looking for something like this for ages- now I have visualisations for songbird, and my life is complete.

Thanks for the perfect instructions!

Charlie

---

### Post by preto on 2009-11-01
I'm running Ubuntu 9.10.

I'm done with the howto so far.

I run:
```

cmake .
make
sudo make install

```there where no errors.

When I now start "projectM-pulseaudio" in a terminal. I get this error:
```

projectM-pulseaudio: error while loading shared libraries: libprojectM-qt.so.1: cannot open shared object file: No such file or directory

```

---

### Post by mocha on 2009-11-01
> **preto said:**
> ```

projectM-pulseaudio: error while loading shared libraries: libprojectM-qt.so.1: cannot open shared object file: No such file or directory

```


Try running "sudo ldconfig" in a terminal, then try re-running projectM.

---

### Post by surement on 2009-11-03
> **punkrockguy318 said:**
> 2.0 is working fine for me, however cmake has trouble detecting that pulseaudio is installed.  i had to take out the pulseaudio checking lines in the cmake scripts to get it to compile, but it works great other than that

How do you do that?? I have the same problem...

 CMake Error at projectM-pulseaudio/CMakeLists.txt:55 (MESSAGE):
   ERROR: Pulse Audio is NOT found.  Please install pulse audio 0.9.8 or
   greater from [www.pulseaudio.org]("http://www.pulseaudio.org").

---

### Post by bennyto on 2009-11-16
hi everybody,

I get a nasty message when I try to make install ...

```
bennyto@ubuntulaptop:~/projectm/projectM-Trunk$ sudo make install
make: *** Pas de règle pour fabriquer la cible « install ». Arrêt.

```:frown:
what should I do ..?

ben

---

### Post by aYs-Halo on 2009-12-12
> **surement said:**
> How do you do that?? I have the same problem...

 CMake Error at projectM-pulseaudio/CMakeLists.txt:55 (MESSAGE):
   ERROR: Pulse Audio is NOT found.  Please install pulse audio 0.9.8 or
   greater from [www.pulseaudio.org]("http://www.pulseaudio.org").

same here..
i managed to take the lines out, but then i get an error during the install process @88% 
"make[2]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/qprojectM-pulseaudio.o] Error 1
make[1]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/all] Error 2
make: *** [all] Error 2"

help anyone? :(

---

### Post by nerdy_kid on 2010-01-02
i made some .debs with checkinstall if anyone wants them.... (compiled with jaunty)

---

### Post by fizyxnrd on 2010-01-28
To those of you with problems finding the pulseaudio package information,
make sure that you have installed the libpulse-dev package.  This should clear up any problems with ccmake finding pulseaudio.

If not, you will still need libpulse-dev (to provide pulseaudio headers), and you may need to modify the CMakeList.txt file.

Go to the projectM-pulseaudio directory and comment out the following lines from CMakeLists.txt

pkg_search_module(LIBPULSE REQUIRED libpulse>=0.9.8

(Line 29)
and

if (LIBPULSE_FOUND)
MESSAGE(STATUS "[projectM-pulseaudio] pulse audio detected.")
else (LIBPULSE_FOUND)
MESSAGE(FATAL_ERROR "ERROR: Pulse Audio is NOT found. Please install pulse audio 0.9.8 or greater from www.pulseaudio.org.")
endif(LIBPULSE_FOUND)

(lines 43-47)

Use cmake or ccmake as usual, make, and make install.

---

### Post by nishant.singh28 on 2010-01-31
```
nishant@nishant-Studio:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 

(<unknown>:14040): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field

[projectM] config file: /home/nishant/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
unconnected: connecting... 
connectHelper:  "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" 
Segmentation fault

```
Now what?

---

### Post by punkrockguy318 on 2010-02-03
> **nishant.singh28 said:**
> ```
nishant@nishant-Studio:~$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 

(<unknown>:14040): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field

[projectM] config file: /home/nishant/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
unconnected: connecting... 
connectHelper:  "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" 
Segmentation fault

```
Now what?

i'm getting the same error here as well

i've tried not including everything and i'm still getting the error

if i start it like 10 times in a row it will start but otherwise it will fail with with either that error or a segfault at start

---

### Post by arrrghhh on 2010-02-08
I believe this is in the repo's now - have you tried installing just "libvisual-projectm"?

---

### Post by punkrockguy318 on 2010-02-08
> **arrrghhh said:**
> I believe this is in the repo's now - have you tried installing just "libvisual-projectm"?

libvisual-projectm is sort of useless

projectM-pulseaudio is where its at

---

### Post by ThatBum on 2010-03-15
**E0:** Things in red are obsolete.

Holy God, thanks for telling me about checkinstall, it is INCREDIBLY  useful.

[COLOR=Red]*I made a deb of projectM using the latest svn using checkinstall, which I  assume is 2.0 (doesn't say in about!).*[/COLOR]

For people who don't want to download the svn and compile and risk  breaking something and all that, I have the package attached here. I  didn't put any dependencies in it because, well, I don't know them, so  you're on your own with that.

Oh, it's 32 bit. I don't have a 64 bit machine around, so eh. I don't  think you can set the architecture in checkinstall. 

Remember, I called the package projectm, so to uninstall it, run 

```
dpkg -r projectm 
or
apt-get remove projectm
or
apt-get purge projectm
```as root

Thanks all. Beats the hell out of Rhythmbox's GOOM and monoscope. 

One more thing, I'm just asking, is there a preset kinda like VLC's  spectrometer out there? It's really informative. 

**E1:**   Ah shoot, it won't let me upload debs. I'll put it in a zip.

**E2:**   And while I'm at it, will someone tell me what in Sam Hill  this "Easter Egg Parameter" does? Or is it a programmer's secret?

[COLOR=Red][I]E3 : I gave the deb to a friend, it didn't install some libs.  Specifically, when running projectM-pulseaudio from a terminal, it asked for  these:
[/I][/COLOR]  
[LIST]
[*][COLOR=Red]*libprojectM-qt.so.1 (symlink of libprojectM-qt.so.1.10)*[/COLOR]
[*][COLOR=Red]*libprojectM.so.2 (symlink of libprojectM.so.2.00)*[/COLOR]
[*][COLOR=Red]*libQtOpenGL.so.4 (symlink of libQtOpenGL.so.4.5.2)*[/COLOR]
[/LIST]
[COLOR=Red][I]I Skype'd him these libs, and on his end he moved them to /usr/lib and made the appropriate symlinks. Then it worked fine, albeit slow because of his hardware, but that's besides the point.

I made a new deb that seems to work. The other one didn't appear to have the libs in it, according to the Included Files tab. The only thing is that is doesn't make the GNOME launcher in the menu though, but no big deal. The icon installs to /usr/share/pixmaps like it's supposed to, so just manually make a launcher.

For those who installed the first one, don't worry, it still installed to /usr, just uninstall and reinstall with this package.

This has been quite the learning experience. Thanks for writing such through instructions![/I][/COLOR]   

**E4**: Now I made a deb out of the tarball from the SourceForge projectM, 2.0.1.
[http://sourceforge.net/projects/projectm/files/](http://sourceforge.net/projects/projectm/files/)

---

### Post by enlight22 on 2010-03-28
I compiled the latest SVN on jaunty, should be version 2.0.1 i guess. made deb with checkinstall. so this is a 64 bit compilation of ProjectM latest.  For some reason the package name is src. if anyone knows how to change that let me know.

---

### Post by cpttripzz on 2010-04-03
Thanks alot, works beautifully. Saved me having to compile this.

---

### Post by ThatBum on 2010-04-11
> **enlight22 said:**
> For some reason the package name is src. if anyone knows how to change that let me know.

Change the "Name" value in the "This package will be built according to these values:" dialog.

Example:

[http://www.falkotimme.com/howtos/checkinstall/images/1.gif](http://www.falkotimme.com/howtos/checkinstall/images/1.gif)

I found the dependencies, by the way, by installing it on a fresh system, and using apt-file to find the missing packages that have the needed files.

They are libqt4-opengl, libglew1.5, and libftgl2.

I would make a new package, but I have Lucid Lynx Beta 2 now, and it just doesn't want to compile under Lucid.

---

### Post by betterthanjordan79 on 2010-05-04
tried this guide 2day on my 10.04 32bit ubuntu and it worked perfect!!i have a hp pavilion dv6000 with nvidia geforce go 7400!!

thanks so much for this!!!been trying to get this to work sice 8.04!!!!!thanks again!!!

---

### Post by Humiliation on 2010-05-08
I get an error when trying to install the deb (32-BIT)
```
Dpkg: error processing /home/dan/Desktop/projectm_2.0.1-1334_i386.deb (--Install): trying to overwrite '/usr/lib/projectm.so.2.00' which is also in package libprojectm2 0:1.2.0-3
dpkg-deb: subproject paste killed by signal (broken pipe)

```

I've been trying for ages to get this to work with the source and the deb so any help is appreciated.

PS Running lucid

---

### Post by ThatBum on 2010-05-11
> **Humiliation said:**
> I get an error when trying to install the deb (32-BIT)
```
Dpkg: error processing /home/dan/Desktop/projectm_2.0.1-1334_i386.deb (--Install): trying to overwrite '/usr/lib/projectm.so.2.00' which is also in package **libprojectm2** 0:1.2.0-3
dpkg-deb: subproject paste killed by signal (broken pipe)

```I've been trying for ages to get this to work with the source and the deb so any help is appreciated.

PS Running lucid

Uninstall package **libprojectm2**.

Also, if it says "...which is also in package xxx" uninstall that too.

---

### Post by Psychoscorpic on 2010-05-16
> **Humiliation said:**
> I get an error when trying to install the deb (32-BIT)
```
Dpkg: error processing /home/dan/Desktop/projectm_2.0.1-1334_i386.deb (--Install): trying to overwrite '/usr/lib/projectm.so.2.00' which is also in package libprojectm2 0:1.2.0-3
dpkg-deb: subproject paste killed by signal (broken pipe)

```

I've been trying for ages to get this to work with the source and the deb so any help is appreciated.

PS Running lucid
Hi "Humiliation"
I get the same error (using the 64bit DEB supplied here by enlight22)
Used Synaptic to "Remove completely" the libprojectm2 package and it's associate, but still same error.

Lucid 64bit, fresh install.

---

### Post by proteusmoteus on 2010-05-23
[enlight22]("http://ubuntuforums.org/member.php?u=1043819")'s deb didnt work for me, but it inspired me to learn checkinstall and make my own.  One major difference is the number of presets in the deb I generated. I had to generate a script to rename all the presets (.milk files) with spaces in their name to underscores so that checkinstall would include them in the deb.

Generated this on a fresh install of Lucid Lynx so hopefully it will work for everyone with an updated system.

Also for everyone with a working projectM, apparently F1 in the visualization window displays a help menu.  An option not listed in the Help Menu though is pressing "b" after "m" to see a tool bar.

---

### Post by ThatBum on 2010-05-23
> **Psychoscorpic said:**
> Hi "Humiliation"
I get the same error (using the 64bit DEB supplied here by enlight22)
Used Synaptic to "Remove completely" the libprojectm2 package and it's associate, but still same error.

Lucid 64bit, fresh install.

If you really got rid of libprojectm2, there shouldn't be a /usr/lib/projectm.so.2.00 anymore. The deb you have there is also trying to install this, but the repos one is also there and is conflicting (the repos one isn't projectm-pulseaudio, it's some kind of thing for libvisual...kind of useless, really).

Double check if it was really uninstalled, then try manually removing /usr/lib/projectm.so.2.0.

---

### Post by biodiesel-bri on 2010-05-29
Thanks proteusmoteus!

---

### Post by Gryphen on 2010-06-21
A easy to "get" over 1000 presets is to copy the contents of all of the preset folders in the source code folder to /usr/share/projectM/all.

Here are instructions if you want to create a shell script to do it for you

```
nano
```paste in 
```
#!/bin/bash

sudo mkdir /usr/share/projectM/all  
cd /usr/local/src/projectm/projectM-Trunk/  #source location
sudo cp -f presets_milkdrop/* /usr/share/projectM/all  
sudo cp -f presets_milkdrop_200/* /usr/share/projectM/all  
sudo cp -f presets_test/* /usr/share/projectM/all  
sudo cp -f presets/* /usr/share/projectM/all  
sudo cp -f presets_milkdrop_104/* /usr/share/projectM/all  
sudo cp -f presets_projectM/* /usr/share/projectM/all 
sudo cp -f presets_yin/* /usr/share/projectM/all

```Ctrl+o

save it with a name ending with .sh
```
chmod 777 [name].sh
``````
./[the name you name chose].sh
```

---

### Post by Psychoscorpic on 2010-06-24
> **Psychoscorpic said:**
> Hi "Humiliation"
I get the same error (using the 64bit DEB supplied here by enlight22)
Used Synaptic to "Remove completely" the libprojectm2 package and it's associate, but still same error.

Lucid 64bit, fresh install.
Ah! Discovered another projectm file was installed in Synaptic and killed it too. Re-ran the .DEB and all is as it should be! ProjectM now appears in Sound & Video and settings worl fine.
Used the Menu (M) to install the pile of Milk presets that came in the archive. I'm smiling again now.

---

### Post by jchedstrom on 2010-07-05
It took me about 2 hours to get projectm installed on Ubuntu 10.04.  These are my solutions for specific problems.
 
During ccmake "libvisual 0.4 not found": assuming you've already install  all of the libvisual components properly, comment out with #'s anything  to do with verifying libvisual installation inside of  'projectM-libvisual/CCMakeLists.txt' and ' projectM-libvisual-alsa/CCMakeLists.txt'...
```
#pkg_search_module(LIBVISUAL REQUIRED libvisual-0.4) 
 
if (LIBPROJECTM_FOUND) 
MESSAGE (STATUS "[projectM-libvisual] projectM detected.") 
else(LIBPROJECTM_FOUND) 
MESSAGE (FATAL_ERROR "projectM NOT detected. Please install the projectM  module or build from the top level projectM source directory.") 
endif(LIBPROJECTM_FOUND) 
 
#if(LIBVISUAL_FOUND) 
#MESSAGE(STATUS "[projectM-libvisual] libvisual detected.") 
#else(LIBVISUAL_FOUND) 
#MESSAGE(FATAL_ERROR "libvisual 0.4 not found! Please visit  http://libvisual.sf.net and download the module.") 
#endif(LIBVISUAL_FOUND)  
```

during make step still having problems finding libvisual/libvisual.h:
```
sudo ln -s /usr/lib/libvisual-0.4/libvisual/ /usr/lib/libvisual
```

"error: X11/extensions/xf86vmode.h: No such file or directory":
```
sudo apt-get install libxxf86vm-dev
```

errors compiling the libvisual-alsa stuff, first error was to do with  undefined 'visual_init': just turn OFF inside ccmake  INCLUDE_LIBVISUAL_ALSA

---

### Post by nerdy_kid on 2010-08-13
im on lucid with nvidia geforce 8600M and getting a seg fault (compiled fine though):
```


./projectM-test
dir:/usr/local/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1280 x 800
[projectM] config file: /home/nerdy_kid/.projectM/config.inp
No Textures Loaded from /usr/local/share/projectM/textures
Segmentation fault


```

how would i get at least a backtrace?

---

### Post by nerdy_kid on 2010-08-13
> **nerdy_kid said:**
> im on lucid with nvidia geforce 8600M and getting a seg fault (compiled fine though):
```


./projectM-test
dir:/usr/local/share/projectM/config.inp 
reading ~/.projectM/config.inp 
Screen Resolution: 1280 x 800
[projectM] config file: /home/nerdy_kid/.projectM/config.inp
No Textures Loaded from /usr/local/share/projectM/textures
Segmentation fault


```

how would i get at least a backtrace?

backtrace:
```


rogram received signal SIGSEGV, Segmentation fault.
0x00362f17 in FTSize::CharSize(FT_FaceRec_**, unsigned int, unsigned int, unsigned int) () from /usr/lib/libftgl.so.2

```
disabled ftgl fonts and problem solved :D

---

### Post by Afi on 2010-08-27
With this error: No Textures Loaded from /usr/share/projectM/textures
i just corrected font paths in /home/user/.projectM/

Title Font = /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
Menu Font = /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMono.ttf

after that projectm-pulseaudio works in Meerkat. I don't know if it's the right way but it works for me.

---

### Post by eddier on 2010-09-12
Afi--your a :KS

Correcting the fonts path has done the trick for me!

Using the 64-bit Deb with Maverick Meerkat.

I wonder if thats the problem with the install from Synaptic??


eddie  :guitar:

---

### Post by zman0900 on 2010-09-26
> **jchedstrom said:**
> 
during make step still having problems finding libvisual/libvisual.h:
```
sudo ln -s /usr/lib/libvisual-0.4/libvisual/ /usr/lib/libvisual
```

Think you made a typo here.  /usr/lib should be /usr/include.  Otherwise, it worked for me.  Thanks.

---

### Post by earthmeLon on 2010-10-18
The program 'ccmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake-curses-gui

---

### Post by DoctorBho on 2010-10-24
Thank you for that, proteusmoteus! I just switched my 32 bit to lucid to 64 bit, and just about everything came back from the repos (Synaptic > File > Save markings, in case anyone is interested) but I had forgotten how much hassle it had been to compile projectm. Boy was I not looking forward to that!

But clicking on your deb, on the other hand, was sweet and effective!

---

### Post by eddier on 2010-11-14
Running Maverick(in mint 10). I see projectM-pulseaudio is in the repo's but I decided to try this install and enable cg in ccmake, Crunch!

```
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp: In function ‘std::string read_config()’:
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:170: error: ‘mkdir’ was not declared in this scope
make[2]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/qprojectM-pulseaudio.o] Error 1
make[1]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/all] Error 2
make: *** [all] Error 2

```

Anyone provide a clue,I tried to decipher it but its a bit gobbledegook to me,it appears to be a missing directory??

eddie

---

### Post by nerdy_kid on 2010-11-14
> **eddier said:**
> Running Maverick(in mint 10). I see projectM-pulseaudio is in the repo's but I decided to try this install and enable cg in ccmake, Crunch!

```
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp: In function ‘std::string read_config()’:
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:170: error: ‘mkdir’ was not declared in this scope
make[2]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/qprojectM-pulseaudio.o] Error 1
make[1]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/all] Error 2
make: *** [all] Error 2

```

Anyone provide a clue,I tried to decipher it but its a bit gobbledegook to me,it appears to be a missing directory??

eddie

Try running "sudo apt-get build-dep projectm-pulseaudio"
and rerunning make.

---

### Post by nerdy_kid on 2010-12-15
> **eddier said:**
> Running Maverick(in mint 10). I see projectM-pulseaudio is in the repo's but I decided to try this install and enable cg in ccmake, Crunch!

```
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp: In function &#8216;std::string read_config()&#8217;:
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:170: error: &#8216;mkdir&#8217; was not declared in this scope
make[2]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/qprojectM-pulseaudio.o] Error 1
make[1]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/all] Error 2
make: *** [all] Error 2

```

Anyone provide a clue,I tried to decipher it but its a bit gobbledegook to me,it appears to be a missing directory??

eddie
fixed:  open qprojectm-pulseaudio.cpp in a text editor, go to line 169 and comment it out.  Then it will compile.  Just make sure that ~/.projectM/config.inp exists, cause I am not a C++ programmer, so I don't know how to completely fix the situation, just kinda hack around it :P  Now I get CG too lol

---

### Post by figure002 on 2011-02-15
> **eddier said:**
> Running Maverick(in mint 10). I see  projectM-pulseaudio is in the repo's but I decided to try this install  and enable cg in ccmake, Crunch!

```
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:  In function ‘std::string read_config()’:
/home/eddie/projectm/projectM-Trunk/src/projectM-pulseaudio/qprojectM-pulseaudio.cpp:170:  error: ‘mkdir’ was not declared in this scope
make[2]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/qprojectM-pulseaudio.o] Error 1
make[1]: *** [projectM-pulseaudio/CMakeFiles/projectM-pulseaudio.dir/all] Error 2
make: *** [all] Error 2

```Anyone provide a clue,I tried to decipher it but its a bit gobbledegook to me,it appears to be a missing directory??

eddie

> **nerdy_kid said:**
> fixed:  open qprojectm-pulseaudio.cpp in a text editor, go to line 169 and comment it out.  Then it will compile.  Just make sure that ~/.projectM/config.inp exists, cause I am not a C++ programmer, so I don't know how to completely fix the situation, just kinda hack around it :P  Now I get CG too lol

I found the fix for this problem. If you read the manual for the mkdir() function (type "man 2 mkdir"), you'll see that this function requires <sys/types.h> and <sys/stat.h>. So do the following:

1) Open "src/projectM-pulseaudio/qprojectM-pulseaudio.cpp" in a text editor.
2) Under line 46 ("#include <math.h>") add the following two lines:
```
#include <sys/types.h>
#include <sys/stat.h>
```3) Save and exit. It should now compile.

I've submitted the patch to the projectM tracker: [https://sourceforge.net/tracker/?func=detail&aid=3182459&group_id=104201&atid=637262](https://sourceforge.net/tracker/?func=detail&aid=3182459&group_id=104201&atid=637262)

---

### Post by punkrockguy318 on 2011-02-15
> **figure002 said:**
> I found the fix for this problem. If you read the manual for the mkdir() function (type "man 2 mkdir"), you'll see that this function requires <sys/types.h> and <sys/stat.h>. So do the following:

1) Open "src/projectM-pulseaudio/qprojectM-pulseaudio.cpp" in a text editor.
2) Under line 46 ("#include <math.h>") add the following two lines:
```
#include <sys/types.h>
#include <sys/stat.h>
```3) Save and exit. It should now compile.

You might want to submit this upstream :popcorn:

---

### Post by figure002 on 2011-02-15
> **punkrockguy318 said:**
> You might want to submit this upstream :popcorn:

Good point. I just submitted the patch to the projectM tracker: [https://sourceforge.net/tracker/?fun...01&atid=637262]("https://sourceforge.net/tracker/?func=detail&aid=3182459&group_id=104201&atid=637262")

---

### Post by punkrockguy318 on 2011-02-15
> **figure002 said:**
> Good point. I just submitted the patch to the projectM tracker: [https://sourceforge.net/tracker/?fun...01&atid=637262]("https://sourceforge.net/tracker/?func=detail&aid=3182459&group_id=104201&atid=637262")

hopefully it gets committed

there hasn't been much/any projectM svn activity in a while iirc :(

---

### Post by phyroarch on 2011-02-17
Hi, I managed to get projectm installed but when I tried it I realized that  it only shown a black screen, I hope somebody have any idea on how to fix this, PS. Im using ubuntu 10.10.

---

### Post by nerdy_kid on 2011-02-17
> **phyroarch said:**
> Hi, I managed to get projectm installed but when I tried it I realized that  it only shown a black screen, I hope somebody have any idea on how to fix this, PS. Im using ubuntu 10.10.

how did you install it?  In Ubuntu 10.10 all you have to do is type

```

sudo apt-get install projectm-pulseaudio

```

in a terminal.

---

### Post by xorman2k7 on 2011-02-25
hi, I'm in a similar situation:
I installed it from the repos and it opens and shows the plugins ok, but even though i configured the right pulseaudio entry it just looks like there's no audio going through it.

then i downloaded the .deb from page 28 and the projectm-test works, but the projectm-pulseaudio one doesn't!

any ideas??

I'm using rhythmbox for playing audio

thanks!

---

### Post by kid_meier on 2011-02-25
> **xorman2k7 said:**
> it just looks like there's no audio going through it.

Maybe this will help, as I just solved something similar. 

Apparently the pulseaudio "monitor" on my default sound card output was muted. I randomly happened upon this by launching PulseAudio Volume Control. Go to the Input Devices tab, from the "Show" drop-down select "Monitors". Then unmute the monitor of your soundcard output. Best to do this with sound playing, when you unmute it you will see the volume meter fluctuate with the audio.

That did it for me. 

You may need to install the 'pavucontrol' package if its not already installed.

Incidentally when this is muted Ear Candy basically mutes everything making it utterly unusable; which has been driving me insane for the past several months.

---

### Post by xorman2k7 on 2011-02-25
that was it! thanks a lot kid_meier!

---

### Post by 55tptag on 2011-03-12
Thanks for the article! Because of your article I can now get visualizations with Exaile.  For Ubuntu 10.04 (64-bit) I had to also install:
libsdl1.2-dev
cmake-curses-gui

---

### Post by psytech on 2011-04-27
A tip for anybody experiencing problems with presets going blank or static - Make sure ProjectM is configured to work with the correct sound card. It took me forever to figure that one out!

---

### Post by crab80 on 2011-05-02
Anyone have any luck getting projectM to work on 11.04? I've tried both compiling it myself using the guide in this thread, and have tried installing through aptitude. For both installations, when I go to Applications>Sound&Video>ProjectM pulseaudio Visualization it does not do anything when I click it - no window of any kind comes up. It's as if the program does not run. I've also tried launching it from the terminal with no success.

---

### Post by nerdy_kid on 2011-05-05
> **crab80 said:**
> Anyone have any luck getting projectM to work on 11.04? I've tried both compiling it myself using the guide in this thread, and have tried installing through aptitude. For both installations, when I go to Applications>Sound&Video>ProjectM pulseaudio Visualization it does not do anything when I click it - no window of any kind comes up. It's as if the program does not run. I've also tried launching it from the terminal with no success.

What is the terminal output when you launch 
```

projectM-pulseaudio

```

from a terminal?
Also, what graphics card are you using, and are the drivers open or closed?

---

### Post by krisgesling on 2011-05-14
For me projectM seemed to be just running through some default visualisations and not responding to any audio source, ie it looked the same whether music was playing or not. 

I don't know why it eventually worked but just changing my hardware profile in sound preferences to Digital Stereo Duplex and then back to Analog Stereo Duplex caused it to work. It's still not responding as I'd expect, it seems to only pick up certain frequencies or something, but it's progress none the less.

The terminal output looks pretty normal:
$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/user/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
Application asked to unregister timer 0x3b000016 which is not registered in this thread. Fix application.
unconnected: connecting... 
connectHelper:  "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" 
CREATED 
READY

---

### Post by s_h_a_d_o_w_s on 2011-05-19
Hey guys I'm still having trouble installing when CG is set to on (I want the nice effects).

```

[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/FBO.o
[  1%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/MilkdropWaveform.o
[  2%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/PerPixelMesh.o
[  3%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Pipeline.o
[  4%] Building CXX object libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o
In file included from /home/maximida/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.hpp:36:0,
                 from /home/maximida/projectm/projectM-Trunk/src/libprojectM/Renderer/Renderer.cpp:1:
/home/maximida/projectm/projectM-Trunk/src/libprojectM/Renderer/ShaderEngine.hpp:27:74: fatal error: Cg/cg.h: No such file or directory
compilation terminated.
make[2]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/Renderer.o] Error 1
make[1]: *** [libprojectM/Renderer/CMakeFiles/Renderer.dir/all] Error 2
make: *** [all] Error 2


```

The fix detailed at the top of this page is already implemented and it still doesn't work. Has anyone gotten it to work? Running Nattyx64 with fglrx.

Also, how do I remove Projectm? It's not in synaptic.

TY

---

### Post by s_h_a_d_o_w_s on 2011-05-19
Hey guys I got it to work by installing sudo aptitude install nvidia-cg-toolkit **even though I have an ATI gpu.**

---

