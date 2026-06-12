---
title: "Question about class instances in C++"
date: 2010-04-30
forum: Programming Talk
---

### Post by AntumDeluge on 2010-04-30
I mostly use Python, so C++ is foreign to me.  From what I understand, I can either create a "prototype"--I think it's called--in the header file, or I can just create the class instance altogether in the main function.  

In case this isn't clear, I'll put up the code I am referring to.  This first method creates a panel in the MainWindow::MainWindow() function:

test.h
[php]#include <wx/wx.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
};
[/php]test.cpp
[php]#include "test.h"

MainWindow::MainWindow(const wxString& title)
  : wxFrame(NULL, -1, title, wxDefaultPosition, wxSize(800,650))
{
    SetIcon(wxIcon(_T("bitmaps/icon.png")));  // Put an icon in the titlebar
    SetMinSize(wxSize(640,400));
    Centre();
    
    wxPanel *bg = new wxPanel(this, -1);  // Create a panel
}
[/php]This next one creates the "prototype" (???) in the header, then refers to it later in MainWindow::MainWindow():

test.h
[php]#include <wx/wx.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    
    wxPanel *bg;  // Prototype??
};
[/php]test.cpp
[php]#include "test.h"

MainWindow::MainWindow(const wxString& title)
  : wxFrame(NULL, -1, title, wxDefaultPosition, wxSize(800,650))
{
    SetIcon(wxIcon(_T("bitmaps/icon.png")));  // Put an icon in the titlebar
    SetMinSize(wxSize(640,400));
    Centre();
    
    bg = new wxPanel(this, -1);  // Create a panel
}
[/php]I'm just confused as to what the difference is, and if there is a benefit to doing it one way or the other.  Is there some documentation that might explain it?

---

### Post by PaulM1985 on 2010-04-30
In the first case, you have defined a MainWindow class (definition is in the header file) with just a constructor.  In the code for the constructor you have created an instance of a wxPanel.

In the second case, you have defined a MainWindow class with a constructor and a member variable which is a pointer to an instance of a wxPanel.  The constructor initialises this wxPanel variable.

Member variables are added to classes to act as an attribute of that class.  For example, you could have a class vehicle, which had attributes noOfWheels, colour, model etc.

```

class Vehicle {

public:
Vehicle();
~Vehicle();

private:
int noOfWheels;
Color colour;
std::string model;
}

```

In your second example, you are saying that a wxPanel is an attribute of a MainWindow.

Paul

---

### Post by MadCow108 on 2010-04-30
the difference is just the scope of the variable.
A scope usually starts with a { and ends with }
All automatic variables in a scope get deleted when the scope ends.
It is very similar with classes.

by declaring it in the class declaration the variable stays in scope and usable during the whole existence of the object created from the class (second case)
It only gets deleted when the whole object gets deleted.

in the first case the variable has local scope to the constructor. That means it will be deleted automatically when it ends and is not available afterwards.

Note that only the pointer gets deleted not the memory allocated by new.
As you lose the pointer to the memory when the constructor ends you can neither access it nor delete it later (= memory leak)

---

### Post by AntumDeluge on 2010-04-30
Okay, I understand now.  Thank you both, very helpful.

But now, I have a question about memory leaks.  But I will look for the answer first.

---

