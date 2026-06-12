---
title: "Simple threading in C++?"
date: 2010-09-20
forum: Programming Talk
---

### Post by compiz addict on 2010-09-20
I want to create a simple program with a thread. I'm using QTDeveloper to make this program.

The thread is going to be a continuous loop, and I would like to have the program terminate the thread using a function.

At the moment I'm pulling hairs out of my head trying to figure this out and impatiently reading though tutorials only to find out in the end that they don't work at all.

---

### Post by s.fox on 2010-09-20
Thread moved to Programming Talk

---

### Post by Sub101 on 2010-09-20
Using QT you define a thread in the header using

```
#include <QThread>
#include <QObject>

class ThreadTry : public QThread
{
........
    Q_OBJECT
```

Where ThreadTry is the name of your class.

In the cpp file you create your program as usual and run from a run method. ie.

```
void ThreadTry::run()
```

In my opinion a must purchase to get your head around QThreads and QT in general is the QT4 book. 

[http://www.amazon.com/Programming-Prentice-Source-Software-Development/dp/0132354160/ref=pd_sim_b_3](http://www.amazon.com/Programming-Prentice-Source-Software-Development/dp/0132354160/ref=pd_sim_b_3)

---

### Post by compiz addict on 2010-09-20
So... how do I write the class?

```

class ThreadTry : public QThread
{
........
    Q_OBJECT

```

is a syntax error. Even If I put the } at the end.

Also, which CPP file do I edit? main.cpp or mainwindowimpl.cpp? Most of my code so far is in mainwindowimpl.cpp

---

### Post by Sub101 on 2010-09-20
> **compiz addict said:**
> So... how do I write the class?

```

class ThreadTry : public QThread
{
........
    Q_OBJECT

```

is a syntax error. Even If I put the } at the end.

Sorry, im assuming you have some knowledge of C++ programming?

A complete header like the above example would be;

```

#include <QThread>
#include <QObject>

class ThreadTry : public QThread

Q_OBJECT

public:
//Public methods go here

private:
//Private variables go here

signals:
//signals would go here

public slots:
//methods run from connections go here

}
```

Then obviously you would need to create the methods etc in the cpp file.

EDIT: In response to which file would you put it in; you would create a new file (if your right click on source and select add new). Threads run from a program, for example the mainwindow would call a thread.

---

### Post by compiz addict on 2010-09-20
Oh, ok. So I put that code into a header file (threadthing.h). The new file option didn't work so I had to manually create the .h file. I used #include "threadthingl.h" in mainwindowimpl.cpp . I have 'void ThreadTry::run();' in mainwindowimpl.cpp where I want the thread to start. I hope this isn't a dumb and broad question, but what do I do now? I've never had to create a header file before, so I assume I have to edit that some more right?

---

### Post by compiz addict on 2010-09-20
Looking at another header file, I would put 'void function()' in private slots, right?

---

### Post by unknownPoster on 2010-09-20
> **compiz addict said:**
> Looking at another header file, I would put 'void function()' in private slots, right?

Yes, No, and Maybe.

It depends on your design. It looks like you need to familiarize yourself with both C++ and object oriented programming.

[http://en.wikipedia.org/wiki/Object-oriented_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)

---

### Post by compiz addict on 2010-09-20
threadthing.h seems to make other things turn into errors?

---

### Post by unknownPoster on 2010-09-20
> **compiz addict said:**
> threadthing.h seems to make other things turn into errors?

You really need to post your code if you want help. We can't read your mind.

---

### Post by compiz addict on 2010-09-20
I have this function in mainwindowimpl.cpp (along with other stuff of course):
```


void test()
{
	
	string lolstr="pie";
	
ofstream myfile;
myfile.open ("b.txt");

myfile << lolstr;

myfile.close();
}

```

and this is threadthing.h:
```


#include <QThread>
#include <QObject>

class ThreadTry : public QThread
{

Q_OBJECT

public:
//Public methods go here

private:
//Private variables go here

signals:
//signals would go here

private slots:
//methods run from connections go here
void test();
};

```

---

### Post by compiz addict on 2010-09-20
I almost posted that twice forgetting to look on page 2, lol

---

### Post by spjackson on 2010-09-21
> **compiz addict said:**
> I want to create a simple program with a thread. I'm using QTDeveloper to make this program.

The thread is going to be a continuous loop, and I would like to have the program terminate the thread using a function.

At the moment I'm pulling hairs out of my head trying to figure this out and impatiently reading though tutorials only to find out in the end that they don't work at all.
Qt comes with an example that does exactly what you describe.

path_to_qt/examples/threads/queuedcustomtype/

This has a thread whose run() method is looping, and there is a button on the window that stops the thread.

I suggest you take a look at this and model your program on it.

---

### Post by dwhitney67 on 2010-09-21
> **compiz addict said:**
> ... I've never had to create a header file before, so I assume I have to edit that some more right?

I would recommend that you take a temporary step back from Qt and instead, focus on the basics of C++ programming, and preferably using a non-IDE application.

---

### Post by Sub101 on 2010-09-21
> **dwhitney67 said:**
> I would recommend that you take a temporary step back from Qt and instead, focus on the basics of C++ programming, and preferably using a non-IDE application.

Yeh, QT and graphics programming in general are a more "advanced" area of C++ programming. So read up and experiment with basics and create some command line applications. 

It will give you the skills that graphical programs are built upon.

---

### Post by compiz addict on 2010-09-21
ok, here's how far I got.
I have this:
```

#include <QThread>
#include <QObject>

```
in mainwindowimpl.h file and in mainwindowimpl.cpp

I have this (along with the class that was already there) in the header file:

```


 class MyThread : public QThread
 {
 public:
     void run();
 };

```

And finally I have the function in the cpp file, that looks like this:

```

void MyThread::run()
{
	string tehstr="text input to be written to file";
	
ofstream myfile;
myfile.open ("b.txt");

myfile << tehstr;

myfile.close();

}

```

I'm using the tutorial I found at [http://doc.trolltech.com/4.5/qthread.html](http://doc.trolltech.com/4.5/qthread.html)

It doesn't compile...

```

Build (make)...
g++ -Wl,-O1 -o bin/tccl-qt build/mainwindowimpl.o build/main.o build/moc_mainwindowimpl.o build/moc_threadthing.o    -L/usr/lib -lQtGui -lQtCore -lpthread 
build/moc_threadthing.o: In function `ThreadTry::qt_metacall(QMetaObject::Call, int, void**)':
moc_threadthing.cpp:(.text+0x5f): undefined reference to `ThreadTry::test()'
collect2: ld returned 1 exit status
make: *** [bin/tccl-qt] Error 1
---------------------- Build finished without error----------------------

```

What am I doing wrong? QTDeveloper doesn't find any errors but g++ sure does :(

---

### Post by compiz addict on 2010-09-21
Figured that problem out, 
there was still that extra header I made that I decided not to use. I have to remove it from the project, nut just take out the #include "threadthing.h"

---

### Post by compiz addict on 2010-09-21
And by doing this:

MyThread tehthread;
tehthread.run();

I've created my first thread! Awesome! Thanks everyone for the help and useful links ;) I'm a 14 year old programmer learning fast.

---

### Post by spjackson on 2010-09-21
> **compiz addict said:**
> And by doing this:

MyThread tehthread;
tehthread.run();

I've created my first thread!
Well, not really. That simply executes the run method synchronously in the main thread.

tehthread.start();

is what you are looking for.

---

### Post by dwhitney67 on 2010-09-21
I would assume the run() method should be declared as protected, not public.  Is this assumption correct?

---

### Post by compiz addict on 2010-09-21
Well, this is what the official documentation says:

> QThreads begin executing in run(). By default, run() starts the event loop by calling exec() (see below). To create your own threads, subclass QThread and reimplement run()

Later I'll make a thread that does an infinite while loop while the main thread does something else, just so I can be sure that I created a thread.

btw, anyone have any tips on threads? Like other things I can do with them etc?

---

### Post by nvteighen on 2010-09-22
The thing is... what is exactly your program going to do? Threads are needed only where concurrency is needed: two or more tasks meant to be run in parallel. So, the first thing to do is to determine whether your program does or doesn't need concurrency. A continous loop isn't necessarily a job for threads.

I'd also follow whitney67's advice if I were you. I've got the impression that you're not fully skilled in C++ and Qt is a somewhat weird and complex scenario. And also, learning the language without an IDE... using a text editor will help you focus on the code and in the knowledge you need to work with that specific language... not just with a specific IDE. Gedit or that KDE default text editor I don't remember its name (Kate?) would be enough, but take a look at Vim, Emacs, Geany, etc.

---

### Post by spjackson on 2010-09-22
> **compiz addict said:**
> Well, this is what the official documentation says:
> QThreads begin executing in run(). By default, run() starts the event  loop by calling exec() (see below). To create your own threads, subclass  QThread and reimplement run()                      Later I'll make a thread that does an infinite while loop while the main thread does something else, just so I can be sure that I created a thread.


It says "reimplement", which you have done. It does not tell you to call the run() method. In the very next paragraph it says "Use the [start]("http://doc.trolltech.com/4.6/qthread.html#start")() method to begin execution."

I pointed you to one of the multi-threading examples that come with the Qt distribution. Did you look at it or any of the other examples?

If you call start() from your main thread, the framework causes your run() method to begin execution in a new thread, and the main thread continues to execute at the next statement after the call to start(). If you simply call run() in the main thread (as per your posted code) then run() is executed in the main thread - all you have done is call the function, which runs to completion and then your main thread continues execution at the next statement after the run().

You don't have to take my word for it; you'll discover this for yourself once your run() method takes a perceptible amount of time to execute. Or go and have a look at the source for the QThread class. It's the start() method in qthread_unix.cpp that calls pthread_create(), not the constructor of QThread. Or better still, look at the Qt examples!!!

---

