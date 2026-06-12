---
title: "GTK progress != widget"
date: 2008-02-06
forum: Programming Talk
---

### Post by tom66 on 2008-02-06
```

pWindow = glade_xml_get_widget(pGlXML, "WindowMain");
pWidget = glade_xml_get_widget(pGlXML, "LoadingGlobalProgress");

gtk_progress_bar_set_fraction(pWidget, 0.001);
gtk_progress_bar_set_fraction(pWidget, 0.005);
gtk_progress_bar_set_fraction(pWidget, 0.095);

```

The above C code uses a Glade XML file to create the program's UI. It works without the three lines which control the progress bar. 

I get an error (actually, three, but repeated):

```

error: cannot convert 'GtkWidget*' to 'GtkProgressbar*' for argument '1' to 'void gtk_progress_bar_set_fraction (GtkProgressBar*, gdouble)' 

```

I know this is a type mismatch, but I don't know the solution. If anyone knows, please let me know.

Thanks!

---

### Post by DoktorSeven on 2008-02-06
You must use the uppercase macros for each GTK widget type to convert the general GtkWidget to the specific widget type.

In your case:
```

gtk_progress_bar_set_fraction(GTK_PROGRESS_BAR(pWidget), 0.001);

```

---

### Post by tom66 on 2008-02-07
Thanks! It solved the problem :)

Thanks again!
Tom

---

