---
title: "Gtk help"
date: 2006-08-23
forum: Programming Talk
---

### Post by zootreeves on 2006-08-23
Hi, How can I get the value of a gtk hscale widget 

I thought it would be somethings like this:

```

GtkWidget * scaler_new(gdouble low, gdouble high, gdouble prec)
{
    GtkWidget * w;
    w = gtk_hscale_new_with_range(low,high,prec);
    gtk_scale_set_value_pos(GTK_SCALE(w),GTK_POS_RIGHT);
    gtk_range_set_update_policy(GTK_RANGE(w),GTK_UPDATE_DISCONTINUOUS);
    gtk_widget_set_size_request(w,200,-1);
    return w;
}
static void
scalar_changed (GtkWidget *button, gpointer data)
{
        float value;
	value = gtk_scale_get_value_pos(button);
	printf("Value: %f\n", value);
}

 slider1 = scaler_new(0, 1, 0.05);
  g_signal_connect (slider1, "value_changed", (GCallback) scalar_changed, NULL);

  gtk_box_pack_start(GTK_BOX (hbox1),slider1,TRUE,TRUE,0);
  gtk_widget_show (slider1);

```

But it always prints 1.00. Any help would be appreciated. thanks

---

### Post by zootreeves on 2006-08-23
Or should it be.

```

static gchar*
format_value_callback (GtkScale *scale,
                       gdouble   value)
{

  printf("%f\n", value);
}


GtkWidget * scaler_new(gdouble low, gdouble high, gdouble prec)
{
    GtkWidget * w;
    w = gtk_hscale_new_with_range(low,high,prec);
    gtk_scale_set_value_pos(GTK_SCALE(w),GTK_POS_RIGHT);
    gtk_range_set_update_policy(GTK_RANGE(w),GTK_UPDATE_CONTINUOUS);
    gtk_widget_set_size_request(w,200,-1);
    return w;
}

  GtkWidget * slider1;
  slider1 = scaler_new(0, 1, 0.05);
  g_signal_connect ((gpointer) slider1, "value_changed",
                    G_CALLBACK (format_value_callback),
                    NULL);

```

but that doesn't seem to work either...

---

### Post by skeeterbug on 2006-08-23
This is in the C# docs (most of the stuff is the same).

[http://go-mono.com/docs/index.aspx?tlink=5@ecma%3a910%23HScale%2f](http://go-mono.com/docs/index.aspx?tlink=5@ecma%3a910%23HScale%2f)

From the Remarks:

"The HScale widget allows the user to select a value with a horizontal slider.

This widget and its model is manipulated using methods and properties in its super classes, Scale and Range."

If you look at scales members:

[http://go-mono.com/docs/index.aspx?link=T%3aGtk.Scale%2f*](http://go-mono.com/docs/index.aspx?link=T%3aGtk.Scale%2f*)

Here there are ValuePos and Digits properties.

---

### Post by jpka on 2010-06-10
Hi! I have *exactly* same problem, but reading about 'ValuePos' & 'Digits' not helpful for me, i'm too novice now and can't imagine where to use it.
Can you please put a line with working code using gtk_scale_get_value_pos? or maybe patch example above? 
Thanks!
(P.S. I don't know about C#, sorry... i use Eclipce and C)

---

### Post by SledgeHammer_999 on 2010-06-10
Uhm have you read the docs about what **gtk_scale_get_value_pos()** does? Probably not. Here is the quote from the [docs](http://library.gnome.org/devel/gtk/stable/GtkScale.html#gtk-scale-get-value-pos)-->*Gets the position in which the current value is displayed*

So this is not what you are looking for.
GtkScale is derived from a GtkRange. So to get the value you cast the GtkScale to GtkRange and use **gtk_range_get_value()**. Here is some example code:
```

GtkHScale *myscale = gtk_hscale_new_with_range(0, 1, 0.05);
gdouble current_value = gtk_range_get_value(GTK_RANGE(myscale));

```

Also the "value-changed" signal emits the new value too.

Maybe you should look to the tutorial too-->[http://library.gnome.org/devel/gtk-tutorial/stable/c633.html](http://library.gnome.org/devel/gtk-tutorial/stable/c633.html)

If you have more questions, I'll gladly answer(if I know them).

---

### Post by jpka on 2010-06-11
Hi SledgeHammer_999 your code work well!

gtk_scale_get_value_pos() has name which look like self-explaining, so i use it, but now gtk_range_get_value more suitable.
Thanks :KS

---

