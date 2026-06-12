---
title: "How to align GTK labels for text entry widgets?"
date: 2009-07-07
forum: Programming Talk
---

### Post by resander on 2009-07-07
I am new to GTK and having a hard time using the layout containers. I cannot make the labels line up vertically. They come out looking like:
```

     label:       textentrywidget
  label biggest:  textentrywidget
   label big:     textentrywidget

```
when I use a 3 rows by 2 columns Table container. The labels go into the first column with vertical EXPAND=false and FILL=true and horizontal EXPAND=false and FILL=true

I want the labels left-aligned vertically in the column OR the first letter 'l' to start at the same position OR the colons at the end to align vertically. 

How can I do that?

---

### Post by monraaf on 2009-07-07
label.set_alignment(xalign=0.0, yalign=0.5)

---

### Post by resander on 2009-07-07
Many thanks. 

I didn't know about the set_alignment function. It is not available in GtkLabel, but in GtkMisc named gtk_misc_set_alignment. And it works!

Here is a fragment from the test program:

```

  GtkWidget * lab = gtk_label_new ( "label:" ) ;
  gtk_misc_set_alignment ( (GtkMisc *)lab , 0, 0.5 ) ;
  gtk_table_attach (GTK_TABLE (box), x, colix, colix+1,
                    rowix, rowix+1, GTK_FILL, GTK_SHRINK, 0, 0);
  colix++ ;
  GtkWidget *entry = gtk_text_entry_new (........ ;
  gtk_table_attach (GTK_TABLE (box), entry, colix, colix+1,
                    rowix, rowix+1, GTK_EXPAND, GTK_SHRINK, 0, 0);

```


Again, many thanks.

---

### Post by monraaf on 2009-07-07
> **resander said:**
> Many thanks. 

I didn't know about the set_alignment function. It is not available in GtkLabel, but in GtkMisc named gtk_misc_set_alignment. And it works!


It works because GtkLabel is a subclass of GtkMisc.

[http://library.gnome.org/devel/gtk/stable/GtkLabel.html#GtkLabel.object-hierarchy](http://library.gnome.org/devel/gtk/stable/GtkLabel.html#GtkLabel.object-hierarchy)

---

