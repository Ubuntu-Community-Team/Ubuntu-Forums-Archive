---
title: "wxWidgets window z-order with tree event"
date: 2008-08-13
forum: Programming Talk
---

### Post by c174 on 2008-08-13
I'm using wxWidgets together with C++ to get a graphical user interface for my application. I work under Windows.

In the top level window I have a tree component. The idea is that clicking an item in the tree should open a new window. The problem is that the new window is alway put behind the top level window... I think this is because the tree receives focus after processing the wxEVT_COMMAND_TREE_ITEM_ACTIVATED event.

I have tried to solve the problem using Raise(), Lower(), Skip(), StopPropagation() at different places in the event handler, but so far without any luck.

If any one knows how to solve this I would be very happy. Thanks everybody :)

This piece of code has the mentioned problem:

```
#include "wx/wx.h"
#include "wx/treectrl.h"

// top window class
class Frame : public wxFrame {
public:
	Frame();
private:
	wxTreeCtrl* tree;
	void onActivate(wxTreeEvent&);	
};
		
Frame::Frame()
	: wxFrame(NULL, -1, wxT("Top level window"), wxDefaultPosition, wxSize(500,500))
{
	tree = new wxTreeCtrl(this, 1 );
	tree->AddRoot( "Root" );
	Connect( 1, wxEVT_COMMAND_TREE_ITEM_ACTIVATED, wxTreeEventHandler(Frame::onActivate));
}

void Frame::onActivate( wxTreeEvent& e )
{
	wxFrame* f = new wxFrame(this, -1, wxT("A new window"), wxDefaultPosition, wxSize(300,300));
	f->Show();
    // how to keep f raised..?
}

// main class
class Main : public wxApp {
public:
    virtual bool OnInit() {
		(new Frame())->Show();
		return true;
	}
};
IMPLEMENT_APP(Main)
```

---

### Post by c174 on 2008-08-18
I just managed to find a solution for this problem myself :) It works by adding an event handler for focus events on the tree. I have included the code below - maybe it can help other people who needs the same kind of functionality.

If somebody knows a better way to do this, then leave a reply as I would very much like to hear about it.

BTW: How can I add [SOLVED] in name of this thread??


```
#include "wx/wx.h"
#include "wx/treectrl.h"

// top window class
class Frame : public wxFrame {
public:
	Frame();
private:
	wxTreeCtrl* tree;
	wxFrame* aframe;
	void onActivate(wxTreeEvent&);	
	void onFocus(wxFocusEvent&);	
};
		
Frame::Frame()
	: wxFrame(NULL, -1, wxT("Top level window"), wxDefaultPosition, wxSize(500,500))
	, aframe(0)
{
	tree = new wxTreeCtrl(this, 1 );
	tree->AddRoot( "Root" );
	
	// need to process focus event at tree level, because focus events do not
	// propagate from child to parent (i.e. from tree to Frame)
	tree->Connect( 1, wxEVT_SET_FOCUS, wxFocusEventHandler(Frame::onFocus));	

	// although command events do progate from child to parent we need to handle
	// the command event at the tree level (child level) to get the right timing
	// of things
	tree->Connect( 1, wxEVT_COMMAND_TREE_ITEM_ACTIVATED, wxTreeEventHandler(Frame::onActivate));	
}

void Frame::onActivate( wxTreeEvent& e )
{
	// create new window and store pointer
	aframe = new wxFrame(this, 2, wxT("A new window"), wxDefaultPosition, wxSize(300,300));
	aframe->Show();
}

void Frame::onFocus( wxFocusEvent& e )
{
	// if pointer is valid raise window
	if( aframe ) aframe->Raise();

	// invalidate pointer in order to prevent aframe from being raise
	// definitely (any movement, clicking, etc in the windows will
	// generate focus events)
	aframe = 0;

        // let wxWidgets continue processing this event
        e.Skip();
}


// main class
class Main : public wxApp {
public:
    virtual bool OnInit() {
		(new Frame())->Show();
		return true;
	}
};
IMPLEMENT_APP(Main)
```

---

### Post by c174 on 2008-08-18
Oops! There is a bug in the code in the previous post. The program actually "works" (on my machine), but that is just by luck.

One should change the lines

```
tree->Connect( 1, wxEVT_SET_FOCUS, wxFocusEventHandler(Frame::onFocus));
tree->Connect( 1, wxEVT_COMMAND_TREE_ITEM_ACTIVATED, wxTreeEventHandler(Frame::onActivate));	
```
into

```
tree->Connect( 1, wxEVT_SET_FOCUS, wxFocusEventHandler(Frame::onFocus),NULL,this);
tree->Connect( 1, wxEVT_COMMAND_TREE_ITEM_ACTIVATED, wxTreeEventHandler(Frame::onActivate),NULL,this);	
```
This is needed because it is Frame that is supposed to handle the event (this = Frame) and not the wxWidgets class wxTreeCtrl. Passing NULL is a placeholder for optional user-data

---

