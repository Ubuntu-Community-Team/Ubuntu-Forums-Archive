---
title: "No scrollbars on toplevel GTK window"
date: 2009-06-20
forum: Programming Talk
---

### Post by bcz on 2009-06-20
Have tried porting an GTK2/C program from standard LCD to an Acer Aspire One netbook with 1024x600 res.  (Linux based, looks like Ubuntu)

Copied binary from Ubuntu 9.04 and it was happy with all shared libraries

Screen is cropped and there are no scrollbars.  I dont appear to have any on a larger screen either, but this has not been a problem on 1600x1200

Does the standard toplevel GTK window not have scrollbars automatically if needed?

Do I need to use "gtk_scrolled_window-new" or should "gtk_window_new" automatically show scrollbars as required on the main window?

Any answers apreciated

Rgds Bill C

---

### Post by kknd on 2009-06-20
> 
Does the standard toplevel GTK window not have scrollbars automatically if needed?

No automatic scrollbars. GtkScrolledWindow is a container that adds scrollbars to a child (it's not a toplevel widget like GtkWindow). Only some widgets have native suport for scrolls. To your case, you will need to add a GtkViewport to make the widgets scrollable.

---

### Post by bcz on 2009-06-20
Thanks

I couldn't find this info in doc, but assumed scrolled window was what I needed, so tested it out

Have it solved now.  Bit of work to get netbook running nicely.  4 line change to my API to get scrollbars working... Much more to make application user acceptable on a small screen though

Rgds Bill

---

