---
title: "GTK - Type-ahead popup placement"
date: 2008-01-11
forum: Programming Talk
---

### Post by cachtenbaum on 2008-01-11
I'm writing a small gtk application and I'm using a GtkTreeView to display the files in the current directory. The treeview is enclosed in a scrolledwindow.
And when I start typing the type-ahead popup appears in the right-hand bottom corner of the treeview's coordinates, i.e. way outside the scrollwindow.

How do I change the position of the type-ahead popup?
So that it appears in the right-hand bottom corner of its parent?

I've submitted a screenshot of the problem [here]("http://img262.imageshack.us/my.php?image=screenshotsl4.jpg")

---

### Post by Kadrus on 2008-01-12
Could you put the code..so we can try to help you with it?

---

### Post by cachtenbaum on 2008-01-12
Here's the code that creates all the gtk widgets...

The create_view function creates a GtkTreeView and populates it.

```

  GtkWidget *window;
  GtkWidget *scrolled_window;
  GtkWidget *view;

  gtk_init (&argc, &argv);

  database_init ();

  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  
  gtk_container_set_border_width (GTK_CONTAINER(window), 4);

  gtk_window_set_title (GTK_WINDOW(window), PACKAGE_STRING);
  gtk_widget_set_size_request (window, 500, 500);

  scrolled_window = gtk_scrolled_window_new (NULL, NULL);


  gtk_scrolled_window_set_policy (GTK_SCROLLED_WINDOW (scrolled_window),
				  GTK_POLICY_AUTOMATIC, GTK_POLICY_ALWAYS);

  view = create_view();

  gtk_scrolled_window_add_with_viewport (GTK_SCROLLED_WINDOW (scrolled_window), view);

  gtk_container_add (GTK_CONTAINER(window), scrolled_window);

  gtk_widget_show_all (GTK_WIDGET(window));

  gtk_main();
```

---

