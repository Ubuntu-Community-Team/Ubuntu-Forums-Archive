---
title: "[C++/wx] Can't Add Widgets to wxDialog"
date: 2010-05-26
forum: Programming Talk
---

### Post by dodle on 2010-05-26
I've always been able to add widgets to a custom dialog with wxPython, but I am having trouble doing it with wxWidgets in C++.  According to [Zetcode](http://zetcode.com/tutorials/wxwidgetstutorial/dialogs/) I should be able to do it.

Here is the member function that contains my dialog:
[php]void MainWindow::OnHelp(wxMenuEvent& event)
{
	wxDialog help(this, -1, _T("Help"), wxDefaultPosition, wxDefaultSize, wxDEFAULT_DIALOG_STYLE);
	help.SetIcon(ICON1);
	
	wxTextCtrl textarea(help, -1, wxEmptyString);
	
	help.ShowModal();
	help.Destroy();
}[/php]

When I try to compile, this is the error that comes up:
```
In member function `void MainWindow::OnHelp(wxMenuEvent&)':
error: no matching function for call to `wxTextCtrl::wxTextCtrl
(wxDialog&, int, const wxChar*&)'
textctrl.h:278: note: candidates are: wxTextCtrl:
:wxTextCtrl(const wxTextCtrl&)
textctrl.h:29: note:                 wxTextCtrl::
wxTextCtrl(wxWindow*, wxWindowID, const wxString&, const wxPoint&, const wxSize&
, long int, const wxValidator&, const wxString&)
textctrl.h:21: note:                 wxTextCtrl::
wxTextCtrl()
```

---

### Post by dwhitney67 on 2010-05-26
The compiler is telling you that wxTextCtrl only support three flavors of constructors:  a default constructor with no args, another constructor that accepts 8 args, and finally a copy constructor.

I cannot tell if any of the parameters in the 8-arg constructor have been assigned default values.  But taking a quick glance at the API, it would appear that you need to pass a pointer to your wxWidget as the first arg.

Consider trying something like:
```

wxDialog* help = new wxDialog(this, -1, _T("Help"), wxDefaultPosition, wxDefaultSize, wxDEFAULT_DIALOG_STYLE);

...

wxTextCtrl* textctrl = new wxTextCtrl textarea(help, wxID_ANY, wxEmptyString);

...

```
Anyhow, C++ is not the issue here; it is your lack of enthusiasm with regards to reading the wxWidget documentation (ie. API docs).

---

### Post by dodle on 2010-05-27
This is what worked for me:
[php]void MainWindow::OnHelp(wxMenuEvent& event)
{
	wxDialog help(this, -1, _T("Help"), wxDefaultPosition, wxDefaultSize, wxDEFAULT_DIALOG_STYLE);
	help.SetIcon(ICON1);
	
	wxTextCtrl textarea(&help, -1, wxEmptyString);
	
	help.ShowModal();
	help.Destroy();
}[/php]

---

