---
title: "GTK3.0+ how to change background color of a widget"
date: 2015-10-31
forum: Programming Talk
---

### Post by DaviesX on 2015-10-31
Hello, I just upgraded to Ubuntu 15.10 yesterday and some of the GTK API went deprecated.  ```
gtk_widget_modify_bg
``` as well as ```
gtk_widget_override_background_color
```. I spent some time search for alternatives but wasn't able to find a simple solution yet. I don't know why this has to involve in CSS. 

Could anyone please tell what is the simplest way to change background color of a widget in GTK3.0+? Thank you.

(as seen: [https://developer.gnome.org/gtk3/stable/GtkWidget.html#gtk-widget-override-background-color](https://developer.gnome.org/gtk3/stable/GtkWidget.html#gtk-widget-override-background-color))

---

### Post by DaviesX on 2015-11-07
It seems like CSS styling is the only way in GTK 3.16+. Here was what I did to make it work:

```

                /* styling background color to black */
                GtkCssProvider* provider = gtk_css_provider_new();
                GdkDisplay* display = gdk_display_get_default();
                GdkScreen* screen = gdk_display_get_default_screen(display);


                gtk_style_context_add_provider_for_screen(screen,
                                                          GTK_STYLE_PROVIDER(provider),
                                                          GTK_STYLE_PROVIDER_PRIORITY_USER);
                
                gtk_css_provider_load_from_data(GTK_CSS_PROVIDER(provider),
                                                "#main_drawing_region,GtkDrawingArea {     \n"
                                                "       background-color: black;                       \n"
                                                "}                                                                \n", -1, NULL);
                g_object_unref(provider);

```
```

    #some-widget-name,
    gtk-widget-type-goes-here#title-label-if-any {
        background-color : black;
    }

```

It's a lot more flexible to style with CSS, and it's neat for people who don't like reading API references.

PS: The article I read:
[https://thegnomejournal.wordpress.com/2011/03/15/styling-gtk-with-css/](https://thegnomejournal.wordpress.com/2011/03/15/styling-gtk-with-css/)

---

### Post by sujataakther on 2015-11-18
You can do this by adding css. I think you already find this code that is given above.

---

