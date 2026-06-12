---
title: "[SOLVED] Qt Tutorial 1 - &amp;quot;Hello World&amp;quot; compile errors"
date: 2008-03-12
forum: Programming Talk
---

### Post by jonathanmotes on 2008-03-12
I'm trying to learn to use qt, starting with the example qt code at [http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html). I've installed everything that was asked for when I tried to compile the first time (libqt4-dev and qt3-dev-tools), and I have build-essential. 

Here's the code:
```

 #include <QApplication>
 #include <QPushButton>

 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);

     QPushButton hello("Hello world!");
     hello.resize(100, 30);

     hello.show();
     return app.exec();
 }


```

I run these commands:
```
 
qmake -project
qmake
make
```

and I get this:```
jmotes1@dell-desktop:~/Projects/Qt/Hello_World$ sudo qmake -project
jmotes1@dell-desktop:~/Projects/Qt/Hello_World$ qmake
jmotes1@dell-desktop:~/Projects/Qt/Hello_World$ make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o main.o main.cpp
main.cpp:6:25: error: QApplication: No such file or directory
main.cpp:7:24: error: QPushButton: No such file or directory
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:11: error: &#8216;QApplication&#8217; was not declared in this scope
main.cpp:11: error: expected `;' before &#8216;app&#8217;
main.cpp:13: error: &#8216;QPushButton&#8217; was not declared in this scope
main.cpp:13: error: expected `;' before &#8216;hello&#8217;
main.cpp:14: error: &#8216;hello&#8217; was not declared in this scope
main.cpp:17: error: &#8216;app&#8217; was not declared in this scope
main.cpp: At global scope:
main.cpp:9: warning: unused parameter &#8216;argc&#8217;
main.cpp:9: warning: unused parameter &#8216;argv&#8217;
make: *** [main.o] Error 1
jmotes1@dell-desktop:~/Projects/Qt/Hello_World$
```

In case it helps, here's the files in the Hello_World directory:
```
jmotes1@dell-desktop:~/Projects/Qt/Hello_World$ ls -l
total 16
-rw-r--r-- 1 jmotes1 jmotes1  286 2008-03-12 16:50 Hello_World.pro
-rw-r--r-- 1 jmotes1 jmotes1  479 2008-03-12 15:36 main.cpp
-rw-r--r-- 1 jmotes1 jmotes1  479 2008-03-12 15:36 main.cpp~
-rw-r--r-- 1 jmotes1 jmotes1 2792 2008-03-12 16:50 Makefile
```

Any Ideas anyone?

Thanks!

---

### Post by LaRoza on 2008-03-12
Moved by request.

---

### Post by dempl_dempl on 2008-03-12
I'm using Qt for couple of years . I remember   having the same issues as you, and all because I had not used Kdevelop.  Kdevelop is your friend. It's made in Qt, and it works best with Qt.It looks pretty much like Visual Studio,  and the only difference is , as far as I'm concerned, that Kdevelop is better than VS   :-)  .   

Bassically ,  It does all of those Qt headache-parts for you. Why would you need to know to configure Qt from command-line?  Maybe some day, when you learn Qt better, but I sincerely doubt it . 

Cheers!

---

### Post by lnostdal on 2008-03-12
hmm .. i disagree .. you should always know how things work "from the command line" .. 

not everyone uses kdevelop, and you should provide build-scripts(#1) that work regardless of what IDE/editor one use .. these build-scripts can the be called from within whatever IDE/editor each user prefers

this is the proper way of doing this ... don't bring the bad ideas/practises of the "MS world", where a project is "melted into" an IDE - over to the "Linux world"

if you do not care then you do not care .. and it might not matter .. but if you want to collaborate with others then it does matter and you should care

#1: cmake or scons are nice in general when doing c or c++ type work .. maybe what qt already provides (qmake?) is a better idea here though, but the same still applies - your project should be buildable outside kdevelop

edit:
i should maybe have pointed out that a large point here is the ability for others to actually understand and change the buildscripts themselves .. this is often a problem with regards to automatically genereated buildscripts which, even though they are portable in nature, still are not maintainable outside their original environment .....

---

### Post by Roptaty on 2008-03-12
Ubuntu renames Qt4 qmake to qmake-qt4. You have to run qmake-qt4 -project and qmake-qt4, and then make... then it should successfully compile. :)

---

### Post by Jessehk on 2008-03-12
> **Roptaty said:**
> Ubuntu renames Qt4 qmake to qmake-qt4. You have to run qmake-qt4 -project and qmake-qt4, and then make... then it should successfully compile. :)


Roptaty is probably right. In Qt3, headers were named qapplication.h, qpushbutton.h, etc. In Qt4, they were renamed o to what they are now. 

In order to confirm it, type in something like:
```

$ which qmake

```

You can either type in the commands with their version like Roptaty suggested, or you can do something like this:
```

$ sudo update-alternatives --config qmake

```

to choose which version you want. :)

---

### Post by jonathanmotes on 2008-03-13
Thanks guys, it worked! I was able to configure it so that I could just enter qmake and it works just fine now.

The comments on using an IDE vs. terminal were interesting also. I personally like to use a terminal and a text editor (like gedit) for simple programming, partly because I like to know what's really going on, and also because I feel that I'm wasting time when I have to configure an IDE. However, I still use an IDE when I have to debug a complex application, and it seems to make things a lot easier for me. I will certainly look into using Kdevelop for those times.

---

### Post by gogaman on 2011-07-02
make sure the following has been run:
$ sudo apt-get libqt4-core libqt4-dev

---

