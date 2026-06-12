---
title: "[C++/wx] Event Table Works but Connect() Does Not"
date: 2010-05-12
forum: Programming Talk
---

### Post by dodle on 2010-05-12
I'm still new to C++ and its event handling.  According to the [Zetcode Tutorial](http://zetcode.com/tutorials/wxwidgetstutorial/events/) there are two ways to catch events; declare an event table or use [color=red]Connect[/color]().  The event table works fine, but the Connect method causes a "segmentation fault".  The event I am catching is a button event.  When the button is pressed the static text on the panel is changed to "Hello World".  I must not be using [color=red]Connect[/color]() correctly.  Does anyone see my error?

Using Event Table:
[php]const int ID_BUTTON = wxNewId(); // Create an Id for my button

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, wxID_ANY, title)
{
    Center(); // Center the window
    
    wxPanel *bg = new wxPanel(this, wxID_ANY); // Background to put items on
    
    display = new wxStaticText(bg, wxID_ANY, _T("Press Button")); // Shows some text
    wxButton *button = new wxButton(bg, ID_BUTTON, _T("Start"));
    
    wxBoxSizer *sizer = new wxBoxSizer(wxVERTICAL);
    sizer->Add(display);
    sizer->Add(button);
    
    bg->SetAutoLayout(true);
    bg->SetSizer(sizer);
    bg->Layout();
}

void MainWindow::ChangeLetter(wxCommandEvent& event)
{
    display->SetLabel(_T("Hello World")); // Change the displayed text to "Hello World"
}

BEGIN_EVENT_TABLE(MainWindow, wxFrame)
    EVT_BUTTON(ID_BUTTON, MainWindow::ChangeLetter)
END_EVENT_TABLE()[/php]

Using Connect():
[php]const int ID_BUTTON = wxNewId(); // Create an Id for my button

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, wxID_ANY, title)
{
    Center(); // Center the window
    
    wxPanel *bg = new wxPanel(this, wxID_ANY); // Background to put items on
    
    display = new wxStaticText(bg, wxID_ANY, _T("Press Button")); // Shows some text
    wxButton *button = new wxButton(bg, ID_BUTTON, _T("Start"));
    
    button->Connect(wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::ChangeLetter));
    
    wxBoxSizer *sizer = new wxBoxSizer(wxVERTICAL);
    sizer->Add(display);
    sizer->Add(button);
    
    bg->SetAutoLayout(true);
    bg->SetSizer(sizer);
    bg->Layout();
}

void MainWindow::ChangeLetter(wxCommandEvent& event)
{
    display->SetLabel(_T("Hello World")); // Change the displayed text to "Hello World"
}[/php]

---

### Post by dwhitney67 on 2010-05-12
Here's an example:  [http://wiki.wxwidgets.org/Example_Of_Using_Connect_For_Events](http://wiki.wxwidgets.org/Example_Of_Using_Connect_For_Events)

---

### Post by dodle on 2010-05-12
Thanks, I see where my error is now:
[php]Connect(ID_BUTTON, wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::ChangeLetter));[/php]

---

