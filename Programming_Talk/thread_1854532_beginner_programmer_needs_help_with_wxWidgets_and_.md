---
title: "beginner programmer needs help with wxWidgets and Code::Blocks!"
date: 2011-10-04
forum: Programming Talk
---

### Post by Mongrel714 on 2011-10-04
I took some programming courses in college and am now trying to get back into it. I'm most experienced with C++ and wanted to learn some GUI stuff, so I looked into wxWidgets. I've installed all of the necessary components (following a how-to guide online) and am just getting started with tutorials for it and I have come across a few (probably blatantly obvious) questions that none of the tutorials seem to cover. If anyone can help me it would be greatly appreciated (I'm doing this in Windows 7 if it matters).

First of all, when I start a new wxWidgets project it always begins with a few folders and some code already written. There's the "Sources" folder with "GUIFrame.cpp" "testApp.cpp" and "testMain.cpp" the "Headers" folder with "GUIFrame.h" "testApp.h" "testMain.h" and "wx_pch.h" the "Resources" folder with "resource.rc" and the "Others" folder with "WxWozFrame.fbp." What are these files? Which one(s) should I be writing in for my program? Or should I be creating a completely new file? I assume that it's either the "App" file or the "Main" file in the "Sources" folder that I should be writing in. Do I keep all the code already in there if I copy-paste test code into it? Or should I delete it? If I keep it, where should my test code go? For example, if I were to want to input this sample code into Code::Blocks in order to run it and test its result, how would I do so?
```
// Name: minimal.cpp
// Purpose: Minimal wxWidgets sample
// Author: Julian Smart
#include &#8220;wx/wx.h&#8221;
// Declare the application class
class MyApp : public wxApp
{
public:
// Called on application startup
virtual bool OnInit();
};
// Declare our main frame class
class MyFrame : public wxFrame
{
public:
// Constructor
MyFrame(const wxString& title);
// Event handlers
void OnQuit(wxCommandEvent& event);
void OnAbout(wxCommandEvent& event);
private:
// This class handles events
DECLARE_EVENT_TABLE()
};
// Implements MyApp& GetApp()
DECLARE_APP(MyApp)
// Give wxWidgets the means to create a MyApp object
IMPLEMENT_APP(MyApp)
// Initialize the application
bool MyApp::OnInit()
{
// Create the main application window
MyFrame *frame = new MyFrame(wxT(&#8220;Minimal wxWidgets App&#8221;));
// Show it
frame->Show(true);
// Start the event loop
return true;
}
// Event table for MyFrame
BEGIN_EVENT_TABLE(MyFrame, wxFrame)
EVT_MENU(wxID_ABOUT, MyFrame::OnAbout)
EVT_MENU(wxID_EXIT, MyFrame::OnQuit)
END_EVENT_TABLE()
void MyFrame::OnAbout(wxCommandEvent& event)
{
wxString msg;
msg.Printf(wxT(&#8220;Hello and welcome to %s&#8221;),
wxVERSION_STRING);
wxMessageBox(msg, wxT(&#8220;About Minimal&#8221;),
wxOK | wxICON_INFORMATION, this);
}
void MyFrame::OnQuit(wxCommandEvent& event)
{
// Destroy the frame
Close();
}
#include &#8220;mondrian.xpm&#8221;
MyFrame::MyFrame(const wxString& title)
: wxFrame(NULL, wxID_ANY, title)
{
// Set the frame icon
SetIcon(wxIcon(mondrian_xpm));
// Create a menu bar
wxMenu *fileMenu = new wxMenu;
// The &#8220;About&#8221; item should be in the help menu
wxMenu *helpMenu = new wxMenu;
helpMenu->Append(wxID_ABOUT, wxT(&#8220;&About...\tF1&#8221;),
wxT(&#8220;Show about dialog&#8221;));
fileMenu->Append(wxID_EXIT, wxT(&#8220;E&xit\tAlt-X&#8221;),
wxT(&#8220;Quit this program&#8221;));
// Now append the freshly created menu to the menu bar...
wxMenuBar *menuBar = new wxMenuBar();
menuBar->Append(fileMenu, wxT(&#8220;&File&#8221;));
menuBar->Append(helpMenu, wxT(&#8220;&Help&#8221;));
// ... and attach this menu bar to the frame
SetMenuBar(menuBar);
// Create a status bar just for fun
CreateStatusBar(2);
SetStatusText(wxT(&#8220;Welcome to wxWidgets!&#8221;));
}
```

Also, when I first opened a wxWidgets project in Code::Blocks a popup appeared telling me something to the effect of "codeblocks does not know the global compiler variable." Later on when I closed Code::Blocks, reopened it, and opened a new wxWidgets project the message had disappeared and I haven't seen it since. Is this a problem I should be concerned about? Or did it fix itself? If it is something that needs to be fixed, how do I fix it?

I'm very eager to start implementing this GUI stuff since there's a project I've undertaken that pretty much needs it. Any help is greatly appreciated!

---

