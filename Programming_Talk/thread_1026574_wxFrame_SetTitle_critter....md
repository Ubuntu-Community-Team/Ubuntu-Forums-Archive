---
title: "wxFrame SetTitle critter..."
date: 2008-12-31
forum: Programming Talk
---

### Post by Jonas thomas on 2008-12-31
I've been working through the zetcode tutorial for wxWidgets and I'm seem to have run across a bug... 
[IMG]http://www.metalshaperman.com/wp-content/uploads/2008/12/flydoodoo.png[/IMG]

In the grand scheme of things this is really really minor, but as an aspiring geek in training it has me curious.

I asked about [this]("http://wxforum.shadonet.com/viewtopic.php?t=22338") on the wxforum and the the thought is that the critter lies within wxGTK or GTK itself..

Like I said this is really small stuff, but I was curious if others are seeing this critter also...
I'm on 8.04 32 bit, It seems I have 2.6, 2.8 wxWidgets libraries, I'm showing libgtk2.0-0 Installed version 2.12.9-3ubuntu5 (which is the latest). 


```


#include <wx/wx.h>

class MyApp : public wxApp
{
  public:
    virtual bool OnInit();
};
class CheckBox : public wxFrame
{
public:
    CheckBox(const wxString& title);

    void OnToggle(wxCommandEvent& event);

    wxCheckBox *m_cb;

};

const int ID_CHECKBOX = 100;


CheckBox::CheckBox(const wxString& title)
       : wxFrame(NULL, wxID_ANY, title, wxDefaultPosition, wxSize(270, 150))
{
  wxPanel *panel = new wxPanel(this, wxID_ANY);

  m_cb = new wxCheckBox(panel, ID_CHECKBOX, wxT("Show title"),
                        wxPoint(20, 20));

  m_cb->SetValue(true);

//  Connect(ID_CHECKBOX, wxEVT_COMMAND_CHECKBOX_CLICKED,
//          wxCommandEventHandler(CheckBox::OnToggle));
Connect(ID_CHECKBOX, wxEVT_COMMAND_CHECKBOX_CLICKED,
          wxCommandEventHandler(CheckBox::OnToggle), NULL, this);

  Centre();
}

void CheckBox::OnToggle(wxCommandEvent& WXUNUSED(event))
{

  if (m_cb->GetValue()) {
      this->SetTitle(wxT("CheckBox"));
  } else {

     //this->SetTitle(wxT("")); // This does not work. The Name in the frame doesn't clear
     //this->SetTitle(wxT(" ")); // This works
     this->SetTitle(wxEmptyString);// This does not work. The text in the frame doesn't clear
        Refresh();
        if(this->GetTitle().IsEmpty()){
        wxMessageBox(wxT("ERROR"));// This is interesting.. The message box fires but the frame doesn't clear
     }
     //this->SetLabel(wxEmptyString);//This has no effect?
     //this->SetLabel(wxT("Blah "));// This has no effect
     //this->Refresh(); This has no effect
  }
     //Refresh(); Appears to have no effect
}

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
{

    //CheckBox *cb = new CheckBox(wxT("CheckBox"));
    CheckBox *cb = new CheckBox(wxT("start up"));
    cb->Show(true);

    return true;
}



```

Compiler string
```
g++ bug.cpp `wx-config --cxxflags --libs` -o runthisjunk
```

---

