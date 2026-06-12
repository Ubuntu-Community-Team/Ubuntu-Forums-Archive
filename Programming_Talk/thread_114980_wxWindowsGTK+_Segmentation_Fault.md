---
title: "wxWindows/GTK+ Segmentation Fault"
date: 2006-01-09
forum: Programming Talk
---

### Post by Hubris9 on 2006-01-09
I'm learning how to use wxWindows with C++. Right now, I'm basically following a tutorial line-for-line. Everything worked perfectly until I tried adding a status bar to my program. Now, after compiling with no errors, I get this error when I run my program:

```
Gtk-CRITICAL **: file gtktypeutils.c: line 309 (gtk_type_parent_class): assertion `node != NULL' failed.

Gtk-WARNING **: invalid cast from `(unknown)' to `GtkObject'

Gtk-WARNING **: invalid cast from `(unknown)' to `GtkObject'

Gtk-WARNING **: invalid cast from `(unknown)' to `GtkObject'

Gtk-CRITICAL **: file gtkobject.c: line 1070 (gtk_object_get_data_by_id): assertion `GTK_IS_OBJECT (object)' failed.

Gtk-WARNING **: invalid cast from `(unknown)' to `GtkObject'
Segmentation fault
```

My source files are as follows:

texteditorapp.h

```
#ifndef __TEXTEDITORAPP_H
#define __TEXTEDITORAPP_H

#include "wx/wxprec.h"

#ifndef WX_PRECOMP
    #include "wx/wx.h"
#endif

class TextEditorApp : public wxApp
{
public:
    virtual bool OnInit ();
};

DECLARE_APP (TextEditorApp)

#endif
```

texteditorapp.cc

```
#include "wx/wxprec.h"

#ifndef WX_PRECOMP
    #include "wx/wx.h"
#endif

#include "texteditorapp.h"
#include "textframe.h"

IMPLEMENT_APP (TextEditorApp)

bool TextEditorApp::OnInit ()
{
    TextFrame *frame = new TextFrame ("Simple Text Editor", 100, 100, 400, 300);
    frame->Show (TRUE);
    SetTopWindow (frame);
    return true;
}
```

textframe.h

```
#ifndef __TEXTFRAME_H
#define __TEXTFRAME_H

#include "wx/wxprec.h"

#ifndef WX_PRECOMP
    #include "wx/wx.h"
#endif

class TextFrame : public wxFrame
{
public:
    TextFrame (const wxChar *title, int xpos, int ypos, int width, int height);
    ~TextFrame ();

private:
    wxTextCtrl *m_pTextCtrl;
    wxMenuBar *m_pMenuBar;
    wxMenu *m_pFileMenu;
    wxMenu *m_pInfoMenu;

    enum
    {
        MENU_FILE_OPEN,
        MENU_FILE_SAVE,
        MENU_FILE_QUIT,
        MENU_INFO_ABOUT
    };
};

#endif
```

textframe.cc

```
#include "wx/wxprec.h"

#ifndef WX_PRECOMP
    #include "wx/wx.h"
#endif

#include "textframe.h"

TextFrame::TextFrame (const wxChar *title, int xpos, int ypos, int width, int height) : wxFrame ((wxFrame *) NULL, -1, title, wxPoint (xpos, ypos), wxSize (width, height))
{
    m_pTextCtrl = new wxTextCtrl (this, -1, wxString ("Type some text..."), wxDefaultPosition, wxDefaultSize, wxTE_MULTILINE);
    m_pMenuBar = new wxMenuBar ();
    //File Menu
    m_pFileMenu = new wxMenu ();
    m_pFileMenu->Append (MENU_FILE_OPEN, "&Open", "Open an existing file");
    m_pFileMenu->Append (MENU_FILE_SAVE, "&Save", "Save the content");
    m_pFileMenu->AppendSeparator ();
    m_pFileMenu->Append (MENU_FILE_QUIT, "&Quit", "Quit the application");
    m_pMenuBar->Append (m_pFileMenu, "&File");
    //Info Menu
    m_pInfoMenu = new wxMenu ();
    m_pInfoMenu->Append (MENU_INFO_ABOUT, "&About", "Shows the application's info");
    m_pMenuBar->Append (m_pInfoMenu, "&Info");
    
    SetMenuBar (m_pMenuBar);
    CreateStatusBar (1); //Remove this line and the program runs normally
}

TextFrame::~TextFrame ()
{

}
```

The packages I have installed for wxwindows and gtk are:
libglib1.2
libglib2.0-0
libglib2.0-data
libglib2.0-dev
libglibmm2.4-1c2
libglibmm2.4-dev
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common
libgtk2.0-dev
libgtk2-perl
libgtkmm-2.4-1c2
libgtkmm-2.4-dev
libwxgtk2.4-1
libwxgtk2.4-dev
libwxgtk2.6-0
python-wxgtk2.6
python-wxversion
wx2.4-headers

Can anyone shed some light on this for me?

---

### Post by toojays on 2006-01-10
Find a tutorial on gdb, and learn enough of it so you can get a backtrace when your program segfaults. That will help you solve this segfault, and also those you get in the future.

---

