---
title: "GTK+ Drag and Drop with icon view"
date: 2011-09-29
forum: Programming Talk
---

### Post by satsujinka on 2011-09-29
Would anyone happen to know how to make it so that when you're in an iconview, drag and drop doesn't begin unless you actually have an icon selected?

So currently, when I try to highlight things to drag I instantly get a drag operation. This is not the correct action, but I'm not certain how to fix it. Here's the code for the icon view declaration and adding it as a source and destination (which might not be correct either, but that's a different issue.)

```

    icon_view = init_view();
    gtk_icon_view_set_text_column(GTK_ICON_VIEW(icon_view), COL_NAME);
    gtk_icon_view_set_pixbuf_column(GTK_ICON_VIEW(icon_view), COL_PIXBUF);
    gtk_icon_view_set_selection_mode(GTK_ICON_VIEW(icon_view), GTK_SELECTION_MULTIPLE);
    gtk_icon_view_set_item_width(GTK_ICON_VIEW(icon_view), 100);
    gtk_drag_dest_set(icon_view, GTK_DEST_DEFAULT_MOTION | 
                        GTK_DEST_DEFAULT_HIGHLIGHT, target_list, 
                        n_targets, GDK_ACTION_COPY);
    gtk_drag_source_set(icon_view, GDK_BUTTON1_MASK, target_list, 
                        n_targets, GDK_ACTION_COPY);
    g_signal_connect(icon_view,"item-activated",G_CALLBACK(on_activate), NULL);
    g_signal_connect(icon_view,"button-press-event", G_CALLBACK(on_button_press), NULL);
    g_signal_connect(icon_view, "popup-menu", G_CALLBACK(on_popup),NULL);
    g_signal_connect (icon_view, "drag-data-received", G_CALLBACK(drag_data_receiver), NULL);
    g_signal_connect (icon_view, "drag-drop", G_CALLBACK (drag_dropped), NULL);
    g_signal_connect (icon_view, "drag-data-get", G_CALLBACK (drag_data_getter), NULL);
    g_signal_connect(homebutton, "clicked", G_CALLBACK(go_home), NULL);

```


Solution:

Use "button-press-event" to enable disable the iconview as a source based on how many items are selected.

---

