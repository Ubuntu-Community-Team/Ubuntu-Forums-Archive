---
title: "Segfault in function called on expose-event GObject"
date: 2009-07-12
forum: Programming Talk
---

### Post by hofsmo on 2009-07-12
I have made a GObject which contains a cairo context for drawing on a GtkDrawingArea. I am able to set and retrieve properties from the object's source file and from int main. Except when I connect with an expose event, in which case I get a segmentation fault.

The functions called when I get the segfault are:
[PHP]
/* The code is written in c*/

/*Callback function called on an expose-event*/
static gboolean
on_expose_event (GtkWidget *area, InlumiDots *dots)
{
  inlumi_dots_draw (dots, area);
  
  return FALSE;
}

/*the drawing function located in the object source file*/
void
inlumi_dots_draw (InlumiDots *dots, GtkWidget *area)
{
  InlumiDotsPrivate *priv;
  dots->priv = priv = INLUMI_DOTS_GET_PRIVATE (dots);
  gdouble radius = priv->dot_size;
  g_message ("%lf",radius);
  
  cairo_t *cr;
  cr = gdk_cairo_create (area->window);
  
  cairo_set_source_rgb (cr, 0, 0, 0);
  cairo_arc (cr, 10, 10, radius, 0, 2*G_PI);
  cairo_fill (cr);
  
  cairo_destroy (cr);	
}
[/PHP]
I can't really see any problem with these functions, so I will include the object sourcefile and the main file. I am not a very experienced programmer, so if I have failed to include some information please tell me. This problem have been bugging me a while now, and I would be really happy to put it behind me.

---

### Post by fr4nko on 2009-07-12
The problem is in the callback for 'expose-event'. The signature of the callback should be
```

gboolean (*callback)(GtkWidget *area, GdkEventExpose *event, InlumiDots *dots)

```instead of
```

gboolean (*callback)(GtkWidget *area, InlumiDots *dots)

```because the event is passed together with the Widget. You can see that by looking in the documentation for GtkWidget for the "expose-event".

So you should modify on_expose_event in testmain2.c like that
```
static gboolean 
on_expose_event (GtkWidget *area, GdkEventExpose *event, InlumiDots *dots)
{
  inlumi_dots_draw (dots, area);

  return FALSE;
}

```

Francesco

---

### Post by hofsmo on 2009-07-12
Thanks Fr4nko you really helped me out there, it works perfectly.

---

