---
title: "QT4 Designer uic doesn't work"
date: 2007-03-23
forum: Programming Talk
---

### Post by ramiro on 2007-03-23
hey all,

I'm trying to create a QT app using qt4 designer. I've created a simple window and I'm trying to compile it, I run

ramiro@sasha:~/edi/src/designer$ uic -o main.h main.ui

with no issues. When I try to create an implementation file, however, I get this:

ramiro@sasha:~/edi/src/designer$ uic -impl main.h -o main.cpp main.ui
Qt User Interface Compiler version 4.2.3
Usage: uic [options] <uifile>

  -h, -help                 display this help and exit
  -v, -version              display version
  -d, -dependencies         display the dependencies
  -o <file>                 place the output into <file>
  -tr <func>                use func() for i18n
  -p, -no-protection        disable header protection
  -g <name>                 change generator

obviously it's not recognising the -impl option, despite the fact that it's exactly as written in the man pages. I even copy/pasted the example make file that is in the man page and ran that with the same issue when I tried to create the implementation file. 

I tried with -impl, -i (as is said in the trolltech website), --impl, but nothing worked. What's the deal here?

I'm running feisty fawn.

---

### Post by ramiro on 2007-03-24
oh yeah, I checked and made sure that the given files were in the current directory. I even tried giving absolute paths to the files. Nothing seems to be working.

As far as I can tell, it's a bug in uic. Does anyone else have this software and want to test it out (sudo apt-get install qt4-designer)

---

### Post by Faryshta on 2008-04-22
Hi. I have the same problem you do.

I hope you could solve it, and please explain me how did you

---

### Post by thornmastr on 2008-04-23
Perhaps you both might want to look closely at QDEVELOP at [http://qdevelop.org](http://qdevelop.org). It might simplify your issues with QT4.

Robert

---

### Post by Lau_of_DK on 2008-04-24
> **ramiro said:**
> hey all,

I'm trying to create a QT app using qt4 designer. I've created a simple window and I'm trying to compile it, I run

ramiro@sasha:~/edi/src/designer$ uic -o main.h main.ui


Hey,

First off I ould highly recommend integrating Qt in Eclipse or alternatively MonkeyStudio or QDevelop (though I had some problems with them both). Secondly you should be able to build any Qt project by

```

qmake
make
./main

```

...as qmake is a product of Qt designed to create suitable make files. If you're in eclipse however, just press "run" :)

Link to Qt's site on Eclipse integration: [http://trolltech.com/developer/downloads/qt/eclipse-integration-download]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")

/Lau

---

### Post by magick.crow on 2009-02-02
sudo aptitude install libqt4-dev

if you type uic-qt4 at the command line it comes back and says that you must install this lib. I did and now view code work!

I guess that qt-designer has an unset dependency and someone should tell someone else to fix that.

---

