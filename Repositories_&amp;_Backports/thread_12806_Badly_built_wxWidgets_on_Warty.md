---
title: "Badly built wxWidgets on Warty"
date: 2005-01-26
forum: Repositories &amp; Backports
---

### Post by Quest-Master on 2005-01-26
So I spoke with the wxWidgets developers, and they told me the version of wxWidgets in Warty can be configured to run using GTK2. 

Apparently, whoever maintains wxWidgets, has configured it for use with GTK1. This might not be true, but otherwise, why else would such a recent version of wx use GTK1?

Because of this, other packages like wx.NET and wxPython also are forced to use GTK1, which does not deserve a spot on a modern Gnome desktop, or a place in the development of quality and top-notch applications.

If the wxWidgets package can be configured for GTK2 instead, I'm sure many developers such as myself would appreciate so. :)

EDIT: Odd.. what the developers seem to be saying is different than what is true. It looks like wx is using GTK2 since it has gtk-2.4 in it's include folder.. maybe there is something just wrong with wxPython?

---

### Post by redrob on 2005-05-19
I've chacked the dependencies on the Hoary versions, and
wxgtk is connecting to GTK 1.2 on Hoary.

Were you looking into the source packages when you saw the wierdness?

---

