---
title: "wxWidgets/GTK gui bug,image problem"
date: 2010-08-15
forum: Programming Talk
---

### Post by E-man96 on 2010-08-15
Thanks in advance for reading this. I am using Ubuntu Linux 10.4 LTS, wxWidgets 2.8,gcc & g++ 4.4.3, and Gtk 2.* (I'm not sure which version, there are too many packages)

Whenever I run my program no icons are shown. This is a big problem because I need buttons for the toolbar. When I run the program in the terminal here is the output...

```

emmanuel@emmanuel-laptop:~/Desktop/c++/wxwdgts/mine$ ./main

(main:9619): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(main:9619): Gdk-CRITICAL **: gdk_drawable_get_depth: assertion `GDK_IS_DRAWABLE (drawable)' failed

```

And here is the program I compiled.
```

#include<wx/wx.h>
#include<wx/toolbar.h>
#include<wx/bitmap.h>

class MyFrame : public wxFrame
  {
  public:
    MyFrame(wxString name);
    void OnQuit(wxCommandEvent& event);
  };

MyFrame::MyFrame(wxString name) : wxFrame(NULL, wxID_ANY, name, wxDefaultPosition, wxSize(300,300))
  { 
    wxBitmap exit(wxT("exit.png"));
    wxToolBar *mtool = CreateToolBar();
    mtool->AddTool((int)wxID_EXIT, exit, wxT("Exit app"));
    mtool->Realize();
    Connect(wxID_EXIT, wxEVT_COMMAND_TOOL_CLICKED, wxCommandEventHandler(MyFrame::OnQuit));
  }
  
void MyFrame::OnQuit(wxCommandEvent& WXUNUSED(event))
  { 
    Close(true);
  }
  
class MyApp : public wxApp
  {
  public:
    virtual bool OnInit();
  };

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
  { 
    MyFrame *main=new MyFrame(wxT("Submenu"));
    main->Show(true);
    return true;
  }


```

---

### Post by E-man96 on 2010-08-16
This was solved in the wxWidgets forums see [http://wxforum.shadonet.com/viewtopic.php?p=122802.:lolflag:](http://wxforum.shadonet.com/viewtopic.php?p=122802.:lolflag:)

---

