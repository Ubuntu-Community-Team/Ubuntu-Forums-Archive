---
title: "first gui in C++ errors"
date: 2009-07-08
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-08
```

#include <wx/wx.h>

class BasicApp : public wxApp
{
public:
    BasicApp();
    virtual bool OnInit();
private:
    wxFrame* frame;
};

DECLARE_APP(BasicApp)

IMPLEMENT_APP(BasicApp)

BasicApp::BasicAppp()
{
  frame = new wxFrame(NULL, -1, "My First GUI Program");
}

bool BasicApp::OnInit()
{
  frame->Show(true);
  return true;
}

```

and when I run ```
 g++ gui.cpp `wx-config --libs ` `wx-config --xxflags` -o gui 
```
I get these errors:
```

gui.cpp:16: error: ISO C++ forbids declaration of ‘BasicAppp’ with no type
gui.cpp:16: error: no ‘int BasicApp::BasicAppp()’ member function declared in class ‘BasicApp’

```

I don't understand because I only have my default destructor and the OnInit member function, so it's giving me errors for member functions I don't have???

Can any one please help me with this?

---

### Post by Mirge on 2009-07-08
BasicApp::BasicApp_**p**_()

:)

---

### Post by c0mput3r_n3rD on 2009-07-08
:D alright that takes care of one issue but of course comes another!:
[CODE]

gui.cpp: In constructor &#8216;BasicApp::BasicApp()&#8217;:
gui.cpp:18: error: conversion from &#8216;const char [21]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682: note:                 wxString::wxString(int) <near match>
[\CODE]

Any ideas about that?

---

### Post by MadCow108 on 2009-07-08
surround your strings with wxT(...)

[http://wiki.wxwidgets.org/WxString#Warnings](http://wiki.wxwidgets.org/WxString#Warnings)

---

### Post by c0mput3r_n3rD on 2009-07-08
Awsome that worked too, how ever when i run the program i get this:
```


(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): Gdk-CRITICAL **: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

```

---

### Post by c0mput3r_n3rD on 2009-07-08
Any body have any idea what that means?

---

### Post by c0mput3r_n3rD on 2009-07-08
Please can any one tell me what those run time errors mean?

---

### Post by smartbei on 2009-07-09
I think you are supposed to create the objects in your application (frames, etc.) in the OnInit. This works for me:
```

#include <wx/wx.h>

class MyApp: public wxApp
{
	virtual bool OnInit();
};


IMPLEMENT_APP(MyApp) 

bool MyApp::OnInit()
{
	wxFrame *frame = new wxFrame((wxFrame *)NULL, -1, _T("Hello World"));
	frame->Show(TRUE);
	return TRUE;
} 

```
I am not sure what version of wx you are using... for me the compile string is:
```

g++ gui.cpp `wx-config --libs ` `wx-config --cxxflags` -o gui

```

Hope that helps!

---

