---
title: "C++, wxwidgets and Eclipse: Not getting along."
date: 2008-05-06
forum: Programming Talk
---

### Post by Fireblend on 2008-05-06
Hello. I am currently interested in making Eclipse work with C++, but I've ran into some trouble. I installed the latest version of CDT (C++ Development Tools) plugin for Eclipse (version is 3.3.2), and it doesn't seem to want to compile anything at all. All I get is a message that says: "Launch Failed no Binaries".

I'm a complete noob at C++ (I've used Eclipse before for Java though) and I've got no idea what to do or what is wrong. I just made a .cpp file with a generic hello world code I found with a google search on an empty C++ project but that's the message that will appear everytime.

As a side note, I'm planning to use wxwidgets as soon as I'm able to even compile C++ applications on Eclipse, so if anyone has any experience with Eclipse+CDT+Wxwidgets, any recommendation, guide, tutorial or commentary would be great, I've looked for documentation on making this combination work but everything is seriously outdated so I'm not even sure if this is possible =/

Any help will be greatly appreciated; thanks in advance.

---

### Post by thornmastr on 2008-05-08
Rather than beat your head against a wall perhaps two suggestions might be beneficial.
1) If yoiu must use wxWidgets, take a very detailed look at CodeBlocks using the wxSmith flavor of wxWidgets. This will probably be enough to resolve most of youre programming requirements.
2). Forget Eclipse and forget wxWidgets. Look at QT4.[http://trolltech.com/](http://trolltech.com/) and as a very nice IDE look at QDevelop. [http://www.qdevelop.org/](http://www.qdevelop.org/)

Hopefully, one of these options will get you started.

Robert Berman

---

### Post by WitchCraft on 2008-05-08
> **Fireblend said:**
> Hello. I am currently interested in making Eclipse work with C++, but I've ran into some trouble. I installed the latest version of CDT (C++ Development Tools) plugin for Eclipse (version is 3.3.2), and it doesn't seem to want to compile anything at all. All I get is a message that says: "Launch Failed no Binaries".

I'm a complete noob at C++ (I've used Eclipse before for Java though) and I've got no idea what to do or what is wrong. I just made a .cpp file with a generic hello world code I found with a google search on an empty C++ project but that's the message that will appear everytime.

As a side note, I'm planning to use wxwidgets as soon as I'm able to even compile C++ applications on Eclipse, so if anyone has any experience with Eclipse+CDT+Wxwidgets, any recommendation, guide, tutorial or commentary would be great, I've looked for documentation on making this combination work but everything is seriously outdated so I'm not even sure if this is possible =/

Any help will be greatly appreciated; thanks in advance.

Eclipse is for Java - meaning it never works, no matter which plugin, no matter whether on Linux or Windows, and no matter which plugin for whatever language.
Try Codeblocks. It has Built-in C++ & wxWidgets support.
And if you need a good Java IDE, try Intellj IDEA.
Then delete Eclipse, it's a waste of diskspace, IMHO.

3) Don't forget wxWidgets, better forget Qt.

---

### Post by Fireblend on 2008-05-08
Thanks for the replies, I'll check those options out. Maybe I should elaborate a little more. As a university project, I've been assigned with making a Space Invaders clone, and as much as possible I'd like it to be cross-platform so it isn't tied to Windows or Linux, which seems to be wxwidget's specialty, and from there my interest on working with it. If there's any other options I'd be more than glad to hear about them.

---

### Post by Aessa on 2008-05-15
Crossplatform for graphical interfaces - simplest way is usually Java. If you're going for gaming, try some OpenGL libs for Java (JNI to native OpenGL libs). I used JOGL and JAMA for a university project which ran in windows - basically a map which can tilt/rotate/pan with little 3D models on it (GPS related). I know there are some better stuff out there for linux Java OpenGL projects, but this is mostly for 3D games. With JOGL 2D is fairly easy.

---

### Post by Silpheed2K on 2008-05-15
To make eclipse work with C++ you have to download the specific eclipse package for C++... you cant use the default one you have to get and use it manually.
[ftp://ftp.cse.buffalo.edu/pub/Eclipse/technology/epp/downloads/release/europa/winter/eclipse-cpp-europa-winter-linux-gtk.tar.gz](ftp://ftp.cse.buffalo.edu/pub/Eclipse/technology/epp/downloads/release/europa/winter/eclipse-cpp-europa-winter-linux-gtk.tar.gz)
CDT is already integrated with newer versions of Eclipse to my knowledge.. no need to download and install it.. I got it to recognize my Intel compilers.
I didnt use CDT at all this is what I did. If you feel it's repetitive then ignore it but this should work for you.

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

