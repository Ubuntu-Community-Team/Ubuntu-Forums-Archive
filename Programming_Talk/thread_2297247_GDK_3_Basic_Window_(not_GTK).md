---
title: "GDK 3 Basic Window (not GTK)"
date: 2015-10-02
forum: Programming Talk
---

### Post by dosh on 2015-10-02
I'm having problems making a basic GDK 3  window as there is little examples of GDK 3 (I found a copy of a basic GDK 1.2 example) and adjusted that. But I am getting a Segmentation Fault.

```



#include <gdk/gdk.h>

#include <glib.h>

int main (int argc, char *argv[]) {
  
    GdkWindow *window;
    GdkWindowAttr attributes;
    gint attributes_mask;
    GMainLoop *mainloop;
   
    if (!gdk_init_check (&argc, &argv)) {
        return FALSE;
    }

    attributes.window_type = GDK_WINDOW_TOPLEVEL;
    attributes.width = 400;
    attributes.height = 400;
    attributes.wclass = GDK_INPUT_OUTPUT;
    attributes.visual=  gdk_screen_get_rgba_visual(gdk_screen_get_default());

    window = gdk_window_new (NULL, &attributes, attributes_mask);

    gdk_window_show (window);

    mainloop = g_main_new (TRUE);

    g_main_run (mainloop);
}

```

---

### Post by dosh on 2015-10-02
I have worked out my problem, I haven't set the attributes_mask. See  [https://developer.gnome.org/gdk3/stable/gdk3-Windows.html#GdkWindowAttributesType]("https://developer.gnome.org/gdk3/stable/gdk3-Windows.html#GdkWindowAttributesType")

---

