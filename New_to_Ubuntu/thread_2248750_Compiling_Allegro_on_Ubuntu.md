---
title: "Compiling Allegro on Ubuntu"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by IanCaio on 2014-10-16
Hello guys,

I've been installing and uninstalling ubuntu several times (usually because I didn't know how to use it, and always filled my hard drive with stuff I didn't know how to take off). Now I'm trying to keep it and to learn as much as possible, since I'm not wasting money on windows and XP is not an option anymore ([-(). So far I can do everything I need here, and even learned how to use wine!
So far, trying not to screw my system, I have only installed stuff through the Ubuntu Software Center, but now that I want to program again in C++ and play with Allegro I need to actually compile something, which always seemed as wandering in unknown and dangerous lands.
I'm trying to go step-by-step, so I know exactly what I'm doing, and so far I've:
1) Downloaded Allegro's source code on the website, unziped it on /usr/local/src/allegro-5.0.10
2) Installed Cmake and Cmake-curses-gui through apt-get.
3) I then readed README and tryied to install all dependencies (X11 development libraries and OpenGL libraries), which in my research resumed to those:
mesa-common-dev (which I think is the actuall X11 dev and OpenGL dev libraries); freeglut3 and freeglut3-dev (related to OpenGL development if I'm not mistaken); libglew-dev and libglu1-mesa (apparently the libraries that are related to OpenGL that weren't included in the previous packages).
4) Created a Build directory inside /usr/local/src/allegro-5.0.10 and finally runned "Cmake .." from that directory

From my researchs, Cmake is supposed to be a substitute to ./configure right?

Well, the output from the Cmake command was the following:

```

iancaio@ian-desktop:/usr/local/src/allegro-5.0.10/Build$ cmake ..
-- The C compiler identification is GNU 4.8.2
-- The CXX compiler identification is GNU 4.8.2
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Allowing GCC to use SSE instructions
-- Found PkgConfig: /usr/bin/pkg-config (found version "0.26") 
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- Looking for include file dirent.h
-- Looking for include file dirent.h - found
-- Looking for include file inttypes.h
-- Looking for include file inttypes.h - found
-- Looking for include files sys/types.h, linux/joystick.h
-- Looking for include files sys/types.h, linux/joystick.h - found
-- Looking for include file stdbool.h
-- Looking for include file stdbool.h - found
-- Looking for include file stdint.h
-- Looking for include file stdint.h - found
-- Looking for include file sys/io.h
-- Looking for include file sys/io.h - found
-- Looking for include file sys/stat.h
-- Looking for include file sys/stat.h - found
-- Looking for include file sys/time.h
-- Looking for include file sys/time.h - found
-- Looking for include file time.h
-- Looking for include file time.h - found
-- Looking for include file sys/utsname.h
-- Looking for include file sys/utsname.h - found
-- Looking for include file sys/types.h
-- Looking for include file sys/types.h - found
[COLOR=#ff0000]-- Looking for include file soundcard.h
-- Looking for include file soundcard.h - not found[/COLOR]
-- Looking for include file sys/soundcard.h
-- Looking for include file sys/soundcard.h - found
[COLOR=#ff0000]-- Looking for include file machine/soundcard.h
[/COLOR] [COLOR=#ff0000]-- Looking for include file machine/soundcard.h - not found[/COLOR]
-- Looking for include file linux/soundcard.h
-- Looking for include file linux/soundcard.h - found
[COLOR=#ff0000]-- Looking for include file libkern/OSAtomic.h
-- Looking for include file libkern/OSAtomic.h - not found[/COLOR]
-- Looking for include file sys/inotify.h
-- Looking for include file sys/inotify.h - found
-- Looking for include file sys/timerfd.h
-- Looking for include file sys/timerfd.h - found
[COLOR=#ff0000]-- Looking for getexecname
-- Looking for getexecname - not found[/COLOR]
-- Looking for mkstemp
-- Looking for mkstemp - found
-- Looking for mmap
-- Looking for mmap - found
-- Looking for mprotect
-- Looking for mprotect - found
-- Looking for sched_yield
-- Looking for sched_yield - found
-- Looking for sysconf
-- Looking for sysconf - found
-- Looking for fseeko
-- Looking for fseeko - found
-- Looking for ftello
-- Looking for ftello - found
-- Check size of _Bool
-- Check size of _Bool - done
[COLOR=#ff0000]-- Performing Test ALLEGRO_HAVE_PROCFS_ARGCV
-- Performing Test ALLEGRO_HAVE_PROCFS_ARGCV - Failed
-- Performing Test ALLEGRO_HAVE_SV_PROCFS_H
-- Performing Test ALLEGRO_HAVE_SV_PROCFS_H - Failed[/COLOR]
-- Performing Test ALLEGRO_HAVE_VA_COPY
-- Performing Test ALLEGRO_HAVE_VA_COPY - Success
-- Looking for XOpenDisplay in /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so
-- Looking for XOpenDisplay in /usr/lib/i386-linux-gnu/libX11.so;/usr/lib/i386-linux-gnu/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/i386-linux-gnu/libX11.so
-- Found OpenGL: /usr/lib/i386-linux-gnu/libGL.so  
-- Looking for include file pthread.h
-- Looking for include file pthread.h - found
[COLOR=#ff0000]-- Looking for pthread_create
-- Looking for pthread_create - not found[/COLOR]
[COLOR=#ff0000]-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found[/COLOR]
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
[COLOR=#ff0000]-- Looking for XcursorImageCreate in Xcursor
-- Looking for XcursorImageCreate in Xcursor - not found
CMake Error at CMakeLists.txt:570 (message):
  X11 support requires Xcursor library.[/COLOR]


-- Configuring incomplete, errors occurred!
See also "/usr/local/src/allegro-5.0.10/Build/CMakeFiles/CMakeOutput.log".
See also "/usr/local/src/allegro-5.0.10/Build/CMakeFiles/CMakeError.log".

```

My conclusions after that (which are not accurate, so I'm here for an enlightment from the gurus :)):
1) Some libraries are missing (like soundcard.h), but that was supposed to happen since README says some add-on libraries from Allegro required some extra libraries, that were not fundamental to the compilation of the core Allegro.
2) Some fundamental libraries were not found (Xcursor and Xcursor-dev maybe?)
3) Two tests failed (is that really a problem?):
-- Performing Test ALLEGRO_HAVE_PROCFS_ARGCV
-- Performing Test ALLEGRO_HAVE_PROCFS_ARGCV - Failed
-- Performing Test ALLEGRO_HAVE_SV_PROCFS_H
-- Performing Test ALLEGRO_HAVE_SV_PROCFS_H - Failed

I've tryied to read the CmakeOutput.log and CmakeError.log, but it seens like it's a little advanced for a begginer like me. I can post it here if you wish though!

Well, what should I do then? Install Xcursor and Xcursor-dev and try again? Am I wrong at something so far?

Sorry about the long text and all the questions, I'm just trying to make sure I dont screw anything up and learn as much as possible in the process hehe

Thanks in advance,
Ian

ps: My intention is to finish the installation with checkinstall so I can uninstall it easily

---

### Post by Vladlenin5000 on 2014-10-16
Hi, welcome.

First of all you need this:
```
[FONT=Arial][FONT=Arial]sudo apt-get install build-essential subversion cmake xorg-dev libgl1-mesa-dev libglu-dev[/FONT][/FONT]
```

Then you should also install all of this complements:
```
[FONT=Arial][FONT=Arial]sudo  apt-get install libpng-dev libcurl4-nss-dev libfreetype6-dev  libjpeg-dev libvorbis-dev libopenal-dev libphysfs-dev libgtk2.0-dev  liboss4-salsa-dev libpulse-dev libflac-dev libdumb1-dev[/FONT][/FONT]
```

Lastly, it's strongly recommended to also install the documentation dependencies:
```
[FONT=Arial][FONT=Arial]sudo apt-get install exuberant-ctags dvi2ps dvipdfmx latex2html pandoc[/FONT][/FONT]
```


After taking care of all this dependencies you can then proceed to compile. You already have it but just in case download it again from the repository:
```
[FONT=Arial]svn co https://alleg.svn.sourceforge.net/svnroot/alleg/allegro/branches/5.0 allegro-5.0[/FONT]
```
This will download the source code to the folder 'allegro-5.0'... Then:
```
[FONT=Arial][FONT=Arial]cd allegro-5.0[FONT=Arial][FONT=Arial]mkdir build[/FONT][/FONT][FONT=Arial][FONT=Arial][FONT=Arial][FONT=Arial]cd build[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]
```

Then
```
[FONT=Arial]sudo cmake -DCMAKE_INSTALL_PREFIX=/usr ..[/FONT]
```
(Press "c" a couple of time then "g" to get back to the terminal, if needed)
This defines where to install *.h* files, add the path [FONT=Arial]"/usr/local/lib" to "/etc/ld.so.conf"[/FONT] and execute [FONT=Arial]"ldconfig".


Now it can be installed:
```
[FONT=Arial][FONT=Arial]sudo make install[/FONT][/FONT]
```


 The last step should be configuring the library to work with IDE Codeblocks.[/FONT]

---

### Post by IanCaio on 2014-10-17
Hey,

Except from the subversion and the documentation dependencies I've looked for all the packages missing, mostly audio, image manipulation and network libraries, and installed them, except from liboss4-salsa-dev, which I didn't find. That's what I get when I run "apt-cache search liboss":
```

iancaio@ian-desktop:~$ apt-cache search liboss
libossp-uuid-dev - OSSP uuid ISO-C and C++ - headers and static libraries
libossp-uuid16 - OSSP uuid ISO-C and C++ - shared library
liboss4-salsa-asound2 - OSS to Alsa compatibility library - binary compatibility symlink
liboss4-salsa2 - OSS to Alsa compatibility library
libossim-dev - The OSSIM library -- development files
libossim1 - The OSSIM library -- shared library
libossp-sa-dev - Abstraction library for the Unix socket API
libossp-sa12 - Abstraction library for the Unix socket API
libossp-uuid-perl - perl OSSP::UUID - OSSP uuid Perl Binding

```

I get nothing when running "dpkg -l | grep liboss", which means I probably don't even have the liboss4-salsa2. But there's no development package there.

I've then, after installing the following packages, tryied to run cmake again:

```

Packages installed:
Cmake; Cmake-curses-gui 
Xorg-dev (development library for Xorg server)
Mesa-common-dev (Mesa development package - also needed for OpenGL dev)
Freeglut3; Freeglut3-dev (libraries for OpenGL development)
libglew-dev; libglu1-mesa (also necessary for OpenGL)
libxcb-cursor-dev (I've installed it, because the first error said "CMake Error at CMakeLists.txt:570 (message): X11 support requires Xcursor library.")
libjpeg-dev (library for JPEG manipulation development)
libcurl4-nss-dev (library of URL client-side network transfer)
libvorbis-dev (Vorbis - used for recording audio with high compression - .ogg; .oga)
libopenal-dev (Open Audio Library - tridimensional multichannel audio library, used with OpenGL)
libphysfs1; libphysfs-dev (files management for games)
libgtk2.0-dev
libpulse-dev (Pulseaudio)
libflac-dev (Audio)
libdumb1; libdumb1-dev (Audio library)

```

When I run cmake again though, the first error persists:
```

iancaio@ian-desktop:/usr/local/src/allegro-5.0.10/Build$ cmake ..
-- Allowing GCC to use SSE instructions
CMake Error at CMakeLists.txt:570 (message):
  X11 support requires Xcursor library.


-- Configuring incomplete, errors occurred!
See also "/usr/local/src/allegro-5.0.10/Build/CMakeFiles/CMakeOutput.log".
See also "/usr/local/src/allegro-5.0.10/Build/CMakeFiles/CMakeError.log".

```

It doesn't show all the other packages found or not found, but it says the Xcursor library is still missing, even though I guess I already installed it:

```

iancaio@ian-desktop:/usr/local/src/allegro-5.0.10/Build$ dpkg -l | grep cursor
ii  dmz-cursor-theme                                      0.4.4ubuntu1                                        all          Style neutral, scalable cursor theme
ii  icoutils                                              0.31.0-2                                            i386         Create and extract MS Windows icons and cursors
ii  libwayland-cursor0:i386                               1.4.0-1ubuntu1                                      i386         wayland compositor infrastructure - cursor library
[COLOR=#000080]ii  libxcb-cursor-dev:i386                                0.1.1-3                                             i386         utility libraries for X C Binding -- cursor, development files
ii  libxcb-cursor0:i386                                   0.1.1-3                                             i386         utility libraries for X C Binding -- cursor
ii  libxcursor-dev:i386                                   1:1.1.14-1                                          i386         X cursor management library (development files)
ii  libxcursor1:i386                                      1:1.1.14-1                                          i386         X cursor management library[/COLOR]
ii  xcursor-themes                                        1.0.3-1                                             all          Base X cursor themes

```

Do I have to download some other package related to Xcursor? Maybe I need to clear the Cmake directory so it start from 0? Not sure what to do right now.

Sorry if I keep trying to explain what the packages are. It's just so this topic can be a future reference for people with troubles trying to install Allegro, in a way they can actually understand what all the packages they are installing are.

Best regards

---

### Post by IanCaio on 2014-10-17
I've managed to finish the installation. I simply deleted the whole Allegro source folder and unziped it again, which deleted also the Cmake files. I then run cmake again. I finished the installation with "make" and "checkinstall" sucessfuly.

So if anyone is having errors while running cmake, even though you already have the packages installed, you might want to delete the folder and start over (or maybe only delete the cmake folder from the source directory).

---

### Post by Vladlenin5000 on 2014-10-17
Indeed. Thank you for your feedback.

Happy Ubuntuing.

---

