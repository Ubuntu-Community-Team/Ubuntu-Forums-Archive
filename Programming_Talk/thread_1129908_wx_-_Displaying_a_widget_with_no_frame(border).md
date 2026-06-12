---
title: "wx - Displaying a widget with no frame(border)"
date: 2009-04-19
forum: Programming Talk
---

### Post by dodle on 2009-04-19
I've created a program that only displays a window with one panel and no frame.  It worked on Windows, but isn't working on Ubuntu.

Python:
[php]import wx

class MainWindow(wx.Window):
    def __init__(self, parent, id):
        wx.Window.__init__(self, parent, id, wx.DefaultPosition, (300,400))
        
        self.Center()
        
        panel_main = wx.Panel(self, -1)
        panel_main.SetBackgroundColour("#ffffff")
        
        
class BmpTxt(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1)
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = BmpTxt(0)
app.MainLoop()[/php]

C++:
[php]#include <wx/wx.h>

class MainWindow : public wxWindow
{
    public : MainWindow(const wxString&);
};

MainWindow::MainWindow(const wxString&)
    : wxWindow(NULL, -1, wxDefaultPosition, wxDefaultSize)
{
    wxPanel *panel_main = new wxPanel(this, -1);
    panel_main->SetBackgroundColour(wxT("#ffffff"));
    Center();
}

class BmpTxt : public wxApp
{
    public : virtual bool OnInit();
};

IMPLEMENT_APP(BmpTxt)

bool BmpTxt::OnInit()
{
    MainWindow *frame = new MainWindow(wxT("hello"));
    frame->Show(true);
    return true;
}
[/php]

There is no terminal output with the Python version, but the C++ version outputs "segmentation fault".

---

### Post by dodle on 2009-04-19
I figured out my problem.  I changed wxWindow to wxFrame and set it's style to wxBORDER_NONE.

---

