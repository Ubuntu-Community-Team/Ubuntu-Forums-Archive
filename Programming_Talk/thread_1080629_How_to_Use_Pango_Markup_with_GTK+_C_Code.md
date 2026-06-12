---
title: "How to Use Pango Markup with GTK+ C Code"
date: 2009-02-25
forum: Programming Talk
---

### Post by rich1939 on 2009-02-25
I have several top-level windows that include GTK TextEntry widgets for entry of data that will be stored in a PostgreSQL database. I'm validating the entries and when I find one that is invalid, I want to change the text color to Red and display a message box indicating that the highlighted entries are invalid, and to please correct them.

I have researched the situation and it seems that the Pango markup language could be used to do what I want...but I'm not sure how to do it. A section of my validation code is as follows:

```

const gchar *text;
GtkWidget *entry;

entry = GTK_WIDGET(gtk_builder_get_object(dbBuilder, "txtSSA"));
text = gtk_entry_get_text(GTK_ENTRY(entry));

// now I want to replace the contents of **text**
// by coloring it red and then posting a message box.

```

Any suggestions of how to do this with Pango?

---

### Post by tom66 on 2009-02-25
Check out the *set_markup* function for your label. I think it sets the Pango markup, or enables parsing, or something to that avail.

---

### Post by rich1939 on 2009-02-25
> **tom66 said:**
> Check out the *set_markup* function for your label. I think it sets the Pango markup, or enables parsing, or something to that avail.

I looked into pango_layout_set_text(); however, it seems to depend upon a PangoLayout, which in turn depends upon a PangoContext. This seems pretty complex and the layout and context both seem to have to be freed at some point. I didn't want to have to "hang" the application in the validation routine, but rather let the user fix the errors and then re-submit the form for re-validation.

How to handle all of this?

---

