---
title: "Printing with Pango"
date: 2012-03-22
forum: Programming Talk
---

### Post by r-senior on 2012-03-22
Has anyone done any printing with GTK of any description and Pango/Cairo?

I'm trying to print plain text and I've got the basics working with a print operation dialog but I'm not handling wrapping lines.

When the print job is about to start the print operation fires a begin-print signal and the handler has to set the total number of pages. For each page a show-page signal fires and the handler renders the page on a Pango/Cairo context.

*In File | Print handler:*
```
delegate = printing.PrintDelegate(text, font)

operation = Gtk.PrintOperation()
operation.connect('draw-page', delegate.on_draw_page)
operation.connect('begin-print', delegate.on_begin_print)
operation.run(Gtk.PrintOperationAction.PRINT_DIALOG, self)
```

I've got these parts working but I'm calculating the number of pages based on the number of lines in my text and the page size. This works OK unless lines are wrapped when rendering a page. In that case, my line count is short and I don't get enough show-page signals to print all the pages.

*In PrintDelegate:*
```
def on_begin_print(self, operation, context):
    # This just insets margins to make a printable body rectangle
    self.body = self.body_rect(context)

    layout = context.create_pango_layout()
    layout.set_width(self.body.width * Pango.SCALE)
    layout.set_height(self.body.height * Pango.SCALE)
    layout.set_font_description(self.font)

    layout.set_text(self.text, -1)
    [COLOR="Red"]total_lines = len(self.text.splitlines())[/COLOR]
    lines_per_page = layout.get_line_count()
    pagination = divmod(total_lines, lines_per_page)
    num_pages = pagination[0] + (1 if pagination[1] else 0)
    operation.set_n_pages(num_pages)

    self.layout = layout

```

```
def on_draw_page(self, operation, context, page_no):
    lines_per_page = self.layout.get_line_count()
    first = page_no * lines_per_page
    last = first + lines_per_page
    lines = self.text.splitlines()
    page_text = '\n'.join(lines[first:last])

    ctx = context.get_cairo_context()
    ctx.move_to(self.body.x, self.body.y)
    self.layout.set_text(page_text, -1)
    PangoCairo.show_layout(ctx, self.layout)
```

Is there a way to ask Pango how many lines it will produce for the whole document, including wrapped lines? I can't see anything obvious.

I've tried not wrapping lines and there's an ellipsization thing where it is supposed to add '...' when it truncates a line but I can't get that to work at the moment either.

I'm using Python with GTK3 and GObject introspection. Not that that matters: the same principles would apply with GTK+, GTK3 or gtkmm in C or C++.

---

### Post by r-senior on 2012-03-24
I've not made any progress but I suspect it's not as easy as I would like. For example,  an application could choose to flip to landscape in the middle of a print run, which would make a pre-print calculation impossible.

I suspect I would need to do a simulated print run and send each line of text individually, detecting when I hit the end of the page to count pages.

I might just try to truncate lines again, which allows me to do the easy calculation up-front. Wrapping is not really that important to me, I was just interested to see if I could do it.

---

### Post by r-senior on 2012-03-24
OK, I downloaded the source code for GEdit to get some clues and it appears the GtkSourceView can do it. This is from the GtkSourceView documentation:

```
// Signal handler for the GtkPrintOperation::begin-print signal

static void
begin_print (GtkPrintOperation *operation,
             GtkPrintContext   *context,
             gpointer           user_data)
{
    GtkSourcePrintCompositor *compositor;
    gint n_pages;

    compositor = GTK_SOURCE_PRINT_COMPOSITOR (user_data);

    while (!gtk_source_print_compositor_paginate (compositor, context));

    [COLOR="Red"]n_pages = gtk_source_print_compositor_get_n_pages (compositor);[/COLOR]
    gtk_print_operation_set_n_pages (operation, n_pages);
}
```

So I'll translate that to Python and see how it goes.

---

