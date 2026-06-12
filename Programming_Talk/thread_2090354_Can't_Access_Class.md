---
title: "Can't Access Class"
date: 2012-12-02
forum: Programming Talk
---

### Post by dodle on 2012-12-02
I can't figure out why I can't access my class "Layout":

main.h:
[php]#include <wx/wx.h>
#include "layout.h"

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString & title);
  private:
    wxPanel *bg;
    Layout *layout;
};[/php]

layout.h:
[php]#include <wx/wx.h>
#include <wxSVG/svgctrl.h>
#include "groups.h"

class Layout
{
  public:
    Layout(wxPanel &parent);
    void SetLayout(int letter, std::vector<Set> group);
  private:
    wxSVGCtrl *ImageDisplay;
    wxStaticText *TextDisplay;
    wxStaticText *LetterDisplay;
};[/php]

I can't figure out what I'm doing wrong.

Output:
```
g++ -c -O9 -o main.o main.cpp "-I/c/Development/Libraries/wx-2.9/include"
In file included from main.cpp:1:0:
main.h:13:5: error: 'Layout' does not name a type
main.cpp: In constructor 'MainWindow::MainWindow(const wxString&)':
main.cpp:19:5: error: 'layout' was not declared in this scope
main.cpp:19:18: error: expected type-specifier before 'Layout'
main.cpp:19:18: error: expected ';' before 'Layout'
make: *** [main.o] Error 1
```

---

### Post by dwhitney67 on 2012-12-02
There does not appear to be anything syntactically wrong with the code you posted, nor anything else wrong with it, that would cause the error you are seeing.  Perhaps you edited the code after it was initially posted, or you forgot to save it on your HDD before attempting to compile it?

To simplify your coding experience, and to speed up the compiler, you should get into the habit of using forward declarations versus including header files whenever appropriate.

For example:
```

#include <wx/wx.h>
//#include "layout.h"   // Not necessary

class Layout;    // Forward declaration

class MainWindow : public wxFrame
{
  public:
    MainWindow(const wxString & title);
  private:
    wxPanel *bg;
    Layout *layout;
};

```
```

#include <wx/wx.h>
//#include <wxSVG/svgctrl.h>
//#include "groups.h"   // Not necessary for any reason!

class wxPanel;
class wxSVGCtrl;
class wxStaticText;

class Layout
{
  public:
    Layout(wxPanel &parent);
    void SetLayout(int letter, std::vector<Set> group);
  private:
    wxSVGCtrl *ImageDisplay;
    wxStaticText *TextDisplay;
    wxStaticText *LetterDisplay;
};

```
Also, when passing a vector as a parameter, consider passing it by reference so as not to incur the overhead of having a copy created every time the method is called.

Also, get into the habit of declaring the header files (or forward declarations) for objects types that are used in the header file.  The vector is a clear example (also Set?).

---

### Post by jw37 on 2012-12-02
Hi dodle, I'm not quite sure what you are doing (and i've forgotten most of my c++ knowlegde), but Layout() is a method of wxWindow class, and so it's a method of wxFrame class.

In case you are creating a composite control, the best way to do it is to subclass wxPanel. Give it a describing name, e.g. LetterCtrl (just an example, probably no good for your application). Define any custom methods needed, e.g. SetValue().

I don't know if my answer was relevant but hope it was more helping than confusing.

---

### Post by dodle on 2012-12-02
> **jw37 said:**
> Hi dodle, I'm not quite sure what you are doing (and i've forgotten most of my c++ knowlegde), but Layout() is a method of wxWindow class, and so it's a method of wxFrame class.

Yep, that was exactly my problem. Thanks. I've changed the name of the header and of the class and it works.

---

