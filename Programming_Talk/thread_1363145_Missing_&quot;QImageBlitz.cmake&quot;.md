---
title: "Missing &quot;QImageBlitz.cmake&quot;"
date: 2009-12-24
forum: Programming Talk
---

### Post by Hellkeepa on 2009-12-24
HELLo!

As my previous thread stated, I'm trying to compile PHP-Qt on my system (Kubuntu 9.10, 64 bit). While I've gotten it to configure against Zend Server, it seems there's some issues with the KDE packages installed by Kubuntu. The source I'm trying to compile from the following repo:
```
svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdebindings/php/phpqt
```
However, when running cmake on this version (after [fixing the PHP-paths](http://ubuntuforums.org/showthread.php?t=1358314)), I get the following error:
```
CMake Error at smoke/qimageblitz/CMakeLists.txt:2 (find_package):
  Could not find module FindQImageBlitz.cmake or a configuration file for
  package QImageBlitz.

  Adjust CMAKE_MODULE_PATH to find FindQImageBlitz.cmake or set
  QImageBlitz_DIR to the directory containing a CMake configuration file for
  QImageBlitz.  The file will have one of the following names:

    QImageBlitzConfig.cmake
    qimageblitz-config.cmake
```
Now, I've installed both the "QImageBlitz4" and "QImageBlitz-dev" packages, verified that the header files are present, but no .cmake file on my system at all. (Even tried find / -iname "*qimageblitz*")
Searching the net gave me precious little, only one forum thread for compiling Dolphin under gnome, and one blog post about compiling Dolphin under OpenSUSE 11.2. Neither of which were of any help, as the closest I got to an answer was "recompile KDE from SVN repo".

Anyone that has any ideas on how/where I can generate/find this missing file, or the least invasive method of getting things to compile? If so, it would be of great assistance, and highly appreciated.

Happy codin'!

---

### Post by BionicSeahorse on 2010-01-02
Having the same issue as the OP. Any advice would be greatly appreciated!

---

### Post by Hellkeepa on 2010-01-03
HELLo!

I did work around that particular issue, I think I copied the file from somewhere else. However, I soon found that I was getting a whole lot of errors about virtual methods not being implemented. Seems the SVN from Berlios is for an older version of KDE, and as such does not compile against KDE 4.3.

Pulled the newest SVN from kde.org, and tried to compile it from that source. After some more issues along this line, I finally got to the point where it complained about the following:
> Unknown CMake command "kde4_add_library".
And that's where I'm stuck now...

Seems like the SVN from the official home page ([www.php-qt.org](www.php-qt.org)) is only meant to be compiled as a part of the whole of KDE. :-(

Happy codin'!

---

### Post by BionicSeahorse on 2010-01-04
I believe you can get around that error by including KDE in your CMakeLists.txt like so:

```
find_package(KDE4 REQUIRED)
```

Let me know if that works out for you!

---

### Post by Hellkeepa on 2010-01-05
HELLo!

Thanks for the tip, I'll investigate it as soon as I have time to sit down with this again. (Having to work kind of sucks at times. :-\ )

Happy codin'!

---

