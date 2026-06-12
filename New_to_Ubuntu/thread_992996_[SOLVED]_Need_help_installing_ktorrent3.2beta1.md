---
title: "[SOLVED] Need help installing ktorrent3.2beta1"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by OisinT on 2008-11-25
so I have the tarball which I've extracted to the desktop.
I navigate to the folder, but it has no makefile or install file or anything.
help is appreciated

---

### Post by taurus on 2008-11-25
Maybe you just run it as it.  While in that directory, can you post the output of this command from a terminal?

```
ls -la
```

---

### Post by OisinT on 2008-11-25
```
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1$ ls -la
total 100
drwxr-xr-x 13 oisint oisint  4096 2008-11-16 10:02 .
drwxr-xr-x 13 oisint oisint  4096 2008-11-25 15:41 ..
-rw-r--r--  1 oisint oisint 20615 2008-11-16 09:58 ChangeLog
drwxr-xr-x  3 oisint oisint  4096 2008-11-16 09:58 cmake
-rw-r--r--  1 oisint oisint  1904 2008-11-16 10:02 CMakeLists.txt
-rw-r--r--  1 oisint oisint 18273 2008-11-16 09:58 COPYING
drwxr-xr-x  2 oisint oisint  4096 2008-11-16 09:58 ideal
drwxr-xr-x  3 oisint oisint  4096 2008-11-16 10:00 ktorrent
drwxr-xr-x  2 oisint oisint  4096 2008-11-16 09:58 ktupnptest
drwxr-xr-x 15 oisint oisint  4096 2008-11-16 09:58 libbtcore
drwxr-xr-x  7 oisint oisint  4096 2008-11-16 10:00 libktcore
drwxr-xr-x  2 oisint oisint  4096 2008-11-16 09:58 libktupnp
drwxr-xr-x  4 oisint oisint  4096 2008-11-16 09:58 plasma
drwxr-xr-x 17 oisint oisint  4096 2008-11-16 09:58 plugins
drwxr-xr-x 45 oisint oisint  4096 2008-11-16 10:02 po
drwxr-xr-x  2 oisint oisint  4096 2008-11-16 09:58 templates

```

---

### Post by OisinT on 2008-11-25
edit: double post. sorry

---

### Post by taurus on 2008-11-25
How about

```
ls -la ~/Desktop/ktorrent-3.2beta1/ktorrent
```

---

### Post by OisinT on 2008-11-25
```
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1$ ls -la ~/Desktop/ktorrent-3.2beta1/ktorrent
total 696
drwxr-xr-x  3 oisint oisint  4096 2008-11-16 10:00 .
drwxr-xr-x 13 oisint oisint  4096 2008-11-16 10:02 ..
-rw-r--r--  1 oisint oisint  2537 2008-11-16 09:58 addpeersdlg.cpp
-rw-r--r--  1 oisint oisint  2095 2008-11-16 09:58 addpeersdlg.h
-rw-r--r--  1 oisint oisint  3957 2008-11-16 09:58 addpeersdlg.ui
-rw-r--r--  1 oisint oisint  3237 2008-11-16 09:58 advancedpref.cpp
-rw-r--r--  1 oisint oisint  1995 2008-11-16 09:58 advancedpref.h
-rw-r--r--  1 oisint oisint 20824 2008-11-16 09:58 advancedpref.ui
-rw-r--r--  1 oisint oisint  2398 2008-11-16 09:58 app.cpp
-rw-r--r--  1 oisint oisint  1756 2008-11-16 09:58 app.h
-rw-r--r--  1 oisint oisint  7401 2008-11-16 09:58 btpref.ui
-rw-r--r--  1 oisint oisint  1714 2008-11-16 09:58 CMakeLists.txt
-rw-r--r--  1 oisint oisint 29983 2008-11-16 09:58 core.cpp
-rw-r--r--  1 oisint oisint  9697 2008-11-16 09:58 core.h
-rw-r--r--  1 oisint oisint 10517 2008-11-16 09:58 fileselectdlg.cpp
-rw-r--r--  1 oisint oisint  2586 2008-11-16 09:58 fileselectdlg.h
-rw-r--r--  1 oisint oisint  9453 2008-11-16 09:58 fileselectdlg.ui
-rw-r--r--  1 oisint oisint  8039 2008-11-16 09:58 generalpref.ui
-rw-r--r--  1 oisint oisint  2432 2008-11-16 09:58 groupfiltermodel.cpp
-rw-r--r--  1 oisint oisint  2324 2008-11-16 09:58 groupfiltermodel.h
-rw-r--r--  1 oisint oisint  2973 2008-11-16 09:58 grouppolicydlg.cpp
-rw-r--r--  1 oisint oisint  1916 2008-11-16 09:58 grouppolicydlg.h
-rw-r--r--  1 oisint oisint  8674 2008-11-16 09:58 grouppolicydlg.ui
-rw-r--r--  1 oisint oisint 14887 2008-11-16 09:58 groupview.cpp
-rw-r--r--  1 oisint oisint  4123 2008-11-16 09:58 groupview.h
-rw-r--r--  1 oisint oisint 22834 2008-11-16 09:58 gui.cpp
-rw-r--r--  1 oisint oisint  6277 2008-11-16 09:58 gui.h
drwxr-xr-x  2 oisint oisint  4096 2008-11-16 09:58 icons
-rw-r--r--  1 oisint oisint 11108 2008-11-16 09:58 importdialog.cpp
-rw-r--r--  1 oisint oisint  2893 2008-11-16 09:58 importdialog.h
-rw-r--r--  1 oisint oisint  3587 2008-11-16 09:58 importdialog.ui
-rw-r--r--  1 oisint oisint  5200 2008-11-16 09:58 ipfilterlist.cpp
-rw-r--r--  1 oisint oisint  2894 2008-11-16 09:58 ipfilterlist.h
-rw-r--r--  1 oisint oisint  5727 2008-11-16 09:58 ipfilterwidget.cpp
-rw-r--r--  1 oisint oisint  2183 2008-11-16 09:58 ipfilterwidget.h
-rw-r--r--  1 oisint oisint  3085 2008-11-16 09:58 ipfilterwidget.ui
-rw-r--r--  1 oisint oisint  3519 2008-11-16 09:58 ktorrent.desktop
-rw-r--r--  1 oisint oisint 13471 2008-11-16 09:58 ktorrent.notifyrc
-rw-r--r--  1 oisint oisint  1087 2008-11-16 09:58 ktorrentplugin.desktop
-rw-r--r--  1 oisint oisint  2766 2008-11-16 09:58 ktorrentui.rc
-rw-r--r--  1 oisint oisint  8124 2008-11-16 09:58 main.cpp
-rw-r--r--  1 oisint oisint  4706 2008-11-16 09:58 missingfilesdlg.cpp
-rw-r--r--  1 oisint oisint  2570 2008-11-16 09:58 missingfilesdlg.h
-rw-r--r--  1 oisint oisint  4815 2008-11-16 09:58 missingfilesdlg.ui
-rw-r--r--  1 oisint oisint  3267 2008-11-16 09:58 networkpref.cpp
-rw-r--r--  1 oisint oisint  2004 2008-11-16 09:58 networkpref.h
-rw-r--r--  1 oisint oisint 12758 2008-11-16 09:58 networkpref.ui
-rw-r--r--  1 oisint oisint  2393 2008-11-16 09:58 pastedialog.cpp
-rw-r--r--  1 oisint oisint  1978 2008-11-16 09:58 pastedialog.h
-rw-r--r--  1 oisint oisint  1841 2008-11-16 09:58 pastedlgbase.ui
-rw-r--r--  1 oisint oisint  6847 2008-11-16 09:58 prefdialog.cpp
-rw-r--r--  1 oisint oisint  2792 2008-11-16 09:58 prefdialog.h
-rw-r--r--  1 oisint oisint  3290 2008-11-16 09:58 proxypref.cpp
-rw-r--r--  1 oisint oisint  2037 2008-11-16 09:58 proxypref.h
-rw-r--r--  1 oisint oisint 13577 2008-11-16 09:58 proxypref.ui
-rw-r--r--  1 oisint oisint 11766 2008-11-16 09:58 qmpref.ui
-rw-r--r--  1 oisint oisint 10924 2008-11-16 09:58 queuemanagermodel.cpp
-rw-r--r--  1 oisint oisint  3661 2008-11-16 09:58 queuemanagermodel.h
-rw-r--r--  1 oisint oisint  5714 2008-11-16 09:58 queuemanagerwidget.cpp
-rw-r--r--  1 oisint oisint  2570 2008-11-16 09:58 queuemanagerwidget.h
-rw-r--r--  1 oisint oisint  1842 2008-11-16 09:58 queuemanagerwidget.ui
-rw-r--r--  1 oisint oisint  9265 2008-11-16 09:58 recommendedsettingsdlg.cpp
-rw-r--r--  1 oisint oisint  2487 2008-11-16 09:58 recommendedsettingsdlg.h
-rw-r--r--  1 oisint oisint 10331 2008-11-16 09:58 recommendedsettingsdlg.ui
-rw-r--r--  1 oisint oisint  5764 2008-11-16 09:58 scandlg.cpp
-rw-r--r--  1 oisint oisint  3200 2008-11-16 09:58 scandlg.h
-rw-r--r--  1 oisint oisint  7668 2008-11-16 09:58 scandlg.ui
-rw-r--r--  1 oisint oisint  5612 2008-11-16 09:58 speedlimitsdlg.cpp
-rw-r--r--  1 oisint oisint  2173 2008-11-16 09:58 speedlimitsdlg.h
-rw-r--r--  1 oisint oisint  4150 2008-11-16 09:58 speedlimitsdlg.ui
-rw-r--r--  1 oisint oisint  7570 2008-11-16 09:58 speedlimitsmodel.cpp
-rw-r--r--  1 oisint oisint  2942 2008-11-16 09:58 speedlimitsmodel.h
-rw-r--r--  1 oisint oisint  3183 2008-11-16 09:58 spinboxdelegate.cpp
-rw-r--r--  1 oisint oisint  2331 2008-11-16 09:58 spinboxdelegate.h
-rw-r--r--  1 oisint oisint  4030 2008-11-16 09:58 statusbar.cpp
-rw-r--r--  1 oisint oisint  2822 2008-11-16 09:58 statusbar.h
-rw-r--r--  1 oisint oisint 10411 2008-11-16 09:58 torrentcreatordlg.cpp
-rw-r--r--  1 oisint oisint  2586 2008-11-16 09:58 torrentcreatordlg.h
-rw-r--r--  1 oisint oisint 10755 2008-11-16 09:58 torrentcreatordlg.ui
-rw-r--r--  1 oisint oisint  4842 2008-11-16 09:58 torrentmigratordlg.cpp
-rw-r--r--  1 oisint oisint  2660 2008-11-16 09:58 torrentmigratordlg.h
-rw-r--r--  1 oisint oisint  1776 2008-11-16 09:58 torrentmigratordlg.ui
-rw-r--r--  1 oisint oisint 12014 2008-11-16 09:58 trayicon.cpp
-rw-r--r--  1 oisint oisint  4372 2008-11-16 09:58 trayicon.h
-rw-r--r--  1 oisint oisint 15008 2008-11-16 09:58 view.cpp
-rw-r--r--  1 oisint oisint  4673 2008-11-16 09:58 view.h
-rw-r--r--  1 oisint oisint 17110 2008-11-16 09:58 viewmanager.cpp
-rw-r--r--  1 oisint oisint  5816 2008-11-16 09:58 viewmanager.h
-rw-r--r--  1 oisint oisint 16005 2008-11-16 09:58 viewmodel.cpp
-rw-r--r--  1 oisint oisint  5121 2008-11-16 09:58 viewmodel.h

```

---

### Post by taurus on 2008-11-25
Do you remember where you downloaded ktorrent3.2beta1?  I want to take a quick peak at it on my machine.

---

### Post by OisinT on 2008-11-25
[http://ktorrent.org/](http://ktorrent.org/)

I downloaded it from "Source code can be found [here]("http://ktorrent.org/downloads/3.2beta1/ktorrent-3.2beta1.tar.bz2")"

---

### Post by taurus on 2008-11-25
Okay, from their website, you have to do something like

```

cd ~/Desktop/ktorrent-3.2beta1
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
make
sudo make install

```

[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads)

---

### Post by OisinT on 2008-11-25
I saw that when I was first trying to install... I'll show you exactly what happens... essentially it works fine until I try to make and it says not found:

```
oisint@OisinT1:~$ cd ~/Desktop/ktorrent-3.2beta1
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1$ mkdir build
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1$ cd build
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
CMake Error: The source directory "/home/oisint/Desktop/ktorrent-3.2beta1/build" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ 
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by OisinT on 2008-11-25
so then i just thought "what if i move the Cmake file from the main folder and run that command...

```
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`..
-- The C compiler identification is GNU

-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake-qt4)
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found
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
-- Found X11: /usr/lib/libX11.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found Phonon: /usr/lib/libphonon.so
-- Found Phonon Includes: /usr/include/KDE;/usr/include
-- Found KDE 4.1 include dir: /usr/include
-- Found KDE 4.1 library dir: /usr/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Found GMP: /usr/include
-- KDE CMake PKGCONFIG macro indicates that qca2 is not installed on your computer.
-- Install the package which contains qca2.pc if you want to support this feature.
-- Could NOT find QCA2 includes
-- Could NOT find QCA2 libraries
CMake Error at /usr/share/kde4/apps/cmake/modules/FindQCA2.cmake:60 (message):
  Could NOT find QCA2
Call Stack (most recent call first):
  CMakeLists.txt:5 (find_package)


-- Configuring done
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ 
oisint@OisinT1:~/Desktop/ktorrent-3.2beta1/build$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by igknighted on 2008-11-25
You probably need the development files for KDE4 and qt4... not sure what they are named in ubuntu (probably qt4-dev and kdebase-dev).  More might be required.

EDIT: What's wrong with ktorrent 3.1.2 in the repo's?

---

### Post by OisinT on 2008-11-25
3.1.2 is majorly buggy and they've updated it to 3.1.5 which is supposed to fix the problems.  My main reason for wanting to go to 3.2beta1 is that 3.2 reintroduces rss feeds and I have to have that.

I'll try installing qt4-dev and see if that helps.  I already have kdebase-dev installed.

 thanks

---

### Post by igknighted on 2008-11-25
> **OisinT said:**
> 3.1.2 is majorly buggy and they've updated it to 3.1.5 which is supposed to fix the problems.  My main reason for wanting to go to 3.2beta1 is that 3.2 reintroduces rss feeds and I have to have that.

I'll try installing qt4-dev and see if that helps.  I already have kdebase-dev installed.

 thanks

Hmm.  Compiling KDE software can be difficult at times (kdenlive, for example), due to how they all tie in together so much.  FWIW, I looked at the dependencies for 3.1.4 in Jaunty and it requires kde>=4.1.7x (kde4.2, pre-alpha), so you might not be able to get ktorrent 3.2 on the old branch of KDE4.  At least without compiling the new libraries to load just for ktorrent.

---

### Post by igknighted on 2008-11-25
That error in your last compile attempt says it is missing libqca2, which is a crypto library.  Try installing libqca2 and libqca2-dev

---

### Post by ctarwater on 2008-11-25
This is how I got it running under Intrepid (gnome)
(it's also posted on the Ktorrent forums)


1. open a terminal

2.
**Code:**
sudo apt-get install ktorrent
(this step is only necessary if you run gnome instead of kde4. It will install all the pretty icons and make sure it looks right when running under gnome)

3.
**Code:**
sudo apt-get install build-essential

4.
**Code:**
sudo apt-get install automake

5.
**Code:**
sudo apt-get build-dep ktorrent

6.
**Code:**
sudo apt-get install libboost-dev


7.
**Code:**
sudo gedit /usr/share/kde4/apps/cmake/modules/KDELibsDependenciesInternal.cmake
(replace 'gedit' with your text editor- kate, etc)

8.
[B]
change:[/B]
SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

**to:**
SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/usr/lib/libkdecore.so;")


**change:**
SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

**to:**
SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/usr/lib/libQtGui.so;general;/usr/lib/libkdecore.so;")

(see [this]("https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/299270") post about the bug dealt with by the above changes if you're curious about it)

9. download the source and extract it to your home folder.

10.
**Code:**
cd ktorrent-3.2beta1

11.
**Code:**
mkdir build

12.
**Code:**
cd build

13.
**Code:**
cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..

14.
**Code:**
make -j4

15.
**Code:**
sudo make install

---

### Post by OisinT on 2008-11-25
I don't have 
SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

or

SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")


I do have:
 SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/build/buildd/kde4libs-4.1.2/obj-x86_64-linux-gnu/lib/libkdecore.so;")

and

 SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/build/buildd/kde4libs-4.1.2/obj-x86_64-linux-gnu/lib/libkdecore.so;")


any advice on what to change those to?

---

### Post by ctarwater on 2008-11-25
you know what, looking at mine (I'm running a 64 bit version too) I had the same one's you did.  The steps I copied from were originally for a 32 bit system though.

Anyway, change them according to the steps and it should work fine (it worked for me)

---

### Post by OisinT on 2008-11-25
> **ctarwater said:**
> you know what, looking at mine (I'm running a 64 bit version too) I had the same one's you did.  The steps I copied from were originally for a 32 bit system though.

Anyway, change them according to the steps and it should work fine (it worked for me)
It worked!  You are an absolute legend.  Thanks

---

### Post by ctarwater on 2008-11-25
Glad to help, I love kTorrent and it took me more than a few hours of scavenging through various forums and pulling bits and pieces from each to manage to get the damn thing to work...but the new version is great!

**note**

to get rid of the annoying "kwallet launcher" and "httpcachecleaner" popups: create a file called "klaunchrc" with the following text:

[FeedbackStyle]
TaskbarButton=false

and move it to: ~/.kde/share/config/klaunchrc 
(thanks to the poster [here]("http://ubuntuforums.org/showthread.php?t=962982&highlight=ktorrent"), I modified their suggestions to fit with this tutorial)

---

