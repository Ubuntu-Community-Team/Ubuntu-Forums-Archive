---
title: "[wxWidgets] Loading Icon from Char Array"
date: 2011-12-14
forum: Programming Talk
---

### Post by dodle on 2011-12-14
I'm trying to use a [color=blue]const unsigned char[][/color] that is data from a .png image for an icon:

[php]static const unsigned char tux_png[] = {
    0x89, 0x50, 0x4e, 0x47, 0x0d, 0x0a, 0x1a, 0x0a, 0x00, 0x00, 0x00, 0x0d, 
    0x49, 0x48, 0x44, 0x52, 0x00, 0x00, 0x01, 0x90, 0x00, 0x00, 0x01, 0xdf, 
    0x08, 0x06, 0x00, 0x00, 0x00, 0x7e, 0xb1, 0x8e, 0x75, 0x00, 0x00, 0xa0, 
    0xdb, 0x49, 0x44, 0x41, 0x54, 0x78, 0x5e, 0xec, 0xdd, 0x6b, 0x4c, 0x55, 
    0xd9, 0x1d, 0xc6, 0xe1, 0x97, 0x9b, 0x47, 0xf0, 0x5e, 0x8c, 0x20, 0x58, 
    0x51, 0x90, 0x86, 0x20, 0x12, 0x2d, 0xa3, 0x1d, 0x7b, 0xb5, 0xde, 0xb0, 
    0x54, 0xc7, 0x68, 0x13, 0x75, 0x54, 0xda, 0x5a, 0x52, 0x3e, 0xd4, 0xcc, 
    0x68, 0x89, 0x71, 0xd0, 0x4c, 0xa3, 0xc9, 0x8c, 0x89, 0x75, 0x92, 0x2a, 
    0x99, 0x89, 0xf3, 0x61, 0x8c, 0x46, 0xc3, 0x28, 0xad, 0x97, 0x8e, 0xd7, 
    0xa9, 0xb5, 0xca, 0xb4, 0xd6, 0x8c, 0x53, 0x99, 0x58, 0x65, 0x94, 0x18, 
    0x71, 0x00, 0x15, 0x51,
...[/php]

But I can't figure out how to use it with [color=blue]wxIcon[/color]. I have read [the docs](http://docs.wxwidgets.org/stable/wx_wxicon.html#wxicon) but still have not figured it out. I tried:

[php]wxIcon icon(tux_png);[/php]

and

[php]wxIcon icon(tux_png, 400, 479);[/php]

and some other things as well. Is there a way to convert data from a [color=blue]const char[][/color] for use with [color=blue]wxIcon[/color] or [color=blue]wxBitmap[/color]?

---

### Post by Bachstelze on 2011-12-14
Have you tried actually making it [font=monospace]const char[][/font], as opposed to [font=monospace]const unsigned char[][/font]?

---

### Post by dodle on 2011-12-14
[php]static const char tux_png[] = {
...
...[/php]
[php]wxIcon icon(tux_png, 400, 479);
SetIcon(icon);[/php]

> :/media/Data/Developing/test$ g++ test.cpp `wx-config --cxxflags --libs` -o test
test.cpp: In constructor &#8216;MainWindow::MainWindow(const wxString&)&#8217;:
test.cpp:17:34: error: conversion from &#8216;const char [41236]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.8/wx/string.h:692:3: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.8/wx/string.h:682:3: note:                 wxString::wxString(int) <near match>

**----- EDIT -----**

[php]wxIcon* icon;
icon = tux_png;[/php]

> :/media/Data/Developing/test$ g++ test.cpp `wx-config --cxxflags --libs` -o test
test.cpp: In constructor &#8216;MainWindow::MainWindow(const wxString&)&#8217;:
test.cpp:16:12: error: cannot convert &#8216;const char [41236]&#8217; to &#8216;wxIcon*&#8217; in assignment

---

### Post by cgroza on 2011-12-15
You need to convert your data to a wxString in order to load it.
In general, wxWidgets does not play very well with other string representations, including a char array.

---

### Post by Bachstelze on 2011-12-15
> **cgroza said:**
> You need to convert your data to a wxString in order to load it.
In general, wxWidgets does not play very well with other string representations, including a char array.

If you read the documentation link provided, wxIcon has a constructor that takes a const char[] as parameter. The chars in this case *do not* represent characters in a string, but the binary data of the pixels in the icon.

---

### Post by dodle on 2011-12-16
I've figured out (with help) how to load the data into a [color=blue]wxImage[/color] and [color=blue]wxBitmap[/color]. Can I convert one of those to [color=blue]wxIcon[/color]? I haven't been able to find a way as of yet, and [color=red]wxIcon::LoadFile[/color] doesn't seem to work like [color=red]wxImage::LoadFile[/color].

[php]wxPanel *bg = new wxPanel(this);

const int tux_png_size = sizeof(tux_png);
wxMemoryInputStream pngStream(tux_png, tux_png_size);

wxImage tux;
tux.LoadFile(pngStream, wxBITMAP_TYPE_PNG);

wxBitmap bmp(tux);

wxStaticBitmap *img = new wxStaticBitmap(bg, -1, bmp);[/php]


**----- SOLVED -----**

Thank you [xaviou](http://forums.wxwidgets.org/viewtopic.php?f=1&t=33158&p=137896#p137896):
[quote="xaviou"]You can use the "CopyFromBitmap" member of wxIcon...[/quote]

[php]const int tux_png_size = sizeof(tux_png);
wxMemoryInputStream pngStream(tux_png, tux_png_size);

wxImage tux;
tux.LoadFile(pngStream, wxBITMAP_TYPE_PNG);

wxIcon icon;
icon.CopyFromBitmap(tux);[/php]

---

