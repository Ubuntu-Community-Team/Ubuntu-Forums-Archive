---
title: "[SOLVED] Find out string length"
date: 2008-06-13
forum: Programming Talk
---

### Post by xlinuks on 2008-06-13
Hi,
In Java I do the following to find out the length of a string:

```

//prerequisites..
Graphics g = getGraphics();
FontMetrics fm = g.getFontMetrics();
String sText = getText();

//there we go !! ->
int iTextLength = fm.stringWidth( sText );

```

Can anyone please provide such a snippet for C++, be it using Pango or Cairo?

PS: when saying "length" I mean the width of the string (in pixels)

---

### Post by NormR2 on 2008-06-13
Ignore this.

---

### Post by xlinuks on 2008-06-13
> **NormR2 said:**
> A couple of hints:
The width would depend on the Font.  Look at the FontMetrics class. 
Another way to find a class/method to use would be to use the Java Doc API Index listing and look for a method that would give a string's width.
I know that it depends on the font, I just "simplified" the example, and, what's more important: I know how to do that in Java, I'm learning C++ so I would like to know how to do that in C++ !!   :)

And since the guys using C++ on Linux prolly use Pango or Cairo, I would like to see a snippet. I understand from seeing snippets rather than reading raw APIs.

OK.. Norm2.. :) but I already posted this..

---

### Post by LaRoza on 2008-06-13
> **xlinuks said:**
> 
And since the guys using C++ on Linux prolly use Pango or Cairo, I would like to see a snippet. I understand from seeing snippets rather than reading raw APIs.


"prolly"?

C++ doesn't have any standard interfaces for that, it would depend on the library being used. 

What library are you using?

---

### Post by moma on 2008-06-13
Here is an example using the XLib. 
[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#text](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#text)  Browse down to "Drawing Text In A Window".
XLib is the very basic library that all X.org programs and toolkits call to do the drawing.  But the new, modern XCB library (C language binding to X) is now starting to replace the old Xlib. Maybe better to study how to code it in XCB. But wait, I think XCB is already working in the Ubuntu's X.org. See [http://xcb.freedesktop.org](http://xcb.freedesktop.org) and [http://en.wikipedia.org/wiki/Xcb](http://en.wikipedia.org/wiki/Xcb). XCB has a compatibility library that translates old Xlib calls to XCB. The X protocol (instructions through the socket/wire) hasn't changed. Study also [this]("http://linuxgazette.net/issue78/tougher.html")...

In Cairo it is equally easy to get the text measurements. Code:
cairo_text_extents_t  txt_ext;
cairo_text_extents(cr, "this is your text string", &txt_ext);

Study: [http://cairographics.org/manual/cairo-Text.html](http://cairographics.org/manual/cairo-Text.html) 
The same coded in Python/Cairo: [http://www.tortall.net/mu/wiki/CairoTutorial#understanding-text](http://www.tortall.net/mu/wiki/CairoTutorial#understanding-text)

I can give you a C++/Cairo example if you ask.

---

### Post by xlinuks on 2008-06-13
Thank you and a lotta kudos!!

---

