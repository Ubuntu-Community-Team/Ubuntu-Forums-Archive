---
title: "having problems with wxWidgets in wxDevc++"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Mavverick on 2008-09-09
Hello... I´m new in this forum.. so I don't know if I should make a new post.. or if I can just ask for some help here!
Anyway.. I'm working in wxDevC++ with wxWidgets.. and I'm having some trouble.
The problem is:
 I have a wxGrid in a file named Inverte_MatrizFrm.cpp... and with spin controls, I let the user insert the number of rows and columns the grid must have. After doing that, he will press a button that will open a new dialog. When this new dialog opens, I want that a new Grid open in it with the same number of columns and rows.. and here is where I'm having trouble!
 This code is in Inverte_MatrizFrm.cpp file:

void Inverte_MatrizFrm::btnInverterMatrizClick(wxCommandEvent& event)
{
	// insert your code here
	InversaDlg TempInversaDlg(this);
	TempInversaDlg.ShowModal();
}

 And this one is in InversaDlg.cpp file:

void InversaDlg::InversaDlgInitDialog(wxInitDialogEvent& event)
{
	// insert your code here
	grdInversa = new wxGrid(pnlInversa, ID_GRDINVERSA, wxPoint(5,5), wxSize(310,160));
    grdInversa->SetFont(wxFont(8, wxSWISS, wxNORMAL,wxNORMAL, false, wxT("Tahoma")));
    grdInversa->SetDefaultColSize(50);
    grdInversa->SetDefaultRowSize(25);
    grdInversa->SetRowLabelSize(50);
    grdInversa->SetColLabelSize(25);
grdInversa->CreateGrid(grdMatriz->GetNumberRows(),grdMatriz->GetNumberCols(),wxGrid::wxGridSelectCells);
}

I have grdMatriz declared in Inverte_MatrizFrm file... and then how it won't work because it says it is not declared! So how could I "transfer" those data to the other file, so that my new Grid can have the same number of columns and rows than the first one??
If anyone can give me a help, I will glad...

Thanks!

---

### Post by ByteJuggler on 2008-09-09
Do you use Ubuntu?  (To clarify: These forums are for users of the Ubuntu operating system, not arbitrary support requests. It looks like wxDevC++ is an open source *Windows only *wxWidgets form designer.  That said, there may be people here that can help you - try the Programming sub-forum though.)

---

