---
title: "libraries in ubuntu development c++ using qt"
date: 2011-12-14
forum: Programming Talk
---

### Post by shubham1 on 2011-12-14
hi all,
i am trying to develope for ubuntu i have read every thing on [http://developer.ubuntu.com/](http://developer.ubuntu.com/)
also i have read the forum stickies
i am using qt creator to create applications i want to know the right of way of using libraries for ubuntu like opengl , gtk+
do i have to bundle these libraries in my software or they will be else where package for eg. if i want to use opengl
i am asking this because i have heard about dependencies in ubuntu software packages
please do not provide links of ubuntu.com or from sticky i have read them all but i have not get so i am asking for help

---

### Post by Zugzwang on 2011-12-14
In Ubuntu Linux, it is custom *not* to bundle libraries with your application. Rather, when you later deploy your application, you build a .deb source package of your application and list all dependencies (libraries and external programs that you use) in a special control file. From this source package, you can build a package that contains the compiled version of your program. 
For any user who wants to install your program, the package manager will then ensure that the necessary libraries and programs are automatically installed.

As an example, direct your browser here: [http://packages.ubuntu.com/oneiric/epiphany](http://packages.ubuntu.com/oneiric/epiphany) - You will see on the right-hand side of the screen that you can download source code packages. The one is the source code as it can be obtained from the developers. The file epiphany_0.7.0-5.debian.tar.gz contains additional information for making a debian package. In particular, it contains control files for compiling the program and dependency lists.

---

### Post by shubham1 on 2011-12-15
> **Zugzwang said:**
> In Ubuntu Linux, it is custom *not* to bundle libraries with your application. Rather, when you later deploy your application, you build a .deb source package of your application and list all dependencies (libraries and external programs that you use) in a special control file. From this source package, you can build a package that contains the compiled version of your program. 
For any user who wants to install your program, the package manager will then ensure that the necessary libraries and programs are automatically installed.

As an example, direct your browser here: [http://packages.ubuntu.com/oneiric/epiphany](http://packages.ubuntu.com/oneiric/epiphany) - You will see on the right-hand side of the screen that you can download source code packages. The one is the source code as it can be obtained from the developers. The file epiphany_0.7.0-5.debian.tar.gz contains additional information for making a debian package. In particular, it contains control files for compiling the program and dependency lists.
thanks so how do a use libraries in qt creator so can i create corss platform for the same code
is there any other editor which is very good for ubuntu development avoid:eclipse , netbeans
gtk+ vs qt library for graphical interface compare for each of these
ubuntu , linux
cross platform
mobile operating system

---

### Post by Zugzwang on 2011-12-15
> **shubham1 said:**
> thanks so how do a use libraries in qt creator so can i create corss platform for the same code


See the documentation: [http://doc.qt.nokia.com/qtcreator-2.3/creator-project-qmake-libraries.html](http://doc.qt.nokia.com/qtcreator-2.3/creator-project-qmake-libraries.html)

---

### Post by shubham1 on 2011-12-15
> **Zugzwang said:**
> See the documentation: [http://doc.qt.nokia.com/qtcreator-2.3/creator-project-qmake-libraries.html](http://doc.qt.nokia.com/qtcreator-2.3/creator-project-qmake-libraries.html)
read it many times cant get my anwser how to inculde an external libraray my question is to use libraries in ubuntu wether i am using gedit what to define or something else

---

### Post by Zugzwang on 2011-12-15
> **shubham1 said:**
> read it many times cant get my anwser how to inculde an external libraray my question is to use libraries in ubuntu wether i am using gedit what to define or something else

Please improve on your grammar, punctuation and spelling. Normally, complaining about this would be a bit picky, but you have reached a level such that we can only guess what you mean here.

So I'm gonna answer the question for which I *think* that you have been asking.

If you build an application in Linux, then you typically employ some build system to automate this task for you. If you now want to use a library in your program, you've got to your build system which libraries you are using, so that this system can pass the necessary parameters to the compiler and the linker. How to do so depends on the choice of your build system.

Different IDEs typically support only a fraction of the available build systems in Linux. The QTCreator for example uses "qmake", which I personally find easy to use. If you use gedit, since this is only an editor and you compile from the terminal anyway, you can use any system you like.

If you use QTCreator and/or qmake, then you will specify the libraries that you need in a .pro project file. The QTCreator "add library" dialog will automatically edit this project file for you. You can however also do it by hand. There is some information in the [qmake Manual]("http://developer.qt.nokia.com/doc/qt-4.8/qmake-project-files.html") that you can use.

There is no way of adding a library to your compilation process that is build-system independent (if you consider compiling by hand also to be some kind of build system).

---

### Post by shubham1 on 2011-12-16
> **Zugzwang said:**
> Please improve on your grammar, punctuation and spelling. Normally, complaining about this would be a bit picky, but you have reached a level such that we can only guess what you mean here.

So I'm gonna answer the question for which I *think* that you have been asking.

If you build an application in Linux, then you typically employ some build system to automate this task for you. If you now want to use a library in your program, you've got to your build system which libraries you are using, so that this system can pass the necessary parameters to the compiler and the linker. How to do so depends on the choice of your build system.

Different IDEs typically support only a fraction of the available build systems in Linux. The QTCreator for example uses "qmake", which I personally find easy to use. If you use gedit, since this is only an editor and you compile from the terminal anyway, you can use any system you like.

If you use QTCreator and/or qmake, then you will specify the libraries that you need in a .pro project file. The QTCreator "add library" dialog will automatically edit this project file for you. You can however also do it by hand. There is some information in the [qmake Manual]("http://developer.qt.nokia.com/doc/qt-4.8/qmake-project-files.html") that you can use.

There is no way of adding a library to your compilation process that is build-system independent (if you consider compiling by hand also to be some kind of build system).
thanks i got it :)

---

