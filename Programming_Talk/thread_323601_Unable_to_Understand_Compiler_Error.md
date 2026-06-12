---
title: "Unable to Understand Compiler Error"
date: 2006-12-22
forum: Programming Talk
---

### Post by studiesrule on 2006-12-22
I've been learning wxWidgets, and am trying to implement: wxInputTextStream in a program of mine. However, whenever I compile, I get this error:

variable ‘wxTextInputStream index’ has initializer but incomplete type
('index' is the name of my variable)

I have absolutely no idea what this error means, let alone how to get around it.

I am using gcc 4.1.2, and the wxWidgets 2.8.0 library.

---

### Post by cgrebeld on 2006-12-22
How are you trying to use it?  Maybe post your code.

---

### Post by studiesrule on 2006-12-23
Well, my own code is awfully similar to the tutorial example, but I'll post both. I've excluded the general code of creating a MyApp class and all. I am using this code in a frame or in a panel (I have tried both). I try to use it by taking the outputted text and using it as an address. I've also tried pasting it as message box text just to see if that made a diff.

Tutorial:
```

wxFileInputStream input( wxT(&#8220;mytext.txt&#8221;) );
wxTextInputStream text( input );
wxUint8 i1;
float f2;
wxString line;
text >> i1;       // read an 8 bit integer.
text >> i1 >> f2; // read an 8 bit integer followed by float.
text >> line;     // read a text line

```
\

My Code:
```

wxFileInputStream input( "mytext.txt" );
wxTextInputStream text( input );
wxString line;

text >> line;     // read a text line
//Message Box time!!!
wxMessageBox(line,_T("About Me!"),wxOK);

```

I have included the header : wx/wfstream.h in both.


My text file says:
Wow! This worked

However, that shouldn't cause a compile time error. Just posted it anyway.

---

### Post by Wybiral on 2006-12-23
You should really post more of the code than just a little snippet... I don't have much experience with wx, but I've been using C++ for some time now, you should post more of the program, preferably all. I have no idea why "wxTextInputStream index" would come up in an incomplete type error unless one of the functions in this source code isn't being used properly (seeing how you yourself haven't initiated it). So either something else in the code, or the tutorial doesn't explain proper usage...

---

### Post by studiesrule on 2006-12-23
sure. I just thought that it was unnessecary, and that it would be too much to post in a forum. Ok here's the full code. All the rest of it works, execpt this bit.

```

// My First wxWidgets App 0.2

#include "wx/wx.h"
#include "wx/wfstream.h"

// First create your own version of the class wxApp. This is your main function

class MyApp: public wxApp  //Note that this doesn't from an instance
{
public:
	//initilize the app using OnInit, which tells whether the apps' been succesfully made or not
	virtual bool OnInit();
};

// Then create window
class MyFrame: public wxFrame
{
public:
	//the constructor
	MyFrame (const wxString& title);

	//Also two simple event handlers
	void OnQuit(wxCommandEvent& event);
	void OnAbout(wxCommandEvent& event);

private:
	// Create the event table for this frame
	DECLARE_EVENT_TABLE()
};

//Now define the event table

BEGIN_EVENT_TABLE(MyFrame,wxFrame)
	EVT_MENU(wxID_EXIT,MyFrame::OnQuit)
	EVT_MENU(wxID_ABOUT,MyFrame::OnAbout)
END_EVENT_TABLE()

//Now initilize the application. This creates an instance of MyApp
IMPLEMENT_APP(MyApp)

//Now, We shall deal with the function OnInit
bool MyApp::OnInit()
{
	//Determine succesful implementation or not
	if(!wxApp::OnInit())
		return false;

	//Now, lets create a frame to go in this app.
	MyFrame *frame = new MyFrame(_T("Teju's First wxApp!"));
	//Remember this frame is NOT instantly visible
	frame->Show(true);

	//Let the event loop go on
	return true;
}

// It's time for the frame's constructor

MyFrame::MyFrame(const wxString& title)
	:wxFrame(NULL,wxID_ANY,title)		//This uses the inherited constructor, passing (the parent window, type of window, title)
{
	//Lets create our menus

	wxMenu *fileMenu = new wxMenu;
	wxMenu *helpMenu = new wxMenu;

	// Now lets add entries into these menus.

	fileMenu->Append(wxID_EXIT,_T("E&xit \tAlt-Q"),_T("Asltla-vista!"));  //The Alt-Q thing REALLY WORKS!!!
	helpMenu->Append(wxID_ABOUT,_T("About... \tF1"),_T("The title speaks for itself"));

	//We need a menu bar to hold these menus

	wxMenuBar *menuBar = new wxMenuBar();

	menuBar->Append(fileMenu,_T("&File"));
	menuBar->Append(helpMenu,_T("&About"));

	//Finally, we'll add this onto our frame.

	SetMenuBar(menuBar);

	//On final touch. We'll create a status bar.

	CreateStatusBar(3); //No. indicate divisions
	SetStatusText("Hello World");
}

//Now onto the event handlers

void MyFrame::OnQuit(wxCommandEvent& event)
{
	Close(true); //Pretty straight-forward
}

void MyFrame::OnAbout(wxCommandEvent& event)
{
	wxFileInputStream input( "mytext.txt" );
	wxTextInputStream text( input );
	wxString line;

	text >> line;     // read a text line
	//Message Box time!!!
	wxMessageBox(line,_T("About Me!"),wxOK);
}
	//That's a wrap


```

All these comments were made by myself, as I was trying to navigate the language. I guess they might be useful to you.

I have a nagging suspicision that my error is also part of my make file. I made to makefile on my own, basically copying the makefile code of the samples, and weeding out the unnessecary stuff. Here is the makefile:
```

## Generic wxWidgets makefile

CC= g++

FILE=wxhello

WX_PATH=/home/teju/usr/wxWidgets-2.8.0

WX_INCL= -I$(WX_PATH)/lib/wx/include/gtk2-ansi-release-2.8 -I$(WX_PATH)/include -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include

CXX_FLAGS= -D__WXGTK__ -I. -DWXUSINGDLL -DWX_PRECOMP -DNO_GCC_PRAGMA -DGTK_NO_CHECK_CASTS -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -O2 -fno-strict-aliasing -pthread -Wall -Wundef -Wno-ctor-dtor-privacy

WX_LIBS= -pthread -L$(WX_PATH)/lib -Wl,-rpath,$(WX_PATH)/lib -lwx_gtk2_core-2.8 -lwx_base-2.8 -pthread -Wl,--version-script,$(WX_PATH)/version-script -lz -ldl -lm  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -lXinerama -lpng -lz

$(FILE): $(FILE).o
	$(CC) -o $(FILE) $(FILE).o $(WX_LIBS)

$(FILE).o: $(FILE).cpp
	$(CC) -c -o $(FILE).o $(CXX_FLAGS) $(WX_INCL) $(FILE).cpp

clean:
	rm $(FILE) $(FILE).o

```

Thanks a lot for your help.

---

### Post by studiesrule on 2006-12-23
I have another question, related to makefiles. I have tried to make makefiles according to the wxWidgets book, and docs, atleast for minimal apps. I have followed instructions to the dot, which are as follows:
```

g++ myfoo.cpp `wx-config --libs --cxxflags` -o myfoo

```
I have later tried to use bakefiles, hoping that the full makefile would do me good. I first tried using the sample example given, which is the wx minimal sample. The makefile generated is:

```

# =========================================================================
#     This makefile was generated by
#     Bakefile 0.2.1 (http://bakefile.sourceforge.net)
#     Do not modify, all changes will be overwritten!
# =========================================================================



# -------------------------------------------------------------------------
# These are configurable options:
# -------------------------------------------------------------------------

# C++ compiler 
CXX = g++

# Standard flags for C++ 
CXXFLAGS = 

# Standard preprocessor flags (common for CC and CXX) 
CPPFLAGS = 

# Standard linker flags 
LDFLAGS = 

# Location and arguments of wx-config script 
WX_CONFIG = wx-config

# C++ flags to use with wxWidgets code 
WX_CXXFLAGS = `$(WX_CONFIG) --cxxflags`



# -------------------------------------------------------------------------
# Do not modify the rest of this file!
# -------------------------------------------------------------------------

### Variables: ###

CPPDEPS = -MT$@ -MF`echo $@ | sed -e 's,\.o$$,.d,'` -MD
MINIMAL_CXXFLAGS =  -g  $(WX_CXXFLAGS) $(CPPFLAGS) $(CXXFLAGS)
MINIMAL_OBJECTS =  \
	minimal_minimal.o

### Conditionally set variables: ###



### Targets: ###

all: minimal

install: all

uninstall: 

clean: 
	rm -f ./*.o
	rm -f ./*.d
	rm -f minimal

minimal: $(MINIMAL_OBJECTS)
	$(CXX) -o $@ $(MINIMAL_OBJECTS) $(LDFLAGS)  -g  `$(WX_CONFIG) --libs core,base`

minimal_minimal.o: ./minimal.cpp
	$(CXX) -c -o $@ $(MINIMAL_CXXFLAGS) $(CPPDEPS) $<

.PHONY: all install uninstall clean


# Dependencies tracking:
-include ./*.d

```

The files compiled fine, and even linked ok. But on running, I get:
```

libwx_gtk2_core-2.8.so.0: cannot open shared object file: No such file or directory

```

I don't know where it is looking, but there is an existing file in the wx libraries, [wx src directory] / lib/ libwx_gtk2_core-2.8.so.0

I have checked and verified that the wx-config returns the wxWidgets 2.8.0 directory that I have compiled. I have no idea what to do now.

---

