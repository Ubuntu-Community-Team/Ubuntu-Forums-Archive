---
title: "Ubuntu Breezy + Qt4"
date: 2006-02-28
forum: Programming Talk
---

### Post by goofeedude on 2006-02-28
Hello,
 I currently dual boot Windows XP Pro and Ubuntu 5.10. I am a computer science student, and my current CS class is Software Construction (learning c++). For an upcoming project we have the option of implementing our program's gui in c++ (using Qt4) or java (using awt and swing). I would rather do Qt for the experience and because I feel Qt can offer a better look n' feel than swing (and perhaps a little more snappy feel).

I installed the Qt package for Windows in XP Pro, and it is awesome. When installed, it created some start menu entries for a Qt command prompt (basically a cmd window setup with certain environment variables) and entries for Qt Designer, documentation, and demos.The package came with an app which is sort of a front end to all sorts of awesome Qt documentation. It is so well documented! There are code examples, tutorials and demos, all with the source code there to examine and learn from, all packaged neatly in an easy-to-navigate interface. It's a great learning experience.

I would like to do my development in Ubuntu though, and was curious if the breezy package of libQt4-dev includes the Qt examples and tutorials interface (which is currently invaluable to me as I learn more of Qt.) 

If the breezy packages in the repositories don't have the tutorials I want, I am considering installing it from the package for X11 available at trolltech.com, and if anyone here has experience with that (and could give me some tips), that would be awesome.

Thanks for your time! Any tips greatly appreciated :-)

---

### Post by asimon on 2006-03-01
The libqt4-dev package neither contains the examples and tutorials nor the documentation. They come in extra packages.

So probably you want the packages: qt4-dev-tools and qt4-doc.
The examples for Qt3 are in a package qt3-examples but there seems to be no such packages for Qt4 (probably an oversight from the packagers).

See [Ubuntu Packages](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=qt4&searchon=names&subword=1&version=breezy&release=all) for a list of all qt4 packages for Breezy.

The Qt4 version in Breezy is quite old (4.0.0). The current version is 4.1.1, so if you want to use that I recommend to download the source from [Troll Tech](http://www.trolltech.com/download/qt/x11.html) and compile it yourself. In that case you want to install the build dependencies for Qt4 beforehand, i.e. something like 'sudo apt-get build-dep qt4-dev-tools libqt3-mt-mysql libqt3-mt-sqlite'

---

### Post by goofeedude on 2006-03-01
Thanks a ton, that's the info I needed to know! I'll reply later with how it turned out.

Edit(March 11, 2006): I used Synaptic to install the dependencies I need by first selecting libqt4-dev for installation, and choosing "Yes" to mark all the dependencies for installation as well. Then I unmarked libqt4-dev for installation, and hit Apply. This installed all the neccessary files to compile the qt package from [http://trolltech.com](http://trolltech.com). I did a default install using the directions supplied by TrollTech. It all works fine!

---

