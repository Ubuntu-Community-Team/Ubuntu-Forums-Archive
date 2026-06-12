---
title: "[Gtk] How to cancel a drag event?"
date: 2012-09-23
forum: Programming Talk
---

### Post by bird1500 on 2012-09-23
Hi,
In Gtk's widget on_drag_begin() I decide whether the drag should be canceled (stopped) or not.

However, no method seems to be able to cancel a drag event, I still get drag_motion events after calling all of these functions from inside the function
on_drag_begin(on_drag_begin(const Glib::RefPtr<Gdk::DragContext> &context)):

context->drag_finish(false, true, 0);
context->drag_refuse(0); //probably same as drag_abort() in C
context->drop_finish(false, 0);
context->drop_reply(false, 0);

Again, none of these cancel/stop the whole drag & drop event shebang, since, as I said, I keep getting the drag motion event and the cursor is still the usual "drag" icon.

Any ideas?

Setting zero to time(NULL) doesn't have any effect.

---

### Post by alexfish on 2012-09-23
Not sure if this will help , save as "dragdrop.c"

```
/* compile: gcc -Wall -g `pkg-config --cflags --libs gtk+-2.0` -o dragdrop dragdrop.c */
#include <gtk/gtk.h>

gboolean on_button_press (GtkWidget* widget,
  GdkEventButton * event, GdkWindowEdge edge)
{
  if (event->type == GDK_BUTTON_PRESS)
  {
    if (event->button == 1) {
      gtk_window_begin_move_drag(GTK_WINDOW(gtk_widget_get_toplevel(widget)),
          event->button,
      event->x_root,
      event->y_root,
      event->time);
    }
  }

  return FALSE;
}


int main( int argc, char *argv[])
{

  GtkWidget *window;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_default_size(GTK_WINDOW(window), 230, 150);
  gtk_window_set_title(GTK_WINDOW(window), "Drag & drop");
  gtk_window_set_decorated(GTK_WINDOW (window), FALSE);
  gtk_widget_add_events(window, GDK_BUTTON_PRESS_MASK);

  g_signal_connect(G_OBJECT(window), "button-press-event",
      G_CALLBACK(on_button_press), NULL);

  g_signal_connect_swapped(G_OBJECT(window), "destroy",
        G_CALLBACK(gtk_main_quit), G_OBJECT(window));

  gtk_widget_show(window);

  gtk_main();

  return 0;
}
```Regards

alexfish

---

### Post by bird1500 on 2012-09-24
Thanks for your effort, but I need to cancel the dnd after it started, not before, since the dnd happens inside a Gtk::DrawingArea on filenames inside it that I draw myself.

---

### Post by satsujinka on 2012-09-24
If you can't get it to cancel, then just have drag-drop not do anything. Yeah, it ends up wasting cycles, but that's probably not a big deal for now.

---

### Post by bird1500 on 2012-09-25
It doesn't do anything, I tried to force the cursor to be an arrow but it's still a drag one, it will be somewhat confusing for the end users.

---

### Post by alexfish on 2012-09-25
> **bird1500 said:**
> Thanks for your effort, but I need to cancel the dnd after it started, not before, since the dnd happens inside a Gtk::DrawingArea on filenames inside it that I draw myself.

not sure what you mean , have not seen your code. sometimes it helps ?

in GTK you got to put the widget in an event box , then tell what events are required

then use the  "g_signal_connect_data"  to call the routine required for  each mouse event

also can draw  "new  cursor(required)" for   each event.

---

### Post by bird1500 on 2012-09-25
The DND is inside a DrawingArea which draws (by hand using Cairo) a table, see screenshot (unfortunately the cursor isn't captured by the gimp's screenshoter tool). Within this manually drawn table there are filenames/songs, so the DND works with respect to the drawn filenames, not to a gtk widget. The relevant DND code is in ui/View.cpp.

The source code is [here]("http://ubuntuforums.org/showthread.php?t=2062371").

---

### Post by alexfish on 2012-09-25
Need more info,

in the bottom area

there are folders to the left ,  is this a tree view

on the right side is this "one drawable area".

---

### Post by bird1500 on 2012-09-25
They are both 2 distinct "drawable areas", one paints a list (view) of files, and the other paints the songs, each inside a Gtk::ScrolledWindow to be able to scroll them, you can see that by looking at the source code.
But in this thread I'm talking about the one to the right, the one with songs, when one's drag starts on a song name (to move it up or down the list) that should be ok, but if one starts a drag not from above a songname, it should cancel the dnd. Right now, the DND happens regardless of where the DND starts, because the DND is obviously enabled with respect to the DrawingArea, not with respect to each painted song name.

---

### Post by alexfish on 2012-09-25
that because each is one drawable , 

possible, best will be to use IMAGE so for each file  " image1" = file1 and so on.

Regards

Alex

---

### Post by pz0151 on 2012-10-04
Hi bird1500,
i think, alexfish shows you the right way to achive what you want.

I had the same problem. Wanted to cancel drag after drag begin but found no way to do it. Did a lot of web searched and tried a lot of code approaches.

Now i don't call Gtk.Drag.SourceSet() within widget constructor but Gtk.Drag.Begin() within PointerMotion event.

Professional approaches do it similar. See Gnome Language trainer ([http://www.koders.com/csharp/fidE05785E172F769A4A1F1415C20180D96DEF743F8.aspx?s=cdef%3Asearch](http://www.koders.com/csharp/fidE05785E172F769A4A1F1415C20180D96DEF743F8.aspx?s=cdef%3Asearch)) or Banshee ([http://www.koders.com/csharp/fidA69945F34E254690DD6C4BE481B62D5B876D3C5A.aspx?s=cdef%3Abutton](http://www.koders.com/csharp/fidA69945F34E254690DD6C4BE481B62D5B876D3C5A.aspx?s=cdef%3Abutton)).

pz0151

---

### Post by alexfish on 2012-10-04
I have been doing some demo's for a gui builder / gtk

there is one possible solution to your delma

take a look at the screen-shot , all of this is using svg / librsvg , this can solve some incompatabilty issues with cairo and gtk / depending on version

 each small widgets to the left is an image from file .png , the slightly larger image is image loaded from svg mapped via hlink
this changes by clicking on each of the small widgets.

a sample of the code
```
<svg  width='200'  height='200'  id='svg2' >
    <image
       x='0'
       y='0'
       id='image'
       xlink:href="file:///gtk-widgets-imgs/check.png"
       height='200'
       width='200' />
</svg>
```The layout area is one image area ,  each widget you see is mapped to a screenarray[x][y],
a pointer to the array is performed by mouse x y , so each mouse event = routine or function x , you could position an image widget at a particular place on the screen IE: over the track you wish to copy , and of same size , if it has an xlink reference , then a dragdrop can be performed ,

you can extract info from the svg image using the librsvg ,hint can use the id= + clipboard, you will need to read up on how API's work

Have fun

Alexfish

---

