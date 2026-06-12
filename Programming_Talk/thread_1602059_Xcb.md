---
title: "Xcb"
date: 2010-10-20
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-20
Having looked at my options with Gtk and Qt I hopped back to the fundamental Xlib facilities and for once I finally feel I am in full control of what actually happens on the display of my App :)

X11 is way better designed than I expected :shock: admittedly X11 text rendering facilities have kind of been superseded by the freetype library, but that too is really easy to understand and program with :)

However as I was following some links from tutorials and things I came across references to XCB... the new light weight replacement for Xlib I gather?

So I'm wondering if that would be the way forward... I gather it outperform the old Xlib that Gtk and Qt are based on by like 25x as much thru-put, so I'm kind of wondering if that is genuine and if anyone got experience with it?

---

### Post by nvteighen on 2010-10-21
> **worksofcraft said:**
> 
So I'm wondering if that would be the way forward... I gather it outperform the old Xlib that Gtk and Qt are based on by like 25x as much thru-put, so I'm kind of wondering if that is genuine and if anyone got experience with it?

No experience with Xcb, but I want to warn you about something: don't confuse interface with implementation.

GTK+'s and Qt's respective APIs are interfaces, so they aren't really "based on X11" at all. They are implemented for X11 in GNU/Linux and UNIX OSs, because that's the graphical system we've got in these OSs, but GTK+ and, specially, Qt do work on Windows, where they're implemented on whatever Windows uses for graphical low-level programming.

What I mean is that neither GTK+ nor Qt reflect what X11 is. They aren't just higher-level versions for X11: when abstracting, you reach a point where you create something different to what you're basing yourself on, like in this case. Obviously, because apart from X11, both libraries are also based on other stuff totally "unrelated" (e.g. GLib) but that end up creating the "Widget-based GUI toolkit" abstraction layer.


So, I don't get what you can gain from X11, save pixel-based headaches. If you just want a GUI library not based on widgets, better use SDL, although it's not actually meant for GUIs either, it is more abstracted, is portable and has font support... and is less likely to make you reinvent the wheel.

---

### Post by worksofcraft on 2010-10-21
> **nvteighen said:**
> ...
So, I don't get what you can gain from X11, save pixel-based headaches. If you just want a GUI library not based on widgets, better use SDL, although it's not actually meant for GUIs either, it is more abstracted, is portable and has font support... and is less likely to make you reinvent the wheel.

What I want is to create my own class of widget. I'll try explain at a high level of abstraction without referring to vectors of strings or anything like that.

What this widget displays is multi line text, but the lines are specialised: Each line can be either anchored on the left margin or on the right margin and the sequence of glyphs of the text in that line are plotted heading away from it's margin.

Within the text of any line there can be further changes in direction, but these I handle by reversing the **display order** of the sequence of characters in that string. (Note this is not the same as reordering the text in the string).  

The problem with all the widgets in the highly abstracted toolkits that I looked at so far is that they have their own **integral logic** for plotting text. This logic is not controlled by the application program, but determined by character set that is being plotted. It does not do what I want and I cannot control it.

OTOH, the mechanism and interdependencies for defining or deriving my own specialized widgets within the framework of these toolkits is extremely complicated requiring extensive knowledge of the internals of the package as well as that of lower level libraries that it is based on. IMO it is something that can only be undertaken by people who have significant experience in working with this code.

As for reinventing wheels... developers of [XCB]("http://xcb.freedesktop.org/") evidently think it is worth doing. :)

---

