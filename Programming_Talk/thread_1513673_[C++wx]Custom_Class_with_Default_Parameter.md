---
title: "[C++/wx]Custom Class with Default Parameter"
date: 2010-06-19
forum: Programming Talk
---

### Post by dodle on 2010-06-19
I'm trying to create a custom wxDialog with an optional third argument (title).  I thought that the correct way to do this was to use "=" to create a default value for the argument.  

Here is a portion of my code:

**gnrcabt.h**
[php]class GenericAbout : public wxDialog
{
  public:
    GenericAbout(wxWindow* parent, wxWindowID id, const wxString& title);
};[/php]

**gnrcabt.cpp**
[php]GenericAbout::GenericAbout(wxWindow* parent, wxWindowID id, const wxString& title) : wxDialog(parent, id, title=_T("Default Title"))
{
}[/php]

**test.cpp**
[php]about = new GenericAbout(this, -1);[/php]

Here is the error when I try to compile:
```
gnrcabt.cpp:3: error: passing `const wxString' as `this' argument of `wxString& wxString::operator=(const wxChar*)' discards qualifiers
```
I don't understand what the error is saying.  But if I change "title=_T("Default Title")" to "title" in **gnrcabt.cpp**, and add a third argument, "title=_T("Custom Title")", to **test.cpp** everything works fine.  But then the third argument is mandatory.  What am I doing wrong?

---

### Post by dodle on 2010-06-19
Ok, figured it out.  I set the default argument in the header file:

**gnrcabt.h**
[php]class GenericAbout : public wxDialog
{
  public:
    GenericAbout(wxWindow* parent, wxWindowID id, const wxString& title=_T("Default Title"));
};[/php]

---

