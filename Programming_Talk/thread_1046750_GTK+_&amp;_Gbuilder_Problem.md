---
title: "GTK+ &amp; Gbuilder Problem"
date: 2009-01-21
forum: Programming Talk
---

### Post by rich1939 on 2009-01-21
I have an application that currently has two top-level windows. Both are defined with Glade 3 and the first top-level window contains a button that calls for the creation of the second top-level window in the following routine:

```

void dbProcessCompanyData()
{
    GtkWidget *cwin;

    cwin = NULL;
    cwin = GTK_WIDGET(gtk_builder_get_object (dbBuilder, "company_data"));
    gtk_widget_show_all (cwin);
.....
}

```

When the "company_data_ window is first instantiated, it displays with all of its child objects just fine. When I click the "close" box to destroy the window it goes away...but when I try to open it again, it just displays the window frame, a grey interior, and none of the child objects (which are enclosed within the window's XML file: company_data).

Any idea what could be going wrong? The call to gtk_builder_get_object does return a non-NULL result the second time.

---

### Post by rich1939 on 2009-01-21
[QUOTE=rich1939;6593560]Not just a bump,

Re the below given code:

```

void dbProcessCompanyData()
{
    GtkWidget *cwin;

    cwin = NULL;
    cwin = GTK_WIDGET(gtk_builder_get_object (dbBuilder, "company_data"));
    gtk_widget_show_all (cwin);
.....
}

```

I should also point out that the variable "dbBuilder" is a global variable, so it should still be intact when this function is called again.

---

### Post by cabalas on 2009-01-21
I believe with libglade (and I assume it is the same with gbuilder) that widgets are only created when the xml file is parsed. If you destroy the widget you cannot use it again, my suggestion would be to just hide the window instead.

---

### Post by rich1939 on 2009-01-21
> **cabalas said:**
> I believe with libglade (and I assume it is the same with gbuilder) that widgets are only created when the xml file is parsed. If you destroy the widget you cannot use it again, my suggestion would be to just hide the window instead.

Hmmm...I was under the impression that gbuilder parses the file, in realtime, to retrieve the specified object at the time the **gtk_builder_get_object()** function is called, whenever it is called. Perhaps this is not true, although what documentation for the function I have read, it leaves the impression that objects can be instantiated at any time from the XML file.

OTOH, I have thought of hiding the window...but I'd rather not have to do that.

I'd really like to have a definitive answer on how the **gtk_builder_get_object()** function behaves. Perhaps someone in the know will respond.

Thanks for your reply.

---

