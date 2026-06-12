---
title: "How to get Qt-4.x on Ubuntu 20.04?"
date: 2020-04-26
forum: New to Ubuntu
---

### Post by michael-bielesky on 2020-04-26
Hi,

A program that I'm compiling on Ubuntu 20.04 requires Qt 4. I tried installing 'qt4-default' package, but I failed because of "unmet dependencies". When attempting to install the missing dependency it also failed because of more missing dependencies and so on. Any suggestions on how to proceed here?

--Mike

---

### Post by Perfect Storm on 2020-04-26
Please post the whole terminal output of the errors. It will make it much easier to give you the help you want.

regards

---

### Post by michael-bielesky on 2020-04-26
[I]$ sudo apt install qt4-default
[/I]*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*Some packages could not be installed. This may mean that you have*
*requested an impossible situation or if you are using the unstable*
*distribution that some required packages have not yet been created*
*or been moved out of Incoming.*
*The following information may help resolve the situation:*

*The following packages have unmet dependencies:*
* qt4-default : Depends: libqt4-dev but it is not going to be installed*
*E: Unable to correct problems, you have held broken packages.*

---

### Post by michael-bielesky on 2020-04-26
From installation of the program:

$ cmake ../-- The C compiler identification is GNU 7.5.0
-- The CXX compiler identification is GNU 7.5.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- The build type is RelWithDebInfo
-- Performing Test HAVE_NO_RTTI
-- Performing Test HAVE_NO_RTTI - Success
-- Performing Test HAVE_RTTI
-- Performing Test HAVE_RTTI - Success
-- Performing Test HAVE_GCC_VISIBILITY
-- Performing Test HAVE_GCC_VISIBILITY - Success
-- Performing Test COMPILES_WITHOUT_FPERMISSIVE
-- Performing Test COMPILES_WITHOUT_FPERMISSIVE - Failed
CMake Error at /usr/share/cmake-3.16/Modules/FindQt4.cmake:1314 (message):
  Found unsuitable Qt version "5.12.8" from /usr/bin/qmake, this code
  requires Qt 4.x
Call Stack (most recent call first):
  CMakeLists.txt:226 (find_package)




-- Configuring incomplete, errors occurred!

---

### Post by guiverc on 2020-04-26
Qt4 is obsolete & EOL (15-March-2019), and coders were told in 2016 to port their code to Qt5 before it was removed from downstream systems (Ubuntu is downstream of Qt).

(Wikipedia reported EOL date was 2015 by upstream Qt; sorry I do recall *flak* over it's removal from the 19.?? releases, but I forget the specifics as was awhile ago now)

It's been years since Qt5 was introduced (19-Dec-2012) so still trying to use an obsoleted and no longer supported library isn't wise, so you should port to Qt5 asap (should have been planned years ago & already implemented).

Qt4 programs were progressively removed in 2019, and libraries were likewise removed.

FYI:  This applies to `python2` as well though it had different dates of course, and it's own timetable.

---

### Post by mIk3_08 on 2020-04-26
try the new one; which is 5.

---

### Post by oarion7 on 2020-04-26
You could go into CMakeLists.txt and change the Qt requirement to the version you have installed, thus allowing you to proceed in the compiling process, but I would expect something to break &#8211; a full number increase in version number is not insignificant. In this case, it's [not strictly major, but does involve changes in the syntax]("https://wiki.qt.io/Transition_from_Qt_4.x_to_Qt5").

You might want to share what program you're trying to install. There could be a newer version or fork or something on Github, there may be an author with an email address, or an alternate application that does something similar, etc.

---

### Post by michael-bielesky on 2020-04-26
Thanks for your comments! I will therefore abandon the idea of having Qt4 along Qt5. The program I'm trying to install is Avogadro 1.2 (molecular editor), which is the stable version and which was available from Ubuntu's 18.04 repositories. Ubuntu 20.04 comes with the beta version Avogadro 1.93.0,  which user interface I don't like and, based on online discussions elsewhere, I'm not the only one. 

--Mike

---

### Post by CelticWarrior on 2020-04-26
> Ubuntu 20.04 comes with the beta version Avogadro 1.93.0,  which user  interface I don't like and, based on online discussions elsewhere, I'm  not the only one. 


You and the other users should give feedback to the developers.

---

### Post by sourceskyboxer on 2020-04-27
I understand you want downgrade Qt 4.x ? 

Same problem with my thread here - You should switch off with "#" official repository of universal Ubuntu Focal than you can put repository of Qt 4.x than make sure with apt-mark hold all Qt 4.x before you want stay current version of Qt 4.x than switch on without "#" from official repository Ubuntu Focal.

I have same problem with Mono Runtime too.
Thanks!

---

### Post by wildmanne39 on 2020-04-27
Hello sourceskyboxer, you can bump your thread once every twelve hours to keep it in view of the volunteers here but please do not post a link to your thread in someone else's.

Thanks

---

### Post by DuckHook on 2020-04-27
The general thrust of this thread is heading off on dangerous tangents. All posters, please pay attention to guiverc's comments:

[LIST=1]
[*]Qt4 is obsolete
[*]Qt5 has been out for over five years
[*]Ubuntu devs have adhered to proper practice and nerfed Qt4 in Focal
[/LIST]
Therefore, rather than monkey around with your system apt-mark-ing critical system libraries that will only end up breaking something else, the following are far better strategies to use:

[LIST=1]
[*]If you must use an app that is built on Qt4, then don't upgrade to Focal. There's nothing wrong with running Bionic vanilla Ubuntu for another three years.
[*]If you don't have three years because you are running one of the flavours, then run Bionic in a VM and your app within the VM.
[*]If your machine is too under-powered to run VMs, then:
[LIST=a]
[*]time to upgrade HW or
[*]try the solution in my sig: "Sandboxing Apps with LXD". LXD can run container instances as far back as Trusty (14.04) and *if they are properly contained*, they pose little threat to security. However, be advised that this method has a learning curve and is not meant for newbies.
[/LIST][/LIST]
CelticWarrior also raises a good point. Make noise and ask the devs to bring this app up to date. Apps that are dependent on obsolete unmaintained libraries are just begging for trouble and are one of the reasons the Windows world continues to be such a security cesspool.

---

### Post by DuckHook on 2020-04-27
> **sourceskyboxer said:**
> I understand you want downgrade Qt 4.x ? 

Same problem with my thread here - You should switch off with "#" official repository of universal Ubuntu Focal than you can put repository of Qt 4.x than make sure with apt-mark hold all Qt 4.x before you want stay current version of Qt 4.x than switch on without "#" from official repository Ubuntu Focal.

I have same problem with Mono Runtime too.
Thanks!
This is very bad and dangerous advice. It has a high likelihood of destroying a whole install. For proper strategy, see [my post above]("https://ubuntuforums.org/showthread.php?t=2441709&p=13951301#post13951301").

---

### Post by michael-bielesky on 2020-06-06
Hi,
Thanks for your reply. I'm new to Linux so kindly let me know if my understanding is correct. The <apt-mark> will set the qt 4.x files/directories to manual which will prevent for example <apt-get auto-remove> from deleting them? Do I use for example <find> to search for all qt 4 files and then apply apt-mark on them? 

I also found this: [https://askubuntu.com/questions/1234786/qt4-libqt4-in-ubuntu-20-04](https://askubuntu.com/questions/1234786/qt4-libqt4-in-ubuntu-20-04)

--Mike

---

### Post by michael-bielesky on 2020-06-06
I just saw that there are replies on a 2nd page. Ok, so I'm not going to proceed with that suggestion. What do thin about this though: [COLOR=#000000] [/COLOR][https://askubuntu.com/questions/1234...n-ubuntu-20-04]("https://askubuntu.com/questions/1234786/qt4-libqt4-in-ubuntu-20-04")

---

### Post by monkeybrain20122 on 2020-06-06
> **michael-bielesky said:**
> I just saw that there are replies on a 2nd page. Ok, so I'm not going to proceed with that suggestion. What do thin about this though: [https://askubuntu.com/questions/1234...n-ubuntu-20-04]("https://askubuntu.com/questions/1234786/qt4-libqt4-in-ubuntu-20-04")

That should be ok but make sure that it doesn't mess up your qt default for otherwise it may have unintended effects(or you have a hard time if you try to build something else with qt5 in the future) qt-chooser presumably allows you to choose which qt but it is notoriously unreliable and since qt4 is gone this may not be in the repo. 

If I were you I would just compile qt-4 from source in my $HOME directory (let's say you install qt4 in $HOME/qt4) and then build my qt4 app with environmental variables like these . 

```
export PATH=$HOME/qt4/bin:$PATH
export PKG_CONFIG_PATH=$HOME/qt4/lib/pkgconfig
export QT_LIBS= $HOME/qt4/lib
export QT_CFLAGS=$HOME/qt4/include
export LD_LIBRARY_PATH=$HOME/qt4/lib:$LD_LIBRARY_PATH

```
If your app doesn't start afterwards export LD_LIBRARY_PATH (last one above) before you invoke the app if you run in the terminal, or
prepend the Exec line in your .desktop file with env LD_LIBRARY_PATH=$HOM/qt4/lib if you use a desktop launcher, so it reads
```
Exec=env LD_LIBRARY_PATH=$HOM/qt4/lib /path/to/your/executable
```

Don't mess with your .bashrc like some forums suggest.

You can get the source [here]("https://download.qt.io/archive/qt/4.8/"), get the qt4-everywhere-opensource-src archive.

qt is straight forward to compile but may take hours depending on how fast your machine is. I think you can also download pre compiled qt libraries from the website then you are all set (at least for qt5, not sure about qt4 though, but may need to adjust the paths above when you compile your app.) You need to google a bit.

I use this method to compile qt5 apps which require higher versions of qt5 than in Ubuntu, it works the same way if you need qt4.

---

