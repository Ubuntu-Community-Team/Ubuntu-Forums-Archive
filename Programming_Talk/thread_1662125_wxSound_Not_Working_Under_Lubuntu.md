---
title: "wxSound Not Working Under Lubuntu"
date: 2011-01-07
forum: Programming Talk
---

### Post by dodle on 2011-01-07
I don't know if this is the best place to put this but, I can't get wxSound to work under Lubuntu. I have an Ubuntu installation and it works fine on that. So there must be something wrong with my system. The problem is simply that no sound plays. I have played wav files using Rhythmbox which work fine, but then when I try to build my own app using wxSound I don't hear anything.

[php]#include <wx/wx.h>
#include <wx/sound.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
};

MainWindow::MainWindow(const wxString& title)
: wxFrame(NULL, -1, title)
{
    wxSound test(_T("crow.wav"));
    test.Play();
}

class App : public wxApp
{
  public:
    virtual bool OnInit();
};

IMPLEMENT_APP(App);

bool App::OnInit()
{
    MainWindow *frame = new MainWindow(_T("Printing"));
    frame->Show(true);
    SetTopWindow(frame);
    return true;
}[/php]

---

