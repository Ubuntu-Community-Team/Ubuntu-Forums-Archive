---
title: "[wxPython/wxWidegts] AboutDialogInfo &amp; Modal"
date: 2010-08-23
forum: Programming Talk
---

### Post by dodle on 2010-08-23
Is there a way to make an AboutDialogInfo/AboutBox window modal?  I haven't been able to find it anywhere in the [wxPyDocs](http://www.wxpython.org/docs/api) or [wx docs](http://docs.wxwidgets.org/stable/wx_classref.html#classref).  Currently, when the AboutBox is open, I can still interact with the main window and open as many about boxes as I want, which doesn't seem like it should be the default behavior.

Here is some sample Python code:
[php]import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title)
        
        self.bg = wx.Panel(self, -1)
        
        about_button = wx.Button(self.bg, -1, "About")
        
        wx.EVT_BUTTON(about_button, -1, self.ShowAbout)
        
        self.about = wx.AboutDialogInfo()
        
    def ShowAbout(self, event):
        wx.AboutBox(self.about)

class MyApp(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Test")
        frame.Show()
        self.SetTopWindow(frame)
        return True

app = MyApp(0)
app.MainLoop()[/php]

and sample C++ code:
[php]#include <wx/wx.h>
#include <wx/aboutdlg.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
    void ShowAbout(wxCommandEvent& event);
  private:
    wxAboutDialogInfo about;
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, title)
{
    wxPanel *bg = new wxPanel(this);

    wxButton *about_button = new wxButton(bg, -1, _T("About"));

    about_button->Connect(wxEVT_COMMAND_BUTTON_CLICKED, wxCommandEventHandler(MainWindow::ShowAbout), 0, this);
}

void MainWindow::ShowAbout(wxCommandEvent& event)
{
    wxAboutBox(about);
}


class MyApp : public wxApp
{
  public:
    virtual bool OnInit();
};

IMPLEMENT_APP(MyApp)

bool MyApp::OnInit()
{
    MainWindow *frame = new MainWindow(_T("test"));
    frame->Show();
    SetTopWindow(frame);
    return true;
}[/php]

---

### Post by dodle on 2010-08-24
*bump*

---

### Post by robots.jpg on 2010-08-24
I'm pretty sure that's GTK's fault.  The native about panels are never  modal as far as I've seen (check any Gnome application.)  Of course, plenty of them still  manage to keep you from opening multiples, but I don't know how to do  that either without creating a custom dialog in wx.

---

### Post by dodle on 2010-08-24
Thanks, I guess I will just create a custom info dialog.

---

### Post by dodle on 2010-08-26
> **robots.jpg said:**
> I'm pretty sure that's GTK's fault.  The native about panels are never  modal as far as I've seen (check any Gnome application.)  Of course, plenty of them still  manage to keep you from opening multiples, but I don't know how to do  that either without creating a custom dialog in wx.

I don't think the problem is GTK.  The following code examples both create a GTK about dialog that is modal:

pygtk:
[php]import gtk

class MainWindow(gtk.Window):
    def __init__(self):
        super(MainWindow, self).__init__()
        
        self.connect("destroy", gtk.main_quit)
        self.set_size_request(250, 150)
        self.set_position(gtk.WIN_POS_CENTER)
        
        about = gtk.Button("About")
        about.set_size_request(80, 25)
        about.connect("clicked", self.OnAbout)
        
        self.add(about)
        
        self.show_all()
    
    def OnAbout(self, widget):
        about = gtk.AboutDialog()
        about.run()
        about.destroy()


MainWindow()
gtk.main()[/php]

gtkmm:
[php]// about.h

#include <gtkmm.h>

class MainWindow : public Gtk::Window
{

public:
  MainWindow();
  virtual ~MainWindow();

protected:
  //Signal handlers:
  void OnAbout();

  //Member widgets:
  Gtk::Button button_about;
};[/php]
[php]// about.cpp

#include "about.h"

MainWindow::MainWindow()
: button_about("about")   // creates a new button with label "Hello World".
{
  // Sets the border width of the window.
  set_border_width(10);

  // When the button receives the "clicked" signal, it will call the
  // on_button_clicked() method defined below.
  button_about.signal_clicked().connect(sigc::mem_fun(*this,
              &MainWindow::OnAbout));

  // This packs the button into the Window (a container).
  add(button_about);

  // The final step is to display this newly created widget...
  show_all();
}

MainWindow::~MainWindow()
{
}

void MainWindow::OnAbout()
{
  Gtk::AboutDialog about;
  about.run();
}[/php]
[php]// main.cpp

#include "about.h"

int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  MainWindow test;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(test);

  return 0;
}[/php]

So I think the problem is in wx/wxPython.

**Edit:** I forgot to mention in my first post that I am using wxGtk 2.8.10.1

---

### Post by robots.jpg on 2010-08-27
All I can tell you is that wx.AboutBox() does create a modal dialog under MS Windows whether it calls the native or wxPython version.  Under Ubuntu, it's not modal either way, so I assumed the difference there was GTK.  Whatever it is, it's platform-specific.

---

### Post by dodle on 2010-08-27
Yes, you are right about that.  I'm trying to update to wxGtk 2.8.11 to see if there is any difference.  I doubt there will be since it is doesn't appear to be a major update.

**Edit:** I found a bug report on this issue: [http://trac.wxwidgets.org/ticket/8845](http://trac.wxwidgets.org/ticket/8845), which has a couple of patches that [sort of] fix the problem.  Though I don't know if they have been applied in newer versions of wx.

---

