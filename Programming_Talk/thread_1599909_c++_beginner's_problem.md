---
title: "c++ beginner's problem"
date: 2010-10-18
forum: Programming Talk
---

### Post by mrkazoodle on 2010-10-18
hi

I learned some basic c++ programming and I want to learn to make simple gui programs using the wxWidgets toolkit.
When I open simple hello world program Geany can build the object and run it. But when I just use the normal build function, I get an error: ```
wx/wx.h: file or folder does not exist
``` which is in the line: ```
#include "wx/wx.h"
``` 
What am I doing wrong?


```
/*
 * hworld.cpp
 */

#include "wx/wx.h" 

class MyApp: public wxApp
{
    virtual bool OnInit();
};

class MyFrame: public wxFrame
{
public:

    MyFrame(const wxString& title, const wxPoint& pos, const wxSize& size);

    void OnQuit(wxCommandEvent& event);
    void OnAbout(wxCommandEvent& event);

    DECLARE_EVENT_TABLE()
};

enum
{
    ID_Quit = 1,
    ID_About,
};

BEGIN_EVENT_TABLE(MyFrame, wxFrame)
    EVT_MENU(ID_Quit, MyFrame::OnQuit)
    EVT_MENU(ID_About, MyFrame::OnAbout)
END_EVENT_TABLE()

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
{
    MyFrame *frame = new MyFrame( _("Hello World"), wxPoint(50, 50),
                                  wxSize(450,340) );
    frame->Show(true);
    SetTopWindow(frame);
    return true;
} 

MyFrame::MyFrame(const wxString& title, const wxPoint& pos, const wxSize& size)
: wxFrame( NULL, -1, title, pos, size )
{
    wxMenu *menuFile = new wxMenu;

    menuFile->Append( ID_About, _("&About...") );
    menuFile->AppendSeparator();
    menuFile->Append( ID_Quit, _("E&xit") );

    wxMenuBar *menuBar = new wxMenuBar;
    menuBar->Append( menuFile, _("&File") );

    SetMenuBar( menuBar );

    CreateStatusBar();
    SetStatusText( _("Welcome to wxWidgets!") );
}

void MyFrame::OnQuit(wxCommandEvent& WXUNUSED(event))
{
    Close(TRUE);
}

void MyFrame::OnAbout(wxCommandEvent& WXUNUSED(event))
{
    wxMessageBox( _("This is a wxWidgets Hello world sample"),
                  _("About Hello World"),
                  wxOK | wxICON_INFORMATION, this);
}

```

---

### Post by Xender1 on 2010-10-18
It seems like you dont have the packages needed to use wxWidgets which is why it is saying it is unable to find the folder (because it probably does not exist). Get the packages for it and you should be all set.

---

### Post by spjackson on 2010-10-18
> **mrkazoodle said:**
> 
I learned some basic c++ programming and I want to learn to make simple gui programs using the wxWidgets toolkit.
When I open simple hello world program Geany can build the object and run it. But when I just use the normal build function, I get an error: ```
wx/wx.h: file or folder does not exist
```
Since Geany can build it, you must have the right headers and libraries. I'm not too sure what you mean by "the normal build function". If you are referring to running g++ from a terminal then you want something like:
```

g++ -o myprog mysource.cpp `wx-config --cxxflags --libs`

```

---

### Post by mrkazoodle on 2010-10-18
I installed the needed packages and they work, I tested that with following commands (and a hello.cpp I downloaded from the wxWidgets site): ```
g++ -c `wx-config --cxxflags` hello.cpp
g++ -o hello hello.o `wx-config --libs`
```
after which a 'hello' executable file showed up in the same folder as the .cpp and .o which works.

With "the normal build function" I meant what Geany does when one presses F9 (it is called 'build'). I called it that way because Geany also has the function to "make object" (which I faultily called "build object", I'm sorry for the confusion but I use a localized version).
Using the "make object" functionality I can make changes to the hello.o file without error and run the code afterwards.

NEW discovery: the error is (also) triggered by pressing compile (F8 )
(I normally don't use that button, but let it compile and build at the same time)

---

### Post by mrkazoodle on 2010-10-18
Might this be missing from the command Geany uses to compile and build the program?

```
What is wx-config

wx-config is a small command-line utility which can help you while building on unix-like systems (including linux and Mac OS X) It will :

    * tell you what compile flags to use (wx-config --cxxflags)
    * tell you what link flags to use (wx-config --libs)
    * can manage multiple wxWidgets installs with different configurations (wx-config --list et al) 
```

---

### Post by spjackson on 2010-10-18
I'm sorry, I misunderstood. I thought you were saying you could build with Geany but not without. If what you really need is to know how to configure Geany in order to be able to build, then I don't know anything about that.

---

### Post by bstree on 2010-10-18
Which IDE you are using?
you need to configure the path to library include files

---

### Post by mrkazoodle on 2010-10-18
Geany
If you can help me do that, you would make my day :p

---

### Post by nvteighen on 2010-10-18
A first issue is the following.

This line:
```

#include "wx/wx.h"

```

will search for a header called wx.h at the subdirectory wh relative to your current directory, not in the system-wide header directory.

When using headers you installed system-wide, you use:
```

#include <wx/wx.h>

```

---

### Post by mrkazoodle on 2010-10-18
Thanks, I already changed that, but it still says the file or directory doesn't exist

---

### Post by mrkazoodle on 2010-10-18
the words "system-wide" got me on the right track!
I hadn't followed the third 'step' in the [tutorial]("http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu"), but now everything is alright (or it seems to be like that :p)
(I thought everything after the first part wasn't interesting for me)

---

### Post by worksofcraft on 2010-10-18
I installed wx and it compiles just fine from the command line:

```

$> sudo apt-get install libwxgtk2.8-dev
...
$> g++ wx_hello.cpp `wx-config --cxxflags --libs`
$> ./a.out
... and up comes a window saying welcome to wxWidgets!

```

i.e. didn't need to do any digital signature checking or any of those other steps.

---

### Post by mrkazoodle on 2010-10-18
the problem wasn't the command line, that worked, it was geany

---

