---
title: "How to program for a calendar in C/C++?"
date: 2007-07-25
forum: Programming Talk
---

### Post by laxmanb on 2007-07-25
How do you program for a calendar in C/C++? I want it to be like the Calendar you see when you click on the date in ubuntu, or the Calendar widget in Visual Studio.

I just want to know the basics of how it's done, so does anyone have an idea of how it's done?

---

### Post by AlexThomson_NZ on 2007-07-25
A bit vague there.

They would use a GtkDrawingArea and render the shapes/numbers/text on that.  Is that what you were asking?  Or were you meaning how know whether a month starts on a Tuesday, etc?

---

### Post by Soybean on 2007-07-25
If you ARE wondering about date handling, there are a few standard C functions that do some date-related things, but they're a little awkward ([http://www.cppreference.com/stddate/index.html](http://www.cppreference.com/stddate/index.html)). The Boost date_time library is probably your best bet.

Boost: [http://www.boost.org/](http://www.boost.org/)
date_time: [http://www.boost.org/doc/html/date_time.html](http://www.boost.org/doc/html/date_time.html)

---

### Post by laxmanb on 2007-07-26
> **AlexThomson_NZ said:**
> A bit vague there.

They would use a GtkDrawingArea and render the shapes/numbers/text on that.  Is that what you were asking?  Or were you meaning how know whether a month starts on a Tuesday, etc?

Yeah... something like this - Only I want to program it myself(quite basic, tho) - And I guess I'll have to know what day a month starts on... 

[IMG]http://img165.imageshack.us/img165/7964/calendardv9.png[/IMG]

---

### Post by LaRoza on 2007-07-26
You might be better off using a scripting language like Python or Ruby.

---

### Post by laxmanb on 2007-07-26
Anything will do - I just need the pseudocode so I can understand how it works before I begin coding...

---

### Post by LaRoza on 2007-07-26
Before programming a GUI, make a command line version, then just use that code for the GUI.

---

### Post by laxmanb on 2007-07-26
> **LaRoza said:**
> Before programming a GUI, make a command line version, then just use that code for the GUI.

will do. but I need to understand the logic on how the dates are 'fit' in the calendar IE which month starts on which day, etc. etc...

---

### Post by kknd on 2007-07-26
You wanna make one or use one?

Gnome has a calendar widget.

---

### Post by laxmanb on 2007-07-27
I want to MAKE one!!

---

### Post by LaRoza on 2007-07-27
In Python, [http://docs.python.org/lib/module-calendar.html](http://docs.python.org/lib/module-calendar.html)

---

