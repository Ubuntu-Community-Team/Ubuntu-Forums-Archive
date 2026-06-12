---
title: "C++ WxWidgets unable to compile"
date: 2006-03-16
forum: Programming Talk
---

### Post by icyisamu on 2006-03-16
I am trying to learn C++ along with some GUI programming using WxWidgets.

I have wx2.6-common and wx2.6-headers packages installed.

The example I am learning is taken from :

[http://wxwindows.kn.vutbr.cz/hworld.txt]("http://wxwindows.kn.vutbr.cz/hworld.txt")

I compiled and got these errors:
```

@desktop:~/Desktop# g++ hword.cpp
hword.cpp:6:20: error: wx/wx.h: No such file or directory
hword.cpp:9: error: expected class-name before &#8216;{&#8217; token
hword.cpp:14: error: expected class-name before &#8216;{&#8217; token
hword.cpp:17: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
hword.cpp:17: error: ISO C++ forbids declaration of &#8216;wxString&#8217; with no type
hword.cpp:19: error: &#8216;wxCommandEvent&#8217; has not been declared
hword.cpp:20: error: &#8216;wxCommandEvent&#8217; has not been declared
hword.cpp:22: error: ISO C++ forbids declaration of &#8216;DECLARE_EVENT_TABLE&#8217; with no type
hword.cpp:23: error: expected &#8216;;&#8217; before &#8216;}&#8217; token
hword.cpp:23: error: expected `;' before &#8216;}&#8217; token
hword.cpp:31: error: &#8216;wxFrame&#8217; has not been declared
hword.cpp:32: error: expected constructor, destructor, or type conversion before &#8216;EVT_MENU&#8217;
hword.cpp:46: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
hword.cpp:46: error: ISO C++ forbids declaration of &#8216;wxString&#8217; with no type
hword.cpp: In constructor &#8216;MyFrame::MyFrame(int)&#8217;:
hword.cpp:47: error: class &#8216;MyFrame&#8217; does not have any field named &#8216;wxFrame&#8217;
hword.cpp:47: error: &#8216;wxFrame&#8217; was not declared in this scope
hword.cpp:47: error: expected primary-expression before &#8216;)&#8217; token
hword.cpp:47: error: &#8216;title&#8217; was not declared in this scope
hword.cpp:47: error: &#8216;pos&#8217; was not declared in this scope
hword.cpp:47: error: &#8216;size&#8217; was not declared in this scope
hword.cpp:49: error: &#8216;wxMenu&#8217; was not declared in this scope
hword.cpp:49: error: &#8216;menuFile&#8217; was not declared in this scope
hword.cpp:49: error: expected type-specifier before &#8216;wxMenu&#8217;
hword.cpp:49: error: expected `;' before &#8216;wxMenu&#8217;
hword.cpp:55: error: &#8216;wxMenuBar&#8217; was not declared in this scope
hword.cpp:55: error: &#8216;menuBar&#8217; was not declared in this scope
hword.cpp:55: error: expected type-specifier before &#8216;wxMenuBar&#8217;
hword.cpp:55: error: expected `;' before &#8216;wxMenuBar&#8217;
hword.cpp:58: error: &#8216;SetMenuBar&#8217; was not declared in this scope
hword.cpp:60: error: &#8216;CreateStatusBar&#8217; was not declared in this scope
hword.cpp:61: error: &#8216;SetStatusText&#8217; was not declared in this scope
hword.cpp: At global scope:
hword.cpp:64: error: variable or field &#8216;OnQuit&#8217; declared void
hword.cpp:64: error: &#8216;int MyFrame::OnQuit&#8217; is not a static member of &#8216;class MyFrame&#8217;
hword.cpp:64: error: &#8216;wxCommandEvent&#8217; was not declared in this scope
hword.cpp:64: error: &#8216;event&#8217; was not declared in this scope
hword.cpp:64: error: &#8216;WXUNUSED&#8217; was not declared in this scope
hword.cpp:65: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
hword.cpp:69: error: variable or field &#8216;OnAbout&#8217; declared void
hword.cpp:69: error: &#8216;int MyFrame::OnAbout&#8217; is not a static member of &#8216;class MyFrame&#8217;
hword.cpp:69: error: &#8216;wxCommandEvent&#8217; was not declared in this scope
hword.cpp:69: error: &#8216;event&#8217; was not declared in this scope
hword.cpp:69: error: &#8216;WXUNUSED&#8217; was not declared in this scope
hword.cpp:70: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token

```

Am I missing something here?

--Solution--

Install the missing libwxgtk2.6-dev

```
sudo apt-get install libwxgtk2.6-dev
```

Change all String functions from :

```
function_name("Hello");
```

to

```
function_name(wxT("Hello"));
```

Then compile using :

```

g++ -c `wx-config --cxxflags` filename.cpp
g++ -o filename filename.o `wx-config --libs`
```

Change filename to the name of your file.

Thanks to everyone who helped me ;)

---

### Post by mandible on 2006-03-16
find the wx.h file
then mkdir called wx in the same directory as your source code and copy wx.h into there
then try and recompile

---

### Post by icyisamu on 2006-03-16
This is what I did:

```

locate wx.h
cp wx.h /media/sda3/Programming/C++/wx
g++ hworld.cpp

[alot of errors, similar to above]

```

hworld.cpp is located in C++ directory, while wx.h is inside wx.

---

### Post by hod139 on 2006-03-16
I think the problem is that the wx2.6-headers package puts the wx headers at 
usr/include/wx-2.6/wx/
where most apps (like your example) expect the headers to be at
usr/include/wx/

You can try changing 
#include "wx/wx.h"
to
#include <wx-2.6/wx/wx.h>

---

### Post by icyisamu on 2006-03-16
[QUOTE=hod139]I think the problem is that the wx2.6-headers package puts the wx headers at 
usr/include/wx-2.6/wx/
where most apps (like your example) expect the headers to be at
usr/include/wx/

You can try changing 
#include "wx/wx.h"
to
#include <wx-2.6/wx/wx.h>[/QUOTE]

You were correct about the "usr/include/wx-2.6/wx/" location.

I edited it as you said but it still didn't work though.

---

### Post by Houman on 2006-03-16
try this:

```

g++ -c `wx-config --cxxflags` hword.cpp
g++ -o hword hword.o `wx-config --libs`
./hword

```

regards,
Houman

---

### Post by icyisamu on 2006-03-16
I tried the commands, but it gave me the errors as well.

---

### Post by hod139 on 2006-03-16
Can you paste the errors you get after running Houman's way?

---

### Post by icyisamu on 2006-03-16
using hod139's " #include <wx-2.6/wx/wx.h> "

```

@desktop:/media/sda3/Programming/C++# g++ -c `wx-config --cxxflags` hworld.cpp
bash: wx-config: command not found
In file included from hworld.cpp:6:
/usr/include/wx-2.6/wx/wx.h:15:21: error: wx/defs.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:16:23: error: wx/object.h: No such file or directory/usr/include/wx-2.6/wx/wx.h:17:25: error: wx/dynarray.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:18:21: error: wx/list.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:19:21: error: wx/hash.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:20:23: error: wx/string.h: No such file or directory/usr/include/wx-2.6/wx/wx.h:21:21: error: wx/intl.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:22:20: error: wx/log.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:23:22: error: wx/event.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:24:20: error: wx/app.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:25:22: error: wx/utils.h: No such file or directory
/usr/include/wx-2.6/wx/wx.h:26:23: error: wx/stream.h: No such file or directoryhworld.cpp:9: error: expected class-name before ‘{’ token
hworld.cpp:14: error: expected class-name before ‘{’ token
hworld.cpp:17: error: expected ‘,’ or ‘...’ before ‘&’ token
hworld.cpp:17: error: ISO C++ forbids declaration of ‘wxString’ with no type
hworld.cpp:19: error: ‘wxCommandEvent’ has not been declared
hworld.cpp:20: error: ‘wxCommandEvent’ has not been declared
hworld.cpp:22: error: ISO C++ forbids declaration of ‘DECLARE_EVENT_TABLE’ with no type
hworld.cpp:23: error: expected ‘;’ before ‘}’ token
hworld.cpp:23: error: expected `;' before ‘}’ token
hworld.cpp:31: error: ‘wxFrame’ has not been declared
hworld.cpp:32: error: expected constructor, destructor, or type conversion before ‘EVT_MENU’
hworld.cpp:46: error: expected ‘,’ or ‘...’ before ‘&’ token
hworld.cpp:46: error: ISO C++ forbids declaration of ‘wxString’ with no type
hworld.cpp: In constructor ‘MyFrame::MyFrame(int)’:
hworld.cpp:47: error: class ‘MyFrame’ does not have any field named ‘wxFrame’
hworld.cpp:47: error: ‘wxFrame’ was not declared in this scope
hworld.cpp:47: error: expected primary-expression before ‘)’ token
hworld.cpp:47: error: ‘title’ was not declared in this scope
hworld.cpp:47: error: ‘pos’ was not declared in this scope
hworld.cpp:47: error: ‘size’ was not declared in this scope
hworld.cpp:49: error: ‘wxMenu’ was not declared in this scope
hworld.cpp:49: error: ‘menuFile’ was not declared in this scope
hworld.cpp:49: error: expected type-specifier before ‘wxMenu’
hworld.cpp:49: error: expected `;' before ‘wxMenu’
hworld.cpp:55: error: ‘wxMenuBar’ was not declared in this scope
hworld.cpp:55: error: ‘menuBar’ was not declared in this scope
hworld.cpp:55: error: expected type-specifier before ‘wxMenuBar’
hworld.cpp:55: error: expected `;' before ‘wxMenuBar’
hworld.cpp:58: error: ‘SetMenuBar’ was not declared in this scope
hworld.cpp:60: error: ‘CreateStatusBar’ was not declared in this scope
hworld.cpp:61: error: ‘SetStatusText’ was not declared in this scope
hworld.cpp: At global scope:
hworld.cpp:64: error: variable or field ‘OnQuit’ declared void
hworld.cpp:64: error: ‘int MyFrame::OnQuit’ is not a static member of ‘class MyFrame’
hworld.cpp:64: error: ‘wxCommandEvent’ was not declared in this scope
hworld.cpp:64: error: ‘event’ was not declared in this scope
hworld.cpp:64: error: ‘WXUNUSED’ was not declared in this scope
hworld.cpp:65: error: expected ‘,’ or ‘;’ before ‘{’ token
hworld.cpp:69: error: variable or field ‘OnAbout’ declared void
hworld.cpp:69: error: ‘int MyFrame::OnAbout’ is not a static member of ‘class MyFrame’
hworld.cpp:69: error: ‘wxCommandEvent’ was not declared in this scope
hworld.cpp:69: error: ‘event’ was not declared in this scope
hworld.cpp:69: error: ‘WXUNUSED’ was not declared in this scope
hworld.cpp:70: error: expected ‘,’ or ‘;’ before ‘{’ token

```

---

### Post by hod139 on 2006-03-16
You are missing the libwxgtk2.6-dev package.
```

sudo apt-get install libwxgtk2.6-dev

``` 
And make sure you put the #include back to how the example had it.  And compile according to Houman.

---

### Post by icyisamu on 2006-03-16
I changed the #include back to "wx/wx.h".

Then I installed the missing package and compiled it using 

```
g++ -c `wx-config --cxxflags` hworld.cpp
```

For now I am getting these errors, and is unable to proceed with the second step suggested by Houman.

```

@desktop:/media/sda3/Programming/C++# g++ -c `wx-config --cxxflags` hworld.cpp

hworld.cpp: In member function &#8216;virtual bool MyApp::OnInit()&#8217;:
hworld.cpp:40: error: conversion from &#8216;const char [12]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp: In constructor &#8216;MyFrame::MyFrame(const wxString&, const wxPoint&, const wxSize&)&#8217;:
hworld.cpp:51: error: conversion from &#8216;const char [10]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp:53: error: conversion from &#8216;const char [6]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp:56: error: conversion from &#8216;const char [6]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp:61: error: conversion from &#8216;const char [22]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp: In member function &#8216;void MyFrame::OnAbout(wxCommandEvent&)&#8217;:
hworld.cpp:72: error: conversion from &#8216;const char [39]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
hworld.cpp:72: error: conversion from &#8216;const char [18]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>

```

---

### Post by Houman on 2006-03-16
hi there,

to fix this problem change all your strings like this:

function("some string");

into this:

function(wxT("some string"));

regards,
Houman

---

### Post by icyisamu on 2006-03-16
[QUOTE=Houman]hi there,

to fix this problem change all your strings like this:

function("some string");

into this:

function(wxT("some string"));

regards,
Houman[/QUOTE]

Thanks to everyone who helped me.

I got it to compile correctly :D

---

### Post by wyo on 2006-04-06
[QUOTE=icyisamu]I am trying to learn C++ along with some GUI programming using WxWidgets.

I have wx2.6-common and wx2.6-headers packages installed.

The example I am learning is taken from :

[http://wxwindows.kn.vutbr.cz/hworld.txt]("http://wxwindows.kn.vutbr.cz/hworld.txt")
[/QUOTE]

Maybe you should better look at wyoGuide ([http://wyoguide.sf.net)](http://wyoguide.sf.net)). It's not though for beginners but it shouldn't be too difficult since all code is described within the guidelines. Just have a look.

O. Wyss

---

### Post by fallingcow on 2006-06-14
Hey, I just ran in to this problem and found the answer in this thread, but I have some related questions:


Ok, this problem seems to be related to compiling unicode support in to wxWidgets, which is apparently NOT the standard, as it is quite difficult to find any sample code (especially in beginners' tutorials) that includes unicode support (wxT() around strings, among other things).

Judging from the problems caused by using Unicode that [this page]("http://www.wxwindows.org/manuals/2.6.3/wx_unicode.html") discusses, I'd rather have it disabled while learning, especially since it's not used in any of the tutorials (even the ones on the offical site!)

Is it possible to disable Unicode support in Ubuntu's wxWidgets, or will I have to compile it from source to do that?

---

### Post by fallingcow on 2006-06-14
Sorry for the double post, attempts to edit my previous post keep logging me out.  :confused: 

OK, I answered my own question.  Yes, you have to re-compile wxWidgets to remove Unicode support.  One must set wxUSE_UNICODE to 0 in setup.h, located at /usr/lib/wx/include/gtk2-unicode-release-2.6/wx (on my system, anyway), then recompile.  I'm trying to find a way to do that with the files provided by the Ubuntu wxWidgets dev packages, but the rest of the source doesn't seem to be installed, and there's no src package for wxWidgets listed in Synaptic.

There must be a better way to do this than grabbing the source off their site, untarring, and praying to the "./configure make install" gods.  I can't believe that the only dev package for wxWidgets provided by Ubuntu is incapable of compiling most of the sample code on the 'net without serious user modification of said code (and how is a newbie supposed to figure that out?).

*goes off to file a bug report*

---

### Post by mohtasham1983 on 2008-06-16
I know it s a bit late, but there might be some people having the same issue. The simplest solution to avoid this problem is to compile it like this:

[PHP]g++ gui.cpp `wx-config --libs` `wx-config --cxxflags` -o hworld[/PHP]

Cheers,

---

### Post by New_wx_User on 2009-09-17
Hi I'm facing a similar problem, when I try to compile my program this error message occurs:

g++  -c -O3  `wx-config --cxxflags`  -c -o GUI.o GUI.cc
GUI.cc: In member function ‘Case* GUI::add_case()’:
GUI.cc:41: error: invalid conversion from ‘const char*’ to ‘wxChar’
GUI.cc:41: error:   initializing argument 1 of ‘wxString::wxString(wxChar, size_t)’
GUI.cc:42: error: no matching function for call to ‘Case::create(int&, wxChar**&)’
Case.h:47: note: candidates are: void Case::create(int, char**)
GUI.cc:45: error: invalid conversion from ‘const char*’ to ‘wxChar’
GUI.cc:45: error:   initializing argument 1 of ‘wxString::wxString(wxChar, size_t)’
make: *** [GUI.o] Error 1

here's the code to GUI.cc:


#include "GUI.h"
#include "Case.h"
#include "Color_Key.h"
#include "wx/bitmap.h"

IMPLEMENT_APP(GUI)

wxApp * theApp = &wxGetApp();

bool GUI::OnInit()
{
  add_case();
  
  return true;
}

Case * GUI::add_case()
{
  int x, y;

  Case * c = new Case(this, "Cancer Grid", wxPoint(-1,-1), wxSize(600,400));
  c->create(argc, argv);
  c->GetPosition(&x, &y);

  Color_Key * colorkey = new Color_Key(c, "Key", wxPoint(x, y+420));
  colorkey->render();
  colorkey->Show();
  SetTopWindow(colorkey);
  
  c->set_palette(colorkey->palette());
  c->Show();
  SetTopWindow(c);
  return c;
}

void GUI::case_holder_duplicate(const Case * c)
{
  Case * c2 = add_case();
  c->clone(c2);
}

thank you for your helps!

---

### Post by azagaros on 2010-01-21
I downloaded something that should of compiled, I have checked and double checked the installs, and forced a reinstall a couple of times and a little miffed at what I am missing here.

```

make[1]: Entering directory `/home/shawn/Downloads/stx-btree-0.8.3/wxbtreedemo'
g++ -DPACKAGE_NAME=\"stx-btree\" -DPACKAGE_TARNAME=\"stx-btree\" -DPACKAGE_VERSION=\"0.8.3\" -DPACKAGE_STRING=\"stx-btree\ 0.8.3\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"stx-btree\" -DVERSION=\"0.8.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_STDBOOL_H=1 -I.    -I/usr/include  -I../include -DBTREE_DEBUG -g -MT WMain.o -MD -MP -MF .deps/WMain.Tpo -c -o WMain.o WMain.cpp
In file included from WMain.h:25,
                 from WMain.cpp:25:
WMain_wxg.h:3:19: error: wx/wx.h: No such file or directory
WMain_wxg.h:4:22: error: wx/image.h: No such file or directory
WMain.cpp:28:24: error: wx/filedlg.h: No such file or directory
WMain.cpp:29:25: error: wx/textfile.h: No such file or directory
WMain.cpp:30:24: error: wx/tokenzr.h: No such file or directory
In file included from WMain.h:25,


```

I am experienced c++ programmer and this says the header file doesn't exist in the scope of the knowledge of the compiler.  I have made sure I have the wxWidgets packages installed more than once.

I didn't write this code and the code has notations for 2.8 of wxWidgets, so the assumption it should compile if the compiler can find the libraries.  How do I fix this?

I am trying to learn about the b+ tree not coding and was investigating the class template for other projects and wx example seemed to be a good place to start learning mechanics of the thought process of said tree.  Reading the various documents and pseudo code was enlightening and mind warping.  

Most of the suggestions in this thread are already in the code.

please help me.

---

### Post by dwhitney67 on 2010-01-21
What files do you have within the /usr/include/wx directory?

If you do not have wx.h or even the /usr/include/wx directory on your system, then contrary to what you think, I would guess that you do *not* have the WxWidgets development package installed.

---

