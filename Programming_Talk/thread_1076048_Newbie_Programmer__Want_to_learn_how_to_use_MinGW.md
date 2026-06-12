---
title: "Newbie Programmer:  Want to learn how to use MinGW"
date: 2009-02-20
forum: Programming Talk
---

### Post by dodle on 2009-02-20
I've been learning to program with Python and wxWidgets, but I want to learn C++ as well.  I'm trying to figure out how to use MinGW on Linux and Windows but am having trouble with libraries.  Here is the "hello world" script that I have been trying to compile:[PHP]// wxhello.cpp
// Version using dynamic event routing
// Robert Roebling, Martin Bernreuther

#include <wx/wx.h>


class MyApp : public wxApp
{
	virtual bool OnInit();
};

IMPLEMENT_APP(MyApp)


class MyFrame : public wxFrame
{
public:
	MyFrame(const wxString& title, const wxPoint& pos, const wxSize& size);
	void OnQuit(wxCommandEvent& event);
	void OnAbout(wxCommandEvent& event);
};

enum
{
	ID_Quit=1,
	ID_About
};


bool MyApp::OnInit()
{
	MyFrame *frame = new MyFrame(_T("Hello World"), wxPoint(50,50),
                wxSize(450,350));

	frame->Connect( ID_Quit, wxEVT_COMMAND_MENU_SELECTED,
		(wxObjectEventFunction) &MyFrame::OnQuit );
	frame->Connect( ID_About, wxEVT_COMMAND_MENU_SELECTED,
		(wxObjectEventFunction) &MyFrame::OnAbout );

	frame->Show(TRUE);
	SetTopWindow(frame);
	return TRUE;
}

MyFrame::MyFrame(const wxString& title, const wxPoint& pos, const wxSize& size)
	: wxFrame((wxFrame*)NULL,-1,title,pos,size)
{
	// create menubar
	wxMenuBar *menuBar = new wxMenuBar;
	// create menu
	wxMenu *menuFile = new wxMenu;
	// append menu entries
	menuFile->Append(ID_About,_T("&About..."));
	menuFile->AppendSeparator();
	menuFile->Append(ID_Quit,_T("E&xit"));
	// append menu to menubar
	menuBar->Append(menuFile,_T("&File"));
	// set frame menubar
	SetMenuBar(menuBar);

	// create frame statusbar
	CreateStatusBar();
	// set statusbar text
	SetStatusText(_T("Welcome to wxWindows!"));
}

void MyFrame::OnQuit(wxCommandEvent& WXUNUSED(event))
{
	Close(TRUE);
}

void MyFrame::OnAbout(wxCommandEvent& WXUNUSED(event))
{
	wxMessageBox(_T("wxWindows Hello World example."),_T("About Hello World"),
                wxOK|wxICON_INFORMATION, this);
}

[/PHP]I tried using this command:```
i586-mingw32msvc-gcc hworld2.cpp
```This is the output:```
hworld2.cpp:5:19: error: wx/wx.h: No such file or directory
hworld2.cpp:9: error: expected class-name before &#8216;{&#8217; token
hworld2.cpp:16: error: expected constructor, destructor, or type conversion before &#8216;class&#8217;
hworld2.cpp: In member function &#8216;virtual bool MyApp::OnInit()&#8217;:
hworld2.cpp:33: error: &#8216;MyFrame&#8217; was not declared in this scope
hworld2.cpp:33: error: &#8216;frame&#8217; was not declared in this scope
hworld2.cpp:33: error: expected type-specifier before &#8216;MyFrame&#8217;
hworld2.cpp:33: error: expected `;' before &#8216;MyFrame&#8217;
hworld2.cpp:36: error: &#8216;wxEVT_COMMAND_MENU_SELECTED&#8217; was not declared in this scope
hworld2.cpp:37: error: &#8216;wxObjectEventFunction&#8217; was not declared in this scope
hworld2.cpp:37: error: &#8216;MyFrame&#8217; is not a class or namespace
hworld2.cpp:39: error: &#8216;MyFrame&#8217; is not a class or namespace
hworld2.cpp:41: error: &#8216;TRUE&#8217; was not declared in this scope
hworld2.cpp:42: error: &#8216;SetTopWindow&#8217; was not declared in this scope
hworld2.cpp: At global scope:
hworld2.cpp:46: error: &#8216;MyFrame&#8217; has not been declared
hworld2.cpp:46: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
hworld2.cpp:46: error: ISO C++ forbids declaration of &#8216;MyFrame&#8217; with no type
hworld2.cpp:46: error: ISO C++ forbids declaration of &#8216;wxString&#8217; with no type
hworld2.cpp: In function &#8216;int MyFrame(int)&#8217;:
hworld2.cpp:47: error: only constructors take base initializers
hworld2.cpp:47: error: &#8216;wxFrame&#8217; was not declared in this scope
hworld2.cpp:47: error: expected primary-expression before &#8216;)&#8217; token
hworld2.cpp:47: error: &#8216;title&#8217; was not declared in this scope
hworld2.cpp:47: error: &#8216;pos&#8217; was not declared in this scope
hworld2.cpp:47: error: &#8216;size&#8217; was not declared in this scope
hworld2.cpp:50: error: &#8216;wxMenuBar&#8217; was not declared in this scope
hworld2.cpp:50: error: &#8216;menuBar&#8217; was not declared in this scope
hworld2.cpp:50: error: expected type-specifier before &#8216;wxMenuBar&#8217;
hworld2.cpp:50: error: expected `;' before &#8216;wxMenuBar&#8217;
hworld2.cpp:52: error: &#8216;wxMenu&#8217; was not declared in this scope
hworld2.cpp:52: error: &#8216;menuFile&#8217; was not declared in this scope
hworld2.cpp:52: error: expected type-specifier before &#8216;wxMenu&#8217;
hworld2.cpp:52: error: expected `;' before &#8216;wxMenu&#8217;
hworld2.cpp:54: error: &#8216;_T&#8217; was not declared in this scope
hworld2.cpp:60: error: &#8216;SetMenuBar&#8217; was not declared in this scope
hworld2.cpp:63: error: &#8216;CreateStatusBar&#8217; was not declared in this scope
hworld2.cpp:65: error: &#8216;SetStatusText&#8217; was not declared in this scope
hworld2.cpp: At global scope:
hworld2.cpp:68: error: &#8216;MyFrame&#8217; is not a class or namespace
hworld2.cpp:68: error: variable or field &#8216;OnQuit&#8217; declared void
hworld2.cpp:68: error: &#8216;wxCommandEvent&#8217; was not declared in this scope
hworld2.cpp:68: error: &#8216;event&#8217; was not declared in this scope
hworld2.cpp:68: error: &#8216;WXUNUSED&#8217; was not declared in this scope
hworld2.cpp:73: error: &#8216;MyFrame&#8217; is not a class or namespace
hworld2.cpp:73: error: variable or field &#8216;OnAbout&#8217; declared void
hworld2.cpp:73: error: &#8216;wxCommandEvent&#8217; was not declared in this scope
hworld2.cpp:73: error: &#8216;event&#8217; was not declared in this scope
hworld2.cpp:73: error: &#8216;WXUNUSED&#8217; was not declared in this scope

```I'm hoping to be able to compile a windows executable, but if someone can show me how to make this into a Linux executable, that would be great too.

I have libwxgtk2.8, libwxbase2.8, mingw32, mingw32-binutils, and mingw32-runtime installed.  I am using Ubuntu 8.04.

**Edit:** MinGW's website hasn't been too helpful, at least not for me.

---

### Post by mriedel on 2009-02-20
First off, you don't compile scripts. This is C++ source. C++ is not a scripting language.

> hworld2.cpp:5:19: error: wx/wx.h: No such file or directory

This is your problem. Ignore all other errors, they are due to this one. The wx headers don't seem to be in the include path used by your compiler.

Edit: To compile anything against any library in C++, you need two things: The library itself (mostly that'll be a .dll on windows or a .so on *nix) and its header files. If you haven't got the wxWidgets headers yet, download them and put them where your compiler can find them. If you did download them, try reading about how mingw/gcc handle includes (headers) and where you have to put them or how you can make the compiler look for includes where you want it to.

---

### Post by dodle on 2009-02-20
Thanks, I didn't have the header files downloaded.  I put them in MinGW's search path, which seemed to make a difference.  But I'm still getting all kinds of errors.  

This is the output of the console, at least what was visible afterwards:```
/region.h: In member function &#8216;bool wxRegionBase::Intersect(const wxRect&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h:251: error: invalid use of incomplete type &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:38: error: forward declaration of &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h: In member function &#8216;bool wxRegionBase::Subtract(const wxRect&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h:256: error: invalid use of incomplete type &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:38: error: forward declaration of &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h: In member function &#8216;bool wxRegionBase::Xor(const wxRect&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h:261: error: invalid use of incomplete type &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:38: error: forward declaration of &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h: In member function &#8216;bool wxRegionWithCombine::Combine(wxCoord, wxCoord, wxCoord, wxCoord, wxRegionOp)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h:290: error: invalid use of incomplete type &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:38: error: forward declaration of &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h: In member function &#8216;bool wxRegionWithCombine::Combine(const wxRect&, wxRegionOp)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/region.h:295: error: invalid use of incomplete type &#8216;struct wxRegion&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:38: error: forward declaration of &#8216;struct wxRegion&#8217;
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:36,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:82: error: field &#8216;font&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:85: error: field &#8216;colFg&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:89: error: field &#8216;colBg&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1209: error: field &#8216;m_cursor&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1210: error: field &#8216;m_font&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1211: error: field &#8216;m_backgroundColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1212: error: field &#8216;m_foregroundColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1219: error: field &#8216;m_updateRegion&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h: In member function &#8216;const wxRegion& wxWindowBase::GetUpdateRegion() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:755: error: &#8216;m_updateRegion&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h: In member function &#8216;wxRegion& wxWindowBase::GetUpdateRegion()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:756: error: &#8216;m_updateRegion&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h: In member function &#8216;const wxCursor& wxWindowBase::GetCursor() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:844: error: &#8216;m_cursor&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h: In member function &#8216;wxWindow* wxWindowBase::GetGrandParent() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/window.h:1526: error: invalid use of incomplete type &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/utils.h:51: error: forward declaration of &#8216;struct wxWindow&#8217;
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/panel.h:15,
                 from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:38,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/generic/panelg.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/generic/panelg.h:31: error: invalid use of incomplete type &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/utils.h:51: error: forward declaration of &#8216;struct wxWindow&#8217;
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:39,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:119: error: invalid use of incomplete type &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/utils.h:51: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: In member function &#8216;virtual bool wxTopLevelWindowBase::IsActive()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:183: error: &#8216;FindFocus&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: In member function &#8216;virtual bool wxTopLevelWindowBase::IsVisible() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:235: error: &#8216;IsShown&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: In member function &#8216;virtual void wxTopLevelWindowBase::DoGetScreenPosition(int*, int*) const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:273: error: &#8216;DoGetPosition&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:353: error: expected class-name before &#8216;{&#8217; token
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: In constructor &#8216;wxTopLevelWindow::wxTopLevelWindow()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:356: error: &#8216;Init&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h: In constructor &#8216;wxTopLevelWindow::wxTopLevelWindow(wxWindow*, wxWindowID, const wxString&, const wxPoint&, const wxSize&, long int, const wxString&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:365: error: &#8216;Init&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/toplevel.h:366: error: &#8216;Create&#8217; was not declared in this scope
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:48,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:835: error: field &#8216;m_pen&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:836: error: field &#8216;m_brush&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:837: error: field &#8216;m_backgroundBrush&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:838: error: field &#8216;m_textForegroundColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:839: error: field &#8216;m_textBackgroundColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:840: error: field &#8216;m_font&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCBase::wxDCBase()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:121: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_pen&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:122: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_brush&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:123: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_backgroundBrush&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:124: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_textForegroundColour&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:125: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_textBackgroundColour&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:126: error: class &#8216;wxDCBase&#8217; does not have any field named &#8216;m_font&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;wxBitmap wxDCBase::GetAsBitmap(const wxRect*) const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:318: error: return type &#8216;struct wxBitmap&#8217; is incomplete
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:319: error: invalid use of incomplete type &#8216;struct wxBitmap&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:30: error: forward declaration of &#8216;struct wxBitmap&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxBrush& wxDCBase::GetBackground() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:528: error: &#8216;m_backgroundBrush&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxBrush& wxDCBase::GetBrush() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:529: error: &#8216;m_brush&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxFont& wxDCBase::GetFont() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:530: error: &#8216;m_font&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxPen& wxDCBase::GetPen() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:531: error: &#8216;m_pen&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxColour& wxDCBase::GetTextForeground() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:533: error: &#8216;m_textForegroundColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual const wxColour& wxDCBase::GetTextBackground() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:534: error: &#8216;m_textBackgroundColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual void wxDCBase::SetTextForeground(const wxColour&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:536: error: &#8216;m_textForegroundColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual void wxDCBase::SetTextBackground(const wxColour&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:538: error: &#8216;m_textBackgroundColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;virtual wxBitmap wxDCBase::DoGetAsBitmap(const wxRect*) const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:734: error: return type &#8216;struct wxBitmap&#8217; is incomplete
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:915: error: field &#8216;m_colFgOld&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCTextColourChanger::wxDCTextColourChanger(wxDC&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:892: error: class &#8216;wxDCTextColourChanger&#8217; does not have any field named &#8216;m_colFgOld&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In destructor &#8216;wxDCTextColourChanger::~wxDCTextColourChanger()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:901: error: &#8216;m_colFgOld&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:902: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In member function &#8216;void wxDCTextColourChanger::Set(const wxColour&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:907: error: &#8216;m_colFgOld&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:908: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:909: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:942: error: field &#8216;m_penOld&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCPenChanger::wxDCPenChanger(wxDC&, const wxPen&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:928: error: class &#8216;wxDCPenChanger&#8217; does not have any field named &#8216;m_penOld&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:928: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:930: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In destructor &#8216;wxDCPenChanger::~wxDCPenChanger()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:935: error: &#8216;m_penOld&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:936: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:969: error: field &#8216;m_brushOld&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCBrushChanger::wxDCBrushChanger(wxDC&, const wxBrush&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:955: error: class &#8216;wxDCBrushChanger&#8217; does not have any field named &#8216;m_brushOld&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:955: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:957: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In destructor &#8216;wxDCBrushChanger::~wxDCBrushChanger()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:962: error: &#8216;m_brushOld&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:963: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCClipper::wxDCClipper(wxDC&, const wxRegion&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:983: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCClipper::wxDCClipper(wxDC&, const wxRect&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:985: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In constructor &#8216;wxDCClipper::wxDCClipper(wxDC&, wxCoord, wxCoord, wxCoord, wxCoord)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:987: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h: In destructor &#8216;wxDCClipper::~wxDCClipper()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dc.h:989: error: invalid use of incomplete type &#8216;struct wxDC&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:36: error: forward declaration of &#8216;struct wxDC&#8217;
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:50,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dcmemory.h: In member function &#8216;void wxMemoryDCBase::SelectObject(wxBitmap&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dcmemory.h:35: error: invalid use of incomplete type &#8216;struct wxBitmap&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:30: error: forward declaration of &#8216;struct wxBitmap&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/dcmemory.h:36: error: invalid use of incomplete type &#8216;struct wxBitmap&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/gdicmn.h:30: error: forward declaration of &#8216;struct wxBitmap&#8217;
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:65,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:49: error: field &#8216;m_dataColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:50: error: field &#8216;m_custColours&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;void wxColourData::SetColour(const wxColour&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:38: error: &#8216;m_dataColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;const wxColour& wxColourData::GetColour() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:39: error: &#8216;m_dataColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;wxColour& wxColourData::GetColour()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:40: error: &#8216;m_dataColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: At global scope:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:125: error: field &#8216;m_fontColour&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:129: error: field &#8216;m_initialFont&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:130: error: field &#8216;m_chosenFont&#8217; has incomplete type
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In copy constructor &#8216;wxFontData::wxFontData(const wxFontData&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:65: error: class &#8216;wxFontData&#8217; does not have any field named &#8216;m_fontColour&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:65: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_fontColour&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:69: error: class &#8216;wxFontData&#8217; does not have any field named &#8216;m_initialFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:69: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_initialFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:70: error: class &#8216;wxFontData&#8217; does not have any field named &#8216;m_chosenFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:70: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_chosenFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;wxFontData& wxFontData::operator=(const wxFontData&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:81: error: &#8216;m_fontColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:81: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_fontColour&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:85: error: &#8216;m_initialFont&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:85: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_initialFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:86: error: &#8216;m_chosenFont&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:86: error: &#8216;const class wxFontData&#8217; has no member named &#8216;m_chosenFont&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;void wxFontData::SetColour(const wxColour&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:97: error: &#8216;m_fontColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;const wxColour& wxFontData::GetColour() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:98: error: &#8216;m_fontColour&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;void wxFontData::SetInitialFont(const wxFont&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:106: error: &#8216;m_initialFont&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;wxFont wxFontData::GetInitialFont() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:107: error: return type &#8216;struct wxFont&#8217; is incomplete
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:107: error: &#8216;m_initialFont&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;void wxFontData::SetChosenFont(const wxFont&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:109: error: &#8216;m_chosenFont&#8217; was not declared in this scope
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h: In member function &#8216;wxFont wxFontData::GetChosenFont() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:110: error: return type &#8216;struct wxFont&#8217; is incomplete
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/cmndata.h:110: error: &#8216;m_chosenFont&#8217; was not declared in this scope
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:84,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h: In member function &#8216;wxSize wxScrollHelper::GetTargetSize() const&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:181: error: invalid use of incomplete type &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/utils.h:51: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h: In constructor &#8216;wxScrolledWindow::wxScrolledWindow()&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:270: error: no matching function for call to &#8216;wxScrollHelper::wxScrollHelper(wxScrolledWindow* const)&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:236: note: candidates are: wxScrollHelper::wxScrollHelper(const wxScrollHelper&)
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:55: note:                 wxScrollHelper::wxScrollHelper(wxWindow*)
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h: In constructor &#8216;wxScrolledWindow::wxScrolledWindow(wxWindow*, wxWindowID, const wxPoint&, const wxSize&, long int, const wxString&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:277: error: no matching function for call to &#8216;wxScrollHelper::wxScrollHelper(wxScrolledWindow* const)&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:236: note: candidates are: wxScrollHelper::wxScrollHelper(const wxScrollHelper&)
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/scrolwin.h:55: note:                 wxScrollHelper::wxScrollHelper(wxWindow*)
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/wx.h:89,
                 from hworld2.cpp:5:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/sizer.h: In member function &#8216;void wxSizerItem::SetMinSize(const wxSize&)&#8217;:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/sizer.h:285: error: invalid use of incomplete type &#8216;struct wxWindow&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/utils.h:51: error: forward declaration of &#8216;struct wxWindow&#8217;
hworld2.cpp: At global scope:
hworld2.cpp:9: error: expected class-name before &#8216;{&#8217; token
hworld2.cpp: In function &#8216;wxAppConsole* wxCreateApp()&#8217;:
hworld2.cpp:13: error: cannot convert &#8216;MyApp*&#8217; to &#8216;wxAppConsole*&#8217; in return
hworld2.cpp: In function &#8216;MyApp& wxGetApp()&#8217;:
hworld2.cpp:13: error: &#8216;wxApp&#8217; has not been declared
hworld2.cpp: At global scope:
hworld2.cpp:17: error: invalid use of incomplete type &#8216;struct wxFrame&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/log.h:552: error: forward declaration of &#8216;struct wxFrame&#8217;
hworld2.cpp: In member function &#8216;virtual bool MyApp::OnInit()&#8217;:
hworld2.cpp:36: error: &#8216;class MyFrame&#8217; has no member named &#8216;Connect&#8217;
hworld2.cpp:38: error: &#8216;class MyFrame&#8217; has no member named &#8216;Connect&#8217;
hworld2.cpp:41: error: &#8216;class MyFrame&#8217; has no member named &#8216;Show&#8217;
hworld2.cpp:42: error: &#8216;SetTopWindow&#8217; was not declared in this scope
hworld2.cpp: In constructor &#8216;MyFrame::MyFrame(const wxString&, const wxPoint&, const wxSize&)&#8217;:
hworld2.cpp:47: error: type &#8216;wxFrame&#8217; is not a direct base of &#8216;MyFrame&#8217;
hworld2.cpp:50: error: invalid use of incomplete type &#8216;struct wxMenuBar&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/frame.h:26: error: forward declaration of &#8216;struct wxMenuBar&#8217;
hworld2.cpp:52: error: invalid use of incomplete type &#8216;struct wxMenu&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:37: error: forward declaration of &#8216;struct wxMenu&#8217;
hworld2.cpp:54: error: invalid use of incomplete type &#8216;struct wxMenu&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:37: error: forward declaration of &#8216;struct wxMenu&#8217;
hworld2.cpp:55: error: invalid use of incomplete type &#8216;struct wxMenu&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:37: error: forward declaration of &#8216;struct wxMenu&#8217;
hworld2.cpp:56: error: invalid use of incomplete type &#8216;struct wxMenu&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/event.h:37: error: forward declaration of &#8216;struct wxMenu&#8217;
hworld2.cpp:58: error: invalid use of incomplete type &#8216;struct wxMenuBar&#8217;
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/wx/frame.h:26: error: forward declaration of &#8216;struct wxMenuBar&#8217;
hworld2.cpp:60: error: &#8216;SetMenuBar&#8217; was not declared in this scope
hworld2.cpp:63: error: &#8216;CreateStatusBar&#8217; was not declared in this scope
hworld2.cpp:65: error: &#8216;SetStatusText&#8217; was not declared in this scope
hworld2.cpp: In member function &#8216;void MyFrame::OnQuit(wxCommandEvent&)&#8217;:
hworld2.cpp:70: error: &#8216;Close&#8217; was not declared in this scope
hworld2.cpp: In member function &#8216;void MyFrame::OnAbout(wxCommandEvent&)&#8217;:
hworld2.cpp:76: error: &#8216;wxMessageBox&#8217; was not declared in this scope

```I don't don't understand very much of this.

**Edit:** Am I missing some other header files?

---

### Post by wmcbrine on 2009-02-21
MinGW is for building Windows programs. For Linux, just use the standard gcc.

I fear from your wording that you're looking at this all the wrong way. The primary task before you is to learn C++ -- the specific compiler environment is secondary. To that end, you have to crawl before you can walk. Even if you know GUI programming in Python, you shouldn't jump straight into GUI programming in C++, without first getting a background in simple, console-based C++ programs. You should learn all about includes and libraries before you ever write a line of GUI code.

---

### Post by dodle on 2009-02-21
I think you're right.  I guess I have to swallow my pride and do some more command line programming.  Thanks for your advice.

---

### Post by SledgeHammer_999 on 2009-02-21
Solution straight from the wxWidgets tutorials [link](http://www.wxwidgets.org/docs/tutorials/hello.htm)
```
g++ hworld2.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld2
```
This builds it as a Linux app. To compile it as a windows app, I think, all you have to do is change **g++** to **i586-mingw32msvc-gcc** or **i586-mingw32msvc-g++**

---

### Post by dodle on 2009-02-21
Hey!  Thanks sledgehammer, that worked perfectly.  I'll read over that tutorial.

---

### Post by dodle on 2009-02-21
Well, everything worked fine for the Linux compiler, but I got errors with MinGW32:```
s` `wx-config --cxxflags` -o hworld2
i586-mingw32msvc-g++: unrecognized option '-pthread'
i586-mingw32msvc-g++: unrecognized option '-pthread'
In file included from /usr/include/wx-2.8/wx/defs.h:21,
                 from /usr/include/wx-2.8/wx/wx.h:15,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/platform.h:526:33: error: wx/msw/libraries.h: No such file or directory
In file included from /usr/include/wx-2.8/wx/generic/filedlgg.h:15,
                 from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/listctrl.h:32:33: error: wx/msw/listctrl.h: No such file or directory
In file included from /usr/include/wx-2.8/wx/wx.h:15,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/defs.h:2806: error: conflicting declaration ‘typedef struct GtkWidget* WXWidget’
/usr/include/wx-2.8/wx/defs.h:2597: error: ‘WXWidget’ has a previous declaration as ‘typedef void* WXWidget’
In file included from /usr/include/wx-2.8/wx/utils.h:21,
                 from /usr/include/wx-2.8/wx/cursor.h:41,
                 from /usr/include/wx-2.8/wx/event.h:22,
                 from /usr/include/wx-2.8/wx/wx.h:25,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/filefn.h:388: error: zero width for bit-field ‘wxAssert_389::BadFileSizeType’
In file included from /usr/include/wx-2.8/wx/generic/filedlgg.h:15,
                 from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/listctrl.h:44: error: expected class-name before ‘{’ token
/usr/include/wx-2.8/wx/listctrl.h: In constructor ‘wxListView::wxListView(wxWindow*, wxWindowID, const wxPoint&, const wxSize&, long int, const wxValidator&, const wxString&)’:
/usr/include/wx-2.8/wx/listctrl.h:55: error: ‘Create’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘void wxListView::Select(long int, bool)’:
/usr/include/wx-2.8/wx/listctrl.h:64: error: ‘SetItemState’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘void wxListView::Focus(long int)’:
/usr/include/wx-2.8/wx/listctrl.h:70: error: ‘SetItemState’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h:71: error: ‘EnsureVisible’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘long int wxListView::GetFocusedItem() const’:
/usr/include/wx-2.8/wx/listctrl.h:77: error: ‘GetNextItem’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘long int wxListView::GetNextSelected(long int) const’:
/usr/include/wx-2.8/wx/listctrl.h:82: error: ‘GetNextItem’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘bool wxListView::IsSelected(long int) const’:
/usr/include/wx-2.8/wx/listctrl.h:88: error: ‘GetItemState’ was not declared in this scope
/usr/include/wx-2.8/wx/listctrl.h: In member function ‘void wxListView::SetColumnImage(int, int)’:
/usr/include/wx-2.8/wx/listctrl.h:98: error: ‘SetColumn’ was not declared in this scope
In file included from /usr/include/wx-2.8/wx/gtk/filedlg.h:13,
                 from /usr/include/wx-2.8/wx/filedlg.h:210,
                 from /usr/include/wx-2.8/wx/wx.h:94,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/generic/filedlgg.h: At global scope:
/usr/include/wx-2.8/wx/generic/filedlgg.h:251: error: expected class-name before ‘{’ token

```Any idea what's wrong?

**Edit:** Fixed part of it.  I downloaded wxMSW and copied wxWidgets-2.8.9/include/wx/msw to /usr/include/wx-2.8/wx.  So now I get the following errors:```
s` `wx-config --cxxflags` -o hworld2
i586-mingw32msvc-g++: unrecognized option '-pthread'
i586-mingw32msvc-g++: unrecognized option '-pthread'
In file included from /usr/include/wx-2.8/wx/wx.h:15,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/defs.h:2806: error: conflicting declaration ‘typedef struct GtkWidget* WXWidget’
/usr/include/wx-2.8/wx/defs.h:2597: error: ‘WXWidget’ has a previous declaration as ‘typedef void* WXWidget’
In file included from /usr/include/wx-2.8/wx/utils.h:21,
                 from /usr/include/wx-2.8/wx/cursor.h:41,
                 from /usr/include/wx-2.8/wx/event.h:22,
                 from /usr/include/wx-2.8/wx/wx.h:25,
                 from hworld2.cpp:5:
/usr/include/wx-2.8/wx/filefn.h:388: error: zero width for bit-field ‘wxAssert_389::BadFileSizeType’

```This is the command I am using:```
i586-mingw32msvc-g++ hworld2.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld2

```

---

### Post by Can+~ on 2009-02-21
Mingw is mostly a port of GCC (notice the capitals) to windows, if you're in linux, just stick to the GCC provided in build-essential. And if you want to program portable, just avoid using those unix specific libraries.

---

