---
title: "[SOLVED] wxWidgets - Accelerators do not work?"
date: 2008-12-10
forum: Programming Talk
---

### Post by Zugzwang on 2008-12-10
Hi All, I've got the following minimal example for using wxWidgets (C++) with accelerators:

[PHP]
#include <wx/wx.h>

//======================================================================
// Declaration of the frame
//======================================================================
class MainFrame : public wxFrame {
public:
	
	// Constructors / Destructors
	MainFrame(wxWindow* parent);
	~MainFrame();

	// Event declaration
	enum
    	{
	        ID_HELLO = wxID_HIGHEST+1,
	};

	// Event implementation
	void OnHello(wxCommandEvent& WXUNUSED(event));

private:
        DECLARE_EVENT_TABLE()
};

//======================================================================
// Declaration/Definition of the Application
//======================================================================
class MyApp : public wxApp
{
private:

	public:

		bool OnInit()
		{
			wxFrame* frame = new MainFrame ( NULL );
			SetTopWindow ( frame );
			frame->Show();
			return true;
		}

		int OnExit() {
			return 0;
		}
};

DECLARE_APP ( MyApp );
IMPLEMENT_APP ( MyApp );


//======================================================================
// Definition of the main Window
//======================================================================
BEGIN_EVENT_TABLE ( MainFrame, wxFrame )
	EVT_MENU ( ID_HELLO, MainFrame::OnHello )
END_EVENT_TABLE()

MainFrame::MainFrame ( wxWindow* parent ) : wxFrame ( parent, -1, _ 
  ( "Test v.0.1" ), wxDefaultPosition, wxSize ( 800,600 ), 
  wxDEFAULT_FRAME_STYLE )
{

	//=================================
	// Create accelerators
	//=================================
	wxAcceleratorEntry entries[1];
	entries[0].Set(wxACCEL_CTRL,  (int) 'X',     ID_HELLO);

	wxAcceleratorTable accel(WXSIZEOF(entries), entries);
        SetAcceleratorTable(accel);
}

MainFrame::~MainFrame()
{
}

void MainFrame::OnHello ( wxCommandEvent& WXUNUSED ( event ) )
{
	std::cout << "I'm here!!!!!\n";
	wxMessageBox ( _ ( "Hello" ), _ ( "About Test v.0.1" ), wxOK, this );
}
[/PHP]

The problem is that when running the application, focussing the window and pressing CTRL+X, nothing happens at all. Does anybody know how to fix this problem?

I'm using the following command for compilation:
```

g++ -o test main.cpp `wx-config --libs --cxxflags aui,html,adv,core,xml,base`

```

Furthermore, "wx-config --version-full" yields "2.8.7.1". The only installed configuration is "gtk2-unicode-release-2.8".

Thanks!

---

### Post by Zugzwang on 2008-12-10
So it seems as if the wxForums are not indexed in Google. A closer look revealed the information that the accelerators have to be defined for each sub-component of the window (I still wonder why they don't work if there aren't any). However, [this page]("http://http://wiki.wxwidgets.org/Catching_key_events_globally") contain alternative ways for registering application-wide hot-keys that work.

---

