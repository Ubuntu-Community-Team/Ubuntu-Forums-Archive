---
title: "constructors and destructors in C++, where do they go?"
date: 2011-05-27
forum: Programming Talk
---

### Post by u-noob-tu on 2011-05-27
im trying to compile a simple dialog using wxwidgets, just to get familiar with it. i think i have everything correct except one thing, i keep getting an "undefined reference to vtable for MyFrame" message. from what ive found on google, it has to do with constructors and destructors. heres my code: ```
#include <wx/wx.h>
#include <wx/string.h>
#include <wx/stattext.h>
#include <wx/gdicmn.h>
#include <wx/font.h>
#include <wx/colour.h>
#include <wx/settings.h>
#include <wx/button.h>
#include <wx/sizer.h>
#include <wx/frame.h>

class MyApp: public wxApp
{
    virtual bool OnInit();
};

class MyFrame: public wxFrame
{
    public:
        MyFrame( const wxString& title = wxEmptyString, 
                 const wxPoint& pos = wxDefaultPosition, 
                 const wxSize& size = wxSize( 385,95 ), 
                 long style = wxDEFAULT_FRAME_STYLE|wxTAB_TRAVERSAL );
        ~MyFrame();

    protected:
        wxStaticText* m_staticText;
        wxButton* m_button;

    private:
            DECLARE_EVENT_TABLE()    
};

BEGIN_EVENT_TABLE(MyFrame, wxFrame)
END_EVENT_TABLE()

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
{
    MyFrame *frame = new MyFrame( _("Awesome"), wxPoint( 50,50 ), wxSize( 385,95 ) );
    frame->Show(true);
    SetTopWindow(frame);
    return true;
}

MyFrame::MyFrame( const wxString& title, 
                 const wxPoint& pos,
                 const wxSize& size,
                 long style )       
                    : wxFrame(NULL, -1, title, pos, size)
{
    this->SetSizeHints( wxDefaultSize, wxDefaultSize );
    
    wxBoxSizer* bSizer;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
    m_staticText = new wxStaticText( this, wxID_ANY, 
                                    wxT("Ryan is the most awesome person!"), 
                                    wxDefaultPosition, wxDefaultSize, 0 );
    m_staticText->Wrap( -1 );
    bSizer->Add( m_staticText, 0, wxALL|wxALIGN_CENTER_HORIZONTAL, 5 );
    
    wxBoxSizer* bSizer2;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
``` i think i have the destructor (~MyFrame();) but i think im missing a constructor, but i dont know where it should go, or even what it is.

---

### Post by Blackbug on 2011-05-27
your constructor is right there
```

MyFrame( const wxString& title = wxEmptyString, 
                 const wxPoint& pos = wxDefaultPosition, 
                 const wxSize& size = wxSize( 385,95 ), 
                 long style = wxDEFAULT_FRAME_STYLE|wxTAB_TRAVERSAL );


```
here its declared
and
```

MyFrame::MyFrame( const wxString& title, 
                 const wxPoint& pos,
                 const wxSize& size,
                 long style )       
                    : wxFrame(NULL, -1, title, pos, size)
{
    this->SetSizeHints( wxDefaultSize, wxDefaultSize );
    
    wxBoxSizer* bSizer;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
    m_staticText = new wxStaticText( this, wxID_ANY, 
                                    wxT("Ryan is the most awesome person!"), 
                                    wxDefaultPosition, wxDefaultSize, 0 );
    m_staticText->Wrap( -1 );
    bSizer->Add( m_staticText, 0, wxALL|wxALIGN_CENTER_HORIZONTAL, 5 );
    
    wxBoxSizer* bSizer2;
    bSizer = new wxBoxSizer( wxVERTICAL );

```
 
here its defined..
 
I don't know much about wxwidgets ( rather just installed yesterday to try ), but the error you are getting should be related to ```
 virtual bool OnInit();

``` because vtable comes in picture with 'virtual keyword' and I dont think you have that anywhere else
and to add your MyFrame is derived from "wxFrame" so you should check it over there in wxFrame class what is written. I will try to look if i could find any about this.
 
If you are just testing an example, not any project or something, it would be nice if you will put the complete code over here, bcz looks like its not complete as of now.

---

### Post by SledgeHammer_999 on 2011-05-27
The code you posted is incomplete. Can you post the entire file?

---

### Post by Arndt on 2011-05-27
> **u-noob-tu said:**
> im trying to compile a simple dialog using wxwidgets, just to get familiar with it. i think i have everything correct except one thing, i keep getting an "undefined reference to vtable for MyFrame" message. from what ive found on google, it has to do with constructors and destructors. heres my code: ```
#include <wx/wx.h>
#include <wx/string.h>
#include <wx/stattext.h>
#include <wx/gdicmn.h>
#include <wx/font.h>
#include <wx/colour.h>
#include <wx/settings.h>
#include <wx/button.h>
#include <wx/sizer.h>
#include <wx/frame.h>

class MyApp: public wxApp
{
    virtual bool OnInit();
};

class MyFrame: public wxFrame
{
    public:
        MyFrame( const wxString& title = wxEmptyString, 
                 const wxPoint& pos = wxDefaultPosition, 
                 const wxSize& size = wxSize( 385,95 ), 
                 long style = wxDEFAULT_FRAME_STYLE|wxTAB_TRAVERSAL );
        ~MyFrame();

    protected:
        wxStaticText* m_staticText;
        wxButton* m_button;

    private:
            DECLARE_EVENT_TABLE()    
};

BEGIN_EVENT_TABLE(MyFrame, wxFrame)
END_EVENT_TABLE()

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
{
    MyFrame *frame = new MyFrame( _("Awesome"), wxPoint( 50,50 ), wxSize( 385,95 ) );
    frame->Show(true);
    SetTopWindow(frame);
    return true;
}

MyFrame::MyFrame( const wxString& title, 
                 const wxPoint& pos,
                 const wxSize& size,
                 long style )       
                    : wxFrame(NULL, -1, title, pos, size)
{
    this->SetSizeHints( wxDefaultSize, wxDefaultSize );
    
    wxBoxSizer* bSizer;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
    m_staticText = new wxStaticText( this, wxID_ANY, 
                                    wxT("Ryan is the most awesome person!"), 
                                    wxDefaultPosition, wxDefaultSize, 0 );
    m_staticText->Wrap( -1 );
    bSizer->Add( m_staticText, 0, wxALL|wxALIGN_CENTER_HORIZONTAL, 5 );
    
    wxBoxSizer* bSizer2;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
``` i think i have the destructor (~MyFrame();) but i think im missing a constructor, but i dont know where it should go, or even what it is.

I think the reason is that you declare a destructor but don't define it. If you don't need to do any particular cleanup, you can remove the line with ~MyFrame().

---

### Post by u-noob-tu on 2011-05-27
this is the entire code. im just learning C++ and wxwidgets and im not making complete programs right now. im just going with the basics for now.

---

### Post by Blackbug on 2011-05-27
Well, then try to do as suggested in one of the post before:
 
> 
I think the reason is that you declare a destructor but don't define it. If you don't need to do any particular cleanup, you can remove the line with ~MyFrame(). 

 
the suggestion is right because when you are declaring your contructor/destructor and not implementing it, compile wont like it.
 
jus this vtable word in error is confusing me, i guess its because of the inheritence and since you are not defining your destructor this vtable term is coming into picture..

---

### Post by u-noob-tu on 2011-05-27
> **Blackbug said:**
> Well, then try to do as suggested in one of the post before:
 

 
the suggestion is right because when you are declaring your contructor/destructor and not implementing it, compile wont like it.
 
jus this vtable word in error is confusing me, i guess its because of the inheritence and since you are not defining your destructor this vtable term is coming into picture..

yeah, removing ~MyFrame(); fixed it and it now compiles. now i get a segfault, though. this is my first time seeing one, so i dont know what to do about it.

---

### Post by Blackbug on 2011-05-27
well, i am not sure because you said this is the complate code, which doesn't seems like.
 
well, you can try debugging it using gdb and see where exactly it terminates..

---

### Post by JupiterV2 on 2011-05-27
gdb is incredibly useful once you learn how to use it. Do you know what a segfault is? You need to know what causes the error, and what it is, before you can try and debug the issue.

---

### Post by u-noob-tu on 2011-05-27
i cant seem to be able to debug it. just says it was unsuccessful. im using Anjuta IDE by the way.

EDIT: i was able to debug it, but there is nothing in the debugging log. its just blank.

---

### Post by Blackbug on 2011-05-27
i am sorry i don't know about that IDE
 
if you use gdb then you need to compile your code with -g for loading symbol tables in the executable..
 
```

g++ -g <whatever cpp file>

```
 
then use
 
```

gdb <executable name> <name of core file >

```
 
NOTE: if its segmentation fault core file should be generated, if not check your ulimit
```

ulimit -a

```
 
the core file should be unlimited, like below
```

core file size          (blocks, -c) unlimited

```
 
if not, type following command
 
```

ulimit -c unlimited

```
 
then again run the executable and see if core file is created or not. and then debug it

---

### Post by SledgeHammer_999 on 2011-05-27
> **u-noob-tu said:**
> this is the entire code. im just learning C++ and wxwidgets and im not making complete programs right now. im just going with the basics for now.

I am impressed that this code compiles. You have forgotten to put a closing bracket in the implementation of MyFrame::MyFrame()

This should do it.

```
MyFrame::MyFrame( const wxString& title, 
                 const wxPoint& pos,
                 const wxSize& size,
                 long style )       
                    : wxFrame(NULL, -1, title, pos, size)
{
    this->SetSizeHints( wxDefaultSize, wxDefaultSize );
    
    wxBoxSizer* bSizer;
    bSizer = new wxBoxSizer( wxVERTICAL );
    
    m_staticText = new wxStaticText( this, wxID_ANY, 
                                    wxT("Ryan is the most awesome person!"), 
                                    wxDefaultPosition, wxDefaultSize, 0 );
    m_staticText->Wrap( -1 );
    bSizer->Add( m_staticText, 0, wxALL|wxALIGN_CENTER_HORIZONTAL, 5 );
    
    wxBoxSizer* bSizer2;
    bSizer = new wxBoxSizer( wxVERTICAL );
}
```

---

### Post by Arndt on 2011-05-27
> **u-noob-tu said:**
> yeah, removing ~MyFrame(); fixed it and it now compiles. now i get a segfault, though. this is my first time seeing one, so i dont know what to do about it.

Something went wrong when you first entered your program (in your first post) - it is cut off in the middle. With the complete program, maybe I can tell what's wrong.

---

