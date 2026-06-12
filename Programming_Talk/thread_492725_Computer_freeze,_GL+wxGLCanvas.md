---
title: "Computer freeze, GL+wxGLCanvas"
date: 2007-07-05
forum: Programming Talk
---

### Post by hecato on 2007-07-05
This is a sample Im constructing, then dont ask me from which site I get it, thought the base is from the wxWiki [http://www.wxwidgets.org/wiki/index.php/WxGLCanvas](http://www.wxwidgets.org/wiki/index.php/WxGLCanvas)

I will see the samples from wx but they are some what large because the kb and mice interaction.

Warning this code is the cause for at less 2 manual resets of my computer. :S


In fact the freeze come when doing resizing of the window with the mouse... dont try it hard or you will be freezed and sure CTRL+ALT+DEL or SUPR dosent work, only manual reset is OK.

[http://rafb.net/p/kknBvL87.html](http://rafb.net/p/kknBvL87.html)
```
#include "wx/wx.h"
 #include "wx/glcanvas.h"
 
 #ifndef WIN32
 #include <unistd.h> // FIXME: Â¿esto sirve en WIN32?
 #endif
 
class MyApp: public wxApp
{
    virtual bool OnInit();
    void Render();
    wxFrame *frame;
    wxGLCanvas * MyGLCanvas;
public:
    void Pinta(wxPaintEvent& event);
protected:
    DECLARE_EVENT_TABLE()
};
 
BEGIN_EVENT_TABLE(MyApp, wxApp)
  EVT_PAINT    (MyApp::Pinta)
END_EVENT_TABLE()
 
IMPLEMENT_APP(MyApp)
 
 
void MyApp::Pinta(wxPaintEvent& WXUNUSED(event)){
    Render();
}
 
bool MyApp::OnInit()
{
    frame = new wxFrame((wxFrame *)NULL, -1,  _T("Hello GL World"), wxPoint(50,50), wxSize(200,200));
    MyGLCanvas = new wxGLCanvas(frame, -1, wxPoint(0,0), wxSize(200,200), wxSUNKEN_BORDER, _T("some text"));
 
    frame->Show(TRUE);
    Render();
    return TRUE;
}
 
void MyApp::Render()
{
    MyGLCanvas->SetCurrent();
    glClearColor(0.0, 0.0, 0.0, 0.0);
    glClear(GL_COLOR_BUFFER_BIT);
    glViewport(0, 0, (GLint)200, (GLint)200);
 
    glBegin(GL_POLYGON);
        glColor3f(1.0, 1.0, 1.0);
        glVertex2f(-0.5, -0.5);
        glVertex2f(-0.5, 0.5);
        glVertex2f(0.5, 0.5);
        glVertex2f(0.5, -0.5);
        glColor3f(0.4, 0.5, 0.4);
        glVertex2f(0.0, -0.8);
    glEnd();
 
    glBegin(GL_POLYGON);
        glColor3f(1.0, 0.0, 0.0);
        glVertex2f(0.1, 0.1);
        glVertex2f(-0.1, 0.1);
        glVertex2f(-0.1, -0.1);
        glVertex2f(0.1, -0.1);
    glEnd();
    glFlush();

}
```

---

### Post by avik on 2007-07-05
While I don't know what the problem is, have you considered SDL instead of wxWidgets?  I attached a file with a sample of OpenGL with SDL.  It's pretty much the best option for cross-platform OpenGL rendering.  Plus SDL is extremely versatile.

Sorry I couldn't be of more help, but you can always try SDL. :)

---

### Post by hecato on 2007-07-05
I will consider it, but the "thing" is taht I actually whant to use wxWidgets, the GLCanvas has only some little methods to call.

That is because Im aiming at learn OpenGL+wxWidgets at the same time.

Now tht Im thinking I will register in the wx forum, I guess they can guide me in his own context.

---

### Post by hecato on 2007-07-05
Checking the code I put, I se tht there was a call that I havent past, at end after glFlush() it should be called  MyGLCanvas->SwapBuffers();



The problem with the freeze of the whole computer is about beryl and compiz., it hapen with any of them, in metacity it just works!!!!

---

