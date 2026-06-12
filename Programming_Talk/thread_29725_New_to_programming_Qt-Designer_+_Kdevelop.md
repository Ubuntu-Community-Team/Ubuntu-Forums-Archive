---
title: "New to programming: Qt-Designer + Kdevelop?"
date: 2005-04-25
forum: Programming Talk
---

### Post by ahessling on 2005-04-25
Hi!

I recently installed kdevelop3 and the qt-designer and I want to create some simple programs that just depend on Qt and not KDE.
For better compatibility I wouldn't like to have a dependency on KDE. Qt would be enough.
I found some tutorials on the internet and one says that I should create a C++ project, then a main window and at last a C++ main file using the qt designer.

I did so but I get the following error:
"There is no plugin for editing C++ code installed.
Note: Plugins are not available in static Qt configurations."

But kdevelop3-plugins is installed which includes some plugins, one of them is:
/usr/lib/qt3/plugins/designer/libcppeditor.so

This directory is added to the plugin directories in the qt-designer but the error won't go away.

So what am I doing wrong?

Actually I don't even know if I want to start programming with Qt. Maybe GTK? 

Advices would be greatly appreciated. :)

Thanks!

Regards,
André

---

### Post by abhaysahai on 2005-05-06
please post the output of `dpkg -l | grep -i  kdevelop`
and 
`dpkg -l | grep -i qt`

Regards,
Abhay

---

### Post by lorap on 2005-05-09
hi friend.
you probably got used to work with microsoft visual studio.
am i right?
you know, it would be a good idea for you to understand gui programming if you start create it yourself, on your own.
kdeveloper was never good as visual studio, the same about anjuta.
moreover when i needed to write very specific applications i needed to create all windows myself so i would know what each line of code means, so from that moment i begun doing everything on my own.
the same i propose to you.
pavel

p.s.:
if you are interested in a good book on programming in linux i will propose you one teaches you not just create a gui but write drivers and even more interesting things.

---

### Post by impeteperry on 2005-09-12
I am in the learning stage of Qt programming but have programmed in Assembler, MDL (MicroStation), C, C++ & visual Bascic in PCOS, DOS and Windows in the past, however this is a whole new ballgame for me.

This is what I do when developing a program. 
1. I use Qt Designer to layout the various windows.
2. Then using "kwrite" I write  the .h and .cpp files following the layout from the "designer" files. So I am in pure  Qt.
3. Next I generate the .pro file with "qmake -project" command.
4. Then the MakeFile, again with the "qmake" command
5..Then I import the whole thing into Kdevelop and do all the  compiling, refinement and debugging there.
6. You can always delete  the .kdevelop files and you are back to a pure Qt program.

I use "C++ GUI Programming in Qt 3" and "O'Reilly's Programming with Qt"

---

### Post by odrop on 2005-09-16
The Code Skipper might be a place to check out if you'd like to read some good tutorials on Qt and KDE programming.
[http://www.codeskipper.com/](http://www.codeskipper.com/)

The Qt Designer specific section is:
[http://www.codeskipper.com/section/ss/1/s/9/](http://www.codeskipper.com/section/ss/1/s/9/)

---

