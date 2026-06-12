---
title: "How to open a second window in QT4 (preferably in the context of using QDevelop)"
date: 2007-10-20
forum: Programming Talk
---

### Post by RChickenMan on 2007-10-20
Good day,

My question regarding developing GUI applications with QT seems pretty basic, but for whatever reason I have not been able to figure it out, despite much Googling, and using other resources available to me.  I am doing some QT GUI development for a school class, and I'm pretty comfortable with it for the most part, what with the signals, slots, widgets, and whatnot.

For whatever reason I am completely lost when it comes to simply opening a new window.  For example, let's say I design my main window using QDesigner, and then make a second window.  Then I want to make it so that when I click a certain button in the main window, it opens the second window.  I assumed that all this requires is declaring an instance of the new window (i.e. calling the default constructor) and then calling the show() function (my new window is inherited from QMainWindow) on that object.  It just doesn't open the new window, despite the fact that, given my understanding of the API, this is what I should be doing.

I'm pretty comfortable working with QT on my own (i.e. without an IDE), but using QDevelop just makes life so much easier!  So if anyone here has experience with QDevelop, your advice would be just that much more useful.  However, answering the question not in the context of QDevelop will help a lot as well.

Thanks a lot to all of you QT programmers out there willing to help out a beginner!

---

### Post by keifer on 2007-10-21
If you can get your hands on a copy of _C++ GUI programming with Qt 4_, you may find it helpful. Chapter 3, Section 4[Using Dialogs] deals with a similar topic.

Short of that, I'm also willing to try and help, but I expect that I've less experience with Qt 4 than you. ;)

For a modeless window, all that should be needed is the following:

```

// Check to see if a second window has already been initialized
if (!secondWindow) {
    secondWindow = new QDialog(this); //or QMainWindow, or your custom class
}
secondWindow->show();
secondWindow->activateWindow();

```

Please note that I'm much more competent in python than C++ (which is rather new to me), so the above may have syntax issues.

It would be really helpful to see the code you are working with, if at all possible. :)

---

### Post by RChickenMan on 2007-10-23
Hey, thanks a lot for lending a hand!

I had actually figured it out, and now I feel dumb.  I was declaring a pointer to the new window, but never actually constructing the object!  I guess when thrown into new concepts (such as GUI programming with a new and mysterious API) you just forget the basics!

---

### Post by SheenuK on 2012-03-26
secondWindow->activateWindow();


At this app crashes. what to do?

---

