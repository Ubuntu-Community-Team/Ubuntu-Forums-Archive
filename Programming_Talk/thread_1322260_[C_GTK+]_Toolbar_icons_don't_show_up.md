---
title: "[C GTK+] Toolbar icons don't show up"
date: 2009-11-10
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-10
Folks, I have a toolbar and I add a few tool buttons but they don't show up (their icons and text labels) according to the system-wide settings. Nautilus does, but not my own toolbar, it only shows the text labels.
Explicitly forcing it to use system-wide settings doesn't work:
```

gtk_toolbar_unset_style(GTK_TOOLBAR(toolbar));

```

The next attempt shows the icons but then it doesn't show up the labels:
```

gtk_toolbar_set_style (GTK_TOOLBAR (toolbar), GTK_TOOLBAR_ICONS);

```

Folks how do I make my toolbar "just work" according to system-wide settings?

---

### Post by PmDematagoda on 2009-11-10
Could you post the entire source code of the program?

And for the second problem where the toolbar buttons show only icons and not the text, that's because you used the wrong value for the second parameter which should be GTK_TOOLBAR_BOTH according to the GTK+ reference manual, so the command would be:-
```
gtk_toolbar_set_style (GTK_TOOLBAR (toolbar), GTK_TOOLBAR_BOTH);
```

---

### Post by froggyswamp on 2009-11-10
This is the code (1 file) and the icons themselves are attached.
```

#include <gtk/gtk.h>

#define ICON_LOCATION "/home/fox/Documents/c/"

typedef struct
{
  gchar *location;
  gchar *stock_id;
  gchar *label;
} NewStockIcon;

const NewStockIcon list[] =
{
  { "checklist.png", "check-list", "Check _List" },
  { "calculator.png", "calculator", "_Calculator" },
  { "camera.png", "screenshot", "_Screenshots" },
  { "cpu.png", "cpu", "CPU _Info" },
  { "desktop.png", "desktop", "View _Desktop" },
  { NULL, NULL, NULL }
};

static void add_stock_icon (GtkIconFactory*, gchar*, gchar*);

int main (int argc, 
          char *argv[])
{
  GtkWidget *window, *toolbar;
  GtkIconFactory *factory;
  gint i = 0;

  gtk_init (&argc, &argv);

  window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW (window), "Icon Factory");
  gtk_container_set_border_width (GTK_CONTAINER (window), 10);

  g_signal_connect (G_OBJECT (window), "destroy", G_CALLBACK (gtk_main_quit), NULL);

  factory = gtk_icon_factory_new ();
  toolbar = gtk_toolbar_new ();
  gtk_toolbar_unset_style(GTK_TOOLBAR(toolbar));
  gtk_toolbar_set_style (GTK_TOOLBAR (toolbar), GTK_TOOLBAR_BOTH);
  
  while (list[i].location != NULL)
  {
    GtkToolItem *item;
    
    gchar *str = g_strconcat(ICON_LOCATION, list[i].location, NULL);
    
    add_stock_icon (factory, str, list[i].stock_id);
    item = gtk_tool_button_new_from_stock (list[i].stock_id);
    gtk_tool_button_set_label (GTK_TOOL_BUTTON (item), list[i].label);
    gtk_tool_button_set_use_underline (GTK_TOOL_BUTTON (item), TRUE);
    gtk_toolbar_insert (GTK_TOOLBAR (toolbar), item, i);
    g_free(str);
    i++;
  }
    
  gtk_icon_factory_add_default (factory);
  
  gtk_toolbar_set_show_arrow (GTK_TOOLBAR (toolbar), FALSE);
  gtk_container_add (GTK_CONTAINER (window), toolbar);

  gtk_widget_show_all (window);
  gtk_main ();
  return 0;
}

static void add_stock_icon (GtkIconFactory *factory, gchar *location, gchar *stock_id) {
  GtkIconSource *source;
  GtkIconSet *set;
  
  source = gtk_icon_source_new ();
  set = gtk_icon_set_new ();
  
  gtk_icon_source_set_filename (source, location);
  gtk_icon_set_add_source (set, source);
  gtk_icon_factory_add (factory, stock_id, set);
}

```
When the _BOTH param is used - only text shows up.
quick recap:
When "unsetting" the style on the toolbar - also only text labels show up (but according to sys-wide settings there should be both icons and labels).

---

