---
title: "[C++/wx] Segfault when wxDialog Closes"
date: 2010-06-14
forum: Programming Talk
---

### Post by dodle on 2010-06-14
This is the class method that creates and shows a dialog.  I don't get any errors on Windows, but on Linux with Gtk the app crashes when I close the dialog.  It has something to do with the child widgets and box sizers.  If I remove the widgets or sizers there is no segfault.  

[php]void MainWindow::OnHelp(wxMenuEvent& event)
{
	wxDialog help(this, -1, _T("Help"), wxDefaultPosition, wxDefaultSize, wxDEFAULT_DIALOG_STYLE);

	#ifdef WIN32
	help.SetIcon(ICON1);
	#endif

	wxRichTextCtrl textarea(&help, -1, wxEmptyString, wxDefaultPosition, wxDefaultSize, wxRE_READONLY);
	wxButton ok(&help, wxID_OK);

	wxString helptext(_T("How to use:\n\
  Selecting a mode:\n\
    The four icons on the left side of the toolbar represent the\n\
    different modes.  Use the \"Tab\" key to toggle between modes,\n\
    or click on an icon with the mouse.\n\
\n\
  Alphabet Mode:\n\
    The first icon on the left is the Alphabet Mode.  Press the\n\
    letter on the keyboard that is displayed on the screen to\n\
    cycle through the English alphabet.  Finish by finding all\n\
    the letters, A-Z.\n\
\n\
  Other Modes:\n\
    In all other modes, simply press a key on the keyboard to see\n\
    a letter with a related image and description.\n\
\n\
  Sounds:\n\
    Press the spacebar to hear the name of the pictured object."));

	textarea.SetValue(helptext);

	helptext.Clear();

	wxBoxSizer help_sizer(wxVERTICAL);
	help_sizer.Add(&textarea, 1, wxEXPAND);
	help_sizer.Add(&ok, 0, wxALIGN_CENTER);

	help.SetAutoLayout(true);
	help.SetSizer(&help_sizer);
	help.Layout();

	help.ShowModal();
}[/php]

**Edit:** This seems to be the right way to do it:

Create the dialog in the constructor:
[php]    // Help Dialog
	help = new wxDialog(this, -1, _T("Help"), wxDefaultPosition, wxDefaultSize, wxDEFAULT_DIALOG_STYLE);

	#ifdef WIN32
	help->SetIcon(ICON1);
	#endif

	wxRichTextCtrl *textarea = new wxRichTextCtrl(help, -1, wxEmptyString, wxDefaultPosition, wxDefaultSize, wxRE_READONLY);
	wxButton *ok = new wxButton(help, wxID_OK);

	wxString helptext(_T("How to use:\n\
  Selecting a mode:\n\
    The four icons on the left side of the toolbar represent the\n\
    different modes.  Use the \"Tab\" key to toggle between modes,\n\
    or click on an icon with the mouse.\n\
\n\
  Alphabet Mode:\n\
    The first icon on the left is the Alphabet Mode.  Press the\n\
    letter on the keyboard that is displayed on the screen to\n\
    cycle through the English alphabet.  Finish by finding all\n\
    the letters, A-Z.\n\
\n\
  Other Modes:\n\
    In all other modes, simply press a key on the keyboard to see\n\
    a letter with a related image and description.\n\
\n\
  Sounds:\n\
    Press the spacebar to hear the name of the pictured object."));

	textarea->SetValue(helptext);

	wxBoxSizer *help_sizer = new wxBoxSizer(wxVERTICAL);
	help_sizer->Add(textarea, 1, wxEXPAND);
	help_sizer->Add(ok, 0, wxALIGN_CENTER);

	help->SetAutoLayout(true);
	help->SetSizer(help_sizer);
	help->Layout();
[/php]

Then use the class method to display it:
[php]void MainWindow::OnHelp(wxMenuEvent& event)
{
    help->ShowModal();
}[/php]

---

