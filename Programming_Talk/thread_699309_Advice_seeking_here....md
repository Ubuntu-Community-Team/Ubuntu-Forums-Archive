---
title: "Advice seeking here..."
date: 2008-02-17
forum: Programming Talk
---

### Post by RemmyLee on 2008-02-17
As someone who predominantly used to GUI programming in a Windows environment via the API, I tend to still think their way when it comes to working with GUIs, for instance:

I'm in the process of converting a toolchain that wrote and one of the tools was a video player for a very obscure format. Now in Windows, I used HWND to get the window's handle and draw the video to the form.
Is there an equivalent to this in GTK+?

Most of my Linux programming experiences are centered around command line tools save libraries that do the window work for you.

---

### Post by pmasiar on 2008-02-17
Read sticky FAQ. Start by reading "How to ask questions".

Hint: better title, language, environment - do we have to guess all that?

---

### Post by Geekkit on 2008-02-17
> **RemmyLee said:**
> Now in Windows, I used HWND to get the window's handle and draw the video to the form. Is there an equivalent to this in GTK+?

Here's a great starting point:

[INDENT][http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)[/INDENT]

Going through the above tutorial will show you how to program in GTK+ 2.0. Or at least the basics.

---

### Post by RemmyLee on 2008-02-17
@pmasiar:

I was asking if GTK had an equivalent to windows HWND or Windows window handle. Language isn't significant, as I believed that by mentioning that it was a GTK+ question, C would be implied as it is what GTK was written in. However, I will attempt to be more painfully obvious in the future as it appears that some people can't make simple connections.

@Geekkit:
Thank you for providing something that I can actually use.

---

### Post by CptPicard on 2008-02-17
> **RemmyLee said:**
> Language isn't significant, as I believed that by mentioning that it was a GTK+ question, C would be implied as it is what GTK was written in.

Yes, it is significant as GTK has bindings to all sorts of languages. C is not implied necessarily.

---

### Post by Geekkit on 2008-02-17
> **RemmyLee said:**
> 
@Geekkit:
Thank you for providing something that I can actually use.

You're welcome. Also, and this is the way I found incredibly helpful for learning GTK, is download GLADE 2 not GLADE 3. The reason why I say version 2 is because version 2 of GLADE generates code whereas version 3 does not. If you create some GUIs with GLADE 2 (via it's drag-n-drop features) then you'll be able to see the code that was created and that will fill in a lot of the blanks.

I think you'll find some similarities but you'll also find a several different approaches as well. If I have a major complaint against GTK is that there's not enough documentation for it. Having said that, many forums (such as this one) and many IRC channels are filled with incredibly helpful people so that makes up for the documentation.

---

### Post by LaRoza on 2008-02-17
> **RemmyLee said:**
> 
I was asking if GTK had an equivalent to windows HWND or Windows window handle. Language isn't significant, as I believed that by mentioning that it was a GTK+ question, C would be implied as it is what GTK was written in. However, I will attempt to be more painfully obvious in the future as it appears that some people can't make simple connections.


Python is written in C as well. (Rather, CPython is)

Your question was vague, and difficult to answer. 

If you had given more, you would have gotten more useful information.

---

### Post by kknd on 2008-02-17
Sorry, double post. If you want to know how to draw things with GTK (using gdk or cairo), read the post below.

---

### Post by kknd on 2008-02-17
> **RemmyLee said:**
> 
I'm in the process of converting a toolchain that wrote and one of the tools was a video player for a very obscure format. Now in Windows, I used HWND to get the window's handle and draw the video to the form.
Is there an equivalent to this in GTK+?

In GTK, to draw something in a GtkWindow or GtkDrawingCanvas, you need to get the GdkWindow of the widget and draw on it at every "expose" event.

Something like that:

[PHP]
gboolean expose_callback(GtkWidget* widget, GdkEvent event,   gpointer data)
{
    // Get a GdkDrawable from: widget->window;
    // Draw to the drawable
    // Dispose
    return FALSE;
}

int main()
{
      ... initialization ...
      GtkWidget* mywidget = constructor(dasds);
      g_signal_connect(mywidget, "expose-event", expose_callback, NULL);
      ... main loop and etc ....
}
  [/PHP]

---

### Post by pmasiar on 2008-02-18
> **RemmyLee said:**
>  I will attempt to be more painfully obvious in the future as it appears that some people can't make simple connections.

If you imply I am not smart enough to read your mind, no problem: I will add you to my ignore list so I would not waste my time trying to help you understand why in 4 hours you did not get any answers.

---

