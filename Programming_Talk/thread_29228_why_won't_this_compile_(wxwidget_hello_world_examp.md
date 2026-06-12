---
title: "why won't this compile? (wxwidget hello world example)"
date: 2005-04-23
forum: Programming Talk
---

### Post by audax321 on 2005-04-23
Hello,

   I'm trying to compile this example I found:

Source: [hworld.cpp](http://www.dieburnbot.com/hworld.cpp) 

Here are the errors I get when I compile. Can someone else run this and see if they get something similar... its complaining about using converting from char to wxString... but the program is not using a char where the error is encountered...

Here's my output:

```

chiddy@ubuntu:~$ g++ hworld.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld
hworld.cpp: In member function `virtual bool MyApp::OnInit()':
hworld.cpp:40: error: conversion from `const char[12]' to `const wxString' is
   ambiguous
/usr/include/wx-2.5/wx/string.h:646: error: candidates are:
   wxString::wxString(wchar_t, unsigned int) <near match>
/usr/include/wx-2.5/wx/string.h:635: error:
   wxString::wxString(int) <near match>
hworld.cpp: In constructor `MyFrame::MyFrame(const wxString&, const wxPoint&,
   const wxSize&)':
hworld.cpp:51: error: conversion from `const char[10]' to `const wxString' is
   ambiguous
/usr/include/wx-2.5/wx/string.h:646: error: candidates are:
   wxString::wxString(wchar_t, unsigned int) <near match>
/usr/include/wx-2.5/wx/string.h:635: error:
   wxString::wxString(int) <near match>
hworld.cpp:53: error: conversion from `const char[6]' to `const wxString' is
   ambiguous
/usr/include/wx-2.5/wx/string.h:646: error: candidates are:
   wxString::wxString(wchar_t, unsigned int) <near match>
/usr/include/wx-2.5/wx/string.h:635: error:
   wxString::wxString(int) <near match>
hworld.cpp:56: error: conversion from `const char[6]' to `const wxString' is
   ambiguous
/usr/include/wx-2.5/wx/string.h:646: error: candidates are:
   wxString::wxString(wchar_t, unsigned int) <near match>
/usr/include/wx-2.5/wx/string.h:635: error:
   wxString::wxString(int) <near match>
hworld.cpp:61: error: conversion from `const char[22]' to `const wxString' is
   ambiguous
/usr/include/wx-2.5/wx/string.h:646: error: candidates are:
   wxString::wxString(wchar_t, unsigned int) <near match>
/usr/include/wx-2.5/wx/string.h:635: error:
   wxString::wxString(int) <near match>
hworld.cpp: In member function `void MyFrame::OnAbout(wxCommandEvent&)':
hworld.cpp:72: error: invalid initialization of reference of type 'const
   wxString&' from expression of type 'const char*'
/usr/include/wx-2.5/wx/msgdlg.h:36: error: in passing argument 1 of `int
   wxMessageBox(const wxString&, const wxString&, long int, wxWindow*, int,
   int)'

``` 

Thanks in advance  :)

---

### Post by toojays on 2005-04-24
I haven't installed wx2.5 yet, so I haven't tried this out, but I have an idea about it.

For every string it complains about, surround the string by _T(). e.g. for```
MyFrame *frame = new MyFrame( "Hello World", wxPoint(50,50), wxSize(450,340) );
``` change it to ```
MyFrame *frame = new MyFrame( _T("Hello World"), wxPoint(50,50), wxSize(450,340) );
```.

The program is using a char: in C++ the input "Hello World" is converted into an array of char, and terminated by a \0 (hence it compains about an array of size 12, although "Hello World" only has 11 characters.

The _T() is a convenience macro provided with wxWidgets. It is also used sometimes as wxT(). You should be able to find some documentation about it somewhere in the wxWidgets docs.

---

### Post by audax321 on 2005-04-24
Thank you, that was exactly the problem  :)

---

