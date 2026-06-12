---
title: "VBScript Help"
date: 2008-07-08
forum: Programming Talk
---

### Post by LittleLORDevil on 2008-07-08
I am working on a VBScript for work and was wondering if anyone knew how to display an image in some sort of box.

Thanks

---

### Post by nvteighen on 2008-07-08
What kind of box? I'd try to use show up a <div></div> with borders, using document.write() and embed the image in there... Or just printing a raw <img>? But this sounds somehow a bit primitive... It's a long time I don't do any scripting.

EDIT: I'm assuming you're working on a web page. You can use VBScript for other stuff too, but only for Windows... By the way, your web page will only be viewable with IE. Use Javascript if you want cross-browser support.

---

### Post by LittleLORDevil on 2008-07-08
I am not working on a webpage, this is a macro for another program for the company that I am working for.

---

### Post by ghostdog74 on 2008-07-08
you could try [HTA](http://en.wikipedia.org/wiki/HTML_Application)

---

### Post by nvteighen on 2008-07-08
> **LittleLORDevil said:**
> I am not working on a webpage, this is a macro for another program for the company that I am working for.
OK. My mistake! As I said, it's a long time I don't touch these kind of programming, so I won't be very helpful...

But, what kind of box? You'll run this calling the Windows Script Host somehow, so you are bound initially to the Windows API; I don't remember anything there that pops out a box with an image, except opening a new window (can you do that in VBScript?).

Is there anything similar in GNOME or KDE to what you want?

---

### Post by LittleLORDevil on 2008-07-08
> **nvteighen said:**
> OK. My mistake! As I said, it's a long time I don't touch these kind of programming, so I won't be very helpful...

But, what kind of box? You'll run this calling the Windows Script Host somehow, so you are bound initially to the Windows API; I don't remember anything there that pops out a box with an image, except opening a new window (can you do that in VBScript?).

Is there anything similar in GNOME or KDE to what you want?

Basically any window that has the capability to show an image, I am not too picky.  It is a last minute requirement thrown in for my project.  I hate it when companies do that.

---

