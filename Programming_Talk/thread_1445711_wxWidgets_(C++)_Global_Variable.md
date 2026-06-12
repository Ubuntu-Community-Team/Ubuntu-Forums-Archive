---
title: "wxWidgets (C++) Global Variable"
date: 2010-04-02
forum: Programming Talk
---

### Post by JustYakov on 2010-04-02
I have two windows: one of them is the main window, and the other one is a special "Edit Names" dialog. The main window opens the file and the second dialog interprets it. The problem is that this code doesn't work because it constructs the window before initializing the variable:

Main window```
void wxEVAFrame::OnLevelNames(wxCommandEvent& event)
{
	LevelNames dlg(this);
	dlg.Prep(filename);    // <-filename is defined in the .h file
}
```
LevelNames:: Prep```
void LevelNames::Prep(wxString fname){
	filename = fname;    // <-filename is defined in the .h file
	wxMessageDialog(this,filename).ShowModal();    // This one displays the proper filename
	ShowModal();
}
```
LevelNames::LevelNames also has the wxMessageDialog thing but it displays nothing.

Please help and/or explain why that is wrong.
Thanks in advance!

---

