---
title: "Trying to keep focus on a specific widget"
date: 2009-04-16
forum: Programming Talk
---

### Post by dodle on 2009-04-16
I'm practicing my C++ and i'm trying to create a program that keeps it's focus on the text area no matter what.  Here is my code:
[php]#include <wx/wx.h>
#include <iostream>
using namespace std;

class MainWindow : public wxFrame
{
    public: MainWindow(const wxString& title);

    void LoseFocus(wxFocusEvent& event);

    wxPanel *panel1;
    wxTextCtrl *text_area;
    wxButton *buttonA;
    wxButton *buttonB;

    wxBoxSizer *v_sizer;
    wxBoxSizer *h_sizer;
};

MainWindow::MainWindow(const wxString& title)
    : wxFrame(NULL, -1, title, wxDefaultPosition, wxSize(300,400), 
                        wxDEFAULT_FRAME_STYLE & ~(wxRESIZE_BORDER|
                            wxRESIZE_BOX|wxMAXIMIZE_BOX))
{
    panel1 = new wxPanel(this, -1);

    text_area = new wxTextCtrl(panel1, -1);
    text_area->SetFocus();
    text_area->Connect(wxEVT_KILL_FOCUS, wxFocusEventHandler(MainWindow::LoseFocus));

    buttonA = new wxButton(panel1, -1, wxT("A"));
    buttonB = new wxButton(panel1, -1, wxT("B"));

    h_sizer = new wxBoxSizer(wxHORIZONTAL);
    h_sizer->Add(buttonA, 1, wxEXPAND);
    h_sizer->Add(buttonB, 1, wxEXPAND);

    v_sizer = new wxBoxSizer(wxVERTICAL);
    v_sizer->Add(text_area, 5, wxEXPAND);
    v_sizer->Add(h_sizer, 1, wxEXPAND);

    panel1->SetSizer(v_sizer);

    Center();
}

void MainWindow::LoseFocus(wxFocusEvent& event)
{
    text_area->SetFocus();
}

class Calc : public wxApp
{
    public : virtual bool OnInit();
};

IMPLEMENT_APP(Calc)

bool Calc::OnInit()
{
    MainWindow *frame = new MainWindow(wxT("Calculator"));
    frame->Show(true);
    return true;
}
[/php]

Right now, if I press one of the buttons I get "segmentation fault" in the terminal and the app shuts down.  What am I doing wrong?

---

### Post by dodle on 2009-04-17
Something is wrong with the handler.  If change it from:
[php]void MainWindow::LoseFocus(wxFocusEvent& event)
{
    text_area->SetFocus();
}[/php]
to:
[php]void MainWindow::LoseFocus(wxFocusEvent& event)
{
    cout << "Hello World" << endl;
}[/php]
I get a printout in the terminal of "Hello World".  So the event is being caught, I'm just not setting up the handler right.... I guess.

---

### Post by c174 on 2009-04-17
> **dodle said:**
> 
[php]
    text_area->Connect(wxEVT_KILL_FOCUS, wxFocusEventHandler(MainWindow::LoseFocus));
[/php]


Try to change the line above to 

[PHP]text_area->Connect(wxEVT_KILL_FOCUS, wxFocusEventHandler(MainWindow::LoseFocus),NULL,this);[/PHP]

The extra arguments are optional data and the event sink, respectively. Here I just put "NULL" since no user data is to be transferred to the focus event. I put "this" since the focus event handler is a member of MainWindow.

If you were handling a COMMAND-event you could use Connect without going through the object that is generating the event (and without the "NULL,this" stuff), because wxWidgets has a system for propagating certain types of events until a handler is found. You can read about this in the docs. It's a little bit tricky ;)

---

### Post by dodle on 2009-04-18
Thanks very much.  That is exactly what I was looking for.

---

