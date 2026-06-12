---
title: "Expected type specifier"
date: 2012-03-15
forum: Programming Talk
---

### Post by vanangamudi on 2012-03-15
here is my problem

[IMG]https://lh3.googleusercontent.com/-6l_gGv-EgrI/T2FQS_FCftI/AAAAAAAAAQQ/a1sfOl8r7FA/s901/Screenshot.png[/IMG]

frmIDE.h
```
#ifndef FRMIDE_H
#define FRMIDE_H

#include <wx/wx.h>


class frmIDE : public wxFrame
{
    public:
        frmIDE(const wxString& title);
        virtual ~frmIDE();

        void OnQuit(wxCommandEvent& event);
        void OnAbout(wxCommandEvent& event);

    protected:
    private:
        DECLARE_EVENT_TABLE();
};



#endif // FRMIDE_H

```



frmIDE.cpp

```
#include "frmide.h"


BEGIN_EVENT_TABLE(frmIDE,wxFrame)
    EVT_MENU(wxID_ABOUT,frmIDE::OnAbout)
    EVT_MENU(wxID_EXIT,frmIDE::OnQuit)
END_EVENT_TABLE()

frmIDE::frmIDE(const wxString& title):wxFrame(NULL,wxID_ANY,title)
{
    //ctor
//    SetIcon(wxIcon(mondrian.xpm));

    wxMenu *menuFile = new wxMenu;
    wxMenu *menuAbout = new wxMenu;

    menuFile->Append(wxID_EXIT,wxT("Quit\tAlt+F4"),wxT("Exit the Program"));
    menuAbout->Append(wxID_ABOUT,wxT("About\tF1"),wxT("Show Info"));

    wxMenuBar *menu = new wxMenuBar();
    menu->Append(menuFile,wxT("&File"));
    menu->Append(menuAbout,wxT("&About"));

    SetMenuBar(menu);

    CreateStatusBar(2);
    SetStatusText(wxT("Hello everyone"));


}


void frmIDE::OnQuit(wxCommandEvent& event)
{
    Close();
}

void frmIDE::OnAbout(wxCommandEvent& event)
{
    wxString msg;
    msg.Printf(wxT("Welcome to wxWidgets %s"),wxVERSION_STRING);

    wxMessageBox(msg,wxT("About"),wxOK|wxICON_INFORMATION,this);
}

frmIDE::~frmIDE()
{
    //dtor
}

```


main.cpp
```
#include "frmide.h"

// Declare the application class
class App : public wxApp
{
    public:
        // Called on application startup
        virtual bool OnInit();
};

// Implements MyApp& GetApp()
DECLARE_APP(App)

// Give wxWidgets the means to create a MyApp object
IMPLEMENT_APP(App)

// Initialize the application
bool App::OnInit()
{
    // Create the main application window
    frmIDE *frame = new frmIDe(wxT("Minimal wxWidgets App"));
    // Show it
    frame->Show(true);
    // Start the event loop
    return true;
}


```

---

### Post by Some Penguin on 2012-03-15
frmIDE != frmIDe

---

### Post by vanangamudi on 2012-03-15
> **Some Penguin said:**
> frmIDE != frmIDe

What?? I'm such a dumb... how did I left that...

---

