---
title: "CMake Compile Errors"
date: 2008-03-07
forum: Programming Talk
---

### Post by xelapond on 2008-03-07
I am trying to compile some plasmoids for my KDE4 desktop from KDE-Look.

Every time I run the Cmake command I get the following output:
```
alex@Andromeda:~/system_status/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=$KDEDIR
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/alex/system_status/build/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/alex/system_status/build/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/alex/system_status/build/CMakeFiles/CMakeTmp/testCCompiler.c
/home/alex/system_status/build/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error: stdio.h: No such file or directory
/home/alex/system_status/build/CMakeFiles/CMakeTmp/testCCompiler.c: In function &#8216;main&#8217;:
/home/alex/system_status/build/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make[1]: Leaving directory `/home/alex/system_status/build/CMakeFiles/CMakeTmp'
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
alex@Andromeda:~/system_status/build$
```

What do I need to do to get CMake working so I can properly compile it?  

Just for reference I am compiling the coremoid widget, is can be found [here]("http://www.kde-look.org/content/show.php/System+Status?content=74891").

Thanks, 

Alex

---

### Post by PaulFr on 2008-03-08
Could you try installing **build-essential** and retry ? ```
sudo apt-get install build-essential
```

---

### Post by xelapond on 2008-03-08
Thanks, it got a little further that time.  Now, when I try and run the CMake command is gives me the following output.
```
alex@Andromeda:~/Desktop/system_status/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=$KDEDIR
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
CMake Error: ERROR: cmake/modules/FindKDE4Internal.cmake not found in /home/alex/.kde4/share/apps;/usr/lib/kde4/share/kde4/apps
-- Configuring done
```

Any further idea?

Thanks, 

Alex

---

### Post by stevescripts on 2008-03-08
do you have cmake installed?

Hope this helps.

Steve

---

### Post by PaulFr on 2008-03-08
I would suggest```
sudo apt-get install apt-file
``` Then when you get any **not found** errors, you can issue```
apt-file search <filename>
```where you replace <filename> with the name indicated as not being found.

For example, in your case, **FindKDE4Internal.cmake** was not found. So I run **apt-file search FindKDE4Internal.cmake** and get > kdelibs5-dev: /usr/lib/kde4/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake
So you may not have **kdelibs5-dev** installed.

Hope this helps.

---

### Post by xelapond on 2008-03-09
Ok, so I got apt-file and apted kdelibs5-dev, and now its complaining about yet more things:

```
alex@Andromeda:~/Desktop/system_status/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=$KDEDIR
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.3.2 (using /usr/bin/qmake)
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
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_NO_THREADSAFE_STATICS
-- Performing Test __KDE_HAVE_NO_THREADSAFE_STATICS - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.0 include dir: /usr/lib/kde4/include
-- Found KDE 4 library dir: /usr/lib/kde4/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/lib/kde4/bin/kconfig_compiler
-- Found KDE4 automoc: /usr/lib/kde4/bin/kde4automoc
CMake Error: Could not find REQUIRED package Plasma
-- Configuring done
```

I apt-filed plasma, nothing happened.  Plasma is not in the repositories, but I assume its installed because I can use Plasmoids, and the desktop background.

---

### Post by PaulFr on 2008-03-09
When it says package missing, you should try ```
aptitude search <pkgname>
``` So in your case, **aptitude search plasma** leads me to **libplasma-dev**. Please check if this is installed.

---

### Post by mszczuj on 2008-04-29
also done:

```
sudo apt-get install libphonon-dev
```

... and works like a charm

---

### Post by jaims on 2008-08-02
That **solved** the issue for me too, trying to build a plasmoid too...

Thanks!

---

### Post by cptr13 on 2008-09-12
this helped me work through these same errors.  Thanks to all on this thread

---

### Post by mkwerner on 2008-10-03
Thanks all - had the same issue (trying to build a plasmoid) and this worked wonderfully!

Cheers,
m.

---

### Post by maqix on 2008-10-07
Hi to all! I'm an italian 15'boy, so my english is orrible... i'm sorry for this...

When i try to compile a plasmoid, the [Weather plasmoid]("http://www.kde-look.org/content/show.php/Weather+Plasmoid?content=84251&PHPSESSID=0c983cd24bc48c078d05438e988e20a7"), i have an error, and this error was show me for all other plasmoid too...

```
make[2]: *** [lib/plasma_applet_weather.so] Error 1
make[1]: *** [CMakeFiles/plasma_applet_weather.dir/all] Error2
make: *** [all] Error 2

```

I hope you help me, and sorry for my uncorrect english :(

---

### Post by Zugzwang on 2008-10-07
> **maqix said:**
> ```
make[2]: *** [lib/plasma_applet_weather.so] Error 1
make[1]: *** [CMakeFiles/plasma_applet_weather.dir/all] Error2
make: *** [all] Error 2

```


We need to see the first error that occurred, but you truncated it. "Error 1" basically means that "something above went wrong - see above for details".

---

### Post by maqix on 2008-10-07
I' don't understand (for my bad english:confused::() the final part of yout post, but I understand that i must post the complete error, so I post all the operation i make on Konsole

```
maqixkde4@trikko:~$ cd Scrivania
maqixkde4@trikko:~/Scrivania$ cd weather
maqixkde4@trikko:~/Scrivania/weather$ cd build
maqixkde4@trikko:~/Scrivania/weather/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..                        
-- Found Qt-Version 4.4.1 (using /usr/bin/qmake)             
-- Found X11: /usr/lib/libX11.so                             
-- Found KDE 4.2 include dir: /opt/kde4/include              
-- Found KDE 4.2 library dir: /opt/kde4/lib                  
-- Found KDE4 kconfig_compiler preprocessor: /opt/kde4/bin/kconfig_compiler                                               
-- Found automoc4: /opt/kde4/bin/automoc4                    
-- Configuring done                                          
-- Generating done                                           
-- Build files have been written to: /home/maqixkde4/Scrivania/weather/build                                              
maqixkde4@trikko:~/Scrivania/weather/build$ make             
Linking CXX shared module lib/plasma_applet_weather.so                                         
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `Plasma_Weather::parseData()':
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:106: undefined reference to `QDomDocument::QDomDocument(QString const&)'                                                                                 
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:110: undefined reference to `QDomDocument::setContent(QIODevice*, QString*, int*, int*)'                                                                 
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:113: undefined reference to `QDomDocument::documentElement() const'                                                                                      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:115: undefined reference to `QDomNode::firstChild() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:117: undefined reference to `QDomNode::firstChild() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:117: undefined reference to `QDomNode::operator=(QDomNode const&)'                                                                                       
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:117: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:118: undefined reference to `QDomNode::firstChild() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:118: undefined reference to `QDomNode::operator=(QDomNode const&)'                                                                                       
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:118: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:164: undefined reference to `QDomNode::nextSibling() const'                                                                                              
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:164: undefined reference to `QDomNode::operator=(QDomNode const&)'                                                                                       
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:164: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `~QDomElement':                     
/usr/include/qt4/QtXml/qdom.h:478: undefined reference to `QDomNode::~QDomNode()'                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `Plasma_Weather::parseData()':      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:120: undefined reference to `QDomNode::isNull() const'                                                                                                   
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:122: undefined reference to `QDomNode::toElement() const'                                                                                                
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:124: undefined reference to `QDomNode::isNull() const'                                                                                                   
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:126: undefined reference to `QDomElement::tagName() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:128: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:129: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:130: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:132: undefined reference to `QDomElement::tagName() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:134: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:165: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `~QDomElement':                     
/usr/include/qt4/QtXml/qdom.h:478: undefined reference to `QDomNode::~QDomNode()'                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `Plasma_Weather::parseData()':      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:165: undefined reference to `QDomDocument::~QDomDocument()'                                                                                              
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:136: undefined reference to `QDomElement::tagName() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:138: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:140: undefined reference to `QDomElement::tagName() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:142: undefined reference to `QDomNode::firstChild() const'                                                                                               
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:142: undefined reference to `QDomNode::operator=(QDomNode const&)'                                                                                       
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:142: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:157: undefined reference to `QDomNode::nextSibling() const'                                                                                              
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:157: undefined reference to `QDomNode::operator=(QDomNode const&)'                                                                                       
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:157: undefined reference to `QDomNode::~QDomNode()'                                                                                                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `~QDomElement':                     
/usr/include/qt4/QtXml/qdom.h:478: undefined reference to `QDomNode::~QDomNode()'                      
CMakeFiles/plasma_applet_weather.dir/plasma-weather.o: In function `Plasma_Weather::parseData()':
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:144: undefined reference to `QDomNode::isNull() const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:146: undefined reference to `QDomNode::toElement() const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:148: undefined reference to `QDomNode::isNull() const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:150: undefined reference to `QDomElement::tagName() const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:152: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:153: undefined reference to `QDomElement::attribute(QString const&, QString const&) const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:160: undefined reference to `QDomNode::parentNode() const'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:160: undefined reference to `QDomNode::operator=(QDomNode const&)'
/home/maqixkde4/Scrivania/weather/plasma-weather.cpp:160: undefined reference to `QDomNode::~QDomNode()'
collect2: ld returned 1 exit status
make[2]: *** [lib/plasma_applet_weather.so] Error 1
make[1]: *** [CMakeFiles/plasma_applet_weather.dir/all] Error 2
make: *** [all] Error 2
maqixkde4@trikko:~/Scrivania/weather/build$

```

Thank for the interesting and for the speed :)

---

### Post by brandonblm on 2008-10-10
I have done everything said and it seems to be helping, but this is the error that I get now....

brandon@brandon-desktop ~/Desktop/weather/build $ make install
[100%] Built target plasma_applet_weather
Install the project...
-- Install configuration: "Debugfull"
-- Installing: /usr/lib/kde4/lib/kde4/plasma_applet_weather.so
CMake Error at cmake_install.cmake:42 (FILE):
  file INSTALL cannot copy file
  "/home/brandon/Desktop/weather/build/lib/plasma_applet_weather.so" to
  "/usr/lib/kde4/lib/kde4/plasma_applet_weather.so".


make: *** [install] Error 1

Can anyone help with this?

---

### Post by Zugzwang on 2008-10-10
> **brandonblm said:**
> Can anyone help with this?

For installing stuff into the system's directories, you need root rights, so run "make install" as sudo. However, that makes removing software possibly tedious.

---

### Post by dwhitney67 on 2008-10-10
> **Zugzwang said:**
> For installing stuff into the system's directories, you need root rights, so run "make install" as sudo. However, that makes removing software possibly tedious.
In other words, don't do it!

brandonblm -

It appears that you are new to *nix.  Don't install files into your root-protected areas unless you are absolutely sure of how to maintain them, or even delete them in the future.

If you are the only user on your system, then be content to keep the plasma_applet_weather (sp?) build in your home directory and reference it from there whenever needed.

---

### Post by brandonblm on 2008-10-11
so how do I then run this weather widget? The files are located in my desktop?

---

### Post by dwhitney67 on 2008-10-11
> **brandonblm said:**
> so how do I then run this weather widget? The files are located in my desktop?
I presume you have built the application... is this correct?

Was there a resulting binary file that represents the application?  If so, run it using a gnome-terminal; something like, where of course 'appname' is a fictitious application.  Replace the name with the actual name of the application you are trying to run:
```
./appname
```

If this succeeds, then you can contemplate creating a gnome applet on your desktop.

P.S.  I recommend that you keep this application, and any files used to build it, in an area other than your desktop.  Consider creating a sub-folder within your home folder.

---

### Post by Loralor on 2008-10-23
Hello there. Totally new to Ubuntu, but getting my nose wet by trying to run some video encoders to put videos on the PSP.

I've been following instructions in [this spot (link)]("http://news.softpedia.com/news/Convert-Movies-with-subtitles-for-your-PSP-on-Ubuntu-67806.shtml"), but I jammed at the "CMAKE ." step

```
#####################################
Configure Started
#####################################
EXTRA Cflags: 
EXTRA CXXflags: 
-- <Checking for Subversion>
-- <***********************>
-- Getting svn version from /home/philippe/avidemux_2.4_branch
-- Current revision is 4494
-- <Checking for PKG-CONFIG>
-- <***********************>
-- OK /usr/bin/pkg-config
-- <Checking for LibXML2>
-- <*********************>
**CMake Error: Could not find Libxml2**
-- Configuring done

```
So I've been poking around, trying various things proposed to similar problems, including this thread. I do have many copies of the LIBXML2 file, as proven by a LOCATE command, yet CMAKE doesn't want to get throu.

Suggestions?
Thanks in advance.

---

### Post by hufemj on 2008-11-01
This really, really helped. I've been struggling with this for a couple of days and now it's fixed.

Thanks!

---

### Post by skewray on 2009-05-14
I got my plasmoid to compile by following the hints in the thread, but I cannot run it.  "make install" puts the .so in /usr/local/lib/kde4/ and the .desktop file in /usr/local/share/kde4/services/, but those directories do not appear to be in plasma's search path.  Is there a way to add new search paths to plasma, or do I have to shove these files into the kde4 system directories in order to run the plasmoid?

---

### Post by haTem on 2009-05-14
> **skewray said:**
> I got my plasmoid to compile by following the hints in the thread, but I cannot run it.  "make install" puts the .so in /usr/local/lib/kde4/ and the .desktop file in /usr/local/share/kde4/services/, but those directories do not appear to be in plasma's search path.  Is there a way to add new search paths to plasma, or do I have to shove these files into the kde4 system directories in order to run the plasmoid?

You can add /usr/local to your $KDEDIRS environment variable. One way to do this would be to add the following to your ~/.bashrc :

```

KDEDIRS=$KDEDIRS:/usr/local
export KDEDIRS

```

You will have to logout/login for this change to take effect.

Alternatively, you can simply install the files into one of the directories already set in $KDEDIRS (the specific paths will depend on your distro).


To get a list of the directories currently set:

```
echo $KDEDIRS
```

Pick one of them (most likely /usr is one of them, I'll use that as an example). Add -DCMAKE_INSTALL_PREFIX=/usr to the end of the cmake command you used while compiling the plasmoid, and make install should install it to that location instead of /usr/local.

---

### Post by skewray on 2009-05-17
I use a csh-derived shell, and the KDEDIRS environment variable appears to be unset.  Setting it has no effect.  Is there a way to change the settings from a KDE settings manager?  Rather than using -DCMAKE_INSTALL_PREFIX=/usr , is there a way to alter the cmake input file to just put the files where they belong?

Brian

---

### Post by CryptSphinx on 2009-05-24
This thread really helped with an issue I had compiling a plasmoid - thanks a lot all

---

### Post by raditzman on 2010-02-11
Thanks for the thread and tip on using apt-file to see which package has the missing file, I successfully compiled a plasmoid :)

---

### Post by genjix on 2010-04-10
the package that you all need is kde-devel. install it.

---

### Post by michelnacouzi on 2011-03-20
Thank you this method was so helpful.

---

### Post by ozone702 on 2011-03-27
> **PaulFr said:**
> I would suggest```
sudo apt-get install apt-file
``` Then when you get any **not found** errors, you can issue```
apt-file search <filename>
```where you replace <filename> with the name indicated as not being found.

For example, in your case, **FindKDE4Internal.cmake** was not found. So I run **apt-file search FindKDE4Internal.cmake** and get So you may not have **kdelibs5-dev** installed.

Hope this helps.

Thank you!  I was having trouble compiling LEMONPOS and this did the trick for me :)

---

### Post by hxcan on 2011-04-07
> **paulfr said:**
> i would suggest```
sudo apt-get install apt-file
``` then when you get any **not found** errors, you can issue```
apt-file search <filename>
```where you replace <filename> with the name indicated as not being found.

For example, in your case, **findkde4internal.cmake** was not found. So i run **apt-file search findkde4internal.cmake** and get so you may not have **kdelibs5-dev** installed.

Hope this helps.


&#38750;&#24120;&#24863;&#35874;&#12290;

---

### Post by masuch on 2011-11-05
> **PaulFr said:**
> I would suggest```
sudo apt-get install apt-file
``` Then when you get any **not found** errors, you can issue```
apt-file search <filename>
```where you replace <filename> with the name indicated as not being found.

For example, in your case, **FindKDE4Internal.cmake** was not found. So I run **apt-file search FindKDE4Internal.cmake** and get So you may not have **kdelibs5-dev** installed.

Hope this helps.

I have to add thanks , it helped me as well.

---

### Post by boddhisatva on 2012-05-25
I have read through this whole thread, but I still can't solve the problem. I get this code:

```
[pawel@pawel-desktop yawp-0.4.3]$ sudo ./install.sh
DEBUG: -DCMAKE_BUILD_TYPE=Release
UNITTESTS: 
LOGLEVEL: -DDEBUG_LOGLEVEL=Debug
LOGFILE: -DDEBUG_LOGFILE=/tmp/yawp.log

Prepare build directory...

Run cmake...
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
-- Found Qt-Version 4.8.1 (using /usr/bin/qmake)
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so;/usr/lib/x86_64-linux-gnu/libXau.so;/usr/lib/x86_64-linux-gnu/libXdmcp.so
-- Looking for XOpenDisplay in /usr/lib/x86_64-linux-gnu/libX11.so;/usr/lib/x86_64-linux-gnu/libXext.so;/usr/lib/x86_64-linux-gnu/libXau.so;/usr/lib/x86_64-linux-gnu/libXdmcp.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Found X11: /usr/lib/x86_64-linux-gnu/libX11.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE 
-- Looking for _POSIX_TIMERS
-- Looking for _POSIX_TIMERS - found
-- Found Automoc4: /usr/bin/automoc4 
-- Found Perl: /usr/bin/perl 
-- Found Phonon: /usr/include 
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.8 include dir: /usr/include
-- Found KDE 4.8 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- CMAKE_BUILD_TYPE: Release
-- CMAKE_C_FLAGS:  -Wno-long-long -std=iso9899:1990 -Wundef -Wcast-align -Werror-implicit-function-declaration -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -Wformat-security -Wmissing-format-attribute -fno-common
-- CMAKE_SKIP_RPATH: NO
-- DEBUG_LOGLEVEL: Debug
-- DEBUG_LOGFILE: /tmp/yawp.log
-- yaWP sevice install dir: share/kde4/services
-- yaWP plugin install dir: lib/kde4
-- yaWP application install dir: share/kde4/apps
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error at po/CMakeLists.txt:6 (MESSAGE):
  Please install the msgfmt binary


-- Configuring incomplete, errors occurred!
CMake failed. Your system probably does not meets all requirements.

```

I've run **apt-file search** and **aptitude search** on the items not found, but no message is returned. **echo $KDEDIRS** returns nothing as well. I've installed a **msgfmt library**, but the terminal asks for **msgfmt binary**, which is not in the Ubuntu package list. 
I've never succeeded in compiling a package despite meticulously following directions (I've tried a dozen times), and this seems to be just another case... 
WTF?

---

### Post by GeneralZod on 2012-05-25
> **boddhisatva said:**
> I have read through this whole thread, but I still can't solve the problem. I get this code:


I've run **apt-file search** and **aptitude search** on the items not found, but no message is returned. **echo $KDEDIRS** returns nothing as well. I've installed a **msgfmt library**, but the terminal asks for **msgfmt binary**, which is not in the Ubuntu package list. 
I've never succeeded in compiling a package despite meticulously following directions (I've tried a dozen times), and this seems to be just another case... 
WTF?

You don't mention trying:

```

sudo apt-get install gettext

```

---

