---
title: "QT Creator build error"
date: 2009-06-01
forum: Packaging and Compiling Programs
---

### Post by Caliga on 2009-06-01
Hello, after being advised by some of the good chaps on this forum to use QT Creator as my IDE (it has all the feautres I need) I downloaded and installed it. WHen trying to build a small text application I get the following build error:

:-1: error: collect2: ld returned 1 exit status

In more detail in the compile section:

 p, li { white-space: pre-wrap; }  Running build steps for project Test...
 [COLOR=#0000FF]Configuration unchanged, skipping QMake step.[/COLOR]
 [COLOR=#0000FF]Starting: /usr/bin/make -w[/COLOR] 
 make: Entering directory `/home/caliga/Test'
 g++ -Wl,-rpath,/home/caliga/qtsdk-2009.02/qt/lib -o Test main.o mainwindow.o moc_mainwindow.o -L/home/caliga/qtsdk-2009.02/qt/lib -lQtGui -L/home/caliga/qtsdk-2009.02/qt/lib -L/usr/X11R6/lib -pthread -lfreetype -lgobject-2.0 -lSM -lICE -pthread -pthread -lXrender -lfontconfig -lXext -lX11 -lQtCore -lm -pthread -lgthread-2.0 -lrt -lglib-2.0 -ldl -lpthread
 [COLOR=#FF0000]/usr/bin/ld: cannot find -lfreetype[/COLOR]
 [COLOR=#FF0000]collect2: ld returned 1 exit status[/COLOR]
 [COLOR=#FF0000]make: *** [Test] Error 1[/COLOR]
 make: Leaving directory `/home/caliga/Test'
 [COLOR=#FF0000]Exited with code 2.[/COLOR]
 [COLOR=#FF0000]Error while building project Test[/COLOR]
 [COLOR=#FF0000]When executing build step 'Make'[/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000][COLOR=Black]Any idea how to go about fixing this? IM relitively new to Linux, so baby steps would be greately apreciated. Especially if you have a simple "apt-get" answer to this :][/COLOR][/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000][COLOR=Black]Love and peace <3[/COLOR]
[/COLOR]

---

### Post by TKab on 2009-06-02
For the specific error you're getting, you'll need to run:

```
sudo apt-get install libfreetype6-dev
```

You'll get the development version of the freetype library.
You might get more errors when you try building after you install
the freetype library. Check out this link:
[http://stackoverflow.com/questions/764928/usr-bin-ld-cannot-find-lfreetype-why-and-how-can-i-make-it-work]("http://stackoverflow.com/questions/764928/usr-bin-ld-cannot-find-lfreetype-why-and-how-can-i-make-it-work")

:)

---

