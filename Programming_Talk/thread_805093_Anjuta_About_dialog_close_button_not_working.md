---
title: "Anjuta: About dialog close button not working"
date: 2008-05-23
forum: Programming Talk
---

### Post by TabletUbuntu on 2008-05-23
Hi All-

I am new to Anjuta and gui programming.  I can create a simple empty window app with various dialogs and controls (anjuta 2.4.1 on Hardy).  When I use the built in Aboutdialog widget, however, the close button does not close the About Dialog window when the app runs.  There are no properties for the Close button, since it is part of an "internal action area".  

Any ideas how to get this to work?  I found an old bug (#361830 AboutDialog does not close) that was apparently fixed in Anjuta 2.1.0.

Anyone know if this is a known bug, or can suggest something to try?

Thanks.

---

### Post by cdekter on 2008-05-25
> **TabletUbuntu said:**
> Hi All-

I am new to Anjuta and gui programming.  I can create a simple empty window app with various dialogs and controls (anjuta 2.4.1 on Hardy).  When I use the built in Aboutdialog widget, however, the close button does not close the About Dialog window when the app runs.  There are no properties for the Close button, since it is part of an "internal action area".  

Any ideas how to get this to work?  I found an old bug (#361830 AboutDialog does not close) that was apparently fixed in Anjuta 2.1.0.

Anyone know if this is a known bug, or can suggest something to try?

Thanks.

You could try writing an event handler function that closes and destroys the dialog. Then bind that event handler to the EVT_CLOSE event for the about dialog. You don't need to specify a particular source for the event, since all you want to do is ensure the dialog closes when the event is emitted.

If this is in fact a bug, the bug would not be in Anjuta - it would be in GTK+ since that's the library Anjuta (via Glade) is using here.

---

