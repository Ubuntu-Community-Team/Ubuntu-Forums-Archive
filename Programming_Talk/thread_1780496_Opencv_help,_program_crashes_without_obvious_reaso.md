---
title: "Opencv help, program crashes without obvious reason c++"
date: 2011-06-12
forum: Programming Talk
---

### Post by hakermania on 2011-06-12
Hello all.

In my program I have a timer which is connected to a void function (if you know about qt programming a bit), this means that I have a timer that goes through a void function every X milliseconds (specified time).
I successfully capture the first image from the webcam, but when I start the timer so as to capture the next webcam image, the program crashes...

Sample Code that describes the problem:
```

//global variables
IplImage *frame;
CvCapture *camera;

//constructor:
    update_image = new QTimer(this);
    connect(update_image, SIGNAL(timeout()), this, SLOT(image_update()));
    ...
    ...
    _frame=cvQueryFrame(camera);_ //take a screenshot (THIS WORKS!)
    cvwidget->putImage(frame); //put it to our widget (THIS WORKS!
    update_image->start(1000); //after one second go through the slot image_update()
 }

void MyCameraWindow::image_update(){
    _frame=cvQueryFrame(camera);_ //take a new screenshot (**THIS CRASHES****!**)
    cvwidget->putImage(frame);
}

```
Please note the 2 underlined rows, they are exactly the same, the one works, the other doesn't !
I've checked if a null pointer is anywhere but no, nothing is invalid...
;)
Any help appreciated !

---

### Post by NovaAesa on 2011-06-12
What do you mean exactly by "crashes"? Segmentation fault? I would start the debugging process by running in gdb and getting a stacktrace.

---

### Post by hakermania on 2011-06-12
Yes, segmentation fault!
Can you please explain me how to work with gdb? I've used it before but in the faaar past, also, mention that I have debug it with Qt's debugger

---

### Post by NovaAesa on 2011-06-12
To debug in gdb, use the command
```
gdb appname
```
Then type
```
run
```
it should then crash. To get a stacktrace, type
```
backtrace
```


EDIT: gdb only works if you have compiled with the -g flag.

---

### Post by hakermania on 2011-06-12
Ok, that's all I get:
```

gdb ./makeopencvwork2 
Reading symbols from /home/alex/Qt/makeopencvwork2/makeopencvwork2...done.
(gdb) run
Starting program: /home/alex/Qt/makeopencvwork2/makeopencvwork2 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d6db70 (LWP 3104)]
[New Thread 0xb73ffb70 (LWP 3105)]

Program received signal SIGSEGV, Segmentation fault.
0x00459562 in cvQueryFrame () from /usr/local/lib/libhighgui.so.2.1
(gdb) backtrace
#0  0x00459562 in cvQueryFrame () from /usr/local/lib/libhighgui.so.2.1
#1  0x0804c111 in MyCameraWindow::image_update (this=0x81f4c80)
    at MyCameraWindow.cpp:45
#2  0x0804cbf8 in MyCameraWindow::qt_metacall(QMetaObject::Call, int, void**)
    ()
#3  0x010f16ba in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
#4  0x011014ff in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#5  0x0114e2f7 in QTimer::timeout() () from /usr/lib/libQtCore.so.4
#6  0x011073ee in QTimer::timerEvent(QTimerEvent*) ()
   from /usr/lib/libQtCore.so.4
#7  0x01100214 in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
#8  0x00645d24 in QApplicationPrivate::notify_helper(QObject*, QEvent*) ()
   from /usr/lib/libQtGui.so.4
#9  0x0064a8ce in QApplication::notify(QObject*, QEvent*) ()
   from /usr/lib/libQtGui.so.4
#10 0x010eb0bb in QCoreApplication::notifyInternal(QObject*, QEvent*) ()
   from /usr/lib/libQtCore.so.4
#11 0x0111b1e4 in ?? () from /usr/lib/libQtCore.so.4
#12 0x01117e27 in ?? () from /usr/lib/libQtCore.so.4
#13 0x01fd6aa8 in g_main_context_dispatch ()
---Type <return> to continue, or q <return> to quit---
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x01fd7270 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#15 0x01fd7524 in g_main_context_iteration ()
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#16 0x0111853c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#17 0x006f9775 in ?? () from /usr/lib/libQtGui.so.4
#18 0x010ea289 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#19 0x010ea522 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) ()
   from /usr/lib/libQtCore.so.4
#20 0x010eeecc in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#21 0x006438e7 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#22 0x0804b1a2 in main ()
(gdb) quit
A debugging session is active.

    Inferior 1 [process 3091] will be killed.

Quit anyway? (y or n) y

```

---

### Post by hakermania on 2011-06-13
bump

---

### Post by dwhitney67 on 2011-06-13
Employ some defensive actions before assuming a pointer is valid.  For instance:
```

void MyCameraWindow::image_update(){
    assert(camera != NULL);
    frame=cvQueryFrame(camera); //take a new screenshot (THIS CRASHES!)
    assert(frame != NULL);
    cvwidget->putImage(frame);
}

```
In the code-snip that you provided for your constructor, what is 'camera' initialized to be?

P.S.  Actually, using assert() is really only good for debugging.  Usage of if-statements would be better.

---

### Post by carlos21 on 2011-06-13
What is camera initialized to? The seg fault could well come from there

---

### Post by hakermania on 2011-06-14
Well, the camera is initialized as:
```
CvCapture * camera = cvCreateCameraCapture(0);
```and this argument is actually passed to the child's constructor:
```
MyCameraWindow *mainWin = new MyCameraWindow(camera);
```The child's constructor looks like:
```

//global variables...
IplImage *frame;
CvCapture *camera;
//constructor 
MyCameraWindow::MyCameraWindow(CvCapture ***cam**, QWidget *parent) : QWidget(parent) {
    _**camera = cam;**_
    QPushButton *capturebtn = new QPushButton;
    QPushButton *closebtn = new QPushButton;
    update_image = new QTimer(this);
    **connect(update_image, SIGNAL(timeout()), this, SLOT(image_update()));**
    connect(capturebtn, SIGNAL(clicked()), this, SLOT(take_image()));
    connect(closebtn, SIGNAL(clicked()), this, SLOT(close()));
    QVBoxLayout *layout = new QVBoxLayout;
    cvwidget = new QOpenCVWidget(this);
    layout->addWidget(cvwidget);
    layout->addWidget(capturebtn);
    layout->addWidget(closebtn);
    setLayout(layout);
    resize(500, 400);
    frame=cvQueryFrame(camera);  //THIS DOES WORK, I CAN SEE MY FACE
    cvwidget->putImage(frame);
    update_image->start(5000); // THIS DOESN'T WORK, IT CRASHES THE FIRST TIME it goes through image_update() slot after 5000 milliseconds (see first post)
}

```

---

### Post by kvv_1986 on 2011-06-14
Edit: Removed nonsense reply. ;)

Okay, undoing the edit:

Are you sure that you can call a member function before the constructor function has been completed?

Hmm... I actually think you cannot, seeing how memory for the code and data members will be allocated only after the object has been created in the statement "MyCameraWindow *mainWin = new MyCameraWindow(camera);".

---

### Post by dwhitney67 on 2011-06-14
> **kvv_1986 said:**
> Edit: Removed nonsense reply. ;)

Okay, undoing the edit:

Are you sure that you can call a member function before the constructor function has been completed?

Hmm... I actually think you cannot, seeing how memory for the code and data members will be allocated only after the object has been created in the statement "MyCameraWindow *mainWin = new MyCameraWindow(camera);".

I sort of agree with your post, but not 100%.

What Hackermania needs to consider doing is developing proper C++ code, such that there are no global variables.

When defining a constructor, the class is constructed before ever reaching the function body.  For example:
```

class Camera
{
public:
   Camera()
      : camera(cvCreateCameraCapture(0))   // initialization is here
   {
      // nothing to do here.
   }
private:
   CvCapture* camera;
};


class MyCameraWindow
{
public:
   MyCameraWindow(Camera& cam, QWidget* parent)
      : camera(cam),
        QWidget(parent)
   {
      // NOT HERE!!! camera = cam;
      ...
   }

private:
   Camera& camera;
};


...

Camera camera;
MyCameraWindow* mainWin = new MyCameraWindow(camera, widget);

```


P.S.  The 'frame' used in MyCameraWindow should not be declared as a member to the class.  It is a transient object, not permanent.

---

### Post by Arndt on 2011-06-14
> **dwhitney67 said:**
> I sort of agree with your post, but not 100%.

What Hackermania needs to consider doing is developing proper C++ code, such that there are no global variables.

When defining a constructor, the class is constructed before ever reaching the function body.  For example:
```

class Camera
{
public:
   Camera()
      : camera(cvCreateCameraCapture(0))   // initialization is here
   {
      // nothing to do here.
   }
private:
   CvCapture* camera;
};


class MyCameraWindow
{
public:
   MyCameraWindow(Camera& cam, QWidget* parent)
      : camera(cam),
        QWidget(parent)
   {
      // NOT HERE!!! camera = cam;
      ...
   }

private:
   Camera& camera;
};


...

Camera camera;
MyCameraWindow* mainWin = new MyCameraWindow(camera, widget);

```



I think this is beyond what I am able to explain to someone else about C++, so I'd like to learn. I made a small program and tried to do what you said above one shouldn't (setting camera where you wrote "NOT HERE"), and got this:

```
class MyCameraWindow2
{
public:
   MyCameraWindow2(Camera& cam)   // line 44
   {
     printf("2\n");
     camera = cam;
     printf("2.1\n");
   }

private:
   Camera& camera;
};

```

```
cplus.cc: In constructor ‘MyCameraWindow2::MyCameraWindow2(Camera&)’:
cplus.cc:44: error: uninitialized reference member ‘MyCameraWindow2::camera’

```

Does it mean it is not only bad practice as such, but the compiler will forbid it? Will the compiler always detect all such cases?

---

### Post by dwhitney67 on 2011-06-14
> **Arndt said:**
> 
Does it mean it is not only bad practice as such, but the compiler will forbid it? Will the compiler always detect all such cases?

You cannot initialize a reference as such in the body of the constructor.  And yes,  the compiler will always catch these cases.

Had the class constructor accepted a pointer instead, then you could have (re-)initialized the member data pointer in the body.

Suffice to say, the initialization of a class occurs prior to the body of the constructor.  For example:
```

class Foo
{
public:
   Foo() : value(10)   // this is where initialization takes place
   {
      // By the time execution reaches this point, the class object
      // is already constructed, and stPtr is pointing to someplace
      // that is probably not desirable.

      // Below stPtr is finally "initialized".
      stPtr = new SomeTtype;
   }

private:
   int       value;
   SomeType* stPtr;
};


// And now, how the class should have been implemented...

class Foo
{
public:
   Foo() : value(10), stPtr(new SomeType) {}

private:
   int       value;
   SomeType* stPtr;
};

```

P.S.  In the examples above, I do not want to imply that classes should be declared and implemented as one entity.  Common practice is to declare a class in a header file, and then do the implementation in a related .cpp or .cxx module.

---

### Post by hakermania on 2011-06-14
Hello guys, thanks for the answers, I solved my problem but not with the way you suggested (i didn't understand it), I just made 2 global variables (image, camera), then initialized camera at the constructor and all seems to work perfectly !

I know that the point is to understand my bad, so, could you please...?

---

