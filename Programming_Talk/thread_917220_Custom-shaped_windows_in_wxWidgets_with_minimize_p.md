---
title: "Custom-shaped windows in wxWidgets with minimize problems"
date: 2008-09-11
forum: Programming Talk
---

### Post by gargoylle_ltk on 2008-09-11
I currently find myself faced with having to write an application which must retain the look and feel of an already developed (not by myself) and deployed Windows application which uses windows with "custom" (think Winamp skin) shapes (yes, I am aware this violates every rule in the usability book - the requirements are clear, I have no say in this). The code I'm currently using looks something like this:
```
class CWindow : public wxTopLevelWindow {
	protected:
		wxBitmap     *frameBitmap;   /* bitmap that holds the "shape" of the window */
		wxRegion     *region;

		/* more stuff */

	public:
		CWindow( wxWindow *parent );

		/* other methods */
};

CWindow::CWindow( wxWindow *parent )
{
	/* load the desired bitmap into frameBitmap */

	/* create the window and set the shape */
	Create( parent, -1, wxT( "" ), wxPoint( topX, topY ), wxSize( frameBitmap->GetWidth(), frameBitmap->GetHeight() ), wxNO_BORDER | wxFRAME_SHAPED );
	region = new wxRegion;
	region->Union( *frameBitmap );

	SetShape( *region );
}
```
Then in OnInit() in my wxApp-derived class I have:
```
CWindow *wnd = new CWindow( NULL );
SetTopWindow( wnd );
wnd->Show( true );
```
This works in the sense that I do indeed get the desired custom-shape effect. However, I'm seeing some strange behaviour from window managers when handling such windows with regard to minimizing the application to the task bar:
[list]
[*]KDE's KWin works as expected and displays a "Minimize" item in the window context menu (the one I get when I right-click the task-bar button for my application) (tested on Gentoo, wxGTK 2.8.7.1-r1, kde 3.5.9)
[*]Gnome's window manager (as well as XFCE's, no idea if they're the same since I use KDE primarily) will not allow me to minimize the application under any circumstances: the "Minimize" item in the window context menu is disabled AND calling [wxTopLevelWindow::Iconize()](http://docs.wxwidgets.org/2.8.6/wx_wxtoplevelwindow.html#wxtoplevelwindowiconize) from the application has no effect whatsoever. (tested on Ubuntu 8.04, gnome 2.22.3, wxGTK 2.8.7.1). Another strange thing is that I can't Alt-drag the window when running under these WMs, while KWin will happilly allow me to do it.
[/list]
I have tried various combinations of window flags to no avail. I would appreciate any pointers anyone can give me as to how I can convince (at least) all of the above window managers to behave in a consistent manner (preferably allowing me to minimize my window :) ).

PS: while I'd much rather use Qt for the job wxGTK was prefered due to license considerations so I'd appreciate not being told to use another toolkit :)

---

### Post by gargoylle_ltk on 2008-09-11
I've come up with a small sample to better demonstrate my point (attached). You need to install the libwxgtk2.8-dev (2.6-dev should work as well) and g++ packages to compile this. Hope someone can take a look at it and point me in the right direction :)

---

