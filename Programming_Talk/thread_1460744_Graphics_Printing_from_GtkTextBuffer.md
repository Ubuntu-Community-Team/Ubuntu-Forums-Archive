---
title: "Graphics Printing from GtkTextBuffer"
date: 2010-04-23
forum: Programming Talk
---

### Post by bcz on 2010-04-23
I use gtk_text_view in a scrolled window to obtain free_format text.

I need to move the text to a PangoLayout to render multiple pages to print using gtk_print_operation.

Is there any recommended way to do this?

I assume I need to make the width of the textView the same as the PangoLayout and read each line of text and render it into the layout until the page is full...not quite as efficient as printf and counting the CRs, but the world wants pretty pictures these days

Any documentation out there ?

Rgds Bill

---

