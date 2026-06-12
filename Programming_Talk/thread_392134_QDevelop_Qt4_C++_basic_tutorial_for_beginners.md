---
title: "QDevelop Qt4 C++ basic tutorial for beginners"
date: 2007-03-24
forum: Programming Talk
---

### Post by clpc on 2007-03-24
I have created a tutorial for absolute beginners to get into programming in Linus using QDevelop and the Qt4 API.

[http://clivecooper.co.uk/tutorial/index.html](http://clivecooper.co.uk/tutorial/index.html)

I hope some of you find it useful.

---

### Post by blanky on 2007-03-24
Pretty cool! The Qt4 documentation is also great :D

---

### Post by nandasunu on 2007-03-24
Thanks for this tutorial, its really helpful.

---

### Post by DAaaMan64 on 2007-04-30
I am checking this out right now, thanks!

---

### Post by dori on 2007-04-30
In your example you create a function called ```
void MainWindowImpl::addClicked()
``` and connect it with btAdd clicked signal. why not using the auto connection? you only have to name you function on_btAdd_Clicked() and the function is automatically connected no need for this line 
```
connect(btAdd, SIGNAL(clicked()), this, SLOT(addClicked()));
```QDevelop even does this for you. right click on your *.ui file in QDevelop and select "Dialog Subclassing" and select what widget and function you want to create and QDevelop does the rest.

---

### Post by rickwookie on 2007-05-21
> **dori said:**
> In your example you create a function called ```
void MainWindowImpl::addClicked()
``` and connect it with btAdd clicked signal. why not using the auto connection? you only have to name you function on_btAdd_Clicked() and the function is automatically connected no need for this line 
```
connect(btAdd, SIGNAL(clicked()), this, SLOT(addClicked()));
```QDevelop even does this for you. right click on your *.ui file in QDevelop and select "Dialog Subclassing" and select what widget and function you want to create and QDevelop does the rest.

When I right-click on the .ui file in QDevelop and select either "Dialog Subclassing" or "Dialog Preview", QDevelop just exits (dies?).

Any idea what's going on there?

Also, forgive the ignorance, but is there any way to view the connections that are created in QT from within QDevelop. It seems that they are put into the XML .ui file, but how are they then turned into 'code'? How does QT generate the C++ to make these connections actually do something, or am I missing something fundamental here?

---

### Post by jonface on 2007-05-21
Looks good, I'll give it a read when I get 5 minutes. Thanks.

---

### Post by std on 2007-05-21
> **rickwookie said:**
> Also, forgive the ignorance, but is there any way to view the connections that are created in QT from within QDevelop. It seems that they are put into the XML .ui file, but how are they then turned into 'code'? How does QT generate the C++ to make these connections actually do something, or am I missing something fundamental here?

I'm not sure about what you wanted to ask, so I'll answer in both ways :P

1. If you refer to how Qt turns the XML .ui file into C++ code, uic does that automagically (more or less, well). Basically, you needn't use Qt Designer if you don't want to -- the code uic generates is human-readable et all, except that for larger interfaces it becomes very tedious (moderately complex Designer interfaces generate 100s of lines of source code).

2. If you refer to how Qt binds slots to signals (as in, generating the background code that makes a slot be called when a signal is emitted), this is, to my understanding, an augmented callback mechanism. When you bind a slot and a signal, you do so using the CONNECT macro. The part of Qt that works out the code in this case is moc.

I have no idea about how exactly moc works (even though I've used Qt extensively). However, one thing I am sure of is that Qt's signal-slots model is an implementation of the Observer pattern. Wikipedia has a reasonably-detailed explanation about it: [http://en.wikipedia.org/wiki/Observer_pattern](http://en.wikipedia.org/wiki/Observer_pattern) .

---

### Post by Mickeysofine1972 on 2007-05-22
Very good howto BTW !

Its a little weird that I just released a very similar one on the Ubuntu Games Developer Wiki LMAO!

[http://ubuntu-gamedev.wikispaces.com](http://ubuntu-gamedev.wikispaces.com)

Although I think yours is much better XD

Mike

---

### Post by knopp182 on 2007-06-21
Very Nice tutorial, Thanks :D

---

### Post by ankursethi on 2007-06-21
Sweet. Add this to one of those sticky mega threads.

---

### Post by daxumaming on 2007-06-24
those are the kind of tutorials I need...
Bookmarked! thanks.

---

### Post by mgoblue on 2007-07-27
I just wanna say thank you for this cause I used it in reference a lot!

---

### Post by Visitor.Q on 2007-10-16
A very good beginners tutorial! I have worked through it, and am now creating my first QT application, which might actually be useful to me as well :) 

Anyway, I have a question, and this might be the right place (correct me if im wrong); 
I have created the mainwindow as given in the tutorial and after adding a lot of stuff in the UI as well as in the code I found that I might need a dialog with ok/cancel. So, there is a template in QDevelop which supplies a code for a dialog window and I created a new project quickly just to see how it's done. I copied some stuff from this new project to my own project and now I can call a dialog by setting the following in the main() function:
```
=== headerfile declaration ===
class PopupDialogNoBubImpl : public QDialog, public Ui::popupNoBub
{
Q_OBJECT
public:
	PopupDialogNoBubImpl( QWidget * parent = 0, Qt::WFlags f = 0 );
private slots:

};
=== code ===

int main(int argc, char ** argv)
{
	QApplication app( argc, argv );
	MainWindowImpl win;
	win.show();
        PopupDialogNoBubImpl dialog; // <<<<-------------
	dialog.show();               // <<<<-------------
	app.connect( &app, SIGNAL( lastWindowClosed() ), &app, SLOT( quit() ) );
	return app.exec();}
```
If I start the app, the main window and the popup both show.
However, if I move the
```
        PopupDialogNoBubImpl dialog;
	dialog.show();
```to the MainWindow class (in another cpp file, according to the tutorial and the header defined as above), like:
```
MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f) 
	: QMainWindow(parent, f)
{
    setupUi(this);
    setupInitialBubData();
    
    PopupDialogNoBubImpl dialog;
    dialog.show();
....
....}
```
the dialog window does not show (but it compiles ok). But I want it to show, so what am I doing wrong?

---

### Post by Visitor.Q on 2007-10-16
> **Visitor.Q said:**
>  ... :) 
Okay, I already found that I needed the dialog.exec() to show the dialog... Perhaps it just helps to specify the problem on a forum to find the solution.

---

### Post by malangaman on 2008-03-14
Thank you, Mr. Cooper

---

### Post by LaRoza on 2008-03-14
Added to my wiki. :)

---

### Post by thaumielx72 on 2010-05-30
OK, I tried to send the OP a PM but I don't have 75 posts yet so I should post more here to correct that problem.  LOL

Anyway here's the message for clcp:

I keep trying to use your tutorial but I can never get the horizontal and vertical layout to work.  They create a red box and highlight the button and input or all three but releasing the cursor leaves the widgets the way they were.

I keep trying new projects but it is getting too frustrating.  Resizing the window, for instance, has no effect on the three boxes at all.  Should I do something other than click on (horizontal or vertical) layout and drag and drop to the window because thats how the first three widgets behaved?

Would love to use QDevelop and Qt but this is telling me I must be in over my head or something.

Thanks in advance!  :guitar:

---

### Post by malangaman on 2010-05-30
Don't get frustrated. Just keep plugging away you'll get it. I did. What version of Qt are you using?

---

### Post by thaumielx72 on 2010-05-30
QDevelop version 0.27, Qtdesigner version 4.6.2, and Qt version 4.6.2

---

### Post by malangaman on 2010-05-31
The tutorial was made under Qt 4.1.1 it may make a difference. It worked fine for me back then, though. I have the same versions as you do now. I will work on it later today and see.

---

