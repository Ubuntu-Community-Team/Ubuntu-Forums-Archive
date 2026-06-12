---
title: "Glade and callback data"
date: 2010-12-29
forum: Programming Talk
---

### Post by mathyou on 2010-12-29
Hi,

I would have posted this in Gtk forums but it looks like the site has exceeded its bandwidth limit. Maybe a gtk guru here can help...

I can't seem to get my head around how callback user data works with glade. I've read through the (few) tutorials there are but it isn't making full sense yet. As a test case, say I wanted to recreate the helloworld2 example that is included with gtk, using glade. In this example two buttons are connected to a callback like so:

```
g_signal_connect (button, "clicked",
		      G_CALLBACK (callback), "button 1");
```

with the second button being passed "button 2". The callback function is: 

```
static void callback (GtkWidget *widget,
                      gpointer   data)
{
    g_print ("Hello again - %s was pressed\n", (gchar *) data);
}
```

What would be the best way to accomplish this with glade and gtk_builder_connect_signals()? I realise I could just create two callbacks, one for each button, and not even need to pass data, but this example is more for educational purposes.

Thanks in advance.
Matt

---

### Post by worksofcraft on 2010-12-29
> **mathyou said:**
> Hi,

I would have posted this in Gtk forums but it looks like the site has exceeded its bandwidth limit. Maybe a gtk guru here can help...

I can't seem to get my head around how callback user data works with glade. I've read through the (few) tutorials there are but it isn't making full sense yet. As a test case, say I wanted to recreate the helloworld2 example that is included with gtk, using glade. In this example two buttons are connected to a callback like so:

```
g_signal_connect (button, "clicked",
		      G_CALLBACK (callback), "button 1");
```

with the second button being passed "button 2". The callback function is: 

```
static void callback (GtkWidget *widget,
                      gpointer   data)
{
    g_print ("Hello again - %s was pressed\n", (gchar *) data);
}
```

What would be the best way to accomplish this with glade and gtk_builder_connect_signals()? I realise I could just create two callbacks, one for each button, and not even need to pass data, but this example is more for educational purposes.

Thanks in advance.
Matt

Well firstly you can tell the call-back widget will actually be button and then you can get it's label I think like so:
[php]
static int callback (GtkButton *widget,
                      gpointer   data)
{
    g_print ("Hello again - %s was pressed\n", gtk_button_get_label(widget);
    return false;
}
[/php]

Now as for user data I prefer to actually create a user data class and pass a pointer to that and you can put whatever you like in there.... but I get confused in plain C and need to do that in C++... I posted an example on another thread.

---

### Post by mathyou on 2010-12-30
> **worksofcraft said:**
> Well firstly you can tell the call-back widget will actually be button and then you can get it's label I think like so:
[php]
static int callback (GtkButton *widget,
                      gpointer   data)
{
    g_print ("Hello again - %s was pressed\n", gtk_button_get_label(widget);
    return false;
}
[/php]

Now as for user data I prefer to actually create a user data class and pass a pointer to that and you can put whatever you like in there.... but I get confused in plain C and need to do that in C++... I posted an example on another thread.

Thank you very much, that helped. For anyone reading this for info, I needed to use GTK_BUTTON() as in ```
gtk_button_get_label(GTK_BUTTON(widget))
```

---

