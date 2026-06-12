---
title: "Problem with Qt's connectSlotsByName"
date: 2007-05-04
forum: Programming Talk
---

### Post by aquavitae on 2007-05-04
Hi

I'm writing a Qt application with a lot of QActions, so in order to minimise the number of connections I have to type in I'm trying connectSlotsByName.  The code (stripped down) looks something like this:

```

///// mainwindow.h

class MainWindow : public QMainWindow {
   Q_OBJECT

   public:
      MainWindow();

   private:
      QAction *actFileNew;
      QMenu *menuFile;

   public slots:
      void on_actFileNew_triggered(bool checked = false);
}


///// mainwindow.cpp
MainWindow::MainWindow() {
   actFileNew = new QAction(QIcon(":/icons/filenew.png"), "New", this);
   menuFile = menuBar()->addMenu("&File");
   menuFile->addAction(actFileNew);
   QMetaObject::connectSlotsByName(this);
}

void MainWindow::on_actFileNew_triggered(bool checked) {
   // Code to show a message
}

```

My program compiles, but the connection doesn't appear to work - when I select the action from the menu, the message is not displayed in on_actFileNew_triggered().  It works if I make the connection manually using connect().

Can anyone suggest why connectSlotsByName isn't working?

---

### Post by dori on 2007-05-04
Why are you using "bool checked = false" in
```
void on_actFileNew_triggered(bool checked = false);
```if you are not making this QAction checkable then  it should just be 
```
void on_actFileNew_triggered();
```

---

### Post by aquavitae on 2007-05-04
I'm using "bool checked = false" just to match the argument for QAction::triggered.  I agree it is not necessary, and I only put it in because I didn't know if it would affect connectSlotsByName. Either way, the connection isn't made.

---

### Post by dori on 2007-05-05
Auto connect is only works with objects made with the designer. All manual created objects you have to connect your self.

---

### Post by aquavitae on 2007-05-07
That seems awkward!  But when its compiling, how does it know the difference between desiger objects and coded objects?  Maybe I can confuse it so it will do it.

---

### Post by dr.pppr on 2009-03-06
I know this is an old thread, but I still wanted to post a reply to this topic because I had the same problem and there is a solution.

Actually connectSlotsByName also works on classes not created by Qt Designer. You just have to specify an **object name** for the action for connectSlotsByName to correctly set up the signal/slot connection.

```

///// mainwindow.cpp
MainWindow::MainWindow() {
   actFileNew = new QAction(QIcon(":/icons/filenew.png"), "New", this);
   **actFileNew->setObjectName("actFileNew");**  // <<< this should do the trick
   menuFile = menuBar()->addMenu("&File");
   menuFile->addAction(actFileNew);
   QMetaObject::connectSlotsByName(this);
}

```

Cheers!
-Stefan

---

### Post by jonathanmotes on 2009-03-24
> **dr.pppr said:**
> 
Actually connectSlotsByName also works on classes not created by Qt Designer. You just have to specify an **object name** for the action for connectSlotsByName to correctly set up the signal/slot connection.



This doesn't work for me. I'm trying to tie a event to a slot in the same class (MainWindow). Can anyone see if I'm doing something wrong?

Thanks!

```
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent), ui(new Ui::MainWindowClass)
{
    ui->setupUi(this);
    count = 0;

    //connect(this, SIGNAL(testSignal()), this, SLOT(on_MainWindow_testSignal()));

    this->setObjectName(QString("MyWindow"));

}

MainWindow::~MainWindow()
{
    delete ui;
}

void MainWindow::on_pushButton_clicked()
{
    cout << "test" << endl;

    testSignal();
}

void MainWindow::on_MyWindow_TestSignal()
{
    cout << count << " on test signal" << endl;
    count++;
}  
```

---

### Post by dr.pppr on 2009-03-24
> **jonathanmotes said:**
> This doesn't work for me. I'm trying to tie a event to a slot in the same class (MainWindow).

You would need to call connectSlotsByName at the end of the constructor...
```
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent), ui(new Ui::MainWindowClass)
{
    ui->setupUi(this);
    count = 0;

    //connect(this, SIGNAL(testSignal()), this, SLOT(on_MainWindow_testSignal()));

    this->setObjectName(QString("MyWindow"));
    **QMetaObject::connectSlotsByName(this);**
}

```

...but this code would still throw a warning during runtime that a matching signal could not be found:
```
QMetaObject::connectSlotsByName: No matching signal for on_MyWindow_testSignal()
```

This is because when connectSlotsByName processes the on_MyWindow_testSignal slot it looks for a **child object** named "MyWindow" of the object passed as parameter (in the above case *this*, the instance of the MainWindow class) which it cannot find because it is not a child object but the instance itself that is named "MyWindow".

Now if you had QObject-derived class named "MyApplication" that had a slot named "on_MyWindow_testSignal" and a member variable m_mainWindow of type *MainWindow ** then a call of connectSlotsByName with the instance of the MyApplication class would be able to set up a connection from the "testSignal" signal of the MainWindow instance (m_mainWindow) to the on_MyWindow_testSignal slot of the MyApplication instance because m_mainWindow would be a child object named "MyWindow" of the MyApplication instance.

In your case you would have to set up the connection manually, but you shouldn't use the "on_" prefix for the slot's name because connectSlotsByName is also called at the end of setupUi which would again throw the warning that there is no matching signal for the slot.

```
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent), ui(new Ui::MainWindowClass)
{
    ui->setupUi(this);
    count = 0;

    **connect(this, SIGNAL(testSignal()), SLOT(testSignalHandler()));**
}
```

Hope this helps.

Cheers!
-Stefan

---

### Post by jonathanmotes on 2009-03-25
Yes, that was very helpful!

I was thinking that connectSlotsByName must only work for child objects. Thanks for clarifying this for me!

---

