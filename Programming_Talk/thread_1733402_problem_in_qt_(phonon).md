---
title: "problem in qt (phonon)"
date: 2011-04-19
forum: Programming Talk
---

### Post by Praveen30 on 2011-04-19
Hello everyone,

I have taken a class in   #ubuntu-classroom.here is the link--
[http://irclogs.ubuntu.com/2011/04/15/%23ubuntu-classroom.html]("http://irclogs.ubuntu.com/2011/04/15/%23ubuntu-classroom.html")

In this class apachelogger told us how to run an application using phonon...it was quite good.Now i am having some problem in running my first application using phonon...

```


#include <QtGui/QApplication>

#include <Phonon/AudioOutput>
#include <Phonon/MediaObject>
#include <Phonon/MediaSource>
#include <Phonon/VideoWidget>
#include <Phonon/VideoPlayer>

using namespace Phonon;

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    MediaObject mo;
    AudioOutput ao;
    createPath(&mo,&ao);
    mo.setCurrentSource(MediaSource("./first_run_jingle.ogg"));
    mo.play();
    return a.exec();
}

```when i run this application using qmake -project, qmake and make..i am getting bunch of errors..

```

praveen@ubuntu:~/phonon-template$ qmake -project
praveen@ubuntu:~/phonon-template$ qmake
praveen@ubuntu:~/phonon-template$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp:3:30: error: Phonon/AudioOutput: No such file or directory
main.cpp:4:30: error: Phonon/MediaObject: No such file or directory
main.cpp:5:30: error: Phonon/MediaSource: No such file or directory
main.cpp:6:30: error: Phonon/VideoWidget: No such file or directory
main.cpp:7:30: error: Phonon/VideoPlayer: No such file or directory
main.cpp:9: error: &#8216;Phonon&#8217; is not a namespace-name
main.cpp:9: error: expected namespace-name before &#8216;;&#8217; token
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:14: error: &#8216;MediaObject&#8217; was not declared in this scope
main.cpp:14: error: expected &#8216;;&#8217; before &#8216;mo&#8217;
main.cpp:15: error: &#8216;AudioOutput&#8217; was not declared in this scope
main.cpp:15: error: expected &#8216;;&#8217; before &#8216;ao&#8217;
main.cpp:16: error: &#8216;mo&#8217; was not declared in this scope
main.cpp:16: error: &#8216;ao&#8217; was not declared in this scope
main.cpp:16: error: &#8216;createPath&#8217; was not declared in this scope
main.cpp:17: error: &#8216;MediaSource&#8217; was not declared in this scope
make: *** [main.o] Error 1

```guys please suggest me something.....

---

### Post by &#423;uperhero on 2011-04-19
Did you add the following line to your .pro file?
```
QT += phonon
```

---

### Post by Praveen30 on 2011-04-19
> **&#423 said:**
> Did you add the following line to your .pro file?
```
QT += phonon
```

yes i have checked this,,but it is of no avail....

---

### Post by &#423;uperhero on 2011-04-19
Are you sure you installed libphonon-dev?

---

### Post by benson444 on 2011-04-19
I think the #includes should be <phonon/...> instead of <Phonon/...>

After changing them, and adding the phonon module to the .pro file, it compiled for me.

---

