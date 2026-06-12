---
title: "[C++/wx] wxToolBar-&gt;SetToolSeparation() Doesn't Work"
date: 2010-05-25
forum: Programming Talk
---

### Post by dodle on 2010-05-25
I can't resize the separators on my toolbar:
[php]// Tool Bar
wxBitmap ico_exit(wxImage(_T("pic/exit.png")));
wxBitmap ico_abc(wxImage(_T("pic/abc.png")));
wxBitmap ico_anim(wxImage(_T("pic/animals.png")));
wxBitmap ico_food(wxImage(_T("pic/food.png")));
wxBitmap ico_inst(wxImage(_T("pic/instrument.png")));

menu = CreateToolBar();
menu->SetToolSeparation(50); // Doesn't work
cout << menu->GetToolSeparation() << endl; // Returns 50 but separators are still same size

menu->AddRadioTool(ID_ABC, wxEmptyString, ico_abc);
menu->AddRadioTool(ID_FOOD, _T("Food"), ico_food);
menu->AddRadioTool(ID_ANIMALS, _T("Animals"), ico_anim);
menu->AddRadioTool(ID_MUSIC, _T("Music"), ico_inst);

menu->AddSeparator();
menu->AddTool(wxID_ABOUT, _T("About"), wxBitmap(wxImage(_T("pic/info.png"))));
menu->AddSeparator();
menu->AddTool(wxID_EXIT, _T("Exit"), ico_exit);

menu->Realize();[/php]
And it doesn't matter where I put "SetToolSeparation()", it always looks the same.  Is this an issue with wxGtk?  Or is it because I am using "CreateToolBar()" instead of "new wxToolBar()"?

**Edit:**  I think this is platform dependent.

---

