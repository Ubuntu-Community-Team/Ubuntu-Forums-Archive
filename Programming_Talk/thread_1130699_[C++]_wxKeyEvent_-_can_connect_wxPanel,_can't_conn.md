---
title: "[C++] wxKeyEvent - can connect wxPanel, can't connect &quot;this&quot;?"
date: 2009-04-20
forum: Programming Talk
---

### Post by dodle on 2009-04-20
If I connect a wxPanel to a wxKeyEvent I get the desired output:
[php]/*
 * KeyMash
 *
 */

#include <wx/wx.h>
#include <iostream>
using namespace std;


class MainWindow : public wxFrame
{
    public : MainWindow(const wxString& title);
    
    wxPanel *panel_main;
    int code;
    
    void p1(wxKeyEvent& event);
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, title, wxDefaultPosition,
                                                    wxSize(600,400))
{
    Center();
    
    panel_main = new wxPanel(this, -1);
    panel_main->SetBackgroundColour(wxT("#000000"));
    
    //Here the panel is connected
    panel_main->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::p1), NULL, this);
    
}

void MainWindow::p1(wxKeyEvent& event)
{
    code = event.GetKeyCode();
    cout << code << endl;
}

class Mash : public wxApp
{
    public : virtual bool OnInit();
};

IMPLEMENT_APP(Mash)

bool Mash::OnInit()
{
    MainWindow *frame = new MainWindow(wxT("KeyMash"));
    frame->Show(true);
    return true;
}
[/php]

But if I change it so that the wxFrame, *this*, is connected:
[php]this->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::p1), NULL, this);[/php]
...there is no output to the terminal.  Can someone explain why this is?  Or am I just not coding something right?

---

