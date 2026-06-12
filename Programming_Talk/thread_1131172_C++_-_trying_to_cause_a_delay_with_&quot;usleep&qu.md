---
title: "C++ - trying to cause a delay with &quot;usleep&quot;"
date: 2009-04-20
forum: Programming Talk
---

### Post by dodle on 2009-04-20
I'm trying to display a countdown on the main panel, counting from 3 to 1 with one second intervals.  But what's happening is when I try to initialize the program, nothing is displayed until the countdown is over.

[php]/*
 * KeyMash
 *
 */

#include <wx/wx.h>
#include <unistd.h>
#include <iostream>
using namespace std;


class MainWindow : public wxFrame
{
    public : MainWindow(const wxString& title);
    
    wxPanel *panel_main;
    int code;
    
    int x1;
    int y1;
    
    int x2;
    int y2;
    
    wxControl *car1;
    wxControl *car2;
    
    wxStaticText *winner;
    wxStaticText *disp;
    
    bool active;
    
    void p1(wxKeyEvent& event);
    void Countdown();
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, title, wxDefaultPosition,
                                                    wxSize(600,400), wxDEFAULT_FRAME_STYLE& ~(wxMAXIMIZE_BOX|wxRESIZE_BORDER))
{
    Center();
    
    active = false;
    
    panel_main = new wxPanel(this, -1);
    panel_main->SetBackgroundColour(wxT("#000000"));
    panel_main->SetFocus();
    
    panel_main->SetFont(wxFont(50, wxFONTFAMILY_DEFAULT, wxFONTSTYLE_NORMAL, wxFONTWEIGHT_NORMAL));
    
    x1 = 180;
    y1 = 340;
    
    x2 = 400;
    y2 = 340;
    
    
    car1 = new wxControl(panel_main, -1, wxPoint(x1,y1), wxSize(24,24));
    car1->SetBackgroundColour(_T("#ff0000"));
    wxStaticText *car1_text = new wxStaticText(panel_main, -1, _T("press \"z\""), wxPoint(20,340));
    car1_text->SetForegroundColour(_T("#ffffff"));
    car1_text->SetFont(wxFont(14, wxFONTFAMILY_DEFAULT, wxFONTSTYLE_NORMAL, wxFONTWEIGHT_NORMAL));
    
    car2 = new wxControl(panel_main, -1, wxPoint(x2,y2), wxSize(24,24));
    car2->SetBackgroundColour(_T("#0000ff"));
    wxStaticText *car2_text = new wxStaticText(panel_main, -1, _T("press \"/\""), wxPoint(500,340));
    car2_text->SetForegroundColour(_T("#ffffff"));
    car2_text->SetFont(wxFont(14, wxFONTFAMILY_DEFAULT, wxFONTSTYLE_NORMAL, wxFONTWEIGHT_NORMAL));
    
    panel_main->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::p1), NULL, this);
    car1->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::p1), NULL, this);
    car2->Connect(wxEVT_KEY_DOWN, wxKeyEventHandler(MainWindow::p1), NULL, this);
    
    MainWindow::Countdown();  // Calls the function to start the countdown
    
}

void MainWindow::p1(wxKeyEvent& event)
{
    code = event.GetKeyCode();
    
    if (active == true)
    {
    if (y1 > 1 and y2 > 1)
    {
        if (code == 90)
        {
            y1 -= 3;
            car1->SetPosition(wxPoint(x1,y1));
        }
        if (code == 47)
        {
            y2 -= 3;
            car2->SetPosition(wxPoint(x2,y2));
        }
    }
    
    if (y1 == 1)
    {
        winner = new wxStaticText(panel_main, -1, _T("Red Wins"));
        winner->SetForegroundColour(_T("#ff0000"));
        winner->CenterOnParent();
    }
    
    if (y2 == 1)
    {
        winner = new wxStaticText(panel_main, -1, _T("Blue Wins"));
        winner->SetForegroundColour(_T("#0000ff"));
        winner->CenterOnParent();
    }
    }
    
}

// Function to countdown and start the game
void MainWindow::Countdown()
{
    disp = new wxStaticText(panel_main, -1, _T("3"));
    disp->SetForegroundColour(_T("#ffffff"));
    usleep(1000000);
    disp->SetLabel(_T("2"));
    usleep(1000000);
    disp->SetLabel(_T("1"));
    usleep(1000000);
    disp->Close();
    active = true;
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

Where do I need to call the function from the start the countdown after the main window has been created?

---

### Post by scourge on 2009-04-20
> **dodle said:**
> I'm trying to display a countdown on the main panel, counting from 3 to 1 with one second intervals.  But what's happening is when I try to initialize the program, nothing is displayed until the countdown is over.

It's been almost a year since I've used wxWidgets, but I don't think you should use sleep functions at all for this kind of stuff. usleep() blocks the event loop and nothing in your GUI can be updated. That's why you see the changes only after the Countdown() function finishes. Maybe you could use a timer instead.

Edit: alternatively you could try ::wxSafeYield after the sleeping. But I'm not a wxWidgets guy anymore, so I may have just given you horrible advice.

Edit2: Oh, and you're using wxWidgets, so you probably want your app to be portable? If so, don't use anything from unistd.h. wxWidgets has sleep function too: [http://docs.wxwidgets.org/stable/wx_timefunctions.html](http://docs.wxwidgets.org/stable/wx_timefunctions.html)

---

