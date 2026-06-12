---
title: "[C++] Can't Find Reference for wxSVG Library"
date: 2010-09-10
forum: Programming Talk
---

### Post by dodle on 2010-09-10
I've wanted to work with SVG image files and am familiar with wxWidgets, so I decided to try wxSVG: [http://sourceforge.net/projects/wxsvg/](http://sourceforge.net/projects/wxsvg/).  But I cannot find any reference nor tutorials for it on its sourceforge project page nor googling the web.  Does anyone know where I can find some good information?  

If not, maybe I will look into the rsvg library.  I just thought wxSVG would be simpler since I am already using wxWidgets.

**Edit:**  I got a start on it by looking over the source code.  So far I have been able to simply display an SVG image, which is what I want to do.  But, wxSVG is still in beta, and I am finding that it does not always display SVG images correctly.  Here is the source for what I have done so far:
[php]#include <wx/wx.h>
#include <wxSVG/svgctrl.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
  private:
    wxSVGCtrl *display;
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, title)
{
    display = new wxSVGCtrl(this);
    display->Load(_T("check.svg"));
}[/php]

From the images attached you can see that the "check.svg" displays correctly, but if the "globe.svg" is loaded, only the outline is displayed.

---

### Post by dodle on 2010-09-14
I was shown another way to render svg files as a wxImage using wxSVGDocument: [http://wxsvg.sourceforge.net/using.html](http://wxsvg.sourceforge.net/using.html)

[php]#include <wx/wx.h>
#include <wxSVG/SVGDocument.h>

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString& title);
  private:
    wxStaticBitmap *img;
};

MainWindow::MainWindow(const wxString& title) : wxFrame(NULL, -1, title)
{
    wxSVGDocument *svgimg = new wxSVGDocument;
    svgimg->Load(_T("globe.svg"));

    img = new wxStaticBitmap(this, -1, wxImage(svgimg->Render()));
}[/php]

But the globe.svg still does not render correctly.  I think it has to do with wxSVG still being in beta.

---

