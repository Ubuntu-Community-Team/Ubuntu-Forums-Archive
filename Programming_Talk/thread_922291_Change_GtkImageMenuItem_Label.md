---
title: "Change GtkImageMenuItem Label"
date: 2008-09-17
forum: Programming Talk
---

### Post by joebert on 2008-09-17
I'm loading a GtkMenu using GladeBuilder for use as a context menu at runtime.

```
builder = gtk_builder_new ();
	gtk_builder_add_from_file (builder, "context-menu.xml", NULL);
```

The menu is a few levels deep, it consists mostly of GtkImageMenuItems.

Some of these items have a default label set in the XML file that I'd like to use as a template for printf before replacing that label with the return value from printf.

For instance in this section I want to replace the rgb(...) template with a label that's actually using the rgb values I'm getting from a GtkTreeViews selected row, the selected row being where the context menu is triggered from.
```
  <object class="GtkUIManager" id="uimanager1">
    <child>
      <object class="GtkActionGroup" id="actiongroup1">
        <child>
          <object class="GtkAction" id="rgb-tocb">
            <property name="stock_id">gtk-copy</property>
            <property name="name">rgb-tocb</property>
            <property name="tooltip" translatable="yes">Copy rgb formated color to clipboard</property>
            <property comments="..." name="label">rgb(%s, %s, %s)</property>
            <signal handler="copy_label_to_clipboard" name="activate"/>
          </object>
        </child>
```

I can't for the life of me figure out how to get a reference to the text label portion of the menu items though. I keep getting messages stating the following.
> cannot convert to a pointer type

Here's my latest attempt.

```
GtkWidget			*item_label;
GtkImageMenuItem	*imi;
GtkMenuItem			*mi;

imi			= GTK_IMAGE_MENU_ITEM (gtk_builder_get_object (builder, "hex-tocb"));
mi			= GTK_MENU_ITEM (imi->menu_item);
item_label	= GTK_LABEL (gtk_bin_get_child (GTK_BIN (mi->item)));
//GTK_LABEL (gtk_bin_get_child (GTK_BIN (GTK_MENU_ITEM (item_label)->item)));
//gtk_label_set_text (item_label, g_strdup_printf (gtk_label_get_text (item_label), shex));
```

Any help would be appreciated.
I've been searching through headers for label_set types of functions, & I'm about out of words to Google for.

---

### Post by SeanHodges on 2008-09-18
This should work:

```
GtkImageMenuItem* item = GTK_IMAGE_MENU_ITEM(
    gtk_builder_get_object(builder, "hex-tocb")
);

// Get the label
GtkWidget* menu_label = gtk_bin_get_child(GTK_BIN(item));
gtk_label_set_text(GTK_LABEL(menu_label), "new label text");
```

If it doesn't work, please post up the errors you are getting from it.

---

### Post by joebert on 2008-09-18
Hi Sean, thanks.

Here's the erros I'm getting

```
(picksel:31377): GLib-GObject-WARNING **: invalid cast from `GtkAction' to `GtkImageMenuItem'

(picksel:31377): GLib-GObject-WARNING **: invalid cast from `GtkAction' to `GtkBin'

(picksel:31377): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(picksel:31377): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

```

---

### Post by joebert on 2008-09-18
I'm getting closer. I looked into that GtkAction bit, came up with the following, and successfully set a new value for the label.

```
GtkAction *action = gtk_builder_get_object(builder, "hex-tocb");
g_object_set(action, "label", "new label ?", NULL);
```

---

### Post by joebert on 2008-09-18
Now we're cookin' with Crisco ! :D

```
GtkBuilder	*builder;
GtkAction	*action;
gchar		*item_label;

action = GTK_ACTION (gtk_builder_get_object(builder, "hex-tocb"));
g_object_get (action, "label", &item_label, NULL);
g_object_set (action, "label", g_strdup_printf (item_label, shex), NULL);
g_object_unref (G_OBJECT (action));
g_free (item_label);
```

---

