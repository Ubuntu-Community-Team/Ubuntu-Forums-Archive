---
title: "wxWidgets painting event issues"
date: 2008-05-24
forum: Programming Talk
---

### Post by jonathanmotes on 2008-05-24
I've been working with wxWidgets for a couple of weeks and I am writing a program to help improve my skills. My program simply shows an image and writes text over the image. 

I want it to automatically update the size of the image as I resize the frame, but I'm having trouble figuring this part out. Currently, it paints the new (resized) image *below* the old one that existed before the resize. I can't seem to figure out a way to completely overwrite the old paint, mainly because I create a new instance of my device context for each resize event (so I apparently don't have control over the previous device context).

Can anyone help me figure this out so that I can get my program to do what I need it to do? The code and resources are attached!

Thanks very much!

image.h
```
#ifndef IMAGE_H_
#define IMAGE_H_

//not all of these are being used at the moment
#include "wx/wxprec.h"
#include "wx/wx.h"
#include "wx/image.h"
#include "wx/file.h"
#include "wx/filename.h"
#include "wx/mstream.h"
#include "wx/wfstream.h"
#include "wx/quantize.h"

class MyCanvas;

class MyFrame: public wxFrame
{
public:
    MyFrame();

    void OnAbout( wxCommandEvent &event );
    void OnNewFrame( wxCommandEvent &event );
    void OnQuit( wxCommandEvent &event );

    MyCanvas *m_canvas;

private:
    DECLARE_DYNAMIC_CLASS(MyFrame)
    DECLARE_EVENT_TABLE()
};

// MyApp

class MyApp: public wxApp
{
public:
    virtual bool OnInit();    
};

// MyCanvas

class MyCanvas: public wxScrolledWindow
{
public:
    MyCanvas( wxWindow *parent, wxWindowID, const wxPoint &pos, const wxSize &size );
    ~MyCanvas();
    void Painting(wxDC&, wxString, int, int);
    //void PrintCenteredText(const wxString& text, wxDC& dc, wxWindow* win);
    void OnPaint( wxPaintEvent &event);
    void OnEraseBackground(wxEraseEvent& event);
    wxBitmap  my_horse_png;
    wxBitmap  my_horse_jpeg;
    wxBitmap my_toucan;

private:
    DECLARE_EVENT_TABLE()
};

//used by MyFrame event table
enum
{
    ID_QUIT  = wxID_EXIT,
    ID_ABOUT = wxID_ABOUT,
};

#endif /*IMAGE_H_*/
```

image.cpp
```
/**************************************************************
 * This is the application implementation
 * ************************************************************/
#include "image.h"
#include<iostream>
using namespace std;

IMPLEMENT_APP(MyApp)

IMPLEMENT_DYNAMIC_CLASS( MyFrame, wxFrame )

//MyFrame event table
BEGIN_EVENT_TABLE(MyFrame,wxFrame)
  EVT_MENU    (ID_ABOUT, MyFrame::OnAbout)
  EVT_MENU    (ID_QUIT,  MyFrame::OnQuit)
END_EVENT_TABLE()

//MyCanvas event table
BEGIN_EVENT_TABLE(MyCanvas, wxScrolledWindow)
    EVT_PAINT(MyCanvas::OnPaint)
END_EVENT_TABLE()

//-----------------------------------------------------------------------------
// MyApp
//-----------------------------------------------------------------------------

bool MyApp::OnInit()
{
	cout << "ON INIT CALLED!" << endl;
    wxInitAllImageHandlers();

    wxFrame *frame = new MyFrame();
    frame->Show( true );

    return true;
}

//MyFrame (constructor) implementation 
    //size is currently 16:10 ratio
MyFrame::MyFrame() : wxFrame( (wxFrame *)NULL, wxID_ANY, _T("Text Over Image"), wxPoint(20, 20), wxSize(800, 555) )
{
  wxMenuBar *menu_bar = new wxMenuBar();

  wxMenu *menuImage = new wxMenu;

  menuImage->AppendSeparator();
  menuImage->Append( ID_ABOUT, _T("&About..."));
  menuImage->AppendSeparator();
  menuImage->Append( ID_QUIT, _T("E&xit\tCtrl-Q"));
  menu_bar->Append(menuImage, _T("&Image"));

  SetMenuBar( menu_bar );

#if wxUSE_STATUSBAR
  CreateStatusBar(2);
  int widths[] = { -1, 100 };
  SetStatusWidths( 2, widths );
#endif // wxUSE_STATUSBAR
  
  cout << "NEW FRAME CONSTRUCTOR CALLED!" << endl;

  m_canvas = new MyCanvas( this, wxID_ANY, wxPoint(0,0), wxSize(10,10) );

  // 500 width * 2750 height
  //m_canvas->SetScrollbars( 10, 10, 50, 50 );
}

void MyFrame::OnQuit( wxCommandEvent &WXUNUSED(event) )
{
  Close(true);
}

void MyFrame::OnAbout( wxCommandEvent &WXUNUSED(event) )
{
  (void)wxMessageBox( _T("Text Over Image Demo\n")
                      _T("By Jonathan Motes (c) 2008"),
                      _T("Text Over Image"), wxICON_INFORMATION | wxOK );
}

MyCanvas::MyCanvas( wxWindow *parent, wxWindowID id, const wxPoint &pos, const wxSize &size )
    : wxScrolledWindow( parent, id, pos, size, wxSUNKEN_BORDER )
{
    SetBackgroundColour(* wxBLACK);
    cout << "NEW CANVAS CONSTRUCTOR CALLED!" << endl;

    //wxBitmap bitmap(100, 100);    

}

MyCanvas::~MyCanvas()
{}

void MyCanvas::Painting(wxDC& dc, wxString message, int x, int y)
{
	dc.DrawText( _T(message), x, y);
	dc.DrawText( _T("I'm scary!\nYou are too!"), x, y+45);
	
}
void MyCanvas::OnPaint( wxPaintEvent &WXUNUSED(event))
{
	cout << "NEW PAINT!" << endl;
    wxPaintDC dc(this);
    PrepareDC(dc);
    
    //doesn't work because it can only clear items in the current instance
    //dc.Clear();

    //wxImage image(_T("beach.jpg"), wxBITMAP_TYPE_JPEG);
    wxImage image(_T("less_than.jpg"), wxBITMAP_TYPE_JPEG);
    //wxImage image(_T("wider_than.png"), wxBITMAP_TYPE_PNG);

    int newWidth;
    int newHeight;
    int height;
    int width;    
    int screenHeight;
    int screenWidth;
    int startX;
    int startY;
    bool scale = true;
    
    //initialize screen dimensions
    wxWindow* win = this;
    
    wxSize size = win->GetClientSize();
    
    cout << "X: " << size.x << endl;
    cout << "Y: " << size.y << endl;
    
    screenHeight = size.y;
    screenWidth = size.x;

    //1. get size of image
    height = image.GetHeight();
    width = image.GetWidth(); 

    /***************************************************************
     * Scale Option
    ***************************************************************/
    if(scale)
    {
        //resize and center horizontally or vertically to fit screen appropriately
        
        //check ratio - if wider than current screen ratio, make image the width of the screen and center vertically
        //wider means ratio of width/height will be larger
        
        //is image ratio wider than system screen ratio?
        if((float)width/(float)height >= (float)screenWidth/(float)screenHeight)
        {
            //make image the width of the screen
            newWidth = screenWidth;
            newHeight = ((float)height/(float)width) * screenWidth;
            
            //center vertically

            startX = 0; 
            //vertical center point of screen - half of image height
            startY = (screenHeight/2) - (newHeight/2);
        }
        else
        {
            //make image the height of the screen
            newHeight = screenHeight;
            newWidth = ((float)width/(float)height) * screenHeight;
        
            //center horizontally
            
            //horizontal center point of screen - half of image width
            startX = (screenWidth/2) - (newWidth/2); 
            startY = 0;
        }
    }
    else
    {
    	//use fill screen option
    	
    	newHeight = screenHeight;
    	newWidth = screenWidth;
    	
    	startX = 0;
    	startY = 0;
    }

    image.Rescale(newWidth, newHeight,400);    
    
    wxBitmap bitmap(image);
    
    //wxBitmap bitmap(_T("./beach.jpg"), wxBITMAP_TYPE_JPEG);

    //dc.Clear();
    
    if (bitmap.Ok())
    {
        dc.DrawBitmap(bitmap, startX, startY);
    }

    wxString message = "Hello There!";

    wxFont font(22, wxFONTFAMILY_DEFAULT, wxNORMAL, wxBOLD, false);

    dc.SetFont(font);
    dc.SetTextForeground(*wxWHITE);
    dc.DrawText( _T(message), (screenWidth/3), 135 );
    
    wxString message2 = "I'm here too!";
    
    Painting(dc, message2, (screenWidth/3), 180);
}
```

---

